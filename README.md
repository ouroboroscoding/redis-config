# NamedRedis by Ouroboros Coding
[![pypi version](https://img.shields.io/pypi/v/namedredis.svg)](https://pypi.org/project/namedredis) ![MIT License](https://img.shields.io/pypi/l/namedredis.svg)

Named Redis: a simple wrapper for redis using config-oc to act as a factory for named connections

# Install
```
pip install namedredis
```

# Requires
namedredis requires python 3.10 or higher

# Uses
namedredis uses the [redis](https://pypi.org/project/redis/) package and returns an instance of StrictRedis.

# Using

example.py
```python
from nredis import nr, reset

# Reference every time
nr('main').set('foo', 'bar')

# Store instance for multiple uses
main_redis = nr('main')
main_redis.set('hello', 'world!')

# Re-fetches a config and resets the connection
reset('main')

# Resets all open connections
reset()
```

config.json
```json
{
	"redis": {
		"main": {
			"host": "localhost",
			"port": 6379,
			"db": 0,
			"protocol": 3
		},
		"secondary": {
			"db": 1
		}
	}
}
```

# Options

The following options all have defaults and don't necessarily need to be set. For more non-standard options, see [redis.StrictRedis](https://redis-py-doc.readthedocs.io/en/master/index.html#redis.StrictRedis)

| Name | Type | Default | Description |
| ---- | ---- | ------- | ----------- |
| host | str | "localhost" | The IP or host name of the server |
| port | unsigned | 6379 | The port of the server |
| db | unsigned | 0 | The DB to connect to on the server |
| protocol | unsigned | 3 | The protocol version to use |
