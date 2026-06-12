---
title: "Repositories Feel like DRM."
date: 2016-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by mintmag on 2016-11-17
Hey guys. Ever since I started using Linux, the one thing that always bothered me was the fact that you had to use repositories to install things. From updating software to installing software, I've always preferred to install programs from a single file like a .exe. 
I like what GOG does with their Linux games. They use a mako installer that works exactly like a exe.

Installing from a repository feels like DRM. Someone once asked me why I don't like about repositories; using command line? The management of dependencies? The inflexibility of the installation?  

 
 
 Do which I said all of the above. If Linux is all about control then why do these repositories feel like DRM? (Not saying they are, DRM only that it feels like it)

---

### Post by QIII on 2016-11-17
How does it "feel like DRM"?

---

### Post by oldos2er on 2016-11-17
> I've always preferred to install programs from a single file like a .exe.

*deb files are single files.

I don't see any real DRM analogy. You're not restricted, you're free to install from source or sources you trust outside repositories (the risk is, of course, that you may break your system in doing so). The programs and files in the official repos are vetted to work with their related Ubuntu version; that in no way means you're restricted to them alone.

---

### Post by mintmag on 2016-11-17
Because it works like Steam. You use an app store so just downloading your programs and taking them with you while possible is quite the chore.

---

### Post by mintmag on 2016-11-17
> **oldos2er said:**
> *deb files are single files.

I don't see any real DRM analogy. You're not restricted, you're free to install from source or sources you trust outside repositories (the risk is, of course, that you may break your system in doing so). The programs and files in the official repos are vetted to work with their related Ubuntu version; that in no way means you're restricted to them alone.

How else would you install them though. I've only ever been able to install from the server. Is there a website you can go to to get the same apps?

---

### Post by MartyBuntu on 2016-11-17
What's the comparison with DRM.?
The use of repositories is one of the Linux world's greatest features. How do you see it as a detriment? It's easy, organised and secure.

---

### Post by oldos2er on 2016-11-17
> Is there a website you can go to to get the same apps packages.ubuntu.com

Edit: And just to be clear, repositories are web sites. Your /etc/apt/sources.list (hence the name) is a list of them, along with any *list files in /etc/apt/sources.list.d/

---

### Post by &amp;KyT$0P# on 2016-11-17
> **mintmag said:**
> You use an app store 
Er, no I don't.  I just uninstall those type programs and use Synaptic instead.

>  just downloading your programs and taking them with you while possible is quite the chore.
Can you please provide more details of the process you have in mind?

---

### Post by mastablasta on 2016-11-18
there are:
 .deb files
.tar.gz files (source files)
.tar.gz files with binaries included (e.g. supertuxcart)
snaps

and of course 
repositories - official ones - security, parther, 3rd party..., and personal package archives (PPA).

.exe ? yes that is good. until a few years ago .exe didn't even need some admin rights an dit can just be run no matter what is inside. in fact there was a feature called autoplay - you inserted a CD and it ran whatever was on it. wheather it was a game's "setup.exe" or a malware file.

in Windows i prefer to use zipped binary files (e.g. portable progs) on Windows. they do not clutter the registry + they are trully portable. you can just zip the program back abc take it with you as ti is settings and all included.

---

### Post by ian-weisser on 2016-11-18
> **mintmag said:**
> They use a mako installer that works exactly like a exe.
Installing from a repository feels like DRM.

You're not the first Windows-power-user to misunderstand the purpose of distros and repositories; you won't be the last.

A Linux OS consists of hundreds of independent applications from unrelated upstream developers. Each developer is constantly improving their tiny piece of the puzzle. Back in the 1990s, each improvement had to be distributed by email or newsgroup, compiled locally, and installed/tested by hand. Less fun than it sounds.

Distros and repositories and software packages came first, over 15 years ago. They supplanted those tedious older methods, and made possible the strong collaboration, QA/QC, reliable upgrades, rapid security patches, and easy installation that you take for granted. 

App stores emerged later, about 10 years ago. An app store is owned by a single Company, and is tied to their business model (not their improvement plans). Yeah, they sometimes use DRM. They copied the concept from us, and turned it into their walled garden.

See the difference?

Ubuntu is not a company. You are not Ubuntu's customer. Ubuntu gets _no_revenue from your use of it. You are a *participant *in the Ubuntu Project.
Steam is. You are. Steam does.

---

### Post by mintmag on 2016-11-19
> **halogen2 said:**
> Er, no I don't.  I just uninstall those type programs and use Synaptic instead.


Can you please provide more details of the process you have in mind?

Weather you use synaptic app center or command line you're still installing from server.

Ideally how I personally would like to install programs would be just like in Windows. You download a single file that you launch to install the program. You are also promoted to where to want it to go.

---

