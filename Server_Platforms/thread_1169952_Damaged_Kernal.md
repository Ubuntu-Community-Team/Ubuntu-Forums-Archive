---
title: "Damaged Kernal?"
date: 2009-05-25
forum: Server Platforms
---

### Post by putz3000 on 2009-05-25
I have an old Compaq Evo computer that I currently run 8.0.4 server on.  It is basically a headless system.  The only thing I have to leave hooked up is the keyboard or it will not boot.  I had to do some work on another machine the other day and needed the keyboard so I ssh'ed into my system and ran the shutdown command.  I then took the keyboard and did the work I needed to.

Now that I am done I thought I would turn the server back on.  When I first rehooked up the keyboard and turned it on I got some beeps from the server.  I was not playing close enough attention to count the number of beeps though - it seemed somewhat rapid.  So I "assumed" I had coiled the keyboard coard up to tight.  However adjusting the cable did not resolve my issue.  I have since hooked up a monitor and what I have discovered is that Grub is unable to load the 2.6.24-24-server kernal (including repair mode).  I can however load off of the 2.6.24-23-server kernal without any problems.  This causes me to "assume" that the .24-24 kernal is damaged.  

What are my repair options if any?  Any suggestions in general?

---

### Post by putz3000 on 2009-06-02
just bumping this post in hopes someone might have an answer / thoughts.

---

### Post by rumblered on 2009-06-02
It does sound like the kernel file itself got damaged. Did you try reinstalling the kernel package?

Also, I'd check how much free space you have and run a manual update.

---

### Post by putz3000 on 2009-06-23
where can I read about reinstalling the kernal package?  I have never done this and do not know anything about it yet.

---

### Post by rumblered on 2009-06-23
In synaptic, you can just find the package and choose 'reinstall'. With apt-get, you'd want to do this:
sudo apt-get install --reinstall <pkgname>

In your case, the full command should be:
sudo apt-get install --reinstall linux-image-2.6.24-24-server

---

### Post by putz3000 on 2009-07-05
THANK YOU!  that did the job.  I was getting ready to follow some guidance I was given that would have simply removed the damaged kernel from being listed in the boot order - basically booting around the damaged kernel.  Your instructions not only kept me from doing that but obviously fixed the damaged kernel and now I can boot off of the reinstalled kernel.

thank you again for all the help.

---

