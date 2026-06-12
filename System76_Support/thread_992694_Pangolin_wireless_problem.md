---
title: "Pangolin wireless problem"
date: 2008-11-25
forum: System76 Support
---

### Post by larand on 2008-11-25
Just got my Pangolin Performance today, and I love it. Quite a step up from my old Apple iBook! Here's my configuration:

```
1 x Pangolin Performance (PAN-P4) 
       Operating System Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
       Display Resolution 15.4" WSXGA+ Super Clear Glossy LCD (1680 x 1050)
       Processor Core 2 Duo P8600 2.40 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Hard Drive 320 GB 5400 RPM SATA II
       Optical Drive CD-RW / DVD-RW
       Wireless 802.11 agn
```

However, after a few hours, my wireless connection started refusing to connect to my home wi-fi network.  Everything seemed fine, then I tested suspend by closing the lid. When it resumed, it wouldn't connect to the router. I checked the logon information, and it had an incorrect password for my WPA2 connection. I pasted in the right information, and still no go--and when I checked the password, it was wrong again. It seems it won't remember the correct password. I tried typing in the PW manually, and it failed again to connect nor did it remember the correct PW. 

Out of curiosity, I tried to connect to a neighbor's wifi (he leaves it wide open), and it failed to connect there as well, although my iMac had no problem connecting. 

I ran iwconfig, and this is what I got:

```
larry@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I restarted it twice to see if that would clear anything out, but it didn't help. I really need to get this up and running.  Any suggestions?

---

### Post by larand on 2008-11-25
Well, that was weird. I still wasn't having any luck this morning, so I connected an ethernet cable from the router to the Pangolin and suddenly my wireless connection started working again. :confused:

Glad to have it back, but I'd sure like to know why the problem happened in the first place, and how I can prevent it from happening again.

---

### Post by thomasaaron on 2008-11-25
Try this:

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

---

### Post by larand on 2008-11-25
Thanks for the reply...

I actually tried that last night after finding it in a previous thread. Those were the only two lines in /etc/network/interfaces, and they were uncommented. So, the mystery continues.

Also, my success this morning didn't last long. Shortly after disconnecting the ethernet cable, thinking my connection was back, it stopped communicating with the router and Firefox froze up. The trackpad buttons intermittently stopped responding to clicks, and when I shut down via the power button (I was unable to get any response from the normal shutdown dropdown) it hangs on "shutting down ALSA." 

Help!

Edit: I forced a shutdown by holding down the power button. When I rebooted, it was completely locked up with an unresponsive keyboard and trackpad. The network manager icon looked like it was frozen in mid-connection.  There were two flashing lights on the front of the base, one was the caps lock indicator and the other just looked like a lock with a keyhole.  I did another forced shutdown via the power button, and now the keyboard and trackpad are responding normally but the network manager isn't seeing any wireless networks, and there are 12 available according to my iMac.

Edit: I went ahead and looked at /etc/network/interfaces again, and verified that it was as it should be. I saved, exited gedit and rebooted. Now I'm getting the flashing lights again and it's stuck on a black screen with the X cursor.

---

### Post by thomasaaron on 2008-11-25
First, it is potentially VERY detrimental to your file-system to do forced shutdowns. I realize that sometimes it might be necessary. But a lot of times you can get around this by holding down Alt and SysReq and then pressing the following keys one at a time: RSEIUB.

If you right-click your networking icon in the upper right of the LCD, do you have both networking and wireless checked?

---

### Post by larand on 2008-11-25
I couldn't get the alt-sysreq sequence to do anything, so I had to do another forced shutdown to get out of the black screen. I know it's not good, but there seemed to be no other choice.

I rebooted and got through login OK, but it's frozen on trying to connect to my network, and the trackpad and keyboard are frozen so I can't right-click the networking icon. The alt-sysreq RSEIUB procedure isn't doing anything. I have two flashing LEDs on the bottom left--the lock and caps-lock icons (the two rightmost ones).

I'll leave it like this until I hear back. I don't want to do another forced shutdown.

---

### Post by thomasaaron on 2008-11-25
Geesh! This is pretty strange.

Did you do *anything* that I should know about: Software downloads, removals; Kubuntu/Xubuntu; different wireless manager; etc...

It sounds like something is royally hosed, and we need to figure out if it is hardware or software/configuration. If you could test your wireless from a live CD, that would be a great start.

Also, the blinking LED's mean you had a kernel panic. Here is what I would do for that:

1. Remove your ac adapter and battery.
2. Re-seat your memory and hard drive.
3. Boot into recovery mode and then run these commands...
```
sudo apt-get install linux-backports-modules-intrepid
sudo reboot -h now
```

---

### Post by larand on 2008-11-25
OK, I rebooted into recovery mode and ran the command. It told me I had the latest version already installed. 

Forgive the noob question, but how do I boot from a CD in Linux? On Macs I hold down the C key while booting...is it the same?

For software installs, I downloaded the Shiki-Colors theme from gnome-look.org and installed it (although I have reverted to the default Human theme).  I also installed Cheese from Synaptic, but it didn't detect my camera so I removed it through Synaptic. I also installed Firestarter through Synaptic, and removed it the same way thinking it might be part of the problem. I installed Camera Monitor, but have not removed it.

Edit: Network manager is not showing a wired ethernet connection, even though the ethernet cable is connected (and was connected during booting). Both networking and wireless are checked.

Edit: Found how to boot from CD. Will test wireless from live CD as soon as it boots.

---

### Post by thomasaaron on 2008-11-25
Firestarter could be part of the issue. It could be that you didn't --purge remove it via Synaptic.

Try:

sudo apt-get install firestarter
sudo apt-get --purge remove firestarter


To boot from a live CD, press F2 when you see the manufacturer splash or post screen.  Then tab over to "Boot" and make your dvd drive your first boot device. Then insert a live CD and press F10 and Enter.

---

### Post by larand on 2008-11-25
Booted from live CD (8.10 64-bit). It did detect the wireless networks in the area, but not the hard-wired connection to the router. I entered the WPA authentication key, and it asked me to establish a keyring and password. I input something and it froze. Keyboard and trackpad are now completely unresponsive, and system is locked.

---

### Post by thomasaaron on 2008-11-25
I suspect it is some sort of hardware issue. Please contact me via email at support(at)system76(dot)com and we will conduct a few other tests.

---

### Post by larand on 2008-11-25
OK, I reinstalled and then uninstalled Firestarter using the commands you gave me. I rebooted and it detected my wireless network and logged on. I then opened Firefox, clicked on a toolbar and got a kernel panic (flashing LEDs again) and a frozen computer. 

Alt-SysReq RSEIUB is not doing anything. Is there anything I can do besides forcing another shutdown?

---

### Post by larand on 2008-11-25
OK, email has been sent.  Thanks for your help.

---

