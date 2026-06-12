---
title: "virtualbox: ubuntu host, kubuntu guest - share"
date: 2008-04-28
forum: Virtualisation
---

### Post by zorkerz on 2008-04-28
Ok there is so much out there about this i have become very frustrated at not being able to get this to work.

I am trying to share /home on my ubuntu host with the kubuntu guest. I have guest additions installed and I have added /home as a shared folder. 

I believe i need to use this command...
```
sudo mount -t vboxsf sharename mountpoint
```
mountpoint being /mnt/share on my kubuntu guest

I do not know what to put in as the sharename.

I think im on the right track with this. If not all take any others around.
What do i need to do to be able to read/write the /home folder of my ubnutu host with my kubuntu guest?

---

### Post by forestpixie on 2008-06-11
The sharename is the name you gave the shared folder in vbox settings.

Edit this is what I did to mount a shared folder from a ubuntu host in a ubuntu guest

1 - Create the shared folder in vbox settings with name muzak
2 - Open a terminal in the guest and make a directory to mount the shared folder in

I created the folder with 

```
sudo/media/music
```
3 - Then mount the shared folder (which I had named muzak) in the new folder with

```
sudo mount -t vboxsf muzak /media/music
```
4 - Opened nautilus and navigated to /media/music to access files from shared folder

---

### Post by philinux on 2008-06-11
Ok did this , but files in there are all root access only, even with gksudo nautilus I cant copy them elsewhere. :confused:

---

### Post by forestpixie on 2008-06-16
Just reinstalled my virtual as I killed it - I found that the shared folder was owned by root as you did, regardless of whether the option in vbox settings was set as read only.

But I had no problem with gksu nautilus - it copied two folders to the desktop and left them with the correct rights.

Once the folder was mounted with the command I got this with the mount command

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
[COLOR="Red"]music on /media/music type vboxsf (rw[/COLOR])

---

