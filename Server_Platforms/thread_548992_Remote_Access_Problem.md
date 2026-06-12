---
title: "Remote Access Problem"
date: 2007-09-12
forum: Server Platforms
---

### Post by CLI-Linux on 2007-09-12
Here's the setup:

[LIST]
[*]Broadband Internet for home
[*]Linksys WRT54GL Router with forwarded ports set up
[*]Ubuntu 7.04 Server
[*]Apache Webserver
[*]Squid  Web Proxy
[*]VSFTP Server
[*]Webmin to administrate the server
[*]SSH Server
[/LIST]

(The Ubuntu Server contains all the servers and apps below it)

I recently had a problem with an SSH session where I got cut off (damn power surges) from a remote location (I'm currently at school).  When I logged back in, it gave me two errors:

something about the file system being read-only
 /home/***/.profile can't be written to; input/output error

when i restarted the server remotely (init 6), i couldn't log into SSH.  I can see it on the network (pings fine), so it's definitely run 'networking' after running through Grub.  Also, I know SquidProxy is back up and running because when I try and access my website (on my Apache Web Server in the same box) I get a "Connection refused" error from SquidProxy.

Is there any other way to get to the box remotely (there's no monitor or keyboard attached)?

Thanks.](*,)

---

