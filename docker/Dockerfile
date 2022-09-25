FROM nvcr.io/nvidia/pytorch:22.05-py3

ENV TZ=Asia/Tokyo

RUN apt-get update && apt-get install -y wget git git-lfs libglib2.0-0 libsm6 libxrender1 libxext-dev

# # VRAM多い人向け（オリジナル）
RUN git clone https://github.com/CompVis/stable-diffusion && \
    cd stable-diffusion && \
    conda init bash && \
    conda env create -f environment.yaml && \
    echo "conda activate ldm" >> ~/.bashrc

# 以下は、このコンテナをdocker runしてから手動で実行してcommitした。↑のcondaのldm env内でコマンドを実行するのが難しいため（多分できるが）
# RUN pip install -e git+https://github.com/CompVis/taming-transformers.git@master#egg=taming-transformers
# RUN pip install pytorch_lightning tensorboard==2.8 omegaconf einops taming-transformers==0.0.1 clip transformers kornia test-tube diffusers invisible-watermark

# RUN git clone https://github.com/gammagec/Dreambooth-SD-optimized.git &&\
#     cd Dreambooth-SD-optimized &&\
#     pip install -e .