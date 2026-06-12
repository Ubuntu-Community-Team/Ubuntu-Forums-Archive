---
title: "Cannot access smb share from Windows 10"
date: 2015-10-28
forum: Server Platforms
---

### Post by Robert Finley on 2015-10-28
I have 3 machines on the network, 2 Windows 10 and an Ubuntu 14.04 server. I can access my home folder on the server from one Windows 10 machine but not the other. 'The account is not authorized to log in from this station.'  Is there anything is smb that can be causing this before I start blowing up the Windows forum?

---

### Post by volkswagner on 2015-10-28
Please post your smb.conf and folder permissions for the directory.

```
ls -l /path/to/share
```

smb.conf file has a lot of comments. A friendly way to post the contents is to strip the comments with the following command.

```
cd /etc/samba
sudo testparm -s smb.conf >smb.conf.clean
cat smb.conf.clean
```

If you get permission denied you can switch to root user first with:
```
sudo su
```

---

### Post by TheFu on 2015-10-29
Or just write the output into /tmp/ OR don't use sudo. It isn't needed to run testparm on my boxes.
```

testparm  > /tmp/smb.conf.clean
```
Yep-that worked here.

---

### Post by Robert Finley on 2015-10-30
Thank you for responding.  My problem steamed from the fact that Windows10 employs a new Samba protocol that breaks Linux compatibility.  [Here]("https://social.technet.microsoft.com/Forums/en-US/26e5fd75-f3ab-4ffe-ace4-ed4ba96f82e5/not-discovering-ubuntu-server-on-network?forum=win10itpronetworking") is my fix.

---

