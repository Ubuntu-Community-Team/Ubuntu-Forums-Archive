---
title: "Cygwin and Kerberos"
date: 2014-05-09
forum: Security
---

### Post by Lee_Machine on 2014-05-09
Let me prefix this question with if this is the wrong forum please point me in the direction of the correct one. 

I'm using Cygwin and Windows 7 and ssh via Cygwin to Linux servers and workstation, to include Ubuntu. For authentication there is always the password but like not having to type my password 1000 times a day so I use my Windows AD kerberos tickets to login to Linux servers that are also on the Window domain. This all works but tickets expire everyday so I would like to add a statement to my bashrc like"

if kerberos_ticket == expired
   then kinit
fi

Looking at the man pages for kinit and klist I don't see how I could script this out. I guess I could grep/awk the output of klist but are there any quick solutions?

thanks,

Brandon

---

### Post by sudodus on 2014-05-09
Maybe your solution is to use [SSH keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") instead of passwords as described in the following link

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by Lee_Machine on 2014-05-09
Thanks, I'm familiar with SSH keys and have that setup too but for hosts that don't have trusted ssh keys setup kerberos works to supplement that.

---

### Post by HermanAB on 2014-05-10
I think you'll have to script it.

---