### Post by QIII on 2016-11-19
You download that file from a server, too.  Anything you download comes from a server.  Do you understand what a server is?

You do not know what the .exe does.

You do not know if the .exe has been tested.

You do not know if the .exe will harm your machine by delivering a malicious payload.

The "where you want it to go" choice is part of the mess Windows makes.  Nevertheless, you can, if you chose to, put many Linux applications where you want them to go.  But you often get to go yourself through the messy process of redirecting things so they will work.  You get a taste of the mess Windows makes.

Rather than being undesirable, what you are talking about now is one of the positive benefits of a standard repository.  Downloading and installing software promiscuously from the web is one of the greatest security failings of the Windows world.  Your argument here is entirely backwards.

---

### Post by ian-weisser on 2016-11-19
> **mintmag said:**
> Ideally how I personally would like to install programs would be just like in Windows. You download a single file that you launch to install the program. You are also promoted to where to want it to go.

Then you seem likely to find Ubuntu frustrating and inconvenient.

Relying upon Windows-power-user skills will lead you down many wrong paths in Linux, and make your learning curve steeper than it needs to be.
Ubuntu is not a drop-in Windows replacement, and is not trying to be one. It's *different*.
You must accept those differences, learn Ubuntu with patience, and be open to learning many all-new basic skills.

---

### Post by mintmag on 2016-11-19
> **mastablasta said:**
> there are:
in Windows i prefer to use zipped binary files (e.g. portable progs) on Windows. they do not clutter the registry + they are trully portable. you can just zip the program back abc take it with you as ti is settings and all included.

I still prefer exe over portable. Portable programs still affect the registry and in my experience tend to be less functional then programs that install. This was abutment with Libireoffice where the installed versions defiantly seems to integrate with the OS more the the portable version. But choice is always a plus. My problem with repo's is that they are often the only choice for most things.

> **MartyBuntu said:**
> What's the comparison with DRM.?
The use of repositories is one of the Linux world's greatest features.  How do you see it as a detriment? It's easy, organised and  secure.

I think it's also one of the main reasons Windows users avoid Linux. Well for me at least. The comparison to DRM comes from needing a direct connection to it to use it. It feels like Steam in many ways. You can download debs from it install directly from them. However, there's very little control you have in doing this and it's a pain. It's not DRM but it _feels_ like DRM.

> **ian-weisser said:**
> You're not the first Windows-power-user to  misunderstand the purpose of distros and repositories; you won't be the  last.

[SNIP]

See the difference?


You're not the first Linux user to assume that I don't understand  how repos work. It's not that I don't understand them it's that I do not  _like_ them. I use the app store compassion simply because I don't  know how else to describe it. Linux might not have a walled garden but  it certainly feels like one. What I don't understand is with hundreds  and hundreds of distributions not one that I can find uses the Windows  traditional method of installing programs. If Linux is all choice and  control; where's the choice and control?

> **QIII said:**
> You download that file from a server, too.   Anything you download comes from a server.  Do you understand what a  server is?

You do not know what the .exe does.

You do not know if the .exe has been tested.

You do not know if the .exe will harm your machine by delivering a malicious payload.

The "where you want it to go" choice is part of the mess Windows makes.   Nevertheless, you can, if you chose to, put many Linux applications  where you want them to go.  But you often get to go yourself through the  messy process of redirecting things so they will work.  You get a taste  of the mess Windows makes.

Rather than being undesirable, what you are talking about now is one of  the positive benefits of a standard repository.  Downloading and  installing software promiscuously from the web is one of the greatest  security failings of the Windows world.  Your argument here is entirely  backwards.

I think you misunderstand what I was trying to say so I'll break it down. 
Everything  you download comes from a server yes, but you need direct access and a  package manager to use a repository. meaning you can't just go to  another computer open a browser and use it like an exe.

exes are easier to use in just about every way.
easier to manage
easier to install
easier to archive 

It's  been a very long time since I got any malware. (Almost ten years I  think) so I think exes are very safe. In fact I think anyone who argues  that Linux is safer then Windows is ignoring just how few people use  Linux. It's like saying this 
"I don't need to lock my doors because my house never gets broken into"
"but your house is in the middle of the desert, and you have no electricity or plumbing"
"So?"

As  for the "where you want it to go" being a bad thing. I'm not sure how  to even respond to that. What about choice and freedom? I looked into  changing it and I can't really find a way of doing it. Being able to  have your own program directory is great especially if you start to run  out of space. It's utter craziness not to want this.

---

### Post by &amp;KyT$0P# on 2016-11-19
> **mintmag said:**
> Ideally how I personally would like to install programs would be just like in Windows. You download a single file that you launch to install the program. You are also promoted to where to want it to go.
There is no "just like in Windows" way to install programs in Linux.  The closest thing would be software tarballs and some .run type installers.

