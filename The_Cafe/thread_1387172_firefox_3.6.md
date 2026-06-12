---
title: "firefox 3.6"
date: 2010-01-21
forum: The Cafe
---

### Post by sudoer541 on 2010-01-21
where can I find a .deb package to install Firefox 3.6?

dont advice me to compile anything please, I just want a point and click solution.

---

### Post by Eisenwinter on 2010-01-21
> **sudoer541 said:**
> dont advice me to compile anything please, I just want a point and click solution.
Then don't use Linux.

---

### Post by snowpine on 2010-01-21
Wait patiently and trust the Canonical developers to provide you with an update once it's been tested with Ubuntu. :)

---

### Post by nmccrina on 2010-01-21
[http://ubuntuforums.org/showthread.php?t=1386995]("http://ubuntuforums.org/showthread.php?t=1386995")

---

### Post by Zoot7 on 2010-01-21
You *could* download the Linux tarball from the Mozilla site, extract it to /opt and then create a desktop shortcut pointing it there.

---

### Post by PurposeOfReason on 2010-01-21
The other thread on the front page wasn't good enough for you?

---

### Post by quazi on 2010-01-21
> **Eisenwinter said:**
> Then don't use Linux.

Well that's an absurd response, particularly on the forum of a Debian based distribution.  There's no reason that compiling and linux need to go hand-in-hand.  In fact, as another poster has pointed out, there's a thread containing a link to a PPA/deb file.

---

### Post by Ric_NYC on 2010-01-21
> **quazi said:**
> **Well that's an absurd response, particularly on the forum of a Debian based distribution.**  There's no reason that compiling and linux need to go hand-in-hand.  In fact, as another poster has pointed out, there's a thread containing a link to a PPA/deb file.

I agree.

---

### Post by whiskeylover on 2010-01-21
I'm not running Ubuntu right now (I'm at work), but on the windows version, I just clicked the menu "Help/Check for Updates". It found the 3.6 update and installed it for me. 

Maybe there is a similar menu option for the linux version? I'll go home and check later.

---

### Post by Techsnap on 2010-01-21
If you're running x86 just download it from the Mozilla site and extract it to /opt.

---

### Post by snowpine on 2010-01-21
> **whiskeylover said:**
> I'm not running Ubuntu right now (I'm at work), but on the windows version, I just clicked the menu "Help/Check for Updates". It found the 3.6 update and installed it for me. 

Maybe there is a similar menu option for the linux version? I'll go home and check later.

It is disabled in Ubuntu, to encourage users to use the package manager for updates.

---

### Post by whiskeylover on 2010-01-21
Oh

---

### Post by Eisenwinter on 2010-01-21
> **quazi said:**
> Well that's an absurd response, particularly on the forum of a Debian based distribution.  There's no reason that compiling and linux need to go hand-in-hand.  In fact, as another poster has pointed out, there's a thread containing a link to a PPA/deb file.
He doesn't have to compile anything, sure. But, he said he wanted a point-and-click solution.

I have not Used Ubuntu in over a year, and even when I did, I would always install software from the command line, so excuse me if I'm missing something.

---

### Post by Gallahhad on 2010-01-21
I'm using Firefox 3.6 here on Debian Lenny 5.0.3, it looks and feels like Firefox. I neither like it better nor less than I ever have. Works a treat for browsing the internet :popcorn:

---

### Post by Eisenwinter on 2010-01-21
> **Gallahhad said:**
> I'm using Firefox 3.6 here on Debian Lenny 5.0.3, it looks and feels like Firefox. I neither like it better nor less than I ever have. Works a treat for browsing the internet :popcorn:
Out of interest, did you install it using the package manager?

---

### Post by Technoviking on 2010-01-21
> **sudoer541 said:**
> where can I find a .deb package to install Firefox 3.6?

dont advice me to compile anything please, I just want a point and click solution.

I have heard there are plans to upgrade Firefox to version 3.6 in Ubuntu 9.10, but it may take a few week due to changes needed in the language packs.

**PLEASE** be careful and thinking about random deb files for Firefox 3.6. They maybe be poorly built or even malicious and really screw up your Ubuntu install.

T-V

---

### Post by phrostbyte on 2010-01-21
There is three options to (easily) install Firefox 3.6 on Ubuntu currently:

32-bit only builds:
- Download directly from Mozilla's site. This is just an archive with Firefox it, and it should run with a simple double click.

- Use this repository: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) (it can be installed with copy/pasting a few commands)

