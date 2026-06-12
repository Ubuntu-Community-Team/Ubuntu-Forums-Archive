---
title: "Keeps asking for a reboot"
date: 2010-06-17
forum: Server Platforms
---

### Post by janaf on 2010-06-17
Pretty much a newb and this is my first post here. 
 
My server keeps displaying a message: "The computer needs to restart to finish installing updates. Please save your work before continuing" every time I log on. Last night I did four consecutive reboots but the message is still there. 
 
I log i remote with NX / Gnome. Synpatic shows "0 to install/update 0 to remove"
 
Is this normal? Does every single update need an independent reboot, so there is a queue to catch up with? Or is there some reboot flag that is not resetting properly after reboot?
 
I do not want to test rebooting too many time as server runs a web site that I need for my living..

---

### Post by CharlesA on 2010-06-17
It shouldn't be asking for a reboot after it's already rebooted. 

What version are you running?

---

### Post by janaf on 2010-06-17
I am running 9.10

---

### Post by CharlesA on 2010-06-17
Do you know what sort of update was applied before this started the happen?

If you login via SSH, does it say "System Restart Required" ?

---

### Post by janaf on 2010-06-17
It apeared early, when the machine was set up half a year ago. At that time there where several installs and updates, so a reebot seemed normal, but then the message never went away. So I really do not know where it originates.

Yes the message is there using SSH too: *** System restart required ***

---

### Post by CharlesA on 2010-06-17
Hrm. Normally that appears if there was a security update that required a reboot. I saw a thread that mentioned that clicking "reboot now" only restarted X, instead of rebooting the entire machine.

I guess you could check to see when it was last rebooted by using both these:

```
uptime
```
```
last
```

---

### Post by FuturePilot on 2010-06-17
Does this file exist? /var/run/reboot-required
It should disappear after rebooting but maybe for some reason it's not.

---

### Post by janaf on 2010-06-17
You are right, the machine has not actually been rebooted! No wonder it came up so fast :rolleyes:
 
Isn't this a bug? 
[LIST]
[*]either you should just see a warning about the needed full reboot
[*]or the button should really do the required reboot
[/LIST]I will do a full reboot later tonight when there are less visitors.............
 
Thanks for taking your time on this!

---

### Post by arrrghhh on 2010-06-17
Well, most don't put Gnome on a server... if you managed the server via SSH and rebooted via SSH, I guarantee you that this would not have happened :D

FYI, if you "need" Gnome on your server (really?) then just install ubuntu-desktop.  If you're installing Gnome, there's really no point in running the -server edition!  (Kinda defeats the purpose...)

---

### Post by linux-hack on 2010-06-17
> **arrrghhh said:**
> Well, most don't put Gnome on a server... if you managed the server via SSH and rebooted via SSH, I guarantee you that this would not have happened :D

FYI, if you "need" Gnome on your server (really?) then just install ubuntu-desktop.  If you're installing Gnome, there's really no point in running the -server edition!  (Kinda defeats the purpose...)

you could install a smaller and lighter desktop environment . like sfce :popcorn:

---

### Post by CharlesA on 2010-06-17
> **janaf said:**
> You are right, the machine has not actually been rebooted! No wonder it came up so fast :rolleyes:
 
Isn't this a bug? 
[LIST]
[*]either you should just see a warning about the needed full reboot
[*]or the button should really do the required reboot
[/LIST]I will do a full reboot later tonight when there are less visitors.............
 
Thanks for taking your time on this!

I wonder if it has to do with the way you were connecting (via FreeNX) but I don't know for sure.

> **arrrghhh said:**
> Well, most don't put Gnome on a server... if you managed the server via SSH and rebooted via SSH, I guarantee you that this would not have happened :D

FYI, if you "need" Gnome on your server (really?) then just install ubuntu-desktop.  If you're installing Gnome, there's really no point in running the -server edition!  (Kinda defeats the purpose...)

Indeed. I'm just forwarding X over SSH (I don't even have a GUI installed, except for the dependencies for VBox) when/if I need to configure stuff in VirtualBox. It's much easier to do via GUI than CLI.

---

### Post by arrrghhh on 2010-06-17
> **boogy9 said:**
> you could install a smaller and lighter desktop environment . like sfce :popcorn:

No, still not recommended.  I sometimes do what CharlesA recommends, forwarding X thru SSH... but for the most part CLI only.  If you want a DE, install ubuntu-desktop, NOT server!!

And I think you mean XFCE, which really isn't that light anymore...

---

### Post by pricetech on 2010-06-17
I've noticed the same thing using NX to my mirror, as well as other boxen I tend.  You can go to the terminal and use the shutdown command to set up a reboot in one minute, which is more than enough time to close out your NX session.

If I called it a bug, I'd blame it on NX, not Ubuntu.

---

### Post by CharlesA on 2010-06-17
> **arrrghhh said:**
> No, still not recommended.  I sometimes do what CharlesA recommends, forwarding X thru SSH... but for the most part CLI only.  If you want a DE, install ubuntu-desktop, NOT server!!


Agreed. I do most of my stuff CLI. I think I've used the VirtualBox GUI a couple times when setting up new VMs, but for the most part, it's just CLI.

---

