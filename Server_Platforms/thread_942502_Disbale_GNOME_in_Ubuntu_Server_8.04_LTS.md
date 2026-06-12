---
title: "Disbale GNOME in Ubuntu Server 8.04 LTS"
date: 2008-10-09
forum: Server Platforms
---

### Post by benoybose on 2008-10-09
I installed GNOME Desktop Environment in Ubuntu Server 8.04 LTS. Now GNOME starts as soon as user boot in to the machine. What can I do to disable GNOME in startup and will be launched only when is it required.

What can I do to load GNOME manually through command line......?

Thanks!

---

### Post by benoybose on 2008-10-09
Is there anyway to disbale the GNOME on starup and load it manually through command line, whenever it is needed....?

---

### Post by lykwydchykyn on 2008-10-09
First, you need to make it so that gdm does not run on boot:

```

cd /etc/rc2.d/
sudo mv S99gdm K99gdm

```

Next, when you want GNOME, just log in and run "startx"

---

### Post by windependence on 2008-10-09
You can prevent automatic running of the GUI when you boot your debian machine by disabling your login manager be it KDM, GDM or XDM from running at boot time. To disable the login manager from automatically running at boot up, run the following command as root

```
sudo update-rc.d -f gdm remove

```

Replace gdm with kdm or xdm if they are what you use.

To start X manually, you would then have to login at the command prompt and enter the command 

```
startx
```

To reset your login manager so that it runs at boot up, do

```
sudo update-rc.d -f gdm defaults
```

-Tim

---

### Post by lazyart on 2008-10-09
Now THAT'S a nice common ground for those who want the GUI to set up and tinker with things.  Otherwise the GUI should be off, off, off!

---

### Post by AgentZ86 on 2008-10-12
> **lazyart said:**
> Now THAT'S a nice common ground for those who want the GUI to set up and tinker with things.  Otherwise the GUI should be off, off, off!

Why should GUI be turned off.

I currently use SME but am considering changing to Ubuntu Server and was considering putting a GUI on it.

Is there any problem with using synaptic and Gnome to install things just like I would on my desktop ?

Please advise

---

### Post by benoybose on 2008-10-17
> **windependence said:**
> You can prevent automatic running of the GUI when you boot your debian machine by disabling your login manager be it KDM, GDM or XDM from running at boot time. To disable the login manager from automatically running at boot up, run the following command as root

```
sudo update-rc.d -f gdm remove

```

Replace gdm with kdm or xdm if they are what you use.

To start X manually, you would then have to login at the command prompt and enter the command 

```
startx
```

To reset your login manager so that it runs at boot up, do

```
sudo update-rc.d -f gdm defaults
```

-Tim


Ok. Thank you dude. What to do if we wish to turn off the GNOME at Runtime........???

---

### Post by lykwydchykyn on 2008-10-17
You mean after it's running already?
```

invoke-rc.d gdm stop

```

---

### Post by MystaMax on 2008-10-17
I've asked a [similar question]("http://ubuntuforums.org/showthread.php?t=682151") in the past, and used a different solution. It involves installing additional packages (sysv-rc-conf). I now use sysv-rc-conf to manage runlevels. 

I found a [post]("http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html#comment-38086") on the net stating that update-rc was for package maintainers to install startup scripts. What does everyone else think?

---

### Post by lykwydchykyn on 2008-10-17
I don't know that it really matters what you use, the whole rc script system is really pretty simple, I don't see how you can go wrong.  I usually don't even mess with the commands myself, I just edit the symlinks.  

If someone knows anything special that sysv-rc-conf does that update-rc.d or just editing symlinks doesn't do, I'd like to know.

I'll have to check out sysv-rc-conf, if the syntax is nicer I'll start recommending it to new users.

---

### Post by MystaMax on 2008-10-17
I hope we're not polluting the thread w/ side discussion:

sysv-rc-conf actually has a CLI gui, where you can check/uncheck services from starting. I've attached a screenshot for reference:

---

