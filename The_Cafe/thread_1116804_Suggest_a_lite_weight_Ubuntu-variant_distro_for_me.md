---
title: "Suggest a lite weight Ubuntu-variant distro for me"
date: 2009-04-05
forum: The Cafe
---

### Post by shuttleworthwannabe on 2009-04-05
This is a pc I have: IBM Thinkpad R31 128MB RAM, Pentium III 1GHz.

I want to use for (1) Word processing, (2) non-intensive spreadsheet and presentations, (3) Email, (4) Browsing, (5) Listening to music

Can you please suggest a light weight distro that will achieve those aims given these specs??

Much appreciated.

S

---

### Post by dragos240 on 2009-04-05
Xubuntu, is for you.

---

### Post by shuttleworthwannabe on 2009-04-05
I found Xubuntu (in Hardy flava) a bit sluggish. Also feels like a trimmed down version of GNOME?? no? How about another desktop environment??

---

### Post by pwnst*r on 2009-04-05
> **shuttleworthwannabe said:**
> This is a pc I have: IBM Thinkpad R31 128MB RAM, Pentium III 1GHz.

I want to use for (1) Word processing, (2) non-intensive spreadsheet and presentations, (3) Email, (4) Browsing, (5) Listening to music

Can you please suggest a light weight distro that will achieve those aims given these specs??

Much appreciated.

