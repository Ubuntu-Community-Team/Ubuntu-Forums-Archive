---
title: "Lubuntu 18.04 for TV BOX &amp; Raspberry Pi  -- THE FUTURE"
date: 2018-07-13
forum: Ubuntu, Linux and OS Chat
---

### Post by Pierre16 on 2018-07-13
The FUTURE OF LUBUNTU as Lightweight Distribution.

I am a long-time Lubuhtu user and absolutely love it. However, it is becoming less and less needed as computer specs have vastly improved and can easily run full versions of Ubuntu. As such, I think it was brilliant to issue a version for the Raspberry Pi.

However, even the Raspberry Pi comes out twice as expensive as a Tv Box once you add all the extras and postage. A TV Box with 2 GB RAM can be had for about 30 to $40, including delivery, and would make a wonderful FANLESS PC.

I would like to suggest that Lubuntu develop a version (LTS) for TV boxes. These would make wonderful fanless silent and dirt cheap computers if Lubuntu could be installed on them. Lubuntu already has a certain expertise with arm processors from developing its Raspberry Pi version. Armbian is a system that could be installed on a TV box. However, as a private issue I would not trust it for doing my banking and other stuff. Only an official distro like Lubuntu would do. Armbian is also incredibly difficult to install and is full of bugs.

As I am not a regular forum user or Lubuntu contributor. I'm asking anybody who like this idea to promote it and post it on on social media as much as they can and get it to Lubuntu developers as well.

I personally have a rooted TX3 mini TV box that has an amlogic S905X processor. I very much hope that a Lubuntu version can be developed for it. Other common processor for TV boxes are the s905w and s912.

Thank you all.

---

### Post by coffeecat on 2018-07-13
Not a support question. *Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by PaulW2U on 2018-07-13
Who is going to do all of this work? It's my understanding that there are only a couple of developers within the Lubuntu team. They are not Canonical employees and may well have day jobs away from Lubuntu. I would imagine that they are focussed on getting their new installer (Calamares) working correctly and busy transitioning to LXQt. Lubuntu 18.10 is going to look quite different to previous releases.

Why not contact the developers directly for their initial comments? Their mailing list is [here]("https://lists.ubuntu.com/mailman/listinfo/Lubuntu-devel").

---

### Post by tsimonq2 on 2018-07-14
I came across this thread and wanted to give a few responses.

> As such, I think it was brilliant to issue a version for the Raspberry Pi.

It's on the TODO list, after Calamares can do OEM (which is essentially what we would be doing post-install).

> I would like to suggest that Lubuntu develop a version (LTS) for TV boxes.

I don't have one of these. Are you willing to develop everything needed for this?

> It's my understanding that there are only a couple of developers within the Lubuntu team.

Walter has taken a hiatus to spend time with family, so we're down to just me doing all of the work on Lubuntu at the moment.

> I would imagine that they are focussed on getting their new installer  (Calamares) working correctly and busy transitioning to LXQt.

That's exactly right. If it's not critical to ship, at the moment, it's bumped down on the TODO list.

Thanks.

---

### Post by Pierre16 on 2018-07-14
> **tsimonq2 said:**
> 


It's on the TODO list, after Calamares can do OEM (which is essentially what we would be doing post-install).




Really, my interest is for TV Boxes, which are half the price and ready to go (power supply, cables, frame, case, ethernet, wifi, etc.) right out of the box.  

> **tsimonq2 said:**
> 


I don't have one of these. Are you willing to develop everything needed for this?



Walter has taken a hiatus to spend time with family, so we're down to just me doing all of the work on Lubuntu at the moment.




Unfortunately, I am not a coder.  HOWEVER, YOU ARE NOT ALONE:

1) I would think that there are major similarities with the Raspberry Pi.  So, some of the work is done.  Would it be able possible to have a combo version compatible with both, the Raspberry Pi and the tv boxes?

2) There is already a private Debian-based version (Armbian) available.  You may be able to join forces.

