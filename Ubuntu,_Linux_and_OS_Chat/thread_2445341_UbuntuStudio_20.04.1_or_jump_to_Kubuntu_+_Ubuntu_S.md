---
title: "UbuntuStudio 20.04.1 or jump to Kubuntu + Ubuntu Studio Installer ?"
date: 2020-06-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Nosphky on 2020-06-12
Knowing that 20.04 will be the last version to go with Xfce and with the 20.04.1 release coming closer in July, I am wondering if I should jump straight to Kubuntu 20.04 with Ubuntu Studio installed on top. It seems from the news postings that that has been the preferred solution of most of the devs for some time already.

I've been using UbuntuStudio for some 7 years and I've become used to Xfce DE. I take it that KDE Plasma 5 is 'better' than Xfce as far as the devs are concerned.

Does anyone have any experience of Xfce v Plasma or the use of the Ubuntu Studio installer on top of other flavours that they would be willing to share?

---

### Post by ajgreeny on 2020-06-12
If you are used to Xfce, why not use Xubuntu rather than Kubuntu and add the specific applications that make up Ubuntu-Studio to the standard installation.

I don't know what those applications are, I'm afraid, but it must be possible to figure out from a current studio installation.
Here's a list as a txt file of what would bw added to my Xubuntyu 20.04 if I installed the ***ubuntu-studio-core*** package.  I already have quite a good assortment of multimedia packages installed (vlc, audacious, audacity, handbrake, openshot, ffmpeg, audio-recorder) so they will not be listed here even if they're dependencies of the studio metapackage.

I hope this helps.

---

### Post by CatKiller on 2020-06-12
The main difference with Ubuntu Studio is that it uses the -lowlatency kernel by default rather than the -generic one. It's easy enough to install that in whichever flavour you prefer.

---

