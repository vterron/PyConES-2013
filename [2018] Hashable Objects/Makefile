#SHELL := /bin/bash

NOTEBOOK_FILE=python-hashable.ipynb

# Find out the module we need for the HTTP server, depending on the Python
# version. [Source: https://stackoverflow.com/a/4933395]
PYTHON_VERSION_FULL := $(wordlist 2,4,$(subst ., ,$(shell python --version 2>&1)))
PYTHON_VERSION_MAJOR := $(word 1,${PYTHON_VERSION_FULL})
MODULE.PYTHON.2 := SimpleHTTPServer
MODULE.PYTHON.3 := http.server

.PHONY: all slides present clean

all : slides

slides: ${NOTEBOOK_FILE}
	./slideshow.py ${NOTEBOOK_FILE}

present: slides
	# Binding to port 0 asks the kernel to allocate us a free port.
	python -m ${MODULE.PYTHON.${PYTHON_VERSION_MAJOR}} 0

abridged: ${NOTEBOOK_FILE}
	./slideshow.py ${NOTEBOOK_FILE} --alternative

clean:
	rm -fv *html
