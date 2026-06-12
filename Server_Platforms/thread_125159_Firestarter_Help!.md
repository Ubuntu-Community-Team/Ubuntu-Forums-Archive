---
title: "Firestarter Help!"
date: 2006-02-03
forum: Server Platforms
---

### Post by Leo_01 on 2006-02-03
> <username> ALL= NOPASSWD: /usr/bin/firestarter

i found this code on firestarter website to allow firestarter to be runned without any root access...
i got a feeling that it is done diffrently in ubuntu...
is that true?
btw...
if i were to follow that the guide says... at which part of sudoers file do i insert to?

---

### Post by dresnu on 2006-02-03
[QUOTE=Leo_01]
i got a feeling that it is done diffrently in ubuntu...
[/QUOTE]

Well I did it that way and it works :D. Just add that line at the end of /etc/sudoers.

---

### Post by Leo_01 on 2006-02-03
ok...
tks.
will try that...

---

### Post by towsonu2003 on 2006-02-03
I wouldn't recommend using firestarter without root privileges (as a normal user). Basically, firestarter configures iptables and by giving the non-root permission away, you are basically opening up your iptables to local and remote exploits, without the need for those exploits to escalate their privileges to root. Well, to be brief, anything that involves a system tweak has to be done by root and root only. 

Also, you do not need firestarter to be run by non root user. run it once as root (with gksudo or from Applications>System Tools), configure it via its wizard and that's all. you won't need to run it ever except to maybe see the logs and to open / close ports upon your needs. 

even if firestarter is not visible in gnome, it is running in the background. to check ```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by Leo_01 on 2006-02-04
Run it once as root?
:confused: 
I am currently the only user in ubuntu...
so are you trying to say that it runs even without typing "sudo firestarter" ?

---

### Post by towsonu2003 on 2006-02-04
[QUOTE=Leo_01]Run it once as root?
:confused: 
[/QUOTE]
sorry for the confusion. run it as root = use sudo / gksudo. 
When you use sudo, you are running a program as root (more exactly, with root privileges).

Root is the account name of the system administrator. It's basically the god of your system. As the root account is disabled by default in ubuntu for security reasons, you use sudo to gain root privileges.

More info here: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

One more important info: while using commands with sudo, make sure you check your command (for mistakes in typing etc). Root is the god of the system, so it has the power to trash the installation.......

---

### Post by Leo_01 on 2006-02-04
Yeah ok...
so does it means thet firestarter runs even without typing any "sudo firestarter" commands? 
I tried the status command and it seems to be running...
so i guess i dun have to "sudo firestarter" to load the firewall but i need to "sudo firestarter" only if i want to change the firewall's config?

---

### Post by towsonu2003 on 2006-02-04
[QUOTE=Leo_01]
so does it means thet firestarter runs even without typing any "sudo firestarter" commands? [/quote]once configured tru the wizard, yes. 
[QUOTE=Leo_01]
so i guess i dun have to "sudo firestarter" to load the firewall but i need to "sudo firestarter" only if i want to change the firewall's config?[/QUOTE]
yep :)

---

### Post by Leo_01 on 2006-02-04
ah damn.
why don't i change to ubuntu earlier!
wow!
even the firewall is fast!

---

