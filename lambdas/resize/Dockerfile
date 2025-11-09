FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

COPY pyproject.toml .

RUN uv sync

COPY handler.py ${LAMBDA_TASK_ROOT}

ENV VIRTUAL_ENV=${LAMBDA_TASK_ROOT}/.venv
ENV PATH=${VIRTUAL_ENV}/bin:${PATH}
ENV PYTHONPATH=${LAMBDA_TASK_ROOT}:${VIRTUAL_ENV}/lib/python3.13/site-packages

CMD ["handler.resize_handler"]
############
#
# TODO: implement the rest of the image
#
############
