---
title: "make it easier to reconfigure x for noobs"
date: 2009-07-13
forum: The Cafe
---

### Post by AndThenWhat on 2009-07-13
I made a Ubuntu Brainstorm idea for creating a GUI (Graphical User Interface) to help Ubuntu 'noobs' (like the ones we see in Absolute Beginner Talk) reconfigure the x server (sudo dpkg-reconfigure xserver-xorg) without having to go into a Terminal on their first day using Ubuntu.

Please vote if you have a Brainstorm account and think this would be helpful:

[http://brainstorm.ubuntu.com/idea/20650/](http://brainstorm.ubuntu.com/idea/20650/)

---

### Post by dragos240 on 2009-07-13
why not tell them to:

Xorg -configure && cp ~/xorg.conf.new /etc/X11/xorg.conf. Easy!

---

### Post by AndThenWhat on 2009-07-13
I just think having a GUI would be easier for someone's grandma or any people who are used to Windows giving them GUI for everything. Using the Terminal is something that IMO is a good skill to have but needs to be developed over time, not right away.

---

### Post by SunnyRabbiera on 2009-07-13
There once was dis[playconfig gtk in the past but its not there anymore.
Getting rid of it without a replacement was a real bad idea...

---

### Post by Skripka on 2009-07-13
> **dragos240 said:**
> why not tell them to:

Xorg -configure && cp ~/xorg.conf.new /etc/X11/xorg.conf. Easy!

So long as you run that line as root, it is easy ;)

---

### Post by monsterstack on 2009-07-13
It doesn't need to be a proper GTK application. You can do something similar with Zenity ([COLOR="Red"]warning[/COLOR], untested code):

```
#!/bin/bash
# Reconfigure X.

if [[ $(whoami) != "root" ]]; then
    zenity --warning --title "Not root user." \
    --text "You are not the superuser. Sorry!"
    exit 9
else
    echo "You're running this as root. Good."; fi
		

zenity --question --title "Reconfigure X." \
        --text "Do you want to reconfigure your graphics settings?"
    
        if [[ $? == 0 ]] ; then
            cp /etc/X11/xorg.conf{,.$(date +'%F-%H%M%S').bak}
            dpkg-reconfigure xserver-xorg
            zenity --info --title "Success." \
            --text "Graphics reconfigured. Changes will take effect\nnext time you log in."
        else
            exit 9; fi

```

Any good?

---

### Post by DoktorSeven on 2009-07-13
> **dragos240 said:**
> why not tell them to:

Xorg -configure && cp ~/xorg.conf.new /etc/X11/xorg.conf. Easy!

Because this doesn't create a usable xorg.conf for many people.  Wrong/unwanted resolution, bad refresh rate for CRTs, unusable 3d for most ATi users, etc.

Sadly, configuring xorg to work with many configurations means getting your hands dirty editing it, not relying on the automatic configuration.

---

### Post by JDShu on 2009-07-13
As a semi-noob, I've always wondered why such a program did not already exist. Every day, the support forums seem to have somebody complaining that they can't set the display resolution to what they want, though ti looked to me that adding a line to xorg.conf was all that was needed.

---

### Post by chris4585 on 2009-07-13
You know there is already a automatic way of doing this? It requires a reboot but who cares?  Reboot into recovery mode, look for the option to fix xorg or something, tada!

---

### Post by johnraff on 2009-07-14
I haven't used either of them, but you might want to check out:
lxrandr
grandr
-both in the Jaunty repositories.

---

