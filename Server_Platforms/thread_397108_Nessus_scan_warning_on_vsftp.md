---
title: "Nessus scan warning on vsftp"
date: 2007-03-30
forum: Server Platforms
---

### Post by zarg@henrikke on 2007-03-30
I have installed vsftp, and after running a nessus scan I got the following warning:

[INDENT][I]It is possible to force the FTP server to connect to third parties hosts by using 
the PORT command. 

This problem allows intruders to use your network resources to scan other hosts, making 
them think the attack comes from your network, or it can even allow them to go through 
your firewall.


Solution: Upgrade to the latest version of your FTP server, or use another FTP server.[/I][/INDENT]

However, by adding this to vsftpd.conf:

port_enable=NO

will I address this issue?

---

### Post by Mr. C. on 2007-03-30
The default for vsftpd is port_enable=YES, but the port_promiscuous value is NO.

Ignore Nessus message regarding this. The vsftpd server is very secure.

MrC

---

### Post by zarg@henrikke on 2007-03-31
Well, my man page says otherwise:

```
 port_enable
              Set to NO if you want to disallow the PORT method of obtaining a data connection.

              **Default: YES**

```

However, I haven't done a nessus rescan yet, to check if this change fixed it. If it does, the default setting in vsftpd.conf should be changed.

---

### Post by Mr. C. on 2007-03-31
I'm sorry, I was distracted and mis-copied the default value, and continued my typing without thinking.

You are correct, the default value for port_enable is YES; the default value for port_promiscuous is NO, and this is the security measure that prevents non-client IP addresses from abusing the PORT command.

I'll correct my previous post.
MrC

---

