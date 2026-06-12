---
title: "Configure share folder between pc wiht Linux"
date: 2017-04-12
forum: Server Platforms
---

### Post by sed_faster on 2017-04-12
Hello,

I have an ubuntu server on my network. I have all pc's with Ubuntu and I intend create a folder on ubuntu server and access from any pc on my network. I know how configure nfs folder, but I don't want need run this command all the times which I need access this folder:

```

sudo mount -t nfs 000.000.100.00:/media /home/user/Documents/sandbox/usb/
 
```

How can I configure the ubuntu server or my pc's, including my laptop, to when connect the network the folder which my ubuntu server it is share be automatic available? 

Thanks

---

### Post by yancek on 2017-04-12
Put an entry in the /etc/fstab file for it on the various computers you want to access it similar to the example below to have it mounted/accessible on booting the various computers.  Change the various parameters if you want.  Place an entry in the /etc/exports file on the server and export it.

> 000.000.100.00:/media /home/user/Documents/sandbox/usb nfs rsize=8192,wsize=8192,nosuid,soft 0 0 

That's a pretty odd mount location but it should work.

---

### Post by sed_faster on 2017-04-12
I don't understand this part: "Place an entry in the /etc/exports file on the server and export it." What should I put in /etc/exports?

I never tested this config before:

```

000.000.100.00:/media /home/user/Documents/sandbox/usb nfs rsize=8192,wsize=8192,nosuid,soft 0 0

```

But I already configured /etc/fstab but if my laptop or desktop booting without access networking I receive various message error relative to path to mount this folder nfs during the boot. This setup don't will show this message if my pc it is disconnect to the network where share folder is it?

---

### Post by wildmanne39 on 2017-04-12
*Thread moved to **Server Platforms**.*

---

