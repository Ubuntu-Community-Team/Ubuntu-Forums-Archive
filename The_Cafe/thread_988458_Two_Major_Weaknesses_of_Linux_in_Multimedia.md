---
title: "Two Major Weaknesses of Linux in Multimedia"
date: 2008-11-20
forum: The Cafe
---

### Post by Doughy on 2008-11-20
I've been using Ubuntu for about 1.5 years now, and I really like it.  I believe the two major areas of limitation are:

1) Video editing.  I had to create a simple video yesterday and it was extremely frustrating.  I ended up installing 4 different programs, none of which really did the job well.  The only one that had the features I need kept crashing my computer completely and I had to reboot multiple times.  It was a miserable experience.

Are there any future plans for developing better video editing software in the future that you are aware of?

2) Print graphics.  Almost no programs in linux support CMYK color.  This is a major letdown for anyone trying to create graphics for printable media.  Hopefully the GIMP and Inkscape will address this soon!

---

### Post by Skripka on 2008-11-20
You missed one of the root problems.

LITTLE color management support to be found....it can be done--but it is anything but simple to do, IME.

---

### Post by Thelasko on 2008-11-20
[Cinelerra]("http://cinelerra.org/")

[CMYK]("http://cue.yellowmagic.info/softwares/separate.html")

---

### Post by snova on 2008-11-20
> 2) Print graphics. Almost no programs in linux support CMYK color. This is a major letdown for anyone trying to create graphics for printable media. Hopefully the GIMP and Inkscape will address this soon!

Krita supports CMYK. It supports just about every colorspace there is.

Some people tout Krita as better than The GIMP, but I can't compare them.

---

### Post by binbash on 2008-11-20
I agree with #1.There is not a pro software like Sony Vegas(windows).

---

### Post by Sephoroth on 2008-11-20
> **binbash said:**
> I agree with #1.There is not a pro software like Sony Vegas(windows).

Well there is Autodesk's IFFFS but I doubt many people would resort to it.

---

### Post by Thelasko on 2008-11-20
> **binbash said:**
> I agree with #1.There is not a pro software like Sony Vegas(windows).

Never heard of Sony Vegas, all the pro's I know run [Avid]("http://en.wikipedia.org/wiki/Media_Composer").

---

### Post by adaptr on 2008-11-20
> There is not a pro software like Sony Vegas
You think Sony Vegas is "pro software" ? Wow.
Look into Avid, Shake, and other near-realtime editors/compositors.

---

### Post by Frak on 2008-11-20
> **adaptr said:**
> You think Sony Vegas is "pro software" ? Wow.
Look into Avid, Shake, and other near-realtime editors/compositors.
I can haz Apple Logic Studio? Oh, and Apple Final Cut Pro?

---

### Post by zmjjmz on 2008-11-20
What programs did you try?

I had to edit video twice. One time I used KDEnlive, and the other time I made the actual video in Flash 5 in WINE, then tried to sync sound to it (failure), and then I ended up editing it in iMovie on my brother's computer.

---

### Post by tvtech on 2008-11-20
> **Thelasko said:**
> Never heard of Sony Vegas, all the pro's I know run [Avid]("http://en.wikipedia.org/wiki/Media_Composer").

all the pro's I know are dumping avid for FCP  

seriously who can beat a 15000 dollar full blown graphics suite?

oh yeah and by the way.  kino works just fine. it even detects my lovely little video cam and controls it fairly well. it's not quite as glamorous as FCP or some of the Adobe stuff out there but... I"m making home movies here, if I was a professional I wouldn't be playing with nix, I'd be on BSD i.e. MacOSX

---

### Post by Frak on 2008-11-20
> **tvtech said:**
> all the pro's I know are dumping avid for FCP  

seriously who can beat a 15000 dollar full blown graphics suite?

