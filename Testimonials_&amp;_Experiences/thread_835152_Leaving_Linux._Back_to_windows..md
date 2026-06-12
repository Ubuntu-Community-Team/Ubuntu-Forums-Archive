---
title: "Leaving Linux. Back to windows."
date: 2008-06-20
forum: Testimonials &amp; Experiences
---

### Post by Hoyland84 on 2008-06-20
After spending endless hours trying to get Linux to work for me, I am sad to say I resign. For whoever cares:

What first trigged me on to Linux was buying a PS3. I started my Linux experience here, hoping to get a better media center out of my PS3. I spent many, many hours trying to set it up right, without fully succeeding. Mostly my problems here was related to screen resolution, using a 720p TV. For now, my linux/ps3 project is put on ice.

Next was setting up a dual boot with Ubuntu 8.04 and WinXP on my laptop. Actually, this has been quite OK. I'm sure i ran in to some troubleshooting, but I can't quite remember now. As my laptop is about 4 years old, worn and torn I figured it was time to do a real upgrade. I got myself a real desktop computer, AMD Athlon 64 X2 6000, 2 gig ram, 1TB HDD and a nice and shiny Samsung 22" widescreen. Nothing special, but still a big upgrade for me. Now I was looking forward to really enjoy using my computer with Ubuntu installed. I didn't even care about making a dual boot with Windows. I soon ran in to trouble, which now have turned in to several long days in front of the screen in frustration.

Ubuntu 8.04 (LiveCD) would simply not install. Hours later i found out I could press F6 and type pci=nomsi on the installation screen. I have no idea what this means and I don't care either. I just want it to work.

Everything then seemed to be going smooth, until I started with the video card (Nvidia GeForce 8200). So many hours I have spent trying to install it's drivers, f****ng it up, reinstalling Ubuntu, configuring display, reinstalling drivers and so on. When I got it to work it would perform quite bad and it wouldn't work again after reboot. I figured i would install Ubuntu 7.10, but to no surprise the installation failed as the screen would go black. I kind of gave up and started to look in other directions. Maybe there was a better Linux distro for me out there?

Reading reviews, checking a lot of web sites led me on to trying openSUSE. I installed v. 10.3 and soon found more problems with my video card. I couldn't run a higher resolution than 800x600. I would update the system, with kernels and whatever, but I could connect to internet either with a hard line or wireless. Surfing the web, trying to solve it, I found out that v. 11 was just released yesterday. So I thought I could give it a try and it turned out to give a much better result than 10.3. Quite easy (still not easy enough though) i managed to run my native resolution 1680x1050. But problems were to follow. No sound and after spending a couple of hours trying to fix it, the sound turned out distorted when it finally came. Wireless doesn't work out of the box either and I haven't even started on the video card.

My life does not evolve around computing. I enjoy surfing the web, playing media, be creative with graphics and even fix a technical problem or two. However, I want things to work. As I now have spent so many hours on troubleshooting in Linux I'm fed up. I know what I get with Windows. I can enjoy spyware, viruses, system crashes and time waiting for things to happen on the screen after I click something. But - things work! Hardware is just no problem. And, Internet Explorer is maybe not so cool, but it's better than Firefox on java, wmp, flash and such (corp. plugins). I am all for open source and the freedom of choice, although I don't let it rule my way of using the computer. Sometimes I use freeware, sometimes open source, sometimes I pay for software, sometimes I even download piracy copies.

Maybe I would have been better off if I had chosen better hardware, more orientated to Linux, but I didn't know this was going to be an issue.

Linux to me is, great when it works, but in my experience it doesn't. At least not easy enough for me to choose it for my computer. I really hoped this would have turned out different, but it didn't. Ubuntu, although much uglier than openSUSE (yes, my personal opinion), was the distro that was most appealing to me. If my video card had worked better in Ubuntu I would probably still be using it. Best of luck to all of you who enjoy using Linux. I'll probably try Ubuntu again in a year or two, when I have to do another format of my slow Windows disk.

---

### Post by Keyper7 on 2008-06-20
I'm sorry about your experience, but I noticed this is your first post here.

Don't you want to give it another shot, but this time asking for help here on each step?

Sometimes you might have had incredibly bad luck and nobody ever posted the solution to your problem on the web, and therefore you can't find it by googling. But posting the error messages and other info around here can give you better hints.

One of the strongest points about Ubuntu is the community. I strongly suggest you not to give up without asking directly for help here first.

PS: Doesn't really matter if you think Ubuntu's default theme is uglier than OpenSUSE's, you can probably install OpenSUSE's theme on Ubuntu with a couple clicks. :)