32-bit or 64-bit:
- [http://ubuntuforums.org/showpost.php?p=8701613&postcount=14](http://ubuntuforums.org/showpost.php?p=8701613&postcount=14) (note the underline)

- Wait till Ubuntu 10.04 is released. :lolflag: (Unless the Ubuntu team decides to officially backport 3.6 to Karmic)

----
The "hard" way would be to *apt-get source firefox*, replace all the Firefox 3.5 source code in the source package with Firefox 3.6 sources, and rebuild it with debuild 

If that will actually work. :P

---

### Post by Eisenwinter on 2010-01-21
> **Technoviking said:**
> I have heard there are plans to upgrade Firefox to version 3.6 in Ubuntu 9.10, but it may take a few week due to changes needed in the language packs.

**PLEASE** be careful and thinking about random deb files for Firefox 3.6. They maybe be poorly built or even malicious and really screw up your Ubuntu install.

T-V
So could the official debs released by cannonical. You can never be 100% sure, unless you have looked at the source code and then created the package.

---

### Post by phrostbyte on 2010-01-21
> **Eisenwinter said:**
> So could the official debs released by cannonical. You can never be 100% sure, unless you have looked at the source code and then created the package.

Right, but it is less likely.

---

### Post by Eisenwinter on 2010-01-21
> **phrostbyte said:**
> Right, but it is less likely.
Of course.

---

### Post by lovinglinux on 2010-01-21
See [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Technoviking on 2010-01-21
> **Eisenwinter said:**
> So could the official debs released by cannonical. You can never be 100% sure, unless you have looked at the source code and then created the package.

Everyone who has upload rights to the Ubuntu repo has been vetted by the MOTU team (for Universe packages) or case of core software like Firefox by the Ubuntu Tech Board. It is not 100% fool proof but can not compared to randomly created deb found on the net.

T-V

---

### Post by kevCast on 2010-01-21
> **Techsnap said:**
> If you're running x86 just download it from the Mozilla site and extract it to /opt.

The fact they don't have x86_64 binary builds is so infuriating.

---

### Post by cariboo on 2010-01-21
There is a ppa for Firefox 3.6/3.7, it is located [here]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa").

---

### Post by nanotube on 2010-01-21
the ubuntuzilla repository, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) has firefox3.6. 

it contains the unmodified 32bit mozilla builds of the releases, just packaged into a .deb and stuffed into a repository.

you can add the repository to your sources.list and install the package from it (then you'll get automatic updates through the update manager).

---

### Post by Gallahhad on 2010-01-22
> **Eisenwinter said:**
> Out of interest, did you install it using the package manager?
No, I downloaded it from [here]("http://en-us.www.mozilla.com/en-US/") and run it out of a folder in ~/ 
I am using MS ttf fonts from my XP partition, and all is well.

---

### Post by sudoer541 on 2010-01-22
> **cariboo907 said:**
> There is a ppa for Firefox 3.6/3.7, it is located [here]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").

thanks cariboo! 
that was easy.
Now I downloaded the needed packages and dependencies, but when I try to install the packages I get some dependencies error messages.

---

### Post by quazi on 2010-01-22
> **Eisenwinter said:**
> Of course.

So you're advocating that one reads the source of every program they install.  For you that may be an acceptable solution, but there are those who want their systems to work without dedicating large amounts of time reading through source code.  The entire premise of Ubuntu is that we have software channels that are vetted and known to be safe.  If you're truly worried about downloading debs from Mozilla's site due to malicious code, I suspect you need to get your head examined.  

Attitudes like this on forums for distributions similar to Ubuntu are certainly detrimental to the spread of linux.  

Reasonable Request: "Oh I don't want to have installing programs be a hassle."

Response:"Then GTFO."

---

### Post by sudoer541 on 2010-01-22
ok, I am downloading the FF3.6 packages from [here ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages")but I get the dependencies error.
I am downloading the 32bit packages.

---

### Post by bodhi.zazen on 2010-01-22
> **sudoer541 said:**
> where can I find a .deb package to install Firefox 3.6?

dont advice me to compile anything please, I just want a point and click solution.

> **Eisenwinter said:**
> Then don't use Linux.

There is much wisdom in what Eisenwinter is advising.

If you want "simple" and "point and click" then you will have to wait for the Ubuntu developers to backport FF 3.6.

If you want to run the latest, greatest applications, outside of the ubuntu repositories you will need to learn 

./configure make make install

Yes it is intimidating, but it is not *that* hard.

Besides, firefox is distributed as a binary, nothing more then downloading and extracting, all of which is point and click.

The instructions for Linux, and even Ubuntu, are on the Firefox web site and the instructions are, IMO, trivial to follow:

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

If that is too hard, you will need to wait, perhaps as long as Ubuntu 10.10

Your other option is something like Arch Linux or Gentoo, but again this requires more then a point and click mentality.

Linux offers choice, the choice is yours.

---

### Post by pablo180 on 2010-01-22
> **whiskeylover said:**
> I'm not running Ubuntu right now (I'm at work), but on the windows version, I just clicked the menu "Help/Check for Updates". It found the 3.6 update and installed it for me. 

Maybe there is a similar menu option for the linux version? I'll go home and check later.

You can on Ubuntu too. Hit ALT+F2 and type 

```
gksudo firefox
```

That opens Firefox with full privileges. Then Help > Check For Updates, it should do it automatically. That is what I did and I now have Firefox 3.6. I'm on Karmic but I presume it's the same?

Flash refuses to work at the moment but I am going to try the latest version from Adobe.

---

### Post by pablo180 on 2010-01-22
> **Eisenwinter said:**
> Then don't use Linux.


What? I was expecting a "It's mine, all mine I say!!" after that. 

It's people like you that hold Linux back and want to keep it all GUI-less, command line driven and next to useless except to an elite. Most people and by that I mean 99.99% of the population do not want to learn every command by heart to achieve even the simplest of things, they have lives.

A computer, and by default its OS, are tools not a religion or way of life.

---

### Post by pablo180 on 2010-01-22
> **pablo180 said:**
> You can on Ubuntu too. Hit ALT+F2 and type 

```
gksudo firefox
```

That opens Firefox with full privileges. Then Help > Check For Updates, it should do it automatically. That is what I did and I now have Firefox 3.6. I'm on Karmic but I presume it's the same?

Flash refuses to work at the moment but I am going to try the latest version from Adobe.

Scratch that! Adobe kept detecting my OS as Mac OS X, I thought it odd and checked Firefox according to Firefox that's what I have (see attachment)! Something went badly wrong.

---

### Post by snowpine on 2010-01-22
> **pablo180 said:**
> What? I was expecting a "It's mine, all mine I say!!" after that. 

It's people like you that hold Linux back and want to keep it all GUI-less, command line driven and next to useless except to an elite. Most people and by that I mean 99.99% of the population do not want to learn every command by heart to achieve even the simplest of things, they have lives.

A computer, and by default its OS, are tools not a religion or way of life.

It has nothing to do with the command line or elitism. It has everything to do with trusting the Canonical developers. They've created a very nice, free Linux distribution for you that happens to use Firefox 3.5 as its default browser. Using the provided version of Firefox requires nothing more difficult than Applications->Internet->Firefox or simply clicking the little orange fox icon on the panel. Even a Windows user should be able to launch Firefox 3.5 in Ubuntu without reading the manual. :)

Now if you believe you know better than the people who developed Ubuntu, and think that Firefox 3.6 is stable, trusted, and thoroughly tested with Ubuntu 9.10, then there are about 10 different methods for installing it (some easier than others) but please don't ask the Ubuntu devs to provide a one-click solution for something that they do not recommend. :(

---

### Post by chris200x9 on 2010-01-22
I didn't know 3.6 was out! Thanx for this thread, one question did the FINALLY fix that bug when printing to pdf?

---

### Post by quazi on 2010-01-22
> **snowpine said:**
> It has nothing to do with the command line or elitism. It has everything to do with trusting the Canonical developers. They've created a very nice, free Linux distribution for you that happens to use Firefox 3.5 as its default browser. Using the provided version of Firefox requires nothing more difficult than Applications->Internet->Firefox or simply clicking the little orange fox icon on the panel. Even a Windows user should be able to launch Firefox 3.5 in Ubuntu without reading the manual. :)

Now if you believe you know better than the people who developed Ubuntu, and think that Firefox 3.6 is stable, trusted, and thoroughly tested with Ubuntu 9.10, then there are about 10 different methods for installing it (some easier than others) but please don't ask the Ubuntu devs to provide a one-click solution for something that they do not recommend. :(

I don't think he was asking specifically that the Ubuntu devs to provide a one-click solution.  What he was asking (in my eyes), was if there was one available.  Thanks to the ubiquity of deb packages, there are several ways to install firefox 3.6 without mucking about with the command line.  

What does trusting the developers mean?  They have created a nice, stable operating system, but I hardly trust them to know exactly what EVERY user wants.  It's absurd to think that if something does not exist in the default repositories that Ubuntu devs think you shouldn't install it.  It may just mean that they don't think that everyone will want/need it installed.

"Now if you believe you know better than the people who developed Ubuntu"

What a hilarious line.  If you install any program not included in the repositories, you must arrogantly believe that know better than the people who developed Ubuntu.  The devs are all-knowing about what should be installed on a users system.  Silly me, I just use Ubuntu as an operating system, not as a complete unalterable program suite.

---

### Post by snowpine on 2010-01-22
> **quazi said:**
> I don't think he was asking specifically that the Ubuntu devs to provide a one-click solution.  What he was asking (in my eyes), was if there was one available.  Thanks to the ubiquity of deb packages, there are several ways to install firefox 3.6 without mucking about with the command line.  

What does trusting the developers mean?  They have created a nice, stable operating system, but I hardly trust them to know exactly what EVERY user wants.  It's absurd to think that if something does not exist in the default repositories that Ubuntu devs think you shouldn't install it.  It may just mean that they don't think that everyone will want/need it installed.

"Now if you believe you know better than the people who developed Ubuntu"

What a hilarious line.  If you install any program not included in the repositories, you must arrogantly believe that know better than the people who developed Ubuntu.  The devs are all-knowing about what should be installed on a users system.  Silly me, I just use Ubuntu as an operating system, not as a complete unalterable program suite.

I respect your opinion :) but in my experience on these forums, most of the "OMG!!! Karmic is the worst release EVER... it's so UNSTABLE!!!" posters are the people who have installed a bunch of experimental or 3rd party applications and PPA's. 

Maybe my position is unpopular, but I truly believe the most stable Ubuntu experience is achieved by installing from the official repositories using the package manager. 

I have not found a single website that works with FF3.6 but not 3.5.

---

### Post by sudoer541 on 2010-01-22
> **bodhi.zazen said:**
> There is much wisdom in what Eisenwinter is advising.

If you want "simple" and "point and click" then you will have to wait for the Ubuntu developers to backport FF 3.6.

If you want to run the latest, greatest applications, outside of the ubuntu repositories you will need to learn 

./configure make make install

Yes it is intimidating, but it is not *that* hard.

Besides, firefox is distributed as a binary, nothing more then downloading and extracting, all of which is point and click.

The instructions for Linux, and even Ubuntu, are on the Firefox web site and the instructions are, IMO, trivial to follow:

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

If that is too hard, you will need to wait, perhaps as long as Ubuntu 10.10

Your other option is something like Arch Linux or Gentoo, but again this requires more then a point and click mentality.

**Linux offers choice, the choice is yours.**

yeah but .deb choice is not offered, so thats not a fair choice. 
anyway I have a dependency problems with the link that cariboo posted. anyone know how to solve it?

---

### Post by pablo180 on 2010-01-22
> **snowpine said:**
> It has nothing to do with the command line or elitism. It has everything to do with trusting the Canonical developers. They've created a very nice, free Linux distribution for you that happens to use Firefox 3.5 as its default browser. Using the provided version of Firefox requires nothing more difficult than Applications->Internet->Firefox or simply clicking the little orange fox icon on the panel. Even a Windows user should be able to launch Firefox 3.5 in Ubuntu without reading the manual. :)

Now if you believe you know better than the people who developed Ubuntu, and think that Firefox 3.6 is stable, trusted, and thoroughly tested with Ubuntu 9.10, then there are about 10 different methods for installing it (some easier than others) but please don't ask the Ubuntu devs to provide a one-click solution for something that they do not recommend. :(

I understand what you are saying but it doesn't really make sense. I don't have to check with Microsoft to ensure that every browser update will work on Windows, I assume the software makers have already tested it. 

There's no reason to assume that Firefox 3.5 is safe, but not 3.6 and if it is released for Linux, or even specifically Ubuntu, one would assume that Mozilla tested it and weren't relying on me to do so!

As I said I do understand where you are coming from, but although the repositories are one of the great benefits of Ubuntu in most ways, sometimes they can be a drawback, as is the case with software developed at a fast pace like browsers, and even email applications (Thunderbird 3?)

---

### Post by snowpine on 2010-01-22
> **pablo180 said:**
> I understand what you are saying but it doesn't really make sense. I don't have to check with Microsoft to ensure that every browser update will work on Windows, I assume the software makers have already tested it. 

There's no reason to assume that Firefox 3.5 is safe, but not 3.6 and if it is released for Linux, or even specifically Ubuntu, one would assume that Mozilla tested it and weren't relying on me to do so!

As I said I do understand where you are coming from, but although the repositories are one of the great benefits of Ubuntu in most ways, sometimes they can be a drawback, as is the case with software developed at a fast pace like browsers, and even email applications (Thunderbird 3?)

Every package in Ubuntu (including the web browser naturally) receives security updates and bug fixes for the lifespan of the release (April 2011 for Karmic). In other words, if a vulnerability is discovered in FF3.5 and fixed in FF3.8 (hypothetically), the version of FF3.5 in the Ubuntu repositories will be patched accordingly.

The question as I understand it is not whether or not FF3.6 will work in Karmic (obviously it will) but whether it's prudent for an inexperienced Linux user to install it himself the day it's released or wait a little while for the Ubuntu developers to test it and move it to the repository. I think my opinion is clear. :)

