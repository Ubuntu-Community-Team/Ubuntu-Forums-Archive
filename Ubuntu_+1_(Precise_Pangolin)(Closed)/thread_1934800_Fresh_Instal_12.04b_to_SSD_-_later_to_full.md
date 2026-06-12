---
title: "Fresh Instal 12.04b to SSD - later to full?"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Fictitious1 on 2012-03-02
/fluff
So my Hard drive died the other night.  We've all had it happen, but at least I had backups of most everything I think, so I'm good.  Just upset more about the lost time.  It was a windows 7 64 host and I run 1-2 virtualbox Ubunutu guests - Have enjoyed Ubuntu for a long time and find myself tooling around with it more than my Win7.  That said I think I'm going to get a SSD today and do a full Ubuntu install host and Win7 guest, I had 11.10 guest, but just heard the 12.04b is out.
\fluff

/question 1
Is it better to just go ahead with a 12.04beta install and then just reinstall everything or upgrade as it gets better to the full release in a few weeks? Or stick with 11.10?

/question 2
If I do a guest Win7 is it possible to just put the whole vdi on the ssd and will that improve performance a lot compared to just running it off my disk drives.  /explanation I have had it set up that my Guests are just like 80gb images and they connect to different VHD's for actual storage.  Planning on doing that with this as well, or just setting up my ext4 disk drive as a network share and then storing everything that way.. dunno, will play with it.

/fluff
Also I'm really enjoying the remote desktop that I FINALLY got going on 11.10, about a thousand threads later.

/question
Has the Remote Desktop (vino?) been fixed in 12.04 yet?


Thanks and looking forward to going full Ubuntu within a few hours probably.

---

### Post by cariboo on 2012-03-02
> **Fictitious1 said:**
> /fluff
So my Hard drive died the other night.  We've all had it happen, but at least I had backups of most everything I think, so I'm good.  Just upset more about the lost time.  It was a windows 7 64 host and I run 1-2 virtualbox Ubunutu guests - Have enjoyed Ubuntu for a long time and find myself tooling around with it more than my Win7.  That said I think I'm going to get a SSD today and do a full Ubuntu install host and Win7 guest, I had 11.10 guest, but just heard the 12.04b is out.
\fluff

/question 1
Is it better to just go ahead with a 12.04beta install and then just reinstall everything or upgrade as it gets better to the full release in a few weeks? Or stick with 11.10?

If you keep up-to-date with updates, you'll end up with a working Precise final, when it's released. As to doing a re-install when it is released, it more depends on how much fooling around with customization, and adding little used programs you've done.

> /question 2
If I do a guest Win7 is it possible to just put the whole vdi on the ssd and will that improve performance a lot compared to just running it off my disk drives.  /explanation I have had it set up that my Guests are just like 80gb images and they connect to different VHD's for actual storage.  Planning on doing that with this as well, or just setting up my ext4 disk drive as a network share and then storing everything that way.. dunno, will play with it.

I've found that most virtual installs seem to perform faster than actual installs, so if you've got the space on your SSD, I'd say go ahead.

> /fluff
Also I'm really enjoying the remote desktop that I FINALLY got going on 11.10, about a thousand threads later.

I personally don't use remote desktop, as the only system I access remotely is my server, which doesn't have a gui. As far as I know Remmina has replaced vino in Precise.

> /question
Has the Remote Desktop (vino?) been fixed in 12.04 yet?

See my comment above

> 
Thanks and looking forward to going full Ubuntu within a few hours probably.

---

### Post by Hedgehog1 on 2012-03-02
Win 7 as a guest OS on Ubuntu using SSD:

This really works well.  I am using SATA III SSD and controller so I get the 6mb speed:

Boot time Win7 ready to use: 13 seconds.

Boot time XP ready to use: 7 seconds.

I am able to edit video in Win7 guest using Sony Vegas - no problem.

My PC is a 6 core AMD and I have 16 gigs of ram, so I can give ram and cores to the guest OSes and get good performance.

You will find that you use Windows less and less as time goes on.  Now it's just for Sony Vegas and iTunes and some testing.

***The Hedge***

:KS

---

### Post by Fictitious1 on 2012-03-03
> **Hedgehog1 said:**
> Win 7 as a guest OS on Ubuntu using SSD:

My PC is a 6 core AMD and I have 16 gigs of ram, so I can give ram and cores to the guest OSes and get good performance.

You will find that you use Windows less and less as time goes on.  Now it's just for Sony Vegas and iTunes and some testing.

***The Hedge***

:KS

Thanks, I just picked up a 64GB Crucial m4 rev309 this afternoon.  Downloading the 12.04 iso right now.  In honesty I think the only reason I was hanging onto Win7 was for iTunes and home-sharing, and a very occasional game.  I've got a 6 core AMD as well and its been great for running multiple guests.  I know 64GB is probably going to be pretty small to get a Win7 guest and the host on as well, but I might try it.  I'll post back when I get all this done and see how things went.

---

