---
title: "VBox: sharing files between host and guest os"
date: 2010-08-27
forum: Virtualisation
---

### Post by t0p on 2010-08-27
I want to print some pictures but my printer (HP Deskjet D2660) won't work with Ubuntu (yeah yeah, I know it's *supposed* to work with Ubuntu - that's why I bought the thing.  Anyway that's a problem for another day).

So, I've got VirtualBox on my Hardy-running machine (the closed-source version with USB support).  I've got XP running as a guest on VBox. Of course the printer will work with XP (thanks to the handy drivers CD HP provided).  I have my pix on a USB flash stick.  I tell the VBox XP to use the stick... and that's where the problem lies.  Sometimes it'll work with the stick, sometimes it won't, sometimes it'll work for a short period of time... anyway I can't get the VBox XP to handle the stick long enough to transfer the pix to the XP desktop or anything like that.

Can I tell the VBox guest XP to access the files from the host Ubuntu?  How?  Thanks.

---

### Post by 29732 on 2010-08-27
devices>install guest additions
note: the vm has to be on
and then you click on devices>shared folders and then make a shared folder
it will be in my network places(on the folder options it should be like use classic windows buttons) and then _____VM or something of that sort

---

### Post by t0p on 2010-08-27
I did as you suggested, but nothing appears in Network Places.

I think the problem is the path I specified when adding the shared folder.  I used the Ubuntu path /home/t0p/Pictures/card-pix; but this is in a virtual xp so I guess the path should be specified differently.

How do I specify a path from a folder on the Ubuntu host machine to the virtual xp?  I know the guest xp sees the Ubuntu machine's ip address as 10.0.2.2.  Does that get included somehow?  Clearly, I know nothing about Windows so need help.

---

### Post by Toz on 2010-08-27
From within the Windows XP guest, map a drive to \\vboxsvr\<share_name> where <share_name> is the name you gave the share via 29732's instructions.

This link might also help:
[http://www.virtuatopia.com/index.php/VirtualBox_Shared_Folders](http://www.virtuatopia.com/index.php/VirtualBox_Shared_Folders)

/ToZ

---

### Post by t0p on 2010-08-27
Thanks Toz.  But (and this is where the extent of my Windows-related ignorance becomes truly apparent) how do I "map a drive" from within XP?

---

### Post by t0p on 2010-08-27
Following advice from that virtuatopia.com link, I issued the following command in the guest XP's command line:

```

net use c: \\vboxsvr\card-pix

```

and got this reply:

```

System error 85 has occurred.

The local device name is already in use.

```

but I can't find c: \\vboxsvr\cardpix, or even c: \\vboxsvr.  Where am I supposed to look?

---

### Post by Toz on 2010-08-27
don't use c: - that's the main hard drive. Try another letter...

net use p: \\vboxsvr\card-pix

---

### Post by t0p on 2010-08-27
Thanks Toz, that did the biz!

---

### Post by 29732 on 2010-08-27
well, there ya go ^_^

---

