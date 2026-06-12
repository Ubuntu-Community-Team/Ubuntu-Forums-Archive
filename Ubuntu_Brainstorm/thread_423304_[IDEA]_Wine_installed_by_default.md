---
title: "[IDEA] Wine installed by default"
date: 2006-08-11
forum: Ubuntu Brainstorm
---

### Post by jason.b.c on 2006-08-11
I think Wine and maybe Dosemu should be installed by default in this next release...

What do you think..???

**Edit by mod**: There are two Brainstorm ideas related to this:
[Idea #762: Better Wine integration](http://brainstorm.ubuntu.com/idea/762/)
[Idea #54: Make WINE a part of the default install](http://brainstorm.ubuntu.com/idea/54/)

---

### Post by goatflyer on 2006-08-11
The only gotcha I see is that newbie users will still have to run winecfg before attempting to use it.  I don't know if there is a way for Ubuntu gurus to automate that.

dosemu --- who else besides me needs that?  :P

---

### Post by kostkon on 2006-08-11
> **goatflyer said:**
> 
dosemu --- who else besides me needs that?  :P

IMO dosbox is better app for DOS emulation.

---

### Post by Perfect Storm on 2006-08-12
Bad idea in my opinion. If there's some space left on the Ubuntu CD, I think it should be used to something more useful.
Another thing is it's continuesly updating if you have added the right sourece to your repo. so nevertheless you gonna download the update(s) anyway.
Thirdly I think it would be a better idea if people trying to use native applications instead of rush off to the wine/Xover/<insert whatever> immedatly.

---

### Post by stoffe on 2006-08-12
If it's included by default it gives the impression that Windows applications will work out of the box, which is rarely true. Most things still don't work without serious manual tweaking, and many things don't work at all.

On top of that, Wine installed apps still are hidden in ~/.wine/drive_c/Program\ Files/ and that's not very easy to discover or for that matter use after it's discovered. Crossover Office adds a Windows Applications menu, something that Wine proper should have too.

There's more reasons too, but in general, Wine should be a conscious choice for now. 

Now, if adding the Wine repos and setting it up to use ALSA and a few other common things were added to CommonCustomizations, I would think that would be a nice thing.

---

### Post by Christmas on 2006-08-12
Wine was always working only half for me. I wouldn't like to see it included in the distribution by default, Linux must have its own applications not to try to make work the ones made for Windows. If that's possible (which at the moment it's not, at least not throught Wine) then it's OK, but it shouldn't be included anyway.

---

### Post by wedderburn on 2006-08-12
as much as i love wine it would give the wrong impression to new users wine is far from finished, in that i mean it require a fair bit of searching for most apps, new users are going to try it and feel it to be dodgy and think the os is inferior because of it, personal experience with my family has taught me this, now when i install Ubuntu i don't include wine or if i do i get the app to work but hide wine from them

a better idea would be to get a list of working apps make a Gui front end similar to crossover tightly integrate it into Ubuntu and make it seem smooth, and only install apps that work, make it modular so the apps install scripts can be downloaded via apt-get/synaptic.

there is a project called wine-doors working towards making wine easier

---

### Post by LordRaiden on 2006-08-12
I don't think that it should be included in the CD or installed by default. A new user should have the opportunity to try Linux native application's before thinking about getting Windows applications working.

That being said, it should be easier for a new user to install Wine from the wineHQ repositories. Including a small guide (HTML or PDF) with links and instructions would help. A link to an online guide (UDSF anyone?) with screenshots might more fitting.

We should try an preserve the notion that the core Ubuntu OS should fit in one CD. Wine is slightly hefty (can't remember between 4-16MB). But Wine should be a bit more "accessible" for a new user (arguably just having a link to the relevant UDSF page is enough - as a bonus, the user will learn something).

Also, arguably there are a lot of applications that *should* be on the Ubuntu ISO, but are not. I think it is better to just let the user know that there is tons more software available with the appropriate installation / configuration links.

---

### Post by mig96 on 2007-04-25
Wine should be included because there's a lot of windows applications out there, and the windows applications will just continue to be written, so Gutsy should be able to cope with it.

---

### Post by 23meg on 2007-04-25
It's a bad idea in many ways:

- There's no room for it on the CD

- It's a beast to maintain and secure

- It's developed very actively, and even minor updates can provide critical new functionality, so a single version on a CD lacks some functionality of the version from the upstream repository

- It will probably never be able to "cope with" most Windows apps, and installing it as default will give the contrary impression

- It will steer many new users away from using native Free apps, at least for a while

---

### Post by lyceum on 2007-04-25
> **23meg said:**
> It's a bad idea in many ways:

- There's no room for it on the CD

- It's a beast to maintain and secure

- It's developed very actively, and even minor updates can provide critical new functionality, so a single version on a CD lacks some functionality of the version from the upstream repository

- It will probably never be able to "cope with" most Windows apps, and installing it as default will give the contrary impression

- It will steer many new users away from using native Free apps

I agree for all these reason and would like to add:

- It is hard to use, it would have to be set up to work by default as well, and how would you do that so that EVERYONE is happy?

- it would confuse new users who would wonder why one thing works and another does not (I know 23meg already said this, but I like the way I said it better :))

I think it would be a better idea to have something pop up telling them they need WINE (like 7.04 does with things that are not set up to work the way the user wants) but even then Crossover would be better for new users as it is easier to use. So all round, I have to second this as a bad idea. Sorry, nice thought though!

---

### Post by Jengu on 2007-04-25
> **23meg said:**
> 
- There's no room for it on the CD


Valid reason.

> 
- It's a beast to maintain and secure


I'm not sure what this is supposed to mean. What maintenance work would need to be done? It is already packaged for Ubuntu. Nor does it need special work to be 'secured.' Windows apps run through wine can only access your home folder, just like any other app run by a user. This situation *could* be better if Ubuntu stepped up and did extra packaging work to have wine run in some sort of jail, since windows software is usually proprietary. But at this point using wine to run windows executables is no more dangerous than running any one of the many unofficial debs people post on this forum. In fact, it is actually less so since debs need to be installed through sudo and wine apps can be installed to your home folder.

> 
- It's developed very actively, and even minor updates can provide critical new functionality, so a single version on a CD lacks some functionality of the version from the upstream repository


Why is it a point against software to be included in the distro if it has frequent releases?

> 
- It will probably never be able to "cope with" most Windows apps, and installing it as default will give the contrary impression


It indeed would be annoying for launchpad to be flooded with wine bug reports. But this could be worked around by popping up a warning when a user double clicks an exe file in nautilus to run it, explaining that running windows apps is not supported by Canonical but provided as a convenience, that wine is imperfect, and that bugs should be reported to the wine bugzilla and provide a clickable link. I think this would be following the example set by the codec assistant.

> 
- It will steer many new users away from using native Free apps, at least for a while

Making window apps easy to run on linux will create far more free software users than it would take away I think. I would go so far as to say that most people who migrate to Linux still end up using wine, even in its current imperfect form, for one or more apps.

How about a compromise: If the user tries to run an exe file, or inserts a CD with an autorun.exe on it, pop up an explanation of why windows software doesn't work on linux (They're different OS!) and offer to download wine from the repos. Also include an explanation like I said above about where bug reports should go.

---

### Post by RAOF on 2007-04-25
Wine is already in universe, or at least was last time I checked.

I would be very surprised if it made it into Main.  That's the section for the programs officially supported by Cannonical, and wine would be an absolute pain to support officially.

---

### Post by mech7 on 2007-04-26
I think wine should be default.. the size reason is not that good a reason i think. Personally haven't used a cd in ages do they still make them? I always have to convert the iso's so they can be burned on dvdrw :( 
And even dvd's don't have that long of a lifetime anymore with bluray and hddvd slowly merging up :)

---

### Post by smartboyathome on 2007-04-26
They make CDs because some people (like me) have computers that can't burn DVDs. Then, this is godly.

---

### Post by garba on 2007-04-26
> **Jengu said:**
> 
How about a compromise: If the user tries to run an exe file, or inserts a CD with an autorun.exe on it, pop up an explanation of why windows software doesn't work on linux (They're different OS!) and offer to download wine from the repos. Also include an explanation like I said above about where bug reports should go.

this is a VERY valid suggestion, many newcomers click on .exe files and wonder when nothing happens... a pop up giving them directions of some sort would be extremely useful

---

### Post by chamberlain2006 on 2007-04-26
The points against having Wine included are very valid.  It's not that reliable, and people would be too confused.  I think a better option would be to have a pop-up when you double click on an exe, telling them that Window applications don't work on Linux, and point them to a page on the Ubuntu wiki that describes Linux programs as an alternative to Windows ones.

---

### Post by 23meg on 2007-04-26
> **Jengu]I'm not sure what this is supposed to mean. What maintenance work would need to be done? It is already packaged for Ubuntu. Nor does it need special work to be 'secured.'[/QUOTE]