Some softwares have these on the official website.  For those that don't, you might be able to get source code and build one yourself.

> **mintmag said:**
> The comparison to DRM comes from needing a direct connection to it to use it. 
What do you mean by "direct connection"?

> Linux might not have a walled garden but it certainly feels like one. What I don't understand is with hundreds and hundreds of distributions not one that I can find uses the Windows traditional method of installing programs. If Linux is all choice and control; where's the choice and control? 
Well, you do have the choice and control to uninstall Linux, don't you?

I've heard that Windows is a good OS for those who like the Windows way.

---

### Post by pauljw on 2016-11-19
> **mintmag said:**
> I still prefer exe over portable. Portable programs still affect the registry and in my experience tend to be less functional then programs that install. This was abutment with Libireoffice where the installed versions defiantly seems to integrate with the OS more the the portable version. But choice is always a plus. My problem with repo's is that they are often the only choice for most things.



I think it's also one of the main reasons Windows users avoid Linux. Well for me at least. The comparison to DRM comes from needing a direct connection to it to use it. It feels like Steam in many ways. You can download debs from it install directly from them. However, there's very little control you have in doing this and it's a pain. It's not DRM but it _feels_ like DRM.



You're not the first Linux user to assume that I don't understand  how repos work. It's not that I don't understand them it's that I do not  _like_ them. I use the app store compassion simply because I don't  know how else to describe it. Linux might not have a walled garden but  it certainly feels like one. What I don't understand is with hundreds  and hundreds of distributions not one that I can find uses the Windows  traditional method of installing programs. If Linux is all choice and  control; where's the choice and control?

As others have already pointed out, linux is not windows and we prefer it that way.  You perceive the repositories as a negative, yet I see them as a huge positive.  I know that I can select from a library of over 50K packages that have been thoroughly tested to work in conjunction with the distro I have chosen.  They are known to be free of malware and safe.  This is not true in the windows world.  Also, when I do a system update, ALL of the software on my system is updated to the latest known safe version, which is not the same as the newest release of some of the software, but for the sake of having a reliable system, it's best.

Of course, if you don't care about system reliability, there are distros that cater to those who wish to be on the bleeding edge of software and the level of expertise required to maintain these systems is considerably higher.

Then there is also the source code for any and all packages required by the GPL.  You can locate the source for a program and download it and compile it for your particular distro and machine.  This can be a very good method as it custom builds the software according to the specifics for your individual system and desired specifications.  However, whenever the software is updated, it will not be an automated process for you to get said update.  Over time, keeping track of your individually installed software can become quite tedious.  

But, that is a bit of that control and choice you seem to looking for.

---

### Post by mintmag on 2016-11-19
> **halogen2 said:**
> There is no "just like in Windows" way to install programs in Linux.  The closest thing would be software tarballs and some .run type installers.

That is not true at all. As I mentioned GOG Linux games use a Mako installer that works exactly like a Windows installer. I love it and want to see more programs use it.



> **halogen2 said:**
> 
What do you mean by "direct connection"?

If the computer with Ubuntu on it can't access the web it's almost a brick. Installing, updating the system and drivers. While "posible" in the strictest meaning of the word, it is so difficult that you might as well not even bother.

> **halogen2 said:**
> 
Well, you do have the choice and control to uninstall Linux, don't you?

I've heard that Windows is a good OS for those who like the Windows way.
Windows is good because it just works. That being said there really should be alternatives. Linux distributions have potential to a great alternative. I think implanting a method of installing programs closer to how exes work would go a long way in doing that. You can still have repos . I don't see why you can't have both. This is mostly a suggestion perhaps I should have titled this thread differently. But I would really like to see a distro implant Mako installation as a main method.

> **pauljw said:**
> As others have already pointed out, linux is not  windows and we prefer it that way.  You perceive the repositories as a  negative, yet I see them as a huge positive.
[SNIP] 

I certainly hope you don't mean me when you say "we" Judging by the  climbing popularity of Linux Mint I'd argue that a lot of people would  like a windows like distor. I just don't think Mint is quite there yet.  Also I perceive the lack of a Mako (exe style) installers forcing me to  use repos to be a negative. What is wrong with having another method to  install software. A method such as this could do a lot to bring more  people over to Linux. Making Linux easier ro use will make more people  want to use it.

---

### Post by &amp;KyT$0P# on 2016-11-19
Searching for "Mako installer" turns up only this thread and a bunch of unrelated stuff.  Can you please post the link to the official site of this installer framework?

---

### Post by cariboo on 2016-11-19
@mintmag, I take it you haven't looked at Snaps yet, they seem to be a bit more like you are looking for, have a look here:

