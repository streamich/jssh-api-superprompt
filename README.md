$uper Prompt

*Super Prompt* command `$` implementation for [`jssh`](http://npmjs.com/package/jssh).

Available functionality in *CoffeeScript*:

Everything written below is valid *CoffeeScript* which transpiles to valid *JavaScript* and get executed in `jssh`.

*$uper prompt* is not implemented yet, but here is an idea of what it could do:

```coffeescript
# `$` stands for '$uper prompt'.

# Connect to more hosts, for example:
ssh '...'

# List available hosts.
$

# Proxy command to the active host.
$ 'ifconfig'

# Execute JS on the active host.
$ -> ls()

# Switch to second host.
$(1)

# Proxy a command to shell on the first host. (Localhost is always the first shell?)
$0 'ls'
$(0) 'whoami'

# Execute a command on 2nd, 3rd, 4th, and 5th hosts.
$([1..4]) 'ls /etc'

# Execute JS on the 2nd host.
$1 -> cd '../test'

# Execute a command on all hosts.
$.all 'rm -rf *'
$.all -> rm '-rf', '/'

# Send data across hosts.
data = 'Hello world'
$2 (data) -> data.to './test.txt'

# From host 2 to host 4
$(2).to(4) (data) -> data.to './test.txt'
```