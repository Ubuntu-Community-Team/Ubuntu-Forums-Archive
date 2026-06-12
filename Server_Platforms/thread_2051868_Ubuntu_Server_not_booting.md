---
title: "Ubuntu Server not booting"
date: 2012-09-02
forum: Server Platforms
---

### Post by thnewguy on 2012-09-02
I'm running into an odd problem with Ubuntu Server 12.04. I'm running it on a headless box in my home and using this box as a file server. I typically turn off the server at night and boot it up each morning. I have found that the server will fail to complete its boot process about one out of every three or four days.

Sometimes I can get the server to boot by simply forcing a poweroff and starting it up again. Other times this has not worked and I have resolved the issue by attaching the main drive to a second computer and booting, then returning the drive to my server.

The server is headless, so I can't see what is happening in real time, but I do know that it is got getting far enough in the boot process to start a network connection. (The router's connection information confirms this and I cannot ping the server.)

At first I thought the boot problems might be connected to kernel updates, as they seemed to go hand-in-hand, but the last time the server failed to complete its boot process no upgrades had occurred since the last boot. I also thought drive usage might be an issue, but the partitions around all at 25% capacity or less and less than 6% of the inodes are used on each partition.

This isn't a critical issue, the server only gets minor usage in my home, but it is a bit annoying. Can someone recommend which log(s) I should look at or things I can try to insure the machine boots at each power-up? Thanks.

---

### Post by Bachstelze on 2012-09-02
There's a lot of things that can prevent a computer to boot completely. We can't help you unless you plug in a monitor and give us the error messages you get. Boot-time logs are generally incomplete, but you can look into /var/log/syslog.

---

