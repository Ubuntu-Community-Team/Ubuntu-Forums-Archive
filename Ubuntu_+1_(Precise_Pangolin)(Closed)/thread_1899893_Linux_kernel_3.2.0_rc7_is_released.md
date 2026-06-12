---
title: "Linux kernel 3.2.0 rc7 is released"
date: 2011-12-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-12-24
The last release candidate of the kernel 3.2.0 is released today.

> There it is, likely the last -rc in before final 3.2, so please do
check it out in between your holiday festivities.

Most of the changes are faily simple one-liners, but some qla4xxx
driver updates stand out and in fact account for about 40% of the diff
("qla4xxx: fix flash/ddb support"). That, together with a VMWare DRI
driver update and some dvb updates and the regular random driver fixes
means that 80+% of the changes are in drivers.

Some net updates, some SH updates, and then a (tiny) smattering of
other stuff. The appended shortlog gives the (fairly boring) details,

                    Linus

---

### Post by Harry33 on 2011-12-24
And already building in Launchpad.

> linux (3.2.0-7.13) precise; urgency=low    [ Upstream Kernel Changes ]    * rebase to upstream 3.2-rc7Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-7.13](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-7.13)

---

### Post by xyzzyman on 2011-12-24
In the change log in Linus Torvalds post this caught my eye: 

Ajaykumar Hotchandani (1):
      PCI: Set device power state to PCI_D0 for device without native PM support

I wonder how many actual devices that affects.

Anyways currently compiling the ubuntu sources from that link for my Oneirc even though Linus himself said this is mostly little one line driver fixes and nothing in the changelog seems to be related to me. :P

---

### Post by VinDSL on 2011-12-24
Built, and working fine, Harry.

Thanks!  ;)

```
vindsl@Zuul:~$ uname -a
Linux Zuul 3.2.0-7-generic #13-Ubuntu SMP Sat Dec 24 18:04:53 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by cropicko on 2011-12-25
How to install new Kernel?:confused:

---

### Post by dino99 on 2011-12-25
> **cropicko said:**
> How to install new Kernel?:confused:

Find some beer & wait for them into the repo :)

---

### Post by 3vi1 on 2011-12-25
No joy here.  It has [the same problem (bug #901386)]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/901386") as all the other recent 3.2 mainline/final kernels for me:

```

Dec 25 11:09:51 saturn kernel: [    5.570067] nvidia 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 25 11:09:51 saturn kernel: [    5.570073] nvidia 0000:05:00.0: setting latency timer to 64
Dec 25 11:09:51 saturn kernel: [    5.570078] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 25 11:09:51 saturn kernel: [    5.570193] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
...
Dec 25 11:10:04 saturn kernel: [   19.384758] NVRM: RmInitAdapter failed! (0x27:0x38:1193)
Dec 25 11:10:04 saturn kernel: [   19.384766] NVRM: rm_init_adapter(0) failed

```

So, it's back to mainline rc4 (the last one that works on this GTX 560 Ti system with the nvidia blobs).

---

### Post by xyzzyman on 2011-12-25
I just unregistered from that bug as it no longer affects me. purging all the drivers from apt, and running the nvidia installer with the --uninstall option, then rebooting so it used the nouveau driver, then installing the nvidia driver fresh and it's all good for me without any kernel options.

---

### Post by VinDSL on 2011-12-25
> **cropicko said:**
> How to install new Kernel?:confused:
Here's what I do (using the latest Launchpad kernel as an example)...

On this machine (see sig), I downloaded...

```
linux-headers-3.2.0-7_3.2.0-7.13_[COLOR="DarkRed"]all.deb[/COLOR]
linux-headers-3.2.0-7-[COLOR="DarkRed"]generic[/COLOR]_3.2.0-7.13_[COLOR="DarkRed"]i386.deb[/COLOR]
linux-image-3.2.0-7-[COLOR="DarkRed"]generic[/COLOR]_3.2.0-7.13_[COLOR="DarkRed"]i386.deb[/COLOR]
```

[COLOR="Blue"]NOTE[/COLOR]:  Different machines will require different files.  The above files are for a generic 32-bit, i686 install.

I downloaded them to ~/home/*<username>*/Downloads/Kernel

[COLOR="Blue"]NOTE[/COLOR]: In my experience, Firefox (browser) / DownThemAll (extension) is the best method for doing http file transfers. Other browsers (with no download manager) will occasionally allow errors to slip by, e.g. produce corrupt downloads.

Then, I opened a terminal, from my desktop, and navigated to that folder...

```
cd Downloads/Kernel
```


And, finally...

```
sudo dpkg -i *.deb
```


I watch them build, and look for errors.  If there are none, I do a restart.

[COLOR="Blue"]NOTE[/COLOR]: The latest grep has a bug in it that produces the following grub error, at the end of the build...

```
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
```
You can ignore it - no harm - no foul.

That's it!

---

### Post by VinDSL on 2011-12-25
> **dino99 said:**
> Find some beer & wait for them into the repo :)
Haha!  Yeah, that'll work too, although...

I prefer a nice Chardonnay!  ;)

dino99 is, of course, being clever, but he's right.

Waiting for a kernel to hit the repos is the safest (and easiest) way to go - just no bragging rights...

---

### Post by 3vi1 on 2011-12-25
> **xyzzyman said:**
> I just unregistered from that bug as it no longer affects me. purging all the drivers from apt, and running the nvidia installer with the --uninstall option, then rebooting so it used the nouveau driver, then installing the nvidia driver fresh and it's all good for me without any kernel options.

Did you install using nvidia's own packages or something?  I'm tempted to try your fix, but this is on a totally clean install the has *only* ever used the Ubuntu nvidia-current packages.

If yours was the same, but you downloaded the nvidia installer just to do the --uninstall, I might give the same a try.

**EDIT:**  *NM - I found (thanks to another contributer on my bug) the problem is due to the new intel_iommu behavior.  Adding intel_iommu=off in grub works around the issue without any other ill effects.  I'm assuming you've manually installed the nVidia packages and were having issues for some other reason.*

---

### Post by xyzzyman on 2011-12-26
> **3vi1 said:**
> Did you install using nvidia's own packages or something?  I'm tempted to try your fix, but this is on a totally clean install the has *only* ever used the Ubuntu nvidia-current packages.

If yours was the same, but you downloaded the nvidia installer just to do the --uninstall, I might give the same a try.

**EDIT:**  *NM - I found (thanks to another contributer on my bug) the problem is due to the new intel_iommu behavior.  Adding intel_iommu=off in grub works around the issue without any other ill effects.  I'm assuming you've manually installed the nVidia packages and were having issues for some other reason.*

I did a fresh install earlier of oneiric, and first thing I did was update everything. nvidia 173 was auto-installed during installation as I had clicked 'install additional software' or whatever the option is. Soon as I installed rc7 and rebooted, same problems. I first booted with 'single' then purge nvidia, and then in a recovery prompt I installed the nvidia binary (tried --uninstall first just in case and it said nothing to uninstall) and working fine now without any kernel switches. I recently grew a conscious and deleted all my pirated media so I have ALOT of hard drive free to play with so I'll set up a partition just for testing this issue and see what I can figure out this week.

---