---

### Post by sudoer541 on 2010-01-22
> **pablo180 said:**
> What? I was expecting a "It's mine, all mine I say!!" after that. 

It's people like you that hold Linux back and want to keep it all GUI-less, command line driven and next to useless except to an elite. Most people and by that I mean 99.99% of the population do not want to learn every command by heart to achieve even the simplest of things, they have lives.

A computer, and by default its OS, are tools not a religion or way of life.

=D> well said!!!
I really dont understand why I have to work so hard to install/upgrade a browser, seriously this is ridiculous!
I dont want to waste my time learning to use the command line because 99% of home users dont care how their pc works as long as it works properly and yes I have a life. 
If this continues I am going back to windows for good! 
I mean windows is not as secure as ubuntu, but hey I can always install an antivirus. 
But seriously I never got any viruses while using windows. I think people should visit and download files from trusted sites, other than that the security and stability issues of windows are pure myth.

---

### Post by Ric_NYC on 2010-01-22
> **pablo180 said:**
> What? I was expecting a "It's mine, all mine I say!!" after that. 

It's people like you that hold Linux back and want to keep it all GUI-less, command line driven and next to useless except to an elite. Most people and by that I mean 99.99% of the population do not want to learn every command by heart to achieve even the simplest of things, they have lives.

A computer, and by default its OS, are tools not a religion or way of life.



