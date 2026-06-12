---
title: "power/cog icon missing - Gnome Flashback"
date: 2016-04-29
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2016-04-29
2 installs of Yakkety. On Yakkety (1) installed gnome-session-flashback & lost the power/cog icon. And nothing I did would bring it back. On Yakkety (2) I installed gnome-session-flashback and it did not lose the power/cog icon.

I am now bugged trying to work out the difference between the 2 installs and why the usual commands do not fix this. I tried, in no particular order,

```
dconf reset -f /org/compiz/
setsid unity
unity
killall unity-panel-service
```

I have removed gnome-session-flashback & re-installed Unity 7. And in case anyone is wondering unity --replace is deprecated and does not do anything. The command to use is unity.

man unity & man unity-panel-service give only a little information that is useful for fixing stuff like this. From the little research I have done it seems that there are 2 panels where the icons go - system indicator panel & application indicator panel. I am guessing that system indicator panel is missing. The guides that I am finding go back to the early days of Unity. I am not seeing anything relating to what a user can do to fix stuff like this.

Oh, such is life.

Regards.

---

### Post by Smask on 2016-04-29
Indicator-session got uninstalled on my computers here...
Wonder if there is a connection between the two?



They run yakkety with proposed enabled and flashback installed.

---

### Post by grahammechanical on 2016-04-29
Thank you. It is indicator-session that is missing on the Yakkety without the power/cog icon. But now it really gets weird. 

> Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:

The following packages have unmet dependencies.  indicator-session : Depends: systemd-services E: Unable to correct problems, you have held broken packages.


apt-get install -f does not resolve the problem. I am beginning to wonder if this is nothing to do with Gnome Flashback but something to do with having proposed enabled or having used apt full-upgrade. Maybe the power cog icon went missing before I logged into Flashback session but I did not notice it. That last statement cannot be right as I used the power/cog menu to log out of Unity to log into Flashback. This is doing my head in.

It is not unknown for 2 installs of the development version to be out of phase with updates.

Regards

---

### Post by lonniehenry-gmail on 2016-04-29
I did update and upgrade via synaptic on a linux mate with proposed enabled and lost the cog also.  Indicator-session removed.  So it is in more than unity or gnome.

---

### Post by ventrical on 2016-04-29
Haven't tried it yet .. but.. 

```

sudo apt install unity-tweak-tool


```

---

### Post by ventrical on 2016-04-29
It is working ok here. (proposed on) Main Server.

---

### Post by ventrical on 2016-04-29
> **grahammechanical said:**
> Thank you. It is indicator-session that is missing on the Yakkety without the power/cog icon. But now it really gets weird. 



apt-get install -f does not resolve the problem. I am beginning to wonder if this is nothing to do with Gnome Flashback but something to do with having proposed enabled or having used apt full-upgrade.

Regards

I used 'full-upgrade' just for test and it worked ok.  I remember the bug/warning you are getting but I forget how to fix it. 

nVidia-340 just destroys gnome-desktop. Lucky I was able to recover.

regards..

---

### Post by ventrical on 2016-04-29
> **grahammechanical said:**
> Thank you. It is indicator-session that is missing on the Yakkety without the power/cog icon. But now it really gets weird. 



apt-get install -f does not resolve the problem. I am beginning to wonder if this is nothing to do with Gnome Flashback but something to do with having proposed enabled or having used apt full-upgrade. Maybe the power cog icon went missing before I logged into Flashback session but I did not notice it. That last statement cannot be right as I used the power/cog menu to log out of Unity to log into Flashback. This is doing my head in.

It is not unknown for 2 installs of the development version to be out of phase with updates.

Regards

```


sudo dpkg --configure -a


```

?

---

### Post by grahammechanical on 2016-04-29
Its late in the day/early in the morning. I am not feeling sociable. Sorry.

> graham@sdb7-Dev:~$ sudo dpkg --configure -a
[sudo] password for graham: 
graham@sdb7-Dev:~$ sudo apt install indicator-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 indicator-session : Depends: systemd-services
E: Unable to correct problems, you have held broken packages.

It cannot be loading with the upstart option can it? I will have to check.

Regards

---

### Post by ventrical on 2016-04-29
Looks as if installed by default here.

```

ventrical@ventrical-System-Product-Name:~$ sudo apt-get install indicator-session
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
indicator-session is already the newest version (12.10.5+16.04.20160412-0ubuntu2).

```

---

### Post by Smask on 2016-04-30
Reinstalled indicator-session again without any problems after I updated a bunch of packages. And no, I can't remember which, just took what I found in the queue.

---

### Post by grahammechanical on 2016-04-30
Yes, something in today's update fixed this problem. Most likely some systemd package. I have now been able to install indicator-session and a restart brings the power/cog icon back. I can log out of Unity & into Flashback and back again.

Now, for some tea with Yak's milk. 

Regards

---

