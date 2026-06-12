---
title: "Hardening Ubuntu: User Accounts"
date: 2008-11-19
forum: Security
---

### Post by talen.quickblade on 2008-11-19
Here I sit looking at the /etc/shadow file wondering where I can find information about some obviously extraneous users. Can anyone point me in the right direction to finding the reasons these users exist on the default installation and which may leave me in a pickle if I go removing them. I've looked around, but seems either I am looking in the wrong place, or for the wrong thing.

```
root:!:14197:0:99999:7::1:
daemon:*:14196:0:99999:7:::
bin:*:14196:0:99999:7:::
sys:*:14196:0:99999:7:::
sync:*:14196:0:99999:7:::
games:*:14196:0:99999:7:::
man:*:14196:0:99999:7:::
lp:*:14196:0:99999:7:::
mail:*:14196:0:99999:7:::
news:*:14196:0:99999:7:::
uucp:*:14196:0:99999:7:::
proxy:*:14196:0:99999:7:::
www-data:*:14196:0:99999:7:::
backup:*:14196:0:99999:7:::
list:*:14196:0:99999:7:::
irc:*:14196:0:99999:7:::
gnats:*:14196:0:99999:7:::
nobody:*:14196:0:99999:7:::
libuuid:!:14196:0:99999:7:::
dhcp:*:14196:0:99999:7:::
syslog:*:14196:0:99999:7:::
klog:*:14196:0:99999:7:::
```

---

### Post by hyper_ch on 2008-11-20
as you may know Linux is by nature a true multiuser system. So seperation of privileges is one of the key points of it's security design.

By default nothing should have more access rights than it really, really requires.

Because of this mindset all the daemons (services) [at least most of them] run under their own user. So the worst thing that can happen is that an individual service may get corrupted but not the whole system.

On windows you have something completely different. (Internet) Explorer is so tightly in the core system that when you find a weakness in it, you can control the whole computer.

---

### Post by scorp123 on 2008-11-20
> **talen.quickblade said:**
> Here I sit looking at the /etc/shadow file wondering where I can find information about some obviously extraneous users.  [http://ubuntuforums.org/showthread.php?p=5606071#post5606071](http://ubuntuforums.org/showthread.php?p=5606071#post5606071)

---

### Post by talen.quickblade on 2008-11-21
Good stuff for sure. Thanks. Next question how can I determine why some of these users exist (irc and games for instance) This is a very vanilla ubuntu server installed, and I certainly have not installed an irc client or server. I'm sure I could safely remove these, though would like to know why someone thought it was a good idea to go ahead and add them.

---

### Post by stmurray on 2008-11-21
The idea is that the risk is minimal.  If you look at those entries you see that the password is either "*" or "!".  That means you could never authenticate as those users.   

The password in the /etc/shadow is actually a hash of the user's password and all authentication mechanisms will hash the user's input to see if that hash matches what is stored in the /etc/shadow files.  Since no password can ever hash to * or !, then no one can ever authenticate using those accounts.  None of those users can ever login without changing the /etc/shadow file.  And if an attacker can do that, then it is game over anyway.  

I am a fairly paranoid type and I just leave them be.

---

### Post by bodhi.zazen on 2008-11-21
> **talen.quickblade said:**
> Here I sit looking at the /etc/shadow file wondering where I can find information about some obviously extraneous users. Can anyone point me in the right direction to finding the reasons these users exist on the default installation and which may leave me in a pickle if I go removing them. 

As you gain experience most of these accounts will make more sense to you. I looked recently (google) and could not find a reference to all these users and what they do.

Basically they are the daemons on your system, mail is your mail system, etc.

See the other comments re security. I think it is safe to say, if you do not know what they are , leave them alone.

I suggest you look at your services and stop (disable) any you do not use and look here :

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

Of course that is some heavy reading, so you may want to start with the stick at the top of this forum.

---

