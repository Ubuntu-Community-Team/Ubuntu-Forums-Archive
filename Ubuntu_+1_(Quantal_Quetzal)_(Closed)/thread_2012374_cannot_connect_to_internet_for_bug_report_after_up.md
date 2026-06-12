---
title: "cannot connect to internet for bug report after update"
date: 2012-06-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-29
Apport reported an internal system, error .. and then I got this:

---

### Post by dino99 on 2012-06-29
broken here too on i386

---

### Post by ventrical on 2012-06-29
It tells me I have broken packages waiting and being held back but synaptic reports nothing. It's like a Nvidia-minator Monster came in and ripped the drivers right out:)

i386Dual Core, Intell MoBo

---

### Post by kansasnoob on 2012-06-29
This be the bug:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334)

Kicked my butt during iso-testing.

And now [the forums are kicking me in the same place]("http://ubuntuforums.org/showthread.php?t=2012354") about not being able to edit previous posts :mad:

---

### Post by cariboo on 2012-06-29
> **kansasnoob said:**
> This be the bug:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334)

Kicked my butt during iso-testing.

And now [the forums are kicking me in the same place]("http://ubuntuforums.org/showthread.php?t=2012354") about not being able to edit previous posts :mad:

We are being inundated by spammers, 200-500 new ones per day, so until we can upgrade the forum and take advantage of new features available in vBulletin 4.X We have had to take some fairly drastic measures to make the forum at least usable.

We are being held up by Mr. Shuttleworth's insistence that Single Sign On work with the latest version of vBulletin, but the end is in sight, as the problem seems to be solved, with only a licensing issue holding things up.

---

### Post by kansasnoob on 2012-06-29
> **cariboo907 said:**
> We are being inundated by spammers, 200-500 new ones per day, so until we can upgrade the forum and take advantage of new features available in vBulletin 4.X We have had to take some fairly drastic measures to make the forum at least usable.

We are being held up by Mr. Shuttleworth's insistence that Single Sign On work with the latest version of vBulletin, but the end is in sight, as the problem seems to be solved, with only a licensing issue holding things up.

I've never seen spam added to any of my existing "posts", to the "thread" certainly, and I always report it quickly.

I don't see how changing the ability to edit an existing post effects spam but I digress. This won't really effect me. It will only effect those who I'd hoped to communicate with so it will just be more difficult for them to learn what I've already learned. Probably no great loss ;)

---

### Post by mc4man on 2012-06-29
> **ventrical said:**
> Apport reported an internal system, error .. and then I got this:
While probably not the nautilus crash, (only a few seem currently affected) if that then apport wouldn't work until nautilus is restarted. 

You can always try going to /var/crash/, finding the crash file & doing a r. click on, ect.

It's also worthwhile to clean out /var/crash occasionaly 

(.crash, .upload, .uploaded

---

### Post by ventrical on 2012-06-29
> **mc4man said:**
> While probably not the nautilus crash, (only a few seem currently affected) if that then apport wouldn't work until nautilus is restarted. 

You can always try going to /var/crash/, finding the crash file & doing a r. click on, ect.

It's also worthwhile to clean out /var/crash occasionaly 

(.crash, .upload, .uploaded

Thanks mc4man. I'll give that a try.  Thanks for staying on topic too! :) lol

---

### Post by kansasnoob on 2012-06-30
> **ventrical said:**
> Thanks mc4man. I'll give that a try.  Thanks for staying on topic too! :) lol

Sorry for going off-topic but my hair was on fire :oops:

OTOH I did list the [bug #]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334") :)

I did some follow up testing yesterday and I'm sure the devs will nail it soon.

---

### Post by balloons on 2012-06-30
Yes, this was nasty to me as well during iso testing. I ended up using the precise version of apport to file the bugs. Re-filing via looking in /var/crash just gave the same error :-( I had to install the old version and feed the error to it before it filed ;-)

---

### Post by ventrical on 2012-06-30
> **kansasnoob said:**
> Sorry for going off-topic but my hair was on fire :oops:

OTOH I did list the [bug #]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334") :)

I did some follow up testing yesterday and I'm sure the devs will nail it soon.


Everybodys' hair is on fire up here in the mid-west :) no pun intended :) lol

Thanks for the bug list.

---

### Post by ventrical on 2012-06-30
> **guitara said:**
> Yes, this was nasty to me as well during iso testing. I ended up using the precise version of apport to file the bugs. Re-filing via looking in /var/crash just gave the same error :-( I had to install the old version and feed the error to it before it filed ;-)

Thanks guitara. I did check that directory out. I'm about to do an update on that install.

---