**Bravooo!!! Bravisimoooo!!!**

---

### Post by snowpine on 2010-01-22
> **sudoer541 said:**
> =D> well said!!!
I really dont understand why I have to work so hard to install/upgrade a browser, seriously this is ridiculous!
I dont want to waste my time learning to use the command line because 99% of home users dont care how their pc works as long as it works properly and yes I have a life. 
If this continues I am going back to windows for good! 
I mean windows is not as secure as ubuntu, but hey I can always install an antivirus. 
But seriously I never got any viruses while using windows. I think people should visit and download files from trusted sites, other than that the security and stability issues of windows are pure myth.

I am still curious to hear which specific websites stopped working for you with FF 3.5, that are worth switching back to Windows for?

---

### Post by phrostbyte on 2010-01-22
> **snowpine said:**
> It has nothing to do with the command line or elitism. It has everything to do with trusting the Canonical developers. They've created a very nice, free Linux distribution for you that happens to use Firefox 3.5 as its default browser. Using the provided version of Firefox requires nothing more difficult than Applications->Internet->Firefox or simply clicking the little orange fox icon on the panel. Even a Windows user should be able to launch Firefox 3.5 in Ubuntu without reading the manual. :)

Now if you believe you know better than the people who developed Ubuntu, and think that Firefox 3.6 is stable, trusted, and thoroughly tested with Ubuntu 9.10, then there are about 10 different methods for installing it (some easier than others) but please don't ask the Ubuntu devs to provide a one-click solution for something that they do not recommend. :(

I don't know if this has been said, but an official backport of Firefox 3.6 to Karmic seems to be a real possibility.

---

### Post by lovinglinux on 2010-01-22
> **phrostbyte said:**
> I don't know if this has been said, but an official backport of Firefox 3.6 to Karmic seems to be a real possibility.

No it hasn't, but i t has been posted on other threads. See discussion after post #343 at [http://ubuntuforums.org/showthread.php?t=1193567&page=35](http://ubuntuforums.org/showthread.php?t=1193567&page=35)

---

### Post by snowpine on 2010-01-22
It is also worth pointing out that even "bleeding edge" distros like sidux and Arch don't have FF3.6 in their repos quite yet. It is totally normal for *any* Linux distro to have a slight delay before the latest version of something comes through updates.

---

### Post by aysiu on 2010-01-22
> **sudoer541 said:**
> where can I find a .deb package to install Firefox 3.6?

dont advice me to compile anything please, I just want a point and click solution. I would highly recommend adding the UbuntuZilla repositories. The terminal is the quickest and easiest way to do it, but if you want point-and-click instructions, they're here:
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

I recommend adding the actual repository, because then your Firefox will *automatically* upgrade to the newest version when it comes out, and you won't have to keep posting these new threads.

If you just want Firefox 3.6 without adding the repository, you can just download and double-click this .deb:
[http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_3.6-0ubuntu1_i386.deb](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_3.6-0ubuntu1_i386.deb)

**Warning**: Works for only 32-bit Ubuntu. If you don't know if you have 32-bit or 64-bit, they you have 32-bit.

Ignore anyone who asks you to add the PPA repositories, for two reasons: 1) The PPA repositories are not any easier to add the UbuntuZilla repositories, and 2) The PPA repositories use the daily builds, which can be unstable, whereas UbuntuZilla has only the stable official Firefox release.

---

### Post by quazi on 2010-01-22
> **snowpine said:**
> I am still curious to hear which specific websites stopped working for you with FF 3.5, that are worth switching back to Windows for?

