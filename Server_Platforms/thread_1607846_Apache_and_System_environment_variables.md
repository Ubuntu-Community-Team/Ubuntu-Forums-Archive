---
title: "Apache and System environment variables"
date: 2010-10-28
forum: Server Platforms
---

### Post by SebScoFr on 2010-10-28
Hi all,

I'm using Ubuntu 10.10 and Apache2.2

When editing the file /etc/apache2/envvars, instead of telling apache what the proxy to use is, like:
```
# The proxy
export HTTP_PROXY=192.168.x.x:xxxx
```
I'd like it to use a system variable. So I defined
```
HTTP_PROXY="http://134.157.220.19:8080"
```
within /etc/environment (which then appears correctly when using the 'printenv' shell command) but apache doesn't seem to recognize it when I try
```
# The proxy
export HTTP_PROXY=$HTTP_PROXY
```
in /etc/apache2/envvars

I execute a php script with phpinfo() in it, I can see the HTTP_PROXY variable under the environment panel but it's value is still set to 'no value'

What am I doing wrong?
Hope I was clear enough!

Thanks for your help

---

