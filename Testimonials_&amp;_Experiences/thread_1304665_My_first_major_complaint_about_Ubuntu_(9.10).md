---
title: "My first major complaint about Ubuntu (9.10)"
date: 2009-10-29
forum: Testimonials &amp; Experiences
---

### Post by HappyFeet on 2009-10-29
I feel sorry for those people that need to use nvidia-settings to change anything video related. When you go to save the file to xorg.conf, it says "failed to parse to /etc/X11/xorg.conf". You need to restart nvidia-settings, and then it will be OK. But, upon reboot, all settings are lost, and you have to re-do it again. This also happens in kubuntu.

**This is a well known bug that was reported during the alpha stages of karmic**, (I submitted it also) and has had plenty of time to be fixed before karmic became final. 

Believe it or not, there are a lot of nvidia users that have dual monitors, and will be miffed by this. While I understand that they can't catch all bugs before release, something of this magnitude going unfixed, is unacceptable. 

I also realize that they will probably come out with a fix via updates, but it should not be there to begin with. Thank god 9.04 is still running great.

And btw, I'm not leaving ubuntu, just venting a little. I'm off to launchpad to give them a piece of my mind.

---

### Post by Antman on 2009-10-29
This issue happens in some other distros as well. The issue is that nvidia-settings needs to be run as root in order to save the file to /etc/X11/xorg.conf.

The work-around is to open a terminal and run:
**sudo nvidia-settings**

This will launch nvidia-settings with root privileges and allow you to save settings.

I do agree that Ubuntu should auto-prompt the user for the root password when launching this from the gui since most users would not know to launch via a terminal with sudo.

---

### Post by HappyFeet on 2009-10-29
> **Antman said:**
> This issue happens in some other distros as well. The issue is that nvidia-settings needs to be run as root in order to save the file to /etc/X11/xorg.conf.

The work-around is to open a terminal and run:
**sudo nvidia-settings**

This will launch nvidia-settings with root privileges and allow you to save settings.

I'm not new. I did run as root. Many other people are having the same issues. Another bug (even bigger) is that nvidia-settings crashes upon saving settings.  ](*,)

---

### Post by ukripper on 2009-10-29
> **HappyFeet said:**
> I'm not new. I did run as root. Many other people are having the same issues. Another bug (even bigger) is that nvidia-settings crashes upon saving settings.  ](*,)

That's not good for starters. i haven't installed 9.10 yet but will soon be offering to my clients soon. Thanks for pointing it out on here.

---

### Post by Antman on 2009-10-29
> **HappyFeet said:**
> I'm not new. I did run as root. Many other people are having the same issues. Another bug (even bigger) is that nvidia-settings crashes upon saving settings.  ](*,)

Sorry, I didn't mean to imply you were a newbie. I was just making the solution/workaround clear for anyone else that reads this thread. ;)

This issue has been a problem in previous versions of Ubuntu as well. At this rate, it may never get fixed.:-\"

*Edit: I meant the sudo nvidia-settings issue has been a problem for awhile, not the nvidia-settings crashing.*

---

### Post by gjoellee on 2009-10-29
> **HappyFeet said:**
> I'm not new. I did run as root. Many other people are having the same issues. Another bug (even bigger) is that nvidia-settings crashes upon saving settings.  ](*,)

This is a bug with the Nvidia driver and not Ubuntu. It can be solved by deleting the xorg.conf

```
sudo rm /etc/X11/xorg.conf
```

Mod Note: It is best to copy and paste the above (and below) command.

Now go save again. You will probable not be able to save your settings yet, but you are able to see the xorg.conf it want to save. Create a new xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

Now copy the xorg.conf the Nvidia program wants to save, and paste it into the Text Editor window and save. Restart Xorg to see the changes. You can restart Xorg by in example restarting your computer.

---

### Post by Jazzy_Jeff on 2009-10-29
I think I am going to wait a week or two to install. Give them a chance to work the bugs out.

---

### Post by gjoellee on 2009-10-29
> **Jazzy_Jeff said:**
> I think I am going to wait a week or two to install. Give them a chance to work the bugs out.

As already said. The bug is not with Ubuntu but with the Nvidia driver (this happens on other distributions as well). You will have to ask Nvidia about solving that problem I guess. Nevertheless, that bug has been here for at least a year, and it probably wont get fixed withing the next year either.

---

### Post by HappyFeet on 2009-10-29
> **gjoellee said:**
> This is a bug with the Nvidia driver and not Ubuntu. It can be solved by deleting the xorg.conf

```
sudo rm /etc/X11/xorg.conf
```

Now go save again. You will probable not be able to save your settings yet, but you are able to see the xorg.conf it want to save. Create a new xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

Now copy the xorg.conf the Nvidia program wants to save, and paste it into the Text Editor window and save. Restart Xorg to see the changes. You can restart Xorg by in example restarting your computer.

Thanks for the fix, as it worked. I still find it strange that 8.10 and 9.04 were fine. Oh well. I will pass on the fix to those who need it. Cheers, and I'm going to ask that this thread be closed.

---

### Post by solwic on 2009-10-29
> **Jazzy_Jeff said:**
> I think I am going to wait a week or two to install. Give them a chance to work the bugs out.

Ditto.  I have the ISO, and I'm getting ready to boot it from my USB stick in LiveCD mode, but I'm not installing for a couple of weeks.  They never get all the bugs in time.  

> **gjoellee said:**
> As already said. The bug is not with Ubuntu but with the Nvidia driver (this happens on other distributions as well). You will have to ask Nvidia about solving that problem I guess. Nevertheless, that bug has been here for at least a year, and it probably wont get fixed withing the next year either.

That may be true, but I've noticed a tendency on these forums to blame something else when really it's just a bug in Ubuntu.  I'm not saying that's the case here, just that I've seen it enough to justify waiting for Ubuntu to start releasing updates, just in case.  

:biggrin:

---

### Post by Elfy on 2009-10-29
closed at OP request

---

