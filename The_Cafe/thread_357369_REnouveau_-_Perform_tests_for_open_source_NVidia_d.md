---
title: "REnouveau - Perform tests for open source NVidia drivers development"
date: 2007-02-09
forum: The Cafe
---

### Post by manmower on 2007-02-09
[REnouveau](http://nouveau.freedesktop.org/wiki/REnouveau) is a tool by which you can help the developers of the free and open source [nouveau driver for nvidia cards](http://nouveau.freedesktop.org/wiki/). Mikos brought this up over at the [Arch Linux forum](http://bbs.archlinux.org/viewtopic.php?pid=228346). I encourage everyone with an nvidia GPU to help out!

[http://users.tkk.fi/~jpakkane/ren/](http://users.tkk.fi/~jpakkane/ren/) has a list of which cards data is still needed from.

[b][jeffc313](http://ubuntuforums.org/showpost.php?p=2134363&postcount=13) has kindly provided a tarball ([http://jeff.crowell.googlepages.com/renoveau.tar.gz](http://jeff.crowell.googlepages.com/renoveau.tar.gz)), eliminating the need to compile it yourself. Thanks!

If the tarball is somehow causing you problems try the instructions in [po0f's post](http://ubuntuforums.org/showpost.php?p=2131578&postcount=5) on how to compile it yourself.[/b]

> REnouveau stands for Reverse Engineer nouveau. KoalaBR maintains some (incomplete) documentation. If interest is high enough, it will be folded into CVS.

It is an application that runs small opengl tests and watches the changes in the video card registers. Usage instructions are on the README file. It takes some time to get into, but once you know it, it is simple to read.

When you run REnouveau, make sure screensaver does not activate, do not wave your mouse over the REnouveau decorationless window and most importantly make sure the whole window is visible all the time.

This is used to do clean room reverse engineering (this is not in violation with nvidia driver license). We do not disassemble binaries.

Steps to follow:

> 1.) Build and/or install renouveau
2.) Make some directory for it, e.g.: mkdir ~/renouveau
3.) Go to this directory: cd ~/renouveau
4.) Run 'renouveau' command
5.) Wait for renouveau OpenGL tests to be finished. Make sure that screensaver is disabled while running tests. Also don't cover test window with mouse cursor (or other windows) and don't move with test window
6.) Create tar.bz2 archive from all output files saved by renouveau in ~/renouveau directory
7.) Send archive to this address: [email]renouveau.dumps@gmail.com[/email]

---

### Post by prizrak on 2007-02-09
Link us to a .deb or at least an .rpm please. I got an nVidia and would be more than willing to help.

---

### Post by Choad on 2007-02-09
yeah, or even a few tips on how to compile from cvs. i cant get it to compile :S

---

### Post by prizrak on 2007-02-09
> **Choad said:**
> yeah, or even a few tips on how to compile from cvs. i cant get it to compile :S

That's the problem with Linux for Human Beings everything is so easy we don't even know how to compile from CVS. I done it before but I'm pretty sure it was magic cuz it all worked without a problem. One tip I got for you is make sure you got build-essential(s?) package installed.

---

### Post by po0f on 2007-02-09
```
[FONT="Courier New"]$ sudo apt-get install build-essential cvs mesa-common-dev libsdl1.2-dev libxvmc-dev nvidia-glx-dev
$ mkdir ~/src
$ cd ~/src
$ cvs -z3 -d:pserver:anonymous@nouveau.cvs.sourceforge.net:/cvsroot/nouveau co -P renouveau
$ cd renouveau
$ make
$ ./renouveau
[/FONT]
```

Worked for me, I can't be bothered with letting it run for now.  I'll let it run later when I'm not using this box.

---

### Post by manmower on 2007-02-10
po0f's instructions should get you there. Also, maybe a mod could edit the topic title so as to attract more attention? I have a feeling this is being overlooked. Compiling and running this should take you about 15 minutes so it really isn't that time consuming.

---

### Post by bapoumba on 2007-02-10
Is title ok with you ?

---

### Post by manmower on 2007-02-10
Excellent, thanks!

---

### Post by Majlo on 2007-02-10
Done. Output files have been sent.

---

### Post by pay on 2007-02-10
How well does this driver perform compared to proprietary nVidia driver and open source radeon driver?

---

### Post by OffHand on 2007-02-10
> **pay said:**
> How well does this driver perform compared to proprietary nVidia driver and open source radeon driver?

