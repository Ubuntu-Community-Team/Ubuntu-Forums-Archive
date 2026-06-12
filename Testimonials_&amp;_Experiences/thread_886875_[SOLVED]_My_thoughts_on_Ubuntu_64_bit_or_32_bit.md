---
title: "[SOLVED] My thoughts on Ubuntu 64 bit or 32 bit"
date: 2008-08-11
forum: Testimonials &amp; Experiences
---

### Post by hufferd on 2008-08-11
I made a post about this a few days ago.  I built myself a new box this year and when I did that I wanted to go with ubuntu 8.04.  So thats what I did I did some reading and as it turns out maybe I did not do enough.  I knew the road to Ubuntu was not going to be easy after being a die hard windows user from back in the days of 3.1  :shock:

None the less I built my new machine and installed 8.04 64 bit OS.  Because after all I now had a 64 bit system. So I thought well I should go with the 64 bit OS then.  Well this is where I failed to read as much as I should have............     Mind you I don't mind messing with things to get them to work and I will stick with something until I am so pissed I'm about ready to throw the computer out the window.  We come to find out that did not take long with the 64 bit OS ver of Ubuntu.  Every time in the first month that I had the OS I was not able to simply install something.  I was having to force install allot of the things I was trying to run.  Because of lack of true software support for 64 bit systems. 

After about 4 months now of getting mad at the 64-bit OS I made the choice to switch back to the Ubuntu 32 bit OS.

And already I am much more happy with things and not having force install every damn thing.....  And so far this last weekend I have seen NO! performance issues with running the 32 bit OS on a 64 bit machine.  So until there is a wider range of software out there that supports 64 bit systems.  I'm going to stick with the 32 bit OS. 

Just may take on it I know some may not agree but I am happy with the change and I am sure in the long run it will make me much more happy :)  


D

---

### Post by Kilz on 2008-08-12
> **hufferd said:**
> I made a post about this a few days ago.  I built myself a new box this year and when I did that I wanted to go with ubuntu 8.04.  So thats what I did I did some reading and as it turns out maybe I did not do enough.  I knew the road to Ubuntu was not going to be easy after being a die hard windows user from back in the days of 3.1  :shock:

None the less I built my new machine and installed 8.04 64 bit OS.  Because after all I now had a 64 bit system. So I thought well I should go with the 64 bit OS then.  Well this is where I failed to read as much as I should have............     Mind you I don't mind messing with things to get them to work and I will stick with something until I am so pissed I'm about ready to throw the computer out the window.  We come to find out that did not take long with the 64 bit OS ver of Ubuntu.  Every time in the first month that I had the OS I was not able to simply install something.  I was having to force install allot of the things I was trying to run.  Because of lack of true software support for 64 bit systems. 

After about 4 months now of getting mad at the 64-bit OS I made the choice to switch back to the Ubuntu 32 bit OS.

And already I am much more happy with things and not having force install every damn thing.....  And so far this last weekend I have seen NO! performance issues with running the 32 bit OS on a 64 bit machine.  So until there is a wider range of software out there that supports 64 bit systems.  I'm going to stick with the 32 bit OS. 

Just may take on it I know some may not agree but I am happy with the change and I am sure in the long run it will make me much more happy :)  


D

Please list each and every application you say you had to force install.

---

### Post by hufferd on 2008-08-12
[GYACHI]("http://ubuntuforums.org/showthread.php?t=773802")

[Lightscribe support]("http://www.lightscribe.com/downloadSection/linux/index.aspx") software 

Even after I did follow the tips for getting java to [work with firefox on a 64bit system ]("http://ubuntuforums.org/showthread.php?t=798571") I then had issues with the browser locking up ----- now that I am back on a 32 bit OS I have had no issues 

MMPOG - [Secondlife]("http://secondlife.com/").  - there is nothing to install here but if you want it to run you have to install the 32bitlibs on a 64 bit system.

There are some others but these are some of the ones just to name a few

---

### Post by Methuselah on 2008-08-12
I don't mind installing 32 bit support libs on 64 bit.
64 bit processors are meant to be able to run programs intended for 32 bit systems.
So far I've had no problems.

I want to be able use my full amount of RAM etc so I chose the 64bit OS.

---

### Post by Kilz on 2008-08-12
> **hufferd said:**
> [GYACHI]("http://ubuntuforums.org/showthread.php?t=773802")

[Lightscribe support]("http://www.lightscribe.com/downloadSection/linux/index.aspx") software 

Even after I did follow the tips for getting java to [work with firefox on a 64bit system ]("http://ubuntuforums.org/showthread.php?t=798571") I then had issues with the browser locking up ----- now that I am back on a 32 bit OS I have had no issues 

MMPOG - [Secondlife]("http://secondlife.com/").  - there is nothing to install here but if you want it to run you have to install the 32bitlibs on a 64 bit system.

There are some others but these are some of the ones just to name a few

