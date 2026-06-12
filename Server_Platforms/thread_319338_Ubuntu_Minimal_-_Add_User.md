---
title: "Ubuntu Minimal - Add User"
date: 2006-12-15
forum: Server Platforms
---

### Post by matt_b on 2006-12-15
Hi all,

I've been experimenting with running my own Ubuntu server (hosting tomcat applications) and have now purchased a VPS through a third party instead of hosting it on my own machine.

On the VPS I've installed 6.06 (Dapper) and it looks like it's a minimal installation (commands like ftp etc. aren't available). There's also only one user - root :-? 

Before I start to add programs, files etc. I would like to add a new user account so that I'm not doing everything as the root user. Trouble is, I'm not sure how to get from a "one root account" to the standard Ubuntu permission set, that is, to have a "standard" user who can sudo and the root account disabled (or given a v. complex password).

Can anyone help? I know I need to use the adduser command but not sure about the switches, and what I need to do to enable sudo.

Thanks
matt_b

---

### Post by cknight725 on 2006-12-15
What, nobody?  I'm interested too!  Actually, I just wanna make 3 copies of the standard administrator account that is created during install ...

---

### Post by tekrei on 2006-12-15
I don't know if this link helps : [http://www.die.net/doc/linux/man/man8/adduser.8.html](http://www.die.net/doc/linux/man/man8/adduser.8.html)
About sudoers : [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by louisgag on 2006-12-17
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#User_Administration](http://ubuntuguide.org/wiki/Ubuntu_Edgy#User_Administration)

---

