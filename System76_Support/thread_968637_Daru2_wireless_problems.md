---
title: "Daru2 wireless problems"
date: 2008-11-02
forum: System76 Support
---

### Post by j.c.sackett on 2008-11-02
So I've developed a problem with my wireless in my daru2.

It works normally if wireless is already on when I boot up. However, if I boot up with wireless off, it stays disabled even when I turn it on.

I've tried killing and restarting nm-applet and restarting networking in init.d and that still doesn't get it to work.

Anyone have any ideas on what I can try?

---

### Post by jdb on 2008-11-02
> **j.c.sackett said:**
> So I've developed a problem with my wireless in my daru2.

It works normally if wireless is already on when I boot up. However, if I boot up with wireless off, it stays disabled even when I turn it on.

I've tried killing and restarting nm-applet and restarting networking in init.d and that still doesn't get it to work.

Anyone have any ideas on what I can try?

I've had wireless problems on my daru2 in the past that this has fixed:

sudo dpkg-reconfigure network-manager

It takes a minute or so for the network to come back up after you issue the command.

jdb

---

### Post by j.c.sackett on 2008-11-03
Thanks for the tip, but that didn't address it. I've gone so far as to purge and reinstall network-manager, and still no effect.

---

### Post by j.c.sackett on 2008-11-03
Okay, the problem is a bit more general.

If I turn off wireless, and turn it back on (using the button), wireless will not actually come back on (i.e it's still shown as disabled).

So basically, turning wireless on doesn't actually turn wireless on. If the computer boots with wireless on, all is well.

---

### Post by thomasaaron on 2008-11-03
How long are you waiting before concluding that it doesn't turn back on. Sometimes this does takes a while.

Second, you may need to press the wireless button twice. The first time turns on bluetooth, the second time turns on wireless. You should have two LEDs on in the wireless slot on the front, right corner of your computer.

---

### Post by j.c.sackett on 2008-11-03
> **thomasaaron said:**
> How long are you waiting before concluding that it doesn't turn back on. Sometimes this does takes a while.

I've waited up to half an hour without it coming back on.

> Second, you may need to press the wireless button twice. The first time turns on bluetooth, the second time turns on wireless. You should have two LEDs on in the wireless slot on the front, right corner of your computer.

Both lights come on with one click. A second button press turns it all off again.

---

### Post by thomasaaron on 2008-11-03
> I've waited up to half an hour without it coming back on.
Yeah, I would call that excessive! :lolflag:

> Both lights come on with one click. A second button press turns it all off again.

OK, that is normal too. Some DarU2 did it one device at a time. Please file a bug report here:

launchpad.net/system76

Please confirm in the bug report that this is happening after a clean boot-up, and not after hibernate.

---

### Post by j.c.sackett on 2008-11-03
> **thomasaaron said:**
> Yeah, I would call that excessive! :lolflag:

Glad we agree. :-P


> 
OK, that is normal too. Some DarU2 did it one device at a time. Please file a bug report here:

launchpad.net/system76


Righto. It's been filed.

> 
Please confirm in the bug report that this is happening after a clean boot-up, and not after hibernate.

Clean boot-up, hibernate, or even if I just turn it off and back on while still running--it happens regardless. I made note of that.

---

### Post by elusivespoon on 2008-12-10
Any progress on this? For some reason my computer will randomly boot without wireless enabled even though I have turned it off, so I have to switch it on and reboot to go on-line.

---

### Post by thomasaaron on 2008-12-11
Not really.

I'm not able to reproduce this on our shop darter. So, either it is some sort of config issue, or a module not loading consistently, or it is a hardware issue. Due to the intermittent nature of it, I'm betting software/configuration.

You might want to do a fresh install at some point to see if the problem goes away. Another option would be to flash the bios or clear the cmos.

I'm not sure what your warranty status is (and wouldn't want to post it in the forums anyway). But if you want to contact me via email, I can check, and also walk you through the steps I just mentioned.

---

### Post by elusivespoon on 2009-01-27
> **thomasaaron said:**
> I'm not sure what your warranty status is (and wouldn't want to post it in the forums anyway). But if you want to contact me via email, I can check, and also walk you through the steps I just mentioned.
I've tried sending an e-mail and a PM, and haven't heard anything back. Can I get a reply ? :)

---

### Post by thomasaaron on 2009-01-27
> I've tried sending an e-mail and a PM, and haven't heard anything back. Can I get a reply ? :) 

I don't see any private messages in my forum account, and I've not seen an email come through.

I can't really check your warranty status without your name and/or order number. Of course, I'd hate for you to put either of those on the forums.

Can you try emailing me again (support-at-system76-dot-com). Or give me a call. [http://system76.com/article_info.php?articles_id=24](http://system76.com/article_info.php?articles_id=24)

---

### Post by elusivespoon on 2009-01-28
I just sent an e-mail entitled "Wireless Problem" referencing this thread to support-at-system76-dot-com.

---

### Post by thomasaaron on 2009-01-28
OK. I see it. I'll respond to it this morning.

Edit:
I searched and found your other one too. Sorry, I missed it.

---