---

### Post by Hoyland84 on 2008-06-20
Well. Maybe if I spend sometime off the computer I will feel more up for it. Right now I must say I'm quite fed up. With that said I haven't ordered my Vista copy just yet.

All in all it is also about the total impression I get of the system. With Windows I could almost always find out things for myself. Troubleshooting with Windows is not so common. With Linux I often feel I have to turn to forums and googleing. Although this community thing is great it takes quite a lot of time having to search around for solutions for every little thing. But - transitioning to Linux is also a learning curve, as it would have been if I were to use Windows for the first time. I couldn't expect everything to be *that* easy.

As I said the main problem for me is my Nvidia GeForce 8200 video card. I have tried to find help for this in the official nvidia linux forum. People have come up solutions not turning to work out very well. When I did get my video card to kind of work, it would perform quite bad. I wouldn't know quite how to explain it, be it seemed to lag with compiz, firefox and simple apps like gedit.

Maybe I won't leave Linux like I said, but I'm pretty sure I will get a Vista copy and at least make a dual boot. Then I don't have to stress so much with getting Ubuntu (or whatever distro) to work. I could just try out now and then and do the forum/googleing thing when I'm up for it.

---

### Post by 3rdalbum on 2008-06-20
Your only problem was your graphics card?

Do yourself a favour: Reinstall Ubuntu and if your graphics card doesn't work with the latest proprietary Nvidia driver (hint: Use the "Envy" program from the repositories to install the driver), then get some other different card. I've got an 8600, which should give you better performance AND you should be able to get them cheaply as they are on the way out.

Then send an angry e-mail to Nvidia, because there's got to be something wrong with their drivers. Not for the first time, either :-(  AFAIK the 8200 wasn't terribly popular, so Linux-related problems are probably less of a priority for Nvidia's developers.

---

### Post by eye208 on 2008-06-20
> **Hoyland84 said:**
> Hours later i found out I could press F6 and type pci=nomsi on the installation screen. I have no idea what this means and I don't care either. I just want it to work.

Everything then seemed to be going smooth, until I started with the video card (Nvidia GeForce 8200).
PCI Express graphics cards make use of message-signaled interrupts. Disabling these globally with the pci=nomsi parameter may not be such a good idea after all.

There should be a way to boot Linux without that option. Did you file a bug report?

---

### Post by Hoyland84 on 2008-06-20
Oh, ok. No, I did not file a bug report. Maybe I should, to do my little part of the contribution. After all, Ubuntu is free and I should be able to do at least as little as that in return.

Googleing "Ubuntu 8.04 Nvidia" and just quickly looking at the search results tells me that there's many people out there struggling with different nvidia graphic cards on Hardy. That's one of the reasons I wanted to try 7.10. Many people seems unhappy with Hardy, for different reasons. Anyway, as I mentioned, 7.10 didn't work.

---

### Post by eye208 on 2008-06-20
This looks like a mainboard chipset problem. The graphics card issue may be just a side effect. There must be some way to run Linux without pci=nomsi on your computer.

Unlike Intel, AMD CPUs still rely on 3rd party chipsets which may or may not work well with Linux. Can you tell the name of your chipset?

---

### Post by WildOscar on 2008-06-20
Sorry to hear about ur troubles mate. Well since ur going to install Vista on ur desktop, may I suggest a much convinient way for u to install UBUNTU. Since you already have the UBUNTU live CD.

WUBI - google it. Its a UBUNTU installer for Windows. It make it easier with a few trade off course. Ur file system is still NTFS, so u have to defrag once in a while and the Hibernate does not work.

I have found Hardy so far MUCH better for me. My desktop is less than a year old. It took a little while.. the forums became my second home. But got it workin. In a week my UBUNTU box could do everything i normally do with Windows and more.

Do not give up mate. UBUNTU is not WINDOWS, its a different OS so things work differently. A little bit of patience will get u there.WUBI - First, then get back to UBUNTU when u feel ur comfortable.

PS: Any NVIDIA problems can be solved unlike ATI. Stick with NVIDIA if ur commin back mate. :D

---

### Post by Keyper7 on 2008-06-20
> **Hoyland84 said:**
> As I said the main problem for me is my Nvidia GeForce 8200 video card. I have tried to find help for this in the official nvidia linux forum.

The problem with the nVidia forums is that it aggregates users from all Linux distros and therefore it's full of irrelevant info for you as an Ubuntu user. It is a useful forum (it was for me more than one time), but this one should be your first choice when it comes to problems you're having with Ubuntu.

By the way, some people on this thread:

