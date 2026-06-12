---
title: "I cannot figure out this ripping/burning thing"
date: 2010-01-09
forum: Ubuntu Studio
---

### Post by Hazelip on 2010-01-09
Okay, I have a problem that is about to make me toss my computer under a truck.  Please, for the love of all that is awesome, help me out here.

I'm still pretty much a Windows user, and I get a paycheck for the Windows stuff I can do.

I've been using Ubuntu on my backup machine (laptop) for a while now, just surfing and document creation and general play.  My tower died, and until I replace it, the backup is now the primary.

My laptop is an HP V6000 maxed out on RAM and runs pretty well.

I'm trying to back up one of the kids' DVDs before I give it to them to destroy.

I have tried to do things the way I've done them in Windows, and failed.  I've tried to copy the VIDEO_TS to a local directory on the HD, then burn a data DVD after including a blank AUDIO_TS directory to go along with it.  Result? Coaster.

I then took that same copied directory with its manually-created partner, and downloaded Nero for linux, and burned a Video DVD project.  Result? Coaster.

I tried creating an ISO from the directories with mkisofs.  Result?  Coaster.

I've tried DVD::Rip, Brasero, Nero, Acid Rip, Devede, DVD95, k3b, ISO Master, and failed with any and all combinations of them.  

I have tried to mount the ISO as a volume, and then I get a permissions error.

I've tried the burned discs in my DVD player, thinking that maybe it's a weird playback on the computer issue, but still it's a no-go.

Can someone, anyone, please help me out here?

I'm on Ubuntu 9.04 Super OS dist. and I'm about to lose my mind.

---

### Post by Darce on 2010-01-10
Hello Hazelip,

Can you play the original DVD on your Ubuntu install ?

Cheers,

Tim

---

### Post by noelvh on 2010-01-10
This is what I have done.
I installed DVDfab (the free version) using WINE and I have had no problems. From there you should be able to use the burning software to move the files to dvd.

I have the very same issues with my kids. The best way to defeat my kids was to connect a computer to my TV and play the ripped DVD from that. No more dead disks.

Good Luck

Noel

---

### Post by howefield on 2010-01-10
Rip the dvd with Handbrake.

Review
[http://www.youtube.com/watch?v=WZFyb9U0LX0](http://www.youtube.com/watch?v=WZFyb9U0LX0)

How to Use
[http://www.youtube.com/watch?v=boHyO5RFWdI](http://www.youtube.com/watch?v=boHyO5RFWdI)

Get it from
handbrake.fr

Then you can use the ripped file to make a dvd iso using Devede.

---

### Post by Hazelip on 2010-01-10
Darce, that is the most confusing thing.  I have absolutely no problems playing DVDs at all.  None.  Everything I need is installed with the Super OS distro.

I finally figured out how to get the job done, but my problem isn't solved.  I ripped using DVDShrink in Wine, and then burned the resulting image with Brasero.  The weird part is that the image I successfully burned and played in a DVD player, won't play at all when mounted with Furious.  I get that same permissions error.

I'd really rather have a totally linux process, but I'd rather have playable archive discs for the lil' beasties.

---

