---
title: "Uninstalling lubuntu"
date: 2016-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by robartist on 2016-03-27
I have an HP stream, 2GB, 32GB and thought that Lubuntu would be quicker in use than Windows 10.

I tried really hard to install it but failed. It took a fair while for me to get it to install in the first place. Then took an age to sort out how to get wifi working. But finally, after a lot of time, I couldn't get the touchpad working.

So, I gave up and uninstalled Lubuntu. Though I still haven't worked out how to uninstall EFI.

I've been using computers for decades and have never had any problems installing Windows. But installing Lubuntu was impossibly difficult. I just couldn't get it fully working.

I know this will fall on deaf ears, but for Linux to really take off it needs to be trivial to install. And after installing it then everything should work. That doesn't seem to be the case at the moment.

I am moderately computer literate and I couldn't get Lubuntu fully working. What hope is there for someone who doesn't have any skills in installing an OS?

Good luck to you all

---

### Post by Bucky Ball on 2016-03-27
For what it's worth, I have exactly the same notebook (HP Stream 11?) and installed without issue. Works faultlessly.

Anyhow, just install Windows. That will wipe out anything that's on there and probably write its own EFI partition, too. 

Hopefully someone with more know-how can input with more detail, if any is required.

You appear to have posted a thread about the trackpad issue 20 hours ago. Is the machine working fine apart from the trackpad issue?

We are an international forum across many time zones so sometimes it can take awhile. If you don't receive a response after 12 hours or so, simply post 'bump' on the thread. That will move it to the top of the new post list.

Anyhow, good luck.

PS: if you want everything to work after install, whinge to the manufacturers of your hardware and ask them to play nice with Linux, not here or to Canonical. We certainly can't do anything to change that apart from let hardware manufacturers know and buy hardware that works fine with Ubuntu. I did and my HP Stream works fine with Xubuntu, which is heavier than Lubuntu, and it is working snappy from the 32Gb eMMC. :D It is a mystery why your trackpad is not working, though. 

PPS: Which release of Lubuntu are you using? 14.04?

PPPS: To install on a HP Stream, which doesn't have an ethernet port or DVD drive, just boot the USB and choose not to update during install and don't tick third-party drivers, for what its worth. Then you don't need to be online and won't get possibly the complaints and issues you were getting. Although the horse has already bolted ...

---

### Post by vasa1 on 2016-03-27
I'd say this belongs in Chat or Recurring. OP has very clearly not asked for support in a specific way.

---

### Post by robartist on 2016-03-27
Thanks BB
I got around the wifi issue by initially connecting my mobile phone to the USB port and updating everything - I HOPE that was via wifi on my phone and not via my phone contract, which would cost a fortune. I then managed to sort out the drivers problem. But as I said it was difficult and time consuming.
Regarding the trackpad issue it seems I am not alone in having problems on the HP Stream. Just Google.

Finally, whilst I understand why you say it is a problem for the computer manufacturers, it is nevertheless true that beginners like me struggle to install Linux. In fact I found it impossible to get a fully working system.

My point was that a lot of people would be put off installing Linux due to it being very difficult to install. If it were as easy to install as Windows then I am sure there would be a lot more users. I found Lubuntu great to use. I just couldn't get the touchpad working. Had I been able to do that I would have stayed with it.

Incidentally, I have tried to install Linux on a variety of machines over the years and have never managed to get a fully working version.

But I am fairly low on ability when it comes to computers. Perhaps installing Linux is something that is too difficult for me.

---

### Post by robartist on 2016-03-27
Sorry meant to say that I installed Lubuntu 15.10

---

### Post by buzzingrobot on 2016-03-27
> **robartist said:**
> 
My point was that a lot of people would be put off installing Linux due to it being very difficult to install. If it were as easy to install as Windows then I am sure there would be a lot more users.

Installing a distribution like Ubuntu *is* easy if it is installed in the same manner as Windows. I.e., point the installer at a single drive, assume no other operating system is on the drive, repartition and reformat the entire drive automatically with no user input, install the OS, and write a new bootloader that overwrites anything else that's there.

