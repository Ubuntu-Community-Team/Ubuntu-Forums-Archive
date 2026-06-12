---
title: "Purple static sometimes followed by crash"
date: 2012-06-23
forum: System76 Support
---

### Post by rbuck01 on 2012-06-23
Model Name: Lemur Ultra
Model Number: lemu3
Ubuntu Version: 12.04
Driver Version: 3.0.0

I am a n00b, bear with me.  Attached (if I did so correctly) are a few pictures to illustrate my problem.

It seems to happen a lot when I use Firefox, but that might just be because I use Firefox, a lot.
With an HDMI connection, I use a tv as an external monitor.
I have no idea what information exactly to give, so I'm just throwing out these things.

It is very much like (the same as?) this:
[http://askubuntu.com/questions/136405/screen-goes-purple-on-ubuntu-12-04](http://askubuntu.com/questions/136405/screen-goes-purple-on-ubuntu-12-04)

---

### Post by isantop on 2012-06-25
> **rbuck01 said:**
> Model Name: Lemur Ultra
Model Number: lemu3
Ubuntu Version: 12.04
Driver Version: 3.0.0

I am a n00b, bear with me.  Attached (if I did so correctly) are a few pictures to illustrate my problem.

It seems to happen a lot when I use Firefox, but that might just be because I use Firefox, a lot.
With an HDMI connection, I use a tv as an external monitor.
I have no idea what information exactly to give, so I'm just throwing out these things.

It is very much like (the same as?) this:
[http://askubuntu.com/questions/136405/screen-goes-purple-on-ubuntu-12-04](http://askubuntu.com/questions/136405/screen-goes-purple-on-ubuntu-12-04)

Is your system fully up to date? Maybe try a reboot to ensure that any updated software is running, and not any old ones.

---

### Post by rbuck01 on 2012-06-25
After reading your reply, I used the Update Manager, then rebooted.

Furthermore, I had already done a clean install of Ubuntu 12.04 on the  20th and installed the System76 Driver as the Knowledge76 website says.
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

So far today, my laptop has not crashed, but it usually takes a while  before anything goes wrong.  Almost always, that weird graphic glitch  occurs and progressively gets worse before the computer crashes.   Because I have this warning sign, I usually get the chance to restart  before it crashes.

I tried to ignore this problem for a long time, but it happens almost everyday.
Based on that AskUbuntu link in my first post, I am pretty sure that I am not the only person who has had this problem.

Thanks for any help.

---

### Post by jwh400 on 2012-06-25
This is a hardware issue but I haven't been able to determine exactly what.  I purchased a PanP 8 last October and it's had 12.04, 11.10, and 10.04 versions and all do the same with Unity or Gnome, running Firefox or Chrome. 

I did notice that the harder you run the computer, the sooner it happens.  Having Firefox, Banshee, gThumb, and LibreOffice open at the same time seems to be more than the computer can handle. The purple lines will appear in a matter of minutes, the shell will crash and all open windows will position themselves on one desktop. The computer will then freeze with Ctl+Alt-F2 having no effect and absolutely no CPU activity indicated by the lamp.

Oh, and System76 is aware of this.

---

### Post by rbuck01 on 2012-06-26
> **jwh400 said:**
> This is a hardware issue but I haven't been able to determine exactly what.  I purchased a PanP 8 last October and it's had 12.04, 11.10, and 10.04 versions and all do the same with Unity or Gnome, running Firefox or Chrome. 

I did notice that the harder you run the computer, the sooner it happens.  Having Firefox, Banshee, gThumb, and LibreOffice open at the same time seems to be more than the computer can handle. The purple lines will appear in a matter of minutes, the shell will crash and all open windows will position themselves on one desktop. The computer will then freeze with Ctl+Alt-F2 having no effect and absolutely no CPU activity indicated by the lamp.

Oh, and System76 is aware of this.
Well, that filled me with foreboding.
But thank you for confirming that I'm not alone on this issue.

Do you have any suggestions on what one should do in this situation?

---

### Post by isantop on 2012-06-26
> **rbuck01 said:**
> Well, that filled me with foreboding.
But thank you for confirming that I'm not alone on this issue.

Do you have any suggestions on what one should do in this situation?

We haven't received mass reports of this, so if you're having it (particularly on multiple installations), you should go ahead and contact us through our website to open a repair ticket.

---

### Post by rbuck01 on 2012-08-06
> **jwh400 said:**
> This is a hardware issue but I haven't been able to determine exactly what.  I purchased a PanP 8 last October and it's had 12.04, 11.10, and 10.04 versions and all do the same with Unity or Gnome, running Firefox or Chrome. 

I did notice that the harder you run the computer, the sooner it happens.  Having Firefox, Banshee, gThumb, and LibreOffice open at the same time seems to be more than the computer can handle. The purple lines will appear in a matter of minutes, the shell will crash and all open windows will position themselves on one desktop. The computer will then freeze with Ctl+Alt-F2 having no effect and absolutely no CPU activity indicated by the lamp.

Oh, and System76 is aware of this.

The problem still isn't fixed for me.  Did you ever find out what it was?

Also, I tried a Xubuntu live USB once and didn't see the glitch.  Have you ever tried a non-Ubuntu installation?

---

### Post by isantop on 2012-08-07
> **rbuck01 said:**
> The problem still isn't fixed for me.  Did you ever find out what it was?

Also, I tried a Xubuntu live USB once and didn't see the glitch.  Have you ever tried a non-Ubuntu installation?

This would be a hardware problem. It's not likely that a non-Unity based OS would have any difference with this, except for maybe that Xubuntu won't put as much of a load on the GPU.

---

### Post by rbuck01 on 2012-08-07
> **isantop said:**
> This would be a hardware problem. It's not likely that a non-Unity based OS would have any difference with this, except for maybe that Xubuntu won't put as much of a load on the GPU.
At this point, I really don't know what exactly to do.
I sent my laptop in to be repaired.  I was told that the motherboard was replaced, but the glitch still occurs on Ubuntu.
I suggested that maybe it was the CPU/GPU, but I was told "I think your system would be exhibiting other things if the CPU was at issue."

It's August, which means the fall semester is going to start soon, so sorry if I sound rushed in trying to get this resolved.

Could it at all be related to these?:
[http://askubuntu.com/questions/165009/graphics-not-working-with-intel-i5-3470](http://askubuntu.com/questions/165009/graphics-not-working-with-intel-i5-3470)
[http://askubuntu.com/questions/155458/ubuntu-12-04-randomly-freezes-on-ivy-bridge-intel-hd-graphics-4000](http://askubuntu.com/questions/155458/ubuntu-12-04-randomly-freezes-on-ivy-bridge-intel-hd-graphics-4000)

---