WINE is in Universe said:**
> Why is it a point against software to be included in the distro if it has frequent releases?

It's not a point against all software; it's specific to WINE. In a lot of use cases I've seen, people seem to be heading to the WINE repositories for the latest version a month after each release.

[QUOTE=Jengu]It indeed would be annoying for launchpad to be flooded with wine bug reports. But this could be worked around by popping up a warning when a user double clicks an exe file in nautilus to run it, explaining that running windows apps is not supported by Canonical but provided as a convenience, that wine is imperfect, and that bugs should be reported to the wine bugzilla and provide a clickable link. I think this would be following the example set by the codec assistant.
[/QUOTE]

Sure, it can be done, but won't work exactly as intended, and the loss will outweigh the benefit, especially given that it's already an apt-get away. Default installation doesn't bring a huge benefit.

[QUOTE=Jengu]Making window apps easy to run on linux will create far more free software users than it would take away I think. I would go so far as to say that most people who migrate to Linux still end up using wine, even in its current imperfect form, for one or more apps.[/QUOTE]

I wouldn't say "most people", but yes, a lot of people do. And you have a point; it does bring an advantage. I'm just not of the belief that default integration in Ubuntu will add much to the already existent convenience of being able to run *some* Windows apps via WINE. I've also seen lots of people insisting on trying to get by with half-working Windows applications that they want to hang on to, which they run via WINE, instead of investigating Free alternatives, and default integration may strengthen that tendency.

---

### Post by smartboyathome on 2007-04-26
I don't think that Wine should be totally avoided. I use it all the time so that I can view Shockwave files in Ubuntu. So, I think that your option should be on the pop-up box along with the rest of the suggested options.

---

### Post by Anthem on 2007-04-26
I'm not against Wine in theory, but it's got a ways to go before it's ready for a stock install.  Check back when they hit 1.0.

---

### Post by wgrant on 2007-04-27
> **mig96 said:**
> Wine should be included because there's a lot of windows applications out there, and the windows applications will just continue to be written, so Gutsy should be able to cope with it.

No.

---

### Post by Rob Alderson on 2007-04-27
While I have some Windows programs that run in Wine I disagree with it being included as standard, I'd rather not have to use it at all, instead of giving programmers an excuse to be lazy we need to be forcing them to produce Linux native versions of their programs.

---

### Post by YokoZar on 2007-05-01
> **Rob Alderson said:**
> While I have some Windows programs that run in Wine I disagree with it being included as standard, I'd rather not have to use it at all, instead of giving programmers an excuse to be lazy we need to be forcing them to produce Linux native versions of their programs.Programs that run with Wine *are* native versions - Wine is a native library.

---

### Post by disturbedite on 2007-05-01
wine is included in kubuntu by default if i remember correctly.  (i installed feisty recently).

---

### Post by aamukahvi on 2007-05-01
> **disturbedite said:**
> wine is included in kubuntu by default if i remember correctly.  (i installed feisty recently).
Just because it's in the repos doesn't mean it's included by default.

---

### Post by disturbedite on 2007-05-01
duh, i know that.  that isn't what i meant.  i thought (correct me if i'm wrong) that wine was installed when i installed feisty.  but i went ahead and added the wine repos and updated wine...

like i said, i thought it was installed already, but if not, then obviously i just added the repo and installed wine, not upgraded it.

---

### Post by Yeeha on 2007-05-02
i totally agree, wine might not be completely ready yet but its much better than being completely without ability to run win programs. Some people dont have access to internet so they cant just get it from repos.

---

### Post by aamukahvi on 2007-05-02
> **disturbedite said:**
> duh, i know that.  that isn't what i meant.  i thought (correct me if i'm wrong) that wine was installed when i installed feisty.  but i went ahead and added the wine repos and updated wine...

like i said, i thought it was installed already, but if not, then obviously i just added the repo and installed wine, not upgraded it.
I seriously doubt it was installed by default, it's in Universe:
```
 **aptitude show wine**
Package: wine
New: yes
State: not installed
Version: 0.9.33-0ubuntu1
Priority: optional
Section: universe/otherosfs
```

---

### Post by disturbedite on 2007-05-02
as i said before, i might be wrong, so whatever...

---

### Post by Shin_Gouki2501 on 2007-05-02
im VERy new to linux i just installed 2 days ago xubuntu 7.04 then i wanted µ torrent to run  so i installed wine.
It took me about 5 mins. the hardest thing was how to start then my win app ^^
But all togehter it was very easy! :)

---

### Post by aamukahvi on 2007-05-02
> **Shin_Gouki2501 said:**
> im VERy new to linux i just installed 2 days ago xubuntu 7.04 then i wanted µ torrent to run  so i installed wine.
It took me about 5 mins. the hardest thing was how to start then my win app ^^
But all togehter it was very easy! :)
µtorrent is reported to run very well under wine. Also Photoshop 7 runs quite well and I even read somewhere that CS2 runs under the newest wine.

---

### Post by Shin_Gouki2501 on 2007-05-02
yes, but what i wanted to say is: it was REALLY easy to get it going IMO there are more important things to focus on :)

---

### Post by disturbedite on 2007-05-02
if you like utorrent, install ktorrent and use it.  its simliar in scope/look and it very resource friendly.  (you can even configure how "friendly" :) ).

---

### Post by aamukahvi on 2007-05-02
And if you use Gnome, I can recommend Deluge. Very nice, although not yet as many features as KTorrent.

---

### Post by hikaricore on 2007-05-02
> **fujitsu said:**
> No.

QFT

Best post ever.  :lolflag:

---

