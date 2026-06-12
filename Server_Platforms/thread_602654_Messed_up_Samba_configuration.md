---
title: "Messed up Samba configuration"
date: 2007-11-04
forum: Server Platforms
---

### Post by Asix on 2007-11-04
Heya everyone,
I'm running Kubuntu Gutsy on my desktop computer, and now I would like to set up Samba server on it, so I could share files with the other three Windows computer in my home network.
I actually have set up Samba, and it worked pretty fine, but then I started experimenting with some Samba configuration, and everything got messed up, so I decided to reinstall Samba and start from scratch.
So I done the following:
```
sudo apt-get remove samba smbfs
```
and that uninstalled everything, but I saw that there's still a folder /etc/samba on my computer, so I removed it manually.
After that, I reinstalled Samba:
```
sudo apt-get install samba smbfs
```
but this time Samba daemon cannot start. I check out the configuration file: ```
sudo kate /etc/samba/smb.conf
``` and it's empty!
How can I fix this? Thanks in advance.

---

### Post by HermanAB on 2007-11-04
Go to the samba web site and get the Official Howto.  It has good examples for every situation.

Cheers,

Herman

---

