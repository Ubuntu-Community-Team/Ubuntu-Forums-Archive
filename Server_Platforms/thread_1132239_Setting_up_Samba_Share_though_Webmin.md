---
title: "Setting up Samba Share though Webmin"
date: 2009-04-21
forum: Server Platforms
---

### Post by DoyleChris on 2009-04-21
I am trying to setup a share on my Ubuntu machine on the Main Drive before i put my other drives in to try out Samba.  I have Ubuntu Server 8.10 installed with Samba and Webmin and i am running a windows vista machine.  I created a new user though Webmin for me to test and made it a admin to access all the drives for now created a share in Samba in webmin for read/writable and i verified in the smb.conf that writeable=yes and i can see it on the network map the drive in vista and can access it but when i go to write something to it it says i dont have access i have tried every thing to set it up and having no joy.  Once things get running smooth i would like Ubuntu server to handle user accounts and passwords for the windows network but thats later.

---

### Post by R.Bucky on 2009-04-21
what are the permissions on the files themselves. I am wondering if Webmin config changes the files to be writeable when you configure a share?

---