### Post by k99goran on 2007-05-03
> **aamukahvi said:**
> µtorrent is reported to run very well under wine. Also Photoshop 7 runs quite well and I even read somewhere that CS2 runs under the newest wine.
I tried a portable version of Photoshop CS2 under Kubuntu and it worked. I'm sure it will under Ubuntu as well.

---

### Post by Longer on 2007-05-03
I`m not sure to this idea... Wine will need a lot of space on cd... There should be something more important... More usefull... Like MC... :) What is more most people don`t use programms for windows... Typing: apt-get install something... is easier... :)

---

### Post by hartz on 2007-05-12
I think a lot of users would benefit from having Wine installed.  A wizard to configure applications found on the Windows partitions would be nice too.

I realize the Wine is not exactly stable, and that applications often needs MS Windows (system/dll) files to be copied over into the wine directories, so this would probably be a somewhat optimistic suggestion for Gutsy, but there it is.

---

### Post by Enverex on 2007-05-12
> **hartz3 said:**
> I think a lot of users would benefit from having Wine installed.

Not really, Wine is complicated to use and the fallout from new users posting rubbish back to the WineHQ site is increasing. If someone knows they need Wine and are intuitive enough to be able to figure out how to use it, they will install it.

> **hartz3 said:**
> A wizard to configure applications found on the Windows partitions would be nice too.

The only time this should EVER be done is if the application fails to install into Wine for one reason or another. It should not be done normally.

> **hartz3 said:**
> I realize the Wine is not exactly stable

One of the main reasons it should not be put in by default. It's not ready for the general public.

> **hartz3 said:**
>  and that applications often needs MS Windows (system/dll) files to be copied over into the wine directories

Again, this shouldn't be done unless an application EXPLICITLY asks for a DLL that Wine does not have built-in. Copying over DLL files willy-nilly will just break Wine.

---

### Post by Auria on 2007-05-12
There are many other Wine threads and the answer has always been no... its alpha/beta (not sure?), complicated, takes oo much place for the CD, would make users think all windows programs are supported, etc.

---

### Post by 23meg on 2007-05-12
I've merged the thread with another one on including WINE by default.

---

### Post by hartz on 2007-05-14
Having read your answers and the answers to the older conversation, I concede. :cool:

---

### Post by ArtificialSynapse on 2007-05-14
The reality is that people need a slow transition into Ubuntu, and the best way to do that is to allow compatibility on as many levels as possible. Implementing wine by default wouldn't discourage users from free software, because they're still emerged in the free environment, I garentee that a new ubuntu user isn't going to be more likely to go out to the store and buy closed source software, when they KNOW that there is a free alterative right at their finger tips, but people don't want to drop everything they're used to and dramatically change.  

Think about it this way : You're a life long Windows user but you like the idea of free software and want to give linux a try, specifically Ubuntu. Are you more likely to make the transition knowing that some of your old programs that you're comfortable with will run? Or knowing that absolutely every program that you've used for the last 10 years will be entirely different?

---

### Post by Enverex on 2007-05-14
> **ArtificialSynapse said:**
> The reality is that people need a slow transition into Ubuntu, and the best way to do that is to allow compatibility on as many levels as possible. Implementing wine by default wouldn't discourage users from free software, because they're still emerged in the free environment, I garentee that a new ubuntu user isn't going to be more likely to go out to the store and buy closed source software, when they KNOW that there is a free alterative right at their finger tips, but people don't want to drop everything they're used to and dramatically change.  

Think about it this way : You're a life long Windows user but you like the idea of free software and want to give linux a try, specifically Ubuntu. Are you more likely to make the transition knowing that some of your old programs that you're comfortable with will run? Or knowing that absolutely every program that you've used for the last 10 years will be entirely different?

Wine is heavy Beta with many Alpha-like parts, it's not simple to use and, as shown by many forum posts, most people can't figure out how to use it. It's not ready for the "newbie" crowed.

---

### Post by kragen on 2007-05-14
I saw this on slashdot and was instantly convinced:

> I do not want to position Ubuntu and Linux as a cheap alternative to Windows ... While Linux is an alternative to Windows, it is not cheap Windows. Linux has its own strengths, and users should want it because of those strengths and not because it's a cheap copy of Windows

Someone at Dell explaining why they didn't want wine shipped with Ubuntu.

---

### Post by Enverex on 2007-05-14
> **kragen said:**
> Someone at Dell explaining why they didn't want wine shipped with Ubuntu.

ROFL. Mark Shuttleworth doesn't work at Dell ;)

---

### Post by foerdi on 2007-05-30
wine in main +1

bad idea? a lot of work?
i know.

but people (/gamers) need it

---

### Post by 23meg on 2007-05-30
[QUOTE=foerdi]but people (/gamers) need it[/QUOTE]

No, they *want* it, without any rational explanation why.

---

### Post by RAOF on 2007-05-31
> **foerdi said:**
> wine in main +1
...
Maybe once there's a 1.0 release, or they start releasing versions that don't break existing working stuff.  It's perfectly suited to Universe (and community maintainence) at the moment.

Incidentally, this [Gutsy spec](https://wiki.ubuntu.com/WineGutsySpec?highlight=%28wine%29) is probably of interest to people.

---

### Post by Old Pink on 2007-05-31
> **mig96 said:**
> there's a lot of windows applications out there, and the windows applications will just continue to be written

**[FONT=Arial Black][SIZE=7][COLOR=Red]UBUNTU IS _NOT_ WINDOWS[/COLOR][/SIZE][/FONT]**

---

### Post by calande on 2007-06-07
> **23meg said:**
> It will steer many new users away from using native Free apps, at least for a while

This is not a problem. Now, not being able to run your favorite applications because they are Windows-only *is* a problem.

---

### Post by 23meg on 2007-06-07
> **calande]This is not a problem. [/QUOTE]

I've witnessed enough people in support forums wrestling with semi-functional Windows apps running via WINE for long periods purely out of habit, instead of seeking Free alternatives, to think otherwise. 

