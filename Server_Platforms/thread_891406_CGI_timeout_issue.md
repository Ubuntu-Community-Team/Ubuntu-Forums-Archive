---
title: "CGI timeout issue"
date: 2008-08-16
forum: Server Platforms
---

### Post by malcomosx.chris on 2008-08-16
Hey

I have a perl cgi script to generate the keys that openvpn requires to run.  How ever it takes such a long time (most of the time), the I get a time out error.  I have change the Timeout variable in apache, but it hasn't made a difference.  I have been scouring the internet and have come to the realization that I need to increase a Timeout variable in CGI.  How ever finding information on how to do this for perl seems to be scarce.  Any help would be greatly appreciated.  Im using Xubuntu 7.10 desktop i386, Apache 2.2.4, perl 5.8.8, the perl script simply executes a bash script that I have already created and the bash script builds all the keys and sets the permissions.

Chris ;)

---

