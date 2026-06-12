---
title: "NFS vs. SMB - fstab"
date: 2009-05-11
forum: Server Platforms
---

### Post by roadrunner84 on 2009-05-11
hi!
i've got a little question about nfs and smb.
now, we use ubuntu server edition for our edi system with our customers. in this server edition, there is a nfs mount to an existing unix machine. but this unix machine only runs till the end of this month , then it will be turned off.
so i edited the fstab file and created a mount point over smb/cif to a windows server share, where the new data will be stored for our new system (it has to be on this server, so the programming guy said). my test with storing data worked great.
fstab info: 
# SMB
//ntflatz/EDI /home/edi.test cifs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

my question is, can i use smb? are there problems?
or will it be better to install unix services on the windows server and mount it again over nfs?

now situation:
ubuntu server (nfs) - unix server

later situation:
ubuntu server (smb) - windows server
or 
ubuntu server (nfs) - windows server

i hope that a linux expert can help me. :) i'm new to linux, but i want to learn it :)

thanks for every answer.


stefan

---

### Post by roadrunner84 on 2009-05-14
hi!

has nobody a tip for me?

Stefan

---

### Post by HermanAB on 2009-05-14
Yes, it will work.  However, samba connections are a bitmore difficult to get to work than NFS, but here is a debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

### Post by roadrunner84 on 2009-05-18
hi! thanks for the information how to debug ist.
but smb is working from the linux to the windows server.

can i leave it with smb or will it be better to use nfs?

---

