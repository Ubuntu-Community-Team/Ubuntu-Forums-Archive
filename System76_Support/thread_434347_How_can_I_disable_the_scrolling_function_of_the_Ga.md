---
title: "How can I disable the scrolling function of the Gazelle touch pad?"
date: 2007-05-05
forum: System76 Support
---

### Post by aay on 2007-05-05
Does anyone know how to disable the scroll wheel thingy on the touch pad of the Gazelle?  That thing drives me crazy.

Adam

---

### Post by aay on 2007-05-05
Well I don't know if this is the proper way, but I experimented and figured out how to turn this awful thing off.

sudo <favorite text editor> /etc/X11/xorg.conf

Find the following section:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"

Add this line:

        Option          "VertScrollDelta"       "0"

Save.

You may just have to log out and log back in, but after logging out I also switched to a virtual terminal and did: sudo /etc/init.d/gdm restart

Now no more vertical scrolling!

Adam

---

### Post by IgnacioMiller on 2007-05-06
You might find [this]("http://ubuntuforums.org/showthread.php?t=434625") useful as well. :)

---

### Post by aay on 2007-05-06
> **IgnacioMiller said:**
> You might find [this]("http://ubuntuforums.org/showthread.php?t=434625") useful as well. :)

Cool.

Thanks.

Adam

---

