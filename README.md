# tt_json5

Basic json5 compliant* parser in python. Readability was more important than speed.

### Todo

- AStream implementation that streams a file. Need to figure out block size and max rewind requirements for that.
- Performance metrics against builtin json, rapidjson, orjson, msgspec.

### Non-compliance*

#### Keys
Unicode regex matching is hard, and finding for the first non-key character is easy. 
Instead of following the spec for keys, which are based on ECMAScript5.1 identifier strings,
I went with finding the first non-key character instead, allowing some invalid keys to exist without raising parse errors.

#### Whitespace
Whenever we look for whitespace this parser only supports space, tab, carriage return and line break. It omits U+2028 and U+2029 because we only parse individual bytes at present.

### Tests

Verified with the official tests from:
https://github.com/json5/json5-tests

It does not pass these 2 tests:
- illegal-unquoted-key-number.txt
- illegal-unquoted-key-symbol.txt
