---
title: "Kernel 3.17RC1 hot and on the buffet."
date: 2014-08-23
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2014-08-23
Greetings,
I can't believe this is a week old and not reported. The thing has a much smoother boot process on my intel system. The sequential login screens are fixed. I have one complete freeze-up that even prevented a Ctl Alt F1. Odly the hard reboot didn't corrupt my file system. I have not so far duplicated the freeze. I was in Firefox at the time.

---

### Post by rrnbtter on 2014-08-23
Greetings,
Well, this time it froze on Truecrypt so there has to be a leak somewhere. I'm back on 3.16 at least until the next RC arrives.

---

### Post by craig10x on 2014-08-23
Probably too early in development to be reliable yet ;)

---

### Post by rrnbtter on 2014-08-23
Greetings,
@craig10x,  Yep, which probably explains why no one was hyping it. It is smooth as silk though. The RC2 should be due since this is day seven. Everything that I have right now with 3.16 is really a great system other than those crazy boot screen gyrations.

---

### Post by tista on 2014-08-23
All,
I"ve applied 3.17-rc1 already on my Thinkpad-8 (8.3" BayTrail-T tablet with 64bit UEFI). But I could say that "it didn't run perfect on those BayTrail reference design boards yet". Exactly it comes with native 3D acceleration Mesa/OpenGL as Kernel space intel driver, works acpi-backlight control out of the box, But it still had lots of lacks on hardware compatibilities, something like wireless LAN and bluetooth (brcm4324? maybe), sound (byt-rt5640), ACPI Battery status and much more...

Although we already know that Intel is used to be under heavy developments for our kernel mainline and now on, too. And my Thinkpad-8 has a bit special tuned wireless modules built by Intel and Lenovo together, so wireless kernel space driver issue might be caused in device specific firmware tuning, or not... Anyway BayTrail-T (Z36xx/37xx) and latest kernel could make me fun so much! ;)

[[img]http://s7.postimg.org/v3xvp5iuf/Screenshot_from_2014_08_24_01_18_39.jpg[/img]](http://postimg.org/image/v3xvp5iuf/)

Best Regards,
Tista

---

### Post by WinEunuchs2Unix on 2014-08-26
This looks like a good place to ask my question.  I grabbed the three deb files from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc2-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc2-utopic/) and installed them over Trusty 14.04, Kernel 3.15.10 but upon reboot it just stopped at the grub background wallpaper after selecting the normal Ubuntu boot.

Do I have to install Ubuntu Utopic Unicorn 14.10 first?

Do I have to install Kernel 3.17-rc1 first?

Should I have waited more than 3 minutes before hard power off?

Thanks in advance.

---

### Post by Doug S on 2014-08-26
> **WinEunuchs2Unix said:**
> Do I have to install Ubuntu Utopic Unicorn 14.10 first? No, you shouldn't have to. I have been running 3.17-rc1 on 14.04 since it came out. I am about to try 3.17RC2.
> **WinEunuchs2Unix said:**
> Do I have to install Kernel 3.17-rc1 first?No.
> **WinEunuchs2Unix said:**
> Should I have waited more than 3 minutes before hard power off?No, you shouldn't have to wait at all. I never do.

Edit: Both the Ubuntu 3.17RC2 and the one I compiled from kernel.org are working fine on my test computer.

---

### Post by WinEunuchs2Unix on 2014-08-26
> **Doug S said:**
> No, you shouldn't have to. I have been running 3.17-rc1 on 14.04 since it came out. I am about to try 3.17RC2.
No.
No, you shouldn't have to wait at all. I never do.

By booting a second time I could see debug info that showed it was freezing after ACPI was loaded.

By setting kernel command "acpi=off" it would boot all the way through to the password prompt but the keyboard was unresponsive.

Rebooting back into the older 3.15 versions is now unsuccessful.

Subsequently I'm typing this in Vista 32 :(

Tomorrow I'll be figuring out how to update-grub using the live CD.

Thanks for your reply.

---

### Post by Doug S on 2014-08-26
> **WinEunuchs2Unix said:**
> Rebooting back into the older 3.15 versions is now unsuccessful.That is odd. I can only assume something got clobbered.

---

