---
title: "so ive installed ubuntu server, now what?"
date: 2010-07-14
forum: Server Platforms
---

### Post by jameslogan on 2010-07-14
hi, this is my first attempt at a server using ubuntu.  basically what im looking to do is setup a number of shared drives for accessing music, movies, photos and general files (documents, pdf files etc).  now while a gui would be great, can anyone tell me how to use the command line to setup these shared drives and also how to make the available in both windows and linux.

any help would be greatly appreciated.

thanks

Jim

---

### Post by arrrghhh on 2010-07-14
Well I have a mixed network as well.  I use different protocols depending on the device - but you can use just one.  The reason I use two is one protocol is faster & better (IMHO) but really only works well with Linux boxes (this is NFS).  The other protocol I use is Samba, or SMB.  It will work with any system, but is a little trickier to setup and doesn't transfer as quickly.  Also, I don't think you can mount SMB shares with fstab... I could be wrong there tho!

So onto setting it up.  Everything can be done via the command line... But there are also several GUI options.  For Samba, I always configure it through Webmin - a webUI that allows for all sorts of configuration options on the server.  NFS is a little easier to setup, but can be done via Webmin as well.

I've heard Webmin is not in the repo's any longer, so you may want to look at eBox - it is in the repo's and from what I've heard a fairly good replacement for Webmin.  I personally use Webmin, but I think there was something about how that system updates the actual server that worried some Ubuntu devs, and they pulled it.  I'd like to know more about this, if anyone has insight.

Onto the links:

[Samba guide using Webmin](http://www.webmin.com/samba-howto.html)
[Samba guide using CLI](http://www.debianhelp.co.uk/samba.htm) (it's for Debian, but the similarities to Ubuntu are enormous...)
[NFS configuration](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html) - I'd definitely look at this even if you only have one Linux client.  Much better than Samba!

---

### Post by YesWeCan on 2010-07-14
See also: [https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html)

@arrrghhh: yes you can mount windows network shares in fstab

---

### Post by arrrghhh on 2010-07-14
> **YesWeCan said:**
> @arrrghhh: yes you can mount windows network shares in fstab

Good to know.  I still prefer NFS if I'm using Linux tho :P

---

### Post by YesWeCan on 2010-07-14
[QUOTE=arrrghhh]Good to know.  I still prefer NFS if I'm using Linux tho :P[/QUOTE]
No question. And one can make a linux directory available to Windows Networking via Samba and concurrently export it using NFS for a linux client to mount. Or the linux client user can simply connect to the server using Nautilus (Places/Connect to Server) and have access to the filesystem. Nautilus will also connect to Windows shares.

---

### Post by arrrghhh on 2010-07-14
Certainly, I do that myself.  Thanks for the info, hopefully the OP can use it!

---

### Post by doogy2004 on 2010-07-14
> **arrrghhh said:**
> Also, I don't think you can mount SMB shares with fstab... I could be wrong there tho!

yes you can mount SMB shares in fstab, you would use smbfs.

---

