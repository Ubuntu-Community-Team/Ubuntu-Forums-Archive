---
title: "I hate to write this.  Really."
date: 2007-10-20
forum: Testimonials &amp; Experiences
---

### Post by Chishikihoufu on 2007-10-20
I want to switch over; very much so.  I'm sick and tired of windows & Microsoft and all that good stuff, and don't have a whole lot of conditions placed on Ubuntu for when I do switch over, and love the whole concept and implementation of OSS.

First off I'd like to say I'd be an above-average computer user; I'm not going to say I know everything about everything, but I build computers for myself and my friends, troubleshoot (windows of course), and last but not least, RTFM for EVERYTHING.  That means when I have a problem, I sit and work at it until I figure it out, and/or read every single resource online - manuals, forums, what have you.

Now for the problem:

It's my understanding that compared to other Distros, Ubuntu likes to bill itself as a Windows replacement, and to me that seems like it should be a pretty straightforward install - which it did, for the desktop environment and assorted software.  On the other hand, after 8 hours straight of banging my head against Wine & World of Warcraft last night, I'm just about to give up on ever coming off Windows.

I jumped from being unable to enable direct rendering, to page faults, back to losing direct rendering somewhere in there, to being unable to remove newer versions of Wine to use old ones, to multiple other problems.

Now, my computer works fine in Windows (obviously), and from what I've researched, everything but the modem should work fine in Ubuntu (which limits me from switching over immediately anyways, but that's another story - I know you guys have absolutely no control over NetoDragon modems who're retarded and don't like to work with Linux.)  My specs: Athlon 64 2800+ (Just using 32 bit software at the moment), gig of PC2700 Corsair, Radeon X800 GTO.

