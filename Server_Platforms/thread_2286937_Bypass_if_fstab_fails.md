---
title: "Bypass if fstab fails"
date: 2015-07-15
forum: Server Platforms
---

### Post by ndnd on 2015-07-15
Hi,
It is not possible for me to physically access the server and so anytime fstab fails (due to a drive (External HD) being unavailable it is a big problem for me. I still want the system to continue to boot so that I can ssh into it. 

This is a big pain for me and so far I am not able to figure out the options for fstab or an alternative (there were some packages however the moderator's post has claimed aren't good and may messup the system) so I prefer to use the fstab. 

All the mounted disks are data disks so they can even be mounted systemwide at the end of the bootup process.Mainly after the SSH service so that a failure to mount will not cut off my access. 

I am running Ubuntu 14.XX


Thanks in advance for your help!

PS: Will need details commands so that I am understand

---

### Post by nerdtron on 2015-07-15
What is your current fstab entry? especially the mount options? So the external hard drive is not always connected to the servers?

---

### Post by papibe on 2015-07-15
Hi ndnd.

I have 2 external 1TB, NTFS formatted, USB drives connected to my home server. It is not the best of situations :?

I have a fstab entry for both of them, but I use the 2 settings that have made life a little easier:
[LIST]
[*]The fourth field (fs_mntops) includes **noauto** to avoid being mounted at boot time.
[*]The sixth field (fs_passno) is set to **0** (zero) to avoid any attempt run fsck on it.
[/LIST]
After a reboot, I ssh to the server, and manually mount the disks. I've never had the need for it, but I believe they could be automatically mounted later on using a upstart task, /etc/rc.local, or even an '@reboot' entry on the root crontab.

Hope it helps. Let us know how that goes.
Regards.

---

### Post by ndnd on 2015-07-16
Thanks Nerdrton and papibe

These are my fstab settings 
> 

diskid mountpoint auto defaults



 if I keep noauto does that mean the drives will not get mounted ? If that is the case don't I just comment out the entry?  Or does it mean that this will get mounted at some later point. Also where exactly should the new settings be put (would leaving a space mean one field - I ask this because in my case 'auto is the 3rd field I assume you replace auto with noauto)

> diskid mountpoint noauto ,,0

Isn't there way if the checking or mounting fails one can simply skip that particular disk and go to next one?  

Thanks again!

---

### Post by sudodus on 2015-07-16
The mount option **noauto** means that the partition is not automatically mounted at boot as papibe wrote. ***And it specifies how it will be mounted***, if you try to mount it later on manually or automatically. I agree , that it should be possible to solve your problem with papibe's method (described in post #3).

-o-

I use noauto for some drives, that are sometimes connected to my main computer, and it works very well.

---

### Post by steeldriver on 2015-07-16
... don't forget the nobootwait option

---

### Post by nerdtron on 2015-07-16
These options were used on mounting NFS shares, because at boot time, NFS share can't be mounted unless the network is initialized. Try them as mount options.

auto,_netdev,bg

You can try _netdev only or bg only or both. The _netdev means to wait for network before mounting the drive, the bg option means try to mount the share, if not available, just retry again but still continue to boot up.

---

### Post by papibe on 2015-07-16
This is the fstab entry for one of my drives:
```
# WD My Book external 1TB USB drive
UUID="02D0852FD08529CA" /home/user/media/MyBook    ntfs    **[COLOR="#FF0000"]noauto[/COLOR]**,uid=1000,gid=1000,umask=077 0 **[COLOR="#FF0000"]0[/COLOR]**
```
When my server boots, it won't be check nor mount. However, since there's an entry there, I can later just simple do:
```
sudo mount ~/media/MyBook
```
I hope this example helps.
Regards.

---

