---
title: "Upgrading to Intrepid already???"
date: 2008-05-06
forum: Repositories &amp; Backports
---

### Post by macroshaft on 2008-05-06
I read a post just after the release of hardy where someone said they had updated their system to point to the Intrepid repositories and now just had to wait for them to open. I am very interested in how this new version will develop so thought I would do the same.

I adjusted sources list so that any reference to hardy was changed to intrepid and for a time this appeared to work, update manager reported errors locating the repositories for a time and then was ok when the repositories opened but a few days later it attempted to dist upgrade and produced an EM stating that this upgrade manager cannot dist upgrade from intrepid to hardy, what am I doing wrong?

---

### Post by ronacc on 2008-05-06
there probably isn't enough in the repos yet to do a dist-upgrade . they just uploaded the toolchain a couple of days ago . things start out kind of slow , just do a regular update daily .

---

### Post by wgrant on 2008-05-06
Do **NOT** attempt to upgrade to Intrepid at this point. If you need to ask what you're doing wrong, you are certainly not ready to upgrade to Intrepid. Your system will be rendered unbootable and otherwise many times throughout the cycle.

---

### Post by macroshaft on 2008-05-06
I'm not attempting a dist-upgrade, this is what it is trying to do as a normal daily upgrade.

If it's not safe to run a pc off these repositories yet at what point does it become usable?

---

### Post by wgrant on 2008-05-06
You certainly should be dist-upgrading, if you upgrade at all.

Unless you're a developer or a very experienced user, you should not consider using Intrepid until perhaps the last month of the development cycle.

---

### Post by aamukahvi on 2008-05-06
Already choked on me once ;) Running it in VirtualBox.

---

### Post by macroshaft on 2008-05-06
Right, I'm being advised here not to install intrepid, yet in the same thread people are admitting to using it. I've asked ho to install it and people say that they have but everyone is still AVOIDING TELLING ME HOW!!

If I wish to run it on a second pc out of curiosity it's my decision and that does not require me to be a developer.

It's great that people are showing that level of concern but it would be better if someone would answer my question.

---

### Post by aamukahvi on 2008-05-06
> **macroshaft said:**
> Right, I'm being advised here not to install intrepid, yet in the same thread people are admitting to using it. I've asked ho to install it and people say that they have but everyone is still AVOIDING TELLING ME HOW!!

If I wish to run it on a second pc out of curiosity it's my decision and that does not require me to be a developer.

It's great that people are showing that level of concern but it would be better if someone would answer my question.
Well,

[LIST=1]
[*]Install Hardy
[*]change /etc/apt/sources.list so it contains only this:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
[*]sudo aptitude update
[*]sudo aptitude dist-upgrade
[/LIST]
Have your backups ready and enjoy ;) Please use VirtualBox or a spare machine.

---

### Post by Eclipse. on 2008-05-06
Intrepid is still really messy and the syncs having got up and running fully yet.

Be prepared to fix broken packages and things but alot of things are broken, some of which will stop you from booting into a GUI.

---

### Post by Scheater5 on 2008-05-06
macroshaft, you seem eager to learn.  So for clarification purposes, I'll say this.  The instructions aamukahvi are, essentially, the "old," (and ugly) way of dist-upgrading.  It will point your apt to the intrepid servers and upgrade any packages as intrepid gets new versions.  In a sense, it's like using a permanently unstable dist like Debian Unstable.  
The difference being, Debian Unstable is infinitely more "stable" than intrepid is right now.  Intrepid is still undergoing massive work, and there are no guarantees (or even effort put in to guarantee) that everything will not break and your whole system come crashing down.  It, as they say, "kills computers and eats kittens."  It's more than "use at your own risk," there really is no point in using it unless you're a developer or packager working on it.  Using it on a workstation is like living in a house with nothing but a foundation.  
Knowing all this, if you still wanna try intrepid, by all means, use aamukahvi's instructions, and test away.  Submit bug reports (because you will have bugs) and help Intrepid be a better distribution.  Just dear God don't do it on your main machine.

