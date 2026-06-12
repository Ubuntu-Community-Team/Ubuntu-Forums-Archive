---
title: "Setting up Samba on Ubuntu Server 11.04 - No Config File"
date: 2011-09-10
forum: Server Platforms
---

### Post by Wayfarer247 on 2011-09-10
Alright, first the issue:  I have installed samba as such:

```
sudo apt-get install samba smbfs
```

This completes successfully.  I go to edit the config file ```
sudo nano /etc/samba/smb.conf
```, and the "samba" directory is not there.  Nothing in /etc/ that even remotely looks like samba or smbd.  There appears to be no config file, so how can I edit samba?  How can I get my config file back?

Here's some more information that I believe caused this problem.  I had my server running samba last year on Ubuntu 10.10, and everything was fine.  I then shut it down over the summer, and only just recently started using it again.  I upgrade the entire server to 11.04, a few days ago.  I looked at my samba and decided I didn't need it, so I removed it.  I used the --purge option to completely remove it from the server.

However, that didn't delete the config files, so I ```
rm -rf /etc/samba 
``` to get rid of all the files related to samba.

Now, I want to use it again.  I installed samba, but the /etc/samba directory has not been built.  I tried restarting the service, and rebooting the server.  That directory is not being made... so I can't get to the config file.  How can I fix this?

---

### Post by Morbius1 on 2011-09-10
smb.conf doesn't come from the "samba" package. It comes from "samba-common" since smb.conf is used in both the server and client side of samba.

You might want to install "samba-common-bin" while you're at it.

---

### Post by Entilza on 2011-09-10
You can also run

tasksel

At the shell which will bring up a list of common services, where you can just highlight File Server and it will install everything necessary.

---

