---
title: "Raid?"
date: 2006-03-06
forum: The Cafe
---

### Post by Cyfr on 2006-03-06
I want to setup a RAID5 server with linux. I havn't decided if I will go with Ubuntu or Gentoo.. or infact any other distro, but lets not go in to that!

I'm lookint at:
AMD64 3200
1Gig 3200 RAM

I don't know which harddrives I should go for...
The motherboard ([http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=279355](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=279355)) seems to support RAID5. Is this the same as having a RAID5 controller?

That motherboard also supports Raid in Sata2... so would I be better buying 4x [http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=154683](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=154683) (Sata150 Raid edition)

or [http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=256891](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=256891) (Sata300 normal Western Digital harddrive, with an extra 8Mb cache (16 in total) 


Any other comments too please! :) (I was gonna post this in the hardware section but it didn't seem relevant because its more an inequiry than a problem with installation :))

---

### Post by Cyfr on 2006-03-06
Oh also, is AMD64 3200 with 1gig ram good enough to run a fileserver which will have apache on also..

With various resource using things using apache (such as torrentflux and ninan newsreader (high speed big downloads))

Along with any future additions i think of ;p

---

### Post by mstlyevil on 2006-03-06
If it supports RAID 5 then yes it would be a onboard RAID 5 controller.

---

### Post by onlyoneskwalla on 2006-05-24
Just a warning linux tends to have troble with many of these motherboard soft raid adapters.  Many call them FakeRaid because they have the appearance of a hardware solution but are in fact just a bios bootable soft-raid.  Further while windows has full support for these and their full features,  Linux requires certain extra programs and kernel patches(ie Dmraid + dm-raid45 for raid5 support). This is not a bash on Linux in any way shape or form, I know linux can do software raid by itself with MD and linux has to adapt around windows so many times.   Basically ending my rant with this if your not gonna use windows on the same raid you might wanna go the Linux softraid route which I believe doesn't even require a raid device, just multiple harddrives.  If you do plan to use windows and linux on the same raid beprepared to dig in and get your geek on:P

---

### Post by Virogenesis on 2006-05-24
Well, 1gig is more than enough to run apache, what are you trying to do run a enterprise worthy server? 
Serously apache doesn't consume alot of ram and as for that board, look into that board find out what controller that motherboard has as alot of motherboards use software raid which is ok but its not the real thing.
Scsi is the way to go for raid I'm afraid but on the otherhand I believe 3ware do support linux out of the box, unlike promise. 
Promise you'll find get bundled with alot of motherboards, you'll also find that you might need nvraid if you get a nforce board. 

Maybe some one else can go more into detail with things as I do not currently run a raid set up, if someone can explain software raid a bit better I believe that will help.

---

