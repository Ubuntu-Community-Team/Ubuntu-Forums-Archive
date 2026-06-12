---
title: "Fix wireless/sound without Sys76 driver?"
date: 2009-11-02
forum: System76 Support
---

### Post by ackey on 2009-11-02
I'm on a Daru2 and upgraded to karmic - I'm not able top run the system76 driver though (it doesn't recognize my system).  Any ideas on how I go about getting the wireless and sound to work without the driver?  I have faith the System76 people can help me with the driver, but perhaps not before I need to use wireless on my laptop.  

While the "alsa force reload" got some sound working, the volume is still very low. 

Trying to play a DVD in VLC (or totem) restarts X.

I'm somewhat afraid to do a clean install without the System76 driver to help get things working, though I'm not convinced they could get worse.

---

### Post by Lee_Machine on 2009-11-02
What do you mean by "It doesn't recognize my system"

Do you have the newest driver installed?


[http://planet76.com/repositories/system76-driver-2.3.9.deb](http://planet76.com/repositories/system76-driver-2.3.9.deb)


For low sound did you try alsamixer?

In terminal type alsamixer, and make sure Master, PCM, and Front are all the way up.

Many times gnome-volume-control will show everything is at max, but it's not.

Or it's maxed, but it's really muted.

---

### Post by ackey on 2009-11-02
Yes, I have the driver installed - 2.3.9
When I try to run it (through the Admin menu) I get:
"This driver is designed for System76 machines running Ubuntu versions 6.06 through 9.10.  If you have a System76 machine running one of the above Ubuntu versions please file a bug report..."

So, I just fixed my sound, dvd, and touchpad problems at once by fixing my menu.lst to actually be defaulting to the new kernel (see [here]("http://ubuntuforums.org/showthread.php?p=8218261#post8218261")).  I still don't have a volume control in my panel, nor one listed under add applet.... No power monitor either.

Wireless still doesn't work and the System 76 driver still doesn't recognize my system.

---

### Post by thomasaaron on 2009-11-02
Is this Nicole? If the driver isn't detecting your computer properly, it might be because of the repairs we did earlier. If they replaced the mobo, then we might need to re-flash the BIOS. Let's take this one to email.

As for the wireless, please send me the output of...
> 
cat /etc/network/interfaces

---

### Post by ackey on 2009-11-03
```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

Tom- Yes, it is me.  I assumed I had a unique problem but thought I should post in case I'm not the only one.  I'll e-mail you.

Edit:
I have been doing some further googling, grep-ing, etc.

When I boot from the live cd, wireless works flawlessly.  I started going though the boot logs for the live and normal boots to see any differences in the network messages.  I see a "wlan0: link becomes ready" much earlier in the live boot than the normal boot.

Also, at some point the NetworkManager applet started showing two entries: lo and wlan0:avahi.  Initially it only showed lo.

For the iwconfig command, wlan0 has information listed (with zeros and an empty essid).  I try specifying the essid to use and then the essid field disappears.  The dmesg output ends with:

```


wlan0:associated
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: disassociating by local choice (reason=3)
wlan0: deauthenticated (Reason: 2)


```

---

### Post by ackey on 2009-11-03
I downloaded the wicd packaged (and its dependencies) to a thumbdrive, removed network-manager and gnome-network-manager and then installed wicd.  

It works! :o

I had seen a variety of wireless-related bugs fixed this way in the forums.  Has any other DarU2 users out there had this problem with NetworkManager?  I'm not convinced that this was really at NetworkManager problem, but now that it is fixed I'm not that concerned.

---

