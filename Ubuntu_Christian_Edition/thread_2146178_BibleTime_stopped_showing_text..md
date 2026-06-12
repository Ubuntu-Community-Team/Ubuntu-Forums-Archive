---
title: "BibleTime stopped showing text."
date: 2013-05-17
forum: Ubuntu Christian Edition
---

### Post by dnr1128 on 2013-05-17
Up until the normal ubuntu 13.04 updates a few days ago, Bibletime 2.9.1 worked fine.  However, now neither it nor xiphos will show text.  The programs will load fine, and show that there are modules loaded.  But when I try to pull up different passages, no text shows, just a blank window.  When I change references, the text will flash up for a split second then disappear.  I've removed, autoremove, purge, using both the terminal and USC.  Nothing seems to work.  Attached is a screenshot showing what it looks like.  I tried changing fonts, no luck.  I can't seem to find a place where font color is controlled, so it can't be that.  This is my main study program, so getting it working is important.  

[IMG]http://i947.photobucket.com/albums/ad317/David_Ryerson/Screenshotfrom2013-05-15130025.png[/IMG]

---

### Post by Saunter on 2013-05-24
Same thing happened to me after 13.04 upgrade.  I have no clues.

---

### Post by skimo12 on 2013-06-04
I am using a normal Ubuntu 13.04, i.e. not the UCE, but I am seeing the same problems here. I did the upgrade from 12.10 to 13.04. 
I think I can confirm that this is not something to do with UCE.

---

### Post by fredbird67 on 2013-06-23
I tried Xubuntu 13.04 here while back and had a slight problem with Xiphos, where the bottom arrow wouldn't show up in the list of books of the Bible.  Frustrated, I then downloaded and installed BibleTime and had the same problem y'all are talkin' about.  I finally gave up and went to Xubuntu 12.04, where Xiphos is at least working perfectly.  Can't comment on BibleTime though, as I don't have it installed, since Xiphos is working AOK and I don't see the point in having that kind of redundancy.

---

### Post by buckeyered802 on 2013-09-11
It is fixed in Bibletime 2.9.2. However, the problem is it is not available in the software center. You have to download the source from sourceforge.net and build it. I did it, but I warn you, it was a pain. Ha ha. I had to install a lot of qt5 dev packages to get it to build.

---

### Post by e8hffff on 2013-09-18
You can download the debs at below url for Saucy which work in Raring;
[http://archive.ubuntu.com/ubuntu/pool/universe/b/bibletime/](http://archive.ubuntu.com/ubuntu/pool/universe/b/bibletime/)

Make sure you remove Bibletime and Bibletime-data before process.  Then install 2.9.2 version debs with gdebi

---

### Post by e8hffff on 2013-09-18
Yeah I had that Xiphos problem too where you can't scroll the books as the selector cuts at screen height even if using multi monitors which I have above each other.

---

### Post by skimo12 on 2014-04-06
Bible time now works fine. I guess that one of those upgrades must have fixed it. I can now see text : )
I guess that once you have all updates done on your system, then it should be fine. I'm running Ubuntu 13.10.

---

