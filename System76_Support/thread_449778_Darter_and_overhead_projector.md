---
title: "Darter and overhead projector"
date: 2007-05-20
forum: System76 Support
---

### Post by perce on 2007-05-20
Hello,

I've tested today my new Darter with an overhead projector.  The combination Fn-F8 doesn't seem to switch from the LCD and he projector. Not a big deal: they work simultaneously. The problem is that the projector displays only part of the screen: it cuts half of the two panels on top and bottom, 
and something on the sides. Also, the image in he projector is a bit distorted. I imagine the reason is that the projectors makes a more or less square image, while the LCD is rectangular.  I've tried to change the resolution to 1024x768, but the image got worse. Do you know how can I fix this? I'm going to use the computer a lot for giving presentations.

---

### Post by thomasaaron on 2007-05-21
I've never used my Darter with an overhead projector, per se. I have used it with a Dell Projector (like this: [http://www.dell.com/content/products/compare.aspx/projectors?c=us&cs=555&l=en&s=biz](http://www.dell.com/content/products/compare.aspx/projectors?c=us&cs=555&l=en&s=biz)) But those can easily cost $2500.
These projectors have internal settings for fine-tuning the display but seem to work out-of-the-box with my Darter.

The only work-around that comes to mind is for you to create your presentation to only use a portion of the screen. It would take some trial and error to fine tune it, but I don't know of a way to create a square display on the Darter.

---

### Post by perce on 2007-05-21
> **thomasaaron said:**
> I've never used my Darter with an overhead projector, per se. I have used it with a Dell Projector  

You mean, you bring your projector around if you give presentations? no way...

> 
The only work-around that comes to mind is for you to create your presentation to only use a portion of the screen. It would take some trial and error to fine tune it, but I don't know of a way to create a square display on the Darter.

I have in mind a second one: to configure a second , external square monitor and use it for the presentations. But I have no idea how to do it.

---

### Post by thomasaaron on 2007-05-21
> You mean, you bring your projector around if you give presentations? no way...
What do you mean? It's a lot less bulky than an overhead projector! (But, truth be told, it belongs to the facility at which I give presentations.)
> 

