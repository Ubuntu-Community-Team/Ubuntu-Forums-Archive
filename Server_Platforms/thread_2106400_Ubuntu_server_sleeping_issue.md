---
title: "Ubuntu server sleeping issue"
date: 2013-01-19
forum: Server Platforms
---

### Post by presentfactory on 2013-01-19
So I am running Ubuntu server system 12.04.1 LTS on a studio laptop just to mess around with a site and stuff but I keep running into a small problem. If I dont do anything on the computer for like 10 minutes the screen goes black, not really a problem as it keeps everything going but if I try to connect to the site from a external source it appears to be down. The only way to "reconnect" it that I found is to connect to its local address with another computer on the router (192.168.1.101). I assumed that the computer was shutting down the LAN or something to save power so I looked in my bios and couldn't find anything relating to power saving. After that I did some research and set the GRUB_CMDLINE_LINUX_DEFAULT value in /etc/default/grub to acpi=off and apm=off then rebuilt it and rebooted the computer, but with no success. Does anyone know why its doing this

---

### Post by JCFutch on 2013-04-19
I too am having this problem. I tried editing the GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub as well, and it seemed to mess up the boot sequence somehow. I did make sure to update grub before rebooting. I am running my server from a wireless connection and when the server "sleeps" it shuts down pretty much everything to the outside world until it is woken up by the keyboard. I am newer to Ubuntu server but am comfortable with command line so I do understand setting different parameters. I too am hosting a site and just want to keep it up at all times. If there is any insight to why this is happening, and HOW I can change it to where it will just not sleep, hibernate, or whatever it is doing...that would be great. Thanks in advance!

---

### Post by tripp98 on 2013-05-05
Laptops have built in low power settings.  check bios and see if it is putting hardware asleep to save power.  if you are testing server software on it disable it while in testing mode.

---

### Post by d4m1r on 2013-05-08
If you are using the machine exclusively for server purposes and want to run it 24/7, disable all power saving functionality in the BIOS and otherwise (to prevent it from going into sleep/suspend/etc entirely).

---

