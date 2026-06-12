---
title: "Suspend in ubuntu!"
date: 2008-04-05
forum: The Cafe
---

### Post by kevin11951 on 2008-04-05
My computer is a dell inspiron b130, and i decided to take a video of me suspending it, and un-suspending it.

it worked flawlessly!

have a look:

[http://www.youtube.com/watch?v=jW5OQIzGPHc](http://www.youtube.com/watch?v=jW5OQIzGPHc)

---

### Post by quanumphaze on 2008-04-06
I hate you :cry:

Please do tell some details

---

### Post by igknighted on 2008-04-06
I didn't realize this was something that caused grief in linux (aside from well documented shortcomings with the ATI drivers).  It's always worked flawlessly for me with pretty much every distro.

---

### Post by quanumphaze on 2008-04-06
Suspend is one of those things that you don't know how much you need it until it's gone.

I'm sorta lucky that mine sometimes works. It suspends alright but to wake it up is the deal breaker.
<rant>
[SIZE="1"]I press any key as usual, but instead of being greeted with the locked prompt I just get a blank screen. Then I have to fiddle the bluetooth switch ~15 times or the laptop lid closed button ~7 times to get it to wake up. (wireless switch may work but kills wireless until next boot).
I type my password and away I go. Often it freezes connecting to wireless (university wireless is the main culprit) and is generally unstable until reboot.
Forget about a second suspend, when it wakes up it is really weird (eg: shutdown pauses until I touch the trackpad)[/SIZE]
</rant>

I have no idea what causes it, but it is the biggest think I hope is fixed in Hardy. But for now I can cope (barely)

---

### Post by fedex1993 on 2008-04-06
also why dont you actually put it in the right place the post

---

### Post by kevin11951 on 2008-04-06
> **fedex1993 said:**
> also why dont you actually put it in the right place the post

and where might that be?

---

### Post by riven0 on 2008-04-06
> **quanumphaze said:**
> .
<rant>
[SIZE="1"]I press any key as usual, but instead of being greeted with the locked prompt I just get a blank screen. Then I have to fiddle the bluetooth switch ~15 times or the laptop lid closed button ~7 times to get it to wake up. (wireless switch may work but kills wireless until next boot)...

I used to have the suspend problem on where I would get a blank screen on resume. However, I found a thread on these forums that posted a solution to the problem:

1. Open up the file /etc/default/acpi-support

2. Find the line POST_VIDEO=true and change it to: 
POST_VIDEO=

3. Reboot

4. Profit! :popcorn:


I haven't had a problem for over a year now.

---

### Post by fedex1993 on 2008-04-06
hmm offtopic or here

---

### Post by riven0 on 2008-04-06
Actually, this probably does belong in the Hardware & Laptops forums.

---

### Post by fedex1993 on 2008-04-06
yeah i would say or even if its 8.04 would be in there to dono but this is sort of the off place to post it

---

### Post by p_quarles on 2008-04-06
> **riven0 said:**
> Actually, this probably does belong in the Hardware & Laptops forums.
> **fedex1993 said:**
> yeah i would say or even if its 8.04 would be in there to dono but this is sort of the off place to post it
This isn't a support question, so doesn't belong in the support forums.

In any case, those who believe a thread was misplaced should *report* the thread to the staff rather than harass the OP.

---

### Post by quanumphaze on 2008-04-06
I believe it may be my fault, I was not exactly asking for help with my thing just having a rant (I'm too lazy to fix it anyway, might make it worse) and the OP was just showing us that it works perfectly on his.

IMO this still belongs in the Cafe

Back off topic, I played with the POST_VIDEO to fix up [this problem]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/91966") (broke in an intel-xorg update though) by commenting it out, but I'll try blanking it.
I think the instability may be from the Atheros wireless I have.

---

### Post by swoll1980 on 2008-04-06
my dell latatude 100L suspends with no problem

---

### Post by darrenn on 2008-04-06
quanumphaze suspend works fine with Fiesty and Hardy just so you know. I have the same laptop as you do. Under Gutsy you can press the power button several times and that will bring it out of suspend. But that is a major pain in the *** so I didn't upgrade to Gutsy. And I couldn't get it to work other than that.

---

### Post by toupeiro on 2008-04-06
Suspend working great in 8.04 64-bit wubi/ubuntu.

---

### Post by DMcA on 2008-04-06
Suspend works great for me in Gutsy with my acer aspire laptop using the free graphics driver. Unfortunately it fails miserably with the fglrx driver for my ATI card (which I do need for googledocs and 3D modelling)

---

