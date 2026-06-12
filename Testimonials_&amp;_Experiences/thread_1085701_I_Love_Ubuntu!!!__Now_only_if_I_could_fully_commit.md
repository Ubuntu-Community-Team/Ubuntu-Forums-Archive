---
title: "I Love Ubuntu!!!  Now only if I could fully commit...."
date: 2009-03-03
forum: Testimonials &amp; Experiences
---

### Post by Committed on 2009-03-03
I've been running ubuntu on my laptop for a few weeks and I liked it so much I put in on my main Vista machine as a dual boot. It's a Gateway Quad core 2.4mhz, 2 g ram, 500gig hardrive. I gave ubuntu 60 gigs of space on my hardrive for now.  

I love the flexibility, the look, the feel, the speed, the security, the control, the community of users and basically everything about it.  I've been using open office for years so that was nothing new.  I'm geeky so I love tinkering with stuff. I have a general disdain for MS and the bloated, turd OS's they are turning out.  I've had my share of troubles with Vista.

I had a huge scare last week with win32:vitro virus on windows.  Fortunately it was a false positive with Avast, but not having to worry about such things with ubuntu is a huge plus.

The only thing keeping me with Vista at all is the fact that I have to run Quickbooks and Chief Architect version 9.  I haven't tried them under Wine but have read that there are problems.  My Avermedia m791 tv tuner card is not supported either.  I might just buy a HDhomerun and be done with it since I always have the tv on when I'm on my PC and I use it as a Tivo to record programs.  So this is the biggest thing so far as I need the tv working.  

Either way, I love ubuntu and will keep it.  Thanks to everyone who has worked on this to make it possible.  =D>

---

### Post by wolfen69 on 2009-03-03
great to hear you are enjoying it. you could use virtualbox and install windows inside of linux, and never have to reboot. have fun.

---

### Post by Vince4Amy on 2009-03-03
> I haven't tried them under Wine but have read that there are problems.

Remember sometimes on WINE mileage will vary depending on the computer. Give it a go anyway I've put this all into one command for you if you want to try so here's a simple way to install WINE:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && sudo apt-get update && sudo apt-get install wine && winecfg
``` 

Check all the options and then close the command line. You can run Windows applications by right clicking the .exe file and open with WINE. The apps should add a shortcut to your menu.

If they don't work be sure to leave a comment on appdb [http://appdb.winehq.org/](http://appdb.winehq.org/) . It's always worth a try :).

---

### Post by Committed on 2009-03-03
> **Vince4Amy said:**
> Remember sometimes on WINE mileage will vary depending on the computer. Give it a go anyway I've put this all into one command for you if you want to try so here's a simple way to install WINE:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && sudo apt-get update && sudo apt-get install wine && winecfg
``` 

Check all the options and then close the command line. You can run Windows applications by right clicking the .exe file and open with WINE. The apps should add a shortcut to your menu.

If they don't work be sure to leave a comment on appdb [http://appdb.winehq.org/](http://appdb.winehq.org/) . It's always worth a try :).

Thanks!  Question, do I have to install my windows apps on my ubuntu partition, or can they be accessed as already installed in windows?

Will look into virtualbox as well.  I have to keep this computer somewhat easy to use with Quickbooks, as my wife does a lot of the bookkeeping.

---

### Post by Vince4Amy on 2009-03-03
> do I have to install my windows apps on my ubuntu partition, 

Some of them, depends how they install initially. If they write a bunch of DLLs, Registry Keys and user specific files you'll have to install them again on WINE and it's best to do so unless they won't install in WINE to start with.

---

### Post by wolfen69 on 2009-03-03
in wine, things may or may not work. with virtualbox, since it is a real install inside of linux, it is guarranteed to work.

---

### Post by mkvnmtr on 2009-03-03
Nothing wrong with a dual boot. systems do different things. I just never let my windows system connect to the internet. If I boot my mac os I usually leave it connected. For internet it is only Ubuntu.

---

### Post by Vince4Amy on 2009-03-03
> **wolfen69 said:**
> in wine, things may or may not work. with virtualbox, since it is a real install inside of linux, it is guarranteed to work.

