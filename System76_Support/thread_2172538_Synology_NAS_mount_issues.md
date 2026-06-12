---
title: "Synology NAS mount issues"
date: 2013-09-05
forum: System76 Support
---

### Post by solotwit on 2013-09-05
Hello, I'm the level past a noob, but just barely. I am trying to get my Synology NAS to mount using NFS. I followed instructions and altered the fstab file, and now when I try to mount -a terminal gives me

mount.nfs:  remote share not in "host:dir" format

now I'm stuck, any ideas?

---

### Post by steeldriver on 2013-09-05
It would be easier to help if you actually posted the fstab file (or at least the offending line)

---

### Post by solotwit on 2013-09-05
That would make sense! Here is what my fstab file is


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=07ce6066-ab66-4938-b6e6-bb43c21ba8d3 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=372ddbe8-ea96-435b-9bb6-02870df0b7c6 none            swap    sw           $
//192.168.2.9/volume1/video /media/video nfs nouser,rsize=8192,wsize=8192,atime,[COLOR=#333333][FONT=georgia]auto,rw,dev,exec,suid 0 0




[/FONT][/COLOR]

---

### Post by steeldriver on 2013-09-05
Your fstab line looks more like a CIFS (SAMBA) style entry - for nfs try

```
**192.168.2.9:/volume1/video** /media/video nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0
```

---

### Post by solotwit on 2013-09-05
Thanks for your help! Now I get this:

mount.nfs: access denied by server while mounting 192.168.2.9:/volume1/video

maybe I should just try CIFS...

---

### Post by solotwit on 2013-09-05
Trying to use CIFS, i have my fstab file like this:

> //droogbase/volume1/video /media/video cifs user, **uid=username,gid=users**,rw,suid,credentials=/etc/cifspwd 0 0


I think uid=admin, but I'm not sure what to put for gid=users?

My other issue is when I try to create the file [COLOR=#000000]etc/cifspwd using command
[/COLOR]echo username=yourusername > /etc/cifspwd
I get the message 
bash: /etc/cifspwd: Permission denied

any help? I've emailed Synology tech support but haven't heard from them yet.

---

### Post by steeldriver on 2013-09-05
I'm pretty much a dunce when it come to CIFS but my *guess* would be that if you are trying to make the mount 'personal' to you, you'd want uid=username,gid=username because Ubuntu uses the 'UPG' (user private group) paradigm. OTOH if you are trying to make the mounted share available to other local users then either 'users' or a new group of your choice such as 'vidusers' that you can add specific people to as required.

To write to a system file like /etc/cifspwd will need elevated privileges - you can either use an editor

```
sudo nano /etc/cifspwd
```

```
gksudo gedit /etc/cifspwd
```

or 

```
echo "username=yourusername" | sudo tee /etc/cifspwd
```

(make that [FONT=courier new]tee -a[/FONT] if you want to append rather than overwrite) or wrap the whole thing in a sudo shell

```
sudo bash -c "echo username=yourusername > /etc/cifspwd"
```

(make the > into >> if you want to append rather than overwrite)

---

### Post by solotwit on 2013-09-05
Thank you steeldriver! This got me pretty close, and is a clear and thorough instruction as to where the code goes and what it does. THANK YOU!  I think i'm going to throw in the towel though. I've put about 8 hours into this and don't really need it. Just something I thought would be useful in the future. It just didn't do what I thought it would.
I was able to access the drive via nautilus > browse the network. AFP (Apple File Protocol?) was what made that happen. What I wanted was a drive to download all torrent files and store/stream all media from using tablets and laptops. It is possible, but not for me, at least not in a reasonable amount of time. I learned a lot though!

---

### Post by steeldriver on 2013-09-05
OK well post back if/when you're ready to have another shot, I have a Netgear NAS on my home network which should be broadly similar (it exports as NFS and CIFS - and can do AFP as well, though that's turned off at the moment)

---

### Post by Eric Goulet on 2013-09-14
I ran into the same trouble when I first started with my new Synology.

> **steeldriver said:**
> **192.168.2.9:/volume1/video** /media/video nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0This is exactly how mine looks... to include the nouser.

> **solotwit said:**
> mount.nfs: access denied by server while mounting 192.168.2.9:/volume1/video

In your Ubuntu terminal, if you run 'showmount -e 192.168.2.9', you should at a minimum see an output of "/volume1/video". If you do not, there is likely an NFS permission issue. You can resolve this by going to the Synology DSM Control Panel => Shared Folder -> Privileges -> NFS Privilege.

---

### Post by fjpos on 2013-10-03
Hi,

You might want to keep AFP (Apple File Protocol) turned off. From my Ubuntu box I could see two network icons for my Synology NAS (as well as other windows machines) which upon checking were for AFP and SMB (samba) network protocol. however the AFP which when turned on through the NAS box was incredibly slow (1.6MB/s transfer speed) while samba was upto 100MB/s. Took me ages to work this out thinking that there was something wrong with Ubuntu.

---

