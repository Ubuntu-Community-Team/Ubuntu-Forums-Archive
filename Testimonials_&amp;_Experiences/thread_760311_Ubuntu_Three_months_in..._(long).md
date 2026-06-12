---
title: "Ubuntu: Three months in... (long)"
date: 2008-04-20
forum: Testimonials &amp; Experiences
---

### Post by rubboferraro on 2008-04-20
Well this is my second post on my Ubuntu experience. the other was a quite short, “Gee, Wow!” post:

[http://ubuntuforums.org/showthread.php?t=674784](http://ubuntuforums.org/showthread.php?t=674784)

Three months in and it has not been without a few hiccups, I even went back to Windows XP for a while. So here I want to express my reasons for my new resolute determination to stick with Ubuntu. Many might me surprised as to why I think Ubuntu will be absolutely necessary for the world to adopt in the near future.

Firstly though I must say I am a little tech savvy, only as a complete amateur enthusiast in computers though, and do realize that the majority of people don't have much of a clue as to how their computer works. They use Internet Explorer and Windows Messenger because they are there on their desktop, and will never download or install anything themselves, not fully understanding how. Ubuntu may not be for them – yet. I, on the other hand, do not find it difficult finding information from “Googling” or copying and pasting “sudo apt-get” in a terminal. For those of us who have a little bit of PC nouse, Ubuntu is a dream - a wet dream.

When I first installed Ubuntu, its simplicity, ease of use, incredible common sense, and functionality just overwhelmed me. As everyone here I'm sure can testify too and have heard it all before; simple installation, stable, no viruses, powerful applications out of the box, fully customizable, completely free etc. The list of awesomeness is just too long to state here (but maybe I will write one up one day :-)). Suffice to say, after using Windows for over ten years and dabbling with various Linux distros, Ubuntu is a real breathe of fresh air.

So, why did I got back to Windows XP?

Well, after getting over the initial “wow” factor and diving into actually pushing my computer to do all the work I wanted (and needed) it to do, I hit a few snags. Mostly this was due to unsupported hardware. Many are amazed by Linux's generic drivers that run everything and mostly they are great, but if you don't have drivers for your piece of hardware you are up **** creek without a paddle. 

My Sony handycam was not detected and I spent a good few days racking my brains over getting it to work. I eventually got it going but not without running Kino as root. I also record songs and could not get an acceptable sounding playback from the mic. I tried Sound Recorder and Audacity and both of them played back fuzzy and soft recordings.

I realize the Linux crowd is only 1% of the market but really, competition is so tough out there, if you are a hardware manufacture and you make Linux drivers you are pretty much guaranteed that 1%. 

I searched high and low for a scanner/printer that supported Linux. Some of the very expensive models had Linux drivers but I didn't need, or want to pay for, all the extra functionality. After some research I discovered that Ubuntu comes with HP drivers so I brought a cheap one even though it didn't say it had Linux support on the box. Considering how much competition vendors have in the printer/scanner market I would say a guaranteed 1% edge in the market would be worth the trouble.

“Hardware manufactures, make Linux drivers, you will sell more hardware!”

Unfortunately for me, after some use successfully, my scanner/printer starting printing only pages of full black. I mulled over my hardware frustrations using Ubuntu and as I had mission critical work to scan/print that day I had no choice but to reinstall Windows. 

This is where it gets interesting (and where I tried to avoid a lawsuit.)

I got gusty gibbon (7.10) off a computer magazine CD. In that same magazine it had a mega review of all the best software for 2007. This was the cream of the crop, the top of the ladder, the best software money could buy in every possible category.

So I decided that if I was going back to Windows I may as well have the latest and greatest. I left my CD's full of old software in the draw and proceeded to download (via torrents) all the highest rated software. I got all the essential software (and then some) that anyone might want or need; Office suites, CD/DVD burning apps, Video editors, Graphic editors, Web page design apps, etc. 

I literally downloaded and installed thousands of dollars worth of software – for free.

It was within a few weeks that I realized that Windows and my new software gave me more headaches than Ubuntu ever did. I won't mention their names but this “top shelf” software behaved rather poorly. 

The office suite constantly crashed, the CD/DVD burining app came with so much confusing bloatware I couldn't even find the option to create a multisession data disk, the anti-virus program slowed my (fairly new and powerful) computer to a crawl, and I experienced numerous other frustrations. 

I actually realized I preferred using the open source software that came with Ubuntu.

And then the final nail in the coffin. I had XP with Service Pack 2 on and all the latest updates. The anti-virus was so intrusive and resource hungry I turned it off temporarily. I then got a very nasty virus that usurped my PC and even attacked my anti-virus software when I tried to remove it. 

I had to reinstall Windows. Or did I?

I analysed my viable my options:

I get a Mac. Well the Mac OS is beautiful, but I could build myself a PC with exactly the same specs for half the price, and even then, where's all the software? 

I use Windows. Do I really want to follow the Windows upgrade path? I certainly don't want Vista. Even if I don't actually fork out thousands of dollars for all the software that I need, do I really want to feel guilty about using illegal software? Downloading dodgy torrents, and applying equally as dodgy cracks and serial keys? Do I want to live in virus hell, or worse, anti-virus software hell?

I use Ubuntu. Software is completely free. Updates are regular and easy to apply. I'm supporting a non commercial philosophy that helps those less well off than me. To name but a few benefits. And the negative; I may have to pull my finger out to get a few things working initially. But after these things have been ironed out the road should be much smoother.

Naturally, I put Ubuntu back on. I can honestly say my scanner/printer has worked perfectly without a glitch (I think it was the empty colour cartridge that spun it out) and my mic is recording with descent audio now.

Compare Encyclopaedia Britannica with Wikipedia. You'd be mad to pay thousands for the Britannica.

Likewise, if the world will adopt Linux, there will be more and more support and contributions to open source software, cultivating it to perfection.

Companies like Apple and Microsoft will always be limited to the contributions of their commercially viable small number of employees. If we all take on Linux the only limit to it's potential development will be the number of every person in the world.

So, to all you newbies (like me), stick with Ubuntu! Crash through those initial hurdles. You will always be up with the latest technology with the greatest of ease. In 4 days time I will get the latest OS on the market by clicking a button. What trouble and cash do I have to go through to get and run Vista?

Happy days Ubuntans!

Yours sincerely,
Lorenzo.

---

### Post by 3rdalbum on 2008-04-20
I know what you mean about anti-virus software sapping your CPU power. I went to a friend's house the other night. Her husband's computer was running like a snail... I eventually found that AVG antivirus was using 70% of the CPU and 80 megabytes of RAM.

As for your Sony camera problem, is this a camera that connects through Firewire? If so, you don't need to run Kino as root. You need to plug your camera in and then use "chmod" on the /dev/raw1394 file, to make it readable and writable by your user account (or by all):

```
sudo chmod a+rw /dev/raw1394
```

This is not done automatically for you, because Firewire has some serious security flaws. Now launch Kino and you'll be all set.

---

### Post by rubboferraro on 2008-04-20
> As for your Sony camera problem, is this a camera that connects through Firewire? If so, you don't need to run Kino as root. You need to plug your camera in and then use "chmod" on the /dev/raw1394 file, to make it readable and writable by your user account (or by all):

Code:

sudo chmod a+rw /dev/raw1394


Awesome! Yes, it is firewire, and I'll definitely give it a whirl when I get around to hooking it up again. I remember the whole process being quite a chore, there was one crucial bit at the end: unplug the firewire and plug it back in again. So simple, but it took me a few hours to find that out in the forums. It should not be so difficult next time.

Thanks for the tip, I'll use it.

Lorenzo.

---

### Post by karellen on 2008-04-20
> So I decided that if I was going back to Windows I may as well have the latest and greatest. I left my CD's full of old software in the draw and proceeded to download (via torrents) all the highest rated software. I got all the essential software (and then some) that anyone might want or need; Office suites, CD/DVD burning apps, Video editors, Graphic editors, Web page design apps, etc. 

what applications? can you name a few?....
> Compare Encyclopaedia Britannica with Wikipedia. You'd be mad to pay thousands for the Britannica.
:lolflag: that was funny. you cannot compare them. Britannica is written by scholars, teachers, people with PhD's in a particular field ;)
Wikipedia is "the encyclopedia that anyone can edit".
that says it all...;)

