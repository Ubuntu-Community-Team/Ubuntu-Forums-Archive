---
title: "More nVidia woes"
date: 2019-07-17
forum: System76 Support
---

### Post by Newbunto on 2019-07-17
OK, so I had Ubuntu 18.04 LTS working well (kernel 4.18.0-25) with nvidia drivers 340.

Then something took it into its head to push out kernel 5.0.0-21 (unclear why, it wasn't me i.e. it wasn't something that I specifically installed).

That's a problem because nvidia 340 does not seem to be compatible with that kernel. During install it fails with something like

[B][FONT=courier new]Building for 5.0.0-21
ERROR (dkms apport) kernel package linux-headers-5.0.0-21-generic is not supported[/FONT][/B]

Kernel 5.0.0-21 (by then the default) then fails to be usable. The early boot is OK but the computer then goes into la la land once it tries to start using graphics i.e. GUI never comes up. Just black screen with 'cursor' in top left.

By using GRUB I can select the previous kernel and that still works well.

From that I tried to install nvidia drivers 430. That installed OK without error (i.e. looks like it's compatible with 5.0.0-21) but doesn't actually work - in the sense that the computer comes up in VGA mode (640x480) i.e. clearly something still wrong. That is good enough access to the computer in order to wipe out '430' and go back to '340' (the network comes up OK too) - and I get back to square 1. Obviously this access is extremely tedious, some applications don't work at all (too wide or too deep or both), others work but not well i.e. it all makes it difficult to debug what is going wrong.

In Ubuntu 16.04 LTS there was a GUI application to manage (nvidia) drivers i.e. show what is installed, which is being used, what is recommended. I can't find that any more in 18.04 LTS. Hints?

Laptop is bonp5. (That's a 1920x1080 screen i.e. nothing too demanding. It's a bit old but I would like to get some more years from it if I can.) I often have an external monitor - 1920x1080 - plugged in, and ideally would use that instead of the built-in display when it is connected.

I think that kernel 5.0.0 is what comes with Ubuntu 19.04 (Disco Dingo). So it looks as if there is some pain in my future when I upgrade from 18.04 to 19.04.

What versions of nvidia drivers actually work at all? What versions of nvidia drivers work with Disco Dingo?

If the answer to either question is 'none', what open source drivers work well enough to a) boot, and b) avoid the dreaded VGA mode.

---

### Post by Bashing-om on 2019-07-17
Newbunto; Hey hey


Hard to say with out knowing the hardware.
Post back:
```

lspci -vnn | grep -i VGA

```

and we see what driver(s) is compatible.

[INDENT]that interface; means a lot
[/INDENT]

---

### Post by Newbunto on 2019-07-17
**[FONT=courier new]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116M [GeForce GT 560M] [10de:1251] (rev a1) (prog-if 00 [VGA controller])[/FONT]**

---

### Post by Bashing-om on 2019-07-17
Newbunto; Well Good !

You want to use the 390 version driver :)
[https://www.nvidia.com/object/IO_32667.html](https://www.nvidia.com/object/IO_32667.html)
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

So now purge all the old Nvidia driver as well as any config file that "might" be in - place,
look:
```

ls -al /etc/X11/Xorg.conf 
ls -al /usr/share/X11/xorg.conf.d/*.conf

```

If there is a Nvidia config file remove it and then:
```

sudo apt remove --purge nvidia*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]should be golden :P
[/INDENT][/INDENT]

---

### Post by Newbunto on 2019-07-18
> You want to use the 390 version driver

I admit that that is one version that I have *not* tried.

> ubuntu-drivers autoinstall

Here's the problem ... that installed 340 (which is what I had before I just purged it) and 340 fails to build with kernel 5.0

So do I want 340 or 390?

---

### Post by Newbunto on 2019-07-18
> **Newbunto said:**
> **[FONT=courier new]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116M [GeForce GT 560M] [10de:1251] (rev a1) (prog-if 00 [VGA controller])[/FONT]**

I don't think "GeForce GT 560M" exists. Don't know whether it is misidentified by **[FONT=courier new]lspci[/FONT]** or in some other way. All other evidence says that it's a GeForce GT_X_ 560M.

---

### Post by ubname on 2019-07-18
Hi, i have GTX 550M and works well with 5xxx kernel nouveau (open source) drivers (less troubles than with the nvidia drivers)
i'm using ubuntu 19.04 though,
newer nvidia drivers they work better with more recent gpu models (like gtx 8xx or gtx 9xx) in my experience.

i'd try to

```
sudo apt remove --purge *nvidia*
```

and reboot.

---

### Post by Newbunto on 2019-07-18
> **ubname said:**
> Hi, i have GTX 550M and works well with 5xxx kernel nouveau (open source) drivers (less troubles than with the nvidia drivers)

That's the fallback position if I can't get it working. nVidia (drivers) seems to be a problem around release upgrades or major kernel version upgrades. Between those times it hasn't given me too many problems.

---

### Post by Newbunto on 2019-07-18
I think I have it working now but there are a few traps for young players.

1. Kernel 4.18 seems to recommend and autoinstall the wrong version (340 rather than 390, and 340 simply doesn't work if I have kernel 5.0 installed as well).

2. There is a subtle unhelpful change in the package name, from nvidia-340 to nvidia-driver-390

3. I probably did need to be more careful with obliterating all traces of the existing drivers before installing a new version, particularly after flailing around and installing lots of different versions.

and the killer

4. If I install '390' under kernel 5.0 it installs it only for kernel 5.0 whereas if I install it under kernel 4.18 it installs it for both itself and kernel 5.0.

Is this an intentional change? Trying to protect me from something bad? An unintentional quirk? Who knows?

I am not sure what I really want but the first time today that I tried the install I did it under kernel 5.0 and so then booting 5.0 gave me the nvidia driver but booting 4.18 gave me the nouveau driver (OK, both worked well enough with limited testing but that doesn't sound logical) - and it is then not possible to install the nvidia driver under 4.18 (already installed - basically does nothing). So I had to remove the driver for the 100th time and reinstall it. Finally everything seems stable and working.

It sure would be nice if one could have multiple video drivers installed and quickly switch between them ... but then if nVidia would just open source their driver, we would only need one driver.

---

