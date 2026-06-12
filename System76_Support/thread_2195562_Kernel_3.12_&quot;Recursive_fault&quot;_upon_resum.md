---
title: "Kernel 3.12: &quot;Recursive fault&quot; upon resuming from suspend"
date: 2013-12-24
forum: System76 Support
---

### Post by KlipperKyle on 2013-12-24
In Linux Kernel 3.12, Whenever I resume my Gazelle Pro 8 laptop from suspend, everything works normal for ~1 second. Then, everything freezes up (every time). Keyboard and mouse become unresponsive. The only thing I can do is hold the power button to force the laptop off.

As far as I can tell, it is a low level failure while resuming from suspend. If I suspend the laptop from a tty (using pm-suspend), I get a kernel dump ending with "Fixing recursive fault but reboot is needed!"

The only additional boot parameters I have added to grub are "acpi_os_name=Linux acpi_osi=" (The same parameters I believe are added by the System76 driver).

I understand that Linux Kernel 3.12 will not be in Ubuntu main until Ubuntu 14.04 (Trusty). (I am running Arch Linux, so I receive kernels sooner than they appear in Ubuntu.)

**Has anyone running Trusty managed to get suspend and resume working?** Are there some boot parameters I need to add?

For more information, I have a thread open on the Arch BBS: <[https://bbs.archlinux.org/viewtopic.php?pid=1356047](https://bbs.archlinux.org/viewtopic.php?pid=1356047)>

It looks like this person has a similar problem (This person is running Trusty): <[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1247654](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1247654)>

Output of inxi -M:

```

Machine:   Mobo: System76 model: Gazelle Professional version: gazp8
           Bios: American Megatrends version: 4.6.5 date: 09/27/2012

```

To replicate:

[list=1]
[*]Boot Linux 3.12 (I booted Linux 3.12.5.)
[*]Ctrl-Alt-F1 (to get to a tty)
[*]Login
[*]Run sudo pm-suspend (to go into standby)
[*]Close the laptop lid. Reopen it
[*]Kernel dump appears. The system is unresponsive to keyboard input.
[/list]

---

### Post by isantop on 2013-12-26
We're not seeing this in our initial trusty testing. Can you grab a live disk of Trusty and see if you still see the problem? It may just be a bug in Arch's kernel build, or something they aren't including.

---

### Post by KlipperKyle on 2013-12-26
> **isantop said:**
> We're not seeing this in our initial trusty testing. Can you grab a live disk of Trusty and see if you still see the problem?

Will do! I'll let you know what happens.

> **isantop said:**
> It may just be a bug in Arch's kernel build, or something they aren't including.

If it is something in the Arch kernel build, how do I go about isolating it. I do not know much about building kernels (or the options in the Ubuntu and Arch kernels). Is there a specific kernel building tutorial you recommend?

---

### Post by KlipperKyle on 2013-12-27
I just tried suspend in Trusty Tahr, and I am experiencing the same crash.

I downloaded the AMD64 image of Trusty from the daily builds (<http://cdimage.ubuntu.com/daily-live/current/>) and dd'ed it to a memory stick. Then, I booted off of the memory stick into Ubuntu Trusty Tahr.

After Unity loaded, I pressed Ctrl-Alt-F1 to drop to tty1.

```

$ uname -r
3.12.0-7-generic
$

```

OK, so I am using kernel 3.12.

I pressed the suspend button. The system suspended. I closed the lid, waited a few seconds, and opened the lid again. I got the same kernel dump. (See attached photo)

Is there some BIOS upgrade I forgot to do at some point?

---

### Post by stoychev.yavor on 2013-12-31
I experence exactly the same issue with both current Arch Linux and Ubuntu Trusty. I have the same BIOS version as the OP.

---

### Post by untrustytahr on 2013-12-31
I also have the same setup (gaz 8 - Arch 3.12 kernel) that has this exact problem.  I tested with Trusty Tar  3.12.0-7-generic kernel with the same result.
 

 Downgrading to the 3.10 LTS kernel fixes the freezing in the installed Arch system.  Instructions here: [https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability#Install_the_linux-lts_package](https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability#Install_the_linux-lts_package)

 

 I also rolled my own 3.12.6 kernel with the .config settings from the 3.10... didn't fix it.

---

### Post by KlipperKyle on 2013-12-31
> **untrustytahr said:**
> Downgrading to the 3.10 LTS kernel fixes the freezing in the installed Arch system.  Instructions here: [https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability#Install_the_linux-lts_package](https://wiki.archlinux.org/index.php/Enhancing_Arch_Linux_Stability#Install_the_linux-lts_package)

That's exactly what I did as a workaround.

> **untrustytahr said:**
> I also rolled my own 3.12.6 kernel with the .config settings from the 3.10... didn't fix it.

Thanks, I was considering building my own kernel to experiment with some of the build options. Now, I know one configuration that *doesn't* work.

---

### Post by untrustytahr on 2014-01-23
Looks like it's fixed with 3.12.8-1 (at least on mine it is). You might want to give it a try.

---

### Post by KlipperKyle on 2014-01-23
> **untrustytahr said:**
> Looks like it's fixed with 3.12.8-1 (at least on mine it is). You might want to give it a try.

I did. I can suspend and resume, but when resuming, the Ethernet device is mysteriously deleted after a few seconds. See <[https://bbs.archlinux.org/viewtopic.php?pid=1373676#p1373676](https://bbs.archlinux.org/viewtopic.php?pid=1373676#p1373676)>.

---

### Post by untrustytahr on 2014-01-24
> **KlipperKyle said:**
> I did. I can suspend and resume, but when resuming, the Ethernet device is mysteriously deleted after a few seconds. See <[https://bbs.archlinux.org/viewtopic.php?pid=1373676#p1373676](https://bbs.archlinux.org/viewtopic.php?pid=1373676#p1373676)>.

Thanks, I didn't notice and probably wouldn't have until i really needed a wired connection.

---

### Post by llamallama on 2014-01-29
I'm having this problem as well on the Lemur Ultra (lemu) under any distro including Trusty.

---

### Post by llamallama on 2014-01-29
This appears to have been fixed recently. Running 3.12.8 and am no longer having any problems.

---

### Post by KlipperKyle on 2014-01-29
> **llamallama said:**
> This appears to have been fixed recently. Running 3.12.8 and am no longer having any problems.

Did you get Ethernet working after resuming your laptop?

That's the only problem I'm having with 3.12.8 and 3.12.9 right now.

---

### Post by default50 on 2014-02-06
Hi everyone:

I'm running Debian testing and the hangs after suspend have been solved, but the r8169 NIC still disappears after suspend. This is my machine:

```
~ # inxi -M; uname -a
Machine:   Mobo: System76 model: Lemur Ultra version: lemu4 Bios: American Megatrends version: 4.6.5 date: 06/25/2012
Linux omoloko 3.12-1-amd64 #1 SMP Debian 3.12.9-1 (2014-02-01) x86_64 GNU/Linux
```

This is **lspci** output after a resume from suspend, and as you can see the NIC is not even listed.

```

~ $ lspci 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
```

I've found this thread at LKML ([https://lkml.org/lkml/2013/12/12/200](https://lkml.org/lkml/2013/12/12/200)) which seems to be the exact same issue.

Maybe we should open a different thread for this problem only?

---

