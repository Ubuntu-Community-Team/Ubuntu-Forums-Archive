---
title: "Proftpd not starting after fresh install"
date: 2007-02-28
forum: Server Platforms
---

### Post by nucklebone on 2007-02-28
After running Synaptic Package Manager to install 'Proftpd' I get this error as proftpd tries to start up:

- IPv6 getaddrinfo 'ubuntubox' error: Name or service not known

Ubuntubox is the name of the machine used for this ftp server on the network.
Any thoughts?


nucklebone

---

### Post by cd-r80 on 2007-02-28
Same error here, but my PROFTPD is working. But I don't use IPv6. Did you try it? I mean login your server.

---

### Post by nucklebone on 2007-02-28
odd. i did try it earlier, but i guess i wasn't patient enough. it does in fact run, but it runs like a sick dog. to be fair, once connected it runs great. it's just the connecting part that is pitifully slow.

thanks.

---

### Post by nucklebone on 2007-02-28
so... ftp works (permission issues to put files though), but sftp give an authentication error. auth logs say:

[COLOR="Red"]Feb 28 11:03:25 ubuntubox sshd[7385]: Failed password for *user* from *xxx.xxx.xxx.xxx* port 49227 ssh2[/COLOR]

i'm trying from a couple of different machines so i'm pretty sure i'm using the right password.

---

### Post by madmaxxx on 2007-02-28
> - IPv6 getaddrinfo 'ubuntubox' error: Name or service not known

[COLOR="Blue"]**same problem...  any help.. please..**[/COLOR]

---

### Post by nucklebone on 2007-02-28
like cd-r80 says, it actually does work. but not right.

if you wait long enough ftp will work, but sftp or ftp over ssh does not work. at all.

installing proftpd from apt-get or Synaptic Package Manager results in this error after install:
[COLOR="Red"]- IPv6 getaddrinfo 'ubuntubox' error: Name or service not known[/COLOR]

BUT it works, just very slow. And if you try to sftp it just doesn't work and you get an authentication error and some similar error in your auth log:
[COLOR="Red"]Feb 28 11:03:25 ubuntubox sshd[7385]: Failed password for *user* from *xxx.xxx.xxx.xxx* port 49227 ssh2[/COLOR]

this is a straight install of Ubuntu. no fancy repositories or stuff like that. ftp and ssh worked great on this same piece of hardware before i re-installed the system. 

anyone have an idea why it's rejecting my password? and yes, i am certain it's correct.

nucklebone

---

### Post by dcaponegro on 2007-03-05
i think it has to do with ipv6 not being enabled in the kernel. ftp should still work fine. At least it does for me. I get the same error.

---

### Post by homerj742 on 2007-03-07
I get the same error, and I'm getting authentication error, or login failed. I'm VERY sure the username and password is correct!

---

### Post by schmidi2 on 2007-03-22
The solution can be found here:

[http://www.linuxquestions.org/questions/showthread.php?t=534121](http://www.linuxquestions.org/questions/showthread.php?t=534121)
(last post)

---
Since you're using also ipv6, then add a line in /etc/hosts like this:
::1             localhost hobbes.malandaynet hobbes
---

---

