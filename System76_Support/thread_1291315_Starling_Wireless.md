---
title: "Starling Wireless"
date: 2009-10-14
forum: System76 Support
---

### Post by jimmie-watters on 2009-10-14
Hi,

I've had my Starling for a few weeks now and everything is going well. I have a question regarding wireless. I am able to connect and surf without any of the problems associated  with a previous generation of driver. But I only seam to connect at 11 Mbps. Windows XP and Vista systems connect at 54 Mbps. Signal strength is good, signal to noise isn't bad; yet i still connect only at 802.11b speeds. Has anyone else seen this? Any suggestions on trouble shooting this would be great.

Thanks

Jim

---

### Post by thomasaaron on 2009-10-14
How far are you from your access point? While we've tested the new driver out to about 120 ft, it definitely slows down the further away you get from the access point. 

It has a lot smaller antennas than a full-blown laptop and will not perform the same at longer distances. I doubt any netbook will.

Also, have you tested with other access points?

---

### Post by jimmie-watters on 2009-10-14
Thanks for the reply Thomas,

Even when I am five-six feet away from a Cisco 1231 AP i still only connect at 11Mbps. Other networks have been public so I haven't checked when knowing how close i am to the ap. Not a huge deal since typically the internet is 10 Mbps or less. Just curious that i don't see it connect at 54 Mbps when extremely close.

Jim

---

### Post by prodigi on 2009-10-20
ok im a total noob at linux but i had xp partitioned and
things weren't working right with linux so i went to re-install
windows and try to detroy the partitions and start fresh but it killed
my laptop. anyway im running ubuntu jaunty jackalope as my 
main o/s i have a gateway amd 64bit and a preinstaled
wireless card. how in the heck do i get my machine to
recognize my airport??? so frustrated but kinda diggin the 
linux thing so far...:( miss my old apple.
someone please email me [email]v.hamler@gmail.com[/email]

thanks:confused:

---

### Post by thomasaaron on 2009-10-20
prodigi,

This forum provides support for System76 computers. While I'd be happy to help you if I could, we don't have any gateways to test with. You'd probably have better luck posting to Ubuntu's Wireless and Networking forums...

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by Eyore15 on 2009-10-22
> **jimmie-watters said:**
> Hi,

I've had my Starling for a few weeks now and everything is going well. I have a question regarding wireless. I am able to connect and surf without any of the problems associated  with a previous generation of driver. But I only seam to connect at 11 Mbps. Windows XP and Vista systems connect at 54 Mbps. Signal strength is good, signal to noise isn't bad; yet i still connect only at 802.11b speeds. Has anyone else seen this? Any suggestions on trouble shooting this would be great.

Thanks

Jim

I'd be glad to try it out on my machine, but I have no idea how to do the measurement.  Is there a utility/cli to invoke that tells me signal strength etc?

---

### Post by jimmie-watters on 2009-10-24
Hi,

I use iwconfig from a command line to give some wireless stats

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g linked  ESSID:"xxxxxx"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=77/100  Signal level=-42 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
As you can see i am getting a bit rate of 54 Mb/s on this AP so i may have to go back to my Cisco AP to see if it is a power or transfer rate configuration issue. But the iwconfig command provides signal, noise level for the given connection i am not certain of how line quality is calculated. Does anyone else know?


I'll let you know if any configuration change on my AP improves my transfer rate.

---