That's how Windows installs.  It's also how Ubuntu installs if you selected the first option in the partitioning section of the installer.  (The Windows installer does allow users to deal with existing partitions individually, but a lot of people don't seem to realize this.)  It's unfortunate that new users wishing to dual boot are thrown immediately into dealing with things they've probably never heard of -- shrinking partitions, bootloaders, etc. -- and even though it obviously discourages Linux adoption it's a result of the current state of art and nothing magic can be done about it.

If you want to install Linux in a dual-boot scenario, then some care needs to be taken and preparations made. Most of it has to do with getting the bootloader right, and that's down to the basic standardized design of PC's and their firmware, not any particular OS.

Hardware support after the installation, especially for unusual or very new hardware, is better in Windows than Linux and, presumably, always will be so long as Windows is the dominant product. Vendors would be foolish to release hardware without concurrently providing Windows support, and they aren't going to delay release while they conjure up Linux support.

The Ubuntu installer does include options, by default unchecked, to download and install updates, as well as Flash, codecs, etc., during the installation. Without an available network, those options, of course, should not be selected. (By comparison, I've found that Win7 installs on hardware introduced after the Win7 install image was released fail because the install image contains no usable ethernet or wireless driver. Win10 will complete the install with no network access, but that still leaves you to acquire the drivers and install them manually.  I've just had that experience with Win10 on three-month-old Intel Skylake hardware. Ubuntu's installer, in contrast, found and enabled the network.)

---

### Post by neu5eeCh on 2016-03-27
This will echo Buckyball's comments, but...

My family has three HP Stream 11's -- my wife and daughters. They all run Ubuntu. First thing I did was to copy the Windows Installation (before I even booted it) to an ISO. Then forgot about it.

I disabled EUFI and Secure Boot because IMHO Secure Boot is an overblown and over hyped piece of rubbish.

Then gave the whole (32 Gigs) "hard drive" to Linux. Done. The trackpad has always worked except for the final update to 15.04 *after* it was past due. Upgrading to 15.10 fixed that. The realtek wireless is a problem in these units. The driver can be gotten [here]("https://github.com/lwfinger/rtlwifi_new"). Hopefully the kernel update in 16.04 will _***finally***_ support these drivers, but I don't know. As it is, using an alias in .bashrc, running the single command "wreinstall" cleans, makes/compiles, and reinstalls the driver after every kernel update.

All in all (and all else being equal), Linux/Ubuntu runs beautifully on these machines. In fairness, [the particular model they're using]("http://www.amazon.com/review/R28HR668I6LU8Y") has been discontinued.  Maybe your newer model has a trackpad that isn't supported yet?

---

### Post by robartist on 2016-03-27
It's a Synaptics trackpad.

I am sorry but I do disagree with some comments.

Although I am not a whizz on Linux I am certainly fairly computer competent. And yet I have never managed to install Linux on a computer and have it fully working.

The difficulties are demonstrated when you point to a link for drivers to get the wifi working. The vast majority of computer users wouldn't know what to do with that. As for typing 'sudo-get etc etc', that really is beyond most users.

Maybe full blown Ubuntu would have delivered a fully working touchpad - I don't know.

But in reality if you were to pick a hundred computer users at random and ask them to install Windows on one machine and Linux on another the likelihood is that they would succeed with Windows but not with Linux. Which is a shame.

I would love Linux to become more universal but the fact that wifi doesn't work out of the box would put most computer users off.

Add into this the fact that I wanted a reasonably lightweight distribution and then the whole thing becomes very difficult.

In my particular case, despite being fairly competent with computers, I found it totally impossible to get Lubuntu fully working with a functional trackpad. And I tried very hard and spent a lot of time reading on the internet.

If I can't get it working I am confident that the vast majority of computer users wouldn't be able to get it working.

I should add that I would love Linux to be easy to install and use and be the most popular operating system.

---

### Post by neu5eeCh on 2016-03-27
//The difficulties are demonstrated when you point to a link for drivers  to get the wifi working. The vast majority of computer users wouldn't  know what to do with that. As for typing 'sudo-get etc etc', that really  is beyond most users.//

Yes, you're absolutely right. For a variety of reasons (most of which are beyond the control of Linux Distros -- including Ubuntu) the Linux desktop requires a certain savvy and knowledge beyond "most users".

I agree.

So if your point is that Linux is harder to install on a newer laptop with Windows pre-installed and vendor provided drivers, then point made. :) We can move on.

As for your trackpad issues: My best advice is to install whatever distro provides the very latest Kernel. That might have to be Arch Linux; but try 16.04 first. Originally, 14.04 didn't work on the HP Stream because the kernel didn't support the hardware. Had to install 15.04. That might be the case with *you*.

---

### Post by buzzingrobot on 2016-03-27
> **robartist said:**
> 

The difficulties are demonstrated when you point to a link for drivers to get the wifi working. The vast majority of computer users wouldn't know what to do with that. 

Few users really need to do that.  

In any case, there is nothing anyone in Linux can do about it.  If a hardware vendor chooses not to release a Linux driver, or chooses to avoid releasing enough information to allow Linux developers to successfully reverse engineer a driver, then there will be no Linux driver.

And, as I mentioned, the same problem affects Windows.  I installed Windows 10 a few days ago  -- using an ISO downloaded that day, so it contained most updates -- on  an Intel machine released in December and manufactured in February.  I.e., before that ISO install image was built. Still, the image didn't contain a usable ethernet or wifi driver.  The install finished and there was no network.

Getting the drivers required going to another machine (which most users do not have), correctly formatting a USB stick (which most users won't know how to do), going to the correct Intel site (which most users won't be aware exists), selecting and downloading the appropriate drivers (again, most won't know), copying them to the USB stick, inserting the USB stick in the Win 10 machine and installing the packages.  Then, I had a network.

My Win7 experience is that you need to acquire  network drivers before the install begins, put them on a second USB stick and make those files available during the install.

None of that makes Linux easier to install if a needed driver simply does not exist, but it does put some things into perspective.

> As for typing 'sudo-get etc etc', that really is beyond most users. 

Also is not really necessary on a correctly installed and working system.  Ubuntu can be installed, updated, and used with no recourse to the command line.  If a user *breaks *something then command lines tools are often the most effective way to deal with that, as they are in Windows (although most Windows users likely just trash everything and reinstall, even for trivial issues).

> I would love Linux to become more universal but the fact that wifi doesn't work out of the box...

Works here out of the box.  Not on Windows.

---

### Post by Bucky Ball on 2016-03-27
I've installed Ubuntu for my 75 year old mother-in-law (she asked me to build her a Linux box: how cool is that?) and various installs for other people and they've never gone anywhere near a terminal. Don't know if they're aware one exists.

---

### Post by Geoffrey_Arndt on 2016-03-29
> **robartist said:**
> I have an HP stream, 2GB, 32GB and thought that Lubuntu would be quicker in use than Windows 10.

I tried really hard to install it but failed. It took a fair while for me to get it to install in the first place. Then took an age to sort out how to get wifi working. But finally, after a lot of time, I couldn't get the touchpad working.

So, I gave up and uninstalled Lubuntu. Though I still haven't worked out how to uninstall EFI.

I've been using computers for decades and have never had any problems installing Windows. But installing Lubuntu was impossibly difficult. I just couldn't get it fully working.

I know this will fall on deaf ears, but for Linux to really take off it needs to be trivial to install. And after installing it then everything should work. That doesn't seem to be the case at the moment.

I am moderately computer literate and I couldn't get Lubuntu fully working. What hope is there for someone who doesn't have any skills in installing an OS?

Good luck to you all

Mr. Rob,

The real secret to an easy install of Linux is two things:

1).   The user must research to see if the target PC for the install is Linux friendly - - preferably an all "Intel" machine:

a).   Intel CPU (like core I3, I5, or I7)
b).   Intel Integrated Graphics - - - avoid Nvidia or AMD/ATI video
c).   Intel Wireless

