---
title: "Apparmor on livecd"
date: 2010-01-29
forum: Security
---

### Post by tgstrts on 2010-01-29
Hi,

Does anyone know if Apparmor will work on the Ubuntu 10.04 livecd? I know there are currently issues running Apparmor on stacked filesystems with aufs. Currently a casper scripts disables Apparmor during boot up. Would be very useful if it could be run in a live session.

Cheers,

---

### Post by cariboo on 2010-01-29
Lucid is only at alpha 2, so there may be many things that don't work properly yet. I would suggest you wait until the RC until you start testing the Live CD.

---

### Post by bodhi.zazen on 2010-01-29
> **tgstrts said:**
> Hi,

Does anyone know if Apparmor will work on the Ubuntu 10.04 livecd? I know there are currently issues running Apparmor on stacked filesystems with aufs. Currently a casper scripts disables Apparmor during boot up. Would be very useful if it could be run in a live session.

Cheers,

I doubt apparmor will be running by default on any Ubuntu live CD. This is because apparmor is not needed on a live CD, problems with apparmor configuration will cause major headaches, and the CD needs to be customized to enable apparmor.

You almost certainly will need to do a respin.

If you would like, try Zenix =)

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

---

### Post by tgstrts on 2010-01-29
Thanks for your replies. I have actually been customising the ubuntu livecd for some time now, mainly out of curiosity and as a challenge to myself to increase my understanding of linux.

I have managed to install applications that I require, create user accounts with config files in the home directories, and have a set of iptables rules load at startup, amongst other things.

Something I have recently figured out is how to have the /home, /var, and /tmp directories mounted as separate volumes with the 'noexec,nodev,nosuid,noatime' options set. This involves creating 'var.squashfs' and 'home.squashfs' files from the contents of their respective directories, then emptying them in the main filesystem before creating 'filesystem.squashfs'. 

I have then edited the 'casper-helpers' script to mount these as loop devices. '12fstab' and '05mountpoints' scripts in casper-bottom have then been edited to mount the loop devices as the read only directories, to create tmpfs mounts for the read write directories, and finally to mount /home and /var as aufs volumes with these RO and RW branches.

I know this may appear pointless to some but I find I learn more effectively by trying to work things out. I would now like to get apparmor working on the livecd but it sounds like it may be too difficult........

---

### Post by bodhi.zazen on 2010-01-29
> **tgstrts said:**
> Thanks for your replies. I have actually been customising the ubuntu livecd for some time now, mainly out of curiosity and as a challenge to myself to increase my understanding of linux.

I have managed to install applications that I require, create user accounts with config files in the home directories, and have a set of iptables rules load at startup, amongst other things.

Something I have recently figured out is how to have the /home, /var, and /tmp directories mounted as separate volumes with the 'noexec,nodev,nosuid,noatime' options set. This involves creating 'var.squashfs' and 'home.squashfs' files from the contents of their respective directories, then emptying them in the main filesystem before creating 'filesystem.squashfs'. 

I have then edited the 'casper-helpers' script to mount these as loop devices. '12fstab' and '05mountpoints' scripts in casper-bottom have then been edited to mount the loop devices as the read only directories, to create tmpfs mounts for the read write directories, and finally to mount /home and /var as aufs volumes with these RO and RW branches.

I know this may appear pointless to some but I find I learn more effectively by trying to work things out. I would now like to get apparmor working on the livecd but it sounds like it may be too difficult........

You need to modify the apparmor profiles so they run on the live CD, again see the Zenix CD ;)

---

