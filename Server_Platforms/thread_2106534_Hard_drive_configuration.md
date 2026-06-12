---
title: "Hard drive configuration"
date: 2013-01-19
forum: Server Platforms
---

### Post by Derlux on 2013-01-19
Hello everyone!

I'm new to this forum and i don't post questions that easily but I couldnt find what I needed using Google.
I've installed a ubuntu server since I found that I had to learn how to use at least one linux distribution and started 2 days ago.

My problem is that I am going to add a 2 1 TB HDD in raid 0. These are going to function as a storage for movies, music etc. for at home. I have found tutorials how to configure these drives but I need to share them with windows machines. Do I need to configure them in NFTS or will my windows machines also be able to write to a for example ext3 formatted drive by using samba.

Thanks for the support!

---

### Post by rubylaser on 2013-01-19
First point, I would not suggest using RAID0.  If you lose 1 drive, you'll lose the data on both.  If you share the filesystem out via Samba (CIFS), Windows will not care what the underlying filesystem is.  You will still be able to write to the share as long as you've allowed the share to be writeable in your smb.conf.

---

### Post by Derlux on 2013-01-19
Thank you for your response! Good to know that ;) I chose for raid 0 since I needed more speed than JBOD can offer me but perhaps raid 1 is better just like I installed my OS. The only problem is that that is "expensive" for a student ;)

Futhermore when I have configured my drives can I give it a mouse pointer with 
 sudo mkdir /data/
Or does it need a underlying folder like

 sudo mkdir /media/data/
With data being the complete new hard drive to be shared with my windows machines. This should have anwsered all my questions.

---

### Post by darkod on 2013-01-19
You can create any mount point you like, including /data. I would use something like /data instead of anything in /media.

---

### Post by Derlux on 2013-01-19
Oke thank you very much! Solved my questions :)

---

