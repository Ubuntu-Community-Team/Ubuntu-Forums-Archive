---
title: "Ubuntu 15.10 won't boot on NUC5PPYH"
date: 2015-11-01
forum: Server Platforms
---

### Post by kayp8217 on 2015-11-01
Hi everyone, recently I bought NUC5PPYH to play around with.  I tried to install Ubuntu 15.10 on it but the installer never loads completely.  After couple progress movements it just stops.

So I installed Ubuntu 15.10 server on the NUC successfully.  However on the very first boot since installation the machine won't boot completely.  It hags after these messages

> Started Apply Kernel Variables
Started udev coldplug all devices
Mounted POSIX message queue File System
Mounted Debug file system
...
Started udev Kernel Device Manager
...
Started Remount Root and Kernel File Systems
Starting Flush Journal to Persistent Storage...
Reached target Local File System (Pre).
Starting ensure /etc/mtab is a symlink to /proc/mounts...
Starting Load/Save Random Seed...
Started Flush Journal to Persistent Storage.
Started ensure /etc/mtab is a symlink to /proc/mounts.


And then nothing happens.  It just stops there.

I tried to search for problems with nuc5ppyh and ubuntu (or Linux in general) and there are very few matches.  I tried searching for the message "Starting Flush Journal to Persistent Storage AND ubuntu" and all references seemed to be about systemd.

At this point I am not sure if this because of a configuration problem, os problem or hardware problem.

I must say that I was able to get Win 10 installed and up and running on this nuc just fine.

I would appreciate any help.  Thanks in advance.

Here are the specs: [http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc5ppyh.html](http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc5ppyh.html)

- Intel Pentium N3700 (2.4 GHz Quad Core, 6W TDP)
- 4gb RAM - DDR3L SODIMM
- 320 gb HDD
etc

---

### Post by lisati on 2015-11-01
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2015-11-02
So, the server install process finishes correctly, no strange messages or errors during install right? But then it starts booting (which means grub bootloader is there) but it never boots completely.

And it does the same with 14.04 server? Note that non-LTS versions of ubuntu, especially the server, are more or less used to develop stable LTS version. That's why most people recommend for a server using only the LTS versions, even for home servers. Plus the non-LTS have very short support life, only 9 months.

If what you want is the desktop version, you can give it another go. Try with 15.10 to boot it into live mode and also with 14.04. Does live mode boot and work fine? And it fails only when installing?

---

### Post by kayp8217 on 2015-11-02
Yes, the Ubuntu 15.10 live image/installer won't fully startup.  It boots but never fully starts up to show you the Try or Install Ubuntu screen.
Yes, the Ubuntu Server 15.10 installed completely, it boots up (after restarting), the OS is loaded based on the messages, but the OS never loads completely.

I had tried installing Ubuntu Server 14.04.3 but ran into "kernel image not found" issue.  Upon searching around I found and fixed the problem and retried and now Ubuntu Server 14.04.3 is installed and running on the NUC.

I still don't understand Ubuntu Server 14.04.3 would work whereas 15.10 won't.  I strongly suspect this has to do with systemd.

Is anyone out there who have successfully installed Ubuntu 15.10 on the NUC - desktop or server?

---

### Post by sudodus on 2015-11-02
The last message 'Started ensure /etc/mtab is a symlink to /proc/mounts.' rings a bell.

In Xenial Xerus, there is a bug, ['the mtab' bug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1511376)

Maybe (but only maybe) Ubuntu Server 15.10 is affected by it too. You can try if the work-around in comment #9 works.

---

### Post by flocculant on 2015-11-02
> **sudodus said:**
> The last message 'Started ensure /etc/mtab is a symlink to /proc/mounts.' rings a bell.

In Xenial Xerus, there is a bug, ['the mtab' bug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1511376)

Maybe (but only maybe) Ubuntu Server 15.10 is affected by it too. You can try if the work-around in comment #9 works.


Don't forget that the hard fail in Xenial shouldn't affect pre-xenial. Prior to that "We've also shipped "debian-fixup.service" since vivid to turn a file into a symlink on
boot."

[https://lists.ubuntu.com/archives/ubuntu-devel/2015-October/038961.html](https://lists.ubuntu.com/archives/ubuntu-devel/2015-October/038961.html)

---

### Post by kayp8217 on 2015-11-02
thanks sudodus and flocculant for your responses.

---

### Post by Stephen_Fenwick on 2015-11-03
Hi,

I'm having a very similar problem installing Ubuntu 15.10, also on a NUC5PPYH. In summary:
 - Ubuntu 15.10 installer hangs on the splash screen, as OP described
 - Ubuntu 15.04 installs successfully and boots without any problems
 - If I install 15.04 and then upgrade to 15.10 it won't boot
 - The above issues happen with both Ubuntu Desktop 15.10 and lubuntu 15.10. I haven't tried Ubuntu Server
 - The BIOS contains a setting for "Operating System" with values "Windows 7", "Windows 8.x/10" and "Linux". I have no idea what this setting does but if I set it to "Linux" 15.10 boots successfully. However that's not a solution for me as I want to dual boot with Windows 10.

If I boot the installer from USB with console output enabled, the boot process hangs after the following lines:
[ OK ] Mounted /tmp.
systemd-udevd.service
tmp.mount

A photo of the boot screen is here: [https://www.dropbox.com/s/ve8w9x51epplri0/IMG_20151103_174440.jpg?dl=0](https://www.dropbox.com/s/ve8w9x51epplri0/IMG_20151103_174440.jpg?dl=0)

This is from lubuntu 15.10, but Ubuntu Desktop gives similar behaviour.

I'm happy to provide more detailed logs, but will need instructions on how to get the right logs from a usb installer that doesn't complete the boot process.

Thanks for any help you can give.
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1754781")

---

### Post by sudodus on 2015-11-03
@ Kamalesh,

*flocculant*, who reported this bug, told us that this 'mtab' bug should not affect 15.10, but if you want to check, it is easy. This bug is squashed in Xenial Xerus, and the current daily iso files are no longer affected by it. So I think you can download a Xenial daily iso file and find out, if your issues are related to this bug or not. If you still want Ubuntu Server, [find the 64-bit daily iso file here](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/105923/downloads).

If you want to help testing the developing version, you are very welcome at the iso-qa-tracker

[http://iso.qa.ubuntu.com/qatracker](http://iso.qa.ubuntu.com/qatracker)

---

### Post by flocculant on 2015-11-03
What you should do is report the issue you have.

---

