---
title: "samba sharing"
date: 2008-11-05
forum: Server Platforms
---

### Post by Geran on 2008-11-05
Hi,

I created a samba file share by editing the /etc/samba/smb.conf file manually. The file share shows up on the network normally, but when I try to open it, I get this message:

"There is no application that is able to handle this file type"

What is the solution for this?

Thanks 

G

---

### Post by ingeva on 2008-11-06
> **Geran said:**
> 
What is the solution for this?
G

I guess you must install samba too. Save your smb.conf file first or it may be overwritten.

sudo apt-get install samba

and start it:
sudo /etc/init.d/samba start     (or reboot).

inge

---

### Post by Iowan on 2008-11-06
For some reason it didn't occur to me that 
samba-server hadn't been installed.  At least on the older systems I use, samba-client comes installed (fine for reading shares on other systems) but samba-server must be installed.  Sometimes, smbfs must also be installed.

---

### Post by ingeva on 2008-11-07
> **Iowan said:**
> For some reason it didn't occur to me that 
samba-server hadn't been installed.  At least on the older systems I use, samba-client comes installed (fine for reading shares on other systems) but samba-server must be installed.  Sometimes, smbfs must also be installed.

I have to check that.

Thanks!

---

### Post by Geran on 2008-11-07
Cool, there may be a problem with one of those packages, I'll look into it. Thanks folks!

---

