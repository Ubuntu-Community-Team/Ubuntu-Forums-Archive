---
title: "Best partition setup Ubuntu Server ftp"
date: 2008-09-02
forum: Server Platforms
---

### Post by coldbluesteel on 2008-09-02
Building an ftp server for a project. Not gonna be seriously used, just experimenting with building an FTP server.

I have an old Dell Optiplex with a PIII 1G proc, 512M RAM, and a 40G hard drive. Old I know, but should work for my project.

I usually just let the default partitioning work for me, but I have been tasked with building the server with specific parameters such as separate / ./var swap and /home partitions.

For an FTP server with this drive, what would be the best partioning scheme and how do I do this with Ubuntu Server 8.04? I can't see any way in the manual tab do set this up?

Is it better to use the default parameters then change the partitions after install? Or will I be creating more of a headache for myself?

Thanks,

CBS

---

### Post by coldbluesteel on 2008-09-05
Anybody that can help me with this?

CBS

---

### Post by windependence on 2008-09-06
[https://help.ubuntu.com/8.04/installation-guide/i386/partition-sizing.html](https://help.ubuntu.com/8.04/installation-guide/i386/partition-sizing.html)

[https://help.ubuntu.com/8.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/8.04/installation-guide/i386/apcs03.html)

[https://help.ubuntu.com/8.04/installation-guide/i386/partition-programs.html](https://help.ubuntu.com/8.04/installation-guide/i386/partition-programs.html)

The best way would certainly be to partition during the install. You can do this easily by selecting "manual" on the partition screen insteed of "guided" (image attached).

Then set up your partitions as you desire.

Do you know why you want to partition this way? Simnple. If you don't have a separate pertition for /var, this is where your log files are kept and a runaway process can easily fill up your root directory (/) if it is just one big partition, and will shut down your machine. making a separate one will aviod this as only /var will fill up.

You can also do your partitioning after setup. but I don't recommend that as the installer will set up all your mount points for you and write your fstab so that they will all be mounted at boot time.

Good luck!

-Tim

---

