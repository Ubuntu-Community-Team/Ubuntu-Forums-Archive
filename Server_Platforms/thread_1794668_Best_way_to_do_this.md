---
title: "Best way to do this ??"
date: 2011-07-01
forum: Server Platforms
---

### Post by mqhavic on 2011-07-01
Hi Guru's

I am looking for the best/cheapest way to build a ubuntu server with 8tb of storage hanging off of it.

I don't feel it needs to be hardware raid, so more software raiding swap in and out failed disk drives.  

The server itself normal duo core CPU with 2Gb of memory and i would like to have the internal drive of the O/S only.

Thanks for your help and ideas

---

### Post by arrrghhh on 2011-07-01
Well if you don't want hardware RAID, then the answer is simple.

Get a mobo with enough plugs to support as many disks as you require...

What your requirements are really depends on how much redundancy you want.  You'll probably want RAID5 or 6.  I would recommend 1tb drives over 2tb drives, because of platter density.  If you're concerned about how many drives, perhaps 2tb or larger drives are necessary.

---

### Post by collisionystm on 2011-07-01
Why do the internal drive of the os only?

Just raid the whole thing. 

If you want 8tb of storage, you had better do a Raid 10. You would be foolish to do anything else with that kind of data to loose.

Although I don't think they make 4tb hard drives yet, do they?

You will probably have to do 2 servers with Raid 10 on 2tb drives.

---

### Post by rubylaser on 2011-07-01
> **collisionystm said:**
> Why do the internal drive of the os only?

Just raid the whole thing. 

If you want 8tb of storage, you had better do a Raid 10. You would be foolish to do anything else with that kind of data to loose.

Although I don't think they make 4tb hard drives yet, do they?

You will probably have to do 2 servers with Raid 10 on 2tb drives.


That would be wasteful in a home scenario (both in terms of disks / power use / and maintenance).  Most people need this for media storage, so a RAID6 with mdadm will be perfectly fine. You'd only need 6 2TB disks to get to 8TB, instead of 8 for a RAID10.   2TB disks are currently the have the best $/GB ratio (the OP said cost was an issue).  Plus, as mdadm currently stands, you can't expand a RAID10 array, something that most media storage users would like (collections only continue to grow).

If you don't need ultra fast throughput (concerns about platter density, > gigabit transfer speeds, etc.), a dual core processor and 2TB hard drives should be more than enough. I would get a motherboard that supports ECC memory, so for cost savings, that'd probably lead you to AMD, and make sure it has 8 SATA ports.

Finally, I'd get 6 of these...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145475&cm_re=hitachi_2tb-_-22-145-475-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145475&cm_re=hitachi_2tb-_-22-145-475-_-Product)
or these...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245&cm_re=samsung_2tb-_-22-152-245-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245&cm_re=samsung_2tb-_-22-152-245-_-Product)

---

### Post by LtPitt on 2011-07-01
I'd install [openfiler]("http://www.openfiler.com/") on a stupid usb stick and fire up the nastiest NAS you've ever had :)

---

### Post by mqhavic on 2011-07-01
Great replies Thanks..

What do you feel is the best setup for the server and media center / HTPC case?  Not really sure whats out there ? Should I do a SCSI to case or FIDI?  Motherboards to stay away from?

Thanks guys..

---

### Post by arrrghhh on 2011-07-01
> **mqhavic said:**
> Great replies Thanks..

What do you feel is the best setup for the server and media center / HTPC case?  Not really sure whats out there ? Should I do a SCSI to case or FIDI?  Motherboards to stay away from?

Thanks guys..

Well, HTPC case and that many hard drives usually are not uttered in the same sentence.

Usually HTPC cases are small, sleek and strive to look good next to your other components.  However, based on your requirements, you're going to need a pretty big case.

No clue what you mean about FIDI, sorry.

As for mobo's to stay away from, anything that's not a name brand.  I've had good luck with Asus boards myself.

---

### Post by rubylaser on 2011-07-01
Yeah, you definately  don't want an HTPC case with this many hard drives.  If you want to have flexibility in the future, and don't want to spend a ton of money on a case, I'd suggest [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811517007") and you'll want a PSU that's a single rail design so that it can power up multiple hard drives at once, something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026&cm_re=corsair_builder_series-_-17-139-026-_-Product").

That case isn't the prettiest, but it has great airflow, and would allow you to add [5-in-3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816133030") or [4-in-3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817993002&Tpk=coolermaster%204%20in%203") hard drive bays in the front to allow for up to 15 hard drives in the future if you so choose.  And, this PSU has the power to run all 15 drives if you ever get there :)

---

### Post by Lloyd_mcse on 2011-07-02
You could grab a little [Coolermaster 330 Elite]("http://www.coolermaster.co.uk/product.php?category_id=3586&product_id=30") for £39.99 (ish), and the Corsair CX430 - I have both running my file server 24/7 and have been great :)

---

