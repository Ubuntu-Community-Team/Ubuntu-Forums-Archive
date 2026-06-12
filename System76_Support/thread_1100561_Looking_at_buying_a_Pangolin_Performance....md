---
title: "Looking at buying a Pangolin Performance..."
date: 2009-03-19
forum: System76 Support
---

### Post by Jozza The Wick on 2009-03-19
Thomas,

I'm looking into getting a System76 laptop, upgrading from my Dell Inspiron (512Mb ram, 30Gb HD!). The pre- and post-sales support is what's convinced me to buy from System76 over other vendors. I do have a few questions, though (am looking at a Pangolin Performance):

1. Does the video card support dual monitors? If not, does any System76 laptop support this? (this might be a dealbreaker)

2. Am I right in assuming that the 7200RPM SATA II drive gives better performance than the 5400RPM drives?

3. I plan to wipe the install & do a 'minimal install' (with an encrypted linux & swap partitions), eventually building up to a XFCE-based system - do you forsee any problems with this?

4. I know you provide drivers for Windows XP - I plan to dual boot into XP, too.

5. I'm looking at some games that required a 'Geforce 6800 or better, with at least 256 MiB VRAM' - I think the GeForce 9300M meets that criteria? (I'm not familiar with differences in video cards)

6. If you guys made a port replicator / docking station, I would be very interested in that. I don't think you do, but please pass on my comments to your R&D people. :D

7. I'd probably want to buy a second power adapter, but they seem a little expensive. Anything special about them versus a generic one? :D

8. When I do wipe & reinstall, I'm probably going to put the 32-bit version rather than the 64bit, since there seem to be more packages & binaries available for it. Seems like 64bit is still rather cutting edge - is it worth the additional effort?

9. I'm sure I'll think of more questions, and will let you know when I do...

thanks!


Joseph

---

### Post by thomasaaron on 2009-03-19
Regarding the Pangolin Performance...
> 
1. Does the video card support dual monitors? If not, does any System76 laptop support this? (this might be a dealbreaker)

It has one VGA out (which can be used to clone your display to an external monitor or create an expanded display with an external monitor). It also has an HDMI output that can power a monitor, however, I'm not sure of the configuration possibilities here. This is the scenario on most of our laptops, except the Serval and Bonobo have a DVI output instead of a VGA output.

> 2. Am I right in assuming that the 7200RPM SATA II drive gives better performance than the 5400RPM drives?

Speed-wise, yes. Battery-wise, no.

> 3. I plan to wipe the install & do a 'minimal install' (with an encrypted linux & swap partitions), eventually building up to a XFCE-based system - do you forsee any problems with this?

We do no testing with XFCE, and we don't support it, so I'm not sure how much difficulty you will have getting the cam, fingerprint reader and nVidia going on it. You *may* just be able to run our System76 driver on it with success. Or you can crack open the driver and see how we enable them in Ubuntu. It will *probably* take some tweaking.

This is a personal opinion, and I certainly don't expect you to buy into my way of thinking: Minimal OSes were great when hardware was slower. Other than personal preference, I don't really see the need for them on modern technology. Just my opinion.

> 4. I know you provide drivers for Windows XP - I plan to dual boot into XP, too.

Not a problem.

> 5. I'm looking at some games that required a 'Geforce 6800 or better, with at least 256 MiB VRAM' - I think the GeForce 9300M meets that criteria? (I'm not familiar with differences in video cards)

Yes, it meets that standard. Typically with nVidia cards, the higher the model number the more powerful they are. Make sure, though, that you don't skimp to badly on the cpu and memory. I'd want to upgrade the CPU to about an P8600 or higher and have 3GB of RAM.

> 6. If you guys made a port replicator / docking station, I would be very interested in that. I don't think you do, but please pass on my comments to your R&D people.

Done. We only have a few requests a year for port replicators. I'm not sure the demand is high enough for profitability, but it's passed on.

> 7. I'd probably want to buy a second power adapter, but they seem a little expensive. Anything special about them versus a generic one?

Nope. Just make sure the specs match up. I can help you with that when you are ready.

> 8. When I do wipe & reinstall, I'm probably going to put the 32-bit version rather than the 64bit, since there seem to be more packages & binaries available for it. Seems like 64bit is still rather cutting edge - is it worth the additional effort?

In my opinion, 64-bit Ubuntu is superior to 32-bit. It has better suspend/hibernate support, it takes better advantage of the 64-bit architecture of our machines, and the 64-bit repositories contain pretty much everything that is in the 32-bit repositories. Flash and Java now have 64-bit plugins. 64-bit is no longer a sub-standard OS, like it was a year or two ago.

> 9. I'm sure I'll think of more questions, and will let you know when I do...

You know where to find me.:popcorn:

---

### Post by Jozza The Wick on 2009-03-19
Thomas,

Thanks for your response! 

1. Do you know if I could plug in an external monitor to the VGA out and another to the HDMI out at the same time? (You may have already said that you don't know the answer to this question, but it's not clear to me).

2. You're probably right on the 'minimal' install, but one of the reasons that I got back into Linux in the first place is that I knew I'd be upgrading my computer and didn't want the massive hardware upgrade to be swallowed by a massive jump in minimum O/S hardware requirements. I like the idea that I can run Ubuntu 7.10 (if I wanted) on my new machine, rather than go from XP to Vista on a machine that's about 10 times more powerful, but not see any noticable performance improvements.

