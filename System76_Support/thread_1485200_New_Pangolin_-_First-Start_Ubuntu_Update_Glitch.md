---
title: "New Pangolin - First-Start Ubuntu Update Glitch"
date: 2010-05-16
forum: System76 Support
---

### Post by re1d on 2010-05-16
My System76 Pangolin Performance arrived on Thursday of last week – one day ahead of schedule – so I thought I'd mention some impressions; and also comment on an update issue that caught me, and might catch some others!
 

 ***The update issue: ***After you start any new machine and log onto the Internet it's going to download updates and ask to install them. When my new Pangolin did that there were quite a few, so I sat quietly watching the process develop and sort of happily looking over my new machine. Then a dialogue box popped up, wanting to install GRUB – saying something about the hard disk drive having changed since last start (this was the first start!) - and wanting to know where to put GRUB. A list of devices was provided.  
 

 Not being quite sure how to proceed, as I hovered over the choices, a tooltip came up with a helpful message: it seemed to recognize that the GRUB reinstall might have caught the user off-guard, and suggested that if you weren't sure which device was your boot device, to install to all of them! It sure sounded like the safe solution, since they suggested it, so after some hesitation I did that. I did get a message saying that GRUB install had failed to /dev/sda2, and also something else (not /dev/sda1) which I took to be the DVD drive – so I didn't worry about them. The rest of the update went normally, and I rebooted.
 

 *Almost* – on reboot, after POST, all I got was a black screen and blinking curser. A cry for help to _Tom Aaron revealed that I should have chosen * **/dev/sda1** * – and ONLY that, in spite of the contextual advice._ Apparently this had also been a problem for some other users, and is not a System76 issue but comes down from the Ubuntu devs. 



Tom offered me assistance in putting it right, but I was extremely busy at work on Friday so couldn't take him up on it; and my attempt to follow a tutorial he linked to didn't work out. So in the end – as it is a brand-new machine – I simply restored it using a new 64-bit image. Tom sent me links to useful info that helped a lot. Everything is fine and the restore didn't take long. I felt kind of noob to have messed up a simple update!  
 

 So thought I might mention it in case it catches someone else. Most of you are probably smart enough to know which drive you boot from, though! So try not to laugh. Just hoping this keeps someone else from making the same mistake. Hopefully it's fixed or soon will be.
 

 This is long enough – will put my Pangolin impressions, which are overall very positive, in another post. I should point out that instead of making me feel I'd made a mistake in buying here, this issue reinforced my strong feeling that the excellent and prompt support provided by System76 is unparalleled - and a great reason to consider one of their systems. Thanks, Tom!

---

### Post by thomasaaron on 2010-05-17
Thanks. You're very kind.

But just FYI, that update hosed a lot of folks. Really, the end user should NEVER have to worry about where to install grub. In my opinion, the devs need to rethink that.

---

### Post by Russellkhan on 2010-05-18
Shouldn't it be /dev/sda ? 

I also recently received my Pangolin Performance and ran into the same dialog box during the first update. A bit of googling told me that Grub belongs on the first hard disk's MBR and not in a partition. I installed it to /dev/sda and have had no problems (I have rebooted a few times since then). 

Not trying to be argumentative, I just would hate for this thread to mislead someone in the future. 

Russ

---

### Post by betrunkenaffe on 2010-05-18
> **Russellkhan said:**
> Shouldn't it be /dev/sda ? 

I also recently received my Pangolin Performance and ran into the same dialog box during the first update. A bit of googling told me that Grub belongs on the first hard disk's MBR and not in a partition. I installed it to /dev/sda and have had no problems (I have rebooted a few times since then). 

Not trying to be argumentative, I just would hate for this thread to mislead someone in the future. 

Russ

Agreed, sda1 would screw up my Windows partition :)

---

### Post by re1d on 2010-05-19
> **Russellkhan said:**
> Shouldn't it be /dev/sda ? 

I also recently received my Pangolin Performance and ran into the same dialog box during the first update. A bit of googling told me that Grub belongs on the first hard disk's MBR and not in a partition. I installed it to /dev/sda and have had no problems (I have rebooted a few times since then). 

Not trying to be argumentative, I just would hate for this thread to mislead someone in the future. 

Russ

Russ,

You may well be correct - and it's a good point about misleading anyone - maybe a moderator should chime in here? 

In my case, I never had a second chance to make that choice - I restored instead, since the machine was brand new and I wasn't able to make the other procedure work. 

On the reinstall and subsequent update, the question never came up, though I was ready for it! So I never tried installing GRUB to /dev/sda1 and don't know what would have happened if  I had.

Tom?:confused:

---

### Post by Russellkhan on 2010-05-20
Well, here's an [example of the documentation]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") I found that instructs to install to MBR. This one doesn't actually say **not** to install to a partition, but some of the ones I ran into in my last googling mentioned some stuff about it being trickier if you do need to install to a partition.

Russ

---

### Post by RedRat on 2010-05-22
> **Russellkhan said:**
> Well, here's an [example of the documentation]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") I found that instructs to install to MBR. This one doesn't actually say **not** to install to a partition, but some of the ones I ran into in my last googling mentioned some stuff about it being trickier if you do need to install to a partition.

Russ
thanks for this documentation. I will keep it around since I will be installing Ubuntu on a machine with WinXP. I suspect that I might need it.

---

