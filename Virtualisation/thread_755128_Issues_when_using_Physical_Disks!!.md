---
title: "Issues when using Physical Disks!!"
date: 2008-04-14
forum: Virtualisation
---

### Post by borillionstar on 2008-04-14
I couldn't find a post about physical disks that had the same issue I am having. I am using vmware workstation 6,

Ill show with images because its easier than trying to type it all out.

[IMG]http://farm3.static.flickr.com/2407/2414242190_e7234664c4.jpg[/IMG]

[IMG]http://farm3.static.flickr.com/2407/2414242466_837f7ac2e2.jpg[/IMG]

[IMG]http://farm4.static.flickr.com/3239/2413417801_66d3e7b089.jpg[/IMG]

[IMG]http://farm3.static.flickr.com/2195/2413417907_4e59229da1.jpg[/IMG]

[IMG]http://farm4.static.flickr.com/3106/2414242844_273e37307b.jpg[/IMG]

[IMG]http://farm4.static.flickr.com/3169/2414320652_c17ca621d0.jpg[/IMG]

:confused: This is the part where everything goes out the window!!

[IMG]http://farm3.static.flickr.com/2231/2413419567_b1639dee9b.jpg[/IMG]

It seems that for some reason vmware in unable to create the files for the vmware machine, when I look in the directory that it should be going to there is nothing there. I am part of the disk group so thats prolly not the issue. Hoping someone else has seen this before.

Thanks Bor.

---

### Post by capricorn180 on 2008-04-19
Had a similar issue when I was trying to set mine up.  I don't know enough about it to know 'why' it doesn't work, only that choosing '/var/lib/vmware-server/Virtual Machines/Windows XP Professional' instead of my /home dir made it work.

My /home is on a separate partition but not sure if thats the reason.  Seems to work fine in /var/lib though.

Hope this helps.

---