[QUOTE=calande said:**
> This is not a problem. Now, not being able to run your favorite applications because they are Windows-only *is* a problem.

A problem which WINE isn't the ultimate solution for, and which providing WINE by default won't fix.

---

### Post by calande on 2007-06-07
So, how do I use AutoCAD on Ubuntu?

---

### Post by 23meg on 2007-06-07
You search the [WINE application database]("http://appdb.winehq.org/") to see if the version you'll be using is known to work, install WINE, run it, and hope it works. You can also search the forums or elsewhere for a guide that describes how to do it.

---

### Post by kknd on 2007-06-09
I don't like wine or other windows compatibility layer installed by default.
It's better to leave ubuntu as clear as possible.

---

### Post by mig96 on 2007-06-12
did i start flame wars?

---

### Post by 23meg on 2007-06-12
No, just a discussion.

---

### Post by bl3s5in on 2007-06-12
Wine should be integrated into the system seamlessly.  You should be able to click on a setup.exe and be shown the install. If we take out the text based part of Wine in Ubuntu, it will attract a much larger user base.

---

### Post by RAOF on 2007-06-13
> **bl3s5in said:**
> Wine should be integrated into the system seamlessly.  You should be able to click on a setup.exe and be shown the install. If we take out the text based part of Wine in Ubuntu, it will attract a much larger user base.

You already can.  I can, certainly.  Although whether or not that setup.exe actually **works** is a bit more up in the air!

---

### Post by slimdog360 on 2007-06-13
No one wants a bloated OS, the inclusion of wine would make the realisation of Ubuntu being bloated (if it isn't already by some standards) more likely.

---

### Post by calande on 2007-06-13
I'm sure many people would prefer the "bloat" of WINE to the lack of functionality of not being able to install Windows applications out of the box.

---

### Post by Ryoushi19 on 2007-08-13
I've got a great idea.  Rather than include wine, how about include a script to pop up and say something along the following:

This file is not a native Linux application, and is designed to run on Windows systems.  It is possible, however, that you may be able to run it with Wine.  There is a chance it may not work, however, if you still wish to install wine, _click here_.

That way, you don't have to worry about putting it on the CD, but it's still friendly enough for users to get it.

---

### Post by graigsmith on 2007-08-13
once i accidently ran a windows virus with wine.  Lets not open the default install up to user runnable programs.  it's a bad idea.

---

### Post by Prosthetic Head on 2007-08-13
I'm dead against this for so many reasons. 
Why add wine by default? It's already in universe. Most ubuntu users i know don't use it and those who do have to go through some trauma to get anything usefull out of it..

---

### Post by GuidoCalvano on 2007-08-13
I haven't read the middle of the six(!) pages, as after page one things got quite repetive for a while.

I aggree with mig96 in that wine should be made more accessible. I don't think it is realistic to think that gutsy or any os or application can cope with windows applications. Hell windows can't even do that.

A popup would make it both completely user friendly and accessible I aggree with Ryoushi19, but you may have to add a bit because graigsmith is also right.

I suggest;
"This file is not a native Linux application, and is designed to run on Windows systems. It is possible, however, that you may be able to run it with Wine. However there is a chance it may not work **and the file could even damage your system**. If you still wish to install wine, click here."

Ofcourse then synaptic is opened to install it, which obviously still requires proper passwords and user permission.

---

### Post by Alexander2007 on 2007-08-14
I don't think that Wine should be included in Gusty. Running Windows applications weaken Linux in my opinion. New people will switch to Linux and look for windows applications instead of the native applications that should be used. Software developers will also see less need to distribute software for Linux as they will run through  Wine. Wine is also not stable or polished enough for general consumption.

---

### Post by runemaste644 on 2007-09-09
> **23meg said:**
> It's a bad idea in many ways:

- There's no room for it on the CD

Unless you use a 4.7 GB DVD. And you could make an ISO image without all the special programs pre-installed, so that would solve that problem.

---

### Post by smartboyathome on 2007-09-09
> **runemaste644 said:**
> Unless you use a 4.7 GB DVD. And you could make an ISO image without all the special programs pre-installed, so that would solve that problem.

So are you suggesting that there should be a version of Ubuntu that is MADE for Windows users that want to install their stuff (which may not even work !!!) on it instead of using the stuff that is already provided? If so, that would totally detour the user away from the point of Ubuntu: to make it and its software free (the average windows software is not free).

---

### Post by 23meg on 2007-09-09
> **runemaste644 said:**
> Unless you use a 4.7 GB DVD. And you could make an ISO image without all the special programs pre-installed, so that would solve that problem.

A DVD version of Ubuntu is available, with all packages from the *main* and *restricted* components. Again, moving WINE into *main* means having to maintain it to the same standards as the rest of the packages in that component.

---

### Post by 23meg on 2007-09-09
[QUOTE=smartboyathome]So are you suggesting that there should be a version of Ubuntu that is MADE for Windows users that want to install their stuff (which may not even work !!!) on it instead of using the stuff that is already provided?[/QUOTE]

[Ubuntu Ultimate]("http://ubuntusoftware.info/ultimate/") ships with up to date versions of WINE; maybe those users should resort to it, or a similar derivative.

---

### Post by nonewmsgs on 2007-09-09
WINE is a pain.  i once had something working on it, but it's definitely not main material yet.

---

### Post by Sturmeh on 2007-10-06
It even gives Microsoft a reason to blame ubuntu for loosing 1% of their marketshare.

It's not hard to install, it's in the default repo's. xD

---

### Post by Lord Illidan on 2007-10-06
While I don't think it should be included as default, a way of popping up a window if the user clicks on an .exe will be quite userfriendly.

It could be like the codec package, giving some warning, and at the same time, providing a way how to easily install wine.

Most users don't know about wine yet. They download Ubuntu, they want to install an exe, why not make it easier for them? **It should be their choice whether to use native applications or not.**

---

### Post by RevolutionMaster on 2007-10-11
Good idea. Possibly list in software manager?

---

### Post by 23meg on 2007-10-11
[QUOTE=Lord Illidan]**It should be their choice whether to use native applications or not.**[/QUOTE]

Is it not their choice at the moment?

---

### Post by Frak on 2007-10-11
I, myself, don't like this idea. I rarely ever use Wine, and wouldn't want it on my system.

---

### Post by olskar on 2007-10-12
Dont like this idea..I think linuxsoftware should be used as far it is possible. If the user needs wine for photoshop or something he/she can easily get it from the repos.

---

### Post by slavik on 2007-10-13
I am against wine by default for a simple reason: something similar to this killed OS/2

if developers get into the mindset of "let's code for windows and there's wine on linux anyway" Linux will see the same amount of native apps as there are. This is already happening with .NET and Mono.

---

### Post by Boaslad on 2007-10-14
I switched to Linux simply because it ISN'T Windows. I don't use Wine... ever. If I want to use a Windows Ap. I go and I use Windows. I don't see Mr. Bill adding any "Linux Ap Launcher"s in his installations, do you? Ubuntu is not suppose to be a Windows clone. It's an alternative to Windows. Something else entirely. If they want to swap, they should come open minded enough to realize that Linux is it's own OS and has it's own set of programs. Many of which are just as, if not MORE powerful that their Windows counterparts. Adding Wine to the installation is a bad idea in that it gives the impression that Ubuntu is just trying to be Windows in another wrapper.

---

### Post by snake444 on 2007-10-15
i used programs in windows that they dont have a clone program in linux
so i need to use wine and i know nobody will write such program to linux because  alot of people doesnt need it...
and i think that you should include wine when it will be more stable and userfriendly because you think that if you dont use it nobody needs it and its wrong you see in this theread how many people need wine included in gutsy..

---

### Post by 23meg on 2007-10-15
[QUOTE=snake444]you see in this theread how many people** need wine included** in gutsy..[/QUOTE]

No, we see in this thread how many people (who posted to this thread) use WINE, which is already included as an option. We don't see anything about why people *need* it by default.

---

### Post by Enverex on 2007-10-15
> **snake444 said:**
>  you see in this theread how many people need wine included in gutsy..

So what is to stop them install it themselves? Are they really that lazy that they need it pre-installed?

Wine is still heavy beta and shouldn't be included because it's not entirely simple to use, sure as hell not as simple as "omg i can't just click my game and have it work, waah" mentality that lots of Ubuntu users have.

It's not in a state that many people should be using and those that can figure it out can install it themselves.

---

### Post by Akash Singhal on 2008-07-04
Why has Ubuntu never been designed to execute .exe files..everytime we have to use them, we have to use wine.this is much frustating...

---

### Post by studyhard888 on 2008-07-04
> **Akash Singhal said:**
> Why has Ubuntu never been designed to execute .exe files..everytime we have to use them, we have to use wine.this is much frustating...


if you execute .exe files for the most time ,i recommend that you use xp or vista ,running ubuntu in Vm .

---

### Post by gunashekar on 2008-07-04
Perhaps nobody has got around to integrate a windows abstraction layer with Linux. It might be a great service if someone would do that. I certainly would love to have an operating system that can run software designed for windows or OS-X or linux.

---

### Post by aysiu on 2008-07-04
Mark Shuttleworth has already said it's not going to happen.

From [Ubuntu Founder: No Emulation Software for Dell Systems](http://www.eweek.com/c/a/Linux-and-Open-Source/Ubuntu-Founder-No-Emulation-Software-for-Dell-Systems/): [quote=Mark Shuttleworth]I do not want to position Ubuntu and Linux as a cheap alternative to Windows. While Linux is an alternative to Windows, it is not cheap Windows. Linux has its own strengths, and users should want it because of those strengths and not because its a cheap copy of Windows.[/quote] When do you ever have Mac users expecting to be able to run .exe files natively in Mac? Or Windows users expecting .deb files to double-click-run in Windows?

It makes no sense for people to expect .exe files to just run in Ubuntu without any kind of helper software installed.

---

### Post by Frak on 2008-07-04
Let's automount .dmg files and run .app files natively.

I want my iWork ;)

---

### Post by gunashekar on 2008-07-04
Maybe Mark Shuttleworth could rethink soon. We can see attempts like [Interix]("http://en.wikipedia.org/wiki/Interix") and Wine / crossover, having a reasonable demand. If this is what people want, I am of the opinion that it will only add to Ubuntu's greatness to enable interoperability.

---

### Post by aysiu on 2008-07-04
No one is preventing anyone from installing and running Wine themselves, but I think it makes sense for the default installation to encourage you to at least give native Linux applications a chance before falling back to Windows-only programs and *hoping* they run in Wine.

---

### Post by gunashekar on 2008-07-04
At a time when Vista is facing a resistance and XP ceases to be sold, perhaps it is the right time to strike a death blow to Microsoft by making the idea of a paid OS meaningless. If most of the software I need / am used to can be installed on an open source OS, I might stop using Windows. Over time, I would start seeing the merits of Open Source applications too.

---

### Post by aysiu on 2008-07-04
> **gunashekar said:**
> At a time when Vista is facing a resistance and XP ceases to be sold, perhaps it is the right time to strike a death blow to Microsoft by making the idea of a paid OS meaningless. If most of the software I need / am used to can be installed on an open source OS, I might stop using Windows. Over time, I would start seeing the merits of Open Source applications too.
Yeah, and the first thing people should look for are native Linux alternatives.

It's only after they've tried that that they should try running native Windows applications through a compatibility layer like Wine.

And nothing is stopping people from installing Wine themselves.

---

### Post by Frak on 2008-07-04
> **gunashekar said:**
> At a time when Vista is facing a resistance and XP ceases to be sold, perhaps it is the right time to strike a death blow to Microsoft by making the idea of a paid OS meaningless. If most of the software I need / am used to can be installed on an open source OS, I might stop using Windows. Over time, I would start seeing the merits of Open Source applications too.
Three issues with that:

1. You're promising a hassle-free alternative.
2. Wine still isn't perfect. It still has bugs, and alot of them at that.
3. That's promising to stop using Windows to start using Windows.

---

### Post by aysiu on 2008-07-04
I think is totally backwards.

You don't move people to an open source operating system in order to use Windows applications.

You start them using open source applications on Windows first. Then you move them to an open source operating system later.

---

### Post by gunashekar on 2008-07-04
Well, I am only suggesting based on my experience. I flirted with GNU/Linux on and off since the time Red Hat was free. I started using linux seriously only when I was certain that some of my preferred windows applications could coexist with Linux - initially dual boot, later wine. Only when I was confident that I could live without windows or wine, I switched completely to Linux. Even now I am forced to save some documents in MS Office formats from within OpenOffice so that Others I work with would be comfortable to work further on them.

---

### Post by Akash Singhal on 2008-07-05
the main problem is that most of softwares presently in the market are compatible only for windows and use .exe files.
Moreover installation through wine are always not successful...In such case we need ubuntu to execute .exe files too.
I think this is the main reason why ubuntu or any other distro of linux is not so popular among people

---

### Post by aysiu on 2008-07-05
> **Akash Singhal said:**
> the main problem is that most of softwares presently in the market are compatible only for windows and use .exe files.
Moreover installation through wine are always not successful...In such case we need ubuntu to execute .exe files too.
Installing Wine by default doesn't solve the problem that non-native executables don't always work with Wine or the problem that most software comes as .exe.

> I think this is the main reason why ubuntu or any other distro of linux is not so popular among people Since most people use Windows, most popular software is designed for Windows. So in other words, being the most popular keeps you popular. Being less popular is the main reason the less popular operating systems are less popular. Is that what you're saying? If so, I agree wholeheartedly. But that has nothing to do with installing Wine by default.

---

### Post by Lster on 2008-07-05
I'm pretty indifferent but on the side of leaving it out. I don't think it constitutes a "bare-minimum" application so I suppose it should be left out.

---

### Post by Brinstar on 2009-03-10
wine should be included with needing to download through synaptic or without using apt-get.

think of the thousands of gamers who need to go through the unecessary step of installing wine. why not remove this hassle? if something is so important to so many of the users, the developers need to listen.

what do others think?

---

### Post by Simian Man on 2009-03-10
There are a lot of good software that should be included that isn't  Wine isn't one of them.  First of all it is fairly large, second of all it shouldn't be seen as an "official" part of a Linux system, it's more of a hack and crutch for those that need it.  Thirdly it is fairly buggy and doesn't make for a good impression of what Linux is all about.

---

### Post by Brinstar on 2009-03-10
> **Simian Man said:**
>  it's more of a hack and crutch for those that need it. 

yes, it's a crutch. but lots of people depend on crutches to get things done. its a stopgap until linux can do better. at the moment, linux does not do games better. hence crossover, cedega etc. maybe one day, but that day is not today. hopefully linux will catch up and even overtake windows soon. but it hasn't yet.

> **Simian Man said:**
> doesn't make for a good impression of what Linux is all about.

what is linux all about? making things harder for the users, so they eventually give up and go back to windows? or making things easier so they stick around and start to realise linux is a better alternative? if you don't let them adjust slowly, by giving them things like wine to let them come over gradually, you are just going to end up alienating people.

---

### Post by darthmob on 2009-03-10
> **Brinstar said:**
> think of the thousands of gamers who need to go through the unecessary step of installing wine. why not remove this hassle?you call it a hassle to type 'sudo apt-get install wine' once in a terminal (or alternatively use synaptic / add-remove program manager)? the packet manager has to be one of the most comfortable functions of ubuntu.

it's ridiculously easy to install wine compared to what has to be done to get most of the games / programs to run properly with it. investing hours of fiddling with not working sound / graphic problems / network problems is what I call hassle. ;)

---

### Post by Simian Man on 2009-03-10
> **Brinstar said:**
> yes, it's a crutch. but lots of people depend on crutches to get things done. its a stopgap until linux can do better. at the moment, linux does not do games better. hence crossover, cedega etc. maybe one day, but that day is not today. hopefully linux will catch up and even overtake windows soon. but it hasn't yet.

Linux doesn't need to do any "catching up".  The reason that games don't work out of the box on Linux has nothing to do with any technical limitations.  Including wine would encourage people to use their old apps from Windows like utorrent and itunes when better software exists for Linux.

> **Brinstar said:**
> 
what is linux all about? making things harder for the users, so they eventually give up and go back to windows? or making things easier so they stick around and start to realise linux is a better alternative? if you don't let them adjust slowly, by giving them things like wine to let them come over gradually, you are just going to end up alienating people.

The benefits of Linux, for me, include freedom and stability.  Neither of these really apply to apps run in wine.  If Linux is an OS that runs their Windows software, only not as well, what reason do people have for sticking with it?

This is not to mention that to get many games to work you have to circumvent DRM protections.  I don't really care about this, but it is technically illegal and, again, kind of goeas against the spirit of Linux.

wine is an amazing thing, don't get me wrong.  It just shouldn't be included as part of a basic Linux install.

---

### Post by Brinstar on 2009-03-10
this is going slightly off the point, but installing the more compatible dev version is not as simple as 'sudo apt-get install wine'. my point is that it helps so many people adjust more easily to linux.

---

### Post by cogadh on 2009-03-10
Wine is not needed because the vast majority of Linux users will simply use the native alternatives to Windows apps that are already part of Ubuntu. The only real exception to this is gaming and in those circustances, installing Wine is a simple process. Why give everyone what only a few actually want?

---

### Post by Simian Man on 2009-03-10
> **cogadh said:**
> Why give everyone what only a few actually want?

Good point.  I don't use wine, so why should I have it installed on my system?  We already mentioned the size this will take up on the install media, but will also waste users hard drives, network bandwidth for downloading the media, network bandwidth for updates...

---

### Post by Dougie187 on 2009-03-10
If you think that out of installing a game in linux the most complicated process is installing wine, then you are sorely mistaken. It's not like installing wine by default would make anyones life easier, it would be there for the people who aren't going to use it taking some space up. And for those who don't know how to use it, they would try and with the vast majority of game be disappointed by how poorly it supports most applications. 

Granted it works great on some games, and its one of the few options people have to use, but its not the most user friendly program. Especially if you are trying to install something that takes a lot of tweaking.

In the end, installing it by default wouldn't make anyones life easier.

---

### Post by Brinstar on 2009-03-10
> **Simian Man said:**
> Good point.  I don't use wine, so why should I have it installed on my system?  We already mentioned the size this will take up on the install media, but will also waste users hard drives, network bandwidth for downloading the media, network bandwidth for updates...

yes this is a good point, but i could argue that several of the installed apps never get used. hopefully things like the package usage survey will help sort this out.

---

### Post by mobilediesel on 2009-03-10
> **Simian Man said:**
> The reason that games don't work out of the box on Linux has nothing to do with any technical limitations.

Exactly. Wanting to run Windows programs in Linux is like wanting to run Commodore 64 BASIC programs in Python. Sure, you can probably get it to work, but why not write a new program for the new platform?

If the game companies won't support Linux, vote with your money. Tell them you're willing to buy their software if they provide a version you can use natively. Or just keep using Windows. Whatever.

---

### Post by kidux on 2009-03-10
No, I don't think it should be. It is a fairly specific piece of software that not everyone is going to need. On top of that, many times you need a different version than current as the ability to run software changes with each release. What may have worked the entire time is now broke kind of thing.

As it stands, I almost think there is too much installed by default, and the use of meta-packages can be infuriatingly frustrating sometimes.

---

### Post by Brinstar on 2009-03-10
> **mobilediesel said:**
> Exactly. Wanting to run Windows programs in Linux is like wanting to run Commodore 64 BASIC programs in Python. Sure, you can probably get it to work, but why not write a new program for the new platform?

If the game companies won't support Linux, vote with your money. Tell them you're willing to buy their software if they provide a version you can use natively. Or just keep using Windows. Whatever.

i am voting with my money, but things in the game industry (thanks to DirectX) are not going to change for a couple of years at least, no matter what. Ubuntu is definitely the best thing to happen to the linux game industry probably ever, because linux is finally starting to go mainstream and become a significant competitor to ms, which means soon enough game developers will have to start looking at cross-platform libs for game engines. i, like many of you, look forward to the day games of the calibre of Portal and Oblivion finally get native linux ports.

---

### Post by cogadh on 2009-03-10
> **Brinstar said:**
> yes this is a good point, but i could argue that several of the installed apps never get used. hopefully things like the package usage survey will help sort this out.
If you are talking about the "popularity-contest" package, considering participation is voluntary, it really isn't going to tell anyone much. People like me aren't going to participate in it because we don't like having something running on our system that "calls home" on a regular basis, wasting system resources and bandwidth; plus there are admitted (potential) privacy problems with the package. All you are going to get are a limited number of users willing to deal with that, which I don't think is going to give anyone a true sampling of what package usage is really like on Ubuntu.

---

### Post by Brinstar on 2009-03-10
> **cogadh said:**
> I don't think is going to give anyone a true sampling of what package usage is really like on Ubuntu.

true but then what else do you suggest?

---

### Post by cogadh on 2009-03-10
I don't suggest anything. I don't believe we need things like the package survey, since all the OS should have are the common basics that every OS should have. Anything beyond that can be added manually as wanted/needed/required, which is why distros like Ubuntu have such robust and easy to use package management.

EDIT - Just to expand on this a bit, the problem with trying to create an OS that is appealing to the greatest number of users is what you actually end up with is an OS that is truly bloated and is appealing to almost no one or is only appealing to the lowest common denominator (for want of a better term). Adding Wine to the base Ubuntu install would be a huge step towards that bloated, generically appealing but actually unappealing OS.

---

### Post by Simian Man on 2009-03-10
> **Brinstar said:**
> i am voting with my money, but things in the game industry (thanks to DirectX) are not going to change for a couple of years at least, no matter what.

Not really.  The fact is that most games *are* cross-platform.  Playstaion and Nintendo systems actually use a rendering API based partially on OpenGL.  If Linux were a viable gaming platform, porting existing games to Linux would actually be fairly easy.  Only games that only target Windows + Xbox actually depend on DirectX.

The problem is that the intersection of people who buy games and people without either a console or a Windows PC is incredibly small.

---

### Post by betrunkenaffe on 2009-03-10
I'm a gamer and I disagree with you.

BTW, this link really just says how much knowledge is needed to install wine.

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

And taken from that site:

Alternative command Line Instructions for Installing Wine:

It is also possible to add the Wine repositories and install via the command line, as follows. These may be useful on Kubuntu, Xubuntu, and other Ubuntu derivatives.

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following into your terminal:

```
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
```

Next, add the repository to your system's list of APT sources:

For Ubuntu Intrepid (8.10):
```
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list
```

For Ubuntu Hardy (8.04):
```
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
```

Then update APT's package information by running 'sudo apt-get update'. You can now install Wine normally or by typing 'sudo apt-get install wine' into the terminal.

The copy paste almost broke my fingers..

And I pretty much echo the previous statements, there are far better things to use the space for, it's not a technical miracle to install. If you want to use it, you'll need to learn Linux alot more anyways to get it working for most of your games. It will waste space for alot of people (myself included since I dual boot my desktop and use my lappy almost all the time [gameless]) and there will be so many complaints about how the "official" Linux support for Windows games has problems. 

Forums such as this one are good because you can get help in your specific distribution but to be honest, I've gotten all my games to work in wine without looking at this forum once (winehq app db + google).

---

### Post by pparks1 on 2009-03-10
I don't really want WINE installed by default because it's something that I simply don't use.   When I made the decision to install and use Linux, I stuck with software designed for the system.   For my gaming needs, I either use my console or my Windows computer

---

### Post by Therion on 2009-03-10
No.  I don't think it should be.  I'm sure if you ask enough people you'll find someone who wants/needs/uses any single application or package you could rattle off.  But what gets included as part of the default install is a balancing act of usefulness for the largest segment of the targeted demographic against available space on standard install media; that being, at the moment, a 700MB CD.

Now if Canonical wants to create a Live**DVD** for routine distro releases I think that would be great (yes I know there are LiveDVD downloads of Ubuntu but as far as I know they really only include additional language packs).  That would give them a lot more flexibility in what's packaged with a default installation.

Further, I have to wonder about Wine with regard to FOSS standards and principles.

---

### Post by Brinstar on 2009-03-10
> **betrunkenaffe said:**
> I'm a gamer and I disagree with you.

BTW, this link really just says how much knowledge is needed to install wine.

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

And taken from that site:

Alternative command Line Instructions for Installing Wine:

It is also possible to add the Wine repositories and install via the command line, as follows. These may be useful on Kubuntu, Xubuntu, and other Ubuntu derivatives.

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following into your terminal:

```
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
```

Next, add the repository to your system's list of APT sources:

For Ubuntu Intrepid (8.10):
```
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list
```

For Ubuntu Hardy (8.04):
```
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
```

Then update APT's package information by running 'sudo apt-get update'. You can now install Wine normally or by typing 'sudo apt-get install wine' into the terminal.

The copy paste almost broke my fingers..

And I pretty much echo the previous statements, there are far better things to use the space for, it's not a technical miracle to install. If you want to use it, you'll need to learn Linux alot more anyways to get it working for most of your games. It will waste space for alot of people (myself included since I dual boot my desktop and use my lappy almost all the time [gameless]) and there will be so many complaints about how the "official" Linux support for Windows games has problems. 

Forums such as this one are good because you can get help in your specific distribution but to be honest, I've gotten all my games to work in wine without looking at this forum once (winehq app db + google).

thanks dude, i already have it installed, as you say its not that hard to install, and again, there are other packages i think are not being used as much as warranting the space on the iso.

---

### Post by Brinstar on 2009-03-10
haha, 22-3, i think a mr. (ms.?) hikaricore is smiling somewhere... :)

---

### Post by cmay on 2009-03-10
no .

do you know earOS. 
it has like a couple of other ubuntu derivatives wine installed per default. and it has virus protection and a firewall. its a media center distro from Denmark actually and it has nothing of value none what so ever for a linux user that knows these two simple things. 

you dont need antivirus in linx and you cant run windows programs in linux or any other unix system wiht out some kind of software emulation and its not worth it. 

earOS just as the other newbie distros that includes wine is failing one thing in the attemts to become more atrative to new users of linux. it has wine installed and wine is not a perfect program that simplly just works. all other good things that could have been done to let linux shine it its own right is not done and simply because we in denmark can not even when producing a linux distro for media center imagine we do not need antivirus and must have wine so we can run microsoft programs on a unix clone. 

earOS is pretty much all dead. same as the other distros i seen that pops up using the wine as default app as main feature is . 

i voted no. 
i want ubuntu to live a long linux live and it will if wine is not a part of it from the begining.

---

### Post by hikaricore on 2009-03-10
> **Brinstar said:**
> haha, 22-3, i think a mr. (ms.?) hikaricore is smiling somewhere... :)

