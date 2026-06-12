---
title: "Install on one computer, use on the next."
date: 2010-06-05
forum: Server Platforms
---

### Post by walle1357 on 2010-06-05
Hi folks out there:
So I want to install Ubuntu Server on my server, but I can't move my monitor. What I have tried to do:
1. Install Ubuntu Server onto Computer A.
2. Move Computer A's hard disk into Computer B.
3. Boot Computer B without a monitor.
4. Use SSH to get a remote terminal. This is where my problem is.

Is this possible? I told the installer to install the OpenSSH Server, so it should work, right?
-walle1357

---

### Post by richardjh on 2010-06-05
This would most likely work, unless the hardware was very different.
Can you boot the server from the hard drive?

Have you since put the drive back into machine A and checked the logs for connection attempts, connection errors etc?

I am assuming the problem you are trying to fix here is that you do not have ssh access to your server. Is that correct?

Did you set up ssh server when the drive was in machine A?
Were you able to ssh into localhost on machine A?

---

### Post by walle1357 on 2010-06-05
Yes, on the computer I installed from. Could it be a problem with GRUB? The computer I installed from (Computer A) also had Windows 7 on it, but on a different drive. No, I have not checked the logs for connection attempts. I actually haven't tried SSHing into localhost from machine A. But yes, the problem is that I do not have SSH access to the server.

---

### Post by volkswagner on 2010-06-06
Possibly you installed the bootloader on your Win7 partition?  Do you get a grub menu when booting your windows box?

You should be able to remove your win7 hard disk, and insert only the Ubuntu disk, then reinstall grub, or reinstall from scratch.  You should test booting with just the Ubuntu drive in PC A, before moving to the PC with no monitor.

---

### Post by walle1357 on 2010-06-16
I am positive the bootloader is on the ubuntu HDD. I booted to the ubuntu HDD, and I got grub.

---

### Post by The Real Dave on 2010-06-16
Are you sure your SSHing to the right IP? Did you set up a static IP on the server, or is it just connecting with DHCP?

---

### Post by walle1357 on 2010-06-27
I have DD-WRT on my router, it was showing one other ip, i ssh'ed to that.

---

### Post by littlegreiger on 2010-06-27
Can you ping the server?
If you can't it might have to do with the way Ubuntu handles hardware changes. When you change hardware Ubuntu likes to add a new entry to ```
/etc/udev/rules.d/70-persistent-net.rules
```based on your MAC address, which will have changed when you swapped machines. 

So my suggestion would be to move the drive back to Computer A and edit that file. There should be two entries, you can delete the first one and change the last part of the second one from Name="eth1" to Name="eth0".

---

### Post by walle1357 on 2010-07-02
No I cannot. Oh, sorry about the long time between replies, I don't check every day :)

---

### Post by littlegreiger on 2010-07-02
Ok, if you can't ping the server then try the steps that I outlined in my last post. That's probably what happened and should fix it.

If you have any questions just post back.

---

### Post by walle1357 on 2010-07-12
Will do when I get the chance. Thanks!

---

### Post by walle1357 on 2010-07-31
Solved!

---

