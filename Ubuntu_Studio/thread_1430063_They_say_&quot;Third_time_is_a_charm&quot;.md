---
title: "They say &quot;Third time is a charm&quot;"
date: 2010-03-14
forum: Ubuntu Studio
---

### Post by wizarddrummer on 2010-03-14
Hi all,

Having suffered enough BSOD's from Windows XP, I decided to see if Linux had come of age yet for the things I like to do. Music, graphics, video, etc.

So I downloaded Ubuntu 9.10. I fought with that installation for about two weeks trying to get all of the dependencies worked out. tried to load programs like Rosengarden and had a horrible time with all of that with JACK, ALSA, LaTeX, livetex, missing files, can't install this or that; not to mention nvidia xorg.conf nightmares ... it was endless.

I said there has to be a better way; a better experience. 

I liked, no, that's incorrect, I LOVED Ubuntu's clean and freakishly well designed user desktop. Very well thought out. So in that respect, Linux has come of age. (btw, I had one of the first versions of Linux back in the early 90's)

Then someone suggested Mint. Mint comes completely configured they said. Only, no one tells you that the DVD Universal Edition, which is larger than the CD, does not come fully configured.

The first thing I tried; listening to an MP3 - FAILED! Firefox (as of this moment) still can not play a flash file and Rosengarden?  Fuggedaboutit, Hoooooooooooooo Weeeeeeeeeeeee. It had so many errors: JACK Server, timer resolution to low, Helper programs like kdialog not there. 

Look folks, I'm old, I'm tired and I am terminally ill (no joke - it kinda puts a new perspective on things cause my time is short.) I just want to have some fun, contribute to the community when i learn some more stuff.

My first experience with a computer was in the 60's, I remember the punched cards of the 70's, DASD packs spinning in washing machine sized units, tape machines the size of refrigerators; and how flabbergasted we were when we could have more than 16MB of memory. I spent many hours hacking out thousands and thousands of lines of C code while consuming  lots-o-puffs-o-cigarettes and (occasionally) some-puff-of-other-stuff along with lots-o-beer and loving every minute that I spent tweaking and fiddling with something in Unix System V on a 3B5 computer.

At this point, I don't really want to spend a good portion of the rest of my short life, in a terminal window, fiddling with a system just to get it to where it will load and run some programs. 

Heck, being forgetful because of lack of 02 to the brain, I kept getting frustrated as to why I could not copy a file from /etc/X11 to /usr/rjw/. Oh, it's /home/rjw ...

So, now I am considering yet another Linux distro Ubuntu Studio. I'm downloading the .iso as I am writing this.

Will this one run "out of the box" so to speak?

According to the docs, it says this one has Rosegarden installed. Will this distro start all of the servers in the background so I can simply run the program without a lot of drama?

Thanks,


Thanks,

---

### Post by sgx on 2010-03-15
Hi, to be honest the 'do it all' apps like Rosegarden, Muse, and LMMS
are in deep waters, for free, or nearly free developers, mastering
digital audio workstations. I would create a separate /home partition, install the Ubuntu Studio, or 64 Studio, if your hardware doesn't click, then add wine and wineasio to your ubuntu using synaptic, the software installer. You may need to look in the recent forum posts, someone has a source for wineasio in a PPA, a repository of software. Using synaptic
will be crucial to your happiness, pressing its 'Reload' button when online gathers apps from repositories that are default, ore ones you select (see the relevant menu in synaptic)
When you add a repository, press Reload, to get it recognized, when the list is downloaded and displayed, you can choose what you need, and 99.57 percent of the time, all your choices will install, along with anything they needed, and function.

After installing wine, and wineasio, the user (not root) must type the command

regsvr32 wineasio.dll

From there, I would download and install Reaper, use youtube videos and their excellent manual, to get rolling if needed You will be able to complete multi-track songs using audio and vst plugins, with high quality.
Plugins not using dongles, or complex copy protection will almost always work. (I found one that didn't, but it is buggy in windows to)

Wineasio will appear in the Reaper dialogue for choosing your asio device.
The windows version of EnergyXT2, and Cantabile 1.2 also are good second choices.

The linux audio apps to focus on are Hydrogen  a excellent drum/sample machine, rakarrack, an excellent multi-fx app, zynaddsubfx, one of the
best synthesizers anywhere, timemachine, a simple high quality recorder,
and qjackctl, the gui patchbay for jackd, the efficient audio server.

qjackctl is crucial to your success, so google it, how-to pages and tips are here, at the 64 Studio website, and on the youtube.

qjackctl allows you to route your apps sound wherever it must go, you can
play plugins in Reaper, while the Hydro' drum machine pounds out your opus, with separate rakarracks FXting each, with zynaddsubfx harmonizing its ethereal wonders, and timemachine recording the lot.  

(the separate /home partition will hold your data and most configurations
intact if you need to reinstall, just choose not to format it in the installer procedure, saving tons of time.)
Cheers

---

### Post by AutoStatic on 2010-03-15
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by rlameiro on 2010-03-15
hi. 
UbuntuStudio will not run everything alone, but will have most of the things pre-configured. 
You will need sometimes to start jack before other software that needs jack. It is not bad, its just how it works. some software will fire up jackd automagically, like ardour. 
About Rosegarde, I really don't know how is it working, i dont use sequencers, but AFAIK Qtractor is a very nice piece of software that will do midi and audio. It will only runs on jack.
Another thing that you would need to have in mind is that Gnu/linux is a secure system, so it will need especial permission to use some resources. for example firewire will need special access, or running realtime software will need your user to be added to the security.conf file. Although this could seam like a lot of trouble just for have a workstation with pro audio software working, it makes your system secure and stable.
Also you can come in here or at the #ubuntustudio channel @freenode and ask for help. people will gladly help you on your journey.
check this help site to see something to start of.
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

If you have some problems post here the problem and the hardware you are using, since a lot of things can be solved just looking ad hardware compatibilities.

hope this help you out.

---

### Post by wizarddrummer on 2010-03-15
> **sgx said:**
> Hi, to be honest the 'do it all' apps like Rosegarden, Muse, and LMMS
are in deep waters, for free, or nearly free developers, mastering
digital audio workstations. I would create a separate /home partition, install the Ubuntu Studio, or 64 Studio, if your hardware doesn't click, then add wine and wineasio to your ubuntu using synaptic, the software installer. You may need to look in the recent forum posts, someone has a source for wineasio in a PPA, a repository of software. Using synaptic
will be crucial to your happiness, pressing its 'Reload' button when online gathers apps from repositories that are default, ore ones you select (see the relevant menu in synaptic)
When you add a repository, press Reload, to get it recognized, when the list is downloaded and displayed, you can choose what you need, and 99.57 percent of the time, all your choices will install, along with anything they needed, and function.

After installing wine, and wineasio, the user (not root) must type the command

regsvr32 wineasio.dll

From there, I would download and install Reaper, use youtube videos and their excellent manual, to get rolling if needed You will be able to complete multi-track songs using audio and vst plugins, with high quality.
Plugins not using dongles, or complex copy protection will almost always work. (I found one that didn't, but it is buggy in windows to)

Wineasio will appear in the Reaper dialogue for choosing your asio device.
The windows version of EnergyXT2, and Cantabile 1.2 also are good second choices.

The linux audio apps to focus on are Hydrogen  a excellent drum/sample machine, rakarrack, an excellent multi-fx app, zynaddsubfx, one of the
best synthesizers anywhere, timemachine, a simple high quality recorder,
and qjackctl, the gui patchbay for jackd, the efficient audio server.

qjackctl is crucial to your success, so google it, how-to pages and tips are here, at the 64 Studio website, and on the youtube.

qjackctl allows you to route your apps sound wherever it must go, you can
play plugins in Reaper, while the Hydro' drum machine pounds out your opus, with separate rakarracks FXting each, with zynaddsubfx harmonizing its ethereal wonders, and timemachine recording the lot.  

(the separate /home partition will hold your data and most configurations
intact if you need to reinstall, just choose not to format it in the installer procedure, saving tons of time.)
Cheers

I am unfamiliar with some of your terminology. Wine? Yeah I like that alot ;) ... Reaper I've used in the Windows Environment. Great application; company also has an app that allows for sync'd network playing; never got the chance to do that before i moved and sold most of my equipment.

So based on what I think I understand, wine is something that a person uses to run windows based programs.

My currently defunct 780i SLI dual 8800 768MB GTX's, 4GB Memroy and 2 500GB SATA drives gaming machine could probably handle the overhead. This interim piece of crap of a computer can just about keep up with itself.

I'm not in a production environment, I just want to, initially, get some software to run so I can have a little "fun"

Thanks for all of the replies.

Edit:1 What is a PPA?

---

### Post by rlameiro on 2010-03-15
PPA is a Personal Package archives from Launchapad.net website.
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

in an Ubuntu system you can add repositories of software (places where you download packages from)and install them. You can add also ppa that are repositories from personal users or projects outside of ubuntu. You can add a repository going to system -> admin -> synaptics and then go to the config menu and select repositories. after that choose the second tab(something about extra software osr something) and click add then you copy the ppa repository link in the webpage, or a DEB repository link.
example of a ppa link: ppa:ubuntustudio-dev/ppa
example of a DEB repo link:  deb [http://apt.puredata.info/releases](http://apt.puredata.info/releases) jaunty main (this is for the jaunty release)

Hope this helps

---

