---
title: "woOT!!  Finally and totally Linux"
date: 2007-12-13
forum: Testimonials &amp; Experiences
---

### Post by melbo on 2007-12-13
I've been playing with distros for the past 5 years.  Tried most of them and I always came to that point where I got lost and ran back to the comfort of my GUI (windoze). Wireless and LANs were particularly tough...

I tried Ubuntu on one of my regularly scheduled Linux checks.  I had my trusty XP on a main partition and tried the live user boot.  Wow.  Was impressed.  I just had to see how fast this was on the HD.  I fired up my expensive Partition software and made some space for a temporary ubuntu trial.

What?  No Way!  I have wifi?  Can't be...  'print via SAMBA server'?  It freakin worked?  This is incredible.  Wait a minute!!!  I can see my old C: drive and those files?  Lets try a firefox profile move from NTFS to the new Ubuntu filesystem.  WORKED!!!  I am crying.

I gave my trial 2 days and found that I can get around in ubuntu without problems and can do everything I need to do.  I fired up gparted(free) and deleted that XP partition after moving my Documents over to the new spot.  I am all in with ubuntu now and am loving every minute of it.  Thank you thank you thank you!!!

No more virus', spyware, or defrags for me.  Those that are stuck on a certain MS app, get over it.  You can find almost everything you need here and the learning curve is well worth not having to buy Office 2008 in a few months. 

My wife is running TinyXP right now and thinks my ubuntu apps look pretty cool.  I had a dream last night about the kernel...  I pictured this spinning orb of light that went round and round, hooking to new processes and dropping others at the same time.  all without having to take a nap every once in awhile.

I'm having an issue with 'wake' on laptop lid being lifted.  I get graphical puke until I ctrl-alt-backspace.  no big deal and I think it is a reported bug.  I do have a question for all you experts though...

Windows spys on you with logs of every shape and color.  index.dats are one example.  I spent my years as a windows user watching my back and deleting my tracks and sensitive information.  I know that the very nature of linux makes it secure from unauthorized users.  I see that ubuntu keeps track of my recent documents, (I always turned that off in XP).  What else is kept about my usage that someone else could 'find'?  And can I clear that info?  I know all about thc secure-delete for files and free space.

I have a new Vista system upstairs that is getting ubuntu tomorrow if I can get around the Display error I'm getting when I try to boot from the CD.  dunno.

Thanks to all for the effort, development, and the drive to adapt this OS and take it to the moon!

melbo

---

### Post by MNICY on 2007-12-14
Great to hear it worked out for you :D

---

### Post by conehead77 on 2007-12-14
For your recently used files: Delete the file ".recently-used.xbel" in your home folder and make a directory with the same name. Ubuntu wont be able to store recently used files anymore.
If somebody knows a better way, please let me know :)

---

### Post by wheredidrealitygo on 2007-12-15
If you're into security, you may also want to check out the .thumbnails folder (remember everything with a . in front is hidden by default) in your /home/<username> folder. It is used to bring up recently looked at pictures much faster, so that way it's not rendering every picture fresh and taking that much longer.

I swiped a script from somewhere else on the forums here (forget where unfortunately) to automate it if you're interested.

---

### Post by blackmachine on 2007-12-16
> **conehead77 said:**
> For your recently used files: Delete the file ".recently-used.xbel" in your home folder and make a directory with the same name. Ubuntu wont be able to store recently used files anymore.
If somebody knows a better way, please let me know :)
This will disable recently used documents
```
sudo rm ~/.recently-used ~/.recently-used.xbel && mkdir ~/.recently-used.xbel
```

---

### Post by matthewcraig on 2007-12-16
> **blackmachine said:**
> This will disable recently used documents
```
sudo rm ~/.recently-used ~/.recently-used.xbel && mkdir ~/.recently-used.xbel
```

No need to use the "sudo" command to remove and create a folder in your own user directory.

Good tip on turning off the Recently Used feature.  Hopefully this will be in the GUI one day.  I am not a fan of a meticulously dated record of all the files accessed, either.

---

