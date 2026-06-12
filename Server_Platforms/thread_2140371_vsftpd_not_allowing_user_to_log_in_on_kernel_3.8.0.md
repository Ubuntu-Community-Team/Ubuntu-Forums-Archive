---
title: "vsftpd not allowing user to log in on kernel 3.8.0-19"
date: 2013-04-29
forum: Server Platforms
---

### Post by doralsoral on 2013-04-29
I recently upgraded my server to 13.04 (which I now regret as I had other huge headaches but have since fixed those). Now I am unnable to log in as a local user to vsftpd (using filezilla as a client). After googling forever I did see a few threads on other forums that is is a bug that relates to the newest kernel (3.8). However I found no solution other than downgrading to a previous kernel. I did boot in to an older kernel and was able to log in that way so this seems correct. I didn't find much about the problem on the net so I was wondering if anyone else has come across this problem and found a fix. The exact error message I get is 

Response:	530 Login incorrect.
Error:	Critical error
Error:	Could not connect to server

Thanks.

---

### Post by popecix on 2013-04-30
having the same issue

actually have two identical machines running Ubuntu

thought it was latest version of vsftpd, so I went back to 2.3.5 (even used the .deb from the server that still works), still getting the same 530 error and PAM "Operation Not Permitted" on the 13.04 box:

Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-17-generic i686):

*username@OptiPlexPrime:~$ ftp localhost**Connected to localhost.*
*220 (vsFTPd 2.3.5)*
*Name (localhost:username): username*
*331 Please specify the password.*
*Password:*
*230 Login successful.*
*Remote system type is UNIX.*
*Using binary mode to transfer files.*
[I]ftp>

[/I]Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic i686)

*username@OptiPlexDeux:~$ ftp localhost*
*Connected to localhost.*
*220 (vsFTPd 2.3.5)*
*Name (localhost:username): username*
*331 Please specify the password.*
*Password:*
*530 Login incorrect.*
*Login failed.*
[I]ftp>
[/I]
Passwords work or I wouldn't have been able to login.

Diffing the vsftpd.conf file returns nothing.
Diffing the /etc/pam.d/vsftpd file returns nothing.
The /etc/shells are right.
It's the exact same username and password on both boxen.
Same permissions on both boxes.

The only difference I'm seeing is I've upped the 'problem' one to 13.04 and thus the new kernel.

---

### Post by weyh on 2013-04-30
I ran into the same problem.  I ended up uninstalling vsftpd and installing pure-ftp.
I was happy with vsftpd until it broke but needed a server that worked.

---

### Post by vectorthorn on 2013-05-06
it's got me too. subscribing...

---

### Post by Cirvaazny on 2013-05-27
I had a similar issue, but it is on 3.8.0-21. Following the instructions for installing the patched version [here]("http://ubuntuforums.org/showthread.php?t=2143073&p=12641567#post12641567") allowed me to have local users log on again. You can find the bug [here]("https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372") in launchpad.

---

