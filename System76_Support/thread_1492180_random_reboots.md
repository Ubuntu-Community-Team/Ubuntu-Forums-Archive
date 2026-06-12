---
title: "random reboots"
date: 2010-05-24
forum: System76 Support
---

### Post by tmurch on 2010-05-24
Hello I have a very odd problem. When my laptop is running on battery power only and I am watching a flash movie or just browsing the web. It will go dark and kick me out to the gui splash login screen. I have no idea why this happens but it never happens while it is plugged in and it is always random. Some days it wont do this other days it will do it all the time. Let me know what kind of logs I can pull to help you with this. 

Tom 

I have a serp6

---

### Post by thomasaaron on 2010-05-24
Hi, Tom.

I'm not absolutely sure the title of this thread corresponds with what you described.

Random reboots means the system is going all the way down and then booting all the way back up... system 76 splash page, ubuntu login page, etc...

If you're not seeing the System76 splash page, then it probably is just crashing X and reverting to a login screen.

Which are you seeing?

The next time it happens, please reboot your machine and *make note of the time when your system is all the way up*. Then, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by reid_rsv869 on 2010-05-25
What kind of Sys76 device are you running?

thanks

Reid

---

### Post by tmurch on 2010-06-22
Your correct it is X crashing. apparently in 10.04 on my serp6 flash and firefox cause the X server to crash. I have tried finding a patch for this on my own but have been unable to get one to work. Any way we could fix this or should I go back to 9.10 where flash actually worked? 

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772)

Tom

Tonight when it crashes while watching youtube I will make the tar for you.

---

