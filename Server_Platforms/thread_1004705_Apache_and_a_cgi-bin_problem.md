---
title: "Apache and a cgi-bin problem"
date: 2008-12-07
forum: Server Platforms
---

### Post by ugo1 on 2008-12-07
Hi

I tried to setup apache server. All works fine with the exception of cgi-bin directory where i got

this error

Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

I checked the apache error log which say:

[[Mon Dec 08 00:03:19 2008] [error] [client xxx.xxx.x.xx] Premature end of script headers: hello.cgi


my document root is

/xxx/xxxxxxx/xxxx/xxx/

the cgi-bin directory is

/xxx/xxxxxxx/xxxx/xxx/cgi-bin/

in apache config file I have set 

ScriptAlias /cgi-bin/ "/xxx/xxxxxxx/xxxx/xxx/cgi-bin/"


perl -c hello.cgi give syntax ok (I have transfered the file setting ftp program in Ascii mode)


perl link in hello.cgi is /usr/bin/perl the same as which perl command output

from the command line the script work


any idea?

Regards

Ugo

---