I take no pride in your overconfidence that everyone would agree with you.
My job here is to just keep things sane which this thread did much better at than your first two.  :p

---

### Post by Brinstar on 2009-03-10
> **hikaricore said:**
> I take no pride in your overconfidence that everyone would agree with you.
My job here is to just keep things sane which this thread did much better at than your first two.  :p

:) no worries, we're all friends here...

---

### Post by FrozenFox on 2009-03-10
If wine worked perfectly, that would be a fine idea. 

However, it doesn't. 

I agree with a couple others who've posted before this..

People need to understand that wine / running windows programs (and the huge list of accompanying bugs) is not part of the native linux experience. In general, they won't ever understand that if they're spoon-fed buggy compatibility out-of-the-box. They MIGHT get it if they have to go and install wine manually. That forces the mental distinction between the OS and 3rd party software that can run windows stuff, shifting focus from "linux" to "wine".

**To summarize, when forced to look up information on running windows programs** in linux instead of having it OOTB, I'm convinced most **users thankfully become**: 

**1) More likely to understand wine's pros & cons & legality**
   ["It's programmed by a community, not microsoft?!"]

**2) Less likely to expect perfection**
   ["But it's part of the system! Why doesn't it work?!"]

**3) More likely to look for native linux programs**
   ["Linux Is Not Windows & Wine is a LAST RESORT"]

