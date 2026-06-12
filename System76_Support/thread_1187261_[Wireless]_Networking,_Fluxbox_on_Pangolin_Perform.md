---
title: "[Wireless] Networking, Fluxbox on Pangolin Performance"
date: 2009-06-14
forum: System76 Support
---

### Post by slackwidow on 2009-06-14
I recently purchased a Pangolin Performance as a replacement for an old (nine years old) Thinkpad on which I mostly ran Debian unstable. Since has a 900 Mhz CPU and 360-odd Mb. RAM, I mostly ran Blackbox, then Fluxbox on it, which was much, much faster than using Gnome.

I also learned from experience that NetworkManager and avahi-daemon (two standard services installed with most if not all flavors of Ubuntu) running under Fluxbox rendered use of a wireless card all but impossible.  

After much heartache I discovered that disabling NetworkManager and avahi-daemon and then configuring my network interfaces by hand was one way to get wireless networking on my Thinkpad running Fluxbox on top of Debian.

Well, the same seems to be the case with the Pangolin Performance running its preinstalled OS, at this point Ubuntu 9.04 with Gnome Display Manager and the Gnome desktop. Amazingly, on my Pangolin Performance Gnome seems to run slower than my desktop (an AMD K8 X2 @ 2.0 GhZ, 2gigs 400Mhz DDR ram). You'd think that the Pangolin, with an equivalent (or faster) CPU and twice the ram running at twice the speed (800 Mhz) would provide a faster desktop experience, but for whatever reason, it doesn't.

If you want a faster graphical user interface experience, by all means install Fluxbox. However, in my case at least, running Fluxbox as a session option from the Gnome Display Manager login screen precludes automatic DHCP configuration of the builtin wireless network card's interface. Does anyone know why that is?  

 In any case there is a workaround. It goes more or less like this:  

1) Install Fluxbox. On my Pangolin performance you can do that using Synaptic in Gnome or on a terminal command line:  sudo apt-get install --install-recommends fluxbox. 

2) Log out of your Gnome session and click "Options". Choose a Fluxbox session.  

3) Fluxbox starts almost instantaneously (unlike Gnome or KDE, which takes 5-10 seconds). Right-click for a context menu and choose Applications -> Terminal Emulators -> Xterm. 

4) Change to the services script directory:[INDENT]cd /etc/init.d 
[/INDENT]5) Turn off the standard Debian/Ubuntu networking services:[INDENT]sudo ./NetworkManager stop  
sudo ./avahi-daemon stop  
[/INDENT]6) To bring up your wireless networking, type[INDENT] sudo iwconfig wlan0

[/INDENT]If you see the first line reads something like[INDENT]wlan0     IEEE 802.11abgn  ESSID:"" 
[/INDENT]it probably means your wireless card has not been associated with an access point yet. 
Try typing "ping yahoo.com" -- if there's no reply you have no internet access and will need to configure the wireless interface manually.

If you know the name of your wireless network, e.g. "linksys", then type the following command:[INDENT]sudo iwconfig wlan0 essid [your wireless network name]  
[/INDENT]For example if your router identifies itself as "linksys" you would type:[INDENT]sudo iwconfig wlan0 essid "linksys"
[/INDENT]7) To automatically obtain an IP address from your wireless network (assuming that your router is configured to allow that) then simply type[INDENT]$ sudo dhclient wlan0  

[/INDENT]That works for me, anyway, when I'm at home on a known wireless network.

---

### Post by jdb on 2009-06-14
> **slackwidow said:**
> I recently purchased a Pangolin Performance as a replacement for an old (nine years old) Thinkpad on which I mostly ran Debian unstable. Since has a 900 Mhz CPU and 360-odd Mb. RAM, I mostly ran Blackbox, then Fluxbox on it, which was much, much faster than using Gnome.

I also learned from experience that NetworkManager and avahi-daemon (two standard services installed with most if not all flavors of Ubuntu) running under Fluxbox rendered use of a wireless card all but impossible.  