2).   A PC from a Linux friendly computer company - - - two examples are:

a).   Dell
b).   Lenovo

OR:

Just buy a "Pre-Loaded" Linux PC from one of the companies listed in my signature line below.   That's what most people do for Windows PC's, why not for Linux???

A preloaded Ubuntu PC from a company like System76 installs completely in about 10 minutes (yes, that's right, 10 minutes, and that's only if you're a slow typist).   And EVERYTHING will work out of the box (including touchpad).

If you need Windows also, consider running it via a free program called "Virtual Box" . . . . outside of high-end games, that works very well.   This method (VIrtual Machines) is used daily by thousands of companies (and a few million users) world wide (yes - really).  

So, to compare the ease of installing Windows versus Linux on machines expressly designed and tested on Windows only - - - is inherently unfair.    It would likewise be unfair if you tried to install Windows on a mainframe or super-computer, because . . . . there isn't one of these machines on Earth designed and tested to run with Windows.  (They're designed to run on Linux/Unix & a few proprietary OS's).

---

### Post by Bucky Ball on 2016-03-29
I have one of the very latest NVidia cards (GTX 970) and it works faultlessly with 15.10 and 16.04 LTS. A blanket statement like 'avoid NVidia and AMD graphics' does not take into account the many cards by both, particularly NVIdia, that *are* supported.

If one were to avoid NVidia and AMD graphics cards for Ubuntu the Ubuntu graphics community, video and photography and other visual media enthusiasts, would be largely dead in the water. Fancy editing and rendering HD 1080p 50fps video with a laptop's dinky Intel graphics? I thought not. But you're probably not about to do that on a standard, web surfing email checking consumer grade lappy in any case I guess. :)

