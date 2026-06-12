---
title: "Another round with Ubuntu"
date: 2009-01-12
forum: Testimonials &amp; Experiences
---

### Post by nerd0795 on 2009-01-12
I've got a brand new laptop (an Acer Aspire 4530).  Well it works all great, Vista working good.  I was told by the person who helped me buy it who is a linux hater (used to be fan with the early versions of Ubuntu, after so many upgrades it got corrupted.  So he told me don't put Ubuntu on it, Ubuntu will kill it.  I wanted to everyday.  So eventually I said screw it.  It's my laptop so I can do what I want with it.  Nobody else uses it.  So I downloaded wubi (heard Ubuntu used to not work on this model.  But Ubuntu 8.10 works on it.  So I wasn't expecting much)  Especially with the ISO on my computer because a day before I recovered someone's data with a Ubuntu 8.10 live cd.  I installed Ubuntu (without the linux hater here) with wubi to make it easy to uninstall.  

So it told me to reboot after all the steps and worked wonderfully.  The install finished.  Though a dilemna appeared.  The graphic card driver wouldn't install.  After some friendly help from this forum I got it to work.  Then compiz was working.  I kept on working to get the headphone jack, built in mic, and other stuff to work.  Then the track pad settings were changed.  

I installed Adobe Flash, and everything was good.  UNTIL, I watched a YouTube Video.  IT was laggy as HELL.  Took 100% CPU usage.  I tried everything, installing older version, installing by synpatic, installing by tar.gz, but nothing worked.  

Though later, my Mom was watching me, when I shut down my computer and the shut down screen had garbled graphics.  No big deal but she got paniced "OMG YOU'RE GONNA BREAK YOUR LAPTOP".  She was already worried after the unsucessful graphic driver installs a reboot had a kernal panic and the system was beeping VERY LOUD.  

I decided to uninstall it though.  The performance wasn't that great due to the drivers of the machine.  Although it was a great experience.  I was also running out of HDD space.  So I uninstalled it D:  I needed to the space (only like 15 gigs left)  When I get another computer (a desktop is my next which will be my first one) I'll put Ubuntu back on.  It was really the drivers, I didn't have enough time to tweak it and the limited HDD space.

---

### Post by jbysmith on 2009-01-12
Wubi's a viable alternative if you don't want to mess with your partitons.  Disk access is a little slower as it's a virtual disk of sorts vs the real thing, but otherwise it's identical.  Just wish it supported more distros for "live testing" purposes; be a lot more accurate of a test drive vs a LiveCD as you can update to current and such.

For your video issues, did you install your proprietary driver or using the default open ones?  (Makes a huge difference in performance)

And are you using flashplugin-nonfree or adobeflash-plugin?  The latter is Flash 10, which seems to run a lot better at least on my system vs the former.  (I think I got the names right.. not at my system at the moment.)

And if anything is gonna actually break the laptop, it'll be Windows :D  (Usually when you mash your head on the keyboard in frustration dealing with the latest Virtumonde malware.)

---

### Post by nerd0795 on 2009-01-12
> **jbysmith said:**
> Wubi's a viable alternative if you don't want to mess with your partitons.  Disk access is a little slower as it's a virtual disk of sorts vs the real thing, but otherwise it's identical.  Just wish it supported more distros for "live testing" purposes; be a lot more accurate of a test drive vs a LiveCD as you can update to current and such.

For your video issues, did you install your proprietary driver or using the default open ones?  (Makes a huge difference in performance)

And are you using flashplugin-nonfree or adobeflash-plugin?  The latter is Flash 10, which seems to run a lot better at least on my system vs the former.  (I think I got the names right.. not at my system at the moment.)

And if anything is gonna actually break the laptop, it'll be Windows :D  (Usually when you mash your head on the keyboard in frustration dealing with the latest Virtumonde malware.)

I used the proprietary one.  I tried both flash plug-ins

---

### Post by nerd0795 on 2009-01-12
UPDATE:  I've found I got 60 gigs available on my other partition (Acer splits main hdd partition into 2 different ones.  So I installed Ubuntu through Wubi on D:  UBUNTU IS BACK :D

---