Edit: I reread your post where you said you'd be installing it on a second machine out of curiosity.  Good form.  And you're right - you don't have to be a developer.  Given that, if you've got the time, take a while a get a launchpad account so you can start submitting and commenting on bug reports.  Consider my above post as the explanation behind all the caution you received from other posters.

---

### Post by ronacc on 2008-05-06
when are they going to open the intrepid forum so we can start whining bitching and moaning about broken stuff:lolflag:

---

### Post by wgrant on 2008-05-07
Two weeks after the last person inappropriately asks how to upgrade to Intrepid. Much like just before releases, except 167 times longer.

---

### Post by plun on 2008-05-07
> **ronacc said:**
> when are they going to open the intrepid forum so we can start whining bitching and moaning about broken stuff:lolflag:

Well...  don't forget broken nVidia drivers....:D

I have already tested and was stranded without any GUI  :^o, it was a Perl mess which was impossible to solve even for Aptitude 

But its more then just toolchain now...

[https://lists.ubuntu.com/archives/intrepid-changes/2008-May/thread.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-May/thread.html)

Just to have ./home on a separate partition...:KS

---

### Post by ronacc on 2008-05-07
as is my habit, I have intrepid , at least the toolchain and a few other things on a seperate drive , I haven't updated it in 2 days , that box has been occupied doing something else , if it ever finishes I'll update and see if my nvidia driver breaks :)

---

### Post by plun on 2008-05-07
> **ronacc said:**
> as is my habit, I have intrepid , at least the toolchain and a few other things on a seperate drive , I haven't updated it in 2 days , that box has been occupied doing something else , if it ever finishes I'll update and see if my nvidia driver breaks :)

OK, please notify us....:)

I also used a "do it yourself-brewed" 2.6.25 kernel and perhaps that
was the problem....173.08 works without patches for 2.6.25 anyway.

:)

---

### Post by ronacc on 2008-05-07
will do, but it will take awhile the box I've got intrepid on is d/ling the sources for the eeepc right now from the horribly slow asus server (16KBs 6hr avg ) and I've still got 1.2 Gig to go , Yes 173.08 works for me with 2.6.25 on my opensuse 11.0B2 install . I stll have the 2.6.24 kernel from hardy with intrepid  .

---

### Post by Eclipse. on 2008-05-07
> **plun said:**
> Well...  don't forget broken nVidia drivers....:D

I have already tested and was stranded without any GUI  :^o, it was a Perl mess which was impossible to solve even for Aptitude 



Downgrade libxfonts1 and you should get back in if its the same problem I had about default fonts.

---

### Post by plun on 2008-05-07
> **Eclipse. said:**
> Downgrade libxfonts and you should get back in if its the same problem I had about default fonts.

Aha...   :)

Well, it was impossible to startx because of this error.


I have OpenSolaris on the testbox for the moment....**Fedora 9**
must also be checked....especially drivers and ongoing "Multimedia dirty formats mess". I think "Fedoras guys" has solved it with total other solutions then "the Ubuntu mess".

Thanks !


ronacc: OK  !

---

### Post by mabovo on 2008-05-07
A good way to entry in the Intrepid world, try getting all PPA's available in every Ubuntu projects like xorg, kernel modules, etc and start installing those experimental packages at your flavor.

If you still have an spare time to spend looking for more advanced improvements to be considered including in Intrepid try a clean install of OpenSolaris that is called the next step Ubuntu will be when grows up ! :)

---

### Post by plun on 2008-05-07
> **mabovo said:**
> 
If you still have an spare time to spend looking for more advanced improvements to be considered including in Intrepid try a clean install of OpenSolaris that is called the next step Ubuntu will be when grows up ! :)

Well, that can be discussed... :) I was like "**Bambi on ice**" and must read manuals...:)  The package management is something totally new and
for both OpenSolaris and Ubuntu I really hope that **PackageKit** comes.
(despite of Debians view)  but... ZFS as file system, great and everything is really professionell integrated, "look and feel" = 10 points....

:)

---

### Post by mabovo on 2008-05-07
Ubuntu 10 x 1 OpenSolaris regarding the amount of packages available in the repos.

---

### Post by InfinityCircuit on 2008-05-08
I concurrently run the following two test machines:

