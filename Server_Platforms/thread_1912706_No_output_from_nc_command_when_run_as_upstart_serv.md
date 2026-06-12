---
title: "No output from nc command when run as upstart service"
date: 2012-01-21
forum: Server Platforms
---

### Post by sblandford on 2012-01-21
I have a simple deamon, helperd, that grabs input from netcat (nc), runs a function and returns the results with nc working the other way, with this function...

```
function helperd ()
{
  while [ 1 ]; do
    #Read precisely one line
    line=$( nc -l 8008 | head -n 1 )
    echo "Got request  : $line"
    result=$( run_command $line )
    sleep 0.1
    echo "Replying with: $result"
    echo "$result" | nc -w 2 127.0.0.1 8009
  done
}
helpderd

```The /etc/init script looks like this...
```
description     "Helper Service"
author          "Simonb Blandford"

start on (net-device-up
          and local-filesystems
          and runlevel [2345])
stop on runlevel [016]

respawn

exec /usr/local/bin/helperd
```helperd is a bash script with #!/bin/bash as the first line.

If I run helperd directly on the command line it works as expected but if I run it as a service nc returns as expected after receiving the command but $line is always empty.

What could be different that would cause nc not to produce any output and just return empty lines when run as an upstart service?

This service used to work fine as a SysV script on CentOS.

---

