---
title: "MythtTV Users: Happy with Ubuntu?"
date: 2005-08-07
forum: The Cafe
---

### Post by tom-ubuntu on 2005-08-07
Hi MythTV Users

I got a Mythtv Box with running still FC2 which I like to update sooner then later. Thinking about using Ubuntu for this purpose. What are your experiences so far? Perhaps compared to other distros? Would you recommend using Ubuntu? If not, what else? What were the issues you had? Every comment is welcome :)

Cheers Joe

---

### Post by tom-ubuntu on 2005-08-08
The number of replies says a lot....  ;-)

---

### Post by dannotdan on 2005-08-08
I've been using MythTV for about 10 months. When I did my initial setup I really wanted it to be with Ubuntu. Ultimately I gave up and used wilsonet.com's FC3 tutorial. 

Ubuntu has lived on my desktop since pre-4.10 and I've never been a big Fedora fan. Now I am also thinking about making the Ubuntu switch for the entertainment center. The two issues I ran into last year were LIRC keymaps and X output on the Hauppauge PVR350. I have since switched to NVIDIA TV-OUT so that just leaves LIRC.

Let me know how the setup goes for you. It will probably be a few weeks before I get to this project but I will be sure to post about my experience.

---

### Post by tom-ubuntu on 2005-08-12
Ok, I am almost finished with my migration from FC2 to Ubuntu. So far, it was quite easy, with a few hurdles:

- forgot to install kernel-headers to compile ivtv (guide didn't mention it)
- Alsa muted my sound output, which took me a while to figure out

Otherwise it is working great. Watching videos and DVD is the most important feature for me; both works fine.

**Todo:**
- MythMusic is installed, but does not show up in MythTV. Any ideas?
- Box reboots on shutdown, very annoying
- Channel definition has to be redone, they are almost not visible. Looks like something changed from ivtv 1.x to 2.x which I am using now.
- Removing service which are not needed (internet superserver: what the heck is this?)

**Could be improved:**
- Offer binary packages of ivtv and lirc (easier for newbies)

Well, all in all I think Ubuntu is a good distro for MythTV, you can do a very light installation. I am interesting how an upgrade to the next version (breezy) works. It was one of the reason why I switched from Fedora to a Debian based installation. Hope it works fine  :)

---

### Post by Footer on 2005-08-23
I installed MythTV on Ubuntu in just a few hours this past weekend.  Still some tweaking to do and need to get it hooked up to the HDTV but all in all, it wasn't a painful experience.  Used a couple of guides I found here on the forums ...

Prior to this, I used Wilson's guide on FC2 and that worked as well.  Was going to do it again but had some issues with my NIC and decided to give Ubuntu a try and WALA! all my hardware was recognized and worked, it's an old PIII box with a Hauppauge PVR250 I found for cheap (<$100 about a year ago).

So far, so good!

---

### Post by icewood on 2005-08-28
Has anyone solved the MythMusic problem? It would be more than great if there is a way to get MythMusic to show up in the MythTV menus.

---

### Post by tom-ubuntu on 2005-09-08
I switched my MythBox to KnoppMyth. Had enough of Ubuntu together with MythTV. There is no real MythTV-Ubuntu community, support is poor, packages are outdated. KnoppMyth is dedicated to MythTV. I never setup a Mythbox that fast! Everything I want was working within hours. As I didn't know Knoppix, biggest problems were related to this. I am quite happy with this now.

Ubuntu is absolutely great for a desktop, but not for a MythTV box IMHO.

---

### Post by Footer on 2005-09-08
Hey joeuser,

I hear you!  I've been living with Myth on Ubuntu for just over two weeks now and I've about had enough as well.  While I had plenty of problems when I was using FC2, at least I was able to get everything working.  I've still got problems using Ubuntu.  Still haven't been able to watch TV.  I keep getting the "Unexpected response to MYTH_PROTO_VERSION:" error message.  From what I can tell, this is because the frontend/backend versions are not the same but they are!  And you're right, there's a very small community of Ubuntu/Myth users out there and it just isn't enough.  There's a forum here now:

[INDENT][http://www.abarbaccia.com/](http://www.abarbaccia.com/)[/INDENT]
but it's just getting going so very little help at this point.

I'm with you, I think I'll switch to KnoppMyth ... Knoppix has always been great with hardware detection and that's important to me since my Myth box is fairly old hardware.

Thanks.

---

### Post by tom-ubuntu on 2005-09-08
I used the forum and the guide from [www.abarbaccia.com](www.abarbaccia.com). But what is the sense of a (small) community board when the packages are not available? 

What I can tell you from the installation with KnoppMyth, you will not regret it switching to it. It is dedicated to MythTV, so if should works fine. What I am still unsure, is how an upgrade to the next version works. I think, just over the iso with the auto-upgrade option. We will see.

---

### Post by Psylon on 2005-09-08
I followed the instructions on this site to get the package installed. Easy...

[https://wiki.ubuntu.com/MythTV?highlight=%28mythtv%29](https://wiki.ubuntu.com/MythTV?highlight=%28mythtv%29)

Configuration took a bit more time. I had to track down how to get my bttv card to work. Wound up with this line in my /etc/modules file:
[I]
bttv card=26 tuner=39[/I]

Tested it with tvtime. Nice little tv application.

Other than that I followed the directions on the mythtv.org site.

I had the basics going in an evening and another evening learning/tweaking.

---

### Post by Footer on 2005-09-09
OK.  I wiped my box and installed KnoppMyth!  BOOM!  Done in about 10 minutes!  The Zap2it stuff took a bit of time but once that was done, I had a working Myth box!  You're right joeuser, very fast and efficient.  I'm still not sure about the Fluxbox window mananger but I guess it really doesn't matter as long as the machine spends most of it's time as a Mythbox.  I like remotely administering with VNC and I did manage to get it installed but going to have to tweak some more to get it working properly.  ssh works right out of the box which is nice.

Bottom line is I think I'll work with KnoppMyth for awhile and see how it goes!

---

