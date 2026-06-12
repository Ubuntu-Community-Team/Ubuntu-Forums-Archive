---
title: "Linux desktop to Linux Samba; How"
date: 2010-06-23
forum: Server Platforms
---

### Post by jwferk on 2010-06-23
OK - I know I'm just missing something really basic here but I need some suggestions.

I took a retired desktop and installed Ubuntu Server edition 10 to create a home server (mainly for backup and data storage).  The Windows shares work fine and Windows 7 Premium sees all three hard disks on the server.

The dumb part is I can't get my Linux desktop (V10) to see the server.  I can ping the server just fine.  I just can't see any of the harddrives.

The desktop also has samba and samba client installed and up to date.

What idiot thing am I not doing?

Thanks.

---

### Post by doas777 on 2010-06-23
do you get any results when you run this on the desktop machine?
```
smbtree -l
```

do you get prompted for a username/password or do you get any error messages? is teh user account and password the same on the desktop as it is on the windows terminal?
are you pinging by name or IP, and are you using the same token to try to connect via samba?

---

### Post by Mad-One on 2010-06-23
Maybe not the answer you want but could you not just mount the server filesystem using nfs. It's what I do to connect my desktop to my server.

---

### Post by arrrghhh on 2010-06-23
I use NFS as well when it's linux-to-linux.  File permissions are handled in a much better fashion, and the overall transfer speeds are faster.  Plus, IMHO it's much easier to configure than SMB.

Not sure if you can do this with samba shares, but with NFS you can also mount them in fstab so they're available immediately once the computer gets a network connection.

---

### Post by jwferk on 2010-06-29
Thanks for the suggestions.  I've installed nfs4 to handle the Linux/Linux transfers.  It took a little bit but it now works well.

I'd like to make a suggestion to the Linux developers - going Windows to Linux shouldn't be easier to set up than a Linux to Linux connection.  NFS is nice once its up and running but I could very well see how it would frustrate a Newbie.  It would be nice to have at least a GUI rather than having to go into fstab, hosts.allow, export and the other files.  If Gates can set up a one click Networking solution, Linux should have something better.

Just a thought.

---

### Post by arrrghhh on 2010-06-29
Linux isn't so about point-and-click unfortunately... If you want pure PnC, get a Mac.

With that said, there are A LOT of third party tools that help Linux be a little more user-friendly.  Webmin or eBox will help you configure samba and NFS without ever touching a configuration file.  The whole point is, if you want to dig into config files you can.  Linux just needs to develop tools on top of that idea to assist in configuration - they're coming, but again devs focus on what they want - which usually is anything but a GUI.  They just get in the way if you're well-versed.

---

