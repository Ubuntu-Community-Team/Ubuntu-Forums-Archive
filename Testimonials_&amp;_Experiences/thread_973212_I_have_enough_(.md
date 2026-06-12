---
title: "I have enough :("
date: 2008-11-06
forum: Testimonials &amp; Experiences
---

### Post by Magnes on 2008-11-06
I use Ubuntu for many years now and today is the first time when I think about jumping back to Windows. Right now in Ubuntu 8.10 nothing works like it should.

I lost several hours just to configure mouse - because even mouse wheel didn't work. Several hours of googling, editing configuration files and writing in console... Great. 
My second mouse wheel still doesn't work (worked on 8.04) and I think it won't because imwheel shows it as button4, button5 (so it's probably not detected at all).
I don't even know how to begin configuring my tablet, which appears DEAD. It worked like a charm before - even with pressure - on 8.04.

Also I don't see any response to bugs I reported on launchpad. It's like silence over the coffin. Maybe none of my problems will be fixed in this edition?

When mice and tablets will be fully autodetected? In Ubuntu 20.10?

And just booting the system is nightmare... It takes probably over two minutes and I have to wait in the BusyBox (black text screen) until my SATA disc get detected.

At work I use Vista. When I hit the button it takes 10-15 seconds to boot. It's tempting because I'm starting to wonder will Ubuntu ever get better? Or will it just be promises only.

And how can I recommend Ubuntu to anyone who isn't a programmer? I did that. But I won't now. I don't want to feel the shame when the person I recommended Ubuntu will uninstall it with scorn.

On brainstorm.ubuntu.com someone suggested using only linux-friendly hardware. Well, maybe I just should use tablets, because there is no tablet that works out-of-the-box and without complicated editing of text files. And maybe I should have bought some mouse that doesn't have so much buttons. What in hell do I need a wheel for? :(

Stick with 8.04? It's also not a solution. I updated in the first place because I hoped some problems I had will be resolved. Well...

(sorry for my English)

---

### Post by lukjad on 2008-11-06
Well, this distrobution is on a 6 month release cycle. That means that every 6 months whatever they have is sent out there. I suggest that if you are looking for stability you either:

a) Use an LTS.
b) Wait this one out until the problems are fixed upstream.
c) Try a different distro, such as Debian that is known for its simplicity and stability.

In the end, you must make the choice. Do you want the latest and the greatest or the tried and true, steady, releases.

---

### Post by wolfen69 on 2008-11-07
why not stay with 8.04?

---

### Post by Magnes on 2008-11-07
> **wolfen69 said:**
> why not stay with 8.04?

Well, it's to late. I already upgraded. I wanted 8.10 for new GIMP and other new applications. Right know I got some good news at the Ubuntu Brainstorm (that input device configuration will be discussed...) so maybe 9.04 won't be such dissapointment. I'll install 8.04 or wait for the bug fixes and fix some things myself, but I'll leave 8.04 on my parents computer mostly because of the tablet problem (they wouldn't be able to use tablet on 8.10 until I figure out a way to configure it). It's hard to fight with the OS when you have little time.

Thanks for replying.

---

### Post by ronnielsen1 on 2008-11-07
> Well, it's to late. I already upgraded.

> If you have the root and home partitions separated then you can seamlessly move to hardy. Just install hardy 8.04.1 over the current installation and specify the installer to format "/" only. After a few mins you shud be back in hardy - I have done this several times when alpha/beta releases simply fail or lock out. You can specify the same username and the same home partition - no data loss will occur.

[http://tennessee.ubuntuforums.com/showthread.php?t=953036](http://tennessee.ubuntuforums.com/showthread.php?t=953036)

>  I wanted 8.10 for new GIMP
[http://tombuntu.com/index.php/2008/10/13/install-gimp-26-in-ubuntu-804/](http://tombuntu.com/index.php/2008/10/13/install-gimp-26-in-ubuntu-804/)

---

### Post by eentonig on 2008-11-07
Hardware, hardware, hardware.... Don't blame Linux or Ubuntu if your HW doesn't work. I know it's a pain, but it's a pain that is being caused by the manufacturer of the HW you have chosen. If they don't create open drivers, then it's nearly impossible to provide a simple user experience.

---

### Post by eldragon on 2008-11-07
> **eentonig said:**
> Hardware, hardware, hardware.... Don't blame Linux or Ubuntu if your HW doesn't work. I know it's a pain, but it's a pain that is being caused by the manufacturer of the HW you have chosen. If they don't create open drivers, then it's nearly impossible to provide a simple user experience.

you shouldnt blame hardware when it used to work on a previous release.

---

### Post by zipperback on 2008-11-07
> **Magnes said:**
> Well, it's to late. I already upgraded.

Ok. So just backup your important data and reinstall 8.04 which is an LTS release. And then just restore your data.



> **Magnes said:**
> 
 I wanted 8.10 for new GIMP and other new applications. 


Nothing prevents you from installing the updated applications.
If there isn't a .deb package available for the application in question, then simply download the source, and compile it.


> **Magnes said:**
> 
Right know I got some good news at the Ubuntu Brainstorm (that input device configuration will be discussed...) so maybe 9.04 won't be such dissapointment. I'll install 8.04 or wait for the bug fixes and fix some things myself, but I'll leave 8.04 on my parents computer mostly because of the tablet problem (they wouldn't be able to use tablet on 8.10 until I figure out a way to configure it). It's hard to fight with the OS when you have little time.
Thanks for replying.

In your original post for this thread you stated *"I use Ubuntu for many years now"* so if that is the case, I'm sorry to say it, but you should have known better than to just blindly upgrade your system without doing your research first to see if 8.10 was going to meet your needs.

Also in your posts on this thread, you've failed to actually provide any useful information so that we might be able to help you.

What specific hardware are you having problems with exactly? What does the output of lspci and lsusb say about the recognized hardware?

Providing even basic information would be a step in the right direction. But again, as you've stated you have been using Ubuntu for many years, this is really stuff you should already know you needed to provide in order to get any kind of help.

So how about it? Could you please provide us the information about the specific hardware that you are working with? Perhaps we an actually help you.

Thank you.

- zipperback
:popcorn:

---