Can you please link to the threads where you asked for help on these problems?

---

### Post by hufferd on 2008-08-12
I didn't say I needed help with them I know how to force an install and they worked after I did that well never could get GYACHI to work but the others worked fine after forcing the install or installing the 32bit libs....  Its the point of having to go through all that you dont have to with the 32bit OS

D :)

---

### Post by loell on 2008-08-12
the case of gyachi is just "**simply just almost there for 64 bit**" 

one could compile it in 64 bit but will be loosing the room voice chat(win32) which is actually tolerable in normal IM uses. 

the force install along with getlibs is just there for those **wanting** not really **needing**. 

sadly this is the downside of chasing a windows feature, 

in due time perhaps the particular component in question will be ported to 64 bit.

---

### Post by Kilz on 2008-08-12
> **hufferd said:**
> I didn't say I needed help with them I know how to force an install and they worked after I did that well never could get GYACHI to work but the others worked fine after forcing the install or installing the 32bit libs....  Its the point of having to go through all that you dont have to with the 32bit OS

D :)

So, let me get this right. Because you have to use the force option to install a few packages, you think there is a overall lack of support for 64bit?

1. The ability to force a package to install is a option designed into apt-get. There is nothing wrong with forcing a package. This is because not every developer has a 64bit machine. But we all know that i386 packages will install and run on the AMD64 version.

2. 32bit libs have a specific folder in a 64bit Ubuntu install. It is /lib32 or /usr/lib32. This was designed in by the developers to hold 32bit libraries. Because the developers know that i386 binaries will run on 64bit Ubuntu but they need libraries. Getlibs makes installing them a breeze. All it takes is a little typing.

3. The reasons to run the AMD64 version are numerous.
  A) There is a a 30% performance increase for applications that crunch numbers. Examples are 3d modeling, video editing, and encoding (ripping media to a file).
  B) You paid for the 64bit hardware, why on earth anyone would pay for hardware and then put an operating system that doesnt make full use of what they paid for is beyond me.

But lest also look at something. You are a new Ubuntu user. There is a learning curve. No matter what version of the OS you would have installed you still have to deal with something new. Now after dealing with the 64bit version, that you find your next install simpler is not strange. 
But that in no way points to a failure of the 64bit version of or its usefulness to you or others. That you didnt ask for help is a sure path to failure.

---

### Post by hyper_ch on 2008-08-13
Hmmm, 4 applications (although rather 3 applications and 1 plugin) are enough to say 20+k other 64bit applications are useless?

GYACHI - never heard of that one before until the other thread about 32/64bit from yesterday...

Lightscribe - never heard of before...

Java in FF - works fine on my bosses notebook...

Secondlife - a time waster ;)

---

### Post by worx101 on 2008-08-13
... personally, i have used the 64bit version of ubuntu 8.04 without any problems since it was released....  Cannot for the life of me understand how it frustrate anyone into downgrading? :S

PS... well there is that annoying adobe flash issue(freaking crashes constantly and I have to exit browser and restart) which is a pain in the *** if you multiple windows open :P

But that is livable as my browser isn't everything :P

---

### Post by hufferd on 2008-08-13
> **hyper_ch said:**
> Hmmm, 4 applications (although rather 3 applications and 1 plugin) are enough to say 20+k other 64bit applications are useless?

GYACHI - never heard of that one before until the other thread about 32/64bit from yesterday...

Lightscribe - never heard of before...

Java in FF - works fine on my bosses notebook...

Secondlife - a time waster ;)

bottom line here is ---------  

All these apps  (& one plug-in) listed above - DID NOT work with out issues - on the 64 bit OS. 

On the 32 bit OS everything is installed and running VERY WELL.  

Thats all I am saying --- 

And Im not the only one that has felt this way I have been reading countless threads of people with same issues.  Who knows knows maybe at the next release --- I will try again :)


Have a great day!
:)

---

### Post by hyper_ch on 2008-08-13
> **hufferd said:**
> All these apps  (& one plug-in) listed above - DID NOT work with out issues - on the 64 bit OS.
You mean the "annoyance" of pressing "force install". 

> **hufferd said:**
> And Im not the only one that has felt this way I have been reading countless threads of people with same issues.
That's why you said:
> **hufferd said:**
> Every time in the first month that I had the OS I was not able to simply install something. I was having to force install allot of the things I was trying to run.
Isn't that a direct contradiction? Either you were not able to install anything or you were able to with a little bit of twinkering...
And then you come to the conclusion:
> **hufferd said:**
>  Because of lack of true software support for 64 bit systems.
So, 4 programs where you had to press some extra buttons make all of the other 20+k apps on 64 totally unusable and useless? A bit of an exaggeration, right?

---

### Post by hufferd on 2008-08-13
HAHA so you got me  LOL 

but yes still my point is I had issue with 64 bit OS that I DON'T have with the 32 bit OS correct???

---

