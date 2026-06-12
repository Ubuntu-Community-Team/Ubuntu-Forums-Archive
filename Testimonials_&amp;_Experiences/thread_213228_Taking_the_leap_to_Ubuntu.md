---
title: "Taking the leap to Ubuntu"
date: 2006-07-11
forum: Testimonials &amp; Experiences
---

### Post by PsiDOC on 2006-07-11
Morning all. This is my 1st post so please be gentle with me. :D

I seem to have linux powered devices all about my home in various guises eg: My WLan Router - WRT54G (DD-WRT) My Satellite System - Dreambox DM7000 (Da-Vinchi Custom) The Kids' Xbox (Very Old version Of GentooX) and even the SatNav in the Truck - TomTom 300 (OEM).
I figured let's have a look at this beastie on the PC.
So Sunday with the afternoon to spare I found a question and answer thingy on the net that recommended Ubuntu or kubuntu as my distro. I decided on ubuntu as I already have the KDE on the Xbox. As an extra note I have never got to play with Gentoox in any great shape or form as the kids are always using the Xbox for it's original purpose!

So we installed it, easy enough job for even a total linux newbie like me.
"Now let's try to get my dual monitors setup" I thought... Oh boy! That's where the fun began.
Got the nvidia drivers installed first time thanks to tseliot's brilliant how to on the Video & Sound section - Many thanks sir. 
Ok now let's do the twin view thingummy bob. I edit up the xorg.conf, log out CTRL, ALT and backspace and..... Command prompt! Error in loading driver line 20-odd. Oh great! what do I do from here? :-k 
So I reboot from Live CD and reinstall.
Try again. Command Prompt!
Reinstall
All in all I did this 4 times. (I know there are a lot of people laughing at me right now because of my daftness!)
So on the 5th time before editing the xorg.conf a quick call is placed to a good friend and a Unix wizz.
He laughs and says "That's easy! - If it errors out call nano from the Command Prompt and edit the xorg.conf from there".... DOH! why didn't I think of that - Been running with windows boxes too long I guess! ](*,) ](*,) ](*,) 
So anyway we try again and it errors out. Line 22 identifier... Ok.. Open in nano and realise that I have 2 identifiers in there! DOH!
Delete one, Save exit, call StartX and....

YIPPEEEE!!!! 2 screens. Mission accomplished for the day.

I know I have a lot to learn and, like the story above, most of it is going to be trial and error on my part, but we'll get there in the end.

So yeah.... Ubuntu. You have another fan! Big ups to the dev team it's a very nicely made distro.

regards,

Psi

---

### Post by nalmeth on 2006-07-11
Sweet!

Hey, do you use Xbox Media Center on the Xbox?

About Gentoox, don't you find it painfully slow running KDE? I did, and then found it has XFCE installed aswell. The Gentoox guys have a new release out now too, I remember it being a breeze to install. Funny considering it is Gentoo. Brilliant devs in my opinion.

---

