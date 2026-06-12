---
title: "File-sharing between Host and Guest OS"
date: 2009-02-28
forum: Virtualisation
---

### Post by boglio on 2009-02-28
I've got VirtualBox-2.1 ose installed on my ubuntu desktop and I'm using WindowsXP as the guest os.

I would like to be able to access files on my Host machine from the Virtual machine!
 
Is this possible?

Edit: How do I mark my threads as solved! I've done it before I believed I went to "Thread tools > Mark thread as solved" but that option isn't there anymore :p

---

### Post by bodhi.zazen on 2009-02-28
IMO the easiest way is to use Samba. Samba should work out of the box between guest and host, use host only networking to increase security or use bridged networking.

---

### Post by albinootje on 2009-02-28
> **boglio said:**
> I've got VirtualBox-2.1 ose installed on my ubuntu desktop and I'm using WindowsXP as the guest os.

I would like to be able to access files on my Host machine from the Virtual machine!


Imho the easiest is the install openssh-server on the host, and then use WinSCP ([http://winscp.sf.net](http://winscp.sf.net)) as client.
The ip-address would be 10.0.2.2 on your host, in case you're using 
the default NAT network option for your guest VM in VirtualBox.

---

### Post by HermanAB on 2009-03-01
My favourite quick and dirty sharing tools are Proftpd and Filezilla.  Note that Filezilla can also do SFTP to a SSH server.  So ssh-server on Ubuntu and Filezilla on Windows is another easy way.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-03-01
Any network protocol (ssh, sshfs, Samba, NFS, FTP, http) will work and they are as easy to learn as are the "Shared Folders" feature of Virtualbox.

---

### Post by kooldino on 2009-03-02
Here's what i just did.

From the XP client, install Guest Additions.

Then under Devices, choose "Shared Folders".

Choose the appropriate folders.

Then under windows explorer, map a network drive and click "browse".  Select from "Virtualbox shared folders".

The odd thing for me is the fact that my /home directory worked fine, but it I tried to share my /home/username directory, it refused connection.  The interesting part is that I can access my /home/username directory if I simply mount the /home.

---

### Post by boglio on 2009-03-02
Thanks for the help guys, I've got things up and running!

---

