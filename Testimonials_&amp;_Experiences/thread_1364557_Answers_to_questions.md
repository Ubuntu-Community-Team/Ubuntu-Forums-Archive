---
title: "Answers to questions"
date: 2009-12-26
forum: Testimonials &amp; Experiences
---

### Post by tv_chopper on 2009-12-26
I'm not a Linux noob, but not wildly experienced and for what it is worth have this observation...

I swapped Ubuntu for XP on my works laptop and have just spent many hours over the last three days trying to figure out why my wlan does not work.  Finding accurate and relevant information regarding, in my case Broadcomm adapters, has been an experience that has led me down many frustrating blind alleys.

It works now, but I can tell you that until support information and solutions are accessible and efficient with the slickness of an Apple (I have two Macs), VMWare or Microsoft, this Ubuntu will not gain the recognition it clearly deserves.

Now I have to go figure out why I only get 800x600 resolution on a monitor that normally displays 1440 by 900.  I'll let you know how I get on in a week or two...

---

### Post by Elfy on 2009-12-26
Yep - wireless can be a pain it seems.

If you have video issues then the first port of call in my experience has been Hardware Drivers in the system admin menu to see if there is a driver available.

Regardless of that - people are only going to be able to help if you want it if you give them some information to work with.

Now is this a request for help or just an experience thread - if the latter I will move it out of the support forums, if it is a request for help then I would post with a bit more information.

```
lspci |grep VGA
``` could tell you what video adaptor

---

### Post by Gone fishing on 2009-12-26
Have you got the propriety drivers loaded? You need to get the computer onto the Internet (LAN cable maybe?) then go to  synaptic (System > Administrator) and make sure you have the restricted driver repository checked then reload to refresh the package data.

I did an HP laptop for a friend and the Free Broadcom driver wouldn't work however the proprietary driver worked fine. You have the choice of which to enable in Hardware drivers (System > Administrator)

Its hard to give advice on the screen resolution as we don't know what graphics you lap top uses but if a graphics driver is available in Hardware driver enable it.

---

### Post by tv_chopper on 2009-12-26
[FONT=Verdana][SIZE=2]*[quote=forestpiskie;8560195]Yep - wireless can be a pain it seems*.

But wireless is consumer electronics these days, can't afford to be a pain, sir.

*If you have video issues then the first port of call in my experience has been Hardware Drivers in the system admin menu to see if there is a driver available.*
[I]
Regardless of that - people are only going to be able to help if you want it if you give them some information to work with[/I].

I wasn't really asking for help, I was observing that seeking assistance and getting to a solution in Ubuntu world is not conducive to a wider spread usage of this wonderful software.  I didn't change XP for Ubuntu for nowt, just imagine the grief I am going to get from corporate IT when they get a whiff of this...

*Now is this a request for help or just an experience thread - if the latter I will move it out of the support forums, if it is a request for help then I would post with a bit more information.*

[/SIZE][/FONT][FONT=Verdana][SIZE=2]It seems, sir, that you are the boss and will move my post at will.  In solving my issues I have tried to stay away from asking the same divvy question as others and have [/SIZE][/FONT][FONT=Verdana][SIZE=2]researched the issues and learned from the experience.  It satisfies my inner-nerd.

I know what my adapter is[/SIZE][/FONT][FONT=Verdana][SIZE=2] (       [/SIZE][/FONT][SIZE=3][FONT=Verdana][SIZE=2]Nvidia GeForce4 Ti 4200 64MB 8x) but I can't seem to locate the driver for it, which is more about being a lousy detective than a satisfied nerd...

Thanks for your patience...
[/SIZE][/FONT][/SIZE]

---

### Post by Gone fishing on 2009-12-26
The driver for your card should be available from Hardware drivers (your card is basically the same as my sons). But you will need to be on the Internet and refresh the repositories before it will appear available and you will be able to activate it

---

### Post by CaptainMark on 2009-12-26
The reason youve had trouble is because the people who made your wirelessa adapter havent made drivers for linux, they easily could if they tried, theyve probaly done the lazy option and only made windows drivers, blame broadcomm for your troubles, not linux. Linux loves you

---

### Post by prenoob on 2009-12-26
> The reason youve had trouble is because the people who made your wirelessa adapter havent made drivers for linux, they easily could if they tried, theyve probaly done the lazy option and only made windows drivers, blame broadcomm for your troubles, not linux. Linux loves you  I fear that summarises the attitude of some people who seem to be saying "I'm clever enough to make Linux work - you're stuck with Windows".  No doubt you don't mean it to come over like that - but it does!

---

### Post by CaptainMark on 2009-12-26
not at all, it just annoys me that many companies make drivers for windows only and ignore linux, because of this linux has a reputation that many types of hardware wont work on it. This means people get put off using linux without trying it, kudos to the op for giving us the benfit of the doubt

---

### Post by 3rdalbum on 2009-12-26
> **prenoob said:**
> I fear that summarises the attitude of some people who seem to be saying "I'm clever enough to make Linux work - you're stuck with Windows".  No doubt you don't mean it to come over like that - but it does!

It's more a case of Broadcom or Nvidia saying "We don't need to make it easy to install our drivers on Linux, because all Linux users are super-geeks".

So when ordinary people start using Linux, they have troubles installing these things.

It's not even just hardware manufacturers - I bought an external hard disk a few years ago and I asked the salesperson if it needed any drivers or if it was just plug 'n' play with Linux. He said "Yes it's plug 'n' play, but you'll need to reformat it from NTFS to Ext3, but I'm sure you'd already know how to do that."

I can install Nvidia drivers. I can compile kernel modules. But not every other Linux user can. Please make user-friendly installers for drivers! That's what's great about Ubuntu - the Hardware Drivers program is very easy for anyone to use, provided you have the drivers in a repository.

---

### Post by The Cog on 2009-12-26
> *> **forestpiskie said:**
> Yep - wireless can be a pain it seems.*

But wireless is consumer electronics these days, can't afford to be a pain, sir.



So don't buy Broadcom. Would you buy Betamax tapes to use in your VHS recorder and then complain to the VHS manufacturer when your new tapes don't play (or even fit in the slot)? They would laugh at you. 

Broadcom have decreed that their drivers cannot be shipped with Linux. That's Broadcom's decision - their drivers, their copyright, their rules on reproduction. There's no point in complaining to the Linux distro makers that they aren't breaking the law - you're complaining at the wrong people. You could maybe blame Broadcom for not allowing inclusion of their drivers, but really, the answer is don't buy hardware from suppliers that don't permit proper Linux support.

---

### Post by ugm6hr on 2009-12-26
> **tv_chopper said:**
> I wasn't really asking for help

Hence moved somewhere more appropriate.

Repost if you want technical help.

---

### Post by Elfy on 2009-12-26
and closed

---

