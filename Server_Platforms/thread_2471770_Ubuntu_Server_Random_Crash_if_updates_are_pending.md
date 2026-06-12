---
title: "Ubuntu Server Random Crash if updates are pending"
date: 2022-02-08
forum: Server Platforms
---

### Post by naxal on 2022-02-08
Hello,

I have an Acer Laptop, configuration -> Intel Pentium Quad Core N3530 / 4GB DDR3 (2x2) / 500 GB HDD running Ubuntu Server 20 LTS min installation along with Snap NextCloud & No IP DDNS Client.

System is stable enough but every time there are some OS related update pending, when put under load, this computer would crash.

Running apt upgrade command to complete those update solves the issue and system stays stable even with heavy load. But this wired issue would repeat itself whenever some OS related update is available and pending installation.

I am confused & clueless :confused: 
what is going on with my setup?

Thanks.

---

### Post by LHammonds on 2022-02-09
Could it be related to how much RAM / Swap space you have available under load or file space?

LHammonds

---

### Post by naxal on 2022-02-09
Hello,

> **LHammonds said:**
> Could it be related to how much RAM / Swap space you have available under load or file space?

Here is one such example of heavy load.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289990&stc=1[/IMG]

System is able to run stable without any issues as long as there are no update pending. Weirdly, system would crash, even with half of this load, if there are any updates pending.

Thanks.

---

### Post by LHammonds on 2022-02-09
I have used NextCloud without any issues but my configuration is vastly different from yours.  I do not use snaps.  I have a dedicated mariadb server and a dedicated apache+php+nextcloud server.  Apache and PHP are installed via the repository but I manually install the NextCloud files like any PHP application.

I also don't run my systems for more than 30 minutes with pending updates.  I wrote scripts that do the apt updates around 3:00 am and another script that runs around 3:30am to check if the server needs to reboot and if it does, it cleanly shutsdown the services and reboots the server.

Not sure why the OS would become unstable with the snap package (assuming OS instability since you said the server crashes and not the app).  I will have to let someone else chime in that has snap experience.

LHammonds

---

### Post by naxal on 2022-02-10
Hello,

Thank you for the reply.

Is Ubuntu Server 20 LTS Min Server installation updates itself? I mean is it by default configured to install updates?

I see, it checks for update without my running any update command. Since SSH login screen would show xx updates pending, but does it also installs any such updates without me running the installation command?

Thanks.

---

### Post by LHammonds on 2022-02-11
When you install Ubuntu Server, one of the choices you make right after the hard drive configuration is about automatic updates.  I select "No automatic updates" since I run my own scripts to initiate updates / upgrades.

LHammonds

---

### Post by TheFu on 2022-02-11
I also run Nextcloud and also do not use the snap package. I run it inside a VM with 
1G of RAM
1 vCPU

It was running on a Pentium G3258 (dual core) for years. That's with a MariaDB server and Nextcloud inside the same VM. It actually had 2 other php-webapps too.  I do NOT allow internet access to nextcloud. I consider it too dangerous.  Remote access is possible using a VPN or ssh-SOCKS5 proxy, both are fairly transparent, IME.

I suspect the problem is storage filling up. Full storage is bad on any Unix system. Check that first. Also, I'd check the server logs for attacks.

You may want to consider NOT using the snap package. Have you checked how many versions of the snap are currently installed? I'm guessing here, but **snap info nextcloud** should show them.  There are probably 3+ more and snaps get installed 4x a day, unless the defaults have been changed.  I have it checking snaps once a week, on Saturdays and only retain 1 extra snap, because they won't allow fewer. In general, I avoid snaps.

---

### Post by naxal on 2022-02-13
Hello,

Thanks for the replies,

[QUOTE="LHammonds"]When you install Ubuntu Server, one of the choices you make right after the hard drive configuration is about automatic updates. I select "No automatic updates" since I run my own scripts to initiate updates / upgrades.[/QUOTE]

I am sorry but with the Server Installation ISO of 20.04 LTS, I don't see any such option !!

[QUOTE="TheFu"]I suspect the problem is storage filling up. Full storage is bad on any Unix system.[/QUOTE]

Disc seems to have plenty of free space,

[IMG]https://i.ibb.co/kqZP5YH/001.png[/IMG]

[IMG]https://i.ibb.co/XZ4p3t1/002.png[/IMG]

I am noticing this issue of system crash for last couple of months and pin pointed it to this update related thing. System runs stable even under heavy load as long as I don't see any update pending. But even with moderate load, it would crash when there is any update pending shown in my SSH login page.

I wonder if my installation of Ubuntu is set to update itself and requires a reboot? As I wrote earlier, I didn't notice any option for auto update enable or disable while OS installing. 

> You may want to consider NOT using the snap package

Snap feels very easy for non technical users like me. Simple one command installation and auto update. Easy one command backup and restoration in case of system outage !!

Thanks.

---

### Post by TheFu on 2022-02-13
Please don't post images for text. This isn't Windows. Just copy/paste the text here and save our bandwidth.

If you don't control the snap updates, they are checked 4x a day.  Snaps have a number of problems which haven't been solved, it seems. Enough of us old-timers specifically avoid snaps because those issues still exist. Some of the issue with snaps which have been known and understood since 2017 still exist which I consider no-go reasons.

There's the marketing parts for what snaps are and do
and 
then there's the truth.

BTW, nobody here works for Canonical. We are just long time users sharing our knowledge and experience.

---

