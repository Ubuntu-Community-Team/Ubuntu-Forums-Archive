---
title: "Server on wireless"
date: 2010-07-19
forum: Server Platforms
---

### Post by ingeva on 2010-07-19
I'm trying to set up a server which will be placed in a location which is inconvenient for cabling. However, it's close enough for wireless use.

However, I have tried all I can, and have not found a workable solution. The problem is that a wireless interface seems to need a desktop software and someone has to log in before the interface is activated.
Naturally, I do not want a desktop; I don't even want a keyboard or a screen after the computer has been set up. Obviously, it must be working after a reboot, wit no operator intervention.

I have all Ubuntu versions from 8.04, but I would prefer one of the newer ones which can run nfsv4.

Any solution please?

---

### Post by Bachstelze on 2010-07-19
If your wireless network uses WPA, use wpasupplicant or wicd.

---

### Post by arrrghhh on 2010-07-19
It's possible for sure... but obviously the server will have to be configured before placed into its final location.

Bachstelze makes a good point.  The other thing to watch out for is what chipset the wireless card uses.  Some chipsets are dead easy to use in Linux, others... not so much.  Ubuntu is getting a lot better, but you may want to test the card out in a ubuntu-desktop box to be sure that ubuntu doesn't have any issues with the card.

That way, you can ensure that it works out of the box.  The rest is just configuration.

---

### Post by ingeva on 2010-07-20
> **Bachstelze said:**
> If your wireless network uses WPA, use wpasupplicant or wicd.Obviously a good idea, but your response raises more questions.
First: wpasupplicant is evidently installed already, since there are scripts using it.

I have no idea how to implement any of this in the startup scripts. I have only been running desktop versions before, and then everything is done automatically -- but I need to log in!

Is it possible to log in automatically?
If I don't need the desktop I see no reason to install it.

If I could use a wired interface it would be much easier. The network will come up before anyone logs in. The wireless isn't even started till someone does.

Bachstelze, can you direct me to a description of a way to do this? Understandable, please -- if I were an expert I wouldn't have to ask! :)
The description I found was way out of my league!
Couldn't this be done using a simple script or init program?

Before going on I should ask: How do I find which driver is in use for my interface?
Is there anything for Linux like the Control Panel for Windows? Hmmm.... There's actually one Windows thing that I miss in Linux ..... :(
Anyway, the interface is a D-link AirPlus G DWL-G510 PCI adapter - if that would help.
I did nothing special to have it installed and working in the Gnome desktop, except setting the password of course (WPA2-PSK).

There's something else I should mention: If I use a WiFi card in my desktop computer and connect it to a remote, my internet connection (eth0) is lost. I believe Linux tries to connect to internet via wlan0 as soon as it's connected, but the internet is still on eth0!
If I could make that work I could connect the other computer to a wireless router (I have one spare) and have them connected that way. Should be easy, but evidently it is not. Is there a way to connect two wireless routers to each other via their wireless ports?
Oh, too many questions already .... :)

Thanks for helping!

---

### Post by Bachstelze on 2010-07-20
> **ingeva said:**
> 
Bachstelze, can you direct me to a description of a way to do this? Understandable, please -- if I were an expert I wouldn't have to ask! :)
The description I found was way out of my league!
Couldn't this be done using a simple script or init program?

It's done in /etc/network/interfaces, just like for a wired interface.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

> Before going on I should ask: How do I find which driver is in use for my interface?

Since your card is PCI, [font=monospace]lspci -k[/font].

> If I could make that work I could connect the other computer to a wireless router (I have one spare) and have them connected that way. Should be easy, but evidently it is not. Is there a way to connect two wireless routers to each other via their wireless ports?

Some routers support it, but not all. The manual should tell you if yours does.

---

### Post by ingeva on 2010-07-20
> **Bachstelze said:**
> It's done in /etc/network/interfaces, just like for a wired interface.
Since your card is PCI, [FONT=monospace]lspci -k[/FONT].
Some routers support it, but not all. The manual should tell you if yours does.

Thanks very much!
I have something more solid to go on now.

The interface driver I found is this:
```
02:01.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci
```

Again, thanks!

---

### Post by ingeva on 2010-07-22
> **Bachstelze said:**
> It's done in /etc/network/interfaces, just like for a wired interface.
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

Sorry for coming back here, but the instructions that you refer to are for Dapper end Edgy. I'm running Karmic (Lucid has too many issues).
The format of the wpa_supplicant.conf file is completely different on my system (looks like XML), so this description does not seem to be relevant for newer versions of Ubuntu. There are still too many unanswered questions here, and after working with this, on and off, for more than a year, I'm tempted to give up having a remote server, and forget about the
added security.

BTW, my wpa_supplicant.conf file looks like this:
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="fi.epitest.hostap.WPASupplicant"/>
                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
        <policy group="netdev">
                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
        <policy context="default">
                <deny own="fi.epitest.hostap.WPASupplicant"/>
                <deny send_destination="fi.epitest.hostap.WPASupplicant"/>
                <deny send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
</busconfig>

```
... but it's in the /etc/dbus-1/system.d directory ....

---

### Post by Bachstelze on 2010-07-22
> **ingeva said:**
> Sorry for coming back here, but the instructions that you refer to are for Dapper end Edgy. I'm running Karmic (Lucid has too many issues).

Same instructions apply (if you don't have /etc/wpasupplicant.conf, just create it).  The file you posted is unrelated.

---

### Post by ingeva on 2010-07-23
> **Bachstelze said:**
> Same instructions apply (if you don't have /etc/wpasupplicant.conf, just create it).  The file you posted is unrelated.OK, but this is actually a little embarrassing:

1. If I start the server (with the Gnome desktop) and do NOT log in, after some time the wireless network comes up anyway! I've just been too impatient!
2. There's also a /etc/wpa_supplicant directory, containing the "missing" files,
    action_wpa.sh
    functions.sh
    ifupdown.sh

3. How do I prevent the X server from being started when the computer is booted?
    I'd like to try without having to re-install the system.... :)

Thank you for your patience!

---

### Post by arrrghhh on 2010-07-23
I think you can just remove GDM from your startup...

```
sudo update-rc.d remove gdm
``` I believe?  If you just rename the file in /etc/init.d/ you may have some odd errors.

---

### Post by Bachstelze on 2010-07-23
> **ingeva said:**
> 
1. If I start the server (with the Gnome desktop) and do NOT log in, after some time the wireless network comes up anyway! I've just been too impatient!

So you have Gnome installed?  Either you didn't tell us, or I missed it.  Anyway, then you will have NetworkManager kicking in, doe it connect to your network?

> 2. There's also a /etc/wpa_supplicant directory, containing the "missing" files,
    action_wpa.sh
    functions.sh
    ifupdown.sh

Doesn't matter, you can put the wpasupplicant.conf file anywhere, even outside /etc if you feel like it.

---

