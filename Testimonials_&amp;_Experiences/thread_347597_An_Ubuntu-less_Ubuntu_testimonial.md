---
title: "An Ubuntu-less Ubuntu testimonial"
date: 2007-01-27
forum: Testimonials &amp; Experiences
---

### Post by sread on 2007-01-27
Just like to share my adventures over the last couple of days, it really highlighted how great Ubuntu is.

To make a long introduction short, my Windows partition was too big, my shared partition was too small and my Ubuntu 6.10's broadcom (everyone's favourite) wireless was on the fritz. 

So..time for a fresh install of 6.10! After burning (and testing) my livecd of 6.10, I was off to the GParted livecd to resize and move around partitions (after backing up all the data of course!). That went without a hitch, Gparted is an excellent piece of software. Windows complained, but after numerous restarts everything was as I started, just different sized partitions.

Now that I was ready to install 6.10 fresh, I remembered an installation DVD I'd burned a month or so ago of a pretty Darwin-esque OS that shall remain unnamed. X. I read a few guides but since I was reinstalling anyways I just ended up loading it up to see what happened. Installation went perfect, but on restart, uh oh! GRUB stage 1.5 and 2 files were on that Ubuntu partition I just filled with something else, so no boot!

Never fear, I was able to boot up into the 6.10 livecd, and thanks to the fully functional Ubuntu present there, connect to the internet and read a bunch of helpful GRUB faqs and man pages along with the usual random forum postings. Turned out that GRUB didn't need Ubuntu, it just needs somewhere to put it's files. Since I happened to have a ext3 partition in my extended partition that I use for sharing files between Windows and Ubuntu, I simply installed the GRUB files into a /boot directory there, rigged up the menu.lst as described in many places and bam, Bob's your uncle. Windows and unnamed OS were up and running via GRUB, no Ubuntu installation at all!

Over all I was really impressed with how easy and stress-free the whole process was. I was never worried when things didn't work because I always knew I had that great 6.10 livecd to fall back on. Thanks to everyone who made it such a full-featured showcase/tool!

Next steps...play around with my new OS, reinstall 6.10 when I'm done and convince my aunt that Ubuntu is much, much better that Windows ME for her aging Dell!

Thanks for reading

Oh, and why did I go to all that trouble to keep my Windows partition running smoothly? Good question....

---

