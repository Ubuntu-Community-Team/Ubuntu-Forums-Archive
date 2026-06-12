---
title: "The drawback of Open Source / Ubuntu / Linux / whatever you like to call it"
date: 2008-11-02
forum: Testimonials &amp; Experiences
---

### Post by Yasero on 2008-11-02
hello everybody,

first of all I would like to say that I am really really happy with Linux, as a Desktop and as a Server. If I had a choice I would never use the windows that was pre-installed on my Laptop.

And Ubuntu has been really great at providing a good way to get Linux fast and easy. This update also went really well, I even didn't had to spend hours reinstalling fglrx, it worked out of the box.

And when you see how great using Open Source and Linux can be, it really pisses you off when something goes wrong. In this case it is not really a major problem, but it is very unnecessary.

In Ubuntu 8.04 my webcam was working great with gspca and almost out of the box. I only had to blacklist the zc0301 driver because this driver only provides v4l2 and was blocking gspca from providing v4l, which I required.

So "blacklist zc0301" and "modprobe gspca", plug in webcam, turn on skype and speak to my family that currently lives about 2500 miles away (not exaggerating)

Everything worked out, I was happy because I bought the webcam without any prior research.

Then I read that in Kernel 2.6.27 there is going to be better webcam support, because gspca is going to be integrated into the Kernel. I didn't care much, but was happy for others who might not have to blacklist any other drivers to use their webcam.

After updating to 8.10, I run skype and realize that webcam was not working. I made sure that zc0301 was not loaded, but the webcam didn't want to work. It was weird. Wasn't this release supposed to make installing webcams easier?

I did some research and realized that there are many many many other users having the same trouble, PRIOR to the release of 8.10. And there seems to be no solution. You can't compile gspca yourself (wouldn't make sense anyway) and using libv4l didn't help me. And, btw, other distributions are having the same problem.

So I am sitting here, realizing that a new version of the system is worse at supporting my hardware that is has promised to support better.

:confused:

Why does this happen? I bet it is some small mistake that has been done somewhere, that for a professional could be solved comparatively quickly. (he/she doesn't need to develop a driver, it was already working, just fix it, some way) but nothing has been done.

There should be someone in charge of that thing at ubuntu or debian or gspca or the kernel, or whatever. But because nobody is really in charge(copyleft and stuff) noones feels obliged to solve the problem, or noone feels obliged the problem because they didn't cause it.

Ubuntu didn't cause the problem, other distributions are having it too.
The kernel people would most probably talk to the developers of gspca, who would say that the driver has been working before, the distributions did something wrong


I am really pissed off, but not to the point that I would stop using open source and stuff, it is just some experience and criticism on my behalf. I think open source is great, I even got this amazing gnome theme and now it looks better than VISTA, :)



YaserO

btw I remember when people used to ask me if I was using Vista when they saw me using gnome (default theme) before Vista was released.

---

### Post by steveneddy on 2008-11-03
> **Yasero said:**
>  I remember when people used to ask me if I was using Vista when they saw me using gnome (default theme) before Vista was released.

Yeah - that happened to me lots when using Compiz.

We once sat next to a Microsoft kiosk at the mall with my laptop running Gnome and Compiz and I had about 50 Ubuntu CD's. I gave away all of them in two hours and pissed off the guys at the Microsoft booth.

---

### Post by Bios Element on 2008-11-04
Yeah. A 'professional' would NOT have in fact fixed it. Ya know I rather dislike the wording you used for that as it implies (Regardless of if you meant it or not) that those who work on Ubuntu are idiots...And yet they work hard and long for personal reasons, as opposed to a "professional" Who works for...what? Money. Often the only reason they do. New releases and patches can hardly be expected to test every single webcam out there, particularly since it's such an *cough* Important *cough* Feature. No doubt it's all great and wonderful but it's hardly the end of the world if it doesn't work.

So to sum it up, It's a bug. No need to flame the Open-Source community which does their best to get things working with thousands of different kinds of hardware configurations. Find a bug report an add your commentary or make one of your own and it should eventually be fixed.

---

### Post by armandh on 2008-11-04
welcome early adopter, to the wider world of post release testing.

---

### Post by Yasero on 2008-11-04
> **Bios Element said:**
> Yeah. A 'professional' would NOT have in fact fixed it. Ya know I rather dislike the wording you used for that as it implies (Regardless of if you meant it or not) that those who work on Ubuntu are idiots...
This was never my intention, sorry if the wording was all bad and stuff, but I was really angry :)

I don't blame Ubuntu at all. Actually the bug, I think, originated from the Kernel itself, because there was a major change regarding the gspca driver. If you google the following "2.6.27 webcam" you will see that webpages are praising the Kernel for having better webcam support.

If you have a drastic change regarding a driver, and advertise it as something positive, than you should put intensive testing into it. Especially because it seems to affect a big part, if not all the gspca driver and not only my webcam. And anyway I don't care about the webcam itself, but about the whole principle.

> **Bios Element said:**
> So to sum it up, It's a bug. No need to flame the Open-Source community which does their best to get things working with thousands of different kinds of hardware configurations. Find a bug report an add your commentary or make one of your own and it should eventually be fixed.
[https://bugs.launchpad.net/ubuntu/+bug/293259](https://bugs.launchpad.net/ubuntu/+bug/293259)
I even put a lot of effort into writing it. :)

My intention was never to flame over the Open Source community, I was just trying to express some thoughts. I seriously love Open Source and I think it is a great thing.



> **steveneddy said:**
> Yeah - that happened to me lots when using Compiz.

We once sat next to a Microsoft kiosk at the mall with my laptop running Gnome and Compiz and I had about 50 Ubuntu CD's. I gave away all of them in two hours and pissed off the guys at the Microsoft booth.

When I first Installed Compiz and took my laptop to school, a girl was starring at my screen during the whole class. She told me that she wasn't able to understand whats going on, or how this whole thing works. Seriously: She was trying to catch the wobbling windows. :D

---