[http://snapcraft.io/](http://snapcraft.io/)

---

### Post by mintmag on 2016-11-20
> **halogen2 said:**
> Searching for "Mako installer" turns up only this thread and a bunch of unrelated stuff.  Can you please post the link to the official site of this installer framework?

My mistake they use makeself and mojosetup [https://icculus.org/mojosetup/](https://icculus.org/mojosetup/) to create the installers.


> **cariboo said:**
> @mintmag, I take it you haven't looked at Snaps  yet, they seem to be a bit more like you are looking for, have a look  here:

[http://snapcraft.io/](http://snapcraft.io/)

I have looked into that but I can't figure out how to use it.

---

### Post by ian-weisser on 2016-11-20
You can use Mojosetup to install Ubuntu software.
Be the first. Somebody has to be the first, figure out how to make it work, and write the tutorials.
Do it.

---

### Post by pauljw on 2016-11-20
> **mintmag said:**
> I certainly hope you don't mean me when you say "we" Judging by the  climbing popularity of Linux Mint I'd argue that a lot of people would  like a windows like distor. I just don't think Mint is quite there yet.  Also I perceive the lack of a Mako (exe style) installers forcing me to  use repos to be a negative. What is wrong with having another method to  install software. A method such as this could do a lot to bring more  people over to Linux. Making Linux easier ro use will make more people  want to use it.

No, I most assuredly did not mean "you", it was my meager attempt at being politically correct and all inclusive.  I have used Mint and don't find it to be all that great and it's based on Ubuntu and uses Ubuntu repos.  It's desktop environment, Mate I think, simply has more of a Windows look and feel, but you can install Mate on most any distro(try that with Windows.)  As for forcing you to use repos for software, I and others have given multiple methods of installing software, none of which are as easy to use as the repositories that you seem to have an aversion to.  I have no idea how long you've been using linux, but if all you're concerned about is playing games with it, Windows is a much better platform.  

Also, speaking just for myself, I don't care if anyone ever "brings" anyone over to linux.  I happen to prefer linux over any other OS just the way it is.  It's different and new users need to let go of their past and spend time learning to use it rather than insist on changing it to be like something it isn't. 

I'm trying to learn BSD so in the event that ex-Windows users manage to corrupt linux to the point where it's just like windows, I can switch to Unix and continue to have a windows free life.

I'm done here, have fun with whatever os you choose.  That is the point, isn't it?  Fun...

---

### Post by vasa1 on 2016-11-20
> **pauljw said:**
> ...
I'm done here ...
Not to worry. Others will step in ;)

---

### Post by mintmag on 2016-11-20
> **pauljw said:**
> No, I most assuredly did not mean "you", it was my meager attempt at being politically correct and all inclusive.  I have used Mint and don't find it to be all that great and it's based on Ubuntu and uses Ubuntu repos.  It's desktop environment, Mate I think, simply has more of a Windows look and feel, but you can install Mate on most any distro(try that with Windows.)  As for forcing you to use repos for software, I and others have given multiple methods of installing software, none of which are as easy to use as the repositories that you seem to have an aversion to.  I have no idea how long you've been using linux, but if all you're concerned about is playing games with it, Windows is a much better platform.  

Also, speaking just for myself, I don't care if anyone ever "brings" anyone over to linux.  I happen to prefer linux over any other OS just the way it is.  It's different and new users need to let go of their past and spend time learning to use it rather than insist on changing it to be like something it isn't. 

I'm trying to learn BSD so in the event that ex-Windows users manage to corrupt linux to the point where it's just like windows, I can switch to Unix and continue to have a windows free life.

I'm done here, have fun with whatever os you choose.  That is the point, isn't it?  Fun...

Would it upset you if I said whatever makes Linux more like Windows makes it better. If Distrowatch, Mint, Manjaro and Zorin are anything to go by, I'd say that the Linux community inadvertently agrees. Linux is aping Windows more and more. 

On to your other points though. Yes there are other methods for installing software and they aren't as easy because they're not as developed. Developing them more I think would only improve things. Since I think repositories are fine for casual users but for those who want' more control they are a pain.

You said you like Linux the way it is and then also said people just need to accept that and not change it. But mate, Linux is always changing. How it works now is completely different to how it worked years ago and who knows how it will work in another ten years (probably, more like Windows). Windows however is a lot more consistent. Also speaking of comparing Mint to Ubuntu I don't think you give Mint enough credit. One of the things it has over Ubtuntu is that it's got 32Bit architecture built into it. I tried installing 32Bit into Ubuntu but couldn't get it to work. It baffles my mind that Canonical did this. It's like how Apple removed the headphone jack. Not having 32Bit arch in a 64Bit system is going to cause problems. Also I haven't had the best luck installing desktop environment into Mint. With Windows you absolutely can change the desktop. Not as much as Linux and I wouldn't recommend it but it can be done.

Lastly 
> **pauljw said:**
> 
 I'm trying to learn BSD so in the event that ex-Windows users manage to  corrupt linux to the point where it's just like windows, I can switch to  Unix and continue to have a windows free life.


Umm that sounds a little tinfoil. Windows-like features and distros maybe. I'm not sure what's worse The idea that Windows users can "corrupt" Linux (what is it sacred or something?) or the idea that you'll keep moving to something different. I mean would you resert to using a stone age DOS-like CLI PC that can only send basic emails just to avoid the "Windows feel?"

---

### Post by JayKay3OOO on 2016-11-20
What I thought the new windows store was going to be a clone of the linux / mac implementation.

Installing stuff from third party, potentially hijacked websites is a very much outmoded and outdated way of thinking.

Ah well. I don't agree since downloading .deb files which are self contained versions of the same software that you would download from the evil, DRM file hosted streams is the same as downloading and installing a .exe file.

I now have my nas with a collection of most of the software I use on windows which I install from the nas... so... DRM?

You can do this same thing on a mac, except on a mac it's even easier to install the software from a downloaded file.

I can see if you feel you are controlled by the software sources, but you're not because you can go to any website that has packaged .deb (linux exe) files for your chosen software that is not in the sources list of software center.

You could easily ignore the software center if you so wished. Updates happen similar to windows so you're stuck with that DRM.

.exe is just a container. It also adds stuff to the registry in windows because some applications you can unzip and run from your windows computer. Some download extra software and some add registry items never telling you what registry items and why is doing it or what damage it might do.

Since I use windows, mac and Linux I'm not trying to fight the linux corner, but here this suggestion of the OP makes the question misunderstood.

I like it. More radical ideas!

---

### Post by ian-weisser on 2016-11-20
> **mintmag said:**
> What I don't understand is with hundreds  and hundreds of distributions not one that I can find uses the Windows  traditional method of installing programs. If Linux is all choice and  control; where's the choice and control?

Yes, there's a set of very good reasons for that.
 A bit of reflecting on the history and structure of the Linux ecosystem, and comparing it to the Windows ecosystem, will tell you why.
Or search-engine it. The history of Linux distros and package managers, and the reasons for their design decisions, are well-documented.

You're not the first person to suggest a Windows-type installer. It's been done. Several times. Browse git projects and you'll find a few.
Windows-type installers get suggested a couple times each year in these forums.
Several projects to develop windows-type installers have been started. Some released working versions.
I remember a short-lived distro that used Windows-type installers back around 2008.
Snaps are probably the newest, and certainly the closest to achieving general acceptance.

---

### Post by mintmag on 2016-11-20
> **cariboo said:**
> @mintmag, I take it you haven't looked at Snaps yet, they seem to be a bit more like you are looking for, have a look here:

[http://snapcraft.io/](http://snapcraft.io/)


Okay I managed to install a few packages. It's very interesting. Do you know how to install from a local .snap file?

> **ian-weisser said:**
> Yes, there's a set of very good reasons for that.
 A bit of reflecting on the history and structure of the Linux  ecosystem, and comparing it to the Windows ecosystem, will tell you why.
Or search-engine it. The history of Linux distros and package managers,  and the reasons for their design decisions, are well-documented.

You're not the first person to suggest a Windows-type installer. It's  been done. Several times. Browse git projects and you'll find a few.
Windows-type installers get suggested a couple times each year in these forums.
Several projects to develop windows-type installers have been started. Some released working versions.
I remember a short-lived distro that used Windows-type installers back around 2008.
Snaps are probably the newest, and certainly the closest to achieving general acceptance.

I  understand that a lot of it is to accommodate the fact that there are  so many distro, However I don't think this is a good thing. It's not too  much choice I see it as more quantity over quality. Anyway I've been  giving snaps a try. So far they look rather promising. Do you know how  to install them from local drives ie .snap files.

---

### Post by cariboo on 2016-11-20
> **mintmag said:**
> Okay I managed to install a few packages. It's very interesting. Do you know how to install from a local .snap file?



I  understand that a lot of it is to accommodate the fact that there are  so many distro, However I don't think this is a good thing. It's not too  much choice I see it as more quantity over quality. Anyway I've been  giving snaps a try. So far they look rather promising. Do you know how  to install them from local drives ie .snap files.

I haven't bothered to try, as I have an always on internet connection. It can be done, as developers need to try out the snap before publishing. I'm not on my main system where all my email is kept, but I will post a link to the mailing list where you can ask all the questions you want when I'm back from work tomorrow.

---

### Post by mintmag on 2016-11-21
> **cariboo said:**
> I haven't bothered to try, as I have an always on internet connection. It can be done, as developers need to try out the snap before publishing. I'm not on my main system where all my email is kept, but I will post a link to the mailing list where you can ask all the questions you want when I'm back from work tomorrow.


And that's exactly why it feels like DRM. Nailed it on the head. You require internet to install. Without internet Linux is a brick, unable to do much of anything.

---

### Post by mastablasta on 2016-11-21
> **mintmag said:**
> And that's exactly why it feels like DRM. Nailed it on the head. You require internet to install. Without internet Linux is a brick, unable to do much of anything.

except that is not true. you can download all packages or even create your own repositories. debian has a couple of DVDs to download. you can go and download them all if you want.

there are offline installers. you Will get them on internet. but they do enable you to download what you want and install it at your convenience (offline). not sure if keryx is still owrking or not: [SIZE=2]https://launchpad.net/keryx/+download
[/SIZE]

you can also install slackware and install everyhtign from source: [SIZE=2]http://www.slackbook.org/html/package-management.html
[/SIZE]

> I  understand that a lot of it is to accommodate the fact that there are  so many distro

as mentioned before do some reasearch.

as for DRM like - please, do some reading on DRM as well. just because you download something from internet and update it from internet (i mean, how else do you want to update? using floppy drives?!) it doesn't mean it is DRM or that it even feels like it. you are also free to download a red hat package and install it on ubuntu.

you can lock the package - no one forces you to upgrade or update. and i am not sure what is so hard about selecting the package and clicking on the lock icon and mark it as locked.

the only issue i see is backwards compatibility. with iwndows you get that with Ubutnu - not always. say you want to install a game from 2003 - it Will likely work just fine from in windows but not in linux. it would be a bit more complicated to do it in linux. on th eplu sside linux programs as a result of shared libraries take up much less space and it was therefore easier to stick a usable OS on the phone that it would be using windows XP or Vista at the time.

---

### Post by mintmag on 2016-11-21
> **mastablasta said:**
> except that is not true. you can download all packages or even create your own repositories. debian has a couple of DVDs to download. you can go and download them all if you want.

there are offline installers. you Will get them on internet. but they do enable you to download what you want and install it at your convenience (offline). not sure if keryx is still owrking or not: [SIZE=2]https://launchpad.net/keryx/+download
[/SIZE]

you can also install slackware and install everyhtign from source: [SIZE=2]http://www.slackbook.org/html/package-management.html

Question, have tried using these methods yourself? Reading on how to do something, and doing it are two very different things. I'm not being mischievous when I say this either. There are a lot of tutorials and documentation for Linux that are total BS. Most of problems I have solved come from learning how something works and then figuring out a way to make it work for me. While I still read I take it with a grain of salt.
[/SIZE]


> **mastablasta said:**
> 
as mentioned before do some reasearch.

as for DRM like - please, do some reading on DRM as well. just because you download something from internet and update it from internet (i mean, how else do you want to update? using floppy drives?!) it doesn't mean it is DRM or that it even feels like it. you are also free to download a red hat package and install it on ubuntu.

To say that something **is** would be objective. To say something** feels like** is to be subjective. It is in my opinion that it feels like DRM. I have researched and I have read lots on DRM and stand by my statement; which is based on experience. Also I already have a very effective way of using apt offline. I will tell you if you like.

---

### Post by mastablasta on 2016-11-21
> **mintmag said:**
> Question, have tried using these methods yourself? Reading on how to do something, and doing it are two very different things. I'm not being mischievous when I say this either. There are a lot of tutorials and documentation for Linux that are total BS. Most of problems I have solved come from learning how something works and then figuring out a way to make it work for me. While I still read I take it with a grain of salt.
.

i used .deb, source (it is actually easy to do and oyu can copy & paste from their readme file), pre-zipped binaries. keryx i haven't tried and i am not sure it still works. i didn't feel the need.

i also locked driver and an app to a version that worked well.

i believe synaptics might also be able to download what you need for offline install. 

i haven't tried snaps, but i think this is closest and a lot better than .exe file. the problem is as mentioned .exe is not contained and the updates are done thorugh app. which sometimes it is good, but dual boot the OS or don't use the win PC for a while and then try to safely surf the web with it - it will go like this :
1. you add OS updates,likely reboot the PC at least once,
2. update browser.
3. if site uses flash open flash & update (maybe possible via browser plugin?) 
4. run java update
5. update antivirus (if you use 3rd party)
6. update firewall (if you use 3rd party)

you should now be ready to surf safely.

in Win 10 pro it is done more like linux. all updates are in windows store.

anyway if you do the same with linux you boot, run the software update (maybe reboot or use the ubuntu patch on the fly or whatever it is called). you are then ready to work and browse safely.

like i said try another dirtro whcih has a different model. see what happens. maybe you wil llike it more. 

there is another experimental one that saves each app in it's won folder enabling you kind of .exe experience. 

even in windows you sometimes can not have 2 version of same app installed. whcih is why i actually like portable apps a lot more than .exe installers. everything you run stays in apps folder. which is why i am kind of excited about snaps on desktop.

---

### Post by ian-weisser on 2016-11-21
> **mintmag said:**
> \Do you know how  to install them from local drives ie .snap files.
sudo snap install /path/to/file.snap [--dangerous]
See man snap

---

### Post by QIII on 2016-11-21
> **mintmag said:**
> And that's exactly why it feels like DRM. Nailed it on the head. You require internet to install. Without internet Linux is a brick, unable to do much of anything.

Perhaps at this point you could explain your subjective understanding of DRM vis-a-vis internet connections.  In fact, it might be enlightening for you to explain your subjective observation about this seeming like DRM in the first place.  You have done a good job at avoiding pointed questions about that.

---

### Post by wildmanne39 on 2016-11-21
Which part of:
> Digital rights management (DRM) is a systematic approach to copyright protection for digital media. The purpose of DRM is to prevent unauthorized redistribution of digital media and restrict the ways consumers can copy content they've purchased.
feels like DRM to you?

Is it the way the software in the repositories can not be redistributed? oh wait the software in the main and universe is open-source and can be.
> Main

The main component contains applications that are free software, can be freely redistributed and are fully supported by the Ubuntu team.

Universe

The universe component is a snapshot of the free, open-source, and Linux world. It houses almost every piece of open-source software, all built from a range of public sources.

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Is it the purchased part? I personally have never purchased software for ubuntu.

You will need to be specific for us to understand the connection between the repository software and DRM.
Thanks

---

### Post by Geoffrey_Arndt on 2016-11-21
Interesting (albeit "troll-like" thread).

About three quarters of what MintMag continues to write in his replies are just a poor understanding of "CompSci 101" basics _& misconceptions/assumptions_.   

For example, the methodology of Linux software management via networked repositories means those servers provide official (safe) packages that are downloaded to "Local Machine" (your PC) and then uncompressed and installed by Local Machine software (dpkg & other core packages).   There is no requirement in most cases for "Server Side Processing".   The repos system basically manages files . . . the user actually installs software locally, but in an efficient way (only required packages downloaded, and then used).   Among other things, this makes Ubuntu updates MUCH faster than Windows updates on average.   

I've installed perhaps a hundred or more "stand-alone" deb files via command line or via "gdebi" . . . these exe's (inaccurate term by the way) can be installed just fine without a networked connection at all. 

In addition to the online repos, there are multiple PPA's (personal package archives)  - - this method is similar to traversing the web to installing typical Win software . . . EXCEPT . . . most PPA's provide better source authentication.

Further, as already mentioned in this thread, there are "fully encapsulated Snappy packages" and "AppImage" exe's, and "Flatpaks" that are all stand-alone binaries, easy to install and "mostly functional (although these tools are still in the later stages of development).

Yet more . . . . there are thousands of Source files hosted (merely hosted) on Git Hub and Sourceforge (and other sites) that can be downloaded to local machine and "built" (compiled).   Again, thank you Satya . . . for directing MS to build a "native" capability in Win10 to run BASH and thereby emulate (actually copy) these Linux software capabilities to the Windows world.   Makes DevOps folks a lot happier.

So, all these technologies, over time, do get simplified and rolled down and into the versions of Ubuntu & Windows we use today.

---

### Post by kpatz on 2016-11-21
I think the OP is misunderstanding "online repository" for DRM.  Sure, you need an internet connection to download from this repository, just like you need an internet connection to download Windows executables from an app store or from any website.  How else do you bring software into your PC in this day and age?  CD/DVD media mainly, and that's just for software you buy in a store.  Open source software for Linux isn't distributed this way, it's free, and available online.

When using a DRM'd piece of software, you have to be connected to the internet even to run it in some cases, or at the very least to "activate" it after installation.  Ubuntu software doesn't require this at all.  Once the package is downloaded, you could disconnect from the internet and the package will still install and run.  The only way to eliminate the need for an internet connection entirely would be to download every package you'll ever need ahead of time and store it locally.  The repository is for convenience mainly.  Instead of having to search the web, download, unzip/extract, configure, build and install, you just enter one command and bingo, it all happens automatically.  Plus you know the package has been vetted and compatible with your distro, up to date, and free of malware--something you can't always be sure of when downloading software from some random website.

---

### Post by mintmag on 2016-11-21
> **ian-weisser said:**
> sudo snap install /path/to/file.snap [--dangerous]
See man snap

I tried that. It goes in but I can't seem to run it.

> **kpatz said:**
> I think the OP is misunderstanding "online  repository" for DRM.  Sure, you need an internet connection to download  from this repository, just like you need an internet connection to  download Windows executables from an app store or from any website.  How  else do you bring software into your PC in this day and age?  CD/DVD  media mainly, and that's just for software you buy in a store.  Open  source software for Linux isn't distributed this way, it's free, and  available online.

When using a DRM'd piece of software, you have to be connected to the  internet even to run it in some cases, or at the very least to  "activate" it after installation.  Ubuntu software doesn't require this  at all.  Once the package is downloaded, you could disconnect from the  internet and the package will still install and run.  The only way to  eliminate the need for an internet connection entirely would be to  download every package you'll ever need ahead of time and store it  locally.  The repository is for convenience mainly.  Instead of having  to search the web, download, unzip/extract, configure, build and  install, you just enter one command and bingo, it all happens  automatically.  Plus you know the package has been vetted and compatible  with your distro, up to date, and free of malware--something you can't  always be sure of when downloading software from some random  website.

This is absolutely true and I would never say  that Linux has DRM. But organizing downloaded packages for offline  redistribution is a chore. To someone unfamiliar with .deb files, how  they work, where they are stored and of course how to use them locally. A  repository does feel like an app store server with DRM. Fortunately if  you know what you're doing you can write scripts or create local repos  (if you've got the space for it) for offline management. I myself  downloaded every single .deb file from a repo and placed them into the  cache/archives directory, This allowed the software center to grab  everything from the cache instead of the server. Great fun. But I had to teach myself how to do that. I would still prefer the exe method. Then again perhaps not. I've been playing around with snap and I prefer apt from it.

> **Wild Man said:**
> Which part of:

feels like DRM to you?

Is it the way the software in the repositories can not be redistributed?  oh wait the software in the main and universe is open-source and can  be.

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Is it the purchased part? I personally have never purchased software for ubuntu.

You will need to be specific for us to understand the connection between the repository software and DRM.
Thanks

It's mostly dependency hell. With DRM free software you download a  single file from a website and as long as you have that file you can  install the program and get it running. No need for server pining or  activating. Linux programs don't have DRM so no pining or activating.  But you can't just go to a website and download a single file either.  Even if you know the exact dependent for a program to work those will  change depending on other programs and updates. Thus archiving files for  programs you want to install on a hard drive very difficult. This  leaves you dependent on both the repositories and the package managers.  It's this **_dependency_** that feels like DRM.

> **Geoffrey_Arndt said:**
> 
SNIP

I know how  repositories work. Just because I don't like them doesn't mean I know  how they work, nor does it mean I am trolling. I am however expressing  what I feel is the biggest achilles heel to the repo system. I'm trying  to emphasizes that a more traditional method of installing packages  would probably help. Then again maybe not. I've used snappy and didn't  like it as much. I can't get local packages to install for some reason.  With apt I can though it was a grueling process to figure out. Also exes are quite safe while the wrong dependency can break your system.

> **QIII said:**
> Perhaps at this point you could explain your  subjective understanding of DRM vis-a-vis internet connections.  In  fact, it might be enlightening for you to explain your subjective  observation about this seeming like DRM in the first place.  You have  done a good job at avoiding pointed questions about that.

I thought I did. What specific thing would you like to know?
> **mastablasta said:**
> SNIP.
I really don't care for the Windows app store. Also I never had much  luck getting source stuff to work. Amway funny story. If you never  connect a Windows machine to the internet it will run fast and reliable  for ages, even without updates. The Linux method of updating is  convenient but there are a could of caviouts to take into account. Most  closed source software is going to update through app anyway. There's  not much Linux can do about that if you're going to use closed source  software. Another thing is it makes archiving annoying. See I keep a  folder with all my favorite exes in it. When I reformat my machine I  simply used that folder to install apps and drivers. When they get  updated I simply replace the exes with the latest ones. With Linux...  this is not something you can do. There are advantages to using exes you  see.

---

### Post by QIII on 2016-11-21
Given the posted description of DRM, could you explain, without the wholesale distribution of red herrings or muddled and pointless generalities, how dependencies relate to feelings of DRM?

---

### Post by mintmag on 2016-11-21
> **QIII said:**
> Given the posted description of DRM, could you explain, without the wholesale distribution of red herrings or muddled and pointless generalities, how dependencies relate to feelings of DRM?

Not sure what you mean by red herrings but to cut it short. Repositories feel like DRM because you **depend** on them. No repo means no software. No website that you can go to and just save what you need for later use. The repo and package manager that connects to it decide what you can have. Repos are like having all your eggs in one basket; and if you can't get to that basket with your machine then no software for you. Pretend you have no internet and that you had to go the public library to download software and you'll see what I mean. I don't think I can make it anymore more clear then that.

---

### Post by wildmanne39 on 2016-11-21
Thread has run its course and is repeating so it is closed!

---