Google is your friend:

[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

---

### Post by pay on 2007-02-10
[QUOTE=http://nouveau.freedesktop.org/wiki/]Currently, nothing works. If you're not a developer, you're not interested in this at all.[/QUOTE]Guess that means no, it's not up to scratch with the open radeon driver yet... It will be an interesting project though. Maybe by the time I'm ready for a new video card it will be mature enough for me to get a nVidia card.

---

### Post by %hMa@?b&lt;C on 2007-02-10
ran the tool, submitted my data.
edit: if anyone wants a package i am making one in a .tar.gz right now
update: [http://jeff.crowell.googlepages.com/renoveau.tar.gz](http://jeff.crowell.googlepages.com/renoveau.tar.gz) here it is
please link it in the first post for people to download, so they wont have to compile.

---

### Post by %hMa@?b&lt;C on 2007-02-10
> **jeffc313 said:**
> ran the tool, submitted my data.
edit: if anyone wants a package i am making one in a .tar.gz right now
update: [http://jeff.crowell.googlepages.com/renoveau.tar.gz](http://jeff.crowell.googlepages.com/renoveau.tar.gz) here it is
please link it in the first post for people to download, so they wont have to compile.
*bump* would a mod please put my link in the first post, it seems that having to compile is a turn off for some people.

---

### Post by manmower on 2007-02-10
I added the link to my initial post, thanks for sharing jeffc313!

---

### Post by Sammi on 2007-02-10
Ok so I did all the commands that po0f recommended and renoveau downloaded, compiled and ran. But now what? Where do I submit the data and what data do I submit :confused:

---

### Post by %hMa@?b&lt;C on 2007-02-10
6.) Create tar.bz2 archive from all output files saved by renouveau in ~/renouveau directory
7.) Send archive to this address: [email]renouveau.dumps@gmail.com[/email]

---

### Post by Sammi on 2007-02-10
And I'm guessing that the output files are all the file that start with card_10de-00c1?

Do those files include info on which card I have or should I write that myself in the e-mail?

---

### Post by manmower on 2007-02-10
Yup all the .txt's starting with card*, just zip 'em up in a tarball. I put my card model in the subject line of my e-mail but I'm not sure it's even necessary. Better safe than sorry though. :)

---

### Post by Sammi on 2007-02-10
Ok thnx for the info :D

---

### Post by %hMa@?b&lt;C on 2007-02-11
a mod should sticky this, for at least a month or so, these people need all the info they can get!

---

### Post by bapoumba on 2007-02-11
Okay, it's sticky. Please remind me to check on it next month ;)
OP _has_ to keep us informed now :-þ

---

### Post by mushroom on 2007-02-11
sent

---

### Post by Spr0k3t on 2007-02-12
Going to do my card when I get home.  It's always good to have open source drivers for hardware.

---

### Post by brazzmonkey on 2007-02-12
i'm getting segmentation fault here...

---

### Post by Carrots171 on 2007-02-14
Can't get it to work on Dapper. When I try to run renouveau, I get this error message: 
```
./renouveau: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./renouveau)

```
Any pointers on how I can get this to work?

---

### Post by manmower on 2007-02-14
> **Carrots171 said:**
> Can't get it to work on Dapper. When I try to run renouveau, I get this error message: 
```
./renouveau: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./renouveau)

```
Any pointers on how I can get this to work?

Did you use the tarball from the first post? Maybe Dapper has an older glibc version, would you try compiling from source and see what happens? An other way would be to upgrade glibc to a newer version, but I don't know if there's one in the Dapper repos though.

---

### Post by PatrickMay16 on 2007-02-14
> **Carrots171 said:**
> Can't get it to work on Dapper. When I try to run renouveau, I get this error message: 
```
./renouveau: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./renouveau)

```
Any pointers on how I can get this to work?

I'm having the same problem. I'm not good with compiling stuff, so I can't do it.

But I have an nvidia card and would like to help out with this. If someone compiles it for dapper, that'd be great.

---

### Post by prizrak on 2007-02-14
Done and sent

---

### Post by disabled_20220313 on 2007-02-14
Hi,

I tried running it and got 

```

detect_devices: create_pcilist() failed.
Device detection failed.

```

Not sure if this means I've done something wrong or what.

I am using the nVidia binary blob driver.....

---

### Post by PatrickMay16 on 2007-02-14
Ah!!!!!!!!!!!!! I got it to compile. Then I ran the tests as instructed, and emailed the resulting text files to the email address, as instructed.

---

### Post by Sammi on 2007-02-15
It's polite to tell how you did it.

---

### Post by rai4shu2 on 2007-02-15
What are the depends here? I can't get this to work:

> ./renouveau: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

EDIT: This is weird, because I can find that file fine in libsdl1.2debian-alsa, which is installed.

/usr/lib/libSDL-1.2.so.0

---

### Post by rai4shu2 on 2007-02-15
Never mind, I got it built. I got this built by installing the following packages:

libsdl1.2-dev, xlibs-dev, xorg-dev, nvidia-glx-dev

---

### Post by rai4shu2 on 2007-02-15
Okay, it builds fine but it totally locks up my box on step 29 or 34 (I tried it twice and had to hard reset both times). Is this program 64-bit clean?

---

### Post by manmower on 2007-02-15
Thanks all for sharing advice on compiling it from source.

To all those experiencing problems running REnouveau, I would suggest sending an email to the devs describing the error and your hardware configuration, and adding your partial dump files (if any) to the mail, so that hopefully these errors can be adressed.

---

### Post by brazzmonkey on 2007-02-15
> **rai4shu2 said:**
> Okay, it builds fine but it totally locks up my box on step 29 or 34 (I tried it twice and had to hard reset both times). Is this program 64-bit clean?
similar troubles here : either it segfaults or freezes my box (mouse can still move, though), somewhere around steps 36 to 39.

---

### Post by menachem on 2007-02-16
Someone should make a live CD (perhaps based on something like Damn Small Linux) that boots up and runs this program. That way we could take it to everyone we know who has an NVidia card and run it on their computers, even if they aren't running linux.

---

### Post by dutchmega on 2007-02-16
> **menachem said:**
> Someone should make a live CD (perhaps based on something like Damn Small Linux) that boots up and runs this program. That way we could take it to everyone we know who has an NVidia card and run it on their computers, even if they aren't running linux.
I think you can just run the Ubuntu liveCD, download that program, compile it & run it...

---

### Post by PatrickMay16 on 2007-02-16
> 	Someone should make a live CD (perhaps based on something like Damn Small Linux) that boots up and runs this program. That way we could take it to everyone we know who has an NVidia card and run it on their computers, even if they aren't running linux.


> **dutchmega said:**
> I think you can just run the Ubuntu liveCD, download that program, compile it & run it...

But wait! Don't you need to be actually using NVIDIA's binary driver? That's what they're trying to reverse engineer, after all. As you see, the ubuntu livecd does not include NVIDIA's binary driver. AGH!!!!!!!! So, this can't work.

---

### Post by Mattallyc on 2007-02-17
> **ciaran.mooney said:**
> Hi,

I tried running it and got 

```

detect_devices: create_pcilist() failed.
Device detection failed.

```

Not sure if this means I've done something wrong or what.

I am using the nVidia binary blob driver.....

Me too.  I downloaded the file in post #1 extracted it to my desktop and in a terminal ran
"sudo ./renouveau" in the extracted folder.
What am I doing wrong?
Cheers,
Matt.

---

### Post by halfvolle melk on 2007-02-17
Try the method from post #5.

---

### Post by Mattallyc on 2007-02-17
> **halfvolle melk said:**
> Try the method from post #5.

Hmmm...
Tried that. All went great but still got the same error message when running it.
Using Ubuntu 6.10 - what can I try next?

---

### Post by ashmew2 on 2007-02-20
Dump sent for GeForce MX 4000 :D

---

### Post by ssam on 2007-03-07
[http://users.tkk.fi/~jpakkane/ren/](http://users.tkk.fi/~jpakkane/ren/) has a list of which cards data is still needed from

[digg]("http://digg.com/linux_unix/Nouveau_Open_Source_3D_needs_you_pleas_send_dumps_of_your_card")

---

### Post by manmower on 2007-03-07
Thanks ssam, I've added the link to the first post as well.

---

### Post by white on 2007-03-07
> **brazzmonkey said:**
> i'm getting segmentation fault here...

I too am getting a segmentation fault.

```
devon@devon-desktop:~/renouveau$ ./renouveau
Segmentation fault (core dumped)
```

It ran 3-4 tests. If everyone else got that than at least I am doing something right. lol

---

### Post by bonzodog on 2007-03-07
Managed to get it to compile, though it wouldn't if the #DEFINES were uncommented in re.c.

Tests done on Zenwalk Linux, Xorg 7.1.1
Geforce 6200 card.

Sent to above mail address.

---

### Post by mikl on 2007-03-08
My computer crashes at step 3... Is this supposed to be run as root?

---

### Post by cowlip on 2007-03-08
I have a TNT2-type card sitting somewhere in my house, it's just a matter of finding it because I see that not many tnt2s have been dumped yet.  I'll have tons of boxes to go through..

---

### Post by SraM on 2007-03-09
> **ciaran.mooney said:**
> Hi,

I tried running it and got 

```

detect_devices: create_pcilist() failed.
Device detection failed.

```

Not sure if this means I've done something wrong or what.

I am using the nVidia binary blob driver.....
I've got another error message: 
> detect_devices: Creating probe window failed.
Device detection failed.

No way to avoid it? Please Help us for helping Open Source...

---

### Post by ThibG on 2007-03-10
My computer frozen a few  time after I start renouveau...
I'm on Edgy Eft, with the nvidia-glx package, from Canonical, and I have a GeForce GO 7600...
By the way, it's not the first time it happened ( but I tried 3 times renouveau, it froze the 3 times ) : a few times, it occured when playing.

---

### Post by cowlip on 2007-03-30
Nouveau have a new renouveau script out, it automatically packs up the results.

I installed the official Nvidia drivers on the Dapper Drake live cd using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") envy_0.8.2-0ubuntu1_all.deb.  Then I installed renouveau (it needed this: sudo apt-get install build-essential cvs mesa-common-dev libsdl1.2-dev libxvmc-dev nvidia-glx-dev )


I have a Riva TNT2 that came with my computer but I can't find it now--maybe some posters reading this post can help in that case.  It seems like they really need TNT2, NV1, 2  cards, among some others, for dumps- but I just did my Geforce Ti 4200.

I used it on a multi-monitor system with Twinview however--does anyone think that affected the results negatively?  And what's this about[ needing kernel, SLI, and Mmio traces (from the Nouveau Companion #16)]("http://nouveau.freedesktop.org/wiki/Nouveau_Companion_16")?  Is it easy to help out with?

> Refer to our status page [http://users.tkk.fi/~jpakkane/ren/](http://users.tkk.fi/~jpakkane/ren/) for renouveau dumps. Only dumps for cards listed in red are currently needed. We would be interested in SLI dumps though (and please set the Topic line of your email to hint at the fact that this is an SLI dump). G80 owner willing to test patches would be very welcome too.

Still [MmioTrace ]("http://nouveau.freedesktop.org/wiki/MmioTrace")dumps would be very welcome.

---

### Post by Megatog615 on 2007-04-17
I use the official drivers from NVIDIA's website. How do I build this if I can't install the nvidia-glx-dev package(since that installs nvidia-glx)?

---

### Post by jiminycricket on 2007-04-22
Nouveau needs ALL NEW DUMPS again, I just saw this on Digg:

So if you've dumped your card already...do it again with the new script :)

[http://digg.com/linux_unix/Nouveau_Open_Source_3D_needs_you_95_1_Of_all_Dumps_are_needed](http://digg.com/linux_unix/Nouveau_Open_Source_3D_needs_you_95_1_Of_all_Dumps_are_needed)

> Nouveau : Open Source 3D needs you! 95.1% Of all Dumps are needed!

Digg helped the Nouveau project get new dumps over a month ago. Now out of 245 nvidia cards, 112 cards are missing and 121 are old dumps. If you have an nvidia card and linux please help.

[quote=diggapleaze]***The following applies to Ubuntu users who would like to contribute a dump and who have nvidia's proprietary driver installed and activated. You MUST turn off desktop effects(beryl or compiz) for the following***

install the dependencies for REnouveau by issuing the following command in a terminal:

sudo apt-get install build-essential cvs mesa-common-dev libsdl1.2-dev libxvmc-dev nvidia-glx-dev dialog

Next, download this script [http://www.ping.de/sites/koala/script/createdump.sh](http://www.ping.de/sites/koala/script/createdump.sh) to your desktop by doing the following:

cd Desktop && wget [http://www.ping.de/sites/koala/script/createdump.sh](http://www.ping.de/sites/koala/script/createdump.sh)

Now make the script executable:

chmod a+x [http://www.ping.de/sites/koala/script/createdump.sh](http://www.ping.de/sites/koala/script/createdump.sh)

and now run the script:

./createdump.sh

Wait for 5 minutes as the funky graphics test run their course. Do NOT touch anything, just leave the computer alone until it's done. When it is finished, check in the rentmp folder on your desktop for a file with a name similar to Nvidia_10de_0141.tar.bz2 (the name of your dump may vary, but it will end with a suffix of tar.bz2). Send this file to renouveau.dumps AT gmail DOT com . Do *not* send the dump if REnouveau crashed in any way. After a few days, check [http://users.tkk.fi/~jpakkane/ren/](http://users.tkk.fi/~jpakkane/ren/) and look for your dump and your name.

Congratulations, you've just contributed to the development of Free nvidia drivers![/quote]

Megatog:  I don't know how you would do that...hmm..anyone else?  I guess people with the new 9xxx nVidia drivers that only support their newer cards would be messed up too because nvidia-glx-dev depends on nvidia-glx instead of  that AND nvidia-glx-new...

---

### Post by Megatog615 on 2007-04-23
How(where) were the files in nvidia-glx-dev acquired?

---

### Post by jiminycricket on 2007-05-01
Megatron, it seems that the package[ nvidia-dev-new]("http://packages.ubuntu.com/feisty/misc/nvidia-glx-legacy-dev") was added to Feisty repositories.  You should be able to use renouveau, now.

---

### Post by Megatog615 on 2007-05-01
I use the official installer from the nvidia website...

---

### Post by Carrots171 on 2007-05-14
> **jiminycricket said:**
> Nouveau needs ALL NEW DUMPS again, I just saw this on Digg:

So if you've dumped your card already...do it again with the new script :)

[http://digg.com/linux_unix/Nouveau_Open_Source_3D_needs_you_95_1_Of_all_Dumps_are_needed](http://digg.com/linux_unix/Nouveau_Open_Source_3D_needs_you_95_1_Of_all_Dumps_are_needed)





Megatog:  I don't know how you would do that...hmm..anyone else?  I guess people with the new 9xxx nVidia drivers that only support their newer cards would be messed up too because nvidia-glx-dev depends on nvidia-glx instead of  that AND nvidia-glx-new...

Thanks for the news on new dumps.  The OP should be updated with these instructions.

---

### Post by adewale on 2007-06-09
i would love to dump my core but i had to disable the nvidia driver cause it freezes my pc i haven't gotten a solution 4 it yet. i use an nvidia mx 400

---

### Post by TheMono on 2007-06-09
Downloaded, compiled for my 64bit machine, segfaulted on running immediately.

I'm probably an unusual case though, 64 bit with bigdesktop enabled.

---

### Post by jiminycricket on 2007-06-09
Go on their IRC channel!  They would love to help you.  BTW Fedora 7 includes an alpha version of the Nouveau driver if you want to test out their live cd.  You have to CTRL + ALT + BCKSPC the x server, then edit xorg.conf to use nouveau instead of nv.  Then 'startx'.

---

### Post by gnomeuser on 2007-06-09
Some of the X developers are also working on the Radeon cards and they appear to need BIOS dumps:

How to get them:
[http://tirdc.livejournal.com/7704.html](http://tirdc.livejournal.com/7704.html)

Where to send them:
[http://bios.egore911.de/](http://bios.egore911.de/)

---

### Post by TheMono on 2007-06-10
Went onto IRC after getting back from work - 85 members, no replies for ten minutes. Gave up.

---

### Post by jiminycricket on 2007-06-10
How about this, does it apply to your card?

[http://nouveau.freedesktop.org/wiki/REnouveau](http://nouveau.freedesktop.org/wiki/REnouveau)
> Requirements:

Functional nvidia drivers are needed, very old ones are not likely to work. 6xxx, 7xxx, 8xxx series are likely to work (based on a cvs commit log mentioning 6xxx support and assumption). 3xxx, 4xxx, 5xxx series may requires a 2.4 kernel, and renouveau must be linked against libGL at compile time.

Note: If you have driver version 9xxx and your card is PCI-E, renouveau may segfault or hang your machine. In this case, please try 8xxx drivers.

gnomeuser: I'll have to do that soon.  My laptop is an (older) ATI Mobility which it seems they're looking for.

---

### Post by TheMono on 2007-06-10
7600GS, so no, it shouldn't apply. I'm also using the stock feisty nvidia binary, nothing fancy through envy or the like.

---

