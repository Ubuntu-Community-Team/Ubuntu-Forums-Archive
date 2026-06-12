---
title: "GRUB boot screen/TTY resolution"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Zvlwab on 2012-04-11
On Ubuntu 10.10 I had a verbose output when booting with a 1600x900 resolution. I recently updated to (X)ubuntu 12.04 and now I'm unable to fix this.

I installed Ubuntu 10.10 in VirtualBox and I easily managed to set this again, but in Ubuntu 12 I didn't even manage to get this output by copying the same grub.cfg file from my virtual machine. (Except for the kernel version and root id of course).

I do get a verbose output by setting GRUB_GFXMODE=text instead of 1600x900 in /etc/default/grub, but this ruins my bootscreen and tty resolution.

I remember I had the same issue when I tried Ubuntu 11, but I switched back to Ubuntu 10 because I didn't want to use anything but GNOME by then.

---

### Post by howefield on 2012-04-11
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by NHclimber on 2012-04-11
There is not quite enough information to give you definitive help here (eg, what kernel parameters were you using before? on what graphics device? ), but here's a typical setup:

Edit /etc/default/grub and edit the relevant lines to read:
```
GRUB_CMDLINE_LINUX_DEFAULT="video=vesafb:mtrr:2"
....
GRUB_GFXMODE=1600x900
GRUB_GFXPAYLOAD_LINUX=KEEP
```

Then run these commands:
```
sudo update-grub2
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

The "echo FRAMEBUFFER ..." pulls in the framebuffer drivers into the initramfs image so that the framebuffer driver can start earlier in the boot process (on my machine, about 3 secs. in boot or so).  Otherwise, the framebuffer drivers won't start until the rootfs has been mounted (20ish secs on non-SSD boots).

If you need earlier messages than this, I can provide instructions for using the "vga=" kernel boot option as well.

---

### Post by Zvlwab on 2012-04-12
```
GRUB_CMDLINE_LINUX_DEFAULT=""
....
GRUB_GFXMODE=1600x900
GRUB_GFXPAYLOAD_LINUX=KEEP
```

I do have those parameters in /etc/default/grub. When I was running Ubuntu 10.10 they did exactly what I wanted them to do.
Now I'm running Xubuntu 12.04 and I'm just getting a black screen at boot until modemmanager starts with exactly the same parameters.
I'm having this problem on my laptop as well as my pc.

```

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```
That just changed the font of my TTY.

---

### Post by NHclimber on 2012-04-12
The "GRUB_CMDLINE_LINUX_DEFAULT=" values are different???

If you don't specify either a VGA console or a framebuffer, then you're not going to get any output on the graphics mode left over from grub until your graphics driver loads.

---

### Post by Zvlwab on 2012-04-18
```
GRUB_CMDLINE_LINUX_DEFAULT=""
...
GRUB_GFXMODE=1600x900
GRUB_GFXPAYLOAD_LINUX=KEEP
```
Those are the settings that used to work for me running Ubuntu 10.10, but they don't work anymore since I upgraded to 12.04. I also tried GRUB_CMDLINE_LINUX_DEFAULT="video=vesafb:mtrr:2" , but it doesn't really do anything.

---

### Post by NHclimber on 2012-04-18
> **Zvlwab said:**
> Those are the settings that used to work for me running Ubuntu 10.10 [...]


Yes. There were many, many, many changes to the linux kernel in the last year and half. This is one of them.

> **Zvlwab said:**
> I also tried GRUB_CMDLINE_LINUX_DEFAULT="video=vesafb:mtrr:2" , but it doesn't really do anything.

That's interesting. Are you certain you followed my previous instructions?
Of course, as I noted in my earlier post, those instructions were generic because you didn't really provide enough information to receive definitive help.

---

### Post by mhogerheijde on 2012-04-20
I seem to have the same issue. I've followed your (NHclimber) instructions and still my grub and TTY are displaying a horrendous resolution.


My /etc/default/grub (minus comments)
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="video=vesafb:mtrr:2 quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=KEEP

```

I checked using vbeinfo what the allowed resolutions are and this resolution is listed.

I will try other resolutions from that same list to see if it is only spefic for this resolution.

---

