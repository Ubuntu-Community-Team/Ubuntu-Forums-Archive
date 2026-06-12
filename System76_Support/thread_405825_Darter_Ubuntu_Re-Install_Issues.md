---
title: "Darter Ubuntu Re-Install Issues"
date: 2007-04-10
forum: System76 Support
---

### Post by madcitybrit on 2007-04-10
Following a password change issue which essentially locked me out of my beloved Darter (and following instructions from another thread which didn't seem to work for me), I downloaded Ubuntu 6.10 (desktop, 32 bit) and ran a fresh install. Now my wireless doesn't seem to be working. I have a wireless network at home which, when I first took delivery of my Darter, was picked up right away, everything just worked out of the box, but that no longer seems to be the case with the new Ubuntu install.

I also plugged my cable (Internet access) directly into the laptop, and couldn't get Internet access that way either (although I never tried this before anyway as I'm always using wireless, and this is a really low priority in comparison).

Should wireless have worked with the default Ubuntu install? Did I install the correct version of Ubuntu? (32 bit versus 64 bit) What do I need to do to get wireless working? 

Just out of curiosity, if I were to get System76 to send me a recovery DVD, will this set things up exactly as when delivered (asking for a username upon first boot, wireless etc. all working)? I'm wondering whether I should just do that.

Another thing I've noticed so far with the new install is that, when selecting the shutdown button on the desktop and being presented with a dialog of options to log off, shutdown, hibernate, suspend etc., and the background fades to a dark version of itself (or to grey or something), the colour graduation is no longer smooth and seems go to a very small colour palette (so only four or five shades of the original background colour). The original (factory installed) setup kept a full colour palette, so the background fade was very smooth. I still have the default 'Human' background (and theme), which I also had before the re-install. Any ideas?

Thanks.

---

### Post by madcitybrit on 2007-04-10
Maybe this, from Restoring Your System ([http://knowledge76.com/index.php/Restoring_Your_System)](http://knowledge76.com/index.php/Restoring_Your_System)), answers some or all of the above...

> 
    *  Log into your newly installed system
    * Connect to the internet with an ethernet cable (verify you're connected by going to a website)
    * Open a terminal (Applications > Accessories > Terminal)
    * Fully update your system by copying and pasting the following line into your terminal 

sudo apt-get update && sudo apt-get --assume-yes dist-upgrade


I couldn't get a connection to the Internet via my ethernet cable at home, so couldn't run the above command. Would this command fix my wireless and background fade (on shutdown /suspend/hibernate dialog) issues?

I guess I need to get Internet access via ethernet cable working first. Any ideas on what I might need to do to get this working? I have cable Internet access at home, and my current setup has the cable Internet box hooked to my wireless router. I plugged this cable directly into my Darter instead and couldn't get Internet access. Should I have seen a connectivity icon of some kind on the desktop? I didn't notice anything when I plugged in.

Thanks.

---

### Post by thomasaaron on 2007-04-10
Based on your description of your fresh install, it sounds like you did not install the system76 driver.

You can get directions for restoring a system76 computer (including the driver) here:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Best,
Tom

---

### Post by thomasaaron on 2007-04-10
Type this in the terminal:

[PHP]sudo /etc/dbus-1/event.d/25NetworkManager restart[/PHP]

If all goes well, a networking icon should appear in the upper right of your screen. Left click the icon and select "Wired Connection."

Best,
Tom

---

### Post by madcitybrit on 2007-04-10
I'm at work right now, left the Darter at home (got fed up with ppl drooling all over it!). I'll try this when I get home this evening and let you know how it goes.

Thanks so much.

---

### Post by madcitybrit on 2007-04-11
> **thomasaaron said:**
> Type this in the terminal:

[PHP]sudo /etc/dbus-1/event.d/25NetworkManager restart[/PHP]

If all goes well, a networking icon should appear in the upper right of your screen. Left click the icon and select "Wired Connection."

Best,
Tom

Okay, I ran the above command in a terminal and it said 'command not found'. I navigated to /etc/dbus-1/event.d/ and there were three files, but none of them were 25NetworkManager. The only three files in there are 20hal, 25avahi-daemon, and 70system-tools-backends. Any thoughts?

Thanks.

---

### Post by thomasaaron on 2007-04-11
It sounds like you did not complete the restore instructions. 
You need to run the system76 driver, which will install network manager and get you back up and running.
All of this is detailed at [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Make sure you are installing Ubunt with a 6.10 CD. If you are using the 7.04 CD, the system76 driver will not run for it yet (but it will within a week).

Also, if you re-install from the CD, I would plug in your ethernet cable FIRST. Not a big deal, but it autoconfigures your DHCP.

Feel free to call me at system76 if you need assistance.

Best,
Tom

---

### Post by madcitybrit on 2007-04-11
Well I reinstalled with the ethernet cable plugged in. At first it didn't work, but I think I've had an issue all along with my cable. After swapping out, I enabled Wired connection under System->Administration->Networking and was able to connect to the Internet. I then ran the sudo apt-get update command from the Restoring Your System doco, and I applied the system76-driver-1.9.9.deb file (which I had downloaded at work to my USB thumb-drive, so I installed it from there) and ran the System->Administration->System76 Driver Installer. My wireless didn't work right away, I had to manually enable it with my home network info via Networking (Wireless connection). I'm a little concerned that my system isn't automatically detecting wireless networks at this point, but I've been unable to try it elsewhere as of yet. In Network Settings under the General tab, I checked the 'Automatic service discovery' option. Perhaps this will allow my system to see other wireless networks, but I don't yet know. When I initially received my Darter I didn't have to do anything here, my wireless network was automatically picked up.

I'm not getting a wireless network icon on my desktop anywhere (I seem to remember having an icon in the panel at the top of the screen when connecting to all and any wireless network before), and Bluetooth doesn't appear to be working. I used to have a Bluetooth File Sharing option under the Applications>Accessories menu, which I was successfully using to switch Bluetooth on and off, but I no longer have that option. I was sharing files between my laptop and Sony Ericsson cellphone out-of-the-box before.

Any ideas on the wireless network detection and panel icon?

... My Bluetooth is now fixed and working. Seems that the Bluetooth File Sharing prog isn't installed by default. I found it in Synaptic Package Manager (under System>Administration) as gnome-bluetooth. I can now switch Bluetooth on and off with this program and I'm successfully transferring files between devices now.

Thanks.

---

### Post by madcitybrit on 2007-04-11
As a point of note for my previous post, perhaps the Synaptic Manager for installing Bluetooth File Sharing should be included as part of the System Recovery doco (as a note for Bluetooth capable laptops say, and in my case a Darter). Just a thought. :)

As for the wireless, I don't recall exactly what the panel icon looked like, but it was next to the date/time and had a series of bars (or perhaps just one), showing signal strength. Regardless, from this icon I was able to see a list of available wireless networks, and it seemed to handle keyring stuff for me too. Like I said before, this was on my Darter when I first received it, but not with the Ubuntu re-install by default. So I'm guessing this is another program (or set of programs) I might need to add, possibly through Synaptic Package Manager again. Do you know what it/they might be?

---

### Post by madcitybrit on 2007-04-12
Okay, wireless networking is fixed. Just as with Bluetooth I had to install network-manager and network-manager-gnome via the Synaptic Package Manager. I now have my icon back in the gnome panel (four bars showing signal strength of my wireless connection; left clicking this shows all available wireless networks, and it handles keyring stuff too).

I am back up and running!

Thanks @thomasaaron for your help.

---

