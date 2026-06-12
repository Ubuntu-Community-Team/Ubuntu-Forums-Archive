---
title: "Bad idea to just give 10 gigs to ubuntu"
date: 2008-02-18
forum: Testimonials &amp; Experiences
---

### Post by mason215 on 2008-02-18
^^^ Someone suggested this for me to do when i wanted to dual boot. But since i had 100 gigs free i decided to give 40 to ubuntu and 60 to XP. Now after a week i already have 9.4 gigs on my ubuntu drive. So iam glad i didnt give ubuntu just 10 gigs, otherwise it would really slow.

---

### Post by freebeer on 2008-02-18
I presume that includes your /home folder?

I've been running 6.06 for 1.5 years now and my / partition is only consuming 3.5 gigs.  And I'm running a fair amount of stuff (ftp, apache, etc.)

---

### Post by Zeroangel on 2008-02-18
Freebeer has a point.

You can run a base Ubuntu with everything you need on 10GB without any really major problems, (at 10GB, you will need to start removing unimportant things after a couple years) but you still need space on top of that to put your DATA! (music, movies, downloads, etc)

I recommend at least 20GB for the OS and its programs (not including music/movies/etc)

I have allocated 15GB to my Ubuntu install and I have created a /home partition.

15GB is plenty if you use the /home/ partition method and you probably wont be running out any time soon if you can manage to repartition your drive.

However, I recommend you create 20GB Windows partition, 20GB Linux Partition and a really fat shared partition. (music/movies/windows games). Make the filesystem FAT32.

Then have Ubuntu mount the shared drive at some place like /media/sharedhd

I recommend a filestructure like this on the shared drive
```
Music
Movies
Programs
Installers
Downloads
```Then create a bunch of symbolic links to the folder, by alt-dragging (select 'link here') your folders from /media/sharedhd to /home/$USER 

WIndows will see this as the D:/ drive (or similar). If you want to install certain programs like 2GB games onto your Windows system, if you do in the D:/ drive then it will be easily accessable from ubuntu! And if you're lucky you might be able to run some of those windows programs using wine.

The main advantage of this method is that all of these filespace expensive things are on their OWN partition.

If you ever break or reinstall Linux, they will remain untouched. If you ever break or reinstall Windows, they will remain untouched.

---

