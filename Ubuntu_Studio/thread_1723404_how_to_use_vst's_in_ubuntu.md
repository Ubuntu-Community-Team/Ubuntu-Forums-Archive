---
title: "how to use vst's in ubuntu"
date: 2011-04-07
forum: Ubuntu Studio
---

### Post by poodoopealeoaph on 2011-04-07
I have a ton of vsts and vsti's that I use in my recording process and believe me I've tried out every single thing that there is to offer with ubuntu's repo's and there is nothing that can compare. So, I'm wondering if anyone can help me figure out how to use superior drummer 2.0 and amplitube 3.0 in ubuntu. I can basically deal without the rest because of what is offered in the repo's but those two I absolutely need. If you want to hear what I can do with them you can check out [http://www.soundcloud.com/adamwebster](http://www.soundcloud.com/adamwebster) or you can check out [http://www.myspace.com/iamwebby](http://www.myspace.com/iamwebby)       by the way, good comments on the music is greatly appreciated.

---

### Post by sgx on 2011-04-07
I have used EZD, and several Amplitube variants, you'll have to
install wine, and wineasio in a working jackd Ubuntu, and use
Reaper as the vst host. The reaper forums have linux users and topics,
and KVR kas a long thread in the Computer Setup forum with all the details. Learn to use the synaptic package manager, and install wine and wineasio. Once wine is installed, open a terminal and run winecfg  
and choose alsa in the sound panel. You will now have a .wine folder, your new windows environment. 

Run your installers from a terminal

wine Install*AmpliTube*Jimi*Hendrix.exe

wine msiexec -i name-of-installer.exe

Note the * to fill in spaces, when running commands in wine.


Standalone versions can start with

wine Amplitube3.exe

For plugins, create the Steinberg/VstPlugins folders in the 

.wine/drive_c/Program Files folder

I Install reaper in /home/user instead of Program Files, to keep
things simple. I would suggest turning off as much eyecandy as
possible, gradients, shadows, anims, since this is all rolling
release beta level integration. You'll find most plugins work, if they
are not using pace/ilok/dongle protections. A few synthmaker-synth-edit made plugins fail to scan, and Reaper requires scanning vsts, so if it gets stuck on one, quit reaper, and start again, it is smart enough to continue correctly. Native Instruments, U-he, Wusik,
AlgoMusic, Camel Audio, Ugo, and many others are known to work.

wine reaper/reaper.exe  starts it, when installed in /home/username

Alsa and jackd are team-mates, qjackctl is the gui for connecting your
detected hardware with software, open qjackctl, start it, start reaper, set its preferences, (reaper auto-connects to jackd, but you must choose wineasio in reaper vst device preferences) 

youtube search for ardour and qjackctl, for quick visuals, and the qjackctl wiki has links with screengrabs and tips.

Musicians new to linux have to invest about 20 hours into figuring it all out, but lots of audio freedom awaits. Your entire vst setup is
just a rompler, waiting to be recorded-enhanced by linux apps, if desired. This all assumes your audio and computer hardware are supported. Google your current gear with alsa, linux, problem  to see any common issues.

Take your time, ask questions, and provide details, and you'll have a fine ride! :)

Cheers

---

### Post by sgx on 2011-04-07
(And just between the two of us, it is best to avoid putting down the linux audio apps, in a linux audio app forum, because some very smart recording musicians use them with great results, and will think you are just a noobie, who lost his windows 7 dvd) :wink:

---

### Post by mango42 on 2011-04-07
+1, **sgx** and a nice concise 'tutorial' to go with it ;-)

I haven't paid much attention to using VSTs in Linux yet as I've been blown away by the CALF offerings for most of the stuff I'm interested in.

However, isn't there a way through to VSTi's using DSSI, or is that only for Linux compiled plugins? I never got further than seeing what looked to be a conflict between DSSI & Wine...

@ **poodoo** - always great to see people using soundcloud but on "The local scene" (which sounds well scary) I couldn't distinguish which VSTs you used - I guess we aren't meant to? ;-)

---

### Post by sgx on 2011-04-07
Hi, there are dssi-vst, and fst, which can command some vsts if
wine and wineasio and jackd are all going, the vsts show in
qjackctl for connection. I always recommend reaper, because it works
far more than other options, and I hate leading people on into
folly and regret. If you're a high-gain guitar picker, find the
LePou Poulin ampsims, and LeCab cab-sim,
Poulin Hybrit Fullstack is a favorite, he has quite a few getting
rave reviews.

Route your guitar to the reaper ampsim, ampsim to the cab-sim, then send that out using qjackctl, disconnecting reaper output from playback 1 and 2, and reconnect it to calf, rakarrack, guitarix etc etc
Cheers

