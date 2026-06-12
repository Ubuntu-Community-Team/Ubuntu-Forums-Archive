---
title: "System76 Drivers"
date: 2006-12-28
forum: System76 Support
---

### Post by Pobega on 2006-12-28
I'm just wondering, if I switch from Ubuntu to Xubuntu will the System76 drivers still work? And by that I mean the 1280x800 resolution, and anything else that is installed.

---

### Post by crichell on 2006-12-28
Yes - the driver will work under Xubuntu.  We don't test the driver thoroughly on Xubuntu but we're happy to fix any bugs you may come across.

---

### Post by Pobega on 2006-12-29
Well I made the switch over to Xubuntu, and everything seems to be working fine. My resolution is back to 1280x800, touchpad scrolling works, but I do have one problem. I can't connect to my Wireless network! I installed network-manager and network-manager-gnome and ran nm-applet, but even though it tells me I'm connected (98% strength) I'm still getting no internet connection.

---

### Post by maxamillion on 2006-12-29
open a terminal and type
```
sudo dhclient
```

That should fix it, I keep hearing about this problem in the irc channels for xubuntu and don't know why the ip address isn't resolved automatically .... if that doesn't work post back.

---

### Post by Pobega on 2006-12-29
Follow-Up Question:

Would these drivers also work on Debian? I have a friend who's getting a System76 laptop, and since he has previous Linux experience he wants to install Debian. So since he isn't registered here, I'm asking for him.

---

### Post by crichell on 2006-12-29
The driver won't work on Debian; however, it is open source so it's simple to take a look at the code.

---

### Post by Pobega on 2006-12-29
Everything seems to work fine, but my only complaint is that it doesn't install my usual 1280x800 resolution. Does anyone have any idea if it's possible to create your own resolutions? If so, how?

**Edit:** After installing 915resolution and restarting X my resolution seems to work, nevermind.

Another question: What apps will I need to get my Wireless running? I'm currently connected through LAN.

---

### Post by Pobega on 2006-12-31
Well I decided to try the third of the three Ubuntu releases, Kubuntu. Sadly, the System76 drivers refuse to run. By this I mean, I can download the file and dpkg it, but it won't run from my menu. In the taskbar it comes up saying "Loading System76 Driver Install..." but it just keeps loading, and eventually gives up. 

And for the record, installed alongside 915resolution your drivers worked **perfectly** in Xubuntu.

---

### Post by crichell on 2006-12-31
This is probably a gtk dependency deal.  We only build and test the driver for Ubuntu.  Run the driver from the terminal for some clues:

```
system76-driver
```

---