I don't believe the OP ever claimed that websites didn't work with FF 3.5, merely that he wanted the newest version available - nothing wrong with that.  There are other differences between the two versions (as you can tell by that number on the right; it went form a 5 to a 6) and an example of that is better javascript performance.

---

### Post by bodhi.zazen on 2010-01-22
This entire thread is a bunch of ranting from people who have never tried installing the binary from mozilla.

It is simple to do, does not use the command line, and is almost exactly the same in Linux as it is in Windows.

There is absolutely no need for a .deb, ppa, backport, script, command line, none of that.

Installing Firefox in Linux is just the same as Windows.

Go to the downloads page, the linux version was selected automatically.

**[http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US)**

When you click the download, a dialog box pops up asking if you want to save the file or open it with Archive manger (which is the default).

Click OK (archive manager, defaults)

firefox-3.6.tag.gz downloads -> archive manager opens -> click extract -> click OK

You now have a folder in your home directory, called "firefox"

Go to places -> home
open the firefox directory
double click on the "firefox" file -> select run

Friefox runs fine

If you wish to change the launcher in your top panel

Right click the firefox icon, select "properties"

In the "command" box you can enter the path, or hit the "Browse" button 

If you use the browse button, the dialog will open to your home directory. double click the firefox directory, select firefox (in the firefox directory) click "OK"

It is as easy as installing firefox in Windows, the process is the same.

All this was done without so much as opening the command line.

You are ranting about something that simply does not exist.

Installing firefox in this way has the advantage in that it will now update automatically or manually 

In firefox, go to Help -> check for updates

Again exactly the same as windows.

To set firefox 3.6 as yoru default browser go to

System -> Preferences -> Preferred Applications

In the dialog, in Web Browser, select custom from the pull down menu, in the command box enter

/home/your_user_name/firefox/firefox

If you wish you can install firefox system wide, extract the tar to /usr/local/firefox

My point is, the differences between installing firefox 3.6 in Windows vs Linux are trivial at best and in fact are all performed via a few mouse clicks.

---

### Post by Excedio on 2010-01-22
> **bodhi.zazen said:**
> If you wish you can install firefox system wide, extract the tar to /usr/local/firefox
 
Can you explain this part to me a bit more clearly? Also, what acout the current install of Firefox, will this process end up running them side-by-side or will 3.6 overwrite 3.5?
 
FYI...I couldn't care less how I install it as long as it's done correctly. Thanks.

---

### Post by aysiu on 2010-01-22
> **Excedio said:**
> 
FYI...I couldn't care less how I install it as long as it's done correctly. Thanks. Then do it with UbuntuZilla:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

It will be done correctly, the Ubuntu and Mozilla builds will be separate, and you will get automatic updates when 3.7 or 3.8 or even 4.0 comes out.

---

### Post by lovinglinux on 2010-01-22
> **bodhi.zazen said:**
> This entire thread is a bunch of ranting from people who have never tried installing the binary from mozilla...

Yes, it can be as simple as that, but wouldn't be a security risk to run Firefox from the home folder? Isn't it why the tutorials explains how to extract to /opt?

---

### Post by mikewhatever on 2010-01-22
> **bodhi.zazen said:**
> This entire thread is a bunch of ranting from people who have never tried installing the binary from mozilla.

It is simple to do, does not use the command line, and is almost exactly the same in Linux as it is in Windows.

.......

+1. It's simply ranting for the sake of it. Some people are never ever satisfied, I guess.

> **lovinglinux said:**
> Yes, it can be as simple as that, but wouldn't be a security risk to run Firefox from the home folder? Isn't it why the tutorials explains how to extract to /opt?

In what way is it a security risk?

---

### Post by bodhi.zazen on 2010-01-22
> **Excedio said:**
> Can you explain this part to me a bit more clearly? Also, what acout the current install of Firefox, will this process end up running them side-by-side or will 3.6 overwrite 3.5?
 
FYI...I couldn't care less how I install it as long as it's done correctly. Thanks.

Download the firefox tar ball, firefox-3.6.tar.gz

If you wish to use a gui, use archive manager.

```
sudo tar xvf firefox-3.6.tar.gz -C /usr/local
```

Then update your links.

So long as you install firefox to /usr/local it runs side-by-side firefox 3.5.x, you may run either version, but not both at the same time

ff 3.5.x /usr/bin/firefox

ff 3.6 /usr/local/firefox/firefox

/usr/bin/firefox is a link, so if you wish you could

```
sudo unlink /usr/bin/firefox
ln -s /usr/local/firefox/firefox /usr/bin/firefox
```

But I would not do that as it may change with system updates.

If you have only one user, IMO, just keep firefox 3.6 in your home directory.

---

### Post by Excedio on 2010-01-22
> **aysiu said:**
> Then do it with UbuntuZilla:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)
 
It will be done correctly, the Ubuntu and Mozilla builds will be separate, and you will get automatic updates when 3.7 or 3.8 or even 4.0 comes out.
 
I actually have this currently. I'm already running 3.6, however...I'd like to explore my options.
 
[IMG]http://www.searchviews.com/wp-content/themes/clean-copy-full-3-column-1/images/the_more_you_know2.jpg[/IMG]

---

### Post by bodhi.zazen on 2010-01-22
> **lovinglinux said:**
> Yes, it can be as simple as that

That is exactly what the OP is asking for and more so, exactly what all the ranting is about.

> but wouldn't be a security risk to run Firefox from the home folder? Isn't it why the tutorials explains how to extract to /opt?

Tutorials advise opt so that multiple users have access to it.

It is not a security risk to keep it in $HOME, especially for a single user.

the location you install firefox into is up to you, /opt or /usr/local , either one is just fine.

In terms of security, well your system is only as secure as your users. If a malicious user has physical access it really does not matter if ff-3.6 is in $HOME or /opt

---

