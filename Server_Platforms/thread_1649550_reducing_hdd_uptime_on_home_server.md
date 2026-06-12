---
title: "reducing hdd uptime on home server?"
date: 2010-12-20
forum: Server Platforms
---

### Post by Hawkoon on 2010-12-20
I have an old laptop that I use as a server and I would like to reduce hard disk uptime. I have an idea how to go about this, but I wonder if I am overlooking something here. So the opinions and suggestions of you server experts out there would be much appreciated.
 
 The reason for using a laptop as server is the low power consumption. Also, with the battery pack installed, it has its own UPS, which is nice to have. Thirdly, it serves only two simple tasks so a desktop system would be overkill. It logs temperature readings from my heating system once a minute and I use it to play music from my audio library, which is located on a USB-connected external drive. It is very convenient since the laptop is always on and requires me to hit just one button to start the music (and wake up the external drive).
 
 Two weeks ago the system hard drive failed. When I installed a replacement drive I looked up its spec and was surprised that it was rated for only 3 years of operation. So now I want to reduce the uptime of the system drive, hoping that I will get a lot more than 3 years out of the laptop.
 
 As for the temperature logging, data is trickling in every minute. Instead of writing it to the system drive I could write the data to a ramdisk and from there, move it to the system drive once a week. So instead of writing continuously to the HDD I would only need one HDD access per week. I am not concerned about loosing data from the ramdisk since I am using a laptop with its battery pack in place.
 
 I used iotop to look what else there is that might keep the system drive from getting some rest and found the following “culprits”:
 
 kjournald
 gconfd-2
 upowerd
 kswapd0
 python
 
 I think python shows only because the iotop monitor is a python program. As for the rest, the daemons, I am not sure as to the longterm consequences (maybe even some risks?) if I disable/stop all of them, especially the journal and swap daemon.
 
 Am I following a reasonable path or am I heading for disaster?
 
 Thanks,
 Hawkoon

---

### Post by HermanAB on 2010-12-20
Howdy,

You got to turn off syslogd else it will never sleep.

---

### Post by tgalati4 on 2010-12-20
You would have to do some major tweaking.  If you don't want to touch the hard disk, then your best bet is to boot off of a LiveCD or USB then run a script that mounts your drive, dumps your data then unmounts your drive.  As long as you have a drive mounted, linux is going to spin it.  Sure it will spin down after a few minutes, but sure enough some process will poke it and it will spin up again.

Or, don't worry about it.  In three years, you will have a different arrangement.  Laptops make poor servers because they are not built for 24/7 operation.

Why not invest in a plug computer and dump the temperature data to a directory on your music drive.

What you currently have is a good demonstration.  Now the next level to find the right hardware to implement it.

---

### Post by Hawkoon on 2010-12-20
> **tgalati4 said:**
> Why not invest in a plug computer and dump the temperature data to a directory on your music drive.

A plug computer might be an option and would probably consume even less power. I would loose the UPS feature though, which is kind of bad for the data. I could collect it on flash memory I suppose, and dump it once a week on the music drive. That could work.

But for now I think I will follow your suggestion on using a USB stick. I don't think a liveCD could work because I need to install extra software for the temperature monitoring. But I can setup an Ubuntu USB stick, possibly even encrypt it (habit of mine). I wonder how responsive the whole system will be. Well, I will give it a try.

---

### Post by elico on 2010-12-20
if you want to make it spin down i really think about some flash\sd drive.

---

### Post by Hawkoon on 2011-01-08
So, since my last post I installed Ubuntu on an 8GB USB stick. Swap resides there as well and the whole setup is encrypted with LUKS and LVM.

I set the laptop's internal drive to spin down after 20min, same for the external USB drive that holds my music.

The whole system is fairly responsive and dead silent. Music serving from the USB drive works fine and the temp logging as well. It is not the fastest flash USB stick I reckon, but booting up seems to take for ages. Luckily I don't need to reboot that often.

---

