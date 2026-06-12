---
title: "Ubuntu a piece of crap?"
date: 2008-11-03
forum: Testimonials &amp; Experiences
---

### Post by runslikeapenguin on 2008-11-03
so far in the past 3 days me and my room mate have downloaded and installed probably 5 versions of Ubuntu and Kubuntu in hopes that one would actually work.

the old version i had installed clean and quickly and ran well, not bloated at all but couldn't do jack, limited applications couldn't install anything, no internet, no sound and it loved randomly crashing. 

i then got it connected to the internet and downloaded the newest version of Ubuntu and it had a ton of errors in the download and install, most of which i had no idea what they were but apparently they were important because nothing worked. literally nothing, every i tried to do something, anything some kind of error message would come up and say i had to change something. and im sure that if i actually attempted to fix the problem the same error message would come up. 

so after that my friend found some Ubuntu disks that were old but newer than what i had. so i installed one and it worked ok i guess but once again when i upgraded to the newest version all kinds of **** went down and i dident even try with that. 

we also found some versions of kubuntu so i installed 7.04 64 bit and that worked great! seriously i was so happy that CD's played, it recognized all my hardware even my graphics card, the internet worked (mostly) and i was getting some sweet themes and back grounds and customizing things when i discovered that it would not load my email from MSN. it would just sit there and download cookies as separate pages over and over and over and over again. so i just figured it was some weird thing so i let it be. but right after that my tool bar disappeared. gone, i had it set up so it would hide and i was having no problems what so ever and then it was just gone. i couldn't bring it up no matter what i did. just gone. so after exhausting my resources on that one my friend announces that he just burned the newest version of kubuntu and had just installed it, so i abandoned the version that i had that was pretty much working minus the tool bar to upgrade to the newest version. 

that went well, no errors on the install and it looked pretty good and whats weird was the internet worked when it was live booting the CD but once installed no internet. and not just that, there it dident recognize half my hard ware, it wouldn't play CD's wouldn't recognize my flash drive and would crash if i tried to multitask with anything. half the time it wouldn't even crash, it would just stop. everything would just halt completely mouse would work menus and tool bars would work but everything else was dead. 

so basically im sick of Ubuntu. i can understand software like this having issues and it being hard to make everything work with all computers in all situations but it seems retarded that simple things like installing programs and getting plug ins for fire fox should be so insanely difficult. seriously the ubuntu distributors should have been able to get things like Flash and the like to work out of the box. and am i missing something but isnt Ubuntus claim to fame being a super user friendly Linux OS that's designed "for human beings"? so far i have gotten the complete opposite vibe from this software. i mean every time ive used a new version there are always different problems and this normally wouldent irritate me as much as this does but the problems are things like the internet not working, why would a newer version of the program change everything that worked before? it seems like the updates in versions are not updates to the software but complete changes, like your downloading something else entirely. it never seems like your getting somethings thats "new and improved" it just seems like your getting something "different and jacked up in a different way".

to sum this all up it feels like Ubuntu is out to get me like its reading my mind, and when i think to my self "this is looking pretty good, i think im going to like this" ubuntu says "**** YOU!" and does what it wants and crashes. 

are there any other distros that would offer a better product? one that's a lot less buggy?

---

### Post by tuxxy on 2008-11-03
sounds like you are trying to install it to unsupported hardware, maybe an older system? updates of OS can cause conflicts sometimes try fresh installs maybe

Flash is not included by default as its proprietary software, ubuntu-restrcited-extras package will install flash, java, mp3/dvd codecs etc

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wandalalakers on 2008-11-03
Try the 32bit version of kubuntu 8.04.
I think from now on I'm only going to install LTS releases.
You could also try LinuxMint.

---

### Post by ukripper on 2008-11-03
hmmmmm...NO!

---

### Post by forger on 2008-11-03
1) Use 32-bit Ubuntu for your closed-source application pleasures (e.g. flash)
Flash cannot be distributed directly, it must be downloaded from adobe, whine to adobe.com about that :)
And in 32-bit, it won't crash.

2) I don't understand, have you tried the latest 8.10? Hope is the last thing that should die. Never stop hoping :)
There are a lot of well-known distributions out there, such as opensuse or fedora, try your luck with those.

3) You never replied to the people that helped you in your final thread: [http://ubuntuforums.org/showthread.php?p=6092616](http://ubuntuforums.org/showthread.php?p=6092616)
How do you expect someone to help you if you don't reply?

4) In general, really wrong approach and an offensive title for a topic.

5) Have you tried [[SIZE="4"]reporting your bugs?[/SIZE]]("https://bugs.launchpad.net/ubuntu/+filebug")

These commands show you in detail what hardware is supported and what is not:
```

lspci -nn
sudo lshw -short

```
If you see a line with "Unknown", it means it's not supported (yet).

---

### Post by tuxxy on 2008-11-03
Flash 10 on Intrepid has yet to crash once for me 64-bit :)

---