### Post by lovinglinux on 2010-01-22
> **mikewhatever said:**
> In what way is it a security risk?

Because you don't need root privileges to replace the binaries with a malicious one? I'm not sure if someone outside would need root privileges to hack your machine anyway, so I might be just a little too much paranoid.

> **bodhi.zazen said:**
> Tutorials advise opt so that multiple users have access to it.

It is not a security risk to keep it in $HOME, especially for a single user.

the location you install firefox into is up to you, /opt or /usr/local , either one is just fine.

In terms of security, well your system is only as secure as your users. If a malicious user has physical access it really does not matter if ff-3.6 is in $HOME or /opt

Thanks for the clarification. I have included a note on my tutorial with that info.

---

### Post by Eisenwinter on 2010-01-22
> **sudoer541 said:**
> yeah but .deb choice is not offered, so thats not a fair choice.
Then get the source, and make a deb package, allowing others to have that choice.

Not a fair choice?

You ARE given the possibility to use the software, the installation way just doesn't meet your "standards", which imo, is really sad.

Yes, I agree, package manager first, but when you can't get software from the package manager, you shouldn't be afraid to install it manually.

You're limiting yourself very much if you choose not to use some program just because it's not in the repositories of your chosen distribution.

---

### Post by sudoer541 on 2010-01-22
> **snowpine said:**
> I am still curious to hear which specific websites stopped working for you with FF 3.5, that are worth switching back to Windows for?


well because there is no easy way (as in .deb package installation)

---

### Post by sudoer541 on 2010-01-22
> **aysiu said:**
> I would highly recommend adding the UbuntuZilla repositories. The terminal is the quickest and easiest way to do it, but if you want point-and-click instructions, they're here:
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

I recommend adding the actual repository, because then your Firefox will *automatically* upgrade to the newest version when it comes out, and you won't have to keep posting these new threads.

If you just want Firefox 3.6 without adding the repository, you can just download and double-click this .deb:
[http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_3.6-0ubuntu1_i386.deb](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_3.6-0ubuntu1_i386.deb)

**Warning**: Works for only 32-bit Ubuntu. If you don't know if you have 32-bit or 64-bit, they you have 32-bit.

Ignore anyone who asks you to add the PPA repositories, for two reasons: 1) The PPA repositories are not any easier to add the UbuntuZilla repositories, and 2) The PPA repositories use the daily builds, which can be unstable, whereas UbuntuZilla has only the stable official Firefox release.


OMG!!! you're the best of the best!!! thank you so much the the second link with the .deb worked famously! 
One more question, when this problem occurs again where do I go to download the new Firefox .deb? from source forge? 

Thanks again!!!:D

---

### Post by sudoer541 on 2010-01-22
> **bodhi.zazen said:**
> This entire thread is a bunch of ranting from people who have never tried installing the binary from mozilla.

It is simple to do, does not use the command line, **and is almost exactly the same in Linux as it is in Windows.**

There is absolutely no need for a .deb, ppa, backport, script, command line, none of that.

[SIZE=3]**Installing Firefox in Linux is just the same as Windows.**[/SIZE]

Go to the downloads page, the linux version was selected automatically.

**[http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US)**

When you click the download, a dialog box pops up asking if you want to save the file or open it with Archive manger (which is the default).

Click OK (archive manager, defaults)

firefox-3.6.tag.gz downloads -> archive manager opens -> click extract -> click OK

You now have a folder in your home directory, called "firefox"

Go to places -> home
open the firefox directory
double click on the "firefox" file -> select run

Friefox runs fine

If you wish to change the launcher in your top panel

Right click the firefox icon, select "properties"

**In the "command" box you can enter the path, or hit the "Browse" button **

If you use the browse button, the dialog will open to your home directory. double click the firefox directory, select firefox (in the firefox directory) click "OK"

**It is as easy as installing firefox in Windows**, the process is the same.

All this was done without so much as opening the command line.

**You are ranting about something that simply does not exist.**

Installing firefox in this way has the advantage in that it will now update automatically or manually 

**In firefox, go to Help -> check for updates**

Again exactly the same as windows.

To set firefox 3.6 as yoru default browser go to

System -> Preferences -> Preferred Applications

In the dialog, in Web Browser, select custom from the pull down menu,** in the command box enter**

/home/your_user_name/firefox/firefox

If you wish you can install firefox system wide, extract the tar to /usr/local/firefox

My point is, the differences between installing firefox 3.6 in Windows vs Linux are trivial at best and in fact are all performed via a few mouse clicks.

Wrong!
the windows and mac os X way is the easiest.

Windows:
either click on help and update firefox (super easy)
OR download the .exe from mozilla (super easy)

Mac Os X:
either click on help and update firefox (super easy)
Or download from mozilla and after the d/l is done drag and drop the app into the applications folder

Linux:
either use the commandline (hard for normal people who want things ready so they can move on with their lives)
download the tar.gz from mozilla and extract it to home and the opt directory and then make a shortcut. (again this is hard for people who want things to "just work")

see the difference? 
I really hate it when I have to go through this work  for "upgrading my internet browser" I am not a programmer I am just a computer user who expects things to work as easy as possible. 
btw there is a huge difference between windows and ubuntu installation.
your solutions seems to be very long and hard to follow. too many "do this and do that"
in windows you just click on a .exe file and done.
btw the help> check for updates its grayed out in firefox ubuntu version. Even if I enable it, it does not detect new version of firefox.
anyway, the problem is solved thanks to aysiu.

---

### Post by aysiu on 2010-01-22
> **sudoer541 said:**
> OMG!!! you're the best of the best!!! thank you so much the the second link with the .deb worked famously! 
One more question, when this problem occurs again where do I go to download the new Firefox .deb? from source forge? 

Thanks again!!!:D This problem won't happen again if you add the UbuntuZilla repository. Just add it. Then every time Firefox has a new version, you can easily install it just as you would any normal Ubuntu update. No more need to manually track down .deb files.