### Post by Nosphky on 2020-06-12
The UbuntuStudioInstaller ([https://ubuntustudio.org/ubuntu-studio-installer](https://ubuntustudio.org/ubuntu-studio-installer)) is a sort of one-shot super package for adding UbuntuStudio capabilities (functionality) to any official flavour of Ubuntu and one of its features is the ability to select subsets of functionality according to your needs.

Apparently the Plasma5 and Xfce have negligible differences in demands on RAM so the choice depends upon such subtleties as 'looks and feel' and 'ways of doing things'.  I haven't completely understood why the majority of UbuntuStudio devs are already using the Plasma5 DE.

I am hoping some of you can come forward with your opinions on the differences between the two DE's (and your prejudices, why not?).

Maybe I'll just have to make a live installation of Kubuntu to see Plasma5's 'ways of doing things'.

---

### Post by CatKiller on 2020-06-12
> **Nosphky said:**
> I am hoping some of you can come forward with your opinions on the differences between the two DE's (and your prejudices, why not?).

Xfce is a bit more basic, and Plasma has more bells and whistles. They're both very customisable. They're both performant. Plasma can have wobbly windows and a desktop cube without installing anything extra.

> Maybe I'll just have to make a live installation of Kubuntu to see Plasma5's 'ways of doing things'.

That would be my recommendation. And any others that you like the sound of. The default look is not the *only* look. It really is *very* customisable.

---

### Post by Nosphky on 2020-06-13
[QUOTE=CatKiller;13964943]Xfce is a bit more basic, and Plasma has more bells and whistles. They're both very customisable. They're both performant. Plasma can have wobbly windows and a desktop cube without installing anything extra.


Well thanks for that, CatKiller. I'd never heard of Wobbly windows or desktop cubes. I've checked them out on a couple of Youtube videos and I don't think they're going to excite me. I'm afraid I'm not a great fan of animations or customisation. About the only customisation I do is to set my desktop background to a plain blue colour - reminds me of the good old days of the MS BSOD !

I'm going to make that live installation of Kubuntu.

---

### Post by guiverc on 2020-06-13
Ubuntu Studio will use KDE yes, but not all of Kubuntu 20.04 LTS.

From *Ubuntu Weekly Newsletter  #630*

> **Ubuntu Studio 20.10 to Ditch the Xfce Desktop in Favor of KDE Plasma**

[COLOR=#333333][FONT=&amp]Marius Nestor writes that the release notes for Ubuntu Studio 20.04 LTS indicated that 20.04 was the last release of Ubuntu Studio that will use the XFCE desktop by default. Ubuntu Studio releases from 20.10 on will include KDE Plasma as it comes with better tools for graphics artists and photographers. Resource usage will remain as light as it was with XFCE for audio production, as the Akonadi server will not be running.

[https://9to5linux.com/ubuntu-studio-20-10-to-ditch-the-xfce-desktop-in-favor-of-kde-plasma](https://9to5linux.com/ubuntu-studio-20-10-to-ditch-the-xfce-desktop-in-favor-of-kde-plasma)[/FONT][/COLOR]


[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue630](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue630)

FYI:  I'd recommend reading the Ubuntu Studio release Marius' article is based on, but I was lazy & looked up UWN & just copy/pasted...

---

### Post by Nosphky on 2020-06-13
Thanks, Guiverc, for these leads. 
Over the next week, I'm going to try out Kubuntu and see for myself. I'm pretty sure whichever way I go I'll be able to do what I require of the OS.

---

### Post by Nosphky on 2020-06-14
Well ...  I did it. Made a live USB stick and tried out Kubuntu. First impressions were that it was very responsive but that the file manager looked a bit 'wireframe-ish' and insubstantial. I got it looking the way I wanted by moving the zoom setting but it took a while to find out where to make actions single click rather than double.

I didn't see any reason I couldn't live with Plasma but in the best interests of procrastination, I'll leave my decision until the .1 update release arrives in July.

---

### Post by CatKiller on 2020-06-14
> **Nosphky said:**
> I got it looking the way I wanted by moving the zoom setting but it took a while to find out where to make actions single click rather than double. 

There's a setting for if you want it different. 

> I didn't see any reason I couldn't live with Plasma but in the best interests of procrastination, I'll leave my decision until the .1 update release arrives in July.

:)

---

### Post by SeijiSensei on 2020-06-14
Procrastination can be good, but I'll just mention I worked my way through the 19.04, 19.10, and 20.04 versions of Kubuntu with nary a hitch.

---

### Post by guiverc on 2020-06-14
I'll post another link [https://www.youtube.com/watch?v=mh3SbbjfBnk](https://www.youtube.com/watch?v=mh3SbbjfBnk) you may find interesting..

BDLL (Big Daddy Linux (Live)) covered Ubuntu Studio 20.04 (it's a two hour show, the first ~50 mins was on Ubuntu Studio I think..

Erich Eickmeyer (of Ubuntu Studio) was there, and as I recall the move to KDE was touched on (Erich has talked about it before; possibly even on BDLL and recently too I suspect) but I was busy & heading out so didn't get to concentrate on the whole show...

---

### Post by Nosphky on 2020-08-17
Well, I duly procrastinated until the .1 release came out. Then I decided to make no decision but just go with UbuntuStudio XFCE 20.04.1 which I duly installed. I took advantage of the clean install to place my /home directory on a separate HDD and I tried to take all the necessary backups when moving from one release to another. 

Mostly, it all went well but still took a while to get all my non-distrib applications re-installed and my screen set up how I like it. One thing I did forget was to note the fix I applied to make Zotero launcher work from my Panel1. I reapplied the procedure on Zotero's website but the result is the same as I had on 18.04.1 a couple of years' ago. It doesn't work. Back in 2018, some months after the installation, I had some sort of inspiration which lead me to getting this launcher to work. Sadly for me, I forgot to make a note of it. So, I'll have to wait for another inspiration, hopefully in a few weeks' time.

In many small ways, the 20.04.1 version of UbuntuStudio was disappointing. In the Whisker drop-down application menu, the two columns had been reversed so my automatic mouse moves honed during more than 6 years now have to be reversed. This is the sort of change that I wouldn't have believed was worth a Dev's effort.

When I came to adjusting settings,  a lot of the old familiar stuff was missing - most important was the settings for software and updates. So I had to go 'terminal' to add PPA's. I suppose it must be present but hidden somewhere. I hope the software updater will remember that I want to be notified about updates and not to make them automatically.

There was no package manager so I had to install Synaptic. 

When I clicked on a pdf file to open it, I was taken to some cloud site in my browser. There appears to be no pdf reader present as basic so I've installed Evince Document Reader which has served me well over the years and which was previously in the US distro.

The next decision point will be around the end of the year when the next, non-LTS, release comes out - this will be Kubuntu + Plasma. Will I stick with LTS or not? Time will tell.

---

