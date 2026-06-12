---
title: "syntax to automount in fstab"
date: 2006-03-10
forum: Server Platforms
---

### Post by ramdez on 2006-03-10
Hello All, I have an ubuntu file server w/ samba 3 on my little home network.  I have 2 XP machines reading from this.  I setup a kubuntu desktop machine and i'm trying to permanantly map 2 shares from the ubuntu server and 1 from an xp machine.

info
the workgroup is OUR NETWORK
ubuntu server \\ubuntu1\media
xp machine is \\windows\mp3s
accounts on both: uname: temp pwd: temppwd

is the syntax the same to map a samba share and a windows share? (if it's the same then I could just use one example).  I'm hoping I can put this in my fstab and mount it automatically.  I tried using smb4k but it's been having problems. I tried mounting as root but there seems to be a file that's open that smb4k needs to write to and can't, I think that might solve it.

Basically, I'm looking to do this the right way and automount the two shares in my fstab.  Thanks for the info.

update:
is this what i'm looking for for the samba share? what is the "smbfs" for the windows share?
//192.168.0.91/z        /mnt/network/z  smbfs   username=guest,password=,umask=007,uid=1000,gid=1000    0       0

---

### Post by claes on 2006-03-10
It's smbfs to connect to windows too. Or you could try cifs if smbfs don't work.

Claes

---

