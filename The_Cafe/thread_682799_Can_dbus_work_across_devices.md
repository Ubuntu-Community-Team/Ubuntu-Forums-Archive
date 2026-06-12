---
title: "Can dbus work across devices?"
date: 2008-01-30
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-01-30
It seems that the holy grail over the next few years is going to be integration between handheld devices and "home base" computers. Linux already has a great (though so far rather unnoticed) foothold, since Linux-based platforms are often very similar regardless of what they are built for. For example, it is amazing how much software there is on a device like the Nokia N810 or Neo 1973 that I use routinely in Ubuntu! That is made quite easy thanks to a lot of common libraries which are open and thus easily moved to anywhere, such as the fantastic GUI toolkits (like GTK) that have become standard on Linux desktops. Windows Mobile or the iPhone do not - and can not - come anywhere close to the portability of Linux software.

Another thing that particularly pleases me is D-Bus, which lets us integrate applications in a way practically unparallelled by the competition. Granted, there can be a standard library for every task under the sun instead, but having a few conventional messages that get bounced around with D-Bus is much easier to implement.

Something I have been wondering about, though, is whether D-Bus's handiness can be expanded beyond just the local computer. Will we some day see D-Bus allowing us to transparently integrate devices linked via Bluetooth or that are connected to the same LAN?
I realize there is some tricky stuff with channels for each user, but there must be some brains pouring in to the idea.
The possibilities of such a system are dream-like. For example, having a device on the network display libnotify's popups from another! Oh boy!
(The more cool stuff, while awesome, is so cool that it's probably really difficult, so I won't let my hopes up for now).

Does this already exist in some form, by chance?

---