---

### Post by rubboferraro on 2008-04-20
> what applications? can you name a few?....

Well, there are a lot of programmers out there who spill their blood and sweat on these things so I will try to put it as nice as possible. 

I have not listed the free stuff that pissed me off (Internet Explorer 7, Windows Media Player etc.) only the pricey ones. These were all rated as the best of 2007 in my PC mag, and also of course the one's I tried:

**MS Office 2007. ** It looked awful on XP. As well as every time I opened Word an error warning would come up saying that it was going to retrieve a lost file because it wasn't shut down properly, then it simply opened up a blank page. I always closed it properly. I ended up putting OpenOffice on.

**Roxio Easy Media Creator 10 suite** I'd been using Nero for years but was just tired of the bloat. Well I think Roxio beat it for bloat. I was confused on how to burn a simple movie! This is the program that I couldn't find the multisession function in. I ended up downloading Express Burn, a totally free app.

Let's get this straight right now - I love simplicity. For me an OS has to get out of my face and let me do the things I need to do as easy and as obviously as possible. Mac's do this extremely well, and Ubuntu with Gnome, is almost as good (but it scores way more points for all the other reasons).

**Adobe Creative Suite** This little baby took ages to just fire up and sure if I was a professional it's probably worth the wait. I need to convert to PDF and Adobe Acrobat 8 Professional did the job, the best thing about it was it created good quality PDF's with a very small footprint. What was not so good was that it refused to embed copyright fonts. I ended up downloading PrimoPDF, once again a free app, which did it without complaint. Photoshop and Illustrator are great but GIMP will do everything I need. The patch to make it legit was a nightmare in itself, and in the end it was bit of overkill.

