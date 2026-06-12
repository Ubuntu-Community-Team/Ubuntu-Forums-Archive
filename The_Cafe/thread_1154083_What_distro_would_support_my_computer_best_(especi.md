---
title: "What distro would support my computer best (especially my graphics card)?"
date: 2009-05-09
forum: The Cafe
---

### Post by gymophett on 2009-05-09
This is my computer: [http://www.bestbuy.com/site/olspage.jsp?skuId=9163772&type=product&id=1218040476935](http://www.bestbuy.com/site/olspage.jsp?skuId=9163772&type=product&id=1218040476935)

I need a distro that will support it best because in Ubuntu my ATI isn't supported with Compiz. I want something Debian based or RPM based. Something not very buggy and well tested. The main ones I have in mind are Debian, Mandriva, Fedora, and Crunchbang.

Which would work best?
Thanks for all of your help! :D

P.S. I'm dual-booting with Vista.

---

### Post by stwschool on 2009-05-09
Your problem is based on the newer Xorg and ATI's drivers, as previously mentioned. Therefore that rules out any linux using the latest Xorg (such as the latest Fedora and possibly even Debian Lenny). I'd suggest Ubuntu 8.10 as it's stable, will have suitable drivers for your hardware, and will install the proprietary drivers much more easily than most other distributions.

---

### Post by gymophett on 2009-05-09
> **stwschool said:**
> Your problem is based on the newer Xorg and ATI's drivers, as previously mentioned. Therefore that rules out any linux using the latest Xorg (such as the latest Fedora and possibly even Debian Lenny). I'd suggest Ubuntu 8.10 as it's stable, will have suitable drivers for your hardware, and will install the proprietary drivers much more easily than most other distributions.

But I kinda wanna distro hop. :)

---

### Post by sgosnell on 2009-05-09
Toshibas are problematic at best.  Probably any distro a couple of versions older than current would work well enough, but Google "Toshiba Satellite Linux" or some such term and see what you find.  The Ubuntu wiki has info on this, I think, and so do the other distro forums/wikis.  Every distro has support forums, and you may want to browse a few.  You don't have to install them all at once, and they're free, so take your time and learn as you go.

---

### Post by Glucklich on 2009-05-09
> **gymophett said:**
> But I kinda wanna distro hop. :)

Then distro hop. He just gave you a heads up, but you can still do it if you want to. Personally, I agree with him. Stay in 8.10 and download the drivers from the ATI site. I would go even further and get one of the LTS versions that are still supported, since 8.10 was dropped with the arrival of 9.04. I think the latest LTS was 8.04. And on a Toshiba laptop, I would advise Xubuntu (or something even more lightweight, if you are linux proficient). Let's just say that my last laptop was a Toshiba and I'm not very happy about how long he lasted. When I changed to a lightweight, I think it was already too late. And the worse part, it was already out of warranty. Simply that, if you see him over-heating and consequently over-ventilating on Linux... DON'T! Stop what you are doing or get back on Windows and do it.

---

### Post by stwschool on 2009-05-09
8.04 is the last LTS, correct. You can still have the latest features by using launchpad (and possibly the backports repository though that might be a bad idea if it updates xorg, I can't tell you if it does because I've not tested that myself) so for instance you could get the network manager applet (a big feature of the jump from 8.04 to 8.10) in 8.04 this way.

And Glucklich is right about Xubuntu, actually 8.04 is really nice, I just recently installed it on an old pc and it's very pleasant, though I would suggest that you then add LXDE on top if your machine's a bit lacking in power. You might still need to use XFCE for some jobs, but LXDE should be fine for most, and while not that attractive it's amazingly fast and lightweight and is very user-friendly (especially for those with a Windows background).

---

### Post by stwschool on 2009-05-09
I've found that a cooling pad can help with overheating. I didn't really expect any effect but using one drops my old Dell about 15 celsius which is a big improvement, if I have it on my lap my legs catch fire!

---

