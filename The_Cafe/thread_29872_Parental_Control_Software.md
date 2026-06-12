---
title: "Parental Control Software"
date: 2005-04-26
forum: The Cafe
---

### Post by Psquared on 2005-04-26
Does anyone know of "any" parental control software that will control wireless internet access remotely.

We have a home network with 2 teenage boys with their own computers. The main computer is hardwired to a 2Wire Homeportal and the other computers connect via wireless adapters. We have Bellsouth DSL and they want another $5 per month to enable parental controls. These controls would allow us to block their internet access at certain times of the day - so they will do their homework rather than play on the internet.

Surely there is another way to do this -- by some software program; and preferably something opensource.

Ideas??

---

### Post by TravisNewman on 2005-04-26
There's the option of filtering by mac address, and then just blocking their mac address whenever you want them to do their homework or whatever, and that doesn't require any software at all, just a web browser to connect to the router.

---

### Post by HungSquirrel on 2005-04-26
If your main computer were the router, you could probably write a shellscript that disabled their connections and have it be run as a cron job.  But, because you're disabling their connections via a seperate router, you'll have to stick with doing it manually for now if I'm not mistaken.

---

### Post by darkoptix on 2005-04-26
I would suggest not blocking the internet at certain times of the day. You must have people trust that would do things, it's a good skill to learn. However, if you have an old computer, look at [www.freesco.org](www.freesco.org) . It's free, and allows cron jobs so you could set it to block certain connections at a time.

---

### Post by Psquared on 2005-04-30
Thanks for the help. Seems like I could update the firmware on my 2Wire Home Portal somehow to include the parental control function. To charge 5.00 a month for this seems outrageous.

I will say that Bellsouth has been very helpful in the past so maybe they would do it for free to keep me from moving to Road Runner. ;)

---

### Post by Nopposan on 2006-12-13
Do your kids' computers have linux installed?  I'm not sure how to do this, but I believe putting a few lines in their crontab can get their computers to block access to the internet at certain times of day; I'm going to work on this too, so I'll try and let you know how it goes.

---

### Post by thomasaaron on 2006-12-13
Yes and no.

I use Dansguardian and Tinyproxy for filtering. It works great, but it's not that hard to turn off.

However, I could not find any accountability software that lets someone know where someone has been on the Internet. So I wrote a program in Python that decodes the mork file that evolution's history is kept in and emails a list of all URL's visited to an accountability partner.

It's not a perfect setup, but you can figure out a lot by deduction.

For example, if somebody clears their evolution history, the next accountability report you receive will be virutally empty, and you might decide it is worth getting suspicious over.

Or if you cease to get daily accountability reports, you know someone has turned off the accountability program.

So far, that's the best I've been able to do.
If you like, I could share the program with you.

Also, a very clear tutorial on setting up Dansguardian and Tinyproxy for content filtering is availabe in the November issue of Linux Journal.

Best,
Tom

---

### Post by Nopposan on 2006-12-13
Well, I'm not sure evolution will be installed by default in Xubuntu, so 'not sure your python script would actually work on the box I'll be using.  Thanks though.

I'll look into the Linux Journal archives for the tutorial.  Thanks again.

---

