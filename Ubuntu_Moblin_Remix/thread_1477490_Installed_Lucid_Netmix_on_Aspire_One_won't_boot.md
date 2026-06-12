---
title: "Installed Lucid Netmix on Aspire One won't boot"
date: 2010-05-08
forum: Ubuntu Moblin Remix
---

### Post by johnzbesko on 2010-05-08
I've installed Lucid Netmix on an Acer Aspire One D250. The internal drive is a 40GB Intel SSD. Install went smoothly; upon reboot, a single blinking cursor appears in the upper left corner. The BIOS prompt is quick, but can be interrupted. I also tried re-installing GRUB2 using a chroot shell-no luck, even though GRUB reports no errors.

BTW, the install has errors with the firmware of the wireless ethernet- something about the b43*.fw missing.

Any help or response is greatly appreciated. Searching for help turned up little.

---

### Post by dik23 on 2010-05-09
yeah same issue here with d250 and blinking cursor fresh install

9.10 will install and run but if upgraded will give same error

anyone ?

edit : both are standard 32bit installs, no unr

have kernels 2.6.32-21 and 22 with same results

---

### Post by narnie on 2010-05-10
Bumpidy bump.

Same problem here.

Installed ok on my Acer Aspire one D250-2584 which uses atheros drivers.

On my wife's and two kids' Acer Apire one D250-1165 it stalls on boot (even though it was fine on live-CD)

when booted with quiet removed and nosplash traded for splash, it gets hung at:

```

ata1: SATA max UDMA/133 abar m1024@0x58358000 port 0x58344100 irq 28
ata2: DUMMY
ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 28
ata4: DUMMY

```

It stalls at that point and nothing else happens.

Any ideas?

With thanks,
Narnie

---

### Post by narnie on 2010-05-10
OK, this appears to be the same problem with loading the b43 module.

I'm really surprised that Ubuntu didn't work harder to prevent this hickup before releasing an LTS edition.

Boot using the CD or usb (as my case).

Mount your root partition (I just used nautilus).

then go to your /media dir and see which directory was added and descend this dir.
Under that dir, find

```
etc/modprobe.d/blacklist.conf
```

edit this file with:

```

sudo nano /media/YOURPATHHERE/etc/modprobe.d/blacklist.conf

```

add this line 

```

blacklist b43

```

Save with Ctrl-X, answer yes you want to save and return to keep the filename.

This will allow you to boot to a prompt.

However, it didn't boot graphically for me.

So far I haven't been able to get a gui.

I'll report back as I get further with this. This may be what I was reading about the problem with kernel mode settings (which was implemented for Lucid and will a source of growing pains) with some intel graphics cards.

Yours,
Narnie

---

### Post by narnie on 2010-05-10
It doesn't seem to be the kernel mode setting that is the problem. I have booted with nomodeset to no avail. It still had the same problem.

---

### Post by johnzbesko on 2010-05-11
So, the problem is not with the solid state drive, but rather the wireless device?

This wireless device has been a pain with earlier kernels and versions as well.

---

### Post by narnie on 2010-05-11
Tried another install, this time, it worked without incident after blacklisting b43 in /etc/modprobe.d/blacklist.conf

My wife will be enjoying the new ubuntu colors. My kids can't wait to get theirs fixed :)

Yours,
Narnie

---

### Post by narnie on 2010-05-12
> **johnzbesko said:**
> So, the problem is not with the solid state drive, but rather the wireless device?

This wireless device has been a pain with earlier kernels and versions as well.

It does seem to be a kernel issue, yes.

I think some of these wireless cards based on this chipsets work, but others in the package do not.

Those that use the same cards as these particular Acer Aspire Ones do get caught in the backlash.

I am surprised, though, that UNE isn't tuned to work with priority for these netbooks since it is the netbook distribution. It should default to blacklist this driver IMHO in the UNE version. It is a simple change to /etc/modprobe.d/blacklist.conf that can easily be undone for those few NOT using UNE on a netbook rather than a NO BOOT scenario for us with them.

As another possible workaround short of having to reboot with the live CD.

---

### Post by narnie on 2010-05-12
For those (like me) not wanting to have to boot the live cd and hand edit and reboot, one might try this.