**4) Less likely to call wine problems "linux problems"**
   ["OMFG linux is gay, my warez dont work!11!!"]
   ["OMFG this pen is gay, my #2 pencil lead dont work!11!!"]

---

### Post by kidux on 2009-03-10
> **FrozenFox said:**
> If wine worked perfectly, that would be a fine idea. 

However, it doesn't. 

I agree with a couple others who've posted before this..

People need to understand that wine / running windows programs (and the huge list of accompanying bugs) is not part of the native linux experience. In general, they won't ever understand that if they're spoon-fed buggy compatibility out-of-the-box. They MIGHT get it if they have to go and install wine manually. That forces the mental distinction between the OS and 3rd party software that can run windows stuff, shifting focus from "linux" to "wine".

To summarize, if you're forced to look up information on running windows programs in linux, I'm convinced most users would be: 

**1) More likely to understand wine's pros & cons & legality**
   ["It's programmed by a community, not microsoft?!"]

**2) Less likely to expect perfection**
   ["But it's part of the system! Why doesn't it work?!"]

**3) More likely to look for native linux programs**
   ["Linux Is Not Windows & Wine is a LAST RESORT"]

**4) Less likely to call wine problems "linux problems"**
   ["OMFG linux is gay my warez dont work!11!!"]
   ["OMFG this pen is gay, my #2 pencil lead dont work!11!!"]
