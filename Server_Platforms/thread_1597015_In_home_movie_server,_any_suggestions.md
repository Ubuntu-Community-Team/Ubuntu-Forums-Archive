---
title: "In home movie server, any suggestions?"
date: 2010-10-14
forum: Server Platforms
---

### Post by JD32 on 2010-10-14
So i'm new to linux but i manged to get a samba server up and running to share with my windows machines. But i still want more. My main goal is to be able to share my movies. I have a laptop hooked to my flat screen with 3TB's of external drives, thats whats acting as my server. I have ubuntu desktop installed because i use it to play movies also. 

I'm looking to set up something that is a little faster than samba (yes i no trying to share through USB 2.0 external drives and a wifi connection isn't going to be real fast no matter what) but i want to be able to access my server remotely. like maybe FTP? but what i'm asking here is what protocol should i use and what programs? i was thinking gadmin-proftpd and then filezilla to access? any suggestions, tutorial, anything would be greatly appreciated!!! 

Thanks!

---

### Post by jbrown96 on 2010-10-14
You should use NFS. UDP-based transport will be faster, especially over wifi. You can install NFS in Windows too, so it offers the best solution. However, your wifi is likely the limiting factor, but moving away from TCP should help.

---

### Post by JD32 on 2010-10-14
Any suggestions of how i can go about this?

---

### Post by volkswagner on 2010-10-15
I have [this how-to]("http://ubuntuforums.org/showthread.php?t=249889") bookmarked as, it is invaluable in creating NFS shares.

---

### Post by arrrghhh on 2010-10-15
NFS won't work if you're away from home.  You mentioned FTP, do you want to be able to share movies away from the house?

If you just want it shared on your LAN, NFS will work much better than samba.

---

### Post by jbrown96 on 2010-10-15
> **arrrghhh said:**
> NFS won't work if you're away from home.  You mentioned FTP, do you want to be able to share movies away from the house?

If you just want it shared on your LAN, NFS will work much better than samba.

You are partially correct. NFS can run over the internet, but it's not recommended. Samba is the same way. Furthermore, I doubt you have the upload bandwidth to stream video. More likely you would need to re-encode in real-time, which is extremely complicated.

---

### Post by JD32 on 2010-10-15
Ya i am looking to share away from home but i don't really need to stream it, just be able to access it and download

---

### Post by arrrghhh on 2010-10-15
FTP then... Or you can use HTTP, but FTP is probably easier to setup/manage intially.

---

### Post by JD32 on 2010-10-15
Any suggestions on what to use to setup FTP???

---

### Post by arrrghhh on 2010-10-16
> **JD32 said:**
> Any suggestions on what to use to setup FTP???

I prefer vsftp, but the only other one in the repo's off the top of my head is proftp.

---

### Post by Darkness Des on 2010-10-16
+1 to VSFTP. Secure, VERY simple to set up, and no headaches along the way (evil glare at Samba)

---

### Post by jbrown96 on 2010-10-16
There's several secure FTP implementations around.: wsftp, vsftp, and proftp. I remember hearing something very negative about proftp's security in the past couple weeks, but can't point you to any resources. I'd recommend vsftp. 

For your home network, you might want to consider using a UPnP sever. I use mediatomb; it's very easy to configure, and I've never had an issue with it. If you have bandwidth problems over wifi, you could try ps3mediaserver, which can encode in real-time (depending on your hardware) to meet  bandwidth restrictions. I used it with my PS3, but it should work with any UPnP client.

---

