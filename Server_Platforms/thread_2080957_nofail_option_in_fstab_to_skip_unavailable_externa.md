---
title: "nofail option in fstab to skip unavailable external drive is not working."
date: 2012-11-05
forum: Server Platforms
---

### Post by donniezazen on 2012-11-05
Hello,

I have an external drive connected to Ubuntu server which I mount using fstab entry. I want to mount when it is available and not when not available and continue boot to OS which get stucks are wait for drive or S for skip or M for manual message.

```
# Western Digital External Drive
UUID=aacc1ddc-911d-42df-a429-c80ea04c598e	/mnt/wd		ext4	defaults,noatime,nofail	0	2
```

I have tried nofail option suggested on [Archlinux]("https://wiki.archlinux.org/index.php/Fstab#External_devices") and [Ubuntu]("http://manpages.ubuntu.com/manpages/precise/man5/fstab.5.html") fstab wiki.
> External devices that are to be mounted when present but ignored if absent may require the nofail option. This prevents errors being reported at boot.
> nofail do not report errors for  this  device  if  it  does  not exist.

I have tried nofail and bg as suggested on this [Ask Ubuntu]("http://askubuntu.com/questions/120/how-do-i-avoid-the-s-to-skip-message-on-boot") thread.

noauto works but problem is that it will not mount my disk when available automatically.

Is there a way I can mount my disk when available and avoid any error on boot when not available.

Thanks.

---

### Post by thnewguy on 2012-11-05
You could put the noauto parameter in the /etc/fstab entry. Then mount the file system later in the boot process. For example, in the /etc/rc.local file you could add the line

mount /dev/device /media/mountpoint &

That will attempt to mount the file system without pausing to wait for a timeout.

---

### Post by donniezazen on 2012-11-05
> **thnewguy said:**
> You could put the noauto parameter in the /etc/fstab entry. Then mount the file system later in the boot process. For example, in the /etc/rc.local file you could add the line

mount /dev/device /media/mountpoint &

That will attempt to mount the file system without pausing to wait for a timeout.

Thanks it does work. It no longer responds to mount -a as I am using noauto function in fstab.

Is it a bug in fstab or am I misunderstanding nofail function?

---

### Post by thnewguy on 2012-11-06
The nofail option simply means errors are not reported. This means trying to mount a device which isn't there may take a long time, but it will not result in an error message. When the documentation says the device will be "ignored" if not present, that just means the mount command doesn't complain if the device isn't there, it doesn't mean the device will be skipped.

---

### Post by donniezazen on 2012-11-06
Thanks for clarifying that.

---