I have in mind a second one: to configure a second , external square monitor and use it for the presentations. But I have no idea how to do it.
Hark! A citizen in need of help!
[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by perce on 2007-05-21
After four hours of hard work the solution has arrived, and it was easier than I expected. First, at the boot time I pressed twice Fn-F8 to switch to the external monitor and turn off the LCD. This put me on he external monitor (projector in my case) but with the wrong resolution. In the Gnome menu to change the resolution I had 1280x800 (the wrong one) as the unique choice. Then I ran the command 

sudo  dpkg-reconfigure -phigh xserver-xorg

and picked 1280x800 and 1024x760. hen in the Gnome menu 1024x768 appeared magically, so that I can chose. If you reboot without choosing the external monitor, you'll notice that the resolution on your LCD is screwed up. Don't worry, you simply have to open the resolution menu and choose back 1200x800, and he screen is normal again.  

It would be nice to be able to switch between the LCD and the external screen "on the fly". I've read in the forum that there is a package called
i810-switch which should do that, do you know if and how it works?

---

### Post by steveneddy on 2007-05-25
@perce - is there something wrong with your "t" button?

---

### Post by perce on 2007-05-25
> **steveneddy said:**
> @perce - is there something wrong with your "t" button?

My keyboard isn't very responsive. I think it's a design problem of the case. In my review of the Darter I put as the disappointment number 1.

---

### Post by steveneddy on 2007-05-26
> **perce said:**
> My keyboard isn't very responsive. I think it's a design problem of the case. In my review of the Darter I put as the disappointment number 1.

So, this post is from a System76 Darter laptop PC?

I wonder if there is a fix or repair to this problem. Sometimes I notice a small glitch on my Serval Performance keyboard, where the shift key is slightly unresponsive, also.

Thanks for the quick reply.

-SE

---

### Post by perce on 2007-05-26
> **steveneddy said:**
> So, this post is from a System76 Darter laptop PC?



yes it is

> 
I wonder if there is a fix or repair to this problem. 


getting used to it. I already make many less typing mistakes than one week ago.

---

### Post by perce on 2007-05-31
After the reinstall I'm no longer able to make the overhead projector work in the easy way: if I give the command

sudo dpkg-reconfigure -phigh xserver-xorg

instead of having to choose only the resolution, it makes me chose the driver of the graphic card too. From lsmod I guess the driver of the graphic card should be i915, but the closest option dpkg-reconfigure gives me is i810, and the default option is vesa. Please help me, because I'll give a talk on Tuesday.

---

### Post by thomasaaron on 2007-05-31
You should choose i810.

---

### Post by perce on 2007-05-31
Thank you Tom, however if I change the resolution with dpkg-reconfigure I loose beryl (even if I chose the driver i810) without been able to choose 1024x768. It is strange that it behaves so differently now, than it did with your installation, because I restored the system using the system76 drivers. The strangest thing is that when I'm using the LCD gnome allows me to choose between 1280x800 and 1024x768, however, when I use the projector  after pressing Fn-F8 at boot time, 1280x800 is the only resolution available. I have checked the xorg.conf file, and for the little I understand, a lot of possible resolutions are listed, but gnome picks only a vary tiny subset of them as options in the change resolution menu.

Now I'm stuck, because the thread Tom suggested to me some posts above essentially says I should add the resolutions by hands to xorg.conf.

---

### Post by thomasaaron on 2007-05-31
When you run dpkg-reconfigure, are you selecting ALL of the possible resolutions it gives you? If not, you should.  You select them with the space bar and then arrow down to the next resolution and press the space bar again until you've selected all of them.

It will still offer you a subset, but I would expect more than one option.


What do you mean you "loose" beryl?

Best,
Tom

---

### Post by perce on 2007-05-31
It's solved now, thank you Tom. I can't make sense of what I did though, to me it seemed just a random sequence of dpkg-reconfigure -phigh xserver-xorg, both when using the LCD and when using the projector, always telling it the same thing, until it finally understood.

Two side remarks:
1) choosing all resolutions listed didn't work: the external projector stopped working, probably because it choose the wrong one.
2)  Fn-F8 works not only before Linux loads, it actually works until X starts.

---

### Post by perce on 2008-01-31
Hi,

with Gutsy I noticed a strange behaviour with a projector: if I plug it, the hotkey Fn-F8 doesn't work (it was working in Feisty after a driver update). Instead the video output goes both to the LCD and to the projector, and Gnome tries to adapt the size of the desktop to the image of the projector (which is a square) and  shrinks the toolbars accordingly. However this doesn't work completely because, if I send evince full screen, it uses all LCD display, and the image is cut in the projector, 

However if I restart X with the projector plugged in, Fn-F8 works perfectly. The projector I've tested is a portable one.

---

### Post by thomasaaron on 2008-01-31
Yes, that sounds about right. You should get the same results (as restarting X) by booting with the projecter plugged in.

As for evince, I'm not sure if there is a fix for that one.

---

### Post by perce on 2008-01-31
> **thomasaaron said:**
> Yes, that sounds about right. You should get the same results (as restarting X) by booting with the projecter plugged in.

As for evince, I'm not sure if there is a fix for that one.

Is there a way to go back to the behaviour of Feisty after your fix? Having to restart X is somewhat annoying, and it was necessary before.

Thank you.

---

### Post by thomasaaron on 2008-01-31
Other than going back to Feisty? Not that I'm aware of.

---

### Post by perce on 2008-02-09
> **thomasaaron said:**
> Other than going back to Feisty? Not that I'm aware of.

Is this a bug, or it is a "feature" of the new Xorg? I mean, should I report a bug somewhere or this behaviour, although annoying to me, is considered the correct one?

---

### Post by perce on 2008-02-09
> **perce said:**
>  Having to restart X is somewhat annoying, and it was necessary before.


Of course this is a typing mistake: what I wanted to say is that restarting X to make a projector work was NOT necessary with Feisty, after I applied a fix you sent months ago.

---