After much heartache I discovered that disabling NetworkManager and avahi-daemon and then configuring my network interfaces by hand was one way to get wireless networking on my Thinkpad running Fluxbox on top of Debian.

Well, the same seems to be the case with the Pangolin Performance running its preinstalled OS, at this point Ubuntu 9.04 with Gnome Display Manager and the Gnome desktop. Amazingly, on my Pangolin Performance Gnome seems to run slower than my desktop (an AMD K8 X2 @ 2.0 GhZ, 2gigs 400Mhz DDR ram). You'd think that the Pangolin, with an equivalent (or faster) CPU and twice the ram running at twice the speed (800 Mhz) would provide a faster desktop experience, but for whatever reason, it doesn't.

If you want a faster graphical user interface experience, by all means install Fluxbox. However, in my case at least, running Fluxbox as a session option from the Gnome Display Manager login screen precludes automatic DHCP configuration of the builtin wireless network card's interface. Does anyone know why that is?  

 In any case there is a workaround. It goes more or less like this:  

1) Install Fluxbox. On my Pangolin performance you can do that using Synaptic in Gnome or on a terminal command line:  sudo apt-get install --install-recommends fluxbox. 

2) Log out of your Gnome session and click "Options". Choose a Fluxbox session.  

3) Fluxbox starts almost instantaneously (unlike Gnome or KDE, which takes 5-10 seconds). Right-click for a context menu and choose Applications -> Terminal Emulators -> Xterm. 

4) Change to the services script directory:[INDENT]cd /etc/init.d 
[/INDENT]5) Turn off the standard Debian/Ubuntu networking services:[INDENT]sudo ./NetworkManager stop  
sudo ./avahi-daemon stop  
[/INDENT]6) To bring up your wireless networking, type[INDENT] sudo iwconfig wlan0

[/INDENT]If you see the first line reads something like[INDENT]wlan0     IEEE 802.11abgn  ESSID:"" 
[/INDENT]it probably means your wireless card has not been associated with an access point yet. 
Try typing "ping yahoo.com" -- if there's no reply you have no internet access and will need to configure the wireless interface manually.

If you know the name of your wireless network, e.g. "linksys", then type the following command:[INDENT]sudo iwconfig wlan0 essid [your wireless network name]  
[/INDENT]For example if your router identifies itself as "linksys" you would type:[INDENT]sudo iwconfig wlan0 essid "linksys"
[/INDENT]7) To automatically obtain an IP address from your wireless network (assuming that your router is configured to allow that) then simply type[INDENT]$ sudo dhclient wlan0  

[/INDENT]That works for me, anyway, when I'm at home on a known wireless network.

I got tired of all the automatic & hidden configuration in Ubuntu.
I never really knew what controlled what or how to change it.
It was a royal pain to figure out what was going on under the covers.
I switched to Arch Linux, it took a while to figure out but I sure am happy with it :)
I'm also a happy fluxbox user.

jdb

---

### Post by slackwidow on 2009-06-15
> **jdb said:**
> I got tired of all the automatic & hidden configuration in Ubuntu.
I never really knew what controlled what or how to change it.
It was a royal pain to figure out what was going on under the covers.
I switched to Arch Linux, it took a while to figure out but I sure am happy with it :)
I'm also a happy fluxbox user.

jdb

Hmmm, maybe I'll have to try Arch Linux. 

What I'm really looking forward to, though, is Slackware 13, which will include Slack's first official x86_64 port. I think that's my best shot at supporting all the hardware on my system76 laptop on an out-of-the-box distro, without too much mucking around under the hood. In the meantime I'm content to clip Ubuntu's horns (Network Manager and avahi-daemon) and tail (Gnome) and go bareback (Fluxbox)!

If it lives up to the name, 64-bit Slackware running KDE will be much faster than Ubuntu but deliver a similarly trouble-free out-of-the-box experience.

---

