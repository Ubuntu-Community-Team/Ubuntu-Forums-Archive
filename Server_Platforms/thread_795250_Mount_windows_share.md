---
title: "Mount windows share"
date: 2008-05-15
forum: Server Platforms
---

### Post by Griffi09 on 2008-05-15
Working with ubuntu server 8, a bit of a novice but trying to learn the command server.  Put my server into an existing windows network.  I want to mount some of those shared volumes, been searching on google but have come up short.

can someone help me with the command.

thanks

---

### Post by HermanAB on 2008-05-15
Hmm, Samba is immensely complicated.  Go to the [http://samba.org](http://samba.org) and look for the Official Howto Guide.  There is also a guide specific to Ubuntu.  Read both guides and buy the book.

Cheers,

Herman

---

### Post by Griffi09 on 2008-05-17
Been working at this for awhile and think i'm getting closer but get an error.  the best command to use so far has been

sudo mount -t ntfs -o username=Administrator,password=password //192.168.1.x/share /mnt/dir


the error:  ntfs-3g failed to access volume no such file or directory.


the directory is shared off win2k3 with permissions for everyone to have full control.

any thoughts?

---

### Post by koenn on 2008-05-17
you can't mount a samba share or windows share as type 'ntfs' : the client (the host where you execute the mount) doesn't see any ntfs filesystem, all it sees is smb packets.

try mount with -t smbfs  or  -t cifs, or smbmount

[http://samba.org/samba/docs/man/manpages-3/smbmount.8.html](http://samba.org/samba/docs/man/manpages-3/smbmount.8.html)

---

### Post by Griffi09 on 2008-05-19
Unfortunately no, still the same error msg.  no matter if i start the command with   mount -t cifs     or mount -t smbfs

using smbmount i get a different error.

"mounting the DFS route for domain not implemented yet No Ipaddress specified or hostname found"

which i don't understand i am specifying the ip address of my 2k3 file server.

any idea's on what i'm doing wrong?

---

### Post by Iowan on 2008-05-19
My latest favorite [link.]("http://ubuntuforums.org/showthread.php?t=800313&highlight=cifs")

---