1) When ubuntu starts to boot, hit the "e" key when you see the boot menu (I'm sorry, but all my machines are still dual boot, so if you don't have a menu, I haven't researched how to get to grub editing without a boot menu but if you need it, let me know and I'll research it for you and post back here).

2) This will take you to a grub boot list that should look something like (but probably not exactly like) this:

```
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022a5a8e-c4b4-4117-9301-71cbbfcab264
linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=022a5a8e-c4b4-4117-9301-71cbbfcab264 ro ipv6.disable=1  quiet splash

```

Look for the line that has

```
quiet splash
```

3) Change the "quite splash" to

```
nosplash b43.blacklist=yes ssb.blacklist=yes
```

so that now it looks like

```
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022a5a8e-c4b4-4117-9301-71cbbfcab264
linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=022a5a8e-c4b4-4117-9301-71cbbfcab264 ro ipv6.disable=1  nosplash b43.blacklist=yes ssb.blacklist=yes

```

then hit CTRL-X to initiate the boot

This should blacklist b43 and ssb for you. Then after you boot, you can:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

and add ```
blacklist b43
#and for good measure
blacklist ssb
```

If you are like me, that should get you up and running with your bright, new, pretty, violacious LTS Lucid Lynx Ubuntu Netbook Edition

---

### Post by johnzbesko on 2010-05-12
OK, so I'll try blacklisting b43. Now what do I do for wireless connectivity? The missus ain't gonna like this...

---

### Post by davec64 on 2010-05-12
> **narnie said:**
> For those (like me) not wanting to have to boot the live cd and hand edit and reboot, one might try this.

1) When ubuntu starts to boot, hit the "e" key when you see the boot menu (I'm sorry, **but all my machines are still dual boot, so if you don't have a menu, I haven't researched how to get to grub editing without a boot menu** but if you need it, let me know and I'll research it for you and post back here).


If memory serves me right, hold down the **SHIFT** key to access the grub boot menu. :)

---

### Post by 00b00nt00 on 2010-05-13
I had this problem, too, but it seems to have resolved itself. Either it was the update to the latest kernel or installing the wireless card driver which solved the issue.

---

### Post by narnie on 2010-05-14
> **johnzbesko said:**
> OK, so I'll try blacklisting b43. Now what do I do for wireless connectivity? The missus ain't gonna like this...


Oh. So sorry. Your right. I should have said what to do from here. The proprietary Broadcom drivers need installed. They are in the repos, so this is relatively easy to do, but first you need connectivity.

You have one of two choices, with the first being the easiest by far.

1) If you can hook up to a wired ethernet port, then you're all set. Plug in there and you should shortly be connected to the internet. Once this is so, run System->Administration->Hardware drivers and install the Broadcom STA drivers by selecting and the then hitting the activate button. When it is done, you are just one reboot away from working wireless.

2) Download the script (code included here) that is attached (it is a mashed up scripts modified from the script generated by Synaptic using a usb key and the cdrom calls changed to mirror calls, but modified to save it in your /var/cache/apt/archive directory so that Synaptic can "see it" and not try to download it).

```
#!/bin/sh
cd /var/cache/apt/archives/
#!/bin/sh
cd /var/cache/apt/archives/
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/b/binutils/binutils_2.20.1-3ubuntu5_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/g/gcc-4.4/gcc-4.4_4.4.3-4ubuntu5_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/g/gcc-defaults/gcc_4.4.3-1ubuntu1_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/l/linux/linux-libc-dev_2.6.32-21.32_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/e/eglibc/libc-dev-bin_2.11.1-0ubuntu7_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/m/manpages/manpages-dev_3.23-1_all.deb
sudo wget -c http://mirrors.kernel.org/ubuntu//pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb

```

Save the attachment to a USB. Untar the file (on ubuntu, just right click and select Extract here).

Open up a terminal window.

Change dirs to the file, make it runnable, then run it by:
```

cd PATH_TO_FILE
chmod +x my_download_acer_aspire_one_broadcom_drivers
./my_download_acer_aspire_one_broadcom_drivers
```

You MUST put the "./" in front on the last line, or it won't run. Put in your password (this assumes you have admin rights).

