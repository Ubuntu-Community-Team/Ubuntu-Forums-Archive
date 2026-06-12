---
title: "Cloud/Server service compatible with ssh/rsync"
date: 2015-05-04
forum: Server Platforms
---

### Post by JunCTionS on 2015-05-04
I'm not sure how to look for this, and of course just searching on duckduckgo (or google) I mostly get biased reviews (paid for blog posts I presume).

So, I'm looking for a good cloud storage which I can SSH into and preferably use rsync. This is to make an offsite backup of my current backups (one on a Raspberry pi and another on a drive attached to my work computer, both to which I rsync into, but one which is failing atm.). 

I'd probably use about 2TB of storage.

Best option of all would be a web host where I could also install my owncloud, ttrss and other software. 

I imagine all clouds use some sort of RAID to prevent loss of data from disk failures, right?.

What is your experience on this? Or do you think there is a better place I can ask.

---

### Post by slickymaster on 2015-05-04
Since it's a support request, moved to the **Server Platforms** sub-forum

---

### Post by Lars Noodén on 2015-05-04
"There is no cloud, only other people's computers" but with that said about privacy they nearly all tend to support SSH and rsync, especially if they are running some GNU/Linux distro.  So it's mostly a matter of finding one in the price range you want.  I saw some articles last year, but cannot find them again, that showed a data loss rate in the mid-single digits.  So for me that indicates they are not a substitute for backup.  Anecdotally I knew of two instances where the hosting service failed and lost data.  I had the latest backups off line so I was able to restore and get going, another person lost a few days of business records because he was relying on the hosting provider.

---

### Post by JunCTionS on 2015-05-04
Oh right, I forgot to mention I looked into amazon cloud drive, and it didn't seem to support ssh. I think the same might go for dropbox and the like.
And sure, there's the whole privacy issue... I'm concerned about that, I just hope familiy pictures and videos shouldn't pose that much of a risk (but they could of course).

---

### Post by Lars Noodén on 2015-05-04
Ok.  That kind of service.  I looked into them for my own potential use a while back and never got far.  There were a lot I ruled out like Box, Dropbox and Amazon Cloud Drive.  
[http://www.zdnet.com/article/no-privacy-on-amazons-cloud-drive/](http://www.zdnet.com/article/no-privacy-on-amazons-cloud-drive/)
[https://www.amazon.com/gp/help/customer/display.html/ref=ap_footer_condition_of_use](https://www.amazon.com/gp/help/customer/display.html/ref=ap_footer_condition_of_use)

Spideroak fared somewhat better.  There were others but I can't recall them at the moment.  Of the category of those kind of services which require specialized client software, I didn't find any that I would feel comfortable using and eventually was so slow in searching that I found other solutions.  However, a new service in that area is Tarsnap, but I haven't had time to look in depth at its specs.  Curiously, some code does seem available for the client:
[https://www.tarsnap.com/download.html](https://www.tarsnap.com/download.html)

---

### Post by SeijiSensei on 2015-05-04
I run virtual machines at [Linode](http://www.linode.com/).  They are an excellent, reliable provider with great support.  The cheapest VM is $10/month.

---

