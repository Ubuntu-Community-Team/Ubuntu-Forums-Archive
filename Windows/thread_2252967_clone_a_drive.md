---
title: "clone a drive"
date: 2014-11-16
forum: Windows
---

### Post by dave6 on 2014-11-16
Hi guys

Need some better advice than I have read "http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone" (way above my head)  I need to replace the main OS (win7.64bit) drive on the other computer which is loaded with my photos and app for photograph editing CS6 "and I am sure you know how much that cost" along with other software including gimp, this computer is not on a network nor the world-wide-waste, stand alone unit and that is the way it will stay.   Once bitten, twice shy.......

My thinking on it was, 
Take the Maxtor drive out plug it into this computer "stata plug" 4 blank of 6, 
Then put the new SSD into the ( [http://www.ebay.co.uk/itm/261492757909?_trksid=p2060778.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.co.uk/itm/261492757909?_trksid=p2060778.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT) ) and copy disk, thus leaving the old Maxtor drive as a master un-used.  "just in case the SSD fails ??? yipss :-((

Help please in little tiny steps

Dave

---

### Post by TheFu on 2014-11-16
Cloning a Windows OS disk to run in a different computer usually is not possible because windows installs specific software based on the hardware involved.  If you just want to clone the data, that is easy. Use dd, ddrescue, partmagic, clonezilla or fsarchive. There are many, many, how-to guides out there that we don't need to restate them.

For windows, the best way to migrate to a new HDD, if you aren't a corporate license user, is to reinstall Windows, then reinstall all the applications. Sorry.

Of course, cloning a drive that has different sector sizes between the source and target can make performance really slow - to avoid that, use gparted to create the partitions on the correct boundaries (other tools do this too), and just copy the data over any way you like.

If this is a Linux OS - cloning is usually easy - dd, ddrescue, heck, even gparted will clone partitions for you. It is best to boot off a liveCD/liveUSB Linux then perform the cloning on two drives that are not mounted at all.

---

### Post by dave6 on 2014-11-16
NO, I said, I need to clone win7 onto an SSD on the other computer. BTW these 2 computers are the (same inside) except one is laying dow, other is standing up and third and most inportant, other computer has more than 1 HDD, second one being the third of 3TB drives, thats over 6TB of photographs
Sorry if there was some confussion............I need to clone 30GB onto a 120GB SSD as the Maxtor drive is starting to go tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, tick, got the idea, it is starting to fail and the fun I had getting the win thing to reg with ms, long phone call give out a very long number got a very very long number from ms, clicked on this clicked on that, then going over the lot again getting CS6 to reg within the 30 day test period then having to input a code to keep it live, aaahhhhhhhhhh...... do not want to go thru all that again.  I hate bloody computers

Back to my point clone a drive??
An easy way.  

Dave

---

### Post by howefield on 2014-11-16
Thread moved to the "*Windows*" forum.

---

### Post by verymadpip on 2014-11-16
Hi there.
I used Macrium Reflect Free to clone an 80GB hard drive directly to a 500GB HDD replacement going into the same machine.  I then had an 80GB partition with the OS on & I kept that separate from the rest , which I use for data storage, program installations & the like.
[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

If your hardware's identical (which I believe you've stated it is) you should be good.
I think you could rearrange your partitioning scheme afterwards if you so choose.

---

### Post by TheFu on 2014-11-16
> **dave6 said:**
> Back to my point clone a drive??
An easy way.  

Dave

```
# dd if=/dev/sdwhateverA of=/dev/sdwhteverB

```
Easy enough?

Of course there are faster, better ways, but you said "easy."

---

