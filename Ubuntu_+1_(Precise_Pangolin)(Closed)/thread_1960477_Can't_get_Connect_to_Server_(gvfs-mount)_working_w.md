---
title: "Can't get Connect to Server (gvfs-mount) working with CIFS/SMB"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bing on 2012-04-17
Hi,

I haven't been able to get Connect to Server in Nautilus working with 12.04 amd64 with a CIFS/SMB server.

I am able to mount via command line with smbfs.

The CIFS/SMB server is on a separate domain.

When I use Connect to Server (or gvfs-mount in the command line), and specify the usual user, domain, and password, it fails to connect and asks for them again.

When I do the usual mount command, i.e.,
sudo mount -t //server.com/ /media/mountname -o username=blah,domain=blah.com

...everything works fine.

Since there's a simple way to mount CIFS/SMB on another domain, I don't really care, but it's a peculiar bug.

Any ideas?

---

### Post by dcstar on 2012-04-18
> **bing said:**
> Hi,

I haven't been able to get Connect to Server in Nautilus working with 12.04 amd64 with a CIFS/SMB server.

I am able to mount via command line with smbfs.

The CIFS/SMB server is on a separate domain.

When I use Connect to Server (or gvfs-mount in the command line), and specify the usual user, domain, and password, it fails to connect and asks for them again.

When I do the usual mount command, i.e.,
sudo mount -t //server.com/ /media/mountname -o username=blah,domain=blah.com

...everything works fine.

Since there's a simple way to mount CIFS/SMB on another domain, I don't really care, but it's a peculiar bug.

Any ideas?

Use the IP address.

---

### Post by cariboo on 2012-04-18
This has worked for several users:

> in /etc/samba/smb.conf add the following to the bottom of the [global] section:

client lanman auth = yes
client ntlmv2 auth = no

---

### Post by jcarloscamargo on 2012-04-19
Check your hostname. If it contains hyphens or it is too long it can cause problems with filers and other cifs/smb servers different than Windows. Edit /etc/hostname and change it for something simpler or shorter then reboot and try again.

I've been struggling with that problem for a few days until I stumbled upon the solution. My case is Ubuntu 12.04 amd64 and a Netapp Filer.

---

### Post by Brazen on 2012-04-20
> **cariboo907 said:**
> This has worked for several users:

Your solution worked for me.  Although I don't understand why it would work from the command line and not from Nautilus.  I would think these two settings would affect both.

---