It's worth a try though. WINE has run flawlessly with almost all of my programs.

---

### Post by stchman on 2009-03-03
> **Vince4Amy said:**
> Remember sometimes on WINE mileage will vary depending on the computer. Give it a go anyway I've put this all into one command for you if you want to try so here's a simple way to install WINE:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list && sudo apt-get update && sudo apt-get install wine && winecfg
``` 

Check all the options and then close the command line. You can run Windows applications by right clicking the .exe file and open with WINE. The apps should add a shortcut to your menu.

If they don't work be sure to leave a comment on appdb [http://appdb.winehq.org/](http://appdb.winehq.org/) . It's always worth a try :).

WINE is available in the repos no need to use the WINE repos.

```
sudo apt-get install wine
```

---

### Post by stchman on 2009-03-03
> **Committed said:**
> I've been running ubuntu on my laptop for a few weeks and I liked it so much I put in on my main Vista machine as a dual boot. It's a Gateway Quad core 2.4mhz, 2 g ram, 500gig hardrive. I gave ubuntu 60 gigs of space on my hardrive for now.  

I love the flexibility, the look, the feel, the speed, the security, the control, the community of users and basically everything about it.  I've been using open office for years so that was nothing new.  I'm geeky so I love tinkering with stuff. I have a general disdain for MS and the bloated, turd OS's they are turning out.  I've had my share of troubles with Vista.

I had a huge scare last week with win32:vitro virus on windows.  Fortunately it was a false positive with Avast, but not having to worry about such things with ubuntu is a huge plus.

The only thing keeping me with Vista at all is the fact that I have to run Quickbooks and Chief Architect version 9.  I haven't tried them under Wine but have read that there are problems.  My Avermedia m791 tv tuner card is not supported either.  I might just buy a HDhomerun and be done with it since I always have the tv on when I'm on my PC and I use it as a Tivo to record programs.  So this is the biggest thing so far as I need the tv working.  

Either way, I love ubuntu and will keep it.  Thanks to everyone who has worked on this to make it possible.  =D>

Gnucash from what I have read is a really great Quicken alternative.  I cannot comment on Chief Architect.

---

### Post by Cybie257 on 2009-03-03
> **stchman said:**
> WINE is available in the repos no need to use the WINE repos.

```
sudo apt-get install wine
```


I've noticed that the WINE repos seem to have the latest version available before the standard repos, which might be expected, but when Update Manager checks for updates, you'll get the WINE updates as they are available. So, I find that it is a good idea to setup the WINE repos. :)

-Cybie

---

### Post by Vince4Amy on 2009-03-03
> WINE is available in the repos no need to use the WINE repos.

No for compatibility I do recommend that the latest version is used, The version in the repos is old.

---

### Post by stchman on 2009-03-03
> **Vince4Amy said:**
> No for compatibility I do recommend that the latest version is used, The version in the repos is old.

According to WineHQ V1.01 is the latest stable version.

[http://www.winehq.org/](http://www.winehq.org/)

The Intrpid repos have you guess V1.01.

Now WineHQ has a development version 1.1.16.  I would prefer to stick with the stable version over experimental software.

---

### Post by Vince4Amy on 2009-03-03
> Now WineHQ has a development version 1.1.16. I would prefer to stick with the stable version over experimental software. But you need to consider the progress of WINE, most applications will work better with newer versions.

---

### Post by stchman on 2009-03-03
> **Vince4Amy said:**
> But you need to consider the progress of WINE, most applications will work better with newer versions.

I am just saying that the version in the Intrepid repos is the same as the latest stable version WineHQ is offering.

As far as work better I disagree.  I tried the 1.1.16 developmental version an some of my Windows games (which ran) did not work at all.  Wait until the 1.1.16 becomes stable.

---

### Post by wolfen69 on 2009-03-03
i would go with virtualbox. below is a screenshot of windows 7 running full screen within linux. performance is very good also. why bother with wine?

---

### Post by Committed on 2009-03-03
> **mkvnmtr said:**
> Nothing wrong with a dual boot. systems do different things. I just never let my windows system connect to the internet. If I boot my mac os I usually leave it connected. For internet it is only Ubuntu.

For the time being, this computer will remain dual boot. I set it to boot automatically to Vista with a 5 second delay so I can get into ubuntu yet my wife doesn't get confused.  ;)

I'm going to install ubuntu on my kids computer(my old p4 2.8ghz machine) and play with both Wine and Virtual box.  He's got nothing to lose on that machine and he's dying to run ubuntu anyways.  This machine is my main business unit and I have much to lose if I screw it up.  I need to do weekly payroll, cad drawings and other stuff.  It's all backed up of course but I need to make sure things are right before I go all out.  

Right now I want TV back on my screen while I work or play.  Need a different tuner card, probably hdhomerun from what I've read.  Right now, I have to boot back up to Vista nights and weekends so it records my shows.  Pain.  BTW, thanks everyone.

---

### Post by Committed on 2009-03-03
> **wolfen69 said:**
> i would go with virtualbox. below is a screenshot of windows 7 running full screen within linux. performance is very good also. why bother with wine?

I've got to read up on this more.  Don't fully understand it yet.  Sounds like ubuntu uses the whole hardrive and Windows is installed inside of ubuntu with virtualbox.?

---

### Post by Vince4Amy on 2009-03-03
> i would go with virtualbox. below is a screenshot of windows 7 running full screen within linux. performance is very good also. why bother with wine? Because it's yet another Windows license. WINE Is great.

> Sounds like ubuntu uses the whole hardrive and Windows is installed inside of ubuntu with virtualbox.?

Virtualbox is like an Emulator, it will emulate PC Hardware which you will the install Windows onto the Virtual PC. It will be running an entire Windows installing in this virtual environment.

---

### Post by Ms_Angel_D on 2009-03-03
Hi, I think we have the same computer, so first I have a question, What model is  your gateway, mine is a GM5478, either way it's definitely the same tuner, so I feel your pain there.

Secondly I want to say that My first ubuntu experience was through virtualbox on windows. I have a tutorial here, just skip down to the part entitled "***Setting up your first virtual machine***" It's the same concept no matter what OS your attempting to install in virtual box.

[http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu](http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu)

Welcome to ubuntu, and I hope you enjoy the experience!

Angel

---

### Post by Committed on 2009-03-03
> **MetalHellsAngel said:**
> Hi, I think we have the same computer, so first I have a question, What model is  your gateway, mine is a GM5478, either way it's definitely the same tuner, so I feel your pain there.

Secondly I want to say that My first ubuntu experience was through virtualbox on windows. I have a tutorial here, just skip down to the part entitled "***Setting up your first virtual machine***" It's the same concept no matter what OS your attempting to install in virtual box.

[http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu](http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu)

Welcome to ubuntu, and I hope you enjoy the experience!

Angel
Yes it is a GM5478.  I've had it for about a year and a half I think.  Yeah, bites about the tuner not being supported so I'll be upgrading that.  

Thanks, I'll check out your tutorial.  Been doing lots of reading lately. I like ubuntu more and more each day, in fact, I hate having to go into windows.

---

### Post by Ms_Angel_D on 2009-03-03
> **Committed said:**
> Yes it is a GM5478.  I've had it for about a year and a half I think.  Yeah, bites about the tuner not being supported so I'll be upgrading that.  

Thanks, I'll check out your tutorial.  Been doing lots of reading lately. I like ubuntu more and more each day, in fact, I hate having to go into windows.

Oh kewl somebody with the same system, here's a question for you does your microphone work? I've been using ubuntu since 7.10 on this system and my microphone has yet to work, I have a launchpad bug open about it but it's yet to be resolved.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307574](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307574) 

If you have the same issues you might want to leave your own comments on the bug as well.

Angel

---

### Post by Committed on 2009-03-03
> **MetalHellsAngel said:**
> Oh kewl somebody with the same system, here's a question for you does your microphone work? I've been using ubuntu since 7.10 on this system and my microphone has yet to work, I have a launchpad bug open about it but it's yet to be resolved.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307574](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307574) 

If you have the same issues you might want to leave your own comments on the bug as well.

Angel

Sorry, never used the microphone.  I think I know where it is.  If I find it I'll hook it up and see if I can get it to work.

---

