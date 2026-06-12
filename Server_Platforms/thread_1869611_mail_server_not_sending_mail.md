---
title: "mail server not sending mail?"
date: 2011-10-26
forum: Server Platforms
---

### Post by kooldino on 2011-10-26
It's not ubuntu, but I figured I'd ask anyway.

On my web server, I'm running CentOS 5.2, and it looks like Exim is my mail server.

It doesn't appear to be sending emails out.

Here is a tail of /var/log/maillog

```
Oct 25 23:45:00 cp authdaemond: modules="authpipe", daemons=5
Oct 25 23:45:00 cp authdaemond: Installing libauthpipe
Oct 25 23:45:00 cp authdaemond: Installation complete: authpipe
Oct 25 23:45:29 cp spamd[4971]: logger: removing stderr method 
Oct 25 23:45:33 cp spamd[4973]: spamd: server started on port 783/tcp (running version 3.2.4) 
Oct 25 23:45:33 cp spamd[4973]: spamd: server pid: 4973 
Oct 25 23:45:33 cp spamd[4973]: spamd: server successfully spawned child process, pid 5022 
Oct 25 23:45:33 cp spamd[4973]: spamd: server successfully spawned child process, pid 5023 
Oct 25 23:45:33 cp spamd[4973]: prefork: child states: IS 
Oct 25 23:45:33 cp spamd[4973]: prefork: child states: II 
```

What's "spamd" all about?  Does it think I'm a spammer or something?

And exim appears to be running:

```
# service exim status
exim (pid 4963 4962 4936 4934 4930) is running...

```

Not really sure what to do here.  Any help would be greatly appreciated.

---

### Post by pdc124 on 2011-11-24
dont know about centos, but have you configured exim ? 
what does 
 telnet localhost 25  
say 
or sudo nmap -sS localhost ?

---

### Post by lisati on 2011-11-24
spamd is part of a spam filtering process. Have a look here: [http://en.wikipedia.org/wiki/Spamd](http://en.wikipedia.org/wiki/Spamd)

Do you have spamassassin installed on your server by any chance?

---

