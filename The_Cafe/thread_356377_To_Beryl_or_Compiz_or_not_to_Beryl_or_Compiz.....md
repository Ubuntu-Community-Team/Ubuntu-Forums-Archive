---
title: "To Beryl or Compiz or not to Beryl or Compiz...."
date: 2007-02-08
forum: The Cafe
---

### Post by PapaWiskas on 2007-02-08
....that is the question.

I have the following Laptop that has been running Ubuntu flawlessly since Breezy, now I am running
Dapper.  To afraid to upgrade to Edgy since I am afraid my wireless would stop working.
I would really like some eye candy, and it seems like Compiz is complicated to install, but Beryl
might be a better choice.
Could anyone tell me by looking at my specs if I could run this or not?  I know I have a 
ATI mobility card and everyone goes on and on about how nvidia is better but ATI is possible.
I just wonder how much work is it going to be to get that cool 3d cube thingy and other 
effects.
Help anyone?

Thank you for your time.

Sony VAIO
ModelVGN-A130P

1 GIG Ram

Graphics
ATI Mobility™ Radeon™ 9200 64MB

Intel® Pentium® M Processor 1.50GHz

---

### Post by John.Michael.Kane on 2007-02-08
The GPU is supported.

You have have enough mem to take beryl on

The Cpu is strong enough for the task.

Have read over this [http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7)

Also from what i have read they seem to have made it a little bit more easier for ati folks to install beryl under edgy,however. the link above should get you going  on dapper.


Note: understand that installing beryl can lead to some issues.

---

### Post by hanzomon4 on 2007-02-08
To be honest, both beryl and compiz are easy to install. 
I the main problem most people run into is setting up accelerated X. AIGLX(easy) XGL(not so easy) so figure out which method your card will support and set that up first.

---

### Post by fuscia on 2007-02-08
papa, have you gotten to try it at all? if not, the sabayon live cd comes with it. you just have to type *aiglx-gentoo* (or, something like that. the site would tell you) at the boot prompt and it will boot right into kde-beryl.

---

### Post by Lord Darth Vader on 2007-02-08
> **SD-Plissken said:**
> 

Also from what i have read they seem to have made it a little bit more easier for ati folks to install beryl under edgy.

I have a laptop with Ati 340M with shared memory and installing beryl under Edgy was really easy.

---

### Post by morphet on 2007-02-08
> **fuscia said:**
> papa, have you gotten to try it at all? if not, the sabayon live cd comes with it. you just have to type *aiglx-gentoo* (or, something like that. the site would tell you) at the boot prompt and it will boot right into kde-beryl.

I would have to advise against Sabayon. It's a really interesting distro, and it is amazing to be able to see beryl even at the liveCD stage. However, your system will require days/weeks of tweaking, which I assume you don't have, if you avoided switching to edgy because of the wifi. A good many gentoo/sabayon users will tell you that Gentoo/Sabayon is an awesome system for the patient, dedicated, experienced user.

---

### Post by Lord Darth Vader on 2007-02-08
> **morphet said:**
> However, your system will require days/weeks of tweaking, 

I have been using Ubuntu as the main OS on my laptop and I chose it among many others. However I have to say that it DOES require many tweaking for many basic tasks before you can call it your main OS! I have a long list that I go through it whenever I have to reinstall Ubuntu.

---

### Post by PapaWiskas on 2007-02-08
I guess what I will do is try an Edgy install and go from there.  The only thing about doing that is losing everything I have set up and got working so far.

It has been a long road since December of 05 to get where I am, I did a upgrade from Breezy to Dapper without to much of an issue.  But if I upgrade to Edgy, I have read several things about the wireless stops working and that is my only way of connecting, if I loose that I am toast.

I know there is a way to back up my system so I dont lose all the software I installed and what not, but then I have to go dig up that post somewhere here on the forums.

All of it seems so daunting just to get that really cool 3D cube....

And fuscia, no I have not tried the sabayon distro yet, my Ubuntu has never ever failed me, but I am growing restless and want to do what all the other cool kids are doing....:lolflag:

> **hanzomon4 said:**
> To be honest, both beryl and compiz are easy to install. 
I the main problem most people run into is setting up accelerated X. AIGLX(easy) XGL(not so easy) so figure out which method your card will support and set that up first.

So how do I figure out which one my card would support?  Sorry if that question is stupid or redundant....

---

### Post by RAV TUX on 2007-02-08
> **PapaWiskas said:**
> ....that is the question.

I have the following Laptop that has been running Ubuntu flawlessly since Breezy, now I am running
Dapper.  To afraid to upgrade to Edgy since I am afraid my wireless would stop working.
I would really like some eye candy, and it seems like Compiz is complicated to install, but Beryl
might be a better choice.
Could anyone tell me by looking at my specs if I could run this or not?  I know I have a 
ATI mobility card and everyone goes on and on about how nvidia is better but ATI is possible.
I just wonder how much work is it going to be to get that cool 3d cube thingy and other 
effects.
Help anyone?

Thank you for your time.

Sony VAIO
ModelVGN-A130P

1 GIG Ram

Graphics
ATI Mobility&#8482; Radeon&#8482; 9200 64MB

