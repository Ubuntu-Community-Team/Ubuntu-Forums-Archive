---
title: "Ubuntu server 'Failed to mount Windows share' on another Ubuntu server"
date: 2013-10-12
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2013-10-12
Hi all

Have a Ubuntu Server 12.04 serving a mix of Windows boxes, the Samba shares utilising the 'Guest' account, share access wthout problem.

Some of the shares are USB drives attached to the server, and these USB shares are not accessible to another development Ubuntu Server 12.04 now added to the network.

Messagebox title is 'Unable to mount location', error message text is 'Failed to mount Windows share'.

Any ideas on a workaround, please?

TIA

---

### Post by volkswagner on 2013-10-13
Please post your mount command.

---

### Post by ChrisRChamberlain on 2013-10-13
volkswagner

Thanks for your reply.

Three of the USB drives.
```
[Hitachi]
    path = /media/Hitachi/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
[Maxtor]
    path = /media/Maxtor/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
[Seagate]
    path = /media/SEA_DISC/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
```

---

### Post by volkswagner on 2013-10-13
Actually I asked for your mount command.  I assume you are not using the terminal or /etc/fstab to mount the share.

I assume you are simply using your file manager/browser to access the share's via "Network" locations.

From your file manager (Nautilus) try going to file > connect to server > then use the smb protocol, add server location //fileserver/Seagate, use
nobody as the user and leave password blank.

My guess is when you click the share, your logged in username is being sent.

---

### Post by The Cog on 2013-10-13
Check the permissions of the /media/* directories. You may find that they are only accessible by the logged-in local user. I think this is what happens when removable media is automounted. Even root doesn't have access to them. 
If this is the problem, all I can suggest is that you add the drives to /etc/fstab and get them mounted as more normal drives with more normal permissions.

---

### Post by ChrisRChamberlain on 2013-10-13
The Cog

Thanks for your response.

Following volkswagner's suggestion, the following works:-

File > Connect to Server...

Server: servername
Type:   Windows share
Share:  USB box name
Domain name: WORKGROUP
User name: username
Password: password

So, thanks to both for posting

---

