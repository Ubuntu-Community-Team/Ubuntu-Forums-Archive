---
title: "Best File Server System"
date: 2009-08-05
forum: Server Platforms
---

### Post by thelethargarian on 2009-08-05
For a couple years now, I have had my old computer (HP Pentium IV Desktop) lying around in the corner. The other day, I realized that I could turn it into a server! It has two 40gb hard drives, 512mb ram, two cd drives and a floppy drive (won't need those much after OS is installed), and all standard ports (ethernet, usb, etc.). My plan is to turn it into an Jaunty Ubuntu Server Edition file server that I can access from any computer with little to no setup on the client computers. I am a webmaster, so I am familiar with FTP and enjoy its simplicity, so I am leaning towards that. I plan to format both drives with ext4 and mount one at root, the other at /home. I was wondering what most people reccomended to use as a simple file server (eg: Samba, FTP, etc.).

Thanks,
thelethargarian

---

### Post by jrollf on 2009-08-05
For local network access i would suggest SAMBA, it will act as an actual file server allowing you to mount directories on the server and use them just like they are local hard drives. Samba will also allow you to control access by both group and individual user levels. 

For internet access I would suggest sFTP with SSH or similar as it is more secure.  Standard FTP does not encrypt you passwords and transmits them in the clear providing a potential security risk.

Just my 2 cents ;)

---

### Post by juancarlospaco on 2009-08-05
SSHfs or NFS, 
Samba and Microsoft protocol that spamm the local network with unnecesary packets.

---

### Post by ugm6hr on 2009-08-05
I would suggest FreeNAS over Ubuntu for a simple home file server.

It has SMB, NFS and FTP options available with a few clicks from its admin web interface.

It also installs on a 128MB USB flash drive (or internal HD) - so takes (almost) no valuable HD space.

See the FreeNAS link below for details.

---

### Post by thelethargarian on 2009-08-05
> **jrollf said:**
> For local network access i would suggest SAMBA, it will act as an actual file server allowing you to mount directories on the server and use them just like they are local hard drives. Samba will also allow you to control access by both group and individual user levels. 

For internet access I would suggest sFTP with SSH or similar as it is more secure.  Standard FTP does not encrypt you passwords and transmits them in the clear providing a potential security risk.

Just my 2 cents ;)

I just researched sFTP a little after you mentioned it and I think I will go with that since it is more secure, though security isn't my biggest concern.

> **ugm6hr said:**
> I would suggest FreeNAS over Ubuntu for a simple home file server.

It has SMB, NFS and FTP options available with a few clicks from its admin web interface.

It also installs on a 128MB USB flash drive (or internal HD) - so takes (almost) no valuable HD space.

See the FreeNAS link below for details.

Thanks for the suggestion, but I am staying with Ubuntu. I have tried all of the other popular distributions (Red Hat, Gentoo, Slackware, Zenwalk, Arch, Suse, Mandriva, Debian (yes I know that Ubuntu is based on Debian) and probably some that I missed) and I have always came back to Xubuntu. It is so trouble free with all of it's auto-configuring, huge repository and other stuff that may be considered worthless junk that slows down their computer to some people.

 Thank you for your help everyone, this is always a very helpful forum :KS.

---