### Post by lee295012-gmail on 2014-08-26
If you're seeing the desktop freezing under 3.16 and 3.17 with alloc_contig_range kernel errors it's being looked into.
[http://lists.freedesktop.org/archives/dri-devel/2014-August/065842.html](http://lists.freedesktop.org/archives/dri-devel/2014-August/065842.html)

---

### Post by WinEunuchs2Unix on 2014-08-26
> **lee295012-gmail said:**
> If you're seeing the desktop freezing under 3.16 and 3.17 with alloc_contig_range kernel errors it's being looked into.
[http://lists.freedesktop.org/archives/dri-devel/2014-August/065842.html](http://lists.freedesktop.org/archives/dri-devel/2014-August/065842.html)

I'll keep monitoring that bug progress.  Is there a list of all ACPI bugs in 3.17?

---

### Post by lee295012-gmail on 2014-08-26
> **WinEunuchs2Unix said:**
> I'll keep monitoring that bug progress.  Is there a list of all ACPI bugs in 3.17?

not that i'm aware of, added cma=0 to grub suggested with the bug report and so far no problems.

---

### Post by zika on 2014-08-26
```
[COLOR=#000000]Alexey Kardashevskiy (1):[/COLOR][COLOR=#000000]PC, KVM, CMA: Fix regression caused by wrong get_order() use
```
[/COLOR]http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES

---

### Post by rrnbtter on 2014-08-26
Greetings,
Hopefully everyone knows by now that the 3.17RC2 kernel is released and at least on my system working fine (so far). There was a git pull on the 3.17RC2 so that the mentioned bugs and others could be fixed. Also, its release was delayed so as to coincide with Linux's 23 anniversity.

---

### Post by xeizoo on 2014-08-26
It, both RC1 abd RC2, craps out on creating Vbox modules which means it's still unusable for me. I need to have a virtual Win 7 running for certain progs, 3.16.1 thankfully works flawless  ...

---

### Post by WinEunuchs2Unix on 2014-08-26
> **Doug S said:**
> That is odd. I can only assume something got clobbered.

OK got my 3.15.10 back up and running.  It was simple as advanced options boot, 'e' on the version, find "linux" command line, going to end, wiping out "acpi=off", F10 to continue boot.

As far as 3.17-rc2 goes the keyboard is simply dead at the password screen.  Even playing around with grub2 recovery mode where fstab is is read-only mode the down arrow key doesn't work to select options and the enter key to select the top option doesn't work.

I've taken the suggestion "cma=0" and incorporated it into the 3.15.x kernels will no ill-effects.  A little research shows cma "contiguous memory allocation" is something new and probably not used yet to assign huge chunks of memory to device drivers.

Thanks to all the helpful advice to get back up and running again.  Tonight I'll dig around to see how CONFIG_INPUT (or whatever the case may be) works.

EDIT 1: "acpi=off" was just the first step in the kernel override.  The next step was "noapic acpi=off" which brought up an erratic mouse pointer and slow as molasis keyboard that allowed me to enter a password before freezing.  I noticed fewer red "fail" status on the boot splash screen (4 instead of 8)?  Normal 3.15.10 kernel gives 4 red "fail".  One is for bluetooth daemon which I don't use and tried to remove once and that took out network manager and my whole desktop / unity (long story).

Next step is to find pause key for boot splash to read the red "fail" statuses and see if remedying them allows clean 3.17-rc2 boot.

EDIT 2: Some suggest pressing the pause key during boot splash screen to read messages but that only clears the screen.  In /var/log/kern.log sections are filled with copious amounts of "\00" in red.  The line before is Appamor running a profile ironically named "sanitizer_helper".  Reading the appamor man page is giving me a headache, I think I'll throw "White House Down" into the Blu-Ray player.

Setting DEFAULT_GRUB="1>2" sets grub2's default boot to "Advanced Options, Kernel 3.15.10" so unattended the Laptop boots clean without 3.17-rc2.

Using RSDT instead of XSDT in the ACPI tables during kernel configuration didn't help:

```

Aug 26 21:49:59 Satellite-L300 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.15.10-031510-generic root=UUID=*secret?* ro cma=0 acpi=rsdt

```

EDIT 3: I've opened every log I can find and other than being a little slower than 3.15.10 version 3.17-rc2 has far fewer error messages and nothing catastrophic.  Indeed the \00's I saw earlier were most likely created when I hard powered off the machine.

Fascinating.

EDIT 4:

I got it to boot once by unplugging the ASM1042 54mm ExpressCard PCI-e USB 3.0 host controller before booting and plugging it in afterwards.  Was it that or the external SATA drive, or the USB Sound driver, or Kingston 64 GB travel mate or one of the two 4 port hubs?  I'll never know since I couldn't replicate the successful boot.  Weird things with the external mouse not working with built in USB 2.0 port properly but perfectly on the USB 3 card.  I'm going to take a break from this for awhile and go back to complicated Kernel Driver for gm965temp to setup private/public keys for OpenSSL so I can install key rings so I can load the module without tainting the kernel.

Interesting :D

---

### Post by ventrical on 2014-09-01
Just for testing purposes I installed it on a locked down install of Lucid (10.04)  and it is amazing what it has done for it's performance.  It has appeared to eliminate a bottleneck that existed and is working superbly fast and slick. Of course will try on Utopic.

---

### Post by WinEunuchs2Unix on 2014-09-01
> **ventrical said:**
> Just for testing purposes I installed it on a locked down install of Lucid (10.04)  and it is amazing what it has done for it's performance.  It has appeared to eliminate a bottleneck that existed and is working superbly fast and slick. Of course will try on Utopic.

could you elaborate or point to a website that explains a "locked down install"?

FTR I see 3.17-rc3 will have bug fixes for ACPI and file systems that FAIK might clean boot my hardware configuration.

---

### Post by jerrylamos on 2014-09-01
3.17-rc3 amd64 here hangs on boot unless nomodeset is specified on linux boot line.  Nomodeset limits resolution to 1024x768 and other nasties.  Intel Core 2 Duo 3 gHz.

Same with i386.

---

### Post by jerrylamos on 2014-09-01
Somewhere I saw directions for removing the 3.17 kernel?  Any clue?

Thanks.

---

### Post by WinEunuchs2Unix on 2014-09-01
> **jerrylamos said:**
> 3.17-rc3 amd64 here hangs on boot unless nomodeset is specified on linux boot line.  Nomodeset limits resolution to 1024x768 and other nasties.  Intel Core 2 Duo 3 gHz.

Same with i386.

Aah-Haah!!!  Thank you very much for the info.  I can successfully boot my laptop to 3.17-rc2 by simply unplugging my TV (1368x768 res), unplugging my ASM Express card dual USB 3.0 card with two 4 port hubs attached, not using my remote keyboard and mouse and adding the following to the kernel command line in grub:

"nomodeset vt.handoff=7 noapic acpi=off"

My built in display looks horrible at 1024x768 instead of 1280x800 and my Seiko colour enhancements are missing.

Intel Core 2 Duo T5750 @ 2Ghz (50% load factor watching internet TV high res), i915 kernel video driver, GPU whitelisted in Google Chrome / Flash,  GME965 chipset motherboard, Toshiba Satellite L300 with 4GB ram (3 gb usually sitting empty), 8GB swap (usually sitting empty) on 1 TB HDD (you guessed it - mostly empty).

I had my hopes on rc3 to fix issues but as the poster who got an early release of the early release states rc3 still has problems so now I'm hoping on rc4.  *wonders if Linus, Greg K-H, intel employees or Guenter troll Ubuntu forums where Idiots like me post their issues* :D

---

### Post by sammiev on 2014-09-01
rc3 still the same here. nomodeset required here on a fully Intel based system.

---

### Post by Doug S on 2014-09-02
Kernel 3.17RC3 is working fine on my test computer.> **jerrylamos said:**
> Somewhere I saw directions for removing the 3.17 kernel?  Any clue?This is what I would do:```
doug@s15:~$ [COLOR=#ff0000]dpkg -l | grep linux-[/COLOR]
ii  linux-firmware                            1.127.5                              all          Firmware for Linux kernel drivers
ii  linux-firmware-image                      3.11.0-rc6-31                        amd64        Linux kernel firmware, version 3.11.0-rc6
ii  linux-generic                             3.13.0.35.42                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-34                   3.13.0-34.60                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic           3.13.0-34.60                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                   3.13.0-35.62                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic           3.13.0-35.62                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-headers-3.17.0-031700rc3[/COLOR]            3.17.0-031700rc3.201408312235        all          Header files related to Linux kernel version 3.17.0
ii  [COLOR=#ff0000]linux-headers-3.17.0-031700rc3-lowlatency[/COLOR] 3.17.0-031700rc3.201408312235        amd64        Linux kernel headers for version 3.17.0 on 64 bit x86 SMP
ii  linux-headers-3.17.0-rc2                  3.17.0-rc2-155                       amd64        Linux kernel headers for 3.17.0-rc2 on amd64
ii  linux-headers-3.17.0-rc3                  3.17.0-rc3-156                       amd64        Linux kernel headers for 3.17.0-rc3 on amd64
ii  linux-headers-generic                     3.13.0.35.42                         amd64        Generic Linux kernel headers
ii  linux-headers-server                      3.13.0.35.42                         amd64        Transitional package.
ii  linux-image-3.13.0-34-generic             3.13.0-34.60                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic             3.13.0-35.62                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-image-3.17.0-031700rc3-lowlatency[/COLOR]   3.17.0-031700rc3.201408312235        amd64        Linux kernel image for version 3.17.0 on 64 bit x86 SMP
ii  linux-image-3.17.0-rc2                    3.17.0-rc2-155                       amd64        Linux kernel, version 3.17.0-rc2
ii  linux-image-3.17.0-rc3                    3.17.0-rc3-156                       amd64        Linux kernel, version 3.17.0-rc3
ii  linux-image-extra-3.13.0-34-generic       3.13.0-34.60                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic       3.13.0-35.62                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.13.0.35.42                         amd64        Generic Linux kernel image
ii  linux-image-server                        3.13.0.35.42                         amd64        Transitional package.
ii  linux-libc-dev:amd64                      3.13.0-35.62                         amd64        Linux Kernel Headers for development
ii  linux-server                              3.13.0.35.42                         amd64        Transitional package.
doug@s15:~$ [COLOR=#ff0000]sudo dpkg -r linux-headers-3.17.0-031700rc3-lowlatency[/COLOR]
(Reading database ... 229733 files and directories currently installed.)
Removing linux-headers-3.17.0-031700rc3-lowlatency (3.17.0-031700rc3.201408312235) ...
doug@s15:~$[COLOR=#ff0000] sudo dpkg -r linux-headers-3.17.0-031700rc3[/COLOR]
(Reading database ... 215699 files and directories currently installed.)
Removing linux-headers-3.17.0-031700rc3 (3.17.0-031700rc3.201408312235) ...
doug@s15:~$ [COLOR=#ff0000]sudo dpkg -P linux-image-3.17.0-031700rc3-lowlatency[/COLOR]
(Reading database ... 220881 files and directories currently installed.)
Removing linux-image-3.17.0-031700rc3-lowlatency (3.17.0-031700rc3.201408312235) ...
Examining /etc/kernel/prerm.d.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.17.0-031700rc3-lowlatency /boot/vmlinuz-3.17.0-031700rc3-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.17.0-031700rc3-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.17.0-031700rc3-lowlatency /boot/vmlinuz-3.17.0-031700rc3-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.17.0-rc3
Found initrd image: /boot/initrd.img-3.17.0-rc3
Found linux image: /boot/vmlinuz-3.17.0-rc2
Found initrd image: /boot/initrd.img-3.17.0-rc2
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb5
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.17.0-031700rc3-lowlatency (3.17.0-031700rc3.201408312235) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.17.0-031700rc3-lowlatency /boot/vmlinuz-3.17.0-031700rc3-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.17.0-031700rc3-lowlatency /boot/vmlinuz-3.17.0-031700rc3-lowlatency
doug@s15:~$
```

---

### Post by zika on 2014-09-02
Got back from a month of swimming (100km) and walk (100km) sunbathing and rest.
3.17 (999, 994) is a keeper... Nice.

---

### Post by jerrylamos on 2014-09-02
> **jerrylamos said:**
> Somewhere I saw directions for removing the 3.17 kernel?  Any clue?

Thanks.Dead pipe simple.  Boot in nomodeset (ugly) sudo synaptic search linux-image-3.17 completely remove including configuration files.  
Then update-grub if another partition is on the top of the list at grub boot.

BTW, updated to 3.16.0-12 and boots normally, does not need nomodeset.  Waiting for rc4.....

---

### Post by ventrical on 2014-09-02
> **WinEunuchs2Unix said:**
> could you elaborate or point to a website that explains a "locked down install"?

FTR I see 3.17-rc3 will have bug fixes for ACPI and file systems that FAIK might clean boot my hardware configuration.


That's my own venacular. apologies..


[http://ubuntuforums.org/showthread.php?t=2240960](http://ubuntuforums.org/showthread.php?t=2240960)

---

### Post by WinEunuchs2Unix on 2014-09-02
> **ventrical said:**
> That's my own venacular. apologies..


[http://ubuntuforums.org/showthread.php?t=2240960](http://ubuntuforums.org/showthread.php?t=2240960)

No need to apologize I coin my own phrases from time to time too.

I took a quick look at that two web page link with embedded links but I'll need more time later.

  Tonight's project is what the mail man just brought - VGA+Audio in converter to HDMI TV out with HDCP @ 1920x1080p res and 5 Gbps.  Time to dust off those CVT and GTF commands so I can upgrade from TV's maximum 1368x768 vga input :D

---

### Post by zika on 2014-09-03
You've might have noticed that all three rc's were recompiled in mainline PPA.

---

### Post by WinEunuchs2Unix on 2014-09-03
> **zika said:**
> You've might have noticed that all three rc's were recompiled in mainline PPA.

Not sure who this is directed at.  I for one didn't notice the recompile and will try the third version tonight.

---

### Post by jerrylamos on 2014-09-03
> **zika said:**
> You've might have noticed that all three rc's were recompiled in mainline PPA.

Yeah, the mainline ppa has been having fits on my Intel Core 2 Duo.  Since 7/31 on 3.16.0-7 thru 3.16.0-11 at best boot to desktop no unity.  Compiz fails hence unity fail.  From launchpad discussions something in the kernel is causing the Intel driver/compiz problems.  Same install, kernel 3.16.0-6 works.

Updating to 3.16.0-12 is enabling normal operation though a bit shaky.  One out of three partitions I've installed on works O.K.  Note today's .iso is still back on 3.16.0-11 hence fails.  Only way it would boot is with nomodeset on linux boot line. Another person posting on the bugs with different hardware does not get any better operation from 3.16.0-12.

BTW, this is with 64 bit.  32 bit has been working O.K.

Waiting for rc4 if any.

---

### Post by rrnbtter on 2014-09-03
Greetings,
3.17RC3 has been working fine on my system. My problem with RC1 was "freezing" and my problem with RC2 was Truecrypt wouldn't open an encrypted container. So far after three days I have found no problems with the RC3 version nor the 3.17 daily after last Sunday. The 3.16 kernel seems to have it bugs weeded out also. I'm ok with both at this point.

---

### Post by zika on 2014-09-03
> **WinEunuchs2Unix said:**
> Not sure who this is directed at.To Whom it May Concern...
If I wanted to address anybody particular I would have mentioned that.
Information I wanted to share is just an information, nothing more, nothing less.

---

### Post by Doug S on 2014-09-03
> **zika said:**
> You've might have noticed that all three rc's were recompiled in mainline PPA.Thanks for the observation. For RC3 the differences in the config file are:```
doug@s15:~/temp-k-git-3.10rc4/linux$ [COLOR=#ff0000]diff .config-3.17.0-031700rc3-lowlatency .config-3.17.0-031700rc3-lowlatency-new[/COLOR]
149c149
< # CONFIG_BUILD_BIN2C is not set
---
> CONFIG_BUILD_BIN2C=y
554c554,555
< # CONFIG_KEXEC_FILE is not set
---
> CONFIG_KEXEC_FILE=y
> CONFIG_KEXEC_VERIFY_SIG=y
```See also: [https://www.mail-archive.com/kexec@lists.infradead.org/msg11126.html](https://www.mail-archive.com/kexec@lists.infradead.org/msg11126.html)

---

### Post by WinEunuchs2Unix on 2014-09-03
> **zika said:**
> To Whom it May Concern...
If I wanted to address anybody particular I would have mentioned that.
Information I wanted to share is just an information, nothing more, nothing less.

WOW! Didn't mean to offend you and cause a heart attack. Just putting in my 2 cents worth and not sure if the original comment was directed at me or not.

---

### Post by WinEunuchs2Unix on 2014-09-03
> **jerrylamos said:**
> Yeah, the mainline ppa has been having fits on my Intel Core 2 Duo.  Since 7/31 on 3.16.0-7 thru 3.16.0-11 at best boot to desktop no unity.  Compiz fails

. . . .

BTW, this is with 64 bit.  32 bit has been working O.K.

Waiting for rc4 if any.

I checked ubuntu and there are daily builds with "999" instead of "rc3" which came out 3 days ago. I'm not sure which 64 bit version to try next and I don't know if I should try "generic" or "low-latency".  I just installed VGA to HDMI hardware only converter and there's a 1/4 second delay in lip syncing so "low-latency" sounds appealing but it probably won't fix this particular issue and might lead to another can of worms.

Like yourself I've been awaiting rc4 but unlike you I never caught the 3.16.xx trains.  The last one I took was 3.15.10 which I'm very happy with.

Any thoughts on "generic" versus "low-latency" within the 64-bit .deb environment would be great.

---

### Post by Jay_Patel on 2014-09-03
I also tried the RC3 release which was last updated on Sep3.
The touchpad is working OK. I am new to ubuntu so don't know much about the advance topics, But here is what I did:
Went to :  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc3-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc3-utopic/)
Dowloaded files: [linux-headers-3.17.0-031700rc3-generic_3.17.0-031700rc3.201409031132_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.17-rc3-utopic/linux-headers-3.17.0-031700rc3-generic_3.17.0-031700rc3.201409031132_i386.deb")
[linux-headers-3.17.0-031700rc3_3.17.0-031700rc3.201409031132_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.17-rc3-utopic/linux-headers-3.17.0-031700rc3_3.17.0-031700rc3.201409031132_all.deb")
[linux-image-3.17.0-031700rc3-generic_3.17.0-031700rc3.201409031132_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.17-rc3-utopic/linux-image-3.17.0-031700rc3-generic_3.17.0-031700rc3.201409031132_i386.deb")

cd
cd /Downloads
sudo dpkg -i *.deb

then rebooted the system when everything was done.

I did got a message "usb string descriptor 0 malformed...." when I press ctrl+ L at boot screen.
I was scared at that moment, but system booted up OK and guess what, my TOUCHPAD was working.

I don't know this will be helpful to you all genious people here, but just wanted to share my experience..

:)

---

### Post by Doug S on 2014-09-03
> **WinEunuchs2Unix said:**
> Any thoughts on "generic" versus "low-latency" within the 64-bit .deb environment would be great.As far as I know, the only difference between "generic" and "low-latency" is the basic, yet deferrable if the processor is idle, clock tick rate. "generic" uses a 250 Hertz clock tick rate and "low-latency" uses a 1000 Hertz clock tick rate.


@Jay_Patel: Welcome to Ubuntu forums, and thanks for your posting.

---

### Post by WinEunuchs2Unix on 2014-09-03
> **Doug S said:**
> As far as I know, the only difference between "generic" and "low-latency" is the basic, yet deferrable if the processor is idle, clock tick rate. "generic" uses a 250 Hertz clock tick rate and "low-latency" uses a 1000 Hertz clock tick rate.


@Jay_Patel: Welcome to Ubuntu forums, and thanks for your posting.

Thank you for taking your time to respond.  I did a little digging and found this explanation from 2010 as well: [http://ubuntuforums.org/showthread.php?t=1477925](http://ubuntuforums.org/showthread.php?t=1477925)

I'll just quote his summary in case you don't want to click the link:
===========================
[COLOR=#000000][INDENT]So there are four levels of preemption in the linux kernel config - Server (no preemption), Desktop (a little preemption), Low-latency (more preemption), and with the RT patch, Real Time (complete preemption).

It's a fascinating concept, and I usually end up using the RT kernel for eveything, just because I like it and it makes life more fun. Even seeing how much lower my frame rate is on games (and watching the NVidia driver crash occasionally in games on my one machine) is something I find intriguing. (I don't play many games, in case you were wondering.)[/INDENT]
[/COLOR]
[INDENT][FONT=Verdana]:sad:
It's not that I'm anti-social, but the voices in my head won't even talk to me anymore...[/FONT]
[/INDENT]-------------------------------------------------

I've decided to install the low-latency (daily build or rc3?) because I'm having a hard time wrapping my head around blu-ray movies HDCP over HDMI and Windows software vendors selling you the copy protection software to watch the blu-ray movies you've bought or borrowed from the library.  Not to mention blu-ray seems to be as quirky on Linux as newer 802.11n and 802.11ac wifi adapters.

I bought a $70 HDMI blu-ray player and am stalling the $1700 laptop that can do the same (with bugs).  However I need "jackd" to take the TV's audio out signal, route it to my USB C-Media microphone In, process it quickly and output it to the USB C-Media's headphone out so I can watch a movie late at night and not worry about sound pollution to those living close by.

Research reveals that "jackd" needs low-latency to perform well.  Besides rc3 is already broken on my laptop so it'll just be more broken :D

---

### Post by Doug S on 2014-09-04
Yes, since that thread was written server and desktop now use the same kernel.

---

### Post by zika on 2014-09-04
> **WinEunuchs2Unix said:**
> WOW! Didn't mean to offend you and cause a heart attack. Just putting in my 2 cents worth and not sure if the original comment was directed at me or not.Nice of You to care about my heart. But do not, it's OK and it not so easily disturbed...:lolflag:
Be sure that You did not offend me, i just forgot to put a smiley in that post of mine... ;)

About 994 and 999 : No milk today:
```
[COLOR=#000000]*** BUILDING: commit:4144c90b76dfe6eaa2205ac947090786b5091cff series:utopic abinum:994 ...
[/COLOR][COLOR=#000000]fatal: 4144c90b76dfe6eaa2205ac947090786b5091cff is not a valid 'commit' object [/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]build-mainline-one: 4144c90b76dfe6eaa2205ac947090786b5091cff: invalid commit[/COLOR]
```[COLOR=#000000]
[/COLOR]```
[COLOR=#000000]*** BUILDING: commit:44bf091f508913c1c35e70ea96430454c95c78f1 series:utopic abinum:999 ...
[/COLOR][COLOR=#000000]fatal: 44bf091f508913c1c35e70ea96430454c95c78f1 is not a valid 'commit' object
[/COLOR][COLOR=#000000]build-mainline-one: 44bf091f508913c1c35e70ea96430454c95c78f1: invalid commit[/COLOR]
```

---

### Post by pqwoerituytrueiwoq on 2014-09-04
I am testing 3.17.0-031700rc3-generic under 14.04 i managed to get a rather nice lockup on wake from suspend (not 100% reproducible)
on wake, music player was sounding strange, freezing up like there was a massive amount of hdd activity
xscreensaver would not appear on my screen
keyboard was unresponsive (REISUB did nothing)
attempted to restart lightdm, via ssh, still nothing on my screen
reboot via ssh was successful
having recovery buttons attached for my Rpi is so convenient (button -> rPi -> ssh -> desktop -> action)

any chance power fluctuation could have caused it to loose part of the data on the ram? there was a T-Storm last night (my rPi did not loose power so it is unlikely)

Desktop is a i54690k+GTX 650 Ti Boost with a HDD and a SSD

---

### Post by WinEunuchs2Unix on 2014-09-06
> **rrnbtter said:**
> Greetings,
3.17RC3 has been working fine on my system. My problem with RC1 was "freezing" and my problem with RC2 was Truecrypt wouldn't open an encrypted container. So far after three days I have found no problems with the RC3 version nor the 3.17 daily after last Sunday. The 3.16 kernel seems to have it bugs weeded out also. I'm ok with both at this point.

I'm happy for you and 3.17-rc3 but no such luck for me :(.

I installed my first trial of 3.16 (release 3.16.2) a few minutes ago and it booted flawlessly.  No ill-effects with 54mm ExpressCard PCI-e USB 3 with 2 hubs attached, the 32"LCD TV running HDMI through VGA+sound "cheap" converter box, wireless keyboard+mouse, and all the other octopussy gadgets I've already forgotton are added onto this laptop (can we legally still it a laptop???).

I'm confident the guys will have all the 3.17-rc99 quirks worked out by the time it becomes a "real" 3.17.1 release.

The next bleeding edge project might be a smart phone with LINUX, or a personal music player with LINUX.  Of course Ubuntu Utopic Unicorn Unity is still waiting in the wings and I've been thinking of trying Fedora or Gnome or ArchLinux.  I'm looking at a used laptop with Nvidia GPU so I can discover all these new bugs others are experiencing that don't exist on my Intel GME965 GPU with i915 driver.  There could be glitches with the 3630QM Quad Core / 8 threads too.  So many choices to wreck the brain, so little time...

---

### Post by rrnbtter on 2014-09-06
Greetings,
@WinEunuchs2Unix, So this is Linux! You are the master of your own destiny, the architect of your own disaster. Hope you are having as much fun as I am. Sounds like quite a system you have there!

---

### Post by WinEunuchs2Unix on 2014-09-06
> **rrnbtter said:**
> Greetings,
@WinEunuchs2Unix, So this is Linux! You are the master of your own destiny, the architect of your own disaster. Hope you are having as much fun as I am. Sounds like quite a system you have there!

Nice.  Can you squeeze Dreams and Desires into a sonnet / stanza? :D

---

### Post by jerrylamos on 2014-09-08
rc4 booted and ran [http://kernel.ubuntu.com/~kernel-ppa...17-rc4-utopic/](http://kernel.ubuntu.com/~kernel-ppa...17-rc4-utopic/)

On this Intel Core 2 Duo rc1, rc2, rc3 boot hung.  Nothing.  Power off time.

---

### Post by tista on 2014-09-08
In this period, Intel devs seem to focus only for "braswell" (means both haswell and broadwell). Yeah they're breaking some gpio pin-control on baytrail-T today. :( And unfortunately legacy-intel Core family as well maybe.

Anyway rc4 could run on legacy Core2 finally? And I hope they could solve our Baytrail-T issues ASAP.... It's clear that 3.14 must be better than 3.17 series at least on our baytrail obviously.:(

Best Regards,
Tista

---

### Post by mrfelker on 2014-09-08
3.17.rc4 is just out - works fine on my system (VMware ESXi Ubuntu utopic VM)

---

### Post by craig10x on 2014-09-08
I'll bet 3.17 kernel will be finalized about 2 weeks before ubuntu 14.10 is released, the way this is moving along...probably about the time of the 14.10 kernel freeze, so this will probably just miss a chance at being in 14.10 i would imagine...

---

### Post by sammiev on 2014-09-08
> **mrfelker said:**
> 3.17.rc4 is just out - works fine on my system (VMware ESXi Ubuntu utopic VM)

It needs more work, boots fine but very slow boot on a full Intel system. Time to kick it to the curb like the other 3

---

### Post by rrnbtter on 2014-09-09
Greetings,
This kernel 3.17RC4 is running much cooler on my system. In the absence of spoilers I think its a keeper. It seems to be doing a grand job so far.

---

### Post by WinEunuchs2Unix on 2014-09-17
Just installed 3.17-rc5 on a new (old) Dell 17R 7720 SE and no problems booting up.  Didn't have time to try it on the Toshiba Satellite L-300 that had apic, acpi and modeset problems under rc1, rc2 and rc3.  I think rc4 too but can't remember.

The new laptop was challenging with UEFI versus BIOS. Legacy boot with OROM.  MBR (Master Boot Record) vs GPT (G parted partitions).  Windows 7 disappearing from grub2 menu.  Intel accelerated HDD using Raid (IMSM) to SSD which requires MDADM --assemble --scan --metafile=imsm to fix things up.  Unfortunately that answer is rather hard to google.  Next under Linux is dm-cache which should mimic Intel RST (Rapid Storage Technology) ie mechanical /spindle disc caching to sdd.

Hopefully all will work under 3.17-rc5 because booting back into 3.16.2 or 3.15.10 would be time-consuming.

---

### Post by WinEunuchs2Unix on 2014-10-27
Just installed 3.18-rc2 it froze during /usr/share/initramfs-tools/scripts/local-premount.  Based on error message about the swap partition UUID I suspect it is in the resume script.  There are three files in the local-premount directory: fixrtc, ntfs_3g and resume.

Hibernation/Resume is not activated on this hardware (Dell Inspiron 17R 7720 Special Edition, Intel 3630QM (Quad Core), Intel 77hm chipset I think).

Time to set the grub boot default to 3.17.1 (been here, done that).

---