### Post by gymophett on 2009-05-09
> **stwschool said:**
> I've found that a cooling pad can help with overheating. I didn't really expect any effect but using one drops my old Dell about 15 celsius which is a big improvement, if I have it on my lap my legs catch fire!

I will go with Ubuntu 8.04 and update everything else through launchpad and I WILL need help. I will keep this forum going. :D

Also, I won't always have to use 8.04 will I?
The drivers will eventually be supported right?

---

### Post by stwschool on 2009-05-09
8.04 and upgrade the key apps yep. Openoffice is there, I think Gnome is on there, gnome-do, all the other good stuff. Regarding the ATI drivers, it depends on whether ATI have a change of heart but they have basically written off their older cards, which means you're kinda stuck at distros that don't use the present Xorg. I'm in the same situation with my laptop, though my desktop is ok as it's Nvidia. Honestly though 8.04 is supported til 2011 so it'll keep you going and being about as productive as an old machine can do, and by 2011 you'll probably want a newer machine anyway right?

---

### Post by Glucklich on 2009-05-09
As a previous Xubuntu user, I never understood why people think it's not attractive. It's not harder to configure than regular Ubuntu and less filled with crap, pragmatically speaking. It doesn't have eye candy but it's not supposed to! That's why it is so good. But yeah... just another of my completely off-topic rants.

About the cooling pad... never tested it. But Ubuntu on my Toshiba was getting 80º Celsius and up, with Xubuntu dropped to 40º. Half! Basically, the temperature my Acer is now running regular Ubuntu. Running Xubuntu really made the difference. Too bad I found it as a "last-resort" at the time, with the damage already done. But at least, Xubuntu gave him 6 more months to live before going for good. I would like to be using it right now, but my sound control doesn't work there since Acer chose the two buttons instead of the wheel.

---

### Post by gymophett on 2009-05-09
> **stwschool said:**
> 8.04 and upgrade the key apps yep. Openoffice is there, I think Gnome is on there, gnome-do, all the other good stuff. Regarding the ATI drivers, it depends on whether ATI have a change of heart but they have basically written off their older cards, which means you're kinda stuck at distros that don't use the present Xorg. I'm in the same situation with my laptop, though my desktop is ok as it's Nvidia. Honestly though 8.04 is supported til 2011 so it'll keep you going and being about as productive as an old machine can do, and by 2011 you'll probably want a newer machine anyway right?

Maybe, maybe not. This card isn't old! I just bought this. It's brand new. I'll keep it a good 4 years.

---

### Post by gymophett on 2009-05-09
Maybe I'll put openbox on 8.04 because 9.04 is buggy on this Toshiba.
It doesn't have effects, but it's nice and fast isn't it?

---

### Post by stwschool on 2009-05-09
Xubuntu 8.04 is very pleasing to the eye (just installed it on an older box as it needed something stable and not too bloated, and I wanted the Ubuntu ease-of-use-and-maintenance), though I remember finding 8.10 a bit ugly. Maybe my tastes changed over time.

---

### Post by stwschool on 2009-05-09
Openbox is fast but a bit sparse. You might want to try OpenBox as the window manager for Gnome (though for the life of me I can't get the thing to work) or use LXDE or as another alternative, try this out (you'll love it, the speed of a window manager but you get to keep Gnome).

I can't remember if it's in the default repositories or not but have a look for E16 window manager (if not look for the enlightenment website and see if they have more info). You can run E16 as the window manager while gnome handles your desktop environment. It gives you super-fast loveliness and you still get Gnome (which I love).

Your other lightweight but user-friendly option is LXDE which I think I mentioned earlier.

---

### Post by sgosnell on 2009-05-09
If you want OpenBox, why not just install Crunchbang?  It's Ubuntu with OpenBox.

---

### Post by LightB on 2009-05-09
Maybe PclinuxOS, it has some nice laptop configurations and installable proprietary drivers in repos. Not the latest software overall, though, but sometimes that's a good thing. That graphics hardware actually runs fairly well with the proprietary driver, but only 3d, the 2d I think sucks.

---

