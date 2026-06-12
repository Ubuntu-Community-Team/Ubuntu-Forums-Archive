---
title: "OH Audacity How do I hate Thee"
date: 2008-05-30
forum: Ubuntu Studio
---

### Post by rab4567 on 2008-05-30
Can someone tell me a foolproof way to set up audacity It seems work fine  on my Acer AMD 4400 6100 nvidia  1GB 320GBHD, but on the HP AMD 4200 6150LE nvidia 2GB 500HD it sticks its tongue out turns around and says NO! What must I do, go to rezound which doesn't work or perhaps maybe (swallow) try ardour. I know I'm not the only one having this problem can anyone help.

---

### Post by aeiah on 2008-05-30
you've not actually said what the problem is yet. when you launch it from a terminal, what error messages pop up?

---

### Post by rab4567 on 2008-05-30
Your absolutely right I'm not getting any sound.  I didn't think about using the terminal but here's the error message.

---

### Post by Bungo Pony on 2008-05-30
Audacity hates Pulse Audio. Try using Jack Audio Control with it. You'll find it soothes the pain a bit.

I've personally given up on Audacity for the time being. I use a piece of Windows software running in WINE for the bulk of my audio editing needs.

---

### Post by Stochastic on 2008-05-31
If you want to get rezound working instead of audacity, edit the first two lines of your /home/username/.rezound/registry.dat file to have "jack" come first, then run jack before starting rezound.

---

### Post by rab4567 on 2008-05-31
Thanks guys, I'm using rezound with jack right now it would be nice to have some detailed  documentation to get know all the different features. Audacity is nice but hard to configure and ardour I don't have clue at all.

---

### Post by rab4567 on 2008-05-31
Its brings questions to mind if I get ride of pulse audio will it break half dozen things that are working fine on my computer now?

---

### Post by thorgal on 2008-05-31
maybe, maybe not.
Most audio apps or sound servers were written before pulseaudio came up. So in principle, switching back to good old alsa should not cause any harm. If you use apps like amarok or xine, mplayer, etc which can use pulaseaudio directly, they can also be reconfigured to use alsa, which they did for a loooong time. The move to PA so early was probably a bit too fast ... in my opinion ...

I don't know about hardy, I don't use it but I know that you can turn off PA by writing (in a terminal) : pulseaudio -k

I tried PA on my laptop running gutsy, and some stuff is quite neat (easy net streaming for exemple, or one unified interface to access all apps connected to the PA server). BUt you need to know your linux to have PA not bulldoze other sound apps and servers (like jack or alsa).

---

### Post by rab4567 on 2008-05-31
There needs to be a definitive manual on alsa and pulse audio, a lot of people are having problems with this issue in hardy. Some have no sound at all this is a major deal beaker for new users I myself want every new user to be blown away by ubuntu and never look back to windows or mac ever again this must be ironed out. I hope one day some one makes a linux audacity replacement thats easy use and powerful.

---

### Post by thorgal on 2008-05-31
I see what you mean ... but that's the open-source world. You get immensely rewarded if you get your hands quite "dirty" at times but yeah, it includes "dirty". I am always impressed by the ubuntu effort to create an "illusion" that linux can be a zero-dollar windows (now, I don't want to be flamed for what I just said because it does not reflect my opinion about what ubuntu is) but whether it is unfortunate or not (and I think it is not at all), ubuntu will never be such a thing, thank god!

but yeah, everyone would like to see all pieces of hardware to be fully supported by linux OOB, and a more unified framework for audio, video, etc. That's true ... personaly, I like to have it a bit messy. It teaches me a lot about my computer and make me take roads I wouldn't have thought of before. Of course, I can say so because after A LOT of tweaking, cursing and sweating, I ended up with a very nice working audio setup for my music production (the reward I was mentioning at the beginning) but coming from unix only and not windows, I did not have certain prejudices or expectations from the start when I came to linux.

---

### Post by rab4567 on 2008-05-31
Your right about cursing and sweating and learning new things, but I come from the matrix mind prison world where everything is done for you for a price and sometimes its hard for us to work it out. The price for freedom is work and for hard core command line users that comes easy, so don't be too hard on us ex window dudes where're learning, it just takes time. But I do miss one audio editing progam called magic.

---

### Post by thorgal on 2008-05-31
> 
magic

:lolflag:

but I am not too hard with those who took the blue pill :)
My presence in this forum and others, even though I don't use ubuntu but debian for multimedia prod, is my feedback to the community as a token of gratitude for the amazing ant work the open-source dev have been delivering until now.

---

