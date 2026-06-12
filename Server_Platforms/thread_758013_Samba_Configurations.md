---
title: "Samba Configurations"
date: 2008-04-17
forum: Server Platforms
---

### Post by jdix123 on 2008-04-17
I've been trying to configure my Samba like this:

I have a partition on the server's hard drive.  I want to be able to access it from any other machine on my LAN without entering a password, and map it as a network drive with a letter on the windows machines.

I want this same partition to be accessible via SSH from machines outside my network.  I've freshly installed 7.1 server and updated it, with Samba and SSH.  I tried to configure Samba using Stormbringer's tutorial here: [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba) but it doesn't seem to be geared towards what I am trying to do.

This is my first attempt at having a server machine with no GUI running, so any help would be greatly appreciated.

---

### Post by ScorpKing on 2008-04-17
in /etc/samba/smb.conf set the option security = user to security = share

---

### Post by tobydeemer on 2008-04-17
HI-
I have a thread dealing with some similar issues here:
[http://ubuntuforums.org/showthread.php?t=738567](http://ubuntuforums.org/showthread.php?t=738567)
that may help, or at least get you going in the right direction.

---

### Post by jdix123 on 2008-04-17
I'm getting a permissions error when trying to save to the share from another machine.

but in my smb.conf I have

read only = no
create mask 0770

---

### Post by jdix123 on 2008-04-23
bump

---

### Post by jdix123 on 2008-04-24
Here is my current smb.conf, though I've tried about a million

```

[global]
guest account = smbguest
log file = /var/log/samba.log
log level = 1
netbios name = Arcshare
security = share
socket options = TCP_NODELAY IPTOS_LOWDELAY
workgroup = arc

[public]
guest ok = yes
guest only = yes
path = /arcshare
read only = no

```

I've added the group and user smbguest to the server machine.  I can view the share from all other machines on the network, but cannot write to them.  I get this error:

"Cannot copy test: Access is Denied.
Make sure that the drive is not full or write protected and that the file is not in use."

I can't figure this out and its driving me crazy.  I've been scouring threads and howtos for weeks now.

---

### Post by Rithmarin on 2008-04-25
Have you checked to see whether the smbguest account has write permissions to the folder you have shared?

What I have done on my system instead of using guest access is set up a normal account with password and just get my desktop to save the access password so it can automatically reconnect. I have seen that on some systems, saving network passwords is disabled, so that might not work for you.

Here's what I use:

[data]
  browseable = yes
  path = /data
  create mask = 0775
  directory mask = 0775
  writeable = yes
  guest ok = no
  public = no
  valid users = @users

Note: in my case I am using "security = user" in global settings and my account was added to the users group.

Rith

---

### Post by jdix123 on 2008-04-25
I'd prefer to have no username or password associated with the share as I'm on a LAN and not worried about outside internet security.  

Anyway, I did get it working with a single username and password, so thanks for your help :)

---