oh yeah and by the way.  kino works just fine. it even detects my lovely little video cam and controls it fairly well. it's not quite as glamorous as FCP or some of the Adobe stuff out there but... I"m making home movies here, if I was a professional I wouldn't be playing with nix, I'd be on BSD i.e. MacOSX
Aye, I use FCP for all my needs (except the simple ones, where iMovie is just fine, which is about 90% of the time :P)

---

### Post by Swagman on 2008-11-21
I used to video weddings etc and built my own NLE machine when P2's were the Beez Kneez. (£400 for a 4 gig scsi drive)

I learnt NLE editing with [**MediaStudio Pro**](http://www.ulead.com/msp/runme.htm) because that's what came with my horrifically expensive NLE card. I tried naughty versions of other NLE's over the years but apart from [**MainActor**](http://www.labdv.com/review/software/mainactor-en.html) and Sony Vegas I always came back to what I was familiar with.

I hated Adobe Premiere
Couldn't afford Lightwave suite.

I wish I had bought MainActor now as they had Amiga roots and supported Linux as well. Unfortunately I wasn't into Linux back then as I was a die-hard Amigan who only used Windows begrudgingly because of NLE.

I find Cinelerra, Kino etc awkward to use as well but I guess thats just just I learnt with MSP and I think thats probably the crux of the issue for most people.

---

### Post by Thelasko on 2008-11-21
> **Swagman said:**
> I find Cinelerra, Kino etc awkward to use as well but I guess thats just just I learnt with MSP and I think thats probably the crux of the issue for most people.

I learned linear editing first.  After doing linear editing, I'll take just about any functional non-linear system without many complaints.

My first experience with a non-linear setup was on a Mac G4 with Adobe Premier back in 2000.  People I knew who had used other systems (namely Avid) said it was terrible.  I thought it was the greatest thing since sliced bread.

---

### Post by Ubuntiac on 2008-11-22
I've been using the KDE4 version of Kdenlive for working on my stuff. Works nice with HDV although there's still the odd kink here and there. There's a GUI wizard called the "Kdenlive Builder Wizard" at kdenlive.org's forums that lets you have the current SVN version easily enough, and from the look of it developments coming along nicely. I've had a number of bugs fixed in days.

The main problem is that if you don't want to install from source or with the Builder Wizard that you need to add repo's and possibly backports.

If you're on Kubuntu, you can add it from the Debian-Multimedia.org repositories, but if you're on Ubuntu you need to enable and update backports first. I'd rather not enable backports either which is why that link is in my signature. ;-)

---

### Post by 3rdalbum on 2008-11-22
My father is a typesetter. He really needs bitmap support in The Gimp. I'm not talking about Windows .bmp files, I'm talking literally 1-bit colour files. Black and white. Also known as "line art". Everyone makes a big deal about missing CMYK support, but professionals are missing something even more basic.

As for video editing, I like Kdenlive, but I can't get Kdenlive 0.7 to work properly on Ubuntu 8.10 and version 0.6 is unstable. It's also not capable of doing much in the way of compositing unfortunately. But it's a promising project.

---

### Post by Rokurosv on 2008-11-22
I think that the lack of any flash creation software is a big issue in Linux too.

---

### Post by Greyed on 2008-11-22
I'd be content with anything that doesn't limit me to broadcast formats.  I wanted to put together a video that would only be played on computers and all of the video editing software I found for Linux (Kino, KDEnlive, Cinelerra) insisted on wanting to cram it into some broadcast ratio.

---

### Post by Ubuntiac on 2008-12-15
@greyed - You could be forgiven for missing it, but Kdenlive 0.7 let's you render to whatever aspect ration you like. Yes the initial *Project Settings* make you choose a preset, but when you render you can either create a new profile that uses any height and width, or choose one of the presets, click the "i" button to see advanced info, then click the edit profile button and change the values of size (eg size=720x480). On some codecs instead of size= you'll just see s=.

Hope that helps!

---

### Post by Phreaker on 2008-12-15
Another major weakness is a lack of a good DAW

---

### Post by Ubuntiac on 2008-12-16
Have you tried both Ardour and Rosegarden?

---

