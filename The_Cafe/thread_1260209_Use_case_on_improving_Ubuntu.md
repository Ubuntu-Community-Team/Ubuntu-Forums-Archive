---
title: "Use case on improving Ubuntu"
date: 2009-09-07
forum: The Cafe
---

### Post by Mateo on 2009-09-07
Here is a simple problem that I think we can find a solution for.  When you want to download software using a PPA, you have to pick from a drop down list what release you are using.  Why should a user need to know what release they use?  And if it IS necessary, there should be a super-easy way to find this out.  

When I was presented with this problem, I used (in Gnome) System -> About Ubuntu.  I knew to check here from years of software use; the About page usually includes version information.

Although this worked, it was not obvious to check here, and the version did not stand out on the page.

But shouldn't the Launchpad site know what release you use?  If I go to Firefox.com using linux, it knows I'm using Linux, if I go on Windows, it knows I'm using Windows.  For Windows, it knows if you are using XP or Vista.  So why shouldn't it know that you're using Ubuntu Ibex or Jaunty or whatever?

Any ideas on how to fix this?

---

### Post by Screwdriver0815 on 2009-09-07
my Idea:

[sarcasm]

make a big wallpaper, stating the name

[/sarcasm]

don't get me wrong, but when a user is "intelligent" enough to know what a ppa is and what he has to do to put it in his package manager, then he surely knows which operating system he uses.

Even when he downloads the .iso file, there is in the filename the version number... or during download: at the download link is written "download Ubuntu Jaunty Jackalope here"...

if he then does not remember it: open a terminal and play around with some commands like uname

But I simply can not believe that users are so dumb and stoned that the do not know which ubuntu version they use.

---

### Post by Swagman on 2009-09-07
wtf is a PPA ?

---

### Post by Mateo on 2009-09-07
> **Screwdriver0815 said:**
> my Idea:

[sarcasm]

make a big wallpaper, stating the name

[/sarcasm]

don't get me wrong, but when a user is "intelligent" enough to know what a ppa is and what he has to do to put it in his package manager, then he surely knows which operating system he uses.

Even when he downloads the .iso file, there is in the filename the version number... or during download: at the download link is written "download Ubuntu Jaunty Jackalope here"...

if he then does not remember it: open a terminal and play around with some commands like uname

But I simply can not believe that users are so dumb and stoned that the do not know which ubuntu version they use.

Well, assuming Ubuntu wants to grow, it has to think "big tent".  You might be an enthusiast and anticipate the next release, but not everyone is like that.   So I am one example of the "dumb and stoned" users who is smart enough to use PPA, but doesn't know off-hand what version one is using.

uname gives you kernel versions, not Ubuntu versions.

---

### Post by Screwdriver0815 on 2009-09-07
> **Swagman said:**
> wtf is a PPA ?

I can only tell you what a ppa is, if you know which operating system, especially which ubuntu version you use :lolflag:

so please fill in this form

[ ] yes I know which Ubuntu version I use

[ ] nope, sorry I don't have any clue

:D

---

### Post by Screwdriver0815 on 2009-09-07
> **Mateo said:**
> Well, assuming Ubuntu wants to grow, it has to think "big tent".  You might be an enthusiast and anticipate the next release, but not everyone is like that.   So I am one example of the "dumb and stoned" users who is smart enough to use PPA, but doesn't know off-hand what version one is using.

uname gives you kernel versions, not Ubuntu versions.

then you use

```
lsb_release -a
```

so you can not remember which version you have installed? :confused:

---

### Post by Paqman on 2009-09-07
> **Swagman said:**
> wtf is a PPA ?

[Here you go]("http://lmgtfy.com/?q=ubuntu+ppa")

---

### Post by steveneddy on 2009-09-07
In Intrepid under System --> About Ubuntu

First line states:

Thank you for your interest in Ubuntu 8.10- the Intrepid Ibex - released in October 2008.

This isn't the case with Jaunty?

---

### Post by Mateo on 2009-09-07
> **steveneddy said:**
> In Intrepid under System --> About Ubuntu

First line states:

Thank you for your interest in Ubuntu 8.10- the Intrepid Ibex - released in October 2008.

This isn't the case with Jaunty?

That's what I was talking about, it's how i found the information.  It's not the first line, though.  It should be highlighted somewhere else on the page, not contained within the body of the text.

That's a decent fix to the problem, but the best fix would be to broadcast ubuntu versions to the browser.

---

### Post by Mateo on 2009-09-07
> **Screwdriver0815 said:**
> then you use

```
lsb_release -a
```

so you can not remember which version you have installed? :confused:

