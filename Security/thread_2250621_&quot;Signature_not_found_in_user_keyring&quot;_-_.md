---
title: "&quot;Signature not found in user keyring&quot; - Can't Log In After Password Reset by Recovery"
date: 2014-10-29
forum: Security
---

### Post by coproc-sbcglobal on 2014-10-29
Hi! 

First, the preliminaries: 

Linux 3.16.0-24-generic #32-Ubuntu SMP x86_64 GNU/Linux
Ubuntu 14.10

I changed my login password, and forgot it. 

I then did the usual password reset steps. 

I got the "token manipulation error" 
[http://ubuntuforums.org/showthread.php?t=2106675](http://ubuntuforums.org/showthread.php?t=2106675)

I solved it with the following command: mount -o remount,rw /

While rebooting my computer, it does a consistency check of the drives each time. 

The check doesn't fail, but I think it has something to do with the password getting modified by the recovery root shell prompt. 

However, after I rebooted the computer, I couldn't log in. 

I tried logging in with the shell by pressing ctrl+f6. 

I could log in with my username and the new password. 

However, I found a .desktop link about accessing my data, and a README file. 

Access-Your-Private-Data.desktop README.txt

[http://ubuntuforums.org/showthread.php?t=1811170&highlight=ecryptfs+passwd](http://ubuntuforums.org/showthread.php?t=1811170&highlight=ecryptfs+passwd)

I think I may be running into a similar problem to this: 

[http://ubuntuforums.org/showthread.php?t=1271640&highlight=ecryptfs+passwd](http://ubuntuforums.org/showthread.php?t=1271640&highlight=ecryptfs+passwd)

---