---

### Post by aysiu on 2010-01-22
> **sudoer541 said:**
> 
Linux:
either use the commandline (hard for normal people who want things ready so they can move on with their lives)
download the tar.gz from mozilla and extract it to home and the opt directory and then make a shortcut. (again this is hard for people who want things to "just work") That's not really it at all.

In Linux, you use the package manager to get updates to software.

In Ubuntu, the updates come every six months with a new release. No .tar.gz. No manual extraction. It just comes automatically after six months.

In rolling releases (Debian unstable, Arch Linux, PCLinuxOS), the package manager pulls in new versions immediately (no six-month wait).

The key is that in Linux, you use the repositories instead of manually downloading updates yourself. Think of it like the iTunes App Store or Android Market.

---

### Post by bodhi.zazen on 2010-01-22
> **sudoer541 said:**
> Wrong!
the windows and mac os X way is the easiest.

Windows:
either click on help and update firefox (super easy)
OR download the .exe from mozilla (super easy)

Mac Os X:
either click on help and update firefox (super easy)
Or download from mozilla and after the d/l is done drag and drop the app into the applications folder

Linux:
either use the commandline (hard for normal people who want things ready so they can move on with their lives)
download the tar.gz from mozilla and extract it to home and the opt directory and then make a shortcut. (again this is hard for people who want things to "just work")

see the difference? 

This is yet another example of people ranting without knowing what they are talking about.

If you follow my instructions (rather then embarrass yourself), rather then using firefox from the Ubuntu Repositories, then it updates just like OSX and Windows (Help - > check for updates).

Also, if you bother to read my instructions, it is all point and click, no command line or programming was involved.

Please quit your senseless trolling.

---

### Post by sudoer541 on 2010-01-22
> **bodhi.zazen said:**
> This is yet another example of people ranting without knowing what they are talking about.

If you follow my instructions (rather then embarrass yourself), rather then using firefox from the Ubuntu Repositories, then it updates just like OSX and Windows (Help - > check for updates).

Also, if you bother to read my instructions, it is all point and click, no command line or programming was involved.

Please quit your senseless trolling.

I am not trolling 
I am just explaining the difficulty level of each OS's installation way of firefox.
Yes I did read your instructions but its still not easy enough. 
Now, I had firefox 3.5 (or whatever came with ubuntu) and I went to help> check for updates and the "check for updates" options is either not there or when I enable it it does not detect the newest version of firefox.
again this problem is solved since aysiu gave me the link to the .deb @ source forge
I hope I was clear.
All the best!

---

### Post by Techsnap on 2010-01-22
He isn't trolling, the simple fact is it is more difficult to install initially from the Mozilla site than it is on Windows. It's plain obvious.

---

### Post by Frak on 2010-01-22
> **bodhi.zazen said:**
> Please quit your senseless trolling.

I'm sorry, but I wholeheartedly agree with him. There's a large bias on "get dirty with the CLI and get it done", but not enough of a bias on "double click this, a prompt will ask you where to put things, and let it go, done". I mean, your method would work, but what if a casual user went to a website, we're going into hypothetical speaking here, and the website wanted Firefox 3.6. Maybe there's something about 3.6 that is just that much better than 3.5. You could either do what you said, which would work, but would be very confusing for a new or casual user that has no idea what's going on, or wait for the package to be backported/officially ported. Now, we go into what makes Windows and OS X so great is that the person creating the software can create a deployment system with relative ease. Very little work is involved between the compilation of the program and deployment. On Linux, that's not so much the case. They have to prepare .debs for the Debian/Ubuntu folks, .rpms for the RedHat/Fedora/OpenSuse/Mandria folks, and .tar.gzs for the Binary/Source folks who do know what they are doing (albeit the easiest crowd to please). And from personal experience, there's a large amount of work involved between compiling and deployment of the application in comparison to Windows or OS X.

Take for instance, Windows, it's very easy to create an installer for an application. It may be long at times, but it's very easy. Mac OS X is super simple as well, in fact, they tell you how to build the binary, and it packages it. If you need an installer, it's also very simple. Linux, well, for such a low market share, you're treading onto a large amount of work.

One of the best parts of Linux is the package manager. It's a centralized location of applications that have been vetted for stability and sanity. On the other hand with approaches taken by distributions like Ubuntu, the package manager becomes an enemy of sorts. It tells you what you can have installed, it tells you what you can't have installed. You over-rely on it for the software you need and take the control away from the application developers and place it in the hands of the packagers. Again, this has its pros and cons, but the biggest con is that it takes part of the reliability that people put in the 3rd party developers and puts them as the "bad guy" of sorts. It takes that feeling of community away that is preached so much around here. In essence, I would say that package managers fit nicely on servers but don't necessarily belong on the desktop, to a degree. It would be great if the application developer provided the binary but the system provided the dependencies.

Over this long-winded wall-o-text, I think I've shown my point of why I think sudoer is right.

---

### Post by sudoer541 on 2010-01-22
> **Techsnap said:**
> He isn't trolling, the simple fact is it is more difficult to install initially from the Mozilla site than it is on Windows. It's plain obvious.


Thank you:D

---

### Post by sudoer541 on 2010-01-22
> **Frak said:**
> I'm sorry, but I wholeheartedly agree with him. There's a large bias on "get dirty with the CLI and get it done", but not enough of a bias on "double click this, a prompt will ask you where to put things, and let it go, done". I mean, your method would work, but what if a casual user went to a website, we're going into hypothetical speaking here, and the website wanted Firefox 3.6. Maybe there's something about 3.6 that is just that much better than 3.5. You could either do what you said, which would work, but would be very confusing for a new or casual user that has no idea what's going on, or wait for the package to be backported/officially ported. Now, we go into what makes Windows and OS X so great is that the person creating the software can create a deployment system with relative ease. Very little work is involved between the compilation of the program and deployment. On Linux, that's not so much the case. They have to prepare .debs for the Debian/Ubuntu folks, .rpms for the RedHat/Fedora/OpenSuse/Mandria folks, and .tar.gzs for the Binary/Source folks who do know what they are doing (albeit the easiest crowd to please). And from personal experience, there's a large amount of work involved between compiling and deployment of the application in comparison to Windows or OS X.

