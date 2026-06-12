---
title: "Will Ubuntu 12 beta properly upgrade to release?"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Poma on 2012-03-21
We want to install Ubuntu to our servers. Right now Ubuntu 10.04 LTS does not support our SAS controller and we also don't want to install non-LTS version. The next LTS version 12.04 is currently in beta stage. So, the question is: will beta automatically upgrade to stable version or we will need to reinstall it on april 26?

---

### Post by Bucky Ball on 2012-03-21
_It would be a ***really*** bad idea to install 12.04 LTS to production machines (servers) at this point!_ There will be breakages. It is still testing. I would wait a month or two after release, rule of thumb ...

You have the right idea sticking with LTS releases, though (five year support).

The answer to your question, though, is yes; you just keep updating and you will end up with the released version eventually, but that would be the least of you problems if you go ahead with installing it now. When you say 'we' I am imagining a company/business/institution. You would run the risk of losing a lot of hours fixing breakages and a 12.04 LTS install at this point could bring your enterprise to a standstill if you're relying on the servers. ;)

Possibly more info on the SAS controller might be helpful and finding out for certain if there is no workaround for 10.04 LTS as it's rock solid and would give you the leeway to wait off for a couple of months after 12.04 LTS release. Then it is a one click upgrade. 10.04 LTS server = support to April 2015. That would definitely be my course of action if there is a way (and would probably stick with it until end of life).

Otherwise, hold off for a few months would be wise and in the meantime install 12.04 LTS server edition on a spare partition or box and familiarise.

---

### Post by Elfy on 2012-03-21
You'd not need to  reinstall, there are a lot of updates at the moment - I'd guess I've seen ~500Mb here since beta was released - but it is beta still.

Whether you'd want to run a beat release on your servers of course is a question only you can answer.

Moved to Dev forum

---

### Post by Poma on 2012-03-21
Did you say I can update major version with one click (10.04 -> 12.04)? Will I have the same system as if I installed 12.04 from scratch? What are potential risks or problems with this procedure?

My problem is that installation does not detect my LSI MegaRAID SAS 9240-4i controller. [Here is the link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091"). This bug is fixed in version 11.10. So maybe it is better to install 11.10 wait for one two months and then upgrade to 12.04?

P.S. Yes, we are a company. Currently we introducing new server setup and we want to configure it only once so that we'll never need to upgrade major version.

---

### Post by Bucky Ball on 2012-03-21
Here is the driver for 10.04 LTS:

[http://www.lsi.com/Pages/user/eula.aspx?file=http%3a%2f%2fwww.lsi.com%2fdownloads%2fPublic%2fMegaRAID%2520Common%2520Files%2fUbuntu_10.04_LTS_05.30.zip&Source=http%3a%2f%2fwww.lsi.com%2fchannel%2fproducts%2fstoragecomponents%2fPages%2fMegaRAIDSAS9240-4i.aspx]("http://www.lsi.com/Pages/user/eula.aspx?file=http%3a%2f%2fwww.lsi.com%2fdownloads%2fPublic%2fMegaRAID%2520Common%2520Files%2fUbuntu_10.04_LTS_05.30.zip&Source=http%3a%2f%2fwww.lsi.com%2fchannel%2fproducts%2fstoragecomponents%2fPages%2fMegaRAIDSAS9240-4i.aspx")

... from this page:

[http://www.lsi.com/channel/products/storagecomponents/Pages/MegaRAIDSAS9240-4i.aspx](http://www.lsi.com/channel/products/storagecomponents/Pages/MegaRAIDSAS9240-4i.aspx)

... and a bunch of other links to trawl:

[http://www.google.com.au/#hl=en&output=search&sclient=psy-ab&q=LSI+MegaRAID+SAS+9240-4i+ubuntu+10.04&oq=LSI+MegaRAID+SAS+9240-4i+ubuntu+10.04&aq=f&aqi=&aql=&gs_sm=3&gs_upl=1176l5850l0l6501l14l14l0l0l0l0l312l3714l2-13.1l14l0&gs_l=hp.3...1176l5850l0l6502l14l14l0l0l0l0l312l3714l2-13j1l14l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=91ab9ffd81bcd339&biw=1024&bih=597](http://www.google.com.au/#hl=en&output=search&sclient=psy-ab&q=LSI+MegaRAID+SAS+9240-4i+ubuntu+10.04&oq=LSI+MegaRAID+SAS+9240-4i+ubuntu+10.04&aq=f&aqi=&aql=&gs_sm=3&gs_upl=1176l5850l0l6501l14l14l0l0l0l0l312l3714l2-13.1l14l0&gs_l=hp.3...1176l5850l0l6502l14l14l0l0l0l0l312l3714l2-13j1l14l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=91ab9ffd81bcd339&biw=1024&bih=597)

Incidentally, from the link you provided, the same bug appears to exist in 11.04, 11.10 AND is confirmed in 12.04 LTS (post # sixty eight) so there goes that idea.

There are a couple of folk who provide workarounds for this in 10.04 which you might have missed, notably post #59.

---

### Post by jerrylamos on 2012-03-21
Topic is a frequent question.  I do mostly testing and  personal use, so in this "development" forum I do frequent installs and have multiple partitions of pangolin because I'm looking for bugs.  Pangolin installs are great for causing bugs.

Now having both Oneiric and Pangolin running on test pc's from current to 2006, I'm not sure what the compelling reason would be to update to Pangolin LTS early?  The goal of Pangolin is LTS stability, from my view not much "new" just some desktop refinements.

If you're at all concerned about stability, wait for the final release which is due shortly.  Even Beta 2 is due Thursday next week.

Good luck.

Jerry

---

### Post by kansasnoob on 2012-03-21
> **Bucky Ball said:**
> _It would be a ***really*** bad idea to install 12.04 LTS to production machines (servers) at this point!_ There will be breakages. It is still testing. I would wait a month or two after release, rule of thumb ...

You have the right idea sticking with LTS releases, though (five year support).

The answer to your question, though, is yes; you just keep updating and you will end up with the released version eventually, but that would be the least of you problems if you go ahead with installing it now. When you say 'we' I am imagining a company/business/institution. You would run the risk of losing a lot of hours fixing breakages and a 12.04 LTS install at this point could bring your enterprise to a standstill if you're relying on the servers. ;)

Possibly more info on the SAS controller might be helpful and finding out for certain if there is no workaround for 10.04 LTS as it's rock solid and would give you the leeway to wait off for a couple of months after 12.04 LTS release. Then it is a one click upgrade. 10.04 LTS server = support to April 2015. That would definitely be my course of action if there is a way (and would probably stick with it until end of life).

Otherwise, hold off for a few months would be wise and in the meantime install 12.04 LTS server edition on a spare partition or box and familiarise.

Great explanation!!!!!!!!!!!!!!!!!

IMHO if you have to ask wait for the official release ;)

---

### Post by Poma on 2012-03-21
It works for me in 12.04 beta and 11.10. Unfortunately I'm a noob in linux so I'm not able to recompile driver and insert it during the install. Also I'm afraid that when I upgrade to new kernel version driver may become invalid (since it's compiled against different kernel) and my system will be unable to detect disks upon reboot. This will be not so good situation.

So I decided to install 12.04. We will set up everything and open this server for public use in the middle of april (after FinalFreeze)

---

### Post by Bucky Ball on 2012-03-21
Good luck with it all. If you consider this thread solved please mark it as 'Solved' from Thread Tools. ;)

PS: Thanks, kansasnoob. :)

---