### Post by Mgiacchetti on 2008-08-13
> **hyper_ch said:**
> Hmmm, 4 applications (although rather 3 applications and 1 plugin) are enough to say 20+k other 64bit applications are useless?

GYACHI - never heard of that one before until the other thread about 32/64bit from yesterday...

Lightscribe - never heard of before...

Java in FF - works fine on my bosses notebook...

Secondlife - a time waster ;)

Gyachi an IM program that supposedly supports voice

Lightscribe a program for Lightscribe cd/dvd burners so you can burn an image on the top of the disk

java in ff  I had problems with this as well

secondlife yes a time waster, but a fun one.

---

### Post by hufferd on 2008-08-13
:)

---

### Post by Methuselah on 2008-08-13
No problem with java in firefox here.
Installed gcj-mozilla.

---

### Post by hyper_ch on 2008-08-13
well I'd say my boss is a typical user and he has no issues with 64bit :)

---

### Post by hufferd on 2008-08-14
Another update

As posted [here]("http://ubuntuforums.org/showthread.php?t=822764") I could not get the Amazon MP3 down loader to install on the 64 bit OS which is needed to down load whole albums at a lower price rather then buying single song titles from Amazon.

---

### Post by Canis familiaris on 2008-08-14
Personally 64bit Ubuntu works very well for me.

Only WINE failed but then I was also too lazy to compile WINE from Source. :)

Overall 64bit Ubuntu rocks IMO.

---

### Post by Methuselah on 2008-08-14
And I take it for granted that I can not only install wine from wine's repos but run 32 bit windows applications on 64bitbuntu.

---

### Post by hyper_ch on 2008-08-14
> **Methuselah said:**
> And I take it for granted that I can not only install wine from wine's repos but run 32 bit windows applications on 64bitbuntu.

You assume wrong... wine runs fine from the wine repos and so do the 32bit apps in wine.

---

### Post by stchman on 2008-08-14
> **hufferd said:**
> I made a post about this a few days ago.  I built myself a new box this year and when I did that I wanted to go with ubuntu 8.04.  So thats what I did I did some reading and as it turns out maybe I did not do enough.  I knew the road to Ubuntu was not going to be easy after being a die hard windows user from back in the days of 3.1  :shock:

None the less I built my new machine and installed 8.04 64 bit OS.  Because after all I now had a 64 bit system. So I thought well I should go with the 64 bit OS then.  Well this is where I failed to read as much as I should have............     Mind you I don't mind messing with things to get them to work and I will stick with something until I am so pissed I'm about ready to throw the computer out the window.  We come to find out that did not take long with the 64 bit OS ver of Ubuntu.  Every time in the first month that I had the OS I was not able to simply install something.  I was having to force install allot of the things I was trying to run.  Because of lack of true software support for 64 bit systems. 

After about 4 months now of getting mad at the 64-bit OS I made the choice to switch back to the Ubuntu 32 bit OS.

And already I am much more happy with things and not having force install every damn thing.....  And so far this last weekend I have seen NO! performance issues with running the 32 bit OS on a 64 bit machine.  So until there is a wider range of software out there that supports 64 bit systems.  I'm going to stick with the 32 bit OS. 

Just may take on it I know some may not agree but I am happy with the change and I am sure in the long run it will make me much more happy :)  


D

I have 64 bit Ubuntu running on 3 different machines and have never had to forc install anything.  The repos are full of 64 bit .deb files and the VERY FEW I do get from [www.getdeb.net](www.getdeb.net) I get the 64 bit version.

Java in 64 bit is easy, just install Icedtea.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

---

### Post by stchman on 2008-08-14
> **Methuselah said:**
> And I take it for granted that I can not only install wine from wine's repos but run 32 bit windows applications on 64bitbuntu.

Why would you use WINE's repos.  WINE is in Hardy's repos.

I run a lot of Windows games using WINE on 64 bit Ubuntu.

---

### Post by hufferd on 2008-08-14
I listed the apps early on in this thread -  

one thats not listed here is 

Amazon's MP3 down loader that you MUST have to download full song albums at a lesser price then buying the songs one by one 

All the apps I spoke of here run fine and installed under Ubuntu 32 bit

---

### Post by hyper_ch on 2008-08-14
> **stchman said:**
> Why would you use WINE's repos.
Because they are more up-to-date ;)

> **hufferd said:**
> All the apps I spoke of here run fine and installed under Ubuntu 32 bit
all the apps you mentioned can also be installed fine and run fine on a 64bit OS

---

### Post by Methuselah on 2008-08-15
> **hyper_ch said:**
> You assume wrong... wine runs fine from the wine repos and so do the 32bit apps in wine.

lol..that's exactly what I said.
I *am* running wine in 64bit ubuntu and running 32bit windows apps in it.

---

### Post by Methuselah on 2008-08-15
> **hyper_ch said:**
> Because they are more up-to-date ;)



Correct.

---

