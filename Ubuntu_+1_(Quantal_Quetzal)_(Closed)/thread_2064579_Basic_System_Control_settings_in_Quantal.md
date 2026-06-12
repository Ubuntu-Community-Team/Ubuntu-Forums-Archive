---
title: "Basic System Control settings in Quantal"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by scradock on 2012-09-29
As some of you may know, I've been using ubuntu since Dapper Drake or somewhere back then. I also have spent a considerable amount of time and effort getting to know the ways we can control stuff to make our machines behave and look as we choose.

But now I AM STUMPED! I am asking for some elementary help, just as if I were a complete newbie.

Would someone PLEASE tell me how I can set the following:

1) For some reason, Quantal is starting with a greeter, asking me for my password, instead of automatically logging me in as I have in earlier installs. How do I chaneg this setting? There is nothing in System Settings about log-in, or the greeter; the gsettings keys for com.canonical.unity-greeter don't include the autologin preference.

2) Where do I change the startup programs? One of the programs I have been using has been removed, but its autostart setting remains in the system, which confuses the start-up process.

3) While I'm at it, what are other people using for instant messaging? I used aMSN until that was removed, when I switched to emesene, which has now also been removed. Empathy will do the messaging, but I can't find how to have it tell me when I have an email in hotmail, and log me in when I wish to read it.

Any helpful hints gratefully received......

---

### Post by stinkeye on 2012-09-29
#1 user accounts

#2 Run the two commands to show all in startup applications 
```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

#3 I don't use

---

### Post by Frogs Hair on 2012-09-29
3. Emesene and Pidgin are in the 12.10 software center. I have the Gnome Shell installed and Empathy is installed by default.

---

### Post by scradock on 2012-09-29
Thanks guys...

---

### Post by scradock on 2012-09-30
OK - another one - the screen keeps blanking out on me if I leave the machine idle. 

All settings under "Brightness & Lock" and "Power" say to never blank screen. I don't see ANY settings relating to screensavers any more.

Any ideas?

---

### Post by floydsp on 2012-10-01
[http://ubuntuforums.org/showthread.php?t=2059551&highlight=floydsp](http://ubuntuforums.org/showthread.php?t=2059551&highlight=floydsp)

This solved my problem

floydsp

---

### Post by philinux on 2012-10-01
> **scradock said:**
> OK - another one - the screen keeps blanking out on me if I leave the machine idle. 

All settings under "Brightness & Lock" and "Power" say to never blank screen. I don't see ANY settings relating to screensavers any more.

Any ideas?

Odd one that. I have it set to never and it stays on.

---

### Post by grahammechanical on 2012-10-01
I have 3 Quantal installs and they are set to never blank the screen when it is idle and Lock is set to Off. And it does what it should do.

We do not have screen savers any more. So, there are no adjustment settings for screen savers. Some have found away around this for 12.04. Those methods might work on 12.10.

I see no point in have a screen saver. On a portable device it will use up battery power. Remember, the aim for Ubuntu is not only to work on all kinds of computer devices but to be unified in look and function.

Another thing. It seems to me that Canonical has a clear definition of what its programming responsibilities are and anything not covered by that definition is left to the Ubuntu community to develop. There is nothing to stop the community from adding what Canonical has left out.

Regards.

**Correction**

This Quantal install that I am using just blanked the screen even though it is set to never. So, there is a bug here.

---

### Post by philinux on 2012-10-01
Screen turning off is happening to my laptop but not the desktop. 

I've not had lappy on for a bit and not really paid attention. Just investigating the lappy now.

[edit] ok sorted. It was the dim screen to save power checkbox. Unticked it and the screen stays on.

---

### Post by scradock on 2012-10-01
> **philinux said:**
> Screen turning off is happening to my laptop but not the desktop. 

I've not had lappy on for a bit and not really paid attention. Just investigating the lappy now.

[edit] ok sorted. It was the dim screen to save power checkbox. Unticked it and the screen stays on.

That sounds odd - "dim screen" is not the same as "blank screen"....

---