1. Debian Sid daily upgraded to Experimental
2. Intrepid Ibex

it's quite enjoyable.

---

### Post by caryb on 2008-05-08
After upgrading to Intrepid I had my Xserver totally hosed! there are broken deps all over the place! One good thing to come out of this is that I'm on a clean Hardy install (as of 2 hours ago) to start the next round of testing. My recommendation [B][U]DO NOT DO IT JUST YET!
[/U][/B]

Cary

---

### Post by trikloretylen on 2008-05-08
> **caryb said:**
> After upgrading to Intrepid I had my Xserver totally hosed! there are broken deps all over the place! One good thing to come out of this is that I'm on a clean Hardy install (as of 2 hours ago) to start the next round of testing. My recommendation **_DO NOT DO IT JUST YET!_**

Intrepid works fine for me so far as long as I don't upgrade libxfont1.

---

### Post by chrisccoulson on 2008-05-08
> **caryb said:**
> After upgrading to Intrepid I had my Xserver totally hosed! there are broken deps all over the place! One good thing to come out of this is that I'm on a clean Hardy install (as of 2 hours ago) to start the next round of testing. My recommendation [B][U]DO NOT DO IT JUST YET!
[/U][/B]

Cary

I dist-upgraded to Intrepid the day that the repos opened, and my X is hosed too. But I don't care, as I'm only running it in VMWare atm.

---

### Post by plun on 2008-05-08
> **trikloretylen said:**
> Intrepid works fine for me so far as long as I don't upgrade libxfont1.

Yup, which also Eclipse pointed out earlier.

Package info
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libxfont1](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libxfont1)

Just to downgrade to Hardys version.


One strange issue I got is that I cannot lock this version with Synaptic...:confused:

---

### Post by disturbedite on 2008-05-08
forgive me if this is a stupid question... but where is the intrepid section in the forum?  it should be in this Development & Programming section like before shouldn't it?  has it not been implemented/added yet?

---

### Post by Naddiseo on 2008-05-08
> **caryb said:**
> After upgrading to Intrepid I had my Xserver totally hosed! there are broken deps all over the place! One good thing to come out of this is that I'm on a clean Hardy install (as of 2 hours ago) to start the next round of testing. My recommendation [B][U]DO NOT DO IT JUST YET!
[/U][/B]

Cary

I'm in the same boat; I changed my sources.lst to intrepid a day before hardy was released then xserver broke on Sunday, so I just reinstalled hardy, it's no biggy and I have backups of everything valuable. I think I'll try again this weekend when I have some more time. <3 breakage.

---

### Post by ronacc on 2008-05-08
I finaly finished d/l'ing the eee sources ( 42 hrs for 1.8 gig ! da** asus server) and got back to my intrepid install , thanks to the warning about libxfont1 I had the hardy .deb handy and got back to my destop after I updated . I cant dist-upgrade right now , I get an error mesage that it breaks the resolver . also after updating I can't navigate ubuntuforums below the section level ( can't load individual threads ) with either firefox or opera . The fun starts again !

@ plun  I was able to lock libxfont1 via synaptic no problem , try again .

---

### Post by cecilpierce on 2008-05-09
ronacc, how did you lock libxfont1 in synaptic ?
btw where is Narcoossee, im in Miami, thanks, Cecil

---

### Post by ronacc on 2008-05-09
once you have the version you want installed highlight it in synaptic and in the top menu package>lock version .
Narcoossee is a rural aera just south of Orlando . I escaped from Miami 30 yrs ago:)

---

### Post by ShodanjoDM on 2008-05-09
Not that I want to do dist-upgrade to Intrepid anytime soon, but I'm just curious will Intrepid use EXT4 filesystem?

---

### Post by aamukahvi on 2008-05-09
> **ShodanjoDM said:**
> Not that I want to do dist-upgrade to Intrepid anytime soon, but I'm just curious will Intrepid use EXT4 filesystem?
It might be included as an experimental option.

---

### Post by plun on 2008-05-09
> **ronacc said:**
> once you have the version you want installed highlight it in synaptic and in the top menu package>lock version .
Narcoossee is a rural aera just south of Orlando . I escaped from Miami 30 yrs ago:)

