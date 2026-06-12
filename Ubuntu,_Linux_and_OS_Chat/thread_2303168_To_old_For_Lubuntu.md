---
title: "To old For Lubuntu?"
date: 2015-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Gibson295 on 2015-11-16
So i got this Old Dell Latitude laptop, has to be 10 years old at least, maybe a little older. Got it for free from work, they just gave it away, and My recent 5 year old laptop quit, and i'm on a tight budget so i figured Meh, Why not. I also have a main tower so anything big that i need to do would be done on that. Anyways Very seldom used computer solid, practically new shape, looks and feels like it would of been a decent business model laptop at the time. Still has Windows XP On it, Decided i'd try dual booting Lubuntu on it, everything works nicely now after hitting a-lot of bumps in the road, however she's a slow old bat, and part of me thought it might be a bit quicker with a Lighter Operating system. And that's where Lubuntu came in, or so i kind of thought.

Everytime i go into the internet browser, weather it's Firefox, or Chrome. I find she slows down quiet a bit, While watching the ram useage i am however rather impressed that with nothing open the system is only using less then 150mb of ram, where as the Windows XP witch also had tied to it avast Anti-virus, was using 300-350MB range with nothing else going. Popping up Google chrome or Firefox on Windows XP would shoot the ram up to near max of what what is available on this sytem. In Lubuntu on the other hand she hardly ever goes over 500mb with either OS's open. Basic uses like hotmail and all that though still see oddly slower then i expected though, Maybe it's just me being used to my other computers being alot faster and newer. When i say newer i mean one now dead 5 year old laptop witch ran a 1st Gen i3 dual core with 4gbs of ram and 1gb dedicated graphics, and a almost 3 year old tower that bears a 3rd gen i5 quad, 16gbs of ram and 2gb dedicated gfx card. Enough about that though, The Old laptop i got that i speak of is a Dell Latitude D520 witch has a 15.4 Inch 1024x768 LCD screen a Intel celeron 2.40Ghz cpu based on Older P4 chips, and 1GB of DDR/333 Mhz memory witch is the MAX it can support. As for graphics, Some Intel 8000 thats all i can say for gfx. Anyways i was thinking i'd get Just Basic light Internet browsing out of it, Foolish me i was even hoping i could watch a youtube video every now and then. I have Pretty decent internet connection (20MB) I can stream 1080p videos on pretty much everything in the house. That being said i sure didn't expect this to do better then 360p Witch is fine! i can accept that, but Frankly this computer runs off my wi-fi almost darn near dial-up speed!  I think i over estimated how low i could go for basic use on hardware requirements, I have a reason to believe that awful old Celeron chip being at 100% use for every little mouse click is probably the root problem here, but doing anything else aside from Internet browsing it seams decent snippy at times, Especially for some Much Older games (Makes a nice machine For DosBox titles in XP) Very Quick for Basic office use without doing anything in the internet browser on BOTH Operating systems, even quicker in Lubuntu. 

I have to wonder why i'm having such a slow/cluttery experience though beyond the old hardware, I say this because i've Ran Windows XP SP3 on a HP Pavillion from 2003 that had 1GB Of DDR/400 Ram in it and a 2.2Ghz AMD Sempron single core, and a ATI Xpress 200 series onboard chip. That computer i could even watch 480p Youtube streams on without a problem!!:D i could only imagine how much better it would of been with Lubuntu, if i still had it, I sold it to an old lady for 50$ back then. Hell i used to play World of warcraft on that computer faster then this laptop can load an email page, that was years ago of course.:o

I've rambled a bit much, but does anything think this old dell latitude is just completely useless and ready for the Recycling bin, or should i hit up the support forum and see if i can get answers as to why She is so slow when running the Internet.

By the way i am new to the forum, My apologies if this doesn't sound like a General chat type thing. Just getting into subjects that interest me, i like old and new tech.
When i get bored i tinker around, Why else would anyone want this old thing haha:D

---

### Post by Sweet_Baby_Jamie on 2015-11-16
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

This might explain alot for you.

---

### Post by Gibson295 on 2015-11-16
Perhaps. But i'm experiencing a memory problem. I do have a 500MB swap partition that its using. and a 20gb partition that the os is installed on.
Its just pretty slow on the internet, on a 20MB connection doesnt make sense when my other computers are fine.

---

### Post by Bucky Ball on 2015-11-16
This is not a support area of the forum. I agree: post a (abridged) support request in the 'Networking and Wireless' area about your issues with slow network connections. You might like to check the third link in my signature for the most effective approach to posting to get your support request dealt with and include the output of this command with your post to get the ball rolling.

```
sudo lshw -C network
```

Good luck.

PS: You answered your own question prior to posting, incidentally. Lubuntu appears to be working just fine, the only issue you're having is slow internet, so no, your machine is not too old to run Lubuntu. You're running it. :)

---

### Post by help_me2 on 2015-11-17
I would try Puppy Linux on it.

---

### Post by mastablasta on 2015-11-17
problem areas identified form the rambling and after removing the unnecessary info:

- wi-fi chip drivers support  - try wired see if it's faster. if it is then try troubleshooting wi-fi
- GPU drivers support - do the drivers get 3D out of the chip or only 2D or some software mode. if 3D is done in software mode it would tax the CPU a lot (slowdown)

tip: 1 GB ram  - swap should be 1 GB or more

---

### Post by nik0laus on 2015-11-20
Try  ToriOs  , 
I gave new life in a far weaker laptop than yours with this minimal distro.

---

### Post by Mike_Walsh on 2015-11-26
I agree with help_me_2.

I have an even older Dell Inspiron from 2002/3.....an original Inspiron 1100. It started life with a 2.2 GHz Celeron (P4-gen), and just 128 MB of RAM. It also had a 20 GB HItachi Travelstar HDD. It ran (what else?) XP. And it was **SLOWWW**.

I increased the RAM to the max of 1 GB. I upgraded the Celeron to a 2.6 GHz P4; you **can** do this, because Celerons/P4's in Dell laptops of that era used the desktop CPU; these sit in a proper ZIF socket, rather than soldered to the board, as the BGA form factor was. Cost; about £6 (US$10) off eBay. And that Travelstar has been upgraded to a 32 GB Transcend PATA/IDE SSD.  Total upgrade costs.....about £50, over approx. 2 years.

Each component has made a small improvement by itself; taken all together, they've transformed the old girl. It now dual-boots Xubuntu 14.04.3 LTS, and Puppy 'Tahrpup' 6.03. 

Xubuntu runs OK, it's a wee bit 'stately', but definitely usable.. I haven't got around to dialing the swappiness down, yet. But Puppy; well, it **flies**.....

If you're interested, you can get it from here:-

[http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/)

Download, burn to disc, run as a LiveCD in the usual way. Then, install if you want. Your best one would be the second entry from the bottom, the no_PAE version. Puppy runs entirely from RAM, so even on elderly hardware, its performance is acceptably sprightly.

I agree with mastablasta, though; whatever Linux distro you use, you need at **least** as much 'swap' space as you have RAM. And the 'buntu's **do** benefit from having the 'swappiness' factor dialed down to around 10, as opposed to the default 60.

Hope that helps.


Regards,

Mike. ;)

---