[http://ubuntuforums.org/showthread.php?t=822315&highlight=8200](http://ubuntuforums.org/showthread.php?t=822315&highlight=8200)

seems to be having relative success with a GF8200. Check it out.

Oh, and one more thing:

> **Hoyland84 said:**
> But - transitioning to Linux is also a learning curve, as it would have been if I were to use Windows for the first time. I couldn't expect everything to be that easy.

> **Hoyland84 said:**
> Oh, ok. No, I did not file a bug report. Maybe I should, to do my little part of the contribution. After all, Ubuntu is free and I should be able to do at least as little as that in return.

Kudos to you. Seriously. I wish every user who had a bad experience with Ubuntu was this reasonable.

---

### Post by eldragon on 2008-06-20
> **Keyper7 said:**
> I'm sorry about your experience, but I noticed this is your first post here.

Don't you want to give it another shot, but this time asking for help here on each step?

Sometimes you might have had incredibly bad luck and nobody ever posted the solution to your problem on the web, and therefore you can't find it by googling. But posting the error messages and other info around here can give you better hints.

One of the strongest points about Ubuntu is the community. I strongly suggest you not to give up without asking directly for help here first.

PS: Doesn't really matter if you think Ubuntu's default theme is uglier than OpenSUSE's, you can probably install OpenSUSE's theme on Ubuntu with a couple clicks. :)

exactly what i was going to point out. it doesnt look like the poster gave it much time. otherwise his post count would have been a bit higher.

if i had followed the same route with this notebook, and had given up before asking a question, id be long gone...

anyway, good luck next time..

---

### Post by ukripper on 2008-06-20
> **Hoyland84 said:**
> I can enjoy spyware, viruses, system crashes and time waiting for things to happen on the screen after I click something. But - things work! 

Irony, you call this working but I call this shooting on your own foot!

---

### Post by Hoyland84 on 2008-06-20
> **Keyper7 said:**
> 
By the way, some people on this thread:

[http://ubuntuforums.org/showthread.php?t=822315&highlight=8200](http://ubuntuforums.org/showthread.php?t=822315&highlight=8200)

seems to be having relative success with a GF8200. Check it out.

Thanks for the tip Keyper7, but I have already been down that road. It fixed my problem to the extent it did for the poster of that thread. I can run my right resolution, but with no 3D acceleration. I want to use Compiz and Blender, so I'm going to need that card working properly.

> **3rdalbum said:**
> I've got an 8600, which should give you better performance AND you should be able to get them cheaply as they are on the way out.


I guess I could bite the dust and just get myself a new video card. After all, it is not that expensive. Costs less than a copy of Vista anyway.

> **eye208 said:**
> This looks like a mainboard chipset problem. The graphics card issue may be just a side effect. There must be some way to run Linux without pci=nomsi on your computer.

Unlike Intel, AMD CPUs still rely on 3rd party chipsets which may or may not work well with Linux. Can you tell the name of your chipset?

It's a NVIDIA GeForce 8200 sitting on a Asus M3N78-EMH HDMI motherboard. As I don't know much about hardware and it's terminology, I'm not sure this is what you're asking for. :confused: :)

> **eldragon said:**
> exactly what i was going to point out. it doesnt look like the poster gave it much time. otherwise his post count would have been a bit higher.

if i had followed the same route with this notebook, and had given up before asking a question, id be long gone...

anyway, good luck next time.. Oh, I can assure you I have spent a lot of time(!), searching for answers. I am not the only one out there with the problems that I have been experiencing, and I know how unpopular it is asking the same question over and over again in a web forum. Still, you have a point. I should have registered on this forum first and used it a bit more than fooling around with google.

> **ukripper said:**
> Irony, you call this working but I call this shooting on your own foot!
Yes, I was beeing ironic.

---

### Post by Hoyland84 on 2008-06-20
Ok. Here's an update on my situation, should anyone care. :)

I am at the moment using openSUSE with my Nvidia driver working prefectly. It even works after rebooting, which it didn't do in Ubuntu. It also seems to be performing better than in Ubuntu. I figured I wanted to give it try since I had gone through the trouble of getting SuSE up and running. Had it turned out not working, well, it would have led me back to Ubuntu which maybe would have led me further on to Vista(?).

I do expect I have to reinstall the driver after any kernel update, but I think I can live with that. Those updates doesn't come around to often I hope(?)

It seems like openSuSE as an organization is working more closely with Nvidia than Ubuntu does. Their official documentation at least has quite a lot on Nvidia graphics and they use the Nvidia logo on there as well.
[http://en.opensuse.org/NVIDIA](http://en.opensuse.org/NVIDIA)

Now, I have some other issues with openSuSE, concerning wireless and sound output, but I will not bother you Ubuntu users with that. I hope I will manage to solve those problems. I also hope I can get Synaptics up and running. Synaptics seems a lot better than Yast, which is the default package manger in openSuSE.

So sorry to say, openSUSE seems to be winning this round. I'm still using Linux though with gnome, and that's got to count for something. Right? :)
 
I'll still be checking back to this forum once in a while, now that I got the account. Should anyone have any questions around the driver issue, or whatever, please speak up. I feel like a somewhat experienced n00b now. Hehe

---

### Post by thiebaude on 2008-06-20
Hoyland84, have you tried the Nvidia geoforce 6800 generic drivers to see if they might perhaps work.

---

### Post by Hoyland84 on 2008-06-20
> **thiebaude said:**
> Hoyland84, have you tried the Nvidia geoforce 6800 generic drivers to see if they might perhaps work.

No. That is something I have not yet heard of. Right now I am fiddling with openSuSE and hopefullt that will work out good for me. Should I get fed up with openSuSE as well and get back to Ubuntu, I will certainly give it a try.

---

### Post by shyuep on 2008-06-20
Sorry to hear about your problems.  As a Ubuntu user who ported over from Windows myself, I must say that I empathize with you.  Ubuntu is great for many things (security, stability, etc.) but it is not as easy as Windows, despite whatever some fanatics would want you to believe.  I am still using Ubuntu because I have managed to solve the problems and it is right for my work (I am a researcher who works around Linux servers).  I love its stability and the fact that I have not had a crash on my Ubuntu machine since I installed it two years ago.  But there was a lot of pain.  Wireless did not work out of the box, and yes the community forums are great but for the average user, you shouldn't even have to use community forums to begin with.  I still don't understand why it's so difficult to get drivers to work properly.  Many fanatics will point the finger at Nvidia and ATI, as if that absolves Ubuntu or Linux in general of all responsibility.  My take is that it does NOT.  It is UBuntu's responsiblity as well to make sure that hard ware support is there.  I can't even get my wireless (a fairly common brand) to work out of the box without jumping through the hoops of ndiswrapper installation for chrissakes and wireless is a mature technology.  That said, Ubuntu is as painless as a Linux distro gets.  I tried 4 thus far and the rest were far more painful.

I keep Vista as my main operating system at home.  It is just so much easier to deal with multimedia and other stuff in windows.  Video playback, as far as I can see, is much better in Vista (and I do know how to configure Ubuntu). 

Crux of the matter is: if you can afford the price and just want something that works, get a WinPC or Mac.  If you have the patience to work through the difficulties (costing you manhours) and Ubuntu offers something that you can't get on a PC (like security and stability and unbeatable $ price), stick with it.  As far as I am concerned, you can get a reasonably secure WinPC as well, just that you ahve to pay more to get there (firewalls, anti-viruses, + OS).  So choose your poison.

---

### Post by jimv on 2008-06-20
> **Hoyland84 said:**
> Well. Maybe if I spend sometime off the computer I will feel more up for it. Right now I must say I'm quite fed up. With that said I haven't ordered my Vista copy just yet.

All in all it is also about the total impression I get of the system. With Windows I could almost always find out things for myself. Troubleshooting with Windows is not so common. With Linux I often feel I have to turn to forums and googleing. Although this community thing is great it takes quite a lot of time having to search around for solutions for every little thing. But - transitioning to Linux is also a learning curve, as it would have been if I were to use Windows for the first time. I couldn't expect everything to be *that* easy.

As I said the main problem for me is my Nvidia GeForce 8200 video card. I have tried to find help for this in the official nvidia linux forum. People have come up solutions not turning to work out very well. When I did get my video card to kind of work, it would perform quite bad. I wouldn't know quite how to explain it, be it seemed to lag with compiz, firefox and simple apps like gedit.

Maybe I won't leave Linux like I said, but I'm pretty sure I will get a Vista copy and at least make a dual boot. Then I don't have to stress so much with getting Ubuntu (or whatever distro) to work. I could just try out now and then and do the forum/googleing thing when I'm up for it.

Oh for the love of God, don't get Vista.  I'm using Vista on my  gaming machine and I wish I stayed with XP.  (Could go back to XP, but I'm too lazy to reinstall everything...particularly Steam.)  For some reason just having Vista instead of XP dropped my framerate by about 15-20 fps.

OH, and I use the EnvyNG app to install my Nvidia drivers and it always reinstalls itself after each kernel upgrade.  So may be try EnvyNG next time?

---

### Post by Keyper7 on 2008-06-20
> **Hoyland84 said:**
> So sorry to say, openSUSE seems to be winning this round. I'm still using Linux though with gnome, and that's got to count for something. Right? :)

You should choose whatever suits you better. The beauty of open source is that nothing is being hidden by properties or patents, so it's good when people like you give this kind of feedback, because the Ubuntu devs can talk with the OpenSuSE devs, find out what they do differently and eventually improve Ubuntu.

---

### Post by Darkade on 2008-06-20
where you using the ubuntu 64 edition? that's likely to be the reason for it not to install

---

### Post by eye208 on 2008-06-20
> **Hoyland84 said:**
> It seems like openSuSE as an organization is working more closely with Nvidia than Ubuntu does.
I think it's a matter of release dates. OpenSUSE 11.0 has just been released, so it's more up to date than Ubuntu 8.04. In October the situation will be reversed. There is a way to fix the problem in Ubuntu now (by applying kernel and nvidia driver updates, see [here](http://coyotesg.blogspot.com/2008/06/cracking-ubuntu-804-to-work-with-nvidia.html)) but I would just wait for these fixes to go into the next release and use OpenSUSE in the meantime. It's not that bad. ;)

---

### Post by forger on 2008-06-20
> **Hoyland84 said:**
> With Windows I could almost always find out things for myself. Troubleshooting with Windows is not so common. With Linux I often feel I have to turn to forums and googleing.
I have a niece,a 10-year-old brat that knows how to cd in directories and run games through the terminal... it isn't that hard, it's because you are used to using Windows.

My niece used Ubuntu for 3 months and she got to know the terminal. Imagine what she will be like for 3 years :)
I used Ubuntu for 3 years in a row, and I must say I'm quite happy with what it has become, hardy is by far the best release (so far):KS

Bottom line is you need to get to know it first, give it some time, about 6 months. Our minds and bodies adapt sooner or later, your mind will soon learn to do things instantly, tasks that you thought impossible. And I'm speaking from personal experience!!

All you need is:
a) patience
b) a book about gnu/linux or whatever you might be doing
c) some google searching experience

