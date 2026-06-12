---
title: "Ubuntu meets the challenge"
date: 2008-07-01
forum: Testimonials &amp; Experiences
---

### Post by freebeer on 2008-07-01
**The challenge:** Install Ubuntu on an old Celeron 700mhz machine, connect to a "distant" wifi access point, AND be a usable desktop machine for my 74 year old father who has little computer experience.

**Executive Summary:**  It works.  :D


**Details:**

The machine is an old, unused Celeron 700mhz frankenclone with 256 megs of RAM and on-board Nvidia (32 meg max, shared memory).

Initial install went fine.  Recognized the video card and USB wifi dongle, however it was really slow.  I happened to have another 256 Meg stick available of the right type, and I put that in.  Examining things in htop indicated that RAM really wasn't the problem... it pointed at video and possibly processor speed being the culprit.  (Gnome, X, etc, were taking a lot of cpu cycles) so I went with a lighter desktop environment.  I have little experience with anything but Gnome, so setting up an alternative was new to me.  Setting up Xfce was simple and straight-forward thanks to an abundance of HOWTOs here and elsewhere.

Xfce made a huge difference in the machine's usability.  No longer did it (seem) to take forever for an app to launch.  The machine is far from snappy, but it is usable to me, and more importantly, quite usable for my father.

The next challenge was the wifi connection.  My father lives next door to me, but we're about 75 meters apart (~75 yards k? :D) Since I did a little bit of homework before I selected the wifi dongle unit, I was confident, but not sure, that Ubuntu would recognize it.  Thankfully it did, so I didn't need to delve into the world of ndiswrapper, etc.  However, I did run into the dreaded "doesn't connect all the time, doesn't remember the password" issue many others have run into.  I wasn't entirely sure this was my problem, since he's ~75 meters from my wifi router and the router folks won't guarantee reception (for valid reasons) at that range.  I ran across a thread here about [wicd ]("http://wicd.sourceforge.net/")and thought I'd give it a try.  Following the instructions, that went better than expected.  The machine gets a steady 56mb connection with a signal strength of 65% minimum AND it remembers the password to the router.  Every time the machine boots up I can get a clear connection without user input.  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG] This is particularly important in this instance, since my father, being relatively new to computers, had to manually make the connection previously, and with two passwords to type in through the default network manager, he was likely to make mistakes. (He's a hunt 'n peck typist, so typos are the norm for him.)
[B]
Ubuntu ready for the desktop?[/B]:  I'd say yes, in this case.  My father wants to get emails, visit some websites, pay bills online, etc.  (Of course he knows nothing about maintaining virus and firewalls and frankly those apps would consume whatever cpu cycles he had left, which is one of the deciding factors of deploying Ubuntu in the first place.)  After I set up Thunderbird for his email and showed him how to access it and to use Firefox, he's happily surfing the net.  Doing exactly what he wants to do.

I still have to do a little tweaking of his desktop environment.  I have a hard enough time reading the system fonts as they are now, so I'm sure he has a harder time (he says it's fine, but I'm sure he just doesn't want me to fuss).  Xfce is unfamiliar to me, so I've yet to spend enough time exploring how best to tweak those things.  The good thing is, they **can** be tweaked, so it's just a matter of time and I'll have it fully configured.

Thanks to the Ubuntu community and the whole FOSS movement, an old machine was rescued from the landfills and an old foggie is cruisin' the 'net.  :D

---

### Post by wolfen69 on 2008-07-02
nice read. isnt it great? ive rescued a few older computers with linux.

---

### Post by hyper_ch on 2008-07-02
good work :)

---

### Post by stalkingwolf on 2008-07-02
You can increase the text size in FF fairly easily.
go to View > text size > increase.

---

### Post by ukripper on 2008-07-02
Nice one! i also love resurrecting old machines and use damn small linux, puppy or fluxbuntu!:)

---

### Post by Martje_001 on 2008-07-02
Nicely done!

---

### Post by freebeer on 2008-07-02
> **ukripper said:**
> Nice one! i also love resurrecting old machines and use damn small linux, puppy or fluxbuntu!:)

I tried DSL (or was it puppy?) on an old compaq laptop.  The liveCD seemed to like the machine ok, but I couldn't get it to respond to the touchpad or an external mouse and so my attempts at testing or installing was thwarted.  Googling showed that it was a relatively common problem, but none of the solutions that they suggested worked.  I didn't spend much time with it though... I'm sure something would have worked eventually, but I just didn't have the time to futz with it.

---

### Post by freebeer on 2008-08-24
Just an update.  After several months, my father has had **zero** issues with the system.  It just plain works for him.  No technical support has been required on my part.

(He has ask the occassional software-type question, such as "how do I forward an email, or what's the difference between a forward and a re-direct" but those aren't technical support imo and totally unrelated to the underlying OS/machine.)

---

### Post by Crafty Kisses on 2008-08-25
Nice read, that's awesome!

---

### Post by Vishal Agarwal on 2008-08-25
Nice Work

---

