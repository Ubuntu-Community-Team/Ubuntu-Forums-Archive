---
title: "Can't play DVDs, libdvdread can't open /"
date: 2008-07-28
forum: System76 Support
---

### Post by andrewdied on 2008-07-28
I have a new serval laptop, running 64 bit ubuntu.  I've read through the various HOWTOs and hints on the forums, including installing medibuntu, libdvdcss2, and even forced my region to 1 (from unset).  When I try to run a movie dvd in movie player, I get:

"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I saw someone run kaffeine from the command line for some error messages, so I tried, too.  Looks like libdvdread thinks my root partition is my dvd player.  How do I switch that?

I also don't even have a ~/.dvdnav directory, but I do have a .dvdcss with some information in it on the DVDs I've put in the drive.  Does that matter?

 libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/andrew/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access

I've also noticed that when I've run install-css.sh I tend to be back-rev'd to 1.2.5 libdvdcss, but that's an aside.

Kaffeine and movie player both can't play it.  Vlc is able to start it, but the playback is awful -- very very choppy, lots of artifacts on the screen.  Strangely, that's a big improvement, since vlc didn't used to be able to play it at all.

Is there any other troubleshooting I can do to help identify the problem and solution?

---

### Post by tuxxy on 2008-07-28
Di you install the ubuntu-restricted-extras package?  This allowed me to run DVD amongst other things;  search for it in the repository or do this in terminal.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by andrewdied on 2008-07-28
> **tuxxy said:**
> Di you install the ubuntu-restricted-extras package?  This allowed me to run DVD amongst other things;  search for it in the repository or do this in terminal.

```
sudo apt-get install ubuntu-restricted-extras
```

Yup, I did that at one point.  I have the latest version, at least according to apt-get.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

BTW, I like the commandline examples.  It makes adding a bunch of packages at once really easy to do.

---

### Post by thomasaaron on 2008-07-29
You might want to try the instructions here...
[http://ubuntuforums.org/showthread.php?t=864720&highlight=dvd](http://ubuntuforums.org/showthread.php?t=864720&highlight=dvd)

---

### Post by darkknight045 on 2008-07-29
I to have had this problem, I installed MPlayer and it fixed that issue.

---

### Post by andrewdied on 2008-07-29
I tried the steps on [http://ubuntuforums.org/showthread.php?t=864720&highlight=dvd](http://ubuntuforums.org/showthread.php?t=864720&highlight=dvd) again, just in case, but that didn't change the answer.  I tried mplayer, too, which showed some *extremely* blocky text on one DVD I hadn't been able to play with, say, kaffeine, but nothing better.

I had also tried the unrestricted extras package, but no different.

Is there any debugging information I can give to help diagnose?  I don't like how the libdvdread library is using / instead of /dev/dvd, or /dev/scd0.

libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication 

```

andrew@ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=andrew)

```

---

### Post by CarlKirkland on 2008-07-31
[FONT="Arial"]Hi Tom,

I hope this finds you well.

A thousand thanks for this post and for your excellent, informative, patient, and gracious support, helping me gain familiarity with Ubuntu and with my new, little Koala.

Totem-Xine in an excellent alternative.

Best regards,
Carl[/FONT]

---