### Post by rab4567 on 2008-05-31
Well as an ex blue pill taker I could never go back, compiz fusion was the vehicle that brought me out of windows gulag and ever since I work hard not to use windows ever! But I do want to give back to the community in some small way, maybe send some money for audacity replacement who knows.

---

### Post by thorgal on 2008-05-31
don't be too hard on audacity. Some don't like it here (Stochastic for example), but it is quite handy. I run it sometimes with jackd as the audio backend and I have very little bad to say about it. But I just use it for quick wav file editing, nothing else.

---

### Post by rab4567 on 2008-05-31
Don't get me wrong I want audacity to work natively with linux oss, alsa, pulse, and jack. I just put titles like the one above to get good feed back. My goal is to make all linux packages work together for the greater good, I'm taking the red pill!

---

### Post by rab4567 on 2008-05-31
Beware of the blue pill makers out there their readying their 7th version 2010.

---

### Post by Stochastic on 2008-06-01
> **rab4567 said:**
> Beware of the blue pill makers out there their readying their 7th version 2010.

Damn Sun Solaris, controlling everyone's mind with their little blue pills!

But in all seriousness, software comes down to personal preference (an a bit of logical decision making).  Your red/blue analogy is kinda off mark.

I see the validity in audacity, but there are lots of other basic wave editors around for linux (audacity is the most popular simply because it runs on Linux, Mac, and Windows, IMHO).  I don't hate it that much, I just steer clear of it because of the number of errors and bugs I've seen while using it.  But it all boils down to preference.

In the meantime, I've found a neat little trick that might help you get audacity working ```
pasuspender -- audacity
``` this will suspend pulse audio while audacity is running.

---

### Post by rab4567 on 2008-06-01
Oh! thanks a bunch, that saves me tons of time. As to the title of this thread its just a method to get peoples attention and get some fee back on this problem. You must believe me I really really like audacity but I hate the way I can not get it to work. You just threw open the door  for me and  others that are in audacity hell. As to the matrix movie references to the blue pill makers we're just poking fun at microsoft.

p.s. How do we reinstall pulse audio? I'm not a command line guru.

---

### Post by Aurora on 2008-06-01
> **thorgal said:**
> ...after A LOT of tweaking, cursing and sweating, I ended up with a very nice working audio setup for my music production...

Would you be willing to describe your setup, in terms of both hardware and software?  I haven't been able to re-purpose my M-Audio interface to work under Linux (with the requisite tweaking, cursing, and sweating), so I'm wondering what I could use instead.

Thanks,

Paul

---

### Post by thorgal on 2008-06-02
Hi Paul,

Here is a link to a description of my studio (with pictures) :
[http://linuxmusicians.com/viewtopic.php?t=101](http://linuxmusicians.com/viewtopic.php?t=101)

I am using debian sid as the main OS, compiled my own realtime kernel and tweaked various things, compiled a few other things, etc. I am a unix guy from the start, so I am not exactly the best person to be asked for a smooth transition from other OS'es to debian-like systems (like ubuntu). But I must say, my experience with UbuntuStudio has been rather negative but that was one year ago (was it based on feisty?), when I built up my PC. After two weeks, I wiped it out and installed 64studio (32bit version) which I upgraded to debian sid after not even one day since 64studio IS debian.

---

### Post by Aurora on 2008-06-03
Thank you so much.  It gives me something to shoot for; for now I have to be frugal.

Wow, we have veered off-topic.

I use Audacity on my MacBook to record my weekly guitar classes: [http://www.guitarforgrownups.com/gfg_classes.html](http://www.guitarforgrownups.com/gfg_classes.html)
Audacity works fine for that, but I don't have a portable interface.  I plug a cheap mic directly into the line-in, so it sounds...about like you'd expect.  Still using MacOS until I can figure out how to get Ubuntu to behave on a MacBook; maybe it would be easier with Debian?

There, back on topic, sort of.

--Paul in Seattle

---

### Post by thorgal on 2008-06-03
Hi Paul,

You have a MacBook ? why don't you stick to it ? OSX is quite neat in many ways :) And you have all these nice cross-platforms apps like jackd and ardour. I would rather not go the debian way. If you are not a unix / linux advanced user, it is quite hard, you would have to spend a few months as a linux beginner to start feeling a bit comfortable. That's the strength of Ubuntu, they have revamped debian so that linux can be more accessible to newbies. UbuntuStudio should be an extension of that concept ... debian is not at all. I really like debian myself but I've been using this OS for 7-8 years in various contexts (servers, physics research, and now music prod).

---

### Post by rab4567 on 2008-06-05
Nothing worked for me still in audacty hell I'm going to down grade to 1.2.7

---

