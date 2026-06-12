---
title: "Newbie - Installing thrid party aps, and adding a chat?"
date: 2011-07-12
forum: Ubuntu Studio
---

### Post by jimijamz3 on 2011-07-12
Newbie, very Newbie I have decided to us Ubuntu Studio in a dual Boot system with Xp for audio recording. My hardware will only work with Windows Xp and Pro Tools. I want to use Ubuntu to mix audio tracks and take use of some of it's advantages.

My problem is that I do not know how to install third party programs. The package installer will not load programs I have downloaded. I also wold like to have the chat program for live tech help and advice with Ubuntue.

Also my windows that are minimized now disapear and do not go to the tab for retreavel.  thats about it some very newbie questions that I am sure are easily solved. I should started with Linux along time ago and would not be so behind the curve. Thanks

---

### Post by Axxl Force on 2011-07-12
Hi JimiJamze,

what do you mean by "3dr party apps". Installing "apps" under ubuntu is very easy! Either you install it by searching it using your software centre or your're provided by the company with a *.deb file which will install just as easy...

If you're talking about a windows "app" though you'll have to use "Wine" which is not that complex either. Just report back which "app" you mean.

cheers
Axxl

---

### Post by jejeman on 2011-07-12
```
The package installer will not load programs I have downloaded. 
```What kind of file type you downloaded?
```
I also wold like to have the chat program for live tech help and advice with Ubuntue.
```There is already program for that installed, I think. Which one depends on verison of Ubuntu you installed. If not, you can use Pidgin - it is in repositories no need for external download.
```
Also my windows that are minimized now disapear and do not go to the tab for retreavel.
```Check if you have "window list" applet on panel. If not, add it.

---

### Post by jimijamz3 on 2011-07-12
Thanks for the recomendation the chat. the program i am trying to install cannot be found with the download manger and I cannnot istall the Tar there are a lot of audio and video programs out there that are free that cannot be found on the search option. I updated Ubuntu Studio 10.10 

and also the thing with the minimized windows, aps etc.. desapearing how do I get them back, I must have hit or did something to make them not go to the status bar. Thanks guys real new to Linux, but willing to learn for sure.

---

### Post by jejeman on 2011-07-12
> I updated Ubuntu Studio 10.10 What does this mean? You updated 10.04 to 10.10, or you updated 10.10. to 11.04? Or maybe Ubuntu 10.10.to ubuntu studio 10.10?
> and also the thing with the minimized windows, aps etc.. desapearing how do I get them back,Maybe its better to give us a screenshot of entire desktop with at least one window open.
> I cannnot istall the Tar there are a lot of audio and video programs out there that are free that cannot be found on the search option.Such as? If you downloaded tar.gz archive that probably means it's a source code inside. So, you have to compile it youre self. Not shure if you are ready for that.

---

### Post by jimijamz3 on 2011-07-12
The issue of the windows disiapearing is resolved the file is Flxer5.2_linux.zip yea I need to learn how to install programs not on the Ubuntu built in software finder. yea I know it is not easy with commands, but I think i can handle if I know how to treat each file type. upload of screen shot.

Thank JeJe

---

### Post by jejeman on 2011-07-13
If you have already resolve the windows problem you didn't have to attach the sreenshot. You didn't answer all my questions.
As far as I can see that Flexer program is flash application. So just unzip it anywhere and start it. If it only has flash projector exe file you will need Wine to be installed to be able to start it.

As a general rule you will have to treat each applicatin you downloaded differently depending on what it actually is - linux precompiled binary, deb package, source code archive... and so on. Reagard the source code, there is always instructions inside the archive which tells what dependecies it needs and how to compile it.
For compiling from the source code you need, for starters, to install "build-essential" package. Rest dependes on dependecies that actuall program needs.

---