---

### Post by poodoopealeoaph on 2011-04-08
> **mango42 said:**
> +1, **sgx** and a nice concise 'tutorial' to go with it ;-)

I haven't paid much attention to using VSTs in Linux yet as I've been blown away by the CALF offerings for most of the stuff I'm interested in.

However, isn't there a way through to VSTi's using DSSI, or is that only for Linux compiled plugins? I never got further than seeing what looked to be a conflict between DSSI & Wine...

@ **poodoo** - always great to see people using soundcloud but on "The local scene" (which sounds well scary) I couldn't distinguish which VSTs you used - I guess we aren't meant to? ;-)

yeah I really like using the amplitube metal, ampeg svx, and superior drummer w/ DFH vst's because they are so natural sounding. For the most part no one can tell that I've replaced/sequenced drums and that I'm not using any real guitar amps.

---

### Post by sgx on 2011-04-08
A big selling point and strength of Amplitube, is for cover bands
to access close approximations of carefully modeled vintage gear
used in the hit songs they must accurately cover, to compete in their
market. With a gui for each model, guitarists (and keyboard/percussionists) don't need much tech savvy to crank out some fine sounds. Since I don't do any covers, I love rakarrack displaying
a plethora of raw parameters, and the ability to receive windows fx
as input. Guitar pickers are so spoilt these days :)

---

### Post by poodoopealeoaph on 2011-04-09
See the only thing about rakarrak is that I've tried it and I really do like just about every clean effect on it but I can't seem to find a usable distortion. I toyed with it for a few hours and all of the distortion sounds were complete junk. It just seemed like clean was good, crunch was somewhat okay but high gain distortion was completely out of the question. There is a possibility that I just wasn't tweaking the right parameters though so if anyone could get a decent high gain sound out of it, take a quick take of you playing through it and put it up and send me the link on this thread so I can hear it.

---

### Post by poodoopealeoaph on 2011-04-09
> **sgx said:**
> I have used EZD, and several Amplitube variants, you'll have to
install wine, and wineasio in a working jackd Ubuntu, and use
Reaper as the vst host. 
Cheers

I've read all over the place that I have to install reaper and wineasio but I can't find either of them. How exactly do I get both of these?

---

