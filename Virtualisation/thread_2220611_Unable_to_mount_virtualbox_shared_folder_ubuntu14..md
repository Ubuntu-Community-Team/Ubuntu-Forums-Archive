---
title: "Unable to mount virtualbox shared folder ubuntu14.04"
date: 2014-04-28
forum: Virtualisation
---

### Post by nick_r2 on 2014-04-28
I successfully installed guest additions on ubuntu 14.04 but the /sbin/mount.vboxsf links to /usr/lib/VBoxGuestAdditions/mount.vboxsf which doesn't exsist. So I get the following errors running the commands.
```
sudo /sbin/mount.vboxsf $sharename /home/user/$sharename
sudo: /sbin/mount.vboxsf: command not found
```
```
sudo mount -t vboxsf $sharename /home/user/$sharename
mount: wrong fs type, bad option, bad superblock on $sharename,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Any Ideas on what I did wrong or what I should try?

---

### Post by jdeca57 on 2014-04-29
The easiest way to use shared folders in Ubuntu - mind this is my opinion and the way it works for me - is to use auto-mount. You can find that when you create a shared folder in the Virtualbox host program.

Once this is active, there exists a folder in /media: /media/sf_sharename that can be made read/write by adding your username in /etc/group after the vboxsf entry. (adding yourself to the group vboxsf) 

This solution simply works and you never have to worry about mounting because the share is always available.

---

### Post by nick_r2 on 2014-04-29
Thankyou, Your solution works great. I'll be using it.
I'm still curious though why mount.vboxsf doesn't install properly using the guest additions CD, although I don't need that now that I'm using the auto-mount method.

---

### Post by jdeca57 on 2014-04-29
To be honest, mostly I stop searching when I find a solution. ;-) But the shared folder question in Virtualbox isn't straightforward. For example, with a Manjaro guest this solution doesn't work. But manually mounting does and if you put the right line in /etc/fstab then it mounts automatically in Manjaro. The moment Ubuntu uses systemd (as announced and it's what Manjaro uses) I guess this answer will be different.

---

### Post by nick_r2 on 2014-04-29
OK well in older versions of ubuntu it worked...

I now know or have what I needed so I'll mark this thread solved.
Thanks again for your replies.

---