I plan on going with 4Gb of memory, and the P8700. Or, is it worth the 6Mb cache? I imagine that the biggest gain is maxining out memory, then increasing HD speed? 

Anyway, may try minimal, or may not bother... :D It's all about effort required versus reward gained :D

3. Encrypted partitions - do you know if I would have any problems with LUKS or dm-crypt?

thanks again!

Joseph

---

### Post by thomasaaron on 2009-03-19
> 1. Do you know if I could plug in an external monitor to the VGA out and another to the HDMI out at the same time? (You may have already said that you don't know the answer to this question, but it's not clear to me).

I've not tried it, and my HDMI monitor was sent out for testing. I'm 95% sure that you can run one monitor off of HDMI and another off of the VGA port. What I'm not sure about is how configurable that kind of a set-up would be (i.e. expanded desktops).

> 3. Encrypted partitions - do you know if I would have any problems with LUKS or dm-crypt?

I've never tested with either of these, so I couldn't say for sure. Intrepid has a neat feature, though, that allows you to create a private encrypted directory. It seems like a very useful feature. See...

[http://tombuntu.com/index.php/2008/09/23/encrypted-private-directory-in-ubuntu-810/](http://tombuntu.com/index.php/2008/09/23/encrypted-private-directory-in-ubuntu-810/)

---

### Post by jpoRS on 2009-03-20
Just for clarification, I am not a System76 employee, just user (I got my Pangolin about six months ago)  Therefore my advice is probably best taken with a grain of salt.

I don't know what your resources are, but when I compared the specs of my old laptop power adapter to my Pangolin's power adapter, they matched.  Hooray free extra power adapter!  Even if you don't have an old laptop/old compatible adapter, keep your eyes/ears peeled for a friend getting rid of an old laptop.  You may be able to scavenge your way into electronic freedom!

Also, if I could chip in on the 32/64 question: Go for it.  I have been running the 64 bit and it is so much faster.  I haven't run into any real compatibility issues.  

Either way, enjoy your new toy!
jim

---

### Post by Jozza The Wick on 2009-03-20
Thanks, jpoRS!

Thomas - look for order #7244.

Everyone else (hey, I'm a business-type guy so I like point these things out) - please notice that effective, responsive customer support generates sales. :) One of the reasons that I decided to go with System76 is the post-sales support that Thomas (and maybe others?) provides. I know that I can come back with a question even a few months later and get patient, dedicated knowledgeable help. You think Dell offers that? :D

Anyway, rant over. Plus, I'm preaching to the choir I'm sure. Thanks again Thomas!

---

### Post by betrunkenaffe on 2009-03-20
> **Jozza The Wick said:**
> Thanks, jpoRS!

Thomas - look for order #7244.

Everyone else (hey, I'm a business-type guy so I like point these things out) - please notice that effective, responsive customer support generates sales. :) One of the reasons that I decided to go with System76 is the post-sales support that Thomas (and maybe others?) provides. I know that I can come back with a question even a few months later and get patient, dedicated knowledgeable help. You think Dell offers that? :D

Anyway, rant over. Plus, I'm preaching to the choir I'm sure. Thanks again Thomas!

Yep, and if thomas doesn't know, he's always willing to look into it.. not to mention the other users.

---

### Post by Jozza The Wick on 2009-04-08
Thomas - I see my laptop has been shipped & am very excited to receive it on Friday!! I have one quick question. I will probably buy a laptop keyboard protector to help preserve it, since I tend to eat & drink at my computer desk. Looking at something like this:

[http://www.protectcovers.com/laptop.htm](http://www.protectcovers.com/laptop.htm)

Do you happen to know if the S76 kepyboard layout fits any standard type? Or, does S76 sell keyboard protectors?

thanks again!

---

### Post by thomasaaron on 2009-04-08
We don't sell them, but that's a seriously great idea.

The keyboard is pretty standard.

---

### Post by Jozza The Wick on 2009-04-09
Yeah, you could get custom Ubuntu / System76 ones... 

Definitely gonna get one for the new machine - I like eating chocolate & cookies and potato chips while playing on computer - you can imagine the results! :D. Will let you know how it goes (i.e. if I need a custom one or can use a standard layout)

---

### Post by Jozza The Wick on 2009-04-14
Thomas - would you be able to find out from your hardware guys what other computers the same keyboard design is used in? Then I could order a laptop keyboard cover for a more 'mainstream' computer that would also fit the Pangolin...

I did try telling one company that (via a livechat 'support') that 'this probably isn't a a company that you've seen before, they're called System76' but I could see that she wasn't able to cope with something that wasn't on her prepared answer script...

The keyboard does look kinda Mac-ish - maybe an Apple cover might fit it?

Also, (sorry should have said this earlier) - I love the Pangolin!! It's fantastic - what a great machine! Gonna show it off to some buddies this weekend...

---

### Post by thomasaaron on 2009-04-14
I'm not trying to see how useless I can be here, but I'm not aware of any of the manufacturers on their list using this keyboard. 

I got on their little chat thingy, and gave them all the info I could. They sent me to Visiflex ( [http://www.viziflex.com/store/template.cfm/ses_/mc,list,x,13,0,x/Viziflex%20Keyboard%20Seels/](http://www.viziflex.com/store/template.cfm/ses_/mc,list,x,13,0,x/Viziflex%20Keyboard%20Seels/) ). I called their 1-800 number and they said they do not have them either.

---

