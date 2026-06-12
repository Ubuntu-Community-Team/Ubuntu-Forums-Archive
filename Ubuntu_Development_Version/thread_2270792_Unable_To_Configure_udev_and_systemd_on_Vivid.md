---
title: "Unable To Configure udev and systemd on Vivid"
date: 2015-03-25
forum: Ubuntu Development Version
---

### Post by cameronbanowsky on 2015-03-25
I cannot configure udev or systemd

```
cam@banowsky:~/rails/lo/db$ sudo dpkg --configure udevSetting up udev (219-4ubuntu10) ...
update-initramfs: deferring update (trigger activated)
insserv: warning: script 'plex' missing LSB tags and overrides
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'mongodb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `mongodb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `mongodb'
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service monit and plex if stopped
insserv:  loop involving service plex at depth 2
insserv:  loop involving service monit at depth 1
insserv: Stopping plex depends on monit and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.103ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-10-generic
Errors were encountered while processing:
 udev
cam@banowsky:~/rails/lo/db$ sudo dpkg-reconfigure udev
sh: 0: getcwd() failed: No such file or directory
sh: 0: getcwd() failed: No such file or directory
/usr/sbin/dpkg-reconfigure: udev is broken or not fully installed



```

I have run 
```

sudo dpkg-reconfigure udev
sudo dpkg-reconfigure systemd
sudo apt-get install -f

```

Every time it gets to this 

```

update-initramfs: Generating /boot/initrd.img-3.19.0-10-generic

```

everything fails.

Any ideas?

---

### Post by cariboo on 2015-03-25
I removed your last post, as any attempt to post an off site script, will be removed, as they have caused problems in the past. If your command has a lot of output, you can use [Ubuntu Pastebin]("http://paste.ubuntu.com/") then provide a link in your post.

**Edit:** One of the  other admins kindly posted the link to your output:

[https://asciinema.org/a/18014](https://asciinema.org/a/18014)

---

### Post by zika on 2015-03-25
What happened before the outputs You gave us?
Why did You try to (re)configure udev?
What did You (and how) install just before these trials of Yours occured?

---

### Post by cameronbanowsky on 2015-03-30
Sorry for such a late response.  I tried all conventional methods i.e.
    apt-get install -f 
or 
    apt-get build-dep udev
    apt-get build-dep systemd
all to no avail.

My solution so those in the future can speed up the fix was to use apt's download function 
   apt-get download systemd
   apt-get download udev
untar those packages and download deps as needed.  Thank you all for the support though.  I am sorry I wasn't around to reply.

---

