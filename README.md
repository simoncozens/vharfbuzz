# vharfbuzz - A user-friendlier way to use Harfbuzz in Python

[uharfbuzz](https://github.com/harfbuzz/uharfbuzz) is an _awesome_ tool for shaping text in Python. But it wraps the Harfbuzz C interface quite closely, so still requires you to perform a bunch of boilerplate operations before you can get on with the shaping. This module allows you a slightly more high-level interface to the text shaping process. For example, rather than:

```python
with open(sys.argv[1], 'rb') as fontfile:
    fontdata = fontfile.read()

text = sys.argv[2]

face = hb.Face(fontdata)
font = hb.Font(face)

buf = hb.Buffer()
buf.add_str(text)
buf.guess_segment_properties()

features = {"kern": True, "liga": True}
hb.shape(font, buf, features)
```

with `vharfbuzz` you can just say:

```python
vhb = Vharfbuzz(sys.argv[1])
buf = vhb.shape(sys.argv[2], {"features": {"kern": True, "liga": True}})
```

The `Vharfbuzz` class also contains a number of other helpful methods to perform common operations on Harfbuzz buffers. See [Read The Docs](https://vharfbuzz.readthedocs.io/en/latest/) for more information.

## Installation

vharfbuzz is available from `pypi`, so can be installed like so:

    pip3 install vharfbuzz

If building from source, you can install it like so:

    pip3 install -r requirements.txt
    pip3 install .
