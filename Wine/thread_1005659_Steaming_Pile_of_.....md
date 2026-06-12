---
title: "Steaming Pile of ...."
date: 2008-12-08
forum: Wine
---

### Post by OrbJinzo on 2008-12-08
Well you get the picture another Steam problem.

ok I have installed steam and got all the games to run and work but I cannot get multiplayer running for the life of me. I have deleted the ClientRegistery.blob and to no avail. I dont not have firestarter nor any other firewall software running. 

my config is

Xubuntu 8.10
wine 1.1.10 lastest

---

### Post by toasty_ghosty on 2008-12-08
Could you provide some more info such as how did you install it, what method(wine doors etc)? I'm sure more people will help with some more info.

---

### Post by OrbJinzo on 2008-12-08
I installed via just normal wine with the msi executable. I didnt use any frontends just plain wine

---

### Post by toasty_ghosty on 2008-12-08
Just a few things to limit this problem. Some may not be related, but the least amount of potential issues the better:

> I dont not have firestarter nor any other firewall software running. 

Your system is still running iptables most likely. Firestarter is just a GUI to allow easier control over firewalls. I ran Counter Strike with Firestarter and didn't have any blocked accesses or any issues. So I do not think that the firewall would be the issue.

Also, are there servers visible, or are you crashing every time you connect?

Lastly, and this might sound weird, but I would change your audio driver to OSS. I have had weird issues using other drivers. The whole game play experience seems better with OSS...

---

### Post by OrbJinzo on 2008-12-09
I tried the changing the sound driver to oss and to no avail.

---

### Post by toasty_ghosty on 2008-12-09
I'm really racking my brain to think what would cause this. But

> Also, are there servers visible, or are you crashing every time you connect?

Knowing this would help limit the issues. Also, can you create your own server in Counter Strike? Or what about a single player game such as Half Life?

---

### Post by OrbJinzo on 2008-12-09
I can create a single player game just fine. basically what it does it tries to query the master servera and after about 3 minutes it times out and same thing happens when I refresh

---

### Post by OrbJinzo on 2008-12-10
up to the top with yas

---

