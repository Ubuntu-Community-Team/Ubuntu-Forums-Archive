---
title: "The Ubuntu server can't log in"
date: 2019-07-18
forum: Server Platforms
---

### Post by sed_faster on 2019-07-18
Hello folks,

I have an server Ubuntu Server 18.04.2 LTS and today when I start up my server the system presented this message "A start job is running for dev-sdb1.device (31s / 1min 30s)". After this time out the log screen stay still and I can't login my system. I don't changed anything on my system or my network/computer. How can I handle this issue?

Thanks

---

### Post by TheFu on 2019-07-18
Check the system log files for more information.
Check the disk SMART data for issues.

Since you are running "Server", I assume you know how to do these things. If you can't boot, the standard solution for that is to boot from alternate media ... i.e. a usb flash drive with a GUI version of the same Ubuntu release.

---

### Post by sed_faster on 2019-07-18
I am a newbie user, but I will googled about this tools and I try fix this situation. However the message and behavior doesn't happen always. I turn the computer and turn on the machine after almost two hours and the computer/system turn on normally. I can't get fixed IP on this server but the system turn on normally.

Thanks  

**Note:** The purpose of this machine is samba file server.

---

### Post by TheFu on 2019-07-18
If you are new to Unix, best to install a desktop distro and load samba that way. For a home user, not providing internet services, there is little/zero problem with this.  Desktop and Server versions are mainly different in the ease-of-use ways ... and whether any GUI is available or not.  Nothing stops typical server packages from being installed, configured and used on the desktop releases.

It will take months for someone new-to-Unix systems to learn enough to run a proper server, if they work at it a few hours a day, EVERY day.  When it comes to Samba, I can only say that if you avoid any GUI for configuring any shares, that is the most stable, fastest, solution.

---