I can see you....:)   Strange lake behind your place.


[[img]http://pici.se/thumbs/t_ovgjZclbZ.gif[/img]](http://pici.se/262247)

Well, I have an uncle, aunt and cousin in Florida....:)


"Lock version" was impossible...  but no problems...

---

### Post by ccw on 2008-05-09
I wouldn't bother with Intrepid just yet...

I'm running it on my laptop:
There's the broken libxfont1 bug
There's a lot of broken dependencies from tool chain transitions (GCC 4.2 to 4.3, and Perl 5.8 to 5.10)
No upgrades of note yet/ nothing fun.

---

### Post by caryb on 2008-05-09
I guess, (as much as it's killing me) (this concept of being on a stable release has whiskers on it) I will have to wait till after the summit when hopefully they will open the Intrepid development post & start again. The only problem I see is we are reducing the testing time to 5 months instead of 6. 6 months is a real short time to test the qty of updates & new features.


Cary

---

### Post by plun on 2008-05-09
> **caryb said:**
> I guess, (as much as it's killing me) (this concept of being on a stable release has whiskers on it) 
Cary

Well... let it kill us....:)

15 minutes if you have ./home on an separate partition....:guitar:

The 6 month must be used better....I have been lurking some places and
it must be more then just upstream "collecting" work.

I cannot see principals and why a package is choosed.  Example the ongoing Multimedia "mess"


:)

---

### Post by ronacc on 2008-05-09
@ plun  "x" marks the spot

---

### Post by mabovo on 2008-05-09
> **plun said:**
> Yup, which also Eclipse pointed out earlier.
Package info
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libxfont1](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libxfont1)
Just to downgrade to Hardys version.


Got X back, thanks.

Now, I have "preliminar" Intrepid working but asking for upgrade packages cpp-4.2 ; gcc-4.2 ; gcc-4.2-base and libxfont1.

Gnome-applets incomplete loading with trash, mixer and fast_switch_user applets missing.

I liked very much a new tool called "friendly-recovery package".
Once in trouble without initializing system due to libxfont, could at least choose between some basic prompt options in order to recovery system without being a Geek :)

If a I remember all the options : 
resume boot
dpkg broken packages
fsck
recover X. 
Very nice. Could only address user to Ctrl+Alt+F1 to a new tty for basic commands like upgrading or downgrading packs.

I could notice that System Monitor indicates less than 50% of cpu usage against 100% in Hardy on my desktop Abit BE-6 with PIII-450Mhz.
Hardy can be used on Celeron 300Mhz Mendocino (Compaq Proliant 400) but System Monitor indicates cpu usage near to 100%.

---

### Post by ronacc on 2008-05-09
use a terminal and the cmd top  (table of processes ) instead of system monitor it's much easier on the resources .

---

### Post by cecilpierce on 2008-05-10
Is libxfont1 1:1.3.2-1 still bugged ?

---

### Post by disturbedite on 2008-05-11
> **cecilpierce said:**
> Is libxfont1 1:1.3.2-1 still bugged ?
i was wondering the same thing, but i'm too lazy to try to upgrade it & find out cuz i think it is the same exact version...

---

### Post by ccw on 2008-05-14
> **cecilpierce said:**
> Is libxfont1 1:1.3.2-1 still bugged ?

It got fixed last night.

---

### Post by MadMan2k on 2008-05-15
> **fujitsu said:**
> 
Unless you're a developer or a very experienced user, you should not consider using Intrepid until perhaps the last month of the development cycle.
but then there was that libc update during the hardy cycle... ;)

---

### Post by macroshaft on 2008-05-18
Ok guys, sorry I've been quiet for a while and thanks for all your replies. These errors you're talking about are exactly why I want to do this, to be able to fix these issues and eventually not have to scream 'HElP!' ever time!

I still havn't upgraded, the sources file has been updated and I've run aptitude update and dist-upgrade. During the upgrade it states:
> 
The following packages have unmet dependencies:
  libffi4: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.3-4ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
