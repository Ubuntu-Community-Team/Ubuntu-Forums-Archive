---
title: "long uptimes == read errors"
date: 2018-08-10
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2018-08-10
Server / HTPC is an AM1 Kabini quad core. 8gigs of ram, 2tb spinning hard drive (main media storage), 120gb ssd for os, and a 2tb usb 3.0 drive for snapraid parity. OS is Ubuntu 16.04.5 Server LTS. Direct boots to Kodi for media center usage in the living room by way of systemd service.

I've noticed that the longer my uptime gets, I gradually get more and more read errors while watching / listening to media through Kodi. I haven't been able to break 3 weeks of uptime for awhile now because media becomes useless when you have to restart it 3-4 times during a movie, or it just skips half of a song to move to the next one.

I've never bothered to check the logs, I always just reboot and I'm good for a few weeks. How can I solve this? The drives all pass smart tests just fine, with no warnings being emailed to me at all. I originally blamed it on Kodi but that path has run out as I've found this is not a common issue.

It's frustrating at best. There is no reason a linux server should need to be rebooted every couple weeks. Other than power outages that my ups can't last through I've wanted to leave it alone for a few months between software updates and reboot as needed, but I can't.

---

### Post by LHammonds on 2018-08-11
I have been running Linux servers since Ubuntu 10.04 and have only needed to reboot for Kernel updates.  The one exception is Java.  My Minecraft server's performance tends to get worse the longer it is running...mainly because of the memory garbage collection not being perfect or the application's coding...not the OS or hardware itself.

So I cannot guess what the problem might be.  One thing that does tend to get used more over time is swap space.  RAM usage can become fully utilized and swap space is used.  One thing to track is the amount of RAM being used and swap space.

Also, are particular media files that are having an issue playing completely fixed after a reboot?  If that is the case, it is not likely a file / storage issue...but might point towards a RAM issue.

Have you run memtest on it?

Also, you really should examine logs for evidence rather than just guessing.  Sometimes you get lucky and they tell you exactly what the problem is.

LHammonds

---

### Post by Tadaen_Sylvermane on 2018-08-14
Marking as solved. I believe my culprit was vibration.

The htpc / server was mounted on the wall, the wall shakes when the door to the garage slams. Vibration is bad for hard drives. I've always been hard on doors, that one in particular. The wife wanted to move the living room around, this required removing the server & tv from the wall. They are now on an entertainment stand, separate from the wall. I'm at 6 days uptime so far without so much as a whisper of errors on Kodi, save for the debug stuff that is normal. 6 days doesn't sound like a lot but before I was getting the read errors after 2-3 days. Gonna keep it going as long as I can and check the log but I'm beginning to wonder if this has been the issue the entire time based on my short term results thus far.

---