Agreed. WINE is more of an advanced operation than replacing Office with OOo.

---

### Post by cmay on 2009-03-10
i been using 64studio for audio recording for a long time. the upgrade to next version has wine installed per default as a single program depends on it. i am very angry wiht this as it causes me many more trouble than it will ever solve. i have therefore uinstalled this upgrade and gone back to the last stable release. 

i imagine that  the loss of users are many more in ubuntu than the new comers to ubuntu who would like wine installed per default if that was ever to happen. 

it is simply a bad bad idea that gives more trouble than it offers solutions. 
in fact i would rather that they (meaning anyone) started selling a ubuntu wiht cross over and wine and lots of games and the restrictive codecs and named it something that has no connection to ubuntu what so ever. 

i think when we look at treads where a  linux distro gets bashed its pretty much a distro that tries to do this and no one likes it that much in the linux community if judged by the post there has been in these forums. ubuntu xp as the last example. i cant even rembember the other ones as when ever a distro does this and start sell it as microsoft office compatible and so on it is something i think of as not worht my time to even remember the name of the distribution. you can buy xandros if you want a linux that wants to be like windows. ubunt is fine as is.

---

### Post by cogadh on 2009-03-10
A perfect example of that is [Linspire]("http://en.wikipedia.org/wiki/Linspire"), which has recieved an enormous amount of flak for its inclusion of Wine as well as closed source products in the OS.