It's not that I don't "remember".  Remember implies that you knew, at one time.  But I originally installed ubuntu Dapper Drake.  That's the only disc I own.  From there I upgraded.  Over time my interest in the new releases has waned, and I simply upgrade for the sake of being upgraded.  I don't care what release I'm using, and I don't take note of it.

It's the same deal with Windows.  Windows users know they're using XP or Vista or whatever, but do they know what Service Pack they have installed?  Why should they?

---

### Post by Elfy on 2009-09-07
Last time I went to a ppa it defaulted to the currently installed version of ubuntu - if it didn't default to the currently installed version - why did it pick the second one down in the drop down menu?

[https://launchpad.net/~banshee-unstable-team/+archive/ppa](https://launchpad.net/~banshee-unstable-team/+archive/ppa)

Defaults to Jaunty for me, perhaps someone not using jaunty could check it.

---

### Post by Viva on 2009-09-07
It is not difficult to get the ubuntu version using the useragent. That is a good idea I think.

---

### Post by Screwdriver0815 on 2009-09-07
> **Mateo said:**
> That's what I was talking about, it's how i found the information.  It's not the first line, though.  It should be highlighted somewhere else on the page, not contained within the body of the text.

That's a decent fix to the problem, but the best fix would be to broadcast ubuntu versions to the browser.

what are we talking about here?

It is too much for the user to go to System --> about Ubuntu... 

sorry, I don't get it.

I mean, you actually **use** this system, right? It is not like that you sit in front of the screen and the system has to get information directly from your brain about what you want to do next. There has to be a minimum of user action to get things done in operating systems.
And the same goes for ppa's. The same goes for anything you want to do in the internet and even in spreadsheats and wordprocessing. 

So I still don't get your point. Sorry.

---

### Post by Screwdriver0815 on 2009-09-07
> **forestpixie said:**
> Last time I went to a ppa it defaulted to the currently installed version of ubuntu - if it didn't default to the currently installed version - why did it pick the second one down in the drop down menu?

[https://launchpad.net/~banshee-unstable-team/+archive/ppa](https://launchpad.net/~banshee-unstable-team/+archive/ppa)

Defaults to Jaunty for me, perhaps someone not using jaunty could check it.

I have checked it with Hardy and it is default in Jaunty there too.

---

### Post by Mateo on 2009-09-07
> **forestpixie said:**
> Last time I went to a ppa it defaulted to the currently installed version of ubuntu - if it didn't default to the currently installed version - why did it pick the second one down in the drop down menu?

[https://launchpad.net/~banshee-unstable-team/+archive/ppa](https://launchpad.net/~banshee-unstable-team/+archive/ppa)

Defaults to Jaunty for me, perhaps someone not using jaunty could check it.

because Karmic is not a stable release.  It goes to the most current stable release. I can confirm this using a Gusty virtual machine, still goes to Jaunty.

---

### Post by Mateo on 2009-09-07
> **Viva said:**
> It is not difficult to get the ubuntu version using the useragent. That is a good idea I think.

Are you sure? I think user agent only goes as far as to say it is linux, not what distribution, let alone what version.

---

### Post by Viva on 2009-09-07
> **Mateo said:**
> Are you sure? I think user agent only goes as far as to say it is linux, not what distribution, let alone what version.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Firefox/3.5

That is mine.

---

### Post by Elfy on 2009-09-07
Aah - ok - ty :) learn something new every day.

---

### Post by steveneddy on 2009-09-07
> **forestpixie said:**
> Last time I went to a ppa it defaulted to the currently installed version of ubuntu - if it didn't default to the currently installed version - why did it pick the second one down in the drop down menu?

[https://launchpad.net/~banshee-unstable-team/+archive/ppa]("https://launchpad.net/%7Ebanshee-unstable-team/+archive/ppa")

Defaults to Jaunty for me, perhaps someone not using jaunty could check it.

I check it with Intrepid and it displays correctly my Ubuntu version.

---

### Post by steveneddy on 2009-09-07
What does your browser tell the server about your browser version and operating system info?

[http://show-ip.net/useragent/](http://show-ip.net/useragent/)

will tell you.

---

### Post by chris4585 on 2009-09-07
You guys know on the System tab of System Monitor, it tells you your version number pretty obviously.

---

### Post by Viva on 2009-09-07
> **chris4585 said:**
> You guys know System Monitor on the System tab, it tells you you're version number pretty obviously.

It does, but it is a pretty basic thing that websites that offer a service that is specific to a browser or operating system should check for the version.

---

### Post by Frak on 2009-09-07
Gives me an idea for a program. A special package manager that only installs from PPA's, and substitutes versions for adding PPA's to the sources. Say you add a PPA for Fiesty, but you run Jaunty, so the program replaces "Fiesty" with "Jaunty".

Should be simple in Python. Everything stops at DPKG anyhow.

EDIT
And I mean it searches all available PPA's for a certain application.

---

### Post by Mateo on 2009-09-07
> **Frak said:**
> Gives me an idea for a program. A special package manager that only installs from PPA's, and substitutes versions for adding PPA's to the sources. Say you add a PPA for Fiesty, but you run Jaunty, so the program replaces "Fiesty" with "Jaunty".

Should be simple in Python. Everything stops at DPKG anyhow.

EDIT
And I mean it searches all available PPA's for a certain application.

The more that I think about it, this seems like an upstream problem with APT.  Why does apt have to have the release version in the sources text file?  Forget about this very specific use case, it's always a bad idea in programming to get information from a text file that it can easily get from the system itself.  So why isn't APT doing this already?

Does anyone know who runs the APT project?  I'd like to submit a patch for this, to make the release information optional.

---

### Post by Ric_NYC on 2009-09-07
If things can be made complicated why make them easy?


Why not select software from a list in a website that shows how it works, screenshots, users reviews and tips... NO! Let's use command lines... Like people were born knowing things without been introduced to them first.

---

### Post by Screwdriver0815 on 2009-09-07
> If things can be made complicated why make them easy?

why do something/use google/being creative and look for something when one also could sit around and complain...

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

---

### Post by Frak on 2009-09-07
> **Ric_NYC said:**
> If things can be made complicated why make them easy?


Why not select software from a list in a website that shows how it works, screenshots, users reviews and tips... NO! Let's use command lines... Like people were born knowing things without been introduced to them first.
[http://allmyapps.com/](http://allmyapps.com/)

---

### Post by Ric_NYC on 2009-09-07
> **Screwdriver0815 said:**
> why do something/use google/being creative and look for something when one also could sit around and complain...

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)


Do you really believe that adding PPA and PPA's keys are necessary to install software in an OS in 2009?

---

### Post by Mateo on 2009-09-07
> **Ric_NYC said:**
> Do you really believe that adding PPA and PPA's keys are necessary to install software in an OS in 2009?

Don't pay attention, he's defending his favorite baseball team.  There is no room for constructive criticism for people of that mindset.

---

### Post by Screwdriver0815 on 2009-09-07
> **Ric_NYC said:**
> Do you really believe that adding PPA and PPA's keys are necessary to install software in an OS in 2009?

of course it is. Or what is better in searching the internet, downloading .deb files, maybe installing a rootkit or anything and getting no updates? 

> Don't pay attention, he's defending his favorite baseball team. There is no room for constructive criticism for people of that mindset.

ah and you think, it is constructive to sit in your chair, wondering why the system in front of you doesn't tell you which version it is, even when you **think** "if the system would tell me..."? And after that, complaining about it that this of course is not userfriendly?

---

### Post by koenn on 2009-09-07
> **forestpixie said:**
> Last time I went to a ppa it defaulted to the currently installed version of ubuntu - if it didn't default to the currently installed version - why did it pick the second one down in the drop down menu?

[https://launchpad.net/~banshee-unstable-team/+archive/ppa](https://launchpad.net/~banshee-unstable-team/+archive/ppa)

Defaults to Jaunty for me, perhaps someone not using jaunty could check it.

> **Screwdriver0815 said:**
> I have checked it with Hardy and it is default in Jaunty there too.

tried, it
Defaults to Hardy (8.04) - which is what I'm using.

---

### Post by zekopeko on 2009-09-07
This was a problem before but they fixed it. I know since I reported a duplicate bug for this behavior in LP.

---

### Post by oldos2er on 2009-09-07
> **Mateo said:**
> Are you sure? I think user agent only goes as far as to say it is linux, not what distribution, let alone what version.

 Assuming you're not using user-agent-switcher.

---

### Post by Frak on 2009-09-07
> **oldos2er said:**
> Assuming you're not using user-agent-switcher.
If you're using a User-Agent switcher, you should very well know why Launchpad doesn't know what to give you.

---

### Post by Mateo on 2009-09-07
Hmm.... Using Jaunty (according to System Monitor)..

Epiphany:

Mozilla/5.0 (X11; U; Linux i686; en; rv:1.9.0.13) Gecko/20080528 Epiphany/2.22 Firefox/3.0

Chromium: 

Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/532.0 (KHTML, like Gecko) Chrome/4.0.207.0 Safari/532.0

Firefox:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) 


So, for some reason Epiphany and Chromium hides it, Firefox does not...

---

### Post by 23meg on 2009-09-07
[https://blueprints.launchpad.net/ubuntu/+spec/apt-firefox-archive-handler](https://blueprints.launchpad.net/ubuntu/+spec/apt-firefox-archive-handler)

---

### Post by MikeTheC on 2009-09-07
I'd never heard of "PPA" before entering this thread, and after reading through it and doing a Google search, I still have no idea what PPA is.

So, if one of you kindly folk wouldn't mind stooping down to my level, what exactly is a PPA in this context?

---

### Post by koenn on 2009-09-07
[http://www.google.com/search?q=ubuntu+ppa](http://www.google.com/search?q=ubuntu+ppa)

or see post 7 in this thread

---

### Post by ad_267 on 2009-09-07
Bring on the [SoftwareStore]("https://wiki.ubuntu.com/SoftwareStore")!

> Establish a mechanism for establishing and conveying a trust level for software in PPAs, and for easily adding PPAs within the Store. 

A PPA is a personal package archive. It's a personal software repository set up on launchpad. To add one to your apt sources at the moment is a bit clumsy, especially adding the gpg key.

---

### Post by Mateo on 2009-09-07
> **MikeTheC said:**
> I'd never heard of "PPA" before entering this thread, and after reading through it and doing a Google search, I still have no idea what PPA is.

So, if one of you kindly folk wouldn't mind stooping down to my level, what exactly is a PPA in this context?

It's a way to download software that are not in the Ubuntu repository, but still hosted on Ubuntu servers.

---

### Post by steveneddy on 2009-09-08
> **ad_267 said:**
> Bring on the [SoftwareStore]("https://wiki.ubuntu.com/SoftwareStore")!



A PPA is a personal package archive. It's a personal software repository set up on launchpad. To add one to your apt sources at the moment is a bit clumsy, especially adding the gpg key.

I have used pps's since the warty days and I have never found it clumsy to install a ppa.

Open up the sources.list file and copy two lines and save.

Open up a terminal and enter one line  of code and hit enter.

It's done.

sudo apt-get update and install  my new software and it will be updated automatically the next software upgrade.

It takes less time than DLing a .deb file then waiting for  the install and it is a more elegant way of performing a mundane task like installing software.

---

### Post by ad_267 on 2009-09-08
> **steveneddy said:**
> I have used pps's since the warty days and I have never found it clumsy to install a ppa.

It's not clumsy for me either, and with the new software store I'd still add them by hand. It can be really confusing for new users though.

---

### Post by Screwdriver0815 on 2009-09-08
> **steveneddy said:**
> I have used pps's since the warty days and I have never found it clumsy to install a ppa.

Open up the sources.list file and copy two lines and save.

Open up a terminal and enter one line  of code and hit enter.

It's done.

sudo apt-get update and install  my new software and it will be updated automatically the next software upgrade.

It takes less time than DLing a .deb file then waiting for  the install and it is a more elegant way of performing a mundane task like installing software.

I also have done it since my starter days in Ubuntu. It is a very good way of installing software. 

The biggest advantage is that you always get updates in the installed software when you leave the ppa activated in the repository manager.

but speaking in general:

Of course it is confusing to new users. Why is it confusing? Because it is new to the new user.
But if the new user would have a little bit of initiative and if he/she would be a little bit curious about the new system he/she is now using, he/she would find out, what it is and how to handle it. There is so much information available in the internet. It just has to be digged out!
Is it really too much demanding, when a user should get himself familiar with certain stuff?

The next thing is: nothing is logic on first sight. Even the software store isn't. So I already know in this moment of writing, that after the Karmic release there will be lots of complaints about how "illogic" this software store is.

"... and maybe an ex-windows user would not know how to handle it..."

the illogic stuff elsewhere... "ah okay, I have to adapt myself to it"... 

But Linux should of course adapt itself to the ex-windows users.... to the "new users"... and the things which are prefered by the "old users" which have brought this system into this stage as it is now, can of course be ignored. Because the "new users" are really important... more important than the others.

its really silly in my eyes. 

Even when I think about the fact that every "making it logic to the ex-windows users" will bring new "illogic things for the ex-windows user" with it. 
So the result is: we do a second windows, which is not right because windows is NOT the nonplusultra, just because people make themselves familiar with it, but do not do this when using Ubuntu or Linux in general.

---

### Post by Exodist on 2009-09-08
> **Screwdriver0815 said:**
> my Idea:

[sarcasm]

make a big wallpaper, stating the name

[/sarcasm]

don't get me wrong, but when a user is "intelligent" enough to know what a ppa is and what he has to do to put it in his package manager, then he surely knows which operating system he uses.

Even when he downloads the .iso file, there is in the filename the version number... or during download: at the download link is written "download Ubuntu Jaunty Jackalope here"...

if he then does not remember it: open a terminal and play around with some commands like uname

But I simply can not believe that users are so dumb and stoned that the do not know which ubuntu version they use.

LMFAO
+2 Cool Points!

---