### Post by ukripper on 2008-11-03
> **tuxxy said:**
> Flash 10 on Intrepid has yet to crash once for me 64-bit :)

+1 even on hardy 64-bit it never crashes for me!

---

### Post by armandh on 2008-11-03
I have had none of the OP's problems but then I know a Linux OS will not fix junk hardware. I do not recommend running on [too slow] anything less than a P-III with less than 512mb mem, and less than 866 mhz. it won't fix a flaky cd drive, bad mem or any other hardware problem. it won't fix un supported hardware or it self ie. bad burns or down loads or unsupported [restricted] code in an upgrade. it is just the easiest thing to blame.

so enjoy your installs and posts, though I doubt you will.

---

### Post by runslikeapenguin on 2008-11-03
i would have a hard time believing that its my hard ware. 

i have an Athlon 64bit 3200+ with 3 gigs of dual channel ram and a Nvidia 6600 GT. with Sony DVD/CD-RW drives.

older hardware yes, but by no means slow or crappy. my friend has been having the both the same and different problems that im having with a year old Alienware laptop. 

are there any common mods to get Ubuntu to not waddle around the computer like it weighs 400lbs? seriously every version gets slower and more bloated.

---

### Post by mikewhatever on 2008-11-03
This rant is awesome. :lolflag:

> **runslikeapenguin said:**
> 
to sum this all up it feels like Ubuntu is out to get me like its reading my mind, and when i think to my self "this is looking pretty good, i think im going to like this" ubuntu says "**** YOU!" and does what it wants and crashes.

Are you suggesting it's self conscious?:p

> are there any other distros that would offer a better product? one that's a lot less buggy?

No, they are all the same.):P

---

### Post by Lesouteneur on 2008-11-03
Something similar happened with me, relating to the kernel:

[http://ubuntuforums.org/showthread.php?t=968663](http://ubuntuforums.org/showthread.php?t=968663)
> **Lesouteneur said:**
> I repeatedly installed Ubuntu 8.10 and Kubuntu 8.10. Neither of them worked. I used different mirrors, torrents, I made a couple of CDs everytime the cd would boot the usplash would hang unless i repeatedly pressed a key through the process of loading. It was very annoying as I needed to do this on every boot. The kernel also apparently didn't take well to my video card, Nvidia 7000M. Kwin and compiz would sometimes have the close minimize and maximize buttons not completely displayed. 

For the time being I have reinstalled Windows Vista, as much as I hate too. I would really like to go back to Ubuntu but this has not been possible at this point. How can I revert the kernel to 2.6.26 and solve my woes?

-----------------
I would encourage you tu use Linux Mint 5 as everything works out of the box, flash, DVD's, codecs. [http://www.linuxmint.com/](http://www.linuxmint.com/)

The kernel also works perfectly fine for me.

---

### Post by BobSongs on 2008-11-03
> **Lesouteneur said:**
> <snip>I would encourage you to use Linux Mint 5 as everything works out of the box, flash, DVD's, codecs. [http://www.linuxmint.com/](http://www.linuxmint.com/)</snip>
Quick question: what repositories does "Linux Mint" use?

I believe it's based... perhaps loosely... on Ubuntu Linux. Does it use Ubuntu's repositories?

For me a distribution's value is based heavily on two things: the richness of the repositories and the friendliness of the forums.

Edit:
Ahh, found my own answer here: [http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

> * It is a Debian-based distribution and as such it is very solid and it comes with one of the greatest package managers.
* It is compatible with and uses Ubuntu repositories. This gives Linux Mint users access to a huge collection of packages and software.
* It comes with a lot of desktop improvements which make it easier for the user to do common things.

---

### Post by steveneddy on 2008-11-03
This link is the section of the forums with two stickies on top:

Compatible hardware

Incompatible hardware

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

This may solve a few of your issues.

You may want to look at some of the links in my sig. They may enlighten you a little.

Good luck.

---

### Post by kjb34 on 2008-11-03
You could try OpenSuse 11. I have a similar setup to yours and I have no problems running Ubuntu. What speed do burn your ISOs to cd? It seems that slower speeds work better for burn live cds.

---

### Post by stinger30au on 2008-11-03
> **runslikeapenguin said:**
> 
i then got it connected to the internet and downloaded the newest version of Ubuntu and it had a ton of errors in the download and install, most of which i had no idea what they were but apparently they were important because nothing worked.


well common sense would tell you if there is errors in the download then dont bother burning it to a disk and installing cos its got parts of the code missing.

i suggest you arm yourself with a torrent app and download a version from here instead

[http://linuxtracker.org/](http://linuxtracker.org/)

---

### Post by runslikeapenguin on 2008-11-04
i will give Linux Mint a try, and i dident download an ISO and then burn a jacked copy to a disk im not that incompetent, it had errors updating from the Ubuntu site.

---

### Post by Lesouteneur on 2008-11-04
nvm

---

### Post by cb951303 on 2008-11-04
obviously you don't know about "ubuntu-restricted-extras"
BTW, what's your motherboard model/brand?

EDIT: Also, considering you don't even know about 'sudo' it might not be all ubuntu's fault.

---

### Post by stalkingwolf on 2008-11-04
> i dident download an ISO and then burn a jacked copy
Ok there are 2 ways to read this.  

If you mean jacked as in screwed up,
that would be on you. I have never had a good download from a torrent
source.  Others have never had a problem.  IT IS on you to check your downloaded file before you burn it.

If you mean jacked as in hijacked or pirated your ignorance is showing.
Nothing to do with a basic install or for that matter advanced setup
has to be jacked.

Now a few rules that I have learned:

1. Use quality media to burn to.  By this I mean Media that you know works
well with your burner.  I have had certain brands of bedia not work well
with certain brands of ROMS.

2. Burn @ 4x or slower.  It just works better for some reason.

3. MAKE SURE that your CD/DVD rrom is clean.  This gave me uncountable headaches recently.  Until I plugged in my external CDRW.  Then all was fine.  Blow your drive out, run a cleaning disk then try again.

I also notice that you used "Old Just REdiscovered" CD's this to at times can be problematic.  Scratches, old PB&J etc on the disk can cause all
kinds of weird errors and mis cueing.

The term hardware covers a multitude of sins.  For instance a HDD that has had several install to it can give you headaches if you dont fdisk it.
There are "left overs" if it has not been properly "cleaned".

Recently I had occasion to rescue a hard drive That I bought which had been
" recertified" IE: returned to original Manufacturer Specs.  Amoung my rescued JPEG files are many pictures I HAVE NEVER SEEN BEFORE.
including a few porn ones.  Nice but not mine.  This might also be a lesson, before selling or giving away a computer, remove YOUR HDD and put in another.

---

### Post by semitone36 on 2008-11-04
> **mikewhatever said:**
> No, they are all the same.):P

Haha.... what?

Anyways if you feel that you are computer savvy I would give Arch a try.  Its way lightweight and you are basically in control of every aspect of it.  But if you just dont feel comfortable with that kind of control and if you still dont feel like linux works for you then perhaps it is just not meant to be.

There is no shame in choosing Windows over Linux if you dont feel it is for you.

---

### Post by dustman on 2008-11-04
Yeah well, I also had problems when installing my first Linux OS (an old Suse linux), but hey, there is internet and there are forums and there are people who willingly choose to spend a bit of their spare time on helping you. And guess what? Now I'm using Ubuntu on a daily basis - everything works!
Despair and quitting are a no-no when using linux, you have to keep trying and you'll get there, don't worry :).

Cheers,

Radu

---

### Post by slei3 on 2008-11-04
it may not work for you! but tell me one thing...

did you have to pay for it!!!

---

### Post by clanky on 2008-11-04
> **slei3 said:**
> it may not work for you! but tell me one thing...

did you have to pay for it!!!

Yeah, because that makes it OK, right?

As people have said, try 32 bit if you really want to use ubuntu, try another distro if you want to experiment to find what will work on your hardware.  My experience with Fedora has been pretty good although to be honest I didn't have any insurmountable problems with ubuntu either.  Have never tried mint, but I have heard a few people who have had good experiences with it from a stability point of view and others who found it too simplified from a performance point of view.  I guess it depends on what you want from your system.

---

### Post by kforum on 2008-11-04
you guys are forgetting one thing... as far as i can tell, all of the listed issues only happened because of 'improper' cd-burning. they are typical of people that havent done their md5sum check homework, and havent burned at low speeds, with reliable media...

cant believe no one made a comment like: did you burn this right?

this might seem like nothing, but in todays realities of these ever more compressed cds... yeah burning is a REALLY important part of the install process.

cheers.

---

### Post by Therion on 2008-11-04
> **kforum said:**
> ...yeah burning is a REALLY important part of the install process.
Very true; the importance can't be overstated.  Also, a LOT of my issues went away when I swapped out my 40 wire/40 pin CD/DVD drive cable for an 80 wire/40 pin cable.  The additional wires "clean up" the signal and after I installed it, I was suddenly finding previously "unbootable" LiveCD's and DVD's working perfectly.  

With ever more data being squeezed onto CD's and DVD's 80 wire cables are becoming a better and better idea.  Burning .iso files NO faster than 8x (and I find 4x much, much more reliable) is also absolutely critical.  As is making sure the file you have is clean.  Torrent's are your best bet as they are self-verifying downloads.  Burning a good, reliable, bootable .iso file is a process, not an event.

---

### Post by Zerocxis on 2008-11-04
@ the OP: don't give up and keep at it, currently I am working through some issues with my mother's old laptop she gave me after she got her new one... for some reason, I can't seem to get Ubuntu to play right (I might have to see if there isn't any unsupported hardware issues) but I haven't given up yet. One thing I also did was request a free CD of Ubuntu, that way I would have a decent copy of Ubuntu so I could be able to install Ubuntu with that if I couldn't get any of the burned copies that I made to work. Anyways, hope this helps --

Zerocxis

---

