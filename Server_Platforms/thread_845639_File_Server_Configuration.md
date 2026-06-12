---
title: "File Server Configuration"
date: 2008-06-30
forum: Server Platforms
---

### Post by mpcheung on 2008-06-30
Hi,

I'm fairly new to Linux and recently set up my old Dell 500SC with Ubuntu Server 8.04 using this guide: [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

I got it running just fine follow the guide stepwise.  However, since it is a "simple" server, it didn't detail ways to set permissions to the folders (delete or rename operations) from Windows XP.  

My server will be stored in my closet.  Ideally I'd like to access it remotely from Windows as a visible drive, with complete admin privileges to the folders on the Ubuntu server.

Right now, I can only add files to the server, but cannot modify or delete files from my Windows machine. Do any of you have any good resources or tips on how to get this running correctly?

Thanks,

MP

---

### Post by erolleman on 2008-06-30
You need to log into your server (whether it's locally or with putty) with root.  Then "cd " to the directory where the root of the share is.  If your files in the share are located in "/media/share" then " cd /media ".  After this type " chmod -R 777 share "  This will set the permissions so that the everyone has read and write access to the shared folder folder called " share ".  If you want to get complex with the permissions on the folder you will need to learn how to use the " chown " and " chmod " commands and learn how to create linux and samba users.

---

