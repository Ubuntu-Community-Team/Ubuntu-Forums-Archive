---
title: "Live cd for developers?"
date: 2007-07-03
forum: The Cafe
---

### Post by kaens on 2007-07-03
Hey everyone, I've been thinking of rolling my own version of the feisty live / install cd, geared towards developers.

The idea was born out of using the live-cd to do some backups for a friend before wiping their drive and installing Ubuntu on it. I got the urge to write a script to make the whole process faster (sure maybe it would be reinventing the wheel a bit, but it's a decent, and not very hard programming excersize), and noticed that there doesn't seem to be much in the way of a programmer's text editor included with the current livecd.

Sure, there's vim. With no syntax highlighting.

First off, I'd like to know if there would be interest in something like this (I'll probably be making it either way, but I'll get around to it a lot faster if I know other people would appreciate it).

Second off, I'd like to know what people would like included on it. I'm thinking of Eclipse, emacs, and vim, lots of programming-languages and the appropriate documentation, maybe give the choice of gnome, kde, or fluxbox as the desktop environment during install (and not install the other ones) given that that can fit on a cd, 

Oh, and nethack. 

So, good idea or not?

And what would you people like to see on it (assuming there's some other people who wish there was an ubuntu live-cd they could use to do a little quick development with tools they like to use)?

---

### Post by Tomosaur on 2007-07-03
I've gotta say, I don't think it's such a great idea, for the following reasons:

1) Speed. The LiveCD is usually a pretty slow example of a distribution. Yes, you can trim the fat and get something fairly workable, but there's no substitute for an installed version. Not everyone has enough RAM necessary to get a LiveCD working fast enough to make the effort worthwhile. Compilation and testing would be a nightmare in this scenario.
2) Non-persistant memory. Great, I have the tools I need. Better not switch off the machine or everything is lost. Yes, I can use a USB stick, but why would I? Why do I need to develop 'on the move', and, if I do need to, isn't a laptop just an infinitely better solution?
3) Developers tend to have their own machines. We don't need to be portable (if anything, moving around is a bad thing for developers).

Of course, I may have misunderstood you completely here. Are you talking about rolling your own **distribution** of Ubuntu geared at developers? In which case, yes, there'd probably be a market for it, but bear in mind that there are distributions out there which perform a similar function, and many developers probably already use one or are versatile enough to convert any Linux distro into a 'development machine'. Part of the indoctrination for a Linux developer is to have everything they need constantly available in the first place, don't you know :P

---

### Post by Warpnow on 2007-07-03
But some coders write in windows and then want to compile it in linux. I think it could be a good idea. Make sure you have different versions of GCC installed, would be my advice. Haha, is that sad? That my code is so bad I often have to dial back the gcc?

---

### Post by kaens on 2007-07-03
> **Tomosaur said:**
> 
Of course, I may have misunderstood you completely here. Are you talking about rolling your own **distribution** of Ubuntu geared at developers? 

Yes. Somewhat. I'm thinking of customizing the current livecd and it's install process to allow some things which developers almost always install on their Ubuntu machines immediately to be installed by default or by choice, and having those tools available on the live cd for the rare occurances when you want (or need) the capability to code up something dealing with the data on a machine without being able to boot the machine from the hard drive.

RAM certainly is an issue. I personally wish the livecd's had an alternate text-mode (yeah, there's the alternate cd, but I can't boot to a shell with that) for machines with low amounts of ram.

> 
Why do I need to develop 'on the move', and, if I do need to, isn't a laptop just an infinitely better solution?

Absolutely a laptop is a better solution. It may not be applicable all the time though, depending on what you're doing. Maybe you don't have a laptop, maybe you don't have your laptop with you. I've used livecds to do work in a linux environment when none was available, and then emailed the completed work to myself.


> 
3) Developers tend to have their own machines. We don't need to be portable (if anything, moving around is a bad thing for developers).

I guess that depends on the developer. I like to go work on  some code in a public place sometimes, and I use a laptop for that. There's a coffeeshop near me with free wifi that has a really awesome atmosphere, and I find it quite conducive to productivity.

[quote=Warpnow]But some coders write in windows and then want to compile it in linux. I think it could be a good idea. Make sure you have different versions of GCC installed, would be my advice. Haha, is that sad? That my code is so bad I often have to dial back the gcc?[/quote]

I often find myself having to dial back gcc to compile something someone else wrote. That's a good call.

Thanks for the responses.

---