---

### Post by karellen on 2008-06-21
> **forger said:**
> I have a niece,a 10-year-old brat that knows how to cd in directories and run games through the terminal... it isn't that hard, it's because you are used to using Windows.

My niece used Ubuntu for 3 months and she got to know the terminal. Imagine what she will be like for 3 years :)
I used Ubuntu for 3 years in a row, and I must say I'm quite happy with what it has become, hardy is by far the best release (so far):KS

Bottom line is you need to get to know it first, give it some time, about 6 months. Our minds and bodies adapt sooner or later, your mind will soon learn to do things instantly, tasks that you thought impossible. And I'm speaking from personal experience!!

All you need is:
a) patience
b) a book about gnu/linux or whatever you might be doing
c) some google searching experience

well it's not fair to compare the case of a 10 years old child with an adult. 
children have **a lot of spare time** ;) and **learn **much more easily

---

### Post by ukripper on 2008-06-21
Once you learn how to use ubuntu, things are pretty simple and straight forward and you feel power in your own hands but with Windows you don't really tend to feel that.

---

### Post by ikki_72 on 2008-06-21
> **forger said:**
> I have a niece,a 10-year-old brat that knows how to cd in directories and run games through the terminal... it isn't that hard, it's because you are used to using Windows.

My niece used Ubuntu for 3 months and she got to know the terminal. Imagine what she will be like for 3 years :)
I used Ubuntu for 3 years in a row, and I must say I'm quite happy with what it has become, hardy is by far the best release (so far):KS

Bottom line is you need to get to know it first, give it some time, about 6 months. Our minds and bodies adapt sooner or later, your mind will soon learn to do things instantly, tasks that you thought impossible. And I'm speaking from personal experience!!

All you need is:
a) patience
b) a book about gnu/linux or whatever you might be doing
c) some google searching experience

kudos to your niece. My 12 years old sister only know **su -**, **pon dsl-provider** which i taught her to get online :) but i bet she'll grow with Linux (at home i installed Debian, i'm using Ubuntu only at my rented room)

---

### Post by hyper_ch on 2008-06-21
Enjoy Windows :)

---

### Post by orkinoks on 2008-10-19
Hi,
the next release of ubuntu (8.10) will be available at the end of october.You better try it as you are still facing problems with opensuse (sound etc.)
I have the same chipset, (Asus MSN78 PRO) and waiting for the 8.10.
Good luck.

---

