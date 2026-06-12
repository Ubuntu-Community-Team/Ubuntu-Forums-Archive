---
title: "Ubuntu Networking"
date: 2009-09-30
forum: Server Platforms
---

### Post by OldManRiver on 2009-09-30
All,

I have two U boxes.  One is networking just fine and I did nothing to config it.

The other will not config to work with network at all.

I've been through all the HOWTOs for samba and have the two smb.conf files the same except for share names.

When I try to look at windows from this box I get error of:

Unable to mount location
Failed to retrieve share list from server

When I try to look at this U box from Windows I get error of:

\\box-name\\folder-name not accessible
User name could not be found

I have done the normal samba user add of:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

followed by the restart of:

sudo /etc/init.d/samba restart

but still can not get this to work.

Any ideas about why I'm not able to make this work?

Thanks!

OMR

---

### Post by DJonsson2008 on 2009-09-30
A couple of things I found that helped me getting started with Samba.

* Try having the exact username/password on all machines.

* KDE Konqueror, for some reason was more robust in 
  getting me going with shared drives and directories
  than Nautilus.

Experience may vary, but I found the capacity to browse
machines for available drives on Ubuntu was not always 
necessary for connecting to them -- provided one had the
correct addresses, and the same username/password
was the logged on both machines.

---

### Post by swerdna on 2009-09-30
Sounds like firewalls. Compare the firewalls on the two U machines with this command:```
sudo ufw status
```.

You can turn a firewall off with this (just to see if it allows the bad U to see and be seen): ```
sudo ufw disable
```and back on with this:```
sudo ufw enable
```

If you need to, you can set the firewall correctly for Samba using this guide: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #5 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

