---
title: "Wireless up and down on 9.10 fresh install"
date: 2009-11-04
forum: System76 Support
---

### Post by abulluck on 2009-11-04
Seems like this issue get overshadowed in the masses with "my wireless is not working at all" so I still have not found an answer.

Since doing a fresh install of 9.10 (keeping home partition intact) I have a wierd issue with wireless being very slow due to it coming and going.  By that I mean I get a lot of network activity when say loading a page, but every few seconds the page pauses while loading and activity goes to zero.  I don't loose my connection, it just goes up and down all the time.

I do need to test fully by plugging directly into my LAN.  But just wanted to throw this out there to see if anyone had it and fixed it.

---

### Post by ctsdownloads on 2009-11-04
> **abulluck said:**
> Seems like this issue get overshadowed in the masses with "my wireless is not working at all" so I still have not found an answer.

Since doing a fresh install of 9.10 (keeping home partition intact) I have a wierd issue with wireless being very slow due to it coming and going.  By that I mean I get a lot of network activity when say loading a page, but every few seconds the page pauses while loading and activity goes to zero.  I don't loose my connection, it just goes up and down all the time.

I do need to test fully by plugging directly into my LAN.  But just wanted to throw this out there to see if anyone had it and fixed it.

Silly question, but are you finding yourself being able to connect your router's login when this drop happens? Also, with network manager, do you see a visual drop with the blue bars or by rolling your cursor over the module? Just curious. If all of that is fine, and the router login is working well, could be DNS related and I have a solution that I use for that.

---

### Post by samalex on 2009-11-04
Actually I ran into this problem two nights ago on my PanP5 running Ubuntu 9.04.  Things were loading very slow, websites stalling, and Hulu nor Youtube would load any videos.  I went to speedtest.net and it showed my downstream speed was about 0.5 mbps with a horrible ping time of around 250ms.

I rebooted and ran the speed test again where it showed downstream at 17 mbps and ping time at 23ms which is more like what I normally get.  I'm sure it wasn't my ISP because my wife had a Hulu video playing on her laptop and surfing and she didn't experience any slowdown.  

Not sure what it was and the logs didn't show anything out of the ordinary.  I just hope this doesn't happen while taking one of my online tests for school :?

Sam

---

### Post by ctsdownloads on 2009-11-04
> **samalex said:**
> Actually I ran into this problem two nights ago on my PanP5 running Ubuntu 9.04.  Things were loading very slow, websites stalling, and Hulu nor Youtube would load any videos.  I went to speedtest.net and it showed my downstream speed was about 0.5 mbps with a horrible ping time of around 250ms.

I rebooted and ran the speed test again where it showed downstream at 17 mbps and ping time at 23ms which is more like what I normally get.  I'm sure it wasn't my ISP because my wife had a Hulu video playing on her laptop and surfing and she didn't experience any slowdown.  

Not sure what it was and the logs didn't show anything out of the ordinary.  I just hope this doesn't happen while taking one of my online tests for school :?

Sam

Generally wifi on any OS is either working fine, slow consistently or not happening. 

Intermittent stuff can happen, but that is where monitoring and reporting on what network manager is doing comes in. If the signal is dropping some, look at it - do the blue bars reflect this? Simple as that.

On my desktop using Ethernet for instance, I can right-click NM and get what you see in the screenshot attached. Do the same the minute it happens again.

Another approach is to copy and paste what iwconfig provides in the terminal.

---

### Post by abulluck on 2009-11-05
Ok, the solution that worked for me was to disable ipv6 in the grub.

---

### Post by ctsdownloads on 2009-11-05
> **abulluck said:**
> Ok, the solution that worked for me was to disable ipv6 in the grub.

Ah yes, going ipv4 with select routers. That is a pain, but glad it worked for out. ;)

---

### Post by samalex on 2009-11-05
> **abulluck said:**
> Ok, the solution that worked for me was to disable ipv6 in the grub.

I didn't think of disabling ip6.. I'll do that tonight and see if that helps.

Thanks for the suggestion...

Sam

---

### Post by Lee_Machine on 2009-11-05
Disabling IPv6 support in Firefox usually speeds up connections. Just make sure your ISP doesn't rely on it for things like their DNS server. 


Disabling IPv6 with Firefox is the way to go, then if you want to go with the OS. Here is how to do both.

In Firefox, type in the address bar: 

**about:config**


In the filter, type: 

**ipv6 **


You will see the variable 

**network.dns.disableIPv6 **


Change value to **true** to disable IPv6 support in Firefox.

To disable IPv6 on the OS do this:

**gksu gedit /etc/modprobe.d/blacklist**

Add at the end of file the line: 

**blacklist ipv6**

Save, then reboot.


To make sure that IPv6 is disabled, type in a terminal: 

**ip a | grep inet6**

---

### Post by __p1n__ on 2009-11-05
You might also consider disabling whatever network managers that you run and just do a static configuration.

---

### Post by jordansc on 2009-11-06
This is a known issue is Karmic:
**[FONT=Arial][SIZE=2][karmic regression] all network apps / browsers suffer from multi-second delays by default due to IPv6 DNS lookups[/SIZE][/FONT]**


[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

This issue slows down all network activity, not just your browser. I did the following to disable IPv6 in the OS (in grub):

start a Terminal session and type:
 gksu gedit /etc/default/grub    ....then change
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 to
 GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
 then
 sudo update-grub
 Reboot and network speed should be back to normal.

---

### Post by HotShotDJ on 2009-11-06
> **jordansc said:**
> 
start a Terminal session and type:
 gksu gedit /etc/default/grub    ....then change
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 to
 GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
 then
 sudo update-grub
 Reboot and network speed should be back to normal.I strongly recommend the addition the following line before running the above code:```
sudo cp /etc/default/grub /etc/default/grub.old
```

---

### Post by jordansc on 2009-11-06
HotShotDJ is absolutely correct. Making a copy of grub should be your first step.

---

