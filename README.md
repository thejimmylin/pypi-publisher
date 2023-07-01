# PYPI Publisher

A template for you to easly to publish a package to PYPI.

## Install building tools

Before publishing, you need to setup a virtual Python environment and install some tools.

```
python3 -m venv .venv
source .venv/bin/activate
pip install -U pip wheel twine
```

## Edit source code and `setup.py`

- Edit the source code. Usually it should be in `your_lovely_package_name/` directory.
- Edit the `setup.py` file to match your package name and version and other details.

Now the repo should be something like this:

```
your_lovely_package_name/
├── __init__.py
└── foo.py
setup.py
README.md  <-- this file
```

## Publish to test.pypi.org (for testing purpose)

This makes you test your package before actually publishing it.

```python
# Build & Upload & Cleanup
python setup.py sdist bdist_wheel && python -m twine upload --repository-url https://test.pypi.org/legacy/ dist/* && rm -rf dist build *egg-info
```

install it with:

```
pip install -i https://test.pypi.org/simple/ your-lovely-package-name
```

## Publish to pypi.org

This makes you actually publish the package to `pypi.org` (where you can `pip install` packages from it).

```python
# Build & Upload & Cleanup
python setup.py sdist bdist_wheel && python -m twine upload dist/* && rm -rf dist build *egg-info
```

You can then install it with regular pip command you normally use:

```
pip install your-lovely-package-name
```
