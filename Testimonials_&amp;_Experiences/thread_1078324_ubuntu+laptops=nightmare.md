---
title: "ubuntu+laptops=nightmare"
date: 2009-02-23
forum: Testimonials &amp; Experiences
---

### Post by NeferalCrossfireX on 2009-02-23
ubuntu just isnt a good o/s for laptops, 8.04 and 8.10 wont even boot from the live cd, it just stays in verbose mode, 9.04 alpha 4 boots into gnome, but dosent support the touchpad. yet opensuse works perfectly, its just kind of sad really.:(

---

### Post by kidux on 2009-02-23
I have it running on my laptop, and it's fine except for a few minor issues. When I had 8.04, the sound would die upon resume from standby, and 8.10 has locked up a couple times resuming from standby.

---

### Post by amauk on 2009-02-23
chances are it's mis-identifying your graphics card
pressing F4 on the menu will allow you to boot using the VESA drivers (safe graphics mode)

install & update
hopefully this will pull down any fixes for your card

---

### Post by tombott on 2009-02-23
> **NeferalCrossfireX said:**
> ubuntu just isnt a good o/s for laptops, 8.04 and 8.10 wont even boot from the live cd, it just stays in verbose mode, 9.04 alpha 4 boots into gnome, but dosent support the touchpad. yet opensuse works perfectly, its just kind of sad really.:(

I do love these sweeping statements.
So Ubuntu doesn't work on your laptop, therefore it's not good for any laptop?
Here's an idea for you, why not post the make and model of your laptop, file a bug report etc. 
That way somebody might address the issue for you.

---

### Post by NeferalCrossfireX on 2009-02-23
> **amauk said:**
> chances are it's mis-identifying your graphics card
pressing F4 on the menu will allow you to boot using the VESA drivers (safe graphics mode)

install & update
hopefully this will pull down any fixes for your card

ive tried that but it still stays in verbose mode except for the jaunty alpha, i'm using opensuse on it now which does the job fine

---

### Post by NeferalCrossfireX on 2009-02-23
> **tombott said:**
> I do love these sweeping statements.
So Ubuntu doesn't work on your laptop, therefore it's not good for any laptop?
Here's an idea for you, why not post the make and model of your laptop, file a bug report etc. 
That way somebody might address the issue for you.

actually it dosent work on any laptop ive ever tried, so its not just a sweeping statement

---

### Post by simtaalo on 2009-02-23
i've used 8.04+8.10 without any problems on my hp laptop.

it is a sweeping statement if you look at how many users on this board are running ubuntu on their laptops, even their macbooks :P

i just installed 8.10 onto an old p4 laptop yesterday and that worked fine, i've installed ubuntu onto many other friends laptops, a range of makes/models and there has never been any problems not even with wireless.

so either its a sweeping statement, or you just can't install for toffee ;)

---

### Post by issih on 2009-02-23
Tis the way with laptops, they tend to use more non-standard hardware, so the quirks of kernels and such like become more important. Some laptops will work with one distro, some with another, its not that ubuntu is bad with laptops, its that out of the box its bad with YOUR laptop, thats all. I would bet there will be a laptop that suse is rubbish on and for which ubuntu works perfectly.

Unless you get all the laptop manufacturers to release device drivers for all their machines written for linux (like they all do for windows), then this will always be the case.

If you want to avoid the pain, then ask people what they use and works, or buy a dell, ideally one they sell preinstalled with ubuntu, but honestly, its not that the OS is bad, its just the nature of the market and the reality of driver availability.

Oh and for the record, I am running it on a macbook, and have used it on a packard bell mv35202 and an ancient hp ze5200 laptops, all worked, sure there were quirks to iron out (usually wireless or sound), but they worked, so you are definitely the exception here

---

### Post by tombott on 2009-02-23
> **NeferalCrossfireX said:**
> actually it dosent work on any laptop ive ever tried, so its not just a sweeping statement

lol, right.
Still no make / models etc?
People here are willing to help, but when you provide no information its a bit hard to do so.
So as I've installed Ubuntu on at least 50 laptops I can say it works and isn't a nightmare (this is following your rational by the way).

---

### Post by NeferalCrossfireX on 2009-02-23
> **tombott said:**
> lol, right.
Still no make / models etc?
People here are willing to help, but when you provide no information its a bit hard to do so.

makes:
samsing r60plus - wont boot into gnome except for jaunty alpha, and dosent support the keypad

acer aspire 5670 - boots but dosent support the touchpad and sound dosent work, wont work in the proper resolution.

gigabyte g5 - stays in verbose mode whichever version you use

thats three that dont work, i cant remember the exacts models of the others, but generally in my experience ubuntu just dosent work well with laptops

---

### Post by anthonie on 2009-02-23
Well, I´m afraid I´ve had quite a few laptops in my hands as well and the recent versions of Ubuntu don´t seem to work very well. I installed 8.10 on my ASUS X50GL, which went quite smoothly, but to say it´s a stable system would be a gross misinterpretation. Frequent lockups, shaky multimedia and silly little things like my machine not doing power-down.

---

### Post by TenPlus1 on 2009-02-23
I have a Compaq Presario M2000 and it just loves Ubuntu...  Everything worked fine apart from the wintel modem, but a quick download managed to sort that too...

---

### Post by Teamgeist on 2009-02-23
The touchpad will work.

You will have to install the xserver-xorg-input-all package which is missing from the Alpha4 Live-CD as stated in the release notes.

> The X.Org synaptics driver is absent from the liveCD, which may prevent touchpad devices from working on laptops. As a workaround, use Ctrl+Alt+F1 to switch to console, log in, run sudo apt-get install xserver-xorg-input-all to download the drivers from the network, and then return to your session with Alt+F7.

[http://www.ubuntu.com/testing/jaunty/alpha4](http://www.ubuntu.com/testing/jaunty/alpha4)

```
sudo apt-get install xserver-xorg-input-all
```

Have fun, but remember it still is Alpha software, meaning that it is supposed to break.

---

### Post by stalkingwolf on 2009-02-23
I have installed 8.04 on 2 HPs,1 Toshiba, 1 EEE PC, several Dells,(C400 &600's and a D400 as i recall),and an Everex step note.  The Everex
was a general PITA.  I threatened to through it out in the road and let a truck run over it several times.  I have even had it run quite well with only 256mb of ram.

When I have had trouble with a Live CD not loading Usually it comes back to
1 The drive doesnt like that brand of media
2  The drive is either getting flaky or needs to be cleaned.
3 Drive speed ( my 8X DVD just wont work)
4 Bad disk ( mine get a lot of use, so get scratched up regular).

Solutions
I have found a brand of media that seems to work for everything.
I have a cleaning disk and a can of air for cleaning drives.
I also have a USB CDRW that I plug in if necessary.  Worst case I pull
the HDD and plug it into My laptop and do the install.  Then reinstall it.
So far I have only had to reconfigure the display settings once.

The everex was a PITA from the off. Unichrome pro display adapter.  Finally got that configured, never got the modem to work, used a serial instead.  Had dial up setup and connected in about 5 minutes.

Next project I am going to put either puppy or DSL on an old (read ancient) Fujitsu lifebook.

---

### Post by aysiu on 2009-02-23
> **tombott said:**
> 
People here are willing to help, but when you provide no information its a bit hard to do so. The OP didn't ask for help, and this is not the support part of the forums.

Why are people always so excited to help people who write posts slamming Ubuntu?

Please read [this](http://ubuntuforums.org/showthread.php?t=634322).

---

### Post by Maheriano on 2009-02-23
I installed it on a Dell D600 and everything worked fine, even the Fcn buttons and the volume buttons.

---

### Post by teeleef on 2009-02-23
Try pressing f3 and adding noapic nolapic to the boot setup.

It has worked with all the laptops I've setup.



Teeleef

---

### Post by solwic on 2009-02-23
> **aysiu said:**
> The OP didn't ask for help, and this is not the support part of the forums.

Why are people always so excited to help people who write posts slamming Ubuntu?

Please read [this](http://ubuntuforums.org/showthread.php?t=634322).

Ah, aysiu...I'm so disillusioned now.  I've visited your site and know you to be a person who wants to help.  Then you link to posts like your "plea", and it sends such a contrasting message.  

:(

---

### Post by lykwydchykyn on 2009-02-23
So cutting through the overhyped subject, the question remains: why does it work on opensuse, but not ubuntu?  That would be a question worthy of coming to the bottom to.

Of course, the best place to do that would be launchpad, not ubuntuforums, IMHO.  ;-)

---

### Post by dBuster on 2009-02-23
Sweeping statement here....

Every laptop I have tried which is 11 or 12, I don't keep track, runs Ubuntu rather well!  No issues with installation or updating.  Did have an issue with the latest one but there are solutions to get that resolved.  

No nightmare...

---

### Post by wolfen69 on 2009-02-23
> **NeferalCrossfireX said:**
> actually it dosent work on any laptop ive ever tried, so its not just a sweeping statement

yes it is a sweeping statement. i have my own pc repair business, and have yet to see a laptop that *won't* run it. and that my friend, is *alot* of laptops.

anyway, just because it does not run on yours, doesn't mean you can't run linux. there are many distros out there besides ubuntu. try one of them.

---

### Post by Dayylin on 2009-02-23
I dropped Ubuntu on my laptop and haven't had a problem. Have also installed in on several different laptops for other people without the hassles that you seem to be encountering.

---

### Post by anthonie on 2009-02-23
Perhaps people could make a habit of it to mention the actual version of Ubuntu they are trying to install. 

In my experience, only the 8.10 version has problems that I have not been able to tackle. All older versions of Ubuntu ran flawless and I have installed them on anything ranging from an old PIII notebook to my latest X50GL Asus with 4 gigs of RAM. 

Installing 8.10 on my most recent machine ran into problems so I started with an older version and upgraded from that. 

So, please mention a version so other people can actually see what you are talking about.

@Dakomata

Freeware as in? The OS is free to download (you can even request a free CD to be send over to your house if you like).

---

### Post by wolfen69 on 2009-02-23
> **dakomata said:**
> is ubuntu a freeware?

see this my friend. [http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by aysiu on 2009-02-23
> **jrock612 said:**
> Ah, aysiu...I'm so disillusioned now.  I've visited your site and know you to be a person who wants to help.  Then you link to posts like your "plea", and it sends such a contrasting message.  

:(
Please re-read the plea again. I'm certain you've missed the point of it.

I'm all for helping those who ask for it.

If someone asks for help and gets no help then, why should that same person get help when she writes a rant bashing Ubuntu? But that's exactly what happens. I guarantee you this thread would have gotten far fewer responses if it had said "Laptop boots up Ubuntu only in verbose mode" instead of "ubuntu+laptops=nightmare"

---

### Post by Tews on 2009-02-23
> **aysiu said:**
> Please re-read the plea again. I'm certain you've missed the point of it.

I'm all for helping those who ask for it.

If someone asks for help and gets no help then, why should that same person get help when she writes a rant bashing Ubuntu? But that's exactly what happens. I guarantee you this thread would have gotten far fewer responses if it had said "Laptop boots up Ubuntu only in verbose mode" instead of "ubuntu+laptops=nightmare"

+1

If this were a legitimate request for help, it would have/should have been posted in the General Help forum.  As it is, I see this as typical flame bait ... just my opinion though ..

---

### Post by stchman on 2009-02-23
> **NeferalCrossfireX said:**
> ubuntu just isnt a good o/s for laptops, 8.04 and 8.10 wont even boot from the live cd, it just stays in verbose mode, 9.04 alpha 4 boots into gnome, but dosent support the touchpad. yet opensuse works perfectly, its just kind of sad really.:(

I have Ubuntu on (2) laptops with no problems.

Toshiba Satellite - 8.04
Acer Aspire One - 8.10

What kind of laptop do you have?  Did you try safe graphics mode?

---

### Post by trepid666 on 2009-02-23
I've had Ubuntu running on my laptop for about 3 or 4 years now. I think it's great. Runs/installs way better than window$ xp ever did

---

### Post by NeferalCrossfireX on 2009-02-23
what the hell is wrong with some of you?
can people only post comments about how utterly perfect ubuntu is? well guess what it isn't! its the best o/s i've ever used but it has its drawbacks, the same as windows/mac or whatever.

i posted an experience ive had in the testimonials and experiences section, which as far as i can work out, is exactly where it belongs.

and yes ive tried all the things suggested but still no luck, and theres nothing wrong with any of the install discs as they work fine in desktop machines soo:p

---

### Post by stchman on 2009-02-23
> **NeferalCrossfireX said:**
> what the hell is wrong with some of you?
can people only post comments about how utterly perfect ubuntu is? well guess what it isn't! its the best o/s i've ever used but it has its drawbacks, the same as windows/mac or whatever.

i posted an experience ive had in the testimonials and experiences section, which as far as i can work out, is exactly where it belongs.

and yes ive tried all the things suggested but still no luck, and theres nothing wrong with any of the install discs as they work fine in desktop machines soo:p

I have never once said Ubuntu is PERFECT.  Ubuntu has it's flaws.  There is no perfect OS.  I simply compare flaws from one OS to another and find Ubuntu to have flaws that I can tolerate much better.

As far as your laptops, did you try creating an Ubuntu bootable USB flash drive?

Maybe your .iso you downloaded is corrupt.  Did you check the MD5 sum on the .iso?  I burn the .iso at about 16X when creating a CD.

Refer to my tutorial about creating Ubuntu CDs.

[http://www.stchman.com/create_cd.html](http://www.stchman.com/create_cd.html)

Hope this helps.

---

### Post by wolfen69 on 2009-02-23
if it doesn't work, it doesn't work. get over it and install what works on it. geez. 

i don't know why some people are so dead set on installing ubuntu. i love the hell out of ubuntu, but it is not the best for every computer on the planet! try another distro, use windows, blow your nose, hold your girlfriends hand, but for the love of god, get over it.

---

### Post by Telekinesis on 2009-02-23
Ubuntu+HP ZD8000=Wonderful.

Most of the time, I think the "Ubuntu doesn't work on insert here" posts are just made by people who don't know what they're doing and they get frustrated. That might not be the case with the laptops this person has tried, but I'd be willing to make a bet that I could get it running on all three of them. ;)

---

### Post by 3/31 on 2009-02-23
Aside from your tone, I must agree.  If Ubuntu simply does not work, try something else.  

You would not keep trying to put a flat tire on your car, would you?

> **wolfen69 said:**
> if it doesn't work, it doesn't work. get over it and install what works on it. geez. 

i don't know why some people are so dead set on installing ubuntu. i love the hell out of ubuntu, but it is not the best for every computer on the planet! try another distro, use windows, blow your nose, hold your girlfriends hand, but for the love of god, get over it.

---

### Post by zero244 on 2009-02-23
I dont what distro I would be using if not Ubuntu.
Ubuntu has the best repositories around.

Ive installed Xubuntu on a couple of dell laptops. Except for a couple of keys not working it worked very well overall.
You might give NOP Puppy Linux 4.12 a shot. Its a derivitive of Puppy not the official release. I use it a lot on this computer along with Ubuntu.
You can do a frugal install of puppy on the same partition with Windows or Ubuntu.
Its just a matter of copying a few files into a folder and run the OS from that folder.
Good luck.

---

### Post by kidux on 2009-02-24
I'm in agreement with Neferal and asiyou. This wasn't an OMGICAN"TGETITTOWORK post, it was I've tried all this, and this is what I determined from my experiences. Those who A)are bashing and almost blatantly calling Neferal stupid need to leave, and B)offering help, while I'm sure is appreciated, is not needed here.

---

### Post by Radioman991 on 2009-02-25
> **NeferalCrossfireX said:**
> ubuntu just isnt a good o/s for laptops, 8.04 and 8.10 wont even boot from the live cd, it just stays in verbose mode, 9.04 alpha 4 boots into gnome, but dosent support the touchpad. yet opensuse works perfectly, its just kind of sad really.:(

UH...I run both...8.10 on a Dell D610, and 8.04 on an Thinkpad T43....from an external USB drive, no less.  I used to run 8.10 on this laptop, but had a need to roll back.

Using the Dell lappy now to post this reply.  From where I sit, it's a fine OS for laptops.   I'll be connecting my Dell to the 42" LCD tonight to watch a little Hulu.com.

YMMV

PK

---

### Post by jbysmith on 2009-02-25
> **wolfen69 said:**
> if it doesn't work, it doesn't work. get over it and install what works on it. geez. 

i don't know why some people are so dead set on installing ubuntu. i love the hell out of ubuntu, but it is not the best for every computer on the planet! try another distro, use windows, blow your nose, hold your girlfriends hand, but for the love of god, get over it.

Heh well put, and dead on. 

I love Ubuntu on my servers; it just plain works without complaint or problem.  

For my personal desktop I'm using Arch.  I found that Arch just suits my needs better on the desktop level than Ubuntu did.  Feisty was excellent, but I wasn't thrilled with it from Gutsy through Intrepid. Granted, the 9.04 daily builds have me *really* tempted to switch again.

I've found openSUSE to be excellent, PCLinuxOS, Fedora, Debian, Mandriva, Vector etc etc.. all worthy of checking out.  Can't just try one distribution and rate Linux as a whole just on that.  They're the same, but also very very different.  Different ways of doing things, different "philosophies", different target audiences.. 

Pick the right tool for the job, no one distro will be best for every possible hardware configuration.  You got plenty of options with the 'Buntu line as far as window managers go, but if the distro itself just doesn't work for you, pick another distro.  There's plenty of quality distributions to choose from; take a look at DistroWatch, download a few and give them a spin, find the one that does it for you.  It gives a list with links to the distro, reviews, major packages in the repositories, the works.  If you don't have a mile high pile of distros on disc, you haven't looked hard enough :D

---

### Post by Father Marc on 2009-02-25
> **jbysmith said:**
> 
I've found openSUSE to be excellent, PCLinuxOS, Fedora, Debian, Mandriva, Vector etc etc.. all worthy of checking out.  Can't just try one distribution and rate Linux as a whole just on that.  They're the same, but also very very different.  Different ways of doing things, different "philosophies", different target audiences.. 


The "big three:" Ubuntu, openSuSE and Fedora, all have very different methods and philosophies (though it seems like Red Hat and Novell are creeping closer), but I've never had a computer on which each of the three didn't "just work."

The communities are slightly different in character, and that might be important to some people.

If you want to help out, openSuSE is, IMHO, the easiest to get involved with because they have easy to find wishlists, wiki needs, etc. Fedora is the hardest... IMHO, of course.

Hey, that's part of the beauty of the Linux world... the variety and choices. If one doesn't work for you, just switch... Open Source is pretty pragmatic by nature.

+ Pax Christi +

---

### Post by stalkingwolf on 2009-02-26
OK I really hate to admit this but I do have 1 laptop that as of this posting I have not gotten any version of Ubuntu to run on.  But I have
not given up.  It just presents some challenges.

It is an old Fujitsu Lifebook with a Pentium 133 processor and as I recall
16mb of ram.

---