I tried multiple versions of Wine, multiple versions of Radeon drivers, fglrx & ati in xorg.conf, slitting my wrists (surprisingly didn't help), compiling a version of Wine, and step-by-step instructions from 4 or 5 different "EASILY MAKE WOW WORK IN UBUNTU" tutorials.  -_-;

So in essence, I just wanted to let the community know how much of a difficultly I had in only trying to run one program with hardware that I know works according to others' testimonials online.  *shrug*  If this is any indication of things to come, there is absolutely no way I'm switching over anytime soon, and my friend who sat next to me the entire time is DEFINITELY not to.

---

### Post by Coldkill on 2007-10-20
Nowhere do I recall anything saying that Ubuntu is a Windows replacement

---

### Post by FredB on 2007-10-20
> **Coldkill said:**
> Nowhere do I recall anything saying that Ubuntu is a Windows replacement

Neither do I. Linux distro are an alternative to Windows, like OS/2 was in its glorious time.

---

### Post by Chishikihoufu on 2007-10-20
Oh christ.  I meant DESKTOP Replacement; as in, out of all the possible Linux Distros, Ubuntu is the furthest along and most suited to being a desktop replacement/alternative in lieu of Windows.

You know what I meant - stop picking apart little statements in an attempt to discredit the rest of what I said.  Then again, if this is the normal response, bugger off and delete my post already.

---

### Post by -grubby on 2007-10-20
you're free to use whatever you want, whatever works best for you. Really. I"m not going to bite your head off if you don't. Ubuntu just happens to work better than Windows does, for me, at least.

---

### Post by MRiGnS on 2007-10-20
> **Chishikihoufu said:**
> Oh christ.  I meant DESKTOP Replacement; as in, out of all the possible Linux Distros, Ubuntu is the furthest along and most suited to being a desktop replacement/alternative in lieu of Windows.

Ubuntu may be one of the most popular Distros and the one with the hugest community, but it's not even close to be the best, easiest whatever for the desktop out of linux distros.

---

### Post by Can+~ on 2007-10-20
I'm using and X800 GTO2 and I can't run any driver (tested: ati, radeon, fgrlx) except vesa. Fglrx is the worse one, it won't boot and before ubuntu starts some green and red lines appear on the screen, then I get to bulletproof.

This is a bad time to own an X800-850 in general. Looks like this last xorg, and the fglrx is useless with this card. I still have hope for the next fglrx to fix this :(.

Question: In feisty I could enable the aiglx, now in gutsy, I also can do it with the vesa driver, but DRI won't run. What was the default ati driver used in Feisty?

---

### Post by conehead77 on 2007-10-20
I wonder why WOW doesnt has a native Linux version? My favorite online game just made a deal with Transgaming to get a "native" client, so im not worried that it doesnt work with wine atm.
You could purchase Cedega for 5$(?) a month, maybe it will work then. 
Your video card could be part of the problem, not much you can do about but waiting for the new drivers.

WOW sucks anyways :lolflag:
j/k, i can feel your pain

---

### Post by sstusick on 2007-10-20
Cedega doesn't live up to the hype, from what I hear and from my own experiences.

---

### Post by Ghost|BTFH on 2007-10-20
First of all:

"Radeon X800 GTO"

That's problem #1.

ATi and Linux don't get along well. Period. I don't care how many people with tape on their glasses want to tell you how EASY it really is to configure, it's a headache, and honestly, ATi has some of the world's worst drivers even for Windows, let alone Linux.

I know this doesn't sound like much of a fix, but step one, GET AN NVIDIA CARD! It's supported. Fully.

Problem #2:

It's not Linux, it's not wine...It's Blizzard and World of Warcraft.

They just recently switched from Hardware based sound to really crappy Software based sound.

Firstly, you need updated drivers. Possibly more updated than what Ubuntu can offer you. With nVidia, they stay pretty up to date, so one update on the drivers and away you go to the next headache...

SOUND...

In order to even get the game running worth a damn, it's required to set the dropdown box in Audio (in winecfg) to Emulation AND check the box for Emulation. As for which one of the sound drivers works best, no clue, but ESD was required to even get sound back on my box.

Now that I'm using Ubuntu Studio, it's a whole new world of pain. ESD isn't even in there (Which is really a blessing.) So does ALSA work? Not yet, I'm going to have to tweak that for awhile...OSS? Nope...no dice there....JACK, by chance? Nope, the server's not set up properly from the word go. I think Pulse Audio is running the show right now, and wine has no driver setups for Pulse. Which means, it's not going to directly interact, which means....yeah, headaches upon headaches. One of these days, I'll have my sound working in Ubuntu Studio...I swear it!

See, I've been running Linux since about 3 months or so after the game came out. So, I've run WoW on everything from Fedora to SuSE as well as Ubuntu. I've never had a major issue with the distributions - only with World of Warcraft.

So, as someone who's dealt with a lot of BS every damned patch day when Blizz decided to modify YET ANOTHER perfectly functioning aspect of the game:

It's not Ubuntu's fault.

Cheers,
Ghost|BTFH

---

### Post by LaRoza on 2007-10-20
(For my perspective, Ubuntu had perfect hardware recognition and worked perfectly on my computers, including an old desktop, a new desktop, a new laptop. I just upgraded my laptop to Gutsy over a wireless network in less than an hour, and had no problems.)

Now on to you...

I see you had many problems, and I am sorry I can not offer a fix. ATI is just recently realising that Linux uses will pay for their cards if they just release information to make good drivers. It is not the fault of Linux in this case.

You might like to try another distro of Linux; Pardus, PCLinuxOS, LinuxMint, or a few others may change your mind.

To me, Ubuntu was a Windows replacement, overwrote Vista with glee...

---

### Post by Gaute65 on 2007-10-20
The problem is probably your ati card. Amd/Ati will release a new driver this month that , according to amd/ati will work much better.( 50-90% performance increase)

---

### Post by NotTheMessiah on 2007-10-20
> **Chishikihoufu said:**
> 
You know what I meant - stop picking apart little statements in an attempt to discredit the rest of what I said.  Then again, if this is the normal response, bugger off and delete my post already.

I think that you should stick with Windows....you're perfect for each other:)

---

### Post by zero244 on 2007-10-20
What is WOW?
I have a feeling if you had a different Video card your setup would run much better.
Some of the ATI cards do have issues. I ran a 9600 ATI with fairly good results. Now Im running all 7600 Nvidia cards with very good results.
You can get a decent Nvidia card for 50 to 100 bucks...........if you figure what Vista costs your still ahead money wise.
Good Luck.

---

### Post by steveneddy on 2007-10-20
> **Chishikihoufu said:**
> , bugger off and delete my post already.

What does "bugger off" mean?

BTW - **I** like Ubuntu because it is **not** Windows. 

If you realize that Linux, Ubuntu, Apple and UNIX are not Windows, you will get to know the operating system better and fell at home in the one that you feel the most comfortable.

Now, I think I will bugger off to another thread.

---

### Post by Sef on 2007-10-20
> ATi and Linux don't get along well. Period. I don't care how many people with tape on their glasses want to tell you how EASY it really is to configure, it's a headache, and honestly, ATi has some of the world's worst drivers even for Windows, let alone Linux.

I know this doesn't sound like much of a fix, but step one, GET AN NVIDIA CARD! It's supported. Fully.

ATI has just recently open sourced their video cards, (the more recent ones), so soon ATI will be better than NVidia.

---

### Post by MRiGnS on 2007-10-20
> **Sef said:**
> ATI has just recently open sourced their video cards, (the more recent ones), so soon ATI will be better than NVidia.

I really doubt ATi will get better drivers just because they open sourced them anytime soon.

gfx drivers are not easy made programs.

In fact I really doubt the open source drivers will be on par with the closed ones by ATi.

---

### Post by sloggerkhan on 2007-10-20
People don't like hearing Ubuntu called a 'windows replacement' because' they feel like it's implying that ubuntu should be like windows, and most ubuntu users don't want it to be like windows at all. 

In any case, you don't buy a Mac and complain that it doesn't run your windows games. You probably shouldn't get linux and expect it to run your windows games. That it even makes the attempt is great, and the fact that there's some success is amazing and a testament to lots of hours put into WINE by developers. Odds are, if you are having trouble with it, others are too, and there's probably a developer or contributor somewhere who could make use of your bug reports so that soon WOW will again be working under WINE.

---

### Post by ezekielrage on 2007-10-20
The fact of the matter is that Ubuntu, like all other linux distros cant run most windows games. If it is games you seek, I suggest you stick with windows... a better option would be to get a gaming console and switch over to Ubuntu... (this is what I have done)
however, a mac would be a better option if you wanna run only WOW.
The best and cheapest choice IMO is to have some sort of a dual boot or two machines.

---