### Post by sgx on 2011-04-09
> **poodoopealeoaph said:**
> I've read all over the place that I have to install reaper and wineasio but I can't find either of them. How exactly do I get both of these?
Reaper is at [http://forum.cockos.com/](http://forum.cockos.com/) download button atop the page.

If wine and wineasio are not listed in synaptic, you may want to add the Faulk PPA to synaptic, the wine files and PPA instructions are here:

[https://launchpad.net/~kxstudio-team/+archive/ppa/+index?start=300&batch=75](https://launchpad.net/~kxstudio-team/+archive/ppa/+index?start=300&batch=75)

manual install looks like this

sudo dpkg -i wineasio_0.7.4+pljones2-3~jaunty1_i386.deb

dpkg is short for debian package, files ending with .deb

When software is installed from synaptic repositories, extra dependencies are fetched and installed. If dpkg sees a needed dependency, it will fail, and mention what is needed for you to find in a web search,
most .deb can be found here

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

Reaper has a ton of videos on youtube, to cover basic and detailed recording

[http://www.google.com/search?q=youtube+reaper+recording&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=](http://www.google.com/search?q=youtube+reaper+recording&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=)

Cheers

---

### Post by mango42 on 2011-04-09
I don't know what it is about Reaper and me but I can never seem to get beyond a wineasio error. Whereas FL9 is no problem, thanks largely to **falkTX**'s excellent tutorial.

However, both those lovely programs inevitably need WINE; **Qtractor** & **Ardour** don't and given sufficient 'dexterity of purpose', between them (plus LMMS for tryouts) can do just about everything the windows stuff offers; with the added advantage of far more flexibility...

...**IMO** but what do I know as I never even 'graduated' to windows7... ;-)

As for distortion, just wind up yer analog side of things until yer ears bleed :guitar:

---

### Post by Pablo_F on 2011-04-09
Hi, 

If you use Reaper as a host you need wineasio. However, if you use dssi-vst (command line *vsthost*), or fst, or festige (a nice graphical VST loader), you don't need wineasio.

For guitar players there is also gx_head, a GPL'd linux native virtual amp based on guitarix. I strongly recommend it. Distortion is more natural than what you can get from a rakarrack effect. Check:

[http://sourceforge.net/apps/wordpress/guitarix/](http://sourceforge.net/apps/wordpress/guitarix/)

[http://sourceforge.net/projects/guitarix/](http://sourceforge.net/projects/guitarix/)

You will have to compile from the sources (unless there is PPA compatible with your ubuntu version that has packaged it, I don't know) but it is not a big deal and we can help you.

Cheers, Pablo

---

### Post by sgx on 2011-04-09
> **mango42 said:**
> I don't know what it is about Reaper and me but I can never seem to get beyond a wineasio error. Whereas FL9 is no problem, thanks largely to **falkTX**'s excellent tutorial.

However, both those lovely programs inevitably need WINE; **Qtractor** & **Ardour** don't and given sufficient 'dexterity of purpose', between them (plus LMMS for tryouts) can do just about everything the windows stuff offers; with the added advantage of far more flexibility...

...**IMO** but what do I know as I never even 'graduated' to windows7... ;-)

As for distortion, just wind up yer analog side of things until yer ears bleed :guitar:You don't graduate to windows 7, you get
tortured by Villenium, Xpee, and Blista, until you dive on a W7 boxed set display out of sheer desparation :rolleyes: 

you might like the Hy-brit Fullstack, 2 cabs with panable separate IRs

[http://lepouplugins.blogspot.com/search?updated-min=2009-01-01T00%3A00%3A00-08%3A00&updated-max=2010-01-01T00%3A00%3A00-08%3A00&max-results=7](http://lepouplugins.blogspot.com/search?updated-min=2009-01-01T00%3A00%3A00-08%3A00&updated-max=2010-01-01T00%3A00%3A00-08%3A00&max-results=7)

Should work as vst fx in fls

Reaper also can be used in wdm or directsound modes, from its audio device preferences. Don't select jackd in winecfg when using reaper, choose alsa, and wine and wineasio should
probably both be installed by synaptic, or both compiled, but not a blend. regsvr32 wineasio.dll  command must be run after installing wineasio. Wineasio must be selected in the Device preferences in Reaper, and jackd must be active...all apps run by the same user...

yada yada...no wonder analog is alive and well :)

---

### Post by rusk911 on 2011-04-09
best way to use VST-s is FeSTige and kxstudio ladish enviroinment.. I use vst guitar amps with Ardour, but vst-s runs separately from Ardour. It helps to avoid Ardour from crashes by wine stuff. But plugins are connected to tracks via simple send-return and restores by Ladish after studio reload!

---

### Post by poodoopealeoaph on 2011-04-09
alright so, first of all, how do you get festige? or was it vestige? because i've used vestige and I wasn't sure if that was just some sort of typo. Also, how do you compile your own stuff from the binaries?

---

### Post by sgx on 2011-04-09
Hi, synaptic is the package manager (software installer-uninstaller)
often used in linux. It is like a gui frontend to linux commands
used for such things

sudo apt-get install festige
sudo dpkg -i festigexxx.deb

Synaptic, and the apt-get install  commands hunt down dependencies needed by what you choose to install, like a gui, shared library, or codec.

Linux software is often stored in repositories, and PPA mini repositories, some are default in synaptic, and more can be added.

There is a textfile in  /etc/apt  called sources.list which you can edit. It lists the repositories synaptic scans when you press its 'reload' button. You must be online when you press reload, for updates
and new files to be found and listed. Each entry follows a format, so close examination will reveal where a space is inserted in a new entry.

When you find a file to install in synaptic, select it, and click the
'apply' button, and all needed files will be installed.

The downloaded package files are kept in /var/cache/apt/archives but
in most distros, the default is to not store them, which I always change in synaptic preferences, so over the years, I have built a handy collection, since new versions sometimes are not what you need.

Get online and type sudo apt-get phasex in a terminal, this should install a nice synthesizer, without needing lots of extras, and it has the special capability of using your line-in as a sound source,
great for spicing up a guitar or percussion set. 

If for some reason, its not a default in the repository,

it's here: [http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)
click phasex from the list, then scroll down on its page to the
architectures, and choose the version you need, i386, amd64 being
the common choices. (Dependencies have links, should any be needed)

A page of download mirrors will open, so pick one. The downloaded file can be installed like this

dpkg -i phasex_0.12.0+m1-3_i386.deb if that is the version you download. 

There are instructions at the PPA sites from Falk and Autostatic
with specifics on adding them to your synaptic system. If there is a typo, it won't wreck the train, you'll just have to go back and fix it
before the apps they contain are listed in a synaptic reload.

[https://edge.launchpad.net/~falk-t-j/+archive/festige](https://edge.launchpad.net/~falk-t-j/+archive/festige)

Take your time, by May 19th, you'll have a gray beard, but more tools for your music! ;)

---

### Post by sgx on 2011-04-09
> **poodoopealeoaph said:**
> See the only thing about rakarrak is that I've tried it and I really do like just about every clean effect on it but I can't seem to find a usable distortion. I toyed with it for a few hours and all of the distortion sounds were complete junk. It just seemed like clean was good, crunch was somewhat okay but high gain distortion was completely out of the question. There is a possibility that I just wasn't tweaking the right parameters though so if anyone could get a decent high gain sound out of it, take a quick take of you playing through it and put it up and send me the link on this thread so I can hear it.

I'm far from a high-gain expert, but with a clean tone, I would use
the various EQ options and a dab of chorus, to boost certain frequencies, and perhaps some very very short delay and phaser, and
then start building some gain, and adding distortion fx.

Guitarix is another option, which supports IRs and has a gui more focused on guitar related fx and ampsims. libzita-convolver, or other
zita related apps may be requested dependencies.

info [http://guitarix.sourceforge.net/](http://guitarix.sourceforge.net/)

[http://www.linuxjournal.com/content/introducing-guitarix](http://www.linuxjournal.com/content/introducing-guitarix)

Cheers

---

### Post by poodoopealeoaph on 2011-04-10
okay sgx. I'm not a complete retard so you don't have to explain to me what synaptic is. Also, the reason why I asked about festige is because I already searched it in synaptic, software center, and terminal. So, unless there is a repo that needs to be added, I'm lost and it isn't because i'm an idiot.

---

### Post by Pablo_F on 2011-04-10
> alright so, first of all, how do you get festige?

The easy way:

Software Center -> Edit -> Software sources -> Other software tab.
Add this line: ppa:falk-t-j/festige
The new repo line will appear. Make sure it is enabled (ticked) and close the window. The list of packages is updated automatically, wait a bit.
Search for festige and install it.

>  or was it vestige? because i've used vestige and I wasn't sure if that was just some sort of typo.
Vestige are the free (as in freedom), reverse engineered, VST SDK headers, which are free as in beer but not free as in freedom. dss-vst, fst, festige, LMMS... use the vestige headers. In the past without vestige, to play VST effects/instruments we had to go to Steinbergs site, tell them "we are plugin developers and please we need your SDK" and compile dssi-vst and/or fst, because of a Steinberg license restriction. Thanks to vestige, the linux native alternatives can be packaged and distributed and so, easily installed.

>  Also, how do you compile your own stuff from the binaries? 

You don't compile from binaries, you compile from the source code. The process depends on the source code. There is normally a README file and/or a INSTALL file which give the clues. You need some basic tools and the development packages of the dependencies.
These can be installed from the repos (synaptic or apt-get install). 

Especifically, you need the package called "build-essential" and some other libfoo-dev packages, where foo depends on the program you want to compile. There is a trick to get the develpment packages to compile lots of linux audio programs, not only ardour (and you don't need to compile ardour anyway) with this command:

sudo apt-get build-dep ardour

Cheers! Pablo

---

### Post by poodoopealeoaph on 2011-04-10
thanks pablo, your advice is always dead on! your the best!

---

### Post by Pablo_F on 2011-04-10
Oh please, sgx is very helpful in this board. He is not calling you names, he was just trying to help you because he likes to help and do so in his _free time_, like many others here. No one thinks that you are an idiot or retard. We all are learning all the time. Don't take it personally when someone explains to you things that you already know. Be considerate. Please.

---

### Post by sgx on 2011-04-10
> **poodoopealeoaph said:**
> okay sgx. I'm not a complete retard so you don't have to explain to me what synaptic is. Also, the reason why I asked about festige is because I already searched it in synaptic, software center, and terminal. So, unless there is a repo that needs to be added, I'm lost and it isn't because i'm an idiot.
Hi, I try to write replies that will also help lurkers, or google searchers in the future, as I am constantly helped by others who 'rambled on', for the good of all. I do realize that opens the door to some misunderstandings. Anyone producing music with Amplitube and linux, is very intelligent, by any standard!
This said by one who lost 2 years off the lifespan after typing this:

bash-4.1$ cd /user/bin
bash: cd: /user/bin: No such file or directory ](*,)

Cheers

---

### Post by sgx on 2011-04-10
> **Pablo_F said:**
> Oh please, sgx is very helpful in this board. He is not calling you names, he was just trying to help you because he likes to help and do so in his _free time_, like many others here. No one thinks that you are an idiot or retard. We all are learning all the time. Don't take it personally when someone explains to you things that you already know. Be considerate. Please.
Thanks for the kind words! So many good people in the linux, and vst
communities, making complex things easier, and good things even better.
Cheers :D

(I need a constant refresher course, if I don't share the little I know, I quickly forget it,
and become a Monday morning newbie all over again :wink: )

---

