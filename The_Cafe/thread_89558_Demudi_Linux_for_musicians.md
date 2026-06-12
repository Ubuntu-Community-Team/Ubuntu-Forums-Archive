---
title: "Demudi: Linux for musicians?"
date: 2005-11-12
forum: The Cafe
---

### Post by jrincon87 on 2005-11-12
Hey. I'd like to set up Ubuntu to be a sound oriented system. But it's been hard and I haven't achieved nothing (have problems with MIDI). To write music scores I found a nice little program called Noteedit (no way I'm gonna use Lilypond). There's another good program called Rosegarden, but without a good midi configuration it might not be worth, and this last it's not so intuitive as I expected it to be (I mean, in comparision with the Windows program to make music scores and to work with MIDI). I've read every manual to set up Ubuntu to make it work with MIDI, but sincerely it's EXTREMELY tedious (and there's the fact that it might not work, and it hasn't for me). I love Ubuntu and I'd like to keep it but I read that there's another Debian based distribution called Demudi, a sound oriented Linux distribution.
Has anybody heard or has this distribution to tell me if it's worth?
I think that's something to improve in Ubuntu and in Linux in general. Linux has the capacity of being an excellent multimedia box (with some work it could get even at the level of Mac in that aspect). By now Linux lacks of good and easy to use music programs.
Comments?
By now I'm gonna give Demudi a try.

---

### Post by kagashe on 2005-11-12
Hi,

I suggest you have a look at [this page]("http://distrowatch.com/table.php?distribution=Demudi") on distrowatch.

There are links for mailing list and forums where you may get the information.

kagashe

---

### Post by johannes on 2005-11-13
I tried out [Demudi]("http://demudi.agnula.org/") some time ago. The Live CD (based on Ubuntu 5.04) worked really great of course, autodetected all my sound hardware and pretty much everything else. I decided to try and install it from the install CD (based Debian Sarge I think), and it seemed to be fine, until I tried apt-getting some new updates. There were a lot of dependencies errors with various basic packages like c++ libraries and I found out I was pretty much unable to upgrade or install anything besides the basic installation. If I tried to remove the outdated libraries then of course all the music apps would be removed as well. It seems like Demudi isn't updated very often.

The good side of Demudi is of course that it comes with great sound support. It uses a low latency multimedia kernel, the Jack Audio Connection Kit by default, MIDI auto configuration (in my case) and a lot of great music apps for both using your computer in a studio and as a studio. :)

I would recommend that if you have a dedicated music computer you should try out Demudi, and use another computer for your every day work/messing around. If you only have one computer and plan to use it for both music making and every day stuff, I recommend that you install Demudi on a diffrent partition and dual boot with Ubuntu or something.

---

### Post by MetalMusicAddict on 2005-11-13
Ive been looking at Demudi for along time now. I really like what they are doing. Ive been trained as an audio engineer and have found the apps in the linux audio world go be great. But...

I think they still have a bit to go. Some things in Demudi need to be updated (drivers, apps etc) and I would wait till the next release to do anything serious but still play with it now. ;)

Im looking at building a mobile project studio I can fit in a roadcase.

---

### Post by GabrielWolff on 2005-11-13
Hey lads.

Before going through installing stuff and so, I'd like one of you to tell me that Noteedit (or ANYTHING else) is as good a program as Finale. I really need a good notation program, and am about to switch back to WIN because of that. I'm really desperade.

Anyone?

Gabriel

---

### Post by papangul on 2005-11-13
There's another distro intended for musicians: [Apodio]("http://www.apo33.org/apodio/gupp/?lng=en")

---

### Post by floppy on 2005-11-13
[QUOTE=GabrielWolff]Hey lads.

Before going through installing stuff and so, I'd like one of you to tell me that Noteedit (or ANYTHING else) is as good a program as Finale. I really need a good notation program, and am about to switch back to WIN because of that. I'm really desperade.

Anyone?

Gabriel[/QUOTE]

I too wish there was more emphasis on music production in Linux. I use a laptop with Win98SE on it for mine. Unfortunately, I have yet to find a usable distro, but I must admit I've only searched occasionally.

Before you totally switch back, consider using Crossover Office. I don't know if Finale works under it, though.
[http://www.codeweavers.com/site/products/cxoffice](http://www.codeweavers.com/site/products/cxoffice)

---

### Post by GabrielWolff on 2005-11-13
It doesn't, at least not any of the versions older than 2006, which I have yet to try. Any other ideas how I could use it other than under Crossover Office? I don't need an entire distro, I guess. Just something like Crossover to run Finale with.
Gabriel

---

### Post by MetalMusicAddict on 2005-11-13
[QUOTE=GabrielWolff]Hey lads.

Before going through installing stuff and so, I'd like one of you to tell me that Noteedit (or ANYTHING else) is as good a program as Finale. I really need a good notation program, and am about to switch back to WIN because of that. I'm really desperade.

Anyone?

Gabriel[/QUOTE]
I dont do much notation but friends use Lilypond.

---

### Post by GabrielWolff on 2005-11-13
[QUOTE=MetalMusicAddict]I dont do much notation but friends use Lilypond.[/QUOTE]
I had a hard time with Lilypond. Any good suggestions for a nice frontend? Something that looks like Finale, or is easy to figure out...

And most important: I got a lot of .mus files I still want to print out or re-arrange. I have to have the possibility to import .mus

Gabriel

---

### Post by MetalMusicAddict on 2005-11-13
Not sure on the .mus files. Maybe [Rosegarden]("http://www.rosegardenmusic.com/")?

---

### Post by GabrielWolff on 2005-11-13
[QUOTE=MetalMusicAddict]Not sure on the .mus files. Maybe [Rosegarden]("http://www.rosegardenmusic.com/")?[/QUOTE]

It's nice, but basically it's not a notation program. It's more like Cubase under WIN. So there IS a possibility to notate, but it's very poor, and not at all enough for writing scores.

Any other ideas?

Gabriel

---

### Post by MetalMusicAddict on 2005-11-13
Yea. I wasnt sure about Rosegarden. Lilypond did seem to be a better option but you said your having a tough time with that. 

Hmm. Ill stay on the lookout and post here if I find anything. Maybe give some of the linux audio fourms a look.

---

### Post by gosh on 2005-11-14
You might also look into the Agnula project.

---

### Post by MetalMusicAddict on 2005-11-14
[QUOTE=gosh]You might also look into the Agnula project.[/QUOTE]
Demudi is part of the "Agnula project" ;)

---

### Post by trash on 2005-11-17
I just booted up Demudi 1.2.1 on my P11, what an awesome livecd... will be installing soon on new roomies machine to get our music room up and running.

---

### Post by MetalMusicAddict on 2005-11-17
Good for you. Since its Debian based I was very comfortable with the install and environment. :)

---