Intel® Pentium® M Processor 1.50GHz

I use Beryl in Sabayon 3.26,...XGL simply works with "NO" tweaking....:popcorn:

(I have an ATI Radeon Platinum)

> **hanzomon4 said:**
> To be honest, both beryl and compiz are easy to install. 
I the main problem most people run into is setting up accelerated X. AIGLX(easy) XGL(not so easy) so figure out which method your card will support and set that up first.

just load a live CD with Beryl installed by default...

I suggest Sabayon...because everything just works....some people I know have had to some minor tweaking but no more then in Ubuntu

Also If you like Ubuntu then try UBeryl...UBeryl is Ubuntu+Beryl....installed by default...works awesome!:popcorn:

> **fuscia said:**
> papa, have you gotten to try it at all? if not, the sabayon live cd comes with it. you just have to type *aiglx-gentoo* (or, something like that. the site would tell you) at the boot prompt and it will boot right into kde-beryl.

No need to type anything...upon booting the live CD you simply select the desktop acceleration of your choice....It honestly could not be easier...

again UBeryl is pain free and based on Ubuntu...also just works:popcorn:

> **morphet said:**
> I would have to advise against Sabayon. It's a really interesting distro, and it is amazing to be able to see beryl even at the liveCD stage. However, your system will require days/weeks of tweaking, which I assume you don't have, if you avoided switching to edgy because of the wifi. A good many gentoo/sabayon users will tell you that Gentoo/Sabayon is an awesome system for the patient, dedicated, experienced user.

hmmm,...sad to here you have had difficulties,....perhaps you should try UBeryl.

As far as days or weeks of tweaking I am so glad that this did not happen to me...everything simply worked "out-of-the-box"....it honestly is the easiest of OS's to install....I had zero tweak time:popcorn:

There is a reason why I use Sabayon on my Primary computer...not because it was hard but because it was easy!...and everything thing just works by default.

Again if you want Beryl by default in Ubuntu simply use UBeryl.....

I will always use Ubuntu on my secondary computer...well I may load Xubuntu or Fluxbuntu on it to increase speed...it kinda crawls on the old P3:popcorn:

I love Beryl for it's function and it's beauty....(yes I said function):popcorn:

> **PapaWiskas said:**
> 

All of it seems so daunting just to get that really cool 3D cube....

And fuscia, no I have not tried the sabayon distro yet, my Ubuntu has never ever failed me, but I am growing restless and want to do what all the other cool kids are doing....:lolflag:



So how do I figure out which one my card would support?  Sorry if that question is stupid or redundant....

No need to figure this out in Sabayon or UBeryl it will do all the work for you,....and detect what will or will not work for you...automagically!:popcorn:

---

### Post by joplass on 2007-02-08
Let me just say that Compiz broke my xserver the only time I tried it.  Beryl has been going strong so far with all the updates and such...

---

### Post by RAV TUX on 2007-02-08
> **joplass said:**
> Let me just say that Compiz broke my xserver the only time I tried it.  Beryl has been going strong so far with all the updates and such...

just don't jump into the latest release....use the "somewhat Stable"....(as stable as Beta can be, which supposedly isn't much)

What comes by default with Sabayon and UBeryl will be fine to start with...start slow with Beryl and ease into it and you will be fine...
start with a live CD/DVD first that has Beryl installed by default:popcorn:

---

### Post by PapaWiskas on 2007-02-08
So is Uberyl in Spanish or English, because my Spanish reading abilities are not good at all.:confused:

Wow....Uberyl is a really slow download...

---

### Post by RAV TUX on 2007-02-08
> **PapaWiskas said:**
> So is Uberyl in Spanish or English, because my Spanish reading abilities are not good at all.:confused:

Wow....Uberyl is a really slow download...UBeryl is in English and Spanish...by default it is in English:popcorn:

---

### Post by PapaWiskas on 2007-02-09
Well I got the Uberyl Live CD to work, wow that Beryl stuff is cool.

The Sabayon Live CD, well, it gives me some sort of watchdog error, so I had to reboot in safe mode and go in that way.
I am thinking I would have to tinker with Sabayon to much to get it to work, where as Uberyl just works.

I have not tried the Edgy Live CD yet, does this also install Beryl by default?

---

### Post by RAV TUX on 2007-02-09
> **PapaWiskas said:**
> 

I have not tried the Edgy Live CD yet, does this also install Beryl by default?

I don't think so, it is probably best you stick with UBeryl

---

### Post by macogw on 2007-02-09
> **PapaWiskas said:**
> So is Uberyl in Spanish or English, because my Spanish reading abilities are not good at all.:confused:

Wow....Uberyl is a really slow download...

I thought it was Italian and English..

---

### Post by PapaWiskas on 2007-02-10
> **macogw said:**
> I thought it was Italian and English..

Spanish.....Italian.....don't understand either one....:lolflag:   sorry...

---

### Post by RAV TUX on 2007-02-10
> **macogw said:**
> I thought it was Italian and English..

It's in Spanish and English, but when you boot the live CD it is in English by default. So if you speak English no worries.:popcorn:

---