---

### Post by Geoffrey_Arndt on 2016-03-29
Yes, Nvidia does provide a great product line and issues Linux drivers (albeit closed - - & often not installable with the standard install process . . ).      Correct me if I'm wrong but other than "high-end" , fps-demanding games, what can't Intel graphics handle?    Especially chipsets like the IrisPros 5200 and similar?   Photo, media, cat/engineering, . . . . all very doable with Intel graphics & the right cpu and ram.

The Original Poster of this thread is frustrated by the install process . . . with much of that frustration stemming from self-inflicted (albeit unrealized) wounds.     _An all Intel machine bumps up the odds for a successful "first-try" install_ and does 95%+ of what most home users, business users, educators, scientists, IT pros and engineers need.   Yes, gamers & media professionals will be happier with Nvidia and that's fine, but let's not *even infer* one can't do media, graphics, etc. without Nvidia/AMD . .

So, the intent of my comments re Intel is not to diss Nvidia or AMD (their Linux support seems to be improving), . . . but to help the OP and similar newbies with a less painful install experience.

---

### Post by Bucky Ball on 2016-03-29
I totally agree with you. But the point I'm making is you made a blanket generalisation without qualifying it with any of the above in the original post.

> ... avoid Nvidia or AMD/ATI video

You qualified it with nothing. :)

> The Original Poster of this thread is frustrated by the install process

The subject of the thread is how does OP uninstall Lubuntu. If there are new support requests, best the OP start a new thread. Anyhow, back on topic for this one.

---

### Post by Geoffrey_Arndt on 2016-03-29
it's just too bad that the install didn't go better, then there might not be a request to uninstall . . . but , , , maybe next time . . .

---

### Post by robartist on 2016-03-30
Ok I think we have to agree to disagree. I've never experienced problems when installing Windows. But with Linux neither the wifi nor the trackpad worked. Again I have never experienced  that on Windows.
And I've done a fair number of installations over the years.

Don't misunderstand me. I  would absolutely love Linux to be the most universally used OS. But it really   isn't as easy as Windows to install - in my years of experience.

---