3) I think that there is a huge commercial opportunity here.  Ubuntu has not really broken into the PC market, unfortunately.  This might be it.  Who would not want a PC with full-fledged OS for $50-$75?  There is about 3 billion people in developing economies.

     LUBUNTU is not a commercial venture BUT UBUNTU is!  They could do all the developing for you/themselves!

---

### Post by Pierre16 on 2018-07-14
Adding to the above:

4) I could easily see Ubuntu (or even you, as a paid developer) working with the TX3 or MX Box people directly to have an Ubuntu or Lubuntu box.  Since the hardware is the same, these commercial companies could greatly expand their sales for the box that they are already making for very little additional cost.  

You may want to propose it to UBUNTU.  I do not have any contact with them, but you probably and would be the best person to sell the idea.  

Thanks for your time in developing Lubuntu, BTW!

---

### Post by cariboo on 2018-07-14
I'd suggest posting [here]("https://community.ubuntu.com/"), to see if you can find a developer for your project, you'll probably have to supply the developer with hardware, if you want to see this through.

---

### Post by QIII on 2018-07-14
Ubuntu is not a commercial venture.  It is an operating system distributed by a commercial venture known as Canonical, Ltd.  Canonical makes no revenue directly from Ubuntu, but from service/support contracts.  They are not likely to find it worth their while to expend a great deal of resources in creating something that will have such a small population of users -- none of whom would likely buy a support contract.

The developers of the flavors are small communities (if you can call two people a "community" in the case of Lubuntu) who give of their own time to develop and maintain the flavors.  They dedicate a good deal of their private time to that end -- and they have real lives besides.

There are also people who have given their time to port Ubuntu flavors to ARM.  Canonical ported the "guts" because there might have been some promise of revenue in that.  The developers of the flavors likely have little more time to give.

Rather than volunteering others' time to do something of interest to you, why not volunteer your own time to make it happen?  If you are unable to produce the source, then you might enlist the help of someone else who is interested.  But don't say what others should and should not be able to do.  Outside of Canonical, except for the few pennies donated by the kind communities they serve, most of them are not getting paid for their work in any other fashion than the satisfaction they earn.

Looking at tsimonq2's wiki page, I don't think we can say that he is a "paid developer".  All of his memberships are in volunteer groups.

---

### Post by lucbertz on 2018-07-24
I've found this TV box sold at about 50 $ on the web: "GeekBox Open Source Cross TV BOX with MXMIII Android 5.1& Ubuntu Dual Boot 4K RK3368 Octa Core 2GB/16GB 802.11AC WIFI 1000M LAN BT4.1 HDMI2.0 OTG".
It is a cheap TV Box with an already installed lubuntu in dual boot with Android ([www.geekbox.tv](www.geekbox.tv)).
Anyway I didn't buy and tried it.

Instead of develop a dedicated version of lubuntu (eventually someone already did it), I guess if there is a list of Android TV box compatible with Ubuntu ARM. LXDE desktop could be installed on top of Ubuntu.

---

### Post by Pierre16 on 2018-07-26
> **QIII said:**
> Ubuntu is not a commercial venture.  It is an operating system distributed by a commercial venture known as Canonical, Ltd.  Canonical makes no revenue directly from Ubuntu, but from service/support contracts.  They are not likely to find it worth their while to expend a great deal of resources in creating something that will have such a small population of users -- none of whom would likely buy a support contract...

Rather than volunteering others' time to do something of interest to you, why not volunteer your own time to make it happen?  If you are unable to produce the source, then you might enlist the help of someone else who is interested.  But don't say what others should and should not be able to do.  Outside of Canonical, except for the few pennies donated by the kind communities they serve, most of them are not getting paid for their work in any other fashion than the satisfaction they earn.

I did not asked to be preached to, especially from someone who brings nothing to the debate.  Read all other responses... they all bring something useful.  The first part is 100% speculation.  You do not speak for Ubuntu or Canonical.  Let them make their own decision.  BTW, I am involved in volunteer work related to Ubuntu/Lubuntu.

---

### Post by QIII on 2018-07-26
Yes.  Let them make their own decision.  You should contact them.

There was no preaching.  I was only pointing out some conditions that you seem not to understand and I made a suggestion for a course of action.

---

