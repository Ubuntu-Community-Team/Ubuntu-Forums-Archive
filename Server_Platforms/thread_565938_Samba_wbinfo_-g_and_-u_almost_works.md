---
title: "Samba: wbinfo -g and -u almost works"
date: 2007-10-02
forum: Server Platforms
---

### Post by HermanAB on 2007-10-02
I've been chasing this problem for several days.

I can join a Windows 2003 Active Directory domain and 'wbinfo -t' returns OK.

However, 'wbinfo -g' returns only two groups then gives a failure message and 'wbinfo -u', doesn't return anything.

So, it almost works.

Can anyone give me a clue on where to look for this problem?

Cheers,

Herman

---

### Post by codmate on 2007-10-03
Do you have the winbind port open?
I think it's 445.

---

### Post by koenn on 2007-10-03
I joined a samba to an 2003 AD domain some weeks ago, and it seems to be working. 
Here are my notes, maybe you can see if you missed something
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

just a hunch : 
It is my understanding you need these in your smb.conf in order to be able to enumerate domain accounts and map unix UIDs and GID's to Microsoft SIDs
```
		# these are needed to get domain accounts to be recognized in unix
		idmap uid = 10000-20000
		idmap gid = 10000-20000
		winbind enum users = yes
		winbind enum groups = yes

```
Maybe you missed them ? there's a type somewhere ? or the uid and gid ranges for samba include uids and gids already in use on the Linux system ? ...

---

### Post by HermanAB on 2007-10-03
I managed to identify a previous version of my Active Directory server where everything works.  

So now I have three VMware images that I can toggle between:
a. Works purffectly
b. Doesn't work
c. A version of 'a' that I am trying to convert to 'b', in order to see what exactly screws things up.

It appears to be a security group definition that causes Samba Winbind to blow up, but I'm not sure what yet.

Cheers,

Herman

---