cpp-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2-base [4.2.3-2ubuntu7 (now)]

Score is 263

Accept this solution? [Y/n/q/?] 



and I select yes, it then offers to install 350 packages and shortly after quits with this 

> Preconfiguring packages ...
(Reading database ... 118056 files and directories currently installed.)
Preparing to replace debconf 1.5.20 (using .../debconf_1.5.21_all.deb) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: warning - old pre-removal script returned error exit status 134
dpkg - trying script from the new package instead ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: error processing /var/cache/apt/archives/debconf_1.5.21_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 134
Errors were encountered while processing:
 /var/cache/apt/archives/debconf_1.5.21_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
gareth@gareth-laptop:~$ 


I have followed the development of both gutsy and hardy but not from as early a stage as this, so does anyone have any suggestions for getting me up and running?

---

### Post by nivron on 2008-05-27
macroshaft,

I had the same exact problem.  I did the following to get past the xargs error:

```
sudo aptitude install findutils
```

After that, I was able to continue along just fine.  Now it's time to see what the next error is going to be. :)

> **macroshaft said:**
> Ok guys, sorry I've been quiet for a while and thanks for all your replies. These errors you're talking about are exactly why I want to do this, to be able to fix these issues and eventually not have to scream 'HElP!' ever time!

I still havn't upgraded, the sources file has been updated and I've run aptitude update and dist-upgrade. During the upgrade it states:


and I select yes, it then offers to install 350 packages and shortly after quits with this 



I have followed the development of both gutsy and hardy but not from as early a stage as this, so does anyone have any suggestions for getting me up and running?

---

### Post by tech0007 on 2008-05-30
> **nivron said:**
> macroshaft,

I had the same exact problem.  I did the following to get past the xargs error:

```
sudo aptitude install findutils
```

After that, I was able to continue along just fine.  Now it's time to see what the next error is going to be. :)

Thanks! This worked!

---

### Post by dlzerocool on 2008-05-30
Thanks a lot !

---

### Post by Gina on 2008-06-01
A big thank you from me too :):)

---

### Post by Gina on 2008-06-01
I'm now running Intrepid successfully on my old desktop.  So far just the updating and Firefox but I'll be testing other things shortly.

---

### Post by habtool on 2008-06-01
Thanks Nivron

---

### Post by grem91 on 2008-06-04
I just upgraded to Intrepid using Hardy. It did a ton of updates but there is a lot of updates that are greyed-out and I can't install. Will these eventually work or do I have to do something?

---

### Post by wgrant on 2008-06-04
> **grem91 said:**
> I just upgraded to Intrepid using Hardy. It did a ton of updates but there is a lot of updates that are greyed-out and I can't install. Will these eventually work or do I have to do something?

I'm afraid that asking such a question is a very good sign that you shouldn't be running Intrepid. You need to know how to deal with this sort of thing, or you'll get yourself into a lot of trouble.

---

### Post by grumpymole on 2008-06-05
@grem91

Short answer: yes.  

Long answer: Generally, the greyed out packages are waiting for newer versions of some dependencies that are still in the pipeline.  When these are available, they will be ungreyed out.

But, during the early phases of Intrepid, you should also expect packages to break and this might leave you without a GUI, or even able to log in.  

If you would like to do this, I would suggest a couple of things: (1) if you can, run intrepid in a virtual machine and take snapshots from time to time, or (2) set up your home partition on a separate partition.  That way if the applications turn on you, you can reinstall and keep your home directory data and settings.

If you don't use one of these (or something similar) methods, you might not be able to recover if something goes wrong.  It's part of the fun.

Also, you can proceed with caution.  Follow the forums and get a feel for when things are breaking before you accept each days updates.

And, I would recommend subscribing to the feed of package updates.  This will give you an idea of what it being updated and what the changes are.  But not what the impact might be.  For Intrepid: subscribe to [http://feeds.ubuntu-nl.org/IntrepidChanges](http://feeds.ubuntu-nl.org/IntrepidChanges)

Cheers

---

### Post by grem91 on 2008-06-05
Thanks for the information. I'm running it in Virtualbox, So theres no risk.

---

