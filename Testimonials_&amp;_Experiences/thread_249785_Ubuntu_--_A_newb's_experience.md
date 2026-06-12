---
title: "Ubuntu -- A newb's experience"
date: 2006-09-03
forum: Testimonials &amp; Experiences
---

### Post by Magnus150 on 2006-09-03
Hello there everyone! For some odd reason I felt like sharing the experience of Ubuntu i've had recently. I just recently switched from Windows XP to Linux as I felt the need for something different. I've been at it for about 2 weeks now and now everything works beautifully. Well, onto the story!

I've been with Microsoft products and computers in general all my life (when I was 3 I erased my father's DOS, one year later I proceeded to fill his 'box with sand), ever since DOS, Windows 3.x all the way to XP. I consider myself somewhat adept with Windows and switching to Linux was quite the experience. The first thing I noticed was that the terminal was almost a complete 360 from command line in Windows. The commands seemed strange and alien as I stumbled through my beginner hiccups. 

I run a Dell box, a cheap customized Dell 2350, a piece of crap, but it works until I get my new computer of choice next year. When I tried to install Ubuntu, I began to truly realize how horrible this thing is. I put in the Live CD to give Ubuntu a go, as I had been wanting to try something different, and I was bombarded by errors. I searched the forums as of a possible solution and found none. By trial and error I deduced it down to my video card. I have an integrated intel graphics i836 (I think) and when I had it loading to my Radeon 9200SE, produced a multitude of problems. No sweat, I'll just load on onboard and figure it out later. Once I switched to onboard it loaded like a champ. I used Live for a minute or two and, wanting the full experience instead of a demo, decided to install to a partition on my secondary storage drive, a Maxtor 180 gig. The partitioner was wonderful! I split the partition in half then the auto partitioner did the rest for me. I then restarted and was thrusted into the alien universe of Linux. 

I then found out two things, 1. 1024x768 is a horrible resolution to run and 2. My belkin wasn't natively supported, zomg! I then booted into windows (grub is a neat dual-booter by the way, I thought it would be much more difficult), and read the forums on a solution. After trying about 2 of them, I found an awesome NDISwrapper guide that told me to blacklist the native drivers, which did the trick. After I had the internet working, I worked on tackling the graphics. This proved much more difficult and ended in me re-installing Ubuntu twice, as I did not know how to fix any mistakes I made. After a long troll around the forum search engine, I did not find any one solution, but I had found a wealth of knowledge on quite a bit. I eventually combined the knowledge I had acquired from said trolling to figure it out on my own. I blacklisted the i836 drivers and then installed the basic non-descriminatory ATI drivers, which did not support 3d (which I found out later to my dismay). After a successful boot into Ubuntu on my PCI, I cried in joy! Finally no more wire switching and BIOS changing! I then found out that no 3D was supported, O NOZ! I searched the forums again and found a script to installing ATI drivers. This script is awesome! It installed 3D support for my ATI Radeon 9200, excellent!

I then proceeded to try to find out if I could read things off of my NTFS partitions, oh yay I can! I later found out that I could also write to these NTFS drivers--even better. After yet another search I found a guide written by Givre' (kudos to you) on how to use the ntfs-3g, I was able to access all my media files. I found out mp3 and other restricted formats were not natively supported, so I searched around for an answer in the forums, and found Easyubuntu (I heartily reccomend this to any new Ubuntu user!) at [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) which set everything up for me in regards to that. 

Throughout this somewhat fun and very educating process, I learned quite a bit about Linux and about how horrible Dell is. I had other adventures (such as flashplayer syncing) but I won't write any more--I doubt anyone will read my whole speech as is, but it was really an enlightening experience. I now have Ubuntu working perfectly and I am enjoying it thoroughly. Everything is free and it is wonderful! My next task is Samba and I'm sure that will be thoroughly enjoyable. Well, I better end this long-winded novel. The future is looking great with Ubuntu!

Magnus150--Linux Virgin

---

### Post by coffeecat on 2006-09-03
> **Magnus150 said:**
> ....one year later I proceeded to fill his 'box with sand

Quite logical really. As a four-year old you thought it would run better with lots more silicon chips. :D

I enjoyed reading your post, Magnus150. It wasn't too long at all. Good luck for the future.

---

### Post by panzer21st on 2006-09-03
Yes, I too, have a Dell piece of junk.  I was really surprised, when everything worked in Ubuntu, on the first try.  I haven't tried the 3d experience yet.  I'll read more on the forums, like you did, before I try.

---

### Post by Magnus150 on 2006-09-03
[http://www.ubuntuforums.org/showthread.php?t=235145](http://www.ubuntuforums.org/showthread.php?t=235145)

Try that if you have an ATI. If it's Nvidia you'll have to look around. It's really handy!

---

### Post by panzer21st on 2006-09-05
I do have Nvidia.  I found a thread that led me to the wiki [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

It works great.  (I did have to go through some of the 'If that doesn't work' troubleshooting.)  Nice having a community helping each other, and all this info.  I don't remember finding things this easily on the MS site.

---

### Post by S1NGH on 2006-09-05
first off, that was a great experience ;)
second of all, don't call yourslef as a newb... you actually worked things around to get your copy of Ubuntu to work the way you just wanted to perform it, i am sure you learnt quite a lot and will carry on doing so. Maybe even make better tweaks to Ubuntu (duh!) and sit back and relax while you watcha movie and roll back and forth in xgl ;)

i am sure that you had a great time once everything was set and going...
good luck with your samba experience and enjoy ;)

---

### Post by Brendt2 on 2006-09-05
Here here...

Of all of my box's ( which are quite widely mixed ) the only computer that gave me any lip was a dell dimension ( older model ).  

But in the end Ubuntu always prevails!

I am glad to hear that it worked for you too!

---