---

### Post by aaronb on 2009-03-10
I agree that wine should be part of the main install.

One barrier to Linux is investments that people have already made in Win32 software. Many software will never be available on Linux as long as a separate package is required for each distribution.

---

### Post by LouisZepher on 2009-03-10
> **cogadh said:**
> Wine is not needed because the vast majority of Linux users will simply use the native alternatives to Windows apps that are already part of Ubuntu. The only real exception to this is gaming and in those circumstances, installing Wine is a simple process. Why give everyone what only a few actually want?
Agreed.  Wine should be a last resort for when there just isn't an equivalent in the Linux world.  I've switched from MS software long before I switched over to Ubuntu permanently.  I switched to OpenOffice, Firefox, Thunderbird, a series of third-party shell/desktop environments, etc.  I  only have Wine to run Starcraft, PaintShop (I've always prefered this over Photoshop, the GUI is more conducive to my own artistic style), and Bryce5.

---

### Post by Paul41 on 2009-03-10
I tried WINE when I first started using Linux but quickly gave up on it. Programs either didn't work at all or didn't work well.

---

### Post by cmay on 2009-03-10
how many linux distributions do you know as popular and has a great community such as ubuntu that uses wine as a default app along with other steps to make it easy to adjust to linux for newcomers such as as example linspire xandros earOS and so on. 

if people have already got their software for win32 they can use either windows or reactOS., the reactOS project is aimed at running windows software as there comes a time and a day where the software you have is no longer supported on the windows platform anyway. 

is this linux problem that people buy software for windows. what about mac then. 
if the argument that it should include wine as default becouse the gamers has problems installing wine and it should be easy for them the list could might as well go on and on. 
i want gcc and geany and the build essential package to be included per default. 
i use this to program.  some programmers wnat java then. 

those of us that uses xine instead of totem want that to be included and the only game i play anyway is supertux so i want that to be fitted on to the cd instead of gnome-games which is boring and i remove everytime i install ubuntu. 

then i never use the restricted drivers for video cards as i simply do not trust them as they are closed source and can not be improved upon by the ubuntu developers so i want the program that makes it easy to isntall those drivers removed so it does not take space on the cd to keep the download as small as possible.

 then i always install openbox as a second windows enviroment and therefor to make it as simple as possible why not just include it as a option in the installer to use openbox as default windows manager. 

the list could go on as we try to make everyone happy. but the way ubuntu is as of right now it can atract users theat use it for their home use and also for buisness people. 

no company would ever choose a distro like linspire or maybe ubuntu the ultimate 
edition which i seem to remember has wine installed per default. its a dvd i used only once for some reason. its simply not ubuntu the way ubuntu should be. i think i gave the dvd away as soon i seen it and one reason i would have done that is if the dvd includes wine. 

it is not hard to install the programs one needs by one self.

---

### Post by kidux on 2009-03-10
> **cmay said:**
> it is not hard to install the programs one needs by one self.
And that is part of the learning process for Linux, specifically Ubuntu. Finding out where to get new software and how to install it. WINE just isn't needed by enough people to warrent inclusion by default.

---

### Post by cmay on 2009-03-10
there you go. 
[http://news.softpedia.com/news/Ubuntu-for-Gamers-49145.shtml](http://news.softpedia.com/news/Ubuntu-for-Gamers-49145.shtml)

it has many games and it has wine installed per default. 
why is it not so popular as the regular ubuntu . 
i do not know. i only used it once and i gave it away. wine was a nightmare to uninstall.

---

### Post by Mark Phelps on 2009-03-10
Throw in my two-cents, too ...

Absolutely NOT (part of the main install).

Why do I vote NO?  Because I feel the main install should consist of those things that most people need in order to do the most common activities, which today, tend to be web-browsing, email, listening to music, watching videos, and using word processing and spreadsheet apps.

Yeah, some folks do gaming (but not me), and some of them insist on MS windows games.  But, gaming presents lots of extra demands on compatibility that web-browsing doesn't. It's not just installing WINE -- it's all the hacking that has to be done afterward to get a game to work.  And that's before we have to deal with SLI-2, SLI-3, or SLI+Physx machines -- and multiple monitors.

Also, WINE is not the only run-MS-Windows-in-Linux solution; there are others as well.  Rather than force WINE on all of us, I think the better solution (the one at present) it to let folks browse the Ubuntu forums and decide for themselves what to install and use.

---

### Post by jimmyhacker on 2009-03-10
> **Brinstar said:**
> 
what is linux all about? making things harder for the users, so they eventually give up and go back to windows? or making things easier so they stick around and start to realise linux is a better alternative? if you don't let them adjust slowly, by giving them things like wine to let them come over gradually, you are just going to end up alienating people.

If you can think like this,you can switch back to your old,screwed,virused,fulled of temporary files operating system,then break the linux community.for a novice nothing is hard.
are you too lazy to make sudo apt-get install wine?i think you prefer to search a game in a couple of hours around web sites,then getting a worm like "Netsky.A" wich is compiled by a cygwin user?

buying and downloading Quake 3 is harder and expensive than typing "sudo apt-get install openarena".....


-"Measure,adjust and thing again"
 
                             Goethe

---

### Post by perce on 2009-03-10
I like the idea of wine, but I've never been able to make any program work properly on it.

---

### Post by Brinstar on 2009-03-10
> **jimmyhacker said:**
> If you can think like this,you can switch back to your old,screwed,virused,fulled of temporary files operating system,then break the linux community.for a novice nothing is hard.
are you too lazy to make sudo apt-get install wine?i think you prefer to search a game in a couple of hours around web sites,then getting a worm like "Netsky.A" wich is compiled by a cygwin user?

buying and downloading Quake 3 is harder and expensive than typing "sudo apt-get install openarena".....


-"Measure,adjust and thing again"
 
                             Goethe

=;

---

### Post by Bios Element on 2009-03-10
How about a guide in the help system? Just the command line list to hold someones hand who actually needs to run a windows program? And include a link to appdb as well.

---

### Post by cogadh on 2009-03-10
> **Bios Element said:**
> How about a guide in the help system? Just the command line list to hold someones hand who actually needs to run a windows program? And include a link to appdb as well.

You mean like this:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by roberto.eiberle on 2009-03-12
I( don't think that a programme that sometimes works, is updated every 2 weeks should be in the main install. It's fun trying out and ocasionally a succes but tweaking things overriding dlls etc. is more complicated for the newcommer than the whole of linux. If one starts from there because of ones windows background the only possible conclusion would be -that's not for me -.New users must start using linux and once they know their way around they know where to find it and get the latest version and possibly they have read the applicationDB and won't be desillusioned.

---