Take for instance, Windows, it's very easy to create an installer for an application. It may be long at times, but it's very easy. Mac OS X is super simple as well, in fact, they tell you how to build the binary, and it packages it. If you need an installer, it's also very simple. Linux, well, for such a low market share, you're treading onto a large amount of work.

One of the best parts of Linux is the package manager. It's a centralized location of applications that have been vetted for stability and sanity. On the other hand with approaches taken by distributions like Ubuntu, the package manager becomes an enemy of sorts. It tells you what you can have installed, it tells you what you can't have installed. You over-rely on it for the software you need and take the control away from the application developers and place it in the hands of the packagers. Again, this has its pros and cons, but the biggest con is that it takes part of the reliability that people put in the 3rd party developers and puts them as the "bad guy" of sorts. It takes that feeling of community away that is preached so much around here. In essence, I would say that package managers fit nicely on servers but don't necessarily belong on the desktop, to a degree. It would be great if the application developer provided the binary but the system provided the dependencies.

Over this long-winded wall-o-text, I think I've shown my point of why I think sudoer is right.


thank you:D
It would be great if all linux distros had one universal package such as a deb or even a GUI accessible .bin.

---

### Post by Zoot7 on 2010-01-22
> **sudoer541 said:**
> Linux:
either use the commandline (hard for normal people who want things ready so they can move on with their lives)
download the tar.gz from mozilla and extract it to home and the opt directory and then make a shortcut. (again this is hard for people who want things to "just work")

see the difference? 
I really hate it when I have to go through this work  for "upgrading my internet browser" I am not a programmer I am just a computer user who expects things to work as easy as possible. 
btw there is a huge difference between windows and ubuntu installation.
your solutions seems to be very long and hard to follow. too many "do this and do that"
in windows you just click on a .exe file and done.
btw the help> check for updates its grayed out in firefox ubuntu version. Even if I enable it, it does not detect new version of firefox.
anyway, the problem is solved thanks to aysiu.
Honestly if you feel this way, Linux isn't really the OS you should be using. You do invariably have to drop to a shell at some point to get something done.
Distros like Ubuntu and others do promise a Linux for noobs or "Linux for Human Beings" experience whereby they try to minimize the usage ot things like the command line, but ultimately you do have to delve into technicalities at some point. As long as Linux as an ecosystem on the desktop is like this I don't believe you can effectively deliever a system that's user friendly in 100% of cases.

So if you want things to be point and click and user friendly, then just use Windows. ;)

EDIT:
> **sudoer541 said:**
> It would be great if all linux distros had one universal package such as a deb or even a GUI accessible .bin.
There's one of the Achilles Heal's of the Linux desktop, no two major distros can agree to do things in a similar and standardized manner. :)

---

### Post by lovinglinux on 2010-01-22
I don't know why you are still complaining. Don't you see all the posts on all the Firefox 3.6 threads (including this one) pointing to a blueprint that shows the policy of Firefox updates will be changed and most likely that soon we will see Firefox 3.6 backported into Karmic repositories? Mozilla is dropping support for Firefox 3.5 in six months, so there is not much Canonical can do about it.

In fact, if you update Firefox using the *ubuntu-mozilla-daily* ppa you will see that, unlike Shiretoko which was installed side-by-side with firefox-3.0, Namoroka updates the firefox-3.5 package instead.

---

### Post by toupeiro on 2010-01-22
ubuntuzilla *could* have been the answer to all this ridiculous "windows is easier to install" banter, however, +epicfail for no support for firefox 3.6 64-bit in the repo...  In almost all cases, ubuntu just works, except when it doesn't... :)  Its not a huge weight on my shoulders.  I know how to get things and install them manually.  I realized those circumstances may pop up by running linux and 64-bit quite a long time ago.  Very rarely do they pop up anymore, but it happens.

If you abandoned windows because you were looking a more uniform way to install things, maybe you should have skipped right over linux.  Weigh the pros and cons, and make your choice, but accept your choice for what it is.

---

### Post by JDShu on 2010-01-22
@lovinglinux: Were you replying to me? I'm not sure if my post was deleted or if I never posted anything in the first place XD. Poor memory.

---

### Post by lovinglinux on 2010-01-22
> **JDShu said:**
> @lovinglinux: Were you replying to me? I'm not sure if my post was deleted or if I never posted anything in the first place XD. Poor memory.

No it wasn't directed to anyone in particular. I also have a poor memory and don't keep tabs on who is complaining or not :) In fact, I don't even bother reading all those arguments.

---

### Post by JDShu on 2010-01-22
LOL fair enough, I think I just forgot to submit my post, actually.

Well, Firefox 3.6 is a huge leap from 3.5.... but I use 3.7a1pre so I am better than you all muhahaha!

---

### Post by lovinglinux on 2010-01-22
> **JDShu said:**
> LOL fair enough, I think I just forgot to submit my post, actually.

Well, Firefox 3.6 is a huge leap from 3.5.... but I use 3.7a1pre so I am better than you all muhahaha!

:lol: I wish I could do that, but I have more than 40 extensions installed and even with compatibility check disabled, some of them might not work at all. Haven't tried tho.

---

### Post by nanotube on 2010-01-23
> **toupeiro said:**
> ubuntuzilla *could* have been the answer to all this ridiculous "windows is easier to install" banter, however, +epicfail for no support for firefox 3.6 64-bit in the repo...  

well, as soon as mozilla starts releasing 64bit builds of their releases, it they'll be in the ubuntuzilla repository. until then - feel free to bug mozilla about it, maybe it'll speed things up in that regard :)

---

