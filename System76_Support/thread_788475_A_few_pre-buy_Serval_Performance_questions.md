---
title: "A few pre-buy Serval Performance questions"
date: 2008-05-09
forum: System76 Support
---

### Post by pitseleh on 2008-05-09
I'm days away from ordering the Serval Performance, but I had a few pre-buy questions, none of which are deal breakers, I just don't want too many surprises. I read that this notebook was based on the Sagers NP2090/NP2092 notebooks, so I was curious if the Quick Charge and Power USB buttons supplied on the NP2090's worked on the Serval. Also, is the LCD screen matte or glossy? And finally, I was curious of the general heat and noise output on the Serval. I know it's a matter of opinion, but any idea of how much would be helpful.

Thanks in advance!

---

### Post by glacialfury on 2008-05-10
I just received my Serval about a week ago.  I can't speak to the model build, but as for the rest - 

It's very quiet, and it runs fairly cool.  You *can* notice where the graphics card is if you doing something intensive (games, rendering etc) - it's right in the spot where your left palm rests.  So you'll have one warm hand and one chilly hand while gaming ;-)

The screen, despite the post in the archives addressing the same question, is glossy.

---

### Post by thomasaaron on 2008-05-12
The screen was matte. Now it is glossy again. And (weirdly) I was just told that it could change back to matte again with no notice. ](*,)](*,)](*,)

Specifically, it is a...
15.4" WSXGA+ (1680x1050) Widescreen (glare type) Enhanced Screen Active Matrix TFT

As for the quick-charge button, I'm not sure. I'll have to test on that. The power USB button does work, though.

---

### Post by rscottfree on 2008-05-25
I'm looking at getting one of the Serval Performances right now, too. The only thing I really really want is suspend/resume from ram to work as near to perfect as possible. I hate waiting for things to boot....

Also, about the matte now glossy monitor: honestly, I'm a matte all the way. Glossy is for people who never turn their lights on, and I like the lights on, so yeah. Is there a way to request a matte monitor? Or should I just wait until it changes again?

OK, I lied, I really really want another thing: apple bluetooth keyboard support. I have an apple wireless (bluetooth) keyboard that I currently use for the Nokia N810. It's beautiful, small, and great for typing lots, which I occasionally do. Imagine that. I'm definitely getting the Serval with the bluetooth, but I would like to know if it supports bluetooth keyboards. I know the apple keyboard uses a fairly standard bluetooth api or what-have-you, and it works on the n810 which is linux-based. 

Anyway, if I could get those two things (or three): suspend, matte, and apple bluetooth keyboard support, that would be fantastic. If not, I might just have to bite the bullet anyway, because I've looked around and System76 can't be beat.

---

### Post by compholio on 2008-05-25
> **thomasaaron said:**
> 
As for the quick-charge button, I'm not sure. I'll have to test on that. The power USB button does work, though.

What exactly are these buttons supposed to do?  I have the SERP3 and they do not <appear> to do anything, but I would need to know their true function in order to accurately test them.

---

### Post by thomasaaron on 2008-05-26
The USB button would allow you to leave a device that charges up via a USB connection in your laptop while the computer is off and plugged in.

I don't think those ever worked on the SerP3. This thread was about the SerP4, which is a completely different MB.

---

### Post by farruinn on 2008-05-27
> **rscottfree said:**
> The only thing I really really want is suspend/resume from ram to work as near to perfect as possible. I hate waiting for things to boot....

Suspend and hibernate work fine, but it seems to me that resuming from hibernate doesn't save a whole lot of time. I guess it would be useful for leaving a session open and restoring it if you need to unplug the laptop for an extended period, but I normally leave the laptop plugged in and just suspend.

---

### Post by hashbaz12 on 2008-05-27
Do the webcam and the fingerprint reader work? Also, if you install a different distro (like Ubuntu Ultimate) does all of the hardware still work or can you only run it with the pre-installed settings? Is the hardware supported only by system 76 or is it made up of components that are supported throughout the linux community? I am very interested in this laptop, but I don't want to buy it and then curse System 76 for the rest of my life.

