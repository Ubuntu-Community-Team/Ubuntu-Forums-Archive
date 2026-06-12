---
title: "Canon camera mount issues in 14.04"
date: 2014-03-23
forum: Ubuntu Development Version
---

### Post by pop-gheorghe-y on 2014-03-23
Hi,

For some time I have a issue with my Canon SX160 camera. Till now each time I plugged in my camera in the USB cable a popup window appeared asked my what to do.
 Now this window is not coming and to be able to download photos I need to use photo command line tool. 

This is what lsusb brings:
```
$ lsusb
Bus 002 Device 010: ID 04a9:325a Canon, Inc. PowerShot SX160 IS
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thanks for any suggestions.

---

### Post by ajgreeny on 2014-03-23
With the camera plugged in run command **mount** and report back here the output.

The camera is seen, so we need to know if it's mounted, if so where, and if not, try to figure out why not.

---

### Post by xc3RnbFO8P on 2014-03-23
I able to connect to my Canon Power Shot SX20 IS
using:
gphoto2
Gtkam

In Terminal I start with:
> gphoto2 --list-files
then
> gphoto2 --auto-detect
> rig@rig-Aspire-R3600:~$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Canon PowerShot SX20 IS        usb:001,035   
Open Gtkam> auodetect (output is (usb:001,001)

change it to usb:001,035

---

### Post by pop-gheorghe-y on 2014-03-23
> [COLOR=#000000]I able to connect to my Canon Power Shot SX20 IS[/COLOR]
[COLOR=#000000]using:[/COLOR]
[COLOR=#000000]gphoto2[/COLOR]
[COLOR=#000000]Gtkam[/COLOR]

With this I am also able to connect, but I prefer the nautilus method. This is what gphoto2-autodetect say:
```
gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
USB PTP Class Camera           usb:002,004     

```


This is what mount say:

```

/dev/sda1 on / type ext4 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda2 on /home type ext4 (rw,noatime)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ghita)



```

---

### Post by ajgreeny on 2014-03-23
I suspect your camera is at /run/user/1000/gvfs, as shown in the mount output, as that is an entry I have never seen before, so navigate to that in nautilus and see if you can open it.
```
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ghita)
```

I have never bothered to connect my cameras but always use a card reader instead; much quicker, I think.

---

### Post by NGRhodes on 2014-04-02
I am having the same issue with my camera, works fine in Kubuntu 14.04, but not in Xubuntu 14.04 or Ubuntu 14.04 - I suspect its an issue with GVFS, but not had chance to investigate further.

---

### Post by NZjelle on 2014-04-02
I always use Gigolo for connecting my Canon camera. As promised, Gigolo will mount (almost) anything. I haven't tried it in 14.04 yet, but perhaps you can give it a go.

---

### Post by ronzo on 2014-04-11
Mount shows:
```
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=myuser)
```

If I list the directory content of /run/user/1001 it shows:
```
d????????? ? ?    ?       ?            ? gvfs
```

Even as root, I cannot list the content of directory gvfs

---

### Post by frank18 on 2014-04-11
Hi guys i have a Sony syber cam and i can't see the video files only the pic, is there anything on can do to overcome this? thanks

---

### Post by ventrical on 2014-04-11
I always ignore the first message (do nothing) and choose Mass Storage on my cameras. Never fails. There were some times when I chose shotwell and did not correctly choose 'Mass Storage'  and that will bork it.

  After choosing to (do nothing) I just go to nautilus and open the folder on  the Camera icon.

---

### Post by Masterfbr on 2015-01-02
Thank you! It's work!!!!!!
):P

---

### Post by cariboo on 2015-01-02
Seeing as we are now discussing Vivid Vervet and Trusty point releases, this thread is closed.

---

