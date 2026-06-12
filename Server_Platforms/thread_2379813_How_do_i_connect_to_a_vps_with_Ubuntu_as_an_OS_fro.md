---
title: "How do i connect to a vps with Ubuntu as an OS from a windows machine?"
date: 2017-12-10
forum: Server Platforms
---

### Post by rius2 on 2017-12-10
[COLOR=#111111][FONT=Ubuntu]So i bought a VPS, that has a Ubuntu OS on it, and i want to connect to it from my Windows pc. I did connect to it PuTTy and installed xrdp, i installed several desktops(gnome, xubuntu, as i am trying to connect to this machine 3 days now). and i followed several tutorials, and i tried several answers given to problems similar to mine, but nothing worked, like this one: [enter link description here]("https://askubuntu.com/questions/803553/sesman-xvnc-doesnt-connect-over-xrdp")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and this one: [enter link description here]("https://superuser.com/questions/789633/unable-to-login-via-xrdp%22from%20superuser%22")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I use Rdc from windows and connect to the linux machine with the provided ip. I get to xrdp login where i can select several connection types. [enter image description here]("https://i.stack.imgur.com/xOPKQ.jpg")And depending on what connection i tri i get all types of error[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]i also installet a tightvncserver on the linux machine as instructed in anoter tutorial[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]these are the errors on each typ of connection i try:[/FONT][/COLOR]

[LIST]
[*]sesman-Xvnc option i get a message :connecting to sesman ip 127.0.0.1 port 3350 and it gets stuck on it
[*]vnc-any : error problem connecting
[*]sesman-any: connecting to sesman ip 127.0.0.1 port 3350 and it gets stuck on it
[*]rdp-any: no error, just a black screen
[*]freerdp-any: error libxrdpfreerdp1.so specified in xrdp.ini
[*]sesman-X11rdp: connecting to sesman ip 127.0.0.1 port 3350 and it gets stuck on it
[/LIST]

---

### Post by darkod on 2017-12-10
Installing so many different GUI connection methods is definitely not recommended on a VPS that is public on the internet. What is wrong with using putty and command line ssh session to administer your VPS? Most linux servers are administered by command line.

I recommend to remove all GUI packages and connection software, and use putty and ssh only.

---

### Post by rius2 on 2017-12-10
Because i need a GUI for what i am doing on the vps.

---

### Post by QIII on 2017-12-10
Because of the number of different desktops you installed and the fact that you did not specify all of the tutorials you looked at and what you did:

Might I suggest that you ask your VPS provider to re-provision your server with a fresh installation and then return here prior to making a lot of changes that will leave the machine in an uknown state?

Right now you have a mishmash that likely presents a security nightmare.  If you really do need a GUI environment, I suggest setting up some containers to keep your VPS itself secure.

---