**Norton 360** Norton had declined as the number 1 antivirus software over the years but this mag said it made a major comeback with norton 360 and placed it as numero uno. Don't even get me started on the hell that this program put me through. I've never liked any antivirus software for that matter. Windows users need to rethink the whole way in which they deal with viruses. Perhaps virtual software or something. A program that constantly runs numerous services on every inch of your hard drive is just not ideal.

I'm trying to remember what I had on :-) 

There were a few programs (**AnyDVD, CloneDVD**) which I thought were great but I had to apply multiple patches (cracks) to get them working. You might say: why don't you just buy them? And I might say where does it end? Why don't you just use Ubuntu.

Of course I also used a lot of programs I did like but didn't think they were worth the price tag seeing that free open source stuff out there did the same job. I liked **Sony Sound Forge** for recording but Audacity did all I needed. 

I could go on and on but suffice to say in most cases I preferred the free open source alternatives and had I stuck with Windows it would have been Windows full of traditionally Linux apps. Then there's Windows itself of course: $200 for awesome stuff right out of the box: check out that in built CD/DVD burning, the awesome compression utility, the powerful word processor, the marvellous web browser etc. 

And to redeem myself of my stupid sarcastic insults I will say that for gaming Windows absolutely rocks. 

> Compare Encyclopaedia Britannica with Wikipedia. You'd be mad to pay thousands for the Britannica.

that was funny. you cannot compare them. Britannica is written by scholars, teachers, people with PhD's in a particular field.

Wikipedia is "the encyclopedia that anyone can edit".

that says it all...

I don't quite get what you mean here? Are you saying Britannica is a better resource? Because the beauty of Wikipedia is the references. Look at those references! some of them are even from Britannica. Or are you saying what I was saying: that masses of human beings can create something vast and wonderful and free a lot faster and better than a small company can that ends up charging a fortune for it?

Cheers,
Lorenzo.

P.S. To all you companies mentioned in my post - I only used your software for a shorter period than you grant free demo's. I do not download or use illegal software anymore. I am a reformed man.

Oh Christ, somebody... call my lawyers...

---