### Post by FAMUgolfer on 2009-01-18
I have a 4530-5889, and yeah Ubuntu was a little time consuming getting graphics, sound, webcam, wireless, and mic to work properly.  My only issue is pretty much the same as yours: youtube is very laggy (plays for 3 seconds then firefox goes grey and then comes back and does it all over again) and also with the logout splash.  The lower half of my logout splash is all jumbled and hazy (sorry, don't know the correct terminology for it)  Other than that, I wish I could get bluetooth working.  Have you solved the bluetooth problem yet?

---

### Post by wolfen69 on 2009-01-18
> **nerd0795 said:**
> 

I installed Adobe Flash, and everything was good.  UNTIL, I watched a YouTube Video.  IT was laggy as HELL.  Took 100% CPU usage. 

that's not surprising, considering it takes more resources to run wubi. a real dual boot (non-wubi) would probably fix that.

---

### Post by 3rdalbum on 2009-01-19
I don't know why Acer makes such a big secondary partition. Most users don't even realise that it's there, and they constantly think that they are running out of space when all they need to do is save to /dev/sda1 (or the D: drive).

---

### Post by hyper_ch on 2009-01-19
do you use 64bit or 32bit?

---

### Post by Martje_001 on 2009-01-19
> **wolfen69 said:**
> that's not surprising, considering it takes more resources to run wubi. a real dual boot (non-wubi) would probably fix that.
Euuhm.. no?

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

---

### Post by solwic on 2009-01-19
> **Martje_001 said:**
> Euuhm.. no?

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

Wubi is slower than a regular install.  Quite significantly, actually.  Especially for read/write to the HDD.

---

### Post by Martje_001 on 2009-01-19
OK, true, but that still has nothing to do with watching video's on youtube.

---

### Post by wolfen69 on 2009-01-19
am i the only person in the world to have done ubuntu installs on over 30 different machines without a problem? am i a genius? i must be. flash has never failed me.

the thing is, none of us can be there to hold your hand and guide you through the process. if i was there for instance, i guarantee flash (youtube) would work. it always does. i make it work. (that's my job)

wubi is ok to check things out, but real computer users will want to setup a real dual boot. if you decide to ignore this advice, that's OK. bill gates and steve jobs are there to lighten your wallet.

---

### Post by Martje_001 on 2009-01-19
> **wolfen69 said:**
> am **i** the only person in the world to have done ubuntu installs on over 30 different machines without a problem? am **i** a genius? **i** must be. flash has never failed me.
1. It's I. Thank you.

2. You must keep in mind that what's easy for you, may be very difficult for someone else.

3. When I started with Ubuntu, installations failed all the time. Now, an install never fails.

---

### Post by solwic on 2009-01-19
> **Martje_001 said:**
> 1. It's I. Thank you.

2. You must keep in mind that what's easy for you, may be very difficult for someone else.

3. When I started with Ubuntu, installations failed all the time. Now, an install never fails.

Are you really nitpicking over grammar?  In that case, there should be no comma between "you" and "may" in number 2.  Likewise the comma between "Ubuntu" and "installations" in number 3 is unnecessary.  

The *point*, though, is that a whole bunch of people have zero issues with Flash (myself included).  I've never had to do more to Flash than install the ubuntu-restricted-extras package.  If there's an issue with Flash, the fact that Wubi is so slow *could* have something to do with it.  Otherwise, it's likely a hardware thing, or something the person did during install of the OS or during install of the Flash component. 

And if that's a problem the OP doesn't want to deal with, there's always Windows or Mac; both of which cost a whole lot more than a few hours searching the net, or even fifty bucks or so to replace whatever hardware might be causing the problem.  :)

Cheers!

---

### Post by Martje_001 on 2009-01-19
> **jrock612 said:**
> Are you really nitpicking over grammar?  In that case, there should be no comma between "you" and "may" in number 2.  Likewise the comma between "Ubuntu" and "installations" in number 3 is unnecessary.
It was not meant that way, but I just think writing 'I' is a basic thing.. Oh well, carry on.

Nevertheless, I think you've got a point. Really. But I think you should also keep in mind that the things that you see as basic, can be very though for a beginner (like I said earlier).

---

### Post by wolfen69 on 2009-01-19
> 1. It's I. Thank you.
i'll type any way i want, thank you. don't like it, don't read it.

> 2. You must keep in mind that what's easy for you, may be very difficult for someone else.
where do i download ubuntu? is a question i've seen. obviously people have difficulty with googling for what the rest of the world takes for granted. stupid people will always be here. your point means nothing. my windows customers are some of the most stupid computer users i've ever seen. it's the user that needs adjusting, not the OS. if you're not willing to learn your OS, then maybe you shouldn't be using a computer in the first place. btw, what did people do before computers were around? maybe those that have problems should toss their machines and live 50's style. they'll probably be better off.

---

### Post by stchman on 2009-01-19
> **nerd0795 said:**
> UPDATE:  I've found I got 60 gigs available on my other partition (Acer splits main hdd partition into 2 different ones.  So I installed Ubuntu through Wubi on D:  UBUNTU IS BACK :D

Give us an lspci output in this thread to see what hardware you have.

---

### Post by collinp on 2009-01-19
Wubi is assured to be slower than a dual-boot install of Ubuntu. Running Windows and Ubuntu at the same time draws more resources than just Ubuntu alone. Plus, it has a lot of effect on Flash and Youtube Videos. The CPU draw of Windows and Ubuntu at the same time, plus Youtube, causes problems.

---