S

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by sisco311 on 2009-04-05
> **pwnst*r said:**
> [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

+1

or you can start with a [minimal installation]("https://help.ubuntu.com/community/Installation/LowMemorySystems") and then install your window manager of choice and your preferred apps.

---

### Post by Sealbhach on 2009-04-05
> **pwnst*r said:**
> [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Crunchbang has Abiword for word processing but it doesn't have spreadsheet or presentations.

You could install  Gnumeric for the spreadsheets, but I don't know of any lightweight presentation package... i.e. lighter than OpenOffice presentation.

---

### Post by ajgreeny on 2009-04-05
Have a look at the minimal installation and then add lxde as the desktop environment.  It is blindingly fast, appearing almost instantly after logging in.  If you have room on disk go for xubuntu and then add lxde to that.

For the clean install of minimal:-
Install lxde in Ubuntu minimal install
First you need to edit the /etc/apt/sources.list file add the following lines
For Hardy Users
```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```
For intrepid or Jaunty change the word hardy as appropriate.
 Start with ```
sudo aptitude install xorg gdm lxde menu synaptic firefox
```
then add whatever you want, eg alsa, pulseaudio, open office, flashplayer, java jre etc etc.
If you already have xubuntu, just edit sources.list as above and add lxde

---

### Post by cardinals_fan on 2009-04-05
With those uses, does it really have to be Ubuntu-based?

If so, I'll second the recommendation of a minimal install.

---

### Post by wolfen69 on 2009-04-05
i know that technically this is not an ubuntu variant, but [Mepis Antix]("http://antix.mepis.org/index.php/Main_Page") is a great lightweight distro based on debian. it should run decent on 128ram.

but why not get another stick of ram? i've seen old ram for $5. you could probably find an old computer and take the ram out. or go to a computer recycling center. they would probably give you one for free. there's really no excuse anymore for not having enough memory.

---

### Post by doorknob60 on 2009-04-05
Debian Lenny with LXDE IMO, very similar to Ubuntu (uses apt-get, synaptic, etc.) so you'll already know how to get around. EDIT: Post 666

---

### Post by shuttleworthwannabe on 2009-04-05
I am leaning toward an LXDE desktop--u-lite may be an option?? Let me also check out MEPIS AntiX; what desktop does MEPIS AntiX use?

---

### Post by sisco311 on 2009-04-05
> **doorknob60 said:**
> Debian Lenny with LXDE IMO, very similar to Ubuntu (uses apt-get, synaptic, etc.) so you'll already know how to get around. EDIT: Post 666

evil archer!!!!
no execute permissions, aaaaaaaaaahhhh
____________________________________________________
----------------------------------------------------

OP: how about [awesome]("http://awesome.naquadah.org/")

---

### Post by kevdog on 2009-04-05
How about just changing window managers instead of metacity/gnome?  e17 (which is great), Openbox/fluxbox come to mind.  You will be amazed how light weight they seem to make Ubuntu.

---

### Post by ArtF10 on 2009-04-05
> **ajgreeny said:**
> Have a look at the minimal installation and then add lxde as the desktop environment.  It is blindingly fast, appearing almost instantly after logging in.  If you have room on disk go for xubuntu and then add lxde to that.

For the clean install of minimal:-
Install lxde in Ubuntu minimal install
First you need to edit the /etc/apt/sources.list file add the following lines
For Hardy Users
```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```
For intrepid or Jaunty change the word hardy as appropriate.
 Start with ```
sudo aptitude install xorg gdm lxde menu synaptic firefox
```
then add whatever you want, eg alsa, pulseaudio, open office, flashplayer, java jre etc etc.
If you already have xubuntu, just edit sources.list as above and add lxde

Or have someone else get you LXDE+Ubuntu:  
[http://www.moonos.co.cc/?page_id=2](http://www.moonos.co.cc/?page_id=2)(choose the LXDE version):guitar:

---

### Post by Mehall on 2009-04-05
I say +1 to Crunchbang Linux.

I've ran it on systems about that "powerful", though I had a bit more RAM, so i don't know how Open Office would fair :/ but as others said, Abiword + Gnumeric, and just use OO.o for Impress if you really have to.

---

### Post by adamlau on 2009-04-05
Ubuntu Minimal + JWM SVN 456 w/o Xft + PCManFM + gamin will run fine on your box. Faster (lighter on resources, more responsive UI) then an LXDE-based system. Faster than Openbox-based Crunchbox.

---

### Post by jimi_hendrix on 2009-04-05
fluxubuntu

---

### Post by ghindo on 2009-04-05
Xubuntu Jaunty may be a bit faster/lighter than previous variants.  I'm not sure.  Give it a shot!

---

### Post by snowpine on 2009-04-06
My recommendation is CrunchBang linux (the best of the lightweight Ubuntu variants in my opinion) and another stick of ram. If you are stuck with only 128mb, your options are very limited, maybe Puppy linux. I really recommend 256mb minimum if you want to use "full featured" applications such as Firefox.

---

### Post by billgoldberg on 2009-04-06
> **shuttleworthwannabe said:**
> This is a pc I have: IBM Thinkpad R31 128MB RAM, Pentium III 1GHz.

I want to use for (1) Word processing, (2) non-intensive spreadsheet and presentations, (3) Email, (4) Browsing, (5) Listening to music

Can you please suggest a light weight distro that will achieve those aims given these specs??

Much appreciated.

S

Forget Xubuntu.

Just installed Slitaz on an Dell Optiplex PII, 192mb ram and it runs super fast.

Plays MP3 files OOTB. The default file manager is a bit strange if you are used to Nautilus, but PcmanFM is in their repositories.

The entire distro is 30mb large.

Video tour: [http://www.youtube.com/watch?v=GXZdjIhqNRs](http://www.youtube.com/watch?v=GXZdjIhqNRs)

---

### Post by caravel on 2009-04-06
The issue with that machine is the RAM.  Get 512MB in there if possible and Xubuntu will run ok.  As it is, you'd have to go for one of the lighter distros.

---

### Post by sertse on 2009-04-06
Minimal install. 

If a full featured, everything configured option is a must, I recommend AntiX. 

Debian / Mepis based, (way of "doing things" is similar to Ubuntu, similiary large repo etc) a customised IceWM as default desktop, and thus even lighter than CrunchBang's Openbox. Doesn't like too shabby either, (They made IceWM look good! imo)

---

### Post by shuttleworthwannabe on 2009-04-07
I checked out AntiX, and seems to fit the bill for now. I will give some feedback once I have tried it. Thanks a million to all for the suggestions!

S

---

### Post by shuttleworthwannabe on 2009-04-07
How about SliTaz?
is this debian or Slackware??

S

---

### Post by snowpine on 2009-04-07
> **shuttleworthwannabe said:**
> How about SliTaz?
is this debian or Slackware??

S

Neither. It is an independent project.

SliTaz 1.0 Stable should run okay on 128mb of ram, however, 160mb is recommended for the current Cooking version. There is a "loram" flavor that is supposed to work with less: [http://slitaz.org/en/get/flavors.html](http://slitaz.org/en/get/flavors.html)

I still recommend increasing your ram if at all possible. :)

---

### Post by shuttleworthwannabe on 2009-04-08
Getting more RAM: I totally agree with you; I have tried with numerous computer repair shops here--firstly they told me that the RAM on this machine uses DDR type sticks and will cost as much as replacing the laptop! Secondly, it is not available. Talk about 3rd World!

---

### Post by wolfen69 on 2009-04-08
let us know how antix works out.

---

### Post by cariboo on 2009-04-08
I run AntiX on an old Compaq PII 350Mhz with 256Mb of 30pin ram. Except for Firefox it runs quite well. I use Opera, not sure of the version, and for what the average computer needs it runs acceptably. It has the added bonus of being Debian based, so the differences are not to great between Ubuntu and AntiX.

Jim

---

### Post by shuttleworthwannabe on 2009-04-08
I see Mint Fluxbox was released earlier today..any idea if this is trimmed down bloat of ubuntu or not?

Yes, once I get to download AntiX, I will surely post back my experience.
Light browsers: How about Google Chrome for linux?? or even Aurora??
S

---

### Post by Twitch6000 on 2009-04-08
> **shuttleworthwannabe said:**
> I see Mint Fluxbox was released earlier today..any idea if this is trimmed down bloat of ubuntu or not?

Yes, once I get to download AntiX, I will surely post back my experience.
Light browsers: How about Google Chrome for linux?? or even Aurora??
S

Mint Fluxbox is trimmed down version of Mint is is decently fast,but I am not sure of the min. specs.

You should try something like debain+lxde or crunchbang.
Google Chrome currently can be run through wine,however it does not have a Linux version at this time.

---

### Post by sheshdd on 2009-04-08
i think there is an ubuntu distro that comes with fluxbox,can't think of anything lighter than that

---

### Post by john_spiral on 2009-04-08
I second Slitaz, you can't beat it for very old hardware. Try the cooking .iso uses the lxde wm, not bad looking. 

Install opera loads faster than the fox.

---

### Post by shuttleworthwannabe on 2009-04-09
Just installed AntiX8. It is better than XP or Ubuntu GNOME, but still sluggish. Problem is the Netgear card WG511 card and my Vodafone HUAWEI E220 USB modem both not working--so wireless is out. Ubuntu Hardy recognizes the E220 modem, but not the Netgear WG511 card--not sure how to get this working.

S

---

### Post by K.Mandla on 2009-04-09
> **dragos240 said:**
> Xubuntu, is for you.
-1.
> **pwnst*r said:**
> [http://crunchbanglinux.org/](http://crunchbanglinux.org/)
+1.
> **sisco311 said:**
> or you can start with a [minimal installation]("https://help.ubuntu.com/community/Installation/LowMemorySystems") and then install your window manager of choice and your preferred apps.
That's the best idea.

---

