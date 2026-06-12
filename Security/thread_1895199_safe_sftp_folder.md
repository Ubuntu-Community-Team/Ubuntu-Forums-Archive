---
title: "safe sftp folder"
date: 2011-12-14
forum: Security
---

### Post by stephenbbb on 2011-12-14
what is the best way to create an account that will only be able to sftp to a folder and download stuff from there or upload stuff.
no reading of any other dirs above that home dir (no access to /usr/bin /usr/sbin except what is needed for sftp download and upload)

Thanks everybody.

---

### Post by lukeiamyourfather on 2011-12-14
You could modify the privileges of all the files, though it might cause issues elsewhere. Why the need to lock it down so much? It might be less complicated to use a tool that reverts any changes made during a session if you're worried about the machine getting junked up.

[http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html](http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html)

---

### Post by jeremywc on 2011-12-14
Sounds like you just need to use SFTP with chroot so they can't move outside of their home directory. Here's a good article on it: [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by stephenbbb on 2011-12-15
yep, chroot is exactly what i need. we'll see if I can make it work. the instructions are somewhat sketchy.

---

### Post by stephenbbb on 2011-12-16
using the suggested addition to sshd_config makes sshd die. 
I noticed there is already a subsystem sftp defined, so maybe that is the problem, but what is the solution? I have: 

Subsystem sftp /usr/lib/openssh/sftp-server 

Subsystem sftp internal-sftp 
Match group guests 
ChrootDirectory /home/%u 
X11Forwarding no 
AllowTcpForwarding no 
ForceCommand internal-sftp 
Match 

thanks everybody

---