---

### Post by thomasaaron on 2008-05-28
The web cam does work (with programs that support the v4l2 protocol: Ekiga Softphone, Cheese, Skype, etc...).

The fingerprint reader is not yet supported under Linux.

We only test with and support Ubuntu (Gnome). Our System76 driver, which patches holes in vanilla Ubuntu will run on Kubuntu and Xubuntu, however, we do no testing with those variants and can't guarantee full functionality. That said, a good number of our customers are running Kubuntu successfully.

As for other linux distros, we do not test with them, so we cannot guarantee full functionality with them. We do provide our customers with whatever info we can to help get their computers running under other distros.

---

### Post by rickdog on 2008-06-17
I am also considering purchasing a Serval Performance and I have a couple more questions:

Is there work being done on getting support for the fingerprint reader?

Can I order it with Kubuntu installed or must I install it myself (it's not a problem, I'd just like to know)?

Is the card reader compatible with my Type II Sprint broadband card?

Thanks

---

### Post by thomasaaron on 2008-06-17
> Is there work being done on getting support for the fingerprint reader?

Yes. We are working on it. It is pretty difficult, though, to get it working right --and-- get it integrated into gnome. Not sure when that functionality will be available.

> Can I order it with Kubuntu installed or must I install it myself (it's not a problem, I'd just like to know)?

You would have to do that yourself. We do not install or support Kubuntu. That said, our System76 driver does run under Kubuntu. Additional support is available from other Kubuntu users on the forums.

> Is the card reader compatible with my Type II Sprint broadband card?

If your sprint card is an *express* card, it will fit in the computer. If it is a pcmcia card, it will not. As for functionality, you will need to google: "Hardy + <model# of the card>" to see if anyone has had any success with your particular card.

---

### Post by rickdog on 2008-06-17
Thanks for answering those questions. Now for a few more...

Does the S-Video port work?

What is the "System76" driver? I didn't see anything in the repos.

Now that Sager has a $300 off sale on the NP2092, would I just be able to do a clean install of Kubuntu and apply the "driver"? I really would like to support System 76, but that's $300 we're talking about!

Anyway, thanks again for the help

Rick

---

### Post by thomasaaron on 2008-06-18
> Does the S-Video port work?
No, but the vga out port works.

> What is the "System76" driver? I didn't see anything in the repos.
It's a python program that applies model-specific patches to our computers.

---

### Post by thinman1189 on 2008-06-24
I'm also thinking about getting a Serval Performance.

Is it possible (or at least not extremely difficult) to install XP on it? My university triple boots XP, Fedora and Ubuntu but I'm not entirely sure if there are any OS specific apps I'd need to be using. I'm well aware of Linux alternatives to Windows specific apps but I just want to be perfectly clear what my options are before I make the purchase. 

Are there any known battery upgrades available (third party is fine)?

---

### Post by thomasaaron on 2008-06-25
> Is it possible (or at least not extremely difficult) to install XP on it? 

Yes. It comes with a Vista drivers disk. XP drivers can be downloaded from online.

> Are there any known battery upgrades available (third party is fine)? 

Probably, but we don't really track that. We sell extras from our website.

---

### Post by thinman1189 on 2008-06-26
> **thomasaaron said:**
> Yes. It comes with a Vista drivers disk. XP drivers can be downloaded from online.



Probably, but we don't really track that. We sell extras from our website.

Sounds good to me, thanks!

---

### Post by kbuel on 2008-06-27
If I need to format, where can I obtain the system76 driver?  (is it on a cd that comes with the computer, or can I download it off of the System76 website)

---

### Post by doorknob60 on 2008-06-28
System 76 Drive: [http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver) There's a download link at the bottom. Also for Kubuntu you wouldn't need to clean install, a simple command in the terminal would do the trick:
```
sudo aptitude install kubuntu-desktop
```

---

