---
title: "Connect to Server"
date: 2012-06-23
forum: Server Platforms
---

### Post by Jacob72 on 2012-06-23
I am running 12.04, I am using the Gnome installation.

I am failing to find a free editor that I can use to synchronise multiple sites, locally and remotely. 

How does the Ubuntu's own Connect to Server option work? Can I build up multiple sites and save all the connection details so they can be accessed again without having to manually add them each time?

---

### Post by darkod on 2012-06-23
Are you talking about connecting to other servers, to copy/sync files, etc?

You can make entries in /etc/fstab which will mount the remote share on boot every time.

As for the sync, you can use something like rsync.

Making an entry in /etc/fstab for a Samba share for example would be like:
```
//server-ip/sharename   /mountpoint   cifs   guest,_netdev   0   0
```

If the share asks for credentials, instead of guest you would use something like username=user,password=pass

There are more complex variations, depending what you need.

---

### Post by Jacob72 on 2012-07-23
Thanks for your reply. 

I am trying to manage sites securely. I find your advice quite technical and would like to find a full tutorial to understand it fully. 

I am also willing to pay for some one-to-one help via SKYPE, please pm me if you or anyone else would be interested in helping me to get set up.

London time :)
Thanks

---