When the files are done downloading, then start up Synaptic. Search for
```

bcmwl-kernel-source
```

Double click it to install and then click the green checkmark to Apply.

When that is done, reboot and you should have a working wireless.

If there are any problems, I'll follow this thread and do my best to help get you up and running.

Cheerio,
Narnie

---

### Post by Fxy on 2010-05-17
Ok guys i don't know if this is of any help but anyway..  If you can reach as far as getting logged into terminal try the following piece of code...
```
startx
```
That piece of code should technically load your graphical desktop environment from the terminal session your currently in...  Has worked great for me on several occasions, with different ubuntu & linux builds :)

---

### Post by narnie on 2010-05-17
> **Fxy said:**
> Ok guys i don't know if this is of any help but anyway..  If you can reach as far as getting logged into terminal try the following piece of code...
```
startx
```
That piece of code should technically load your graphical desktop environment from the terminal session your currently in...  Has worked great for me on several occasions, with different ubuntu & linux builds :)

Not with this bug. It totally halts the boot process. Can't even Alt-Sysrq-REISUB to reboot.

If my steps above are followed, it will boot to the gdm GUI and the user can log in and fix their wireless.

Yours,
Narnie

---

### Post by johnzbesko on 2010-05-21
Success! Though I'm not quite sure what was the key step in making things work.

Blacklisting the b43 (and ssb) seemed to work to allow me to boot from the hard disk. At first, however, I discovered I had to edit the grub entry to not include "quiet splash". I did this because the Acer did not boot, and I wanted to see what was going on. But then it booted?!?

Next, I updated all software packages- including a new kernel version. Again, trouble booting- that's when I blacklisted ssb, as well as b43. It then booted.

I attempted to install restricted drivers, using the gui app. Installing the b43 driver failed, so I tried the STA driver. That worked.

Now the Acer boots (with "quiet splash" included) and the wireless also works.

Thank you to all who replied to this thread.

---

### Post by narnie on 2010-05-21
> **johnzbesko said:**
> Success! Though I'm not quite sure what was the key step in making things work.

Blacklisting the b43 (and ssb) seemed to work to allow me to boot from the hard disk. At first, however, I discovered I had to edit the grub entry to not include "quiet splash". I did this because the Acer did not boot, and I wanted to see what was going on. But then it booted?!?

Next, I updated all software packages- including a new kernel version. Again, trouble booting- that's when I blacklisted ssb, as well as b43. It then booted.

I attempted to install restricted drivers, using the gui app. Installing the b43 driver failed, so I tried the STA driver. That worked.

Now the Acer boots (with "quiet splash" included) and the wireless also works.

Thank you to all who replied to this thread.

Very pleased to hear you got it working. Installing the STA drivers are the key.

I just wish on the netbook edition b43 was blacklisted from the start. It is interesting that removing the "quite splash" sometimes helped. Didn't help on my system, because on these netbooks I do that anyway to see what is going on with a new install when it hangs, but it seemed to work occasionally with Karmic. I usually change the "quite splash" to "nosplash" when I boot when troubleshooting.

I trust your wife will be happy :)

Yours,
Narnie

---

### Post by yurfader on 2010-05-30
Yes, the key is the STA dirver. When I installed the b43 driver I had the boot issue randomly, once I changed it to the STA driver it just worked. I did not blacklisted anything i just installed the STA driver. Hope this helps.

:guitar:

---

### Post by huntspores on 2010-07-28
Same issue, hang at Dummy SATA line or a blank screen with a cursor blinking in the upper left corner on a brand new HP Mini 110 - 1212NR with XP.  The B43 driver would work once every five or six reboots or so.  Replaced the B43 for the STA driver, five reboots in a row and now works like a charm. THX.

---

### Post by fonsi2099 on 2011-03-13
This help from other Ubuntero "Netbook 10.10 doesn't boot up" have worked for me: " I tried re-installing after removing the additional SD card that I have as storage expansion (/dev/mmcblk0), and hey presto! it works.

I conclude that the install process must've installed the grub boot stuff on that disk instead of the main SSD. (And yes, I definitely did the original installation to the /dev/sda1 partition and not to the expansion disk - my data is still intact on that disk.)
:D

---

