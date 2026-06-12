---
title: "File server questions"
date: 2005-03-19
forum: Server Platforms
---

### Post by eraos on 2005-03-19
Forgive me if this question has been asked a lot... but how do I use Ubuntu as a file server for only a home network? (My isp doesn't allow personal web servers.)

I will be using the system's 40 gb slave drive to hold all the data for sharing and storing and stuff.  Are there any programs I can download (like Apache or something?) that can make this easier?  Or can I simply share the drive over the network and allow users to read/write?

Thanks

---

### Post by eraos on 2005-03-19
[https://www.ubuntulinux.org/wiki/SettingUpSamba](https://www.ubuntulinux.org/wiki/SettingUpSamba)

I just found that and it lists how to create a shared folder using samba...

but can a 3rd party program be used for this?

---

### Post by orion_114 on 2005-03-19
Samba (SMB) is the program you are looking for. It allows you  to share files and folders on your home network. You can get it from synaptic.

---

### Post by eraos on 2005-03-19
Now how do I share a drive/folder?  I have the drive mounted as /depot

The Setting Up Samba page shows how to share the home directory.

Thanks for the reply.

---

### Post by orion_114 on 2005-03-19
In hoary you can setup a share from the administration menu.
In Warty its a bit more complicated you can probably find some info here ....
[http://us1.samba.org/samba/](http://us1.samba.org/samba/)

---