### Post by neu5eeCh on 2016-03-30
> **Geoffrey_Arndt said:**
> A preloaded Ubuntu PC from a company like System76 installs completely in about 10 minutes (yes, that's right, 10 minutes, and that's only if you're a slow typist).   And EVERYTHING will work out of the box (including touchpad).

Yeah, that's what *I* used to think and the reason I spent a good chunk of change on a System 76 laptop. Came with a stuck pixel, which they wouldn't exchange because I didn't notice until the first month had passed, and "Sleep" doesn't work (and never did). One of the reasons I bought from them was to have a Linux system on which Sleep worked (wanted everything to just work). I still probably would have bought the system, but they should be up front about what doesn't work.

---

### Post by neu5eeCh on 2016-03-30
> **robartist said:**
> But it really   isn't as easy as Windows to install - in my years of experience.

In your experience, perhaps, but you might find the following somewhat cautionary:

[http://www.zdnet.com/article/sticking-with-windows-7-the-forecast-calls-for-pain/](http://www.zdnet.com/article/sticking-with-windows-7-the-forecast-calls-for-pain/) 

More to the point, have you ever _*really*_ tried installing non-OEM windows in a new (or old) machine? *I have*. I used to think like you; and I was shocked to discover that installing Windows (after years of Linux) is a real PITA and much more time consuming and problematic --- than Linux.

I think Linux is a better system. Given that I have 3 HP Streams in use in my family, and that everything works (but Sleep), I don't think you tried very hard to solve your installations problems. That's okay, but I'm skeptical of your post.

---

### Post by Geoffrey_Arndt on 2016-03-30
VT . . just curious, how are you defining "sleep"??

On my Sys76 Galago laptop,  the unit will go into a suspend state after a few minutes of inactivity.  The screen is dark but immediately returns to a normal display upon key-press or mouse-motion.    If the laptop is not used after a specified time (30" in my case) . . the suspend changes state and the laptop enters hibernation status.   Keypress of mouse-motion will not wake up, but a simple press of the on/off button returns the laptop to the exact screen as it was prior to suspend . . hibernate.   It will show the exact web page, or app that was open, and function normally.

This doesn't happen on your Sys76?   What did the Sys76 folks say about it when you opened a trouble-ticket?    If something doesn't work - - they'll respond with a confirmation, or the suggested work-around.   At least, that's been my experience - - so, my next PC will be System76 once again.

Oh . . . by the way,  the OP very likely could have the bad luck of having 1 or 2, or even 3 PC's in a row, that were not Linux friendly, on top of maybe not being a "give it the old College try" kind of guy. ? ? ?  who really knows ? ? ?  - - everything on an internet forum is as verifiable as "hearsay" is in a Court of Law (until it's tested in real-life) . . .

PS:   what else is strange . . . I've installed various Linux distros on at least two dozen or more PC's over the years.   All the laptops had standard synaptics trackpads - - not one instance of failure . . . not one.

---

### Post by robartist on 2016-03-31
Why be so aggressive VT Poet??

You say 'I don't think you tried very hard to solve your installations problems'.

How on earth do you know that? FYI I spent hours trying and failing to resolve the trackpad issue. And as I keep saying not everyone has in depth knowledge of fault finding in Linux.

But go on, enlighten me. How do I get the trackpad working on LUBUNTU (note not Ubuntu). Please give full instructions and I shall try yet again.

I challenge you to come up with a set of instructions that will work on my HP Stream 11".

You seem very confident that I haven't made any effort to resolve this problem. Presumably you can readily resolve it.

---

### Post by xc3RnbFO8P on 2016-03-31
Can you show the output of 
> sudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf

---

### Post by neu5eeCh on 2016-03-31
And while you're at it:

```
inxi -F
```

If you don't have it, then:

```
sudo apt install inxi
```

---

### Post by robartist on 2016-04-01
HA!!! I notice that after accusing me of not trying to find a solution you are totally unable to help me with solving the trackpad problem!!

---

### Post by robartist on 2016-04-01
VTPoet. Can you please not join in this thread.

---

### Post by howefield on 2016-04-01
> **robartist said:**
> VTPoet. Can you please not join in this thread.

Please desist in telling others where they can and cannot post.

Posting in a public forum means that you get to see responses that you might not agree with or like, that's the way it goes. Anything that falls outside of the forum [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules") can be reported.

---

### Post by robartist on 2016-04-01
I thought these forums were to help people. I personally found VTPoets reply unhelpful and didn't like the tone of the reply. It seemed unnecessary to treat me, a newbie, like that.

---

### Post by vasa1 on 2016-04-01
> **robartist said:**
> I thought these forums were to help people. I personally found VTPoets reply unhelpful and didn't like the tone of the reply. It seemed unnecessary to treat me, a newbie, like that.You should go back and read your own first post with an impartial frame of mind. It didn't make me want to help. Whether I could or not is another matter.

---

### Post by robartist on 2016-04-01
vasa not sure what you mean. I tried to use lubuntu and failed. Then went on to say that Linux is great but would be even greater if it was easy to install - a fair point. Certainly not aggressive. I didn't have anyone to be aggressive to. 

But anyway. Some people seem to think that ubuntu works ok on the hp stream 11.

As mentioned above I can't get it going for a different reason. Can you help?

---

### Post by 1clue on 2016-04-01
Can we relax a bit?

This forum **is** for support, but rather than a paid staff you get a bunch of other regular (maybe some not-so-regular) people who use Ubuntu of some flavor.

@robartist,

IMO Ubuntu is one of the easiest operating systems to install, from any vendor.  Obviously your experience differs.

I think very few people who call themselves Windows experts have actually installed the full licensed Microsoft Windows, from a purchased box or from a Microsoft.com download, from scratch on a disk that never contained Windows. Most people buy a PC with Windows already on it. They upgrade it with Windows provided by the manufacturer of the hardware, which already has all the driver issues fixed. That's an extremely different scenario from taking an unmodified Microsoft Windows and installing it, getting all the proprietary drivers and getting it to work.

My first exposure to Ubuntu was from a friend of mine, who installed it in almost exactly 5 minutes, from the cd-rom installer's first prompt to reboot into the new OS. He used the defaults for everything. I have never seen this on anything else, not even a Mac. This was years back, but the computer was an old HP laptop and on Windows its WIFI had been broken for years. On Ubuntu everything worked flawlessly.

Obviously this does not work with all hardware. It takes time for the people with experience with your hardware to see your post and respond to it.  Sometimes it takes days or weeks.  Sometimes you're the only one and have to break new ground, so to speak. That's usually on esoteric hardware though. Usually mainstream hardware has lots of experienced users.

If you have some patience I'm sure we can get this sorted out for you, either for Linux or for Windows.

---

### Post by howefield on 2016-04-01
> **robartist said:**
> As mentioned above I can't get it going for a different reason. Can you help?

Your question has been moved to one of the support forums, [here]("http://ubuntuforums.org/showthread.php?t=2319146"). Feel free to expand as you see fit. Posting tips which might help are [here]("http://ubuntuforums.org/showthread.php?t=2158945").

---

### Post by robartist on 2016-04-01
Perhaps rather than everyone having a go at me they could have a go at solving the problem of how to get linux working on my hp stream?

Please just chill and get on with helping me get linux working - IF it is possible. Maybe not.

---

### Post by robartist on 2016-04-01
1clue

Yes I do disagree with the relative difficulty of installing linux vs windows.

I am a pensioner and have used computers for decades and have never had a problem installing windows from scratch - which I have done many times. On the other hand I have tried to install linux on several occasions over the last decade and have NEVER got it fully working.

Maybe I am just unusually unlucky.

---

### Post by 1clue on 2016-04-01
There is definitely a different mindset. I've been a computer programmer and IT guy since 1994. In 1996 I was heavily into Linux. Back then a gui on Linux was entirely optional, not stable and generally not bothered with. Since 1996 I have never bought a Microsoft operating system, with the exception of a laptop for my wife. Early on I took to building my own desktop hardware, both to avoid Microsoft licensing and to get hardware that works well with Linux. I've installed and used Windows for my work, mostly for testing. It has always been a highly involved task.

My favorite Linux distro is Gentoo. It's a source-based system. You start by setting some global configuration options, configuring and compiling your kernel, and then absolutely everything on your system is compiled by you, with your configuration rather than someone else's. The exception would be closed-source drivers or closed-source software you put on it. So I'm not exactly put off by difficult installs.

I'm sorry that I don't have anything like your laptop, so I won't be much use for your specific problems. As well, every time I've put Ubuntu on a system it went trouble-free, so I'm not much on debugging for this distro.

Given that several others have announced their similar hardware works fine, I suspect you may have a hardware problem or you may have missed something during the install process.

Good luck and have fun.

---

### Post by neu5eeCh on 2016-04-01
> **robartist said:**
> HA!!! I notice that after accusing me of not trying to find a solution you are totally unable to help me with solving the trackpad problem!!

Um, I asked you to post the results of inxi -F?

Can you do that or not?

That in addition to Ringi's request will tell me if the hardware on yours is the same as the three systems my family uses. If it's the same, then it strictly limits the reasons your installation isn't working. Among them: bad ISO or your installing an older version of a 'buntu with an outdated kernel.

> **robartist said:**
> Perhaps rather than everyone having a go at me they could have a go at  solving the problem of how to get linux working on my hp stream?

**Edit:** I don't get this complaint. Both i and another user asked you to post information to suss out your problem.

---

### Post by 1clue on 2016-04-01
This thread has been classified as a chat thread due to the way the discussion has turned.

If you want help to fix your Lubuntu install it might be a good idea to clear the air by starting a new thread.

It would be a good idea to include the output of the commands VTPoet is asking for.

---

### Post by Geoffrey_Arndt on 2016-04-02
RobArtist:

Looks like the "ball is in your court" (a US basketball term) . . . . so, you've asked for help, the forum is trying to assist.   Will you now cooperate and provide the details requested?

---

### Post by Bucky Ball on 2016-04-02
> **Geoffrey_Arndt said:**
> 
Looks like the "ball is in your court" (a US basketball term) ...

From tennis as far as I knew. It's origins have nothing to do with the US or basketball from what I can see. Commonly used for lots of situations, though, so valid to use in the context of basketball. ;) 

[http://www.answers.com/Q/Where_did_this_idiom_come_from''_the_ball_is_in_your_court](http://www.answers.com/Q/Where_did_this_idiom_come_from''_the_ball_is_in_your_court)''
[http://idioms.thefreedictionary.com/court](http://idioms.thefreedictionary.com/court)

---

### Post by Geoffrey_Arndt on 2016-04-02
Well shucks . . . live & learn . . . being a basketball guy, always associated it with that sport although I can see where it applies to the fuzzy balls sport.  :D

---

