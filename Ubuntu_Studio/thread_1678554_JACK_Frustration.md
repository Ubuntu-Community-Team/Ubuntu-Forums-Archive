---
title: "JACK Frustration"
date: 2011-01-30
forum: Ubuntu Studio
---

### Post by genmi on 2011-01-30
Running Ubuntu 10.4 LTS, just upgraded from 9.10. Before the upgrade I attempted to build JACK2 from the source on the Jack Audio website. I did not realize at the time that I had to delete the other version. So I upgraded, and then attempted to delete ALL versions of Jack... uninstalled with Synaptic and located whatever Jack2 files I could still on my machine and removed them. 

When I reinstalled Jack from synaptic and run "jackd --version i get this:

```
jackd: symbol lookup error: jackd: undefined symbol: clock_source
```From reading other threads i have deduced that I still have two versions of Jack on my computer. Is this true? if so, how do I remove ALL jack files everywhere and start fresh?

Thanks to anyone who can help.

---

### Post by Pablo_F on 2011-01-31
Hi, 

Run:

sudo updatedb
locate jack

Cheers, Pablo

---

### Post by genmi on 2011-01-31
Pablo..

Thanks for the support. Ran those commands, then reinstalled jackd from synaptic package manager. When I ran jackd --version it says 1.9.7

Now when I start up the jackserver with qjackctl I get this in the messages window:

```

p, li { white-space: pre-wrap; } [COLOR=#999999]18:03:22.336 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:03:22.396 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]18:03:22.438 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]18:03:22.632 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:03:24.312 JACK is starting...[/COLOR]
 [COLOR=#990099]18:03:24.314 /usr/bin/jackd -r -t2000 -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Unknown driver "alsa"
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]18:03:24.370 JACK was started with PID=27916.[/COLOR]
 [COLOR=#999999]18:03:24.389 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]18:03:24.390 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:03:24.392 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:03:24.803 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]18:03:26.376 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```

---

### Post by Pablo_F on 2011-02-01
Unknown driver alsa? Weird.

What is the output of *cat /proc/asound/version* ?

---

### Post by genmi on 2011-02-01
Weird indeed.

Output: ```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

---

### Post by Pablo_F on 2011-02-01
Hi again, 

How on earth have you installed jackd2? The last jackd2 (aka jackdmp) stable version is 1.9.6. 1.9.6 is in the official ubuntu repos. 1.9.7 is under development, not yet released afaik.

I suggest you stick to the jackd1 or jackd2 packages from ubuntu repos unless you want to get involved in testing or development, in which case this is not the right forum. You should report bugs or comments in the #jack channel in irc.freenode.net or in jackaudio.org, I suppose. 

Cheers, Pablo

---

### Post by genmi on 2011-02-01
I simply installed it from the synaptic repository, listed as 'jackd' with neither a 1 nor a 2 appended to it. I just removed it and then installed jackd2 from the repository. And lo and behold, it is still saying 1.9.7 under the version.

---

### Post by Pablo_F on 2011-02-01
In that case, I guess you have some bleeding edge repo enabled . What are your software sources? You can just look at the terminal output of:

cat /etc/apt/sources.list /etc/apt/sources.list.d/* |grep -v "#"

Cheers, Pablo

EDIT: Note that synaptic is not a repository, but a tool to manage the binary packages that exist in the repositories that you have enabled. By default, the ubuntu main, universe, multiverse and restricted, plus security updates.

---

### Post by genmi on 2011-02-01
```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse



deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb http://apt.puredata.info/releases lucid main
deb http://ppa.launchpad.net/falk-t-j/lucid/ubuntu lucid main
deb http://ppa.launchpad.net/pmcenery/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/psyke83/ppa/ubuntu karmic main

```

---

### Post by genmi on 2011-02-02
I know that I just recently added the falk-t-j repository in an attempt to fix this problem, so I just removed it and removed/installed jackd.. now when I do a version check I get this:

```
jackd: symbol lookup error: jackd: undefined symbol: clock_source
```

---

### Post by steveneddy on 2011-02-02
I recently tried to get Jack running so i could use Ardour and after weeks of frustration with 10.04 and Jack I finally decided to purchase a Mac and Protools - it is so much easier.

---

### Post by Pablo_F on 2011-02-02
Hi,

Well, If I were you I would do the following: 

Stick to the lucid official jackd package.
Only use bleeding edge or specialized repos to install the packages you really need, then disable them by means of System -> Administration -> Software Origins or System -> Administrationy -> Synaptic -> Configuration ->  Repositories. Then, reload (or *sudo apt-get update*)

In synaptic, you can filter by origin. 

In a terminal, you can learn what files a given package installs by using:

dpkg -L package

If you see the need of deleting files manually, use *locate jack* and *sudo rm file* with caution but before this, do a *sudo updatedb*. There will be some libjacks that you (or the package manager) should delete before trying to install jackd again.

Last but not least, never ever mix repos for different ubuntu versions unless you know very well what you are doing. 

Cheers! Pablo

---

### Post by Pablo_F on 2011-02-02
> I recently tried to get Jack running so i could use Ardour and after weeks of frustration with 10.04 and Jack I finally decided to purchase a Mac and Protools - it is so much easier. 

For me it is so much easier to just use jack and ardour instead of trying to figure out what users do to mess up their systems and try to help them. I use jack all the time, even for listening to music or recording the radio. If genmy asks for help is because he is interested in jack and ardour, I suppose. Jack works almost out of the box in ubuntu lucid, with a well supported card.

---

### Post by AutoStatic on 2011-02-02
> **steveneddy said:**
> I recently tried to get Jack running so i could use Ardour and after weeks of frustration with 10.04 and Jack I finally decided to purchase a Mac and Protools - it is so much easier.Hello steveneddy, what's the purpose of your post? You have a high posting rating (+4500!!!) so I assume you know what you're talking about GNU/Linux/FLOSS-wise and know about the do's and don'ts on forums like this.
You're not [Jono Bacon]("http://wootangent.net/2010/07/roasting-bacon/") by any chance, are you? ;)

Best,

Jeremy

---

### Post by steveneddy on 2011-02-02
> **AutoStatic said:**
> Hello steveneddy, what's the purpose of your post? You have a high posting rating (+4500!!!) so I assume you know what you're talking about GNU/Linux/FLOSS-wise and know about the do's and don'ts on forums like this.
You're not [Jono Bacon]("http://wootangent.net/2010/07/roasting-bacon/") by any chance, are you? ;)

Best,

Jeremy

I was merely stating my opinion that I found Jack with Ardour was very frustrating to get working for me - I was trying to get a professional quality sound recording set up for home that I could get work done on with a small initial financial outlay of cash. I initially found that using USB mics were almost impossible to use with anything but "podcasting" and integrating pro quality mics - or mics with an XLR connection - with additional hardware that was only marginally supported at best - makes it difficult to consider Linux as a device for recording audio in a multitrack format in a manner that one may consider pro level.

In my opinion - if one has the means - recording audio using Mac hardware and Pro Tools software - with the integration of hardware that allows the use of professional mics - is a preferred method of recording audio at home or in a professional studio, especially when it becomes necessary to record multiple tracks simultaneously.

I never stated that it was impossible - as some on the internet have had great success using Linux as a recording platform - but at times utilizing JACK can be frustrating with hardware that may not be recognized at all by JACK but fully operational otherwise by the OS.

---

### Post by steveneddy on 2011-02-02
I would also like to add:

After reading the OP's original post I would recommend to the OP that he/she try Ubuntu Studio if simply trying to get JACK running correctly. JACK is installed by default in Ubuntu Studio edition and should be the latest version of JACK.

Another point I would like to make is that the recording community regards Ubuntu Studio 8.04 to be a better version of Ubuntu to use for recording due to the fact that it uses the -rt kernel - seemingly performing better than the -preempt kernel that is offered by the latest version of Ubuntu Studio.

---

### Post by mango42 on 2011-02-03
Bbbbut, if a complete non-computerate, addled old muso like me can get it all working (thanks largely to all the dedicated, knowledgeable and very helpful posters here!) then I don't see what the issue is, beyond not following instructions to the letter.

Sure, Hardy Heron was great but very difficult to get what you call bleeding edge technology working (eg: some recent firewire interfaces like Focusrite). I would say from nearly a year trying that Lucid Lynx Studio is at least on a par with professional systems on other OS's and in many cases, superior - particularly in the matter of ease of use - once configured properly.

If you want to spend countless $thousand$, fine; go ahead and lock yourself into proprietary systems but for purely home/hobby/semi-pro use with no material return (or overheads beyond being fair to the programmers!) in sight, Linux audio provides everything needed - just add patience, assiduous research and above all, humility and gratitude to all the brilliant programmers who provide these tools purely for the pleasure of doing so...

As for the preempt vs realtime issue, most stuff runs fine on the former - from what I understand (remarkably little really :), realtime is only needed for coping with fancy multichannel hardware and for those of us with high outboard demands like 8 port MIDI running alongside 8 channel audio on ancient, inappropriate laptops that need IRQ/process steering.

Having said that, it doesn't take much research to get -rt working fine in Lucid Studio - and the rewards of getting it all working are immense, IMO. I've been fooling around with music software since Atari ST days and it has never, *ever* been as pleasurable, smooth, flexible, deliciously anarchic and *downright convenient* as it is now on Lucid Studio.

YMMV ;-)


:guitar:

ps: greetings to Iota Geminorum from the Cassiopaean contingent of the Galactic Federation now taking up the very last grandstand seats just outside Earth orbit ;-)

---

### Post by cchhrriiss121212 on 2011-02-03
Please stop posting misinformation, steveneddy.
> additional hardware that was only **marginally supported at best** - makes  it difficult to consider Linux as a device for recording audio in a  multitrack format in a manner that one may consider pro level.
Some devices are not supported, but there are plenty of options out there for USB/Firewire/PCI with full support. All you need to do is a bit of research on what to buy first.
> at times utilizing JACK can be frustrating with hardware that may not be  recognized at all by JACK but fully operational otherwise by the OS.
What hardware are you specifically referring to here? If the system can use a device, then jack can use it as they are both relying on ALSA.

> Another point I would like to make is that the recording community  regards Ubuntu Studio 8.04 to be a better version of Ubuntu to use for  recording due to the fact that it uses the -rt kernel - seemingly  performing better than the -preempt kernel that is offered by the latest  version of Ubuntu Studio.
What community is that? 8.04 is soon to reach end-of-life and will have software that is 2 years old, I would not recommend it to anyone. Also an rt kernel can be installed on any version of Ubuntu you like, in addition many users may not even need an rt kernel, the low-latency and generic kernel are producing very good performance nowadays:
[https://wiki.ubuntu.com/RealTime#Natty%20Benchmarks]("https://wiki.ubuntu.com/RealTime#Natty%20Benchmarks")

A Mac is a good choice for audio work if you have the cash for it, but to post it as a solution here along with various incorrect statements is not helpful to anyone.

---

### Post by AutoStatic on 2011-02-03
> **steveneddy said:**
> I was merely stating my opinion that I found Jack with Ardour was very frustrating to get working for me - I was trying to get a professional quality sound recording set up for home that I could get work done on with a small initial financial outlay of cash. I initially found that using USB mics were almost impossible to use with anything but "podcasting" and integrating pro quality mics - or mics with an XLR connection - with additional hardware that was only marginally supported at best - makes it difficult to consider Linux as a device for recording audio in a multitrack format in a manner that one may consider pro level.Hello steveneddy, so because *you* had a hard time setting up JACK and Ardour this "makes it difficult to consider Linux as a device for recording audio in a multitrack format in a manner that one may consider pro level"? And what do you mean exactly with "with additional hardware that was only marginally supported at best"? If you investigate a little bit before acquiring a decent pro-audio soundcard you will find out there's a vast number of soundcards that is fully supported, from FireWire and USB to PCI.

> **steveneddy said:**
> In my opinion - if one has the means - recording audio using Mac hardware and Pro Tools software - with the integration of hardware that allows the use of professional mics - is a preferred method of recording audio at home or in a professional studio, especially when it becomes necessary to record multiple tracks simultaneously.My opinion differs on this matter, my preferred method of recording audio at home and with the band is a PC with FLOSS tools. But discussing this would be pointless, we're both entitled to our opinions :)

> **steveneddy said:**
> I never stated that it was impossible - as some on the internet have had great success using Linux as a recording platform - I'm one of those. I use it exclusively and I'm quite happy with it.

> **steveneddy said:**
> ...but at times utilizing JACK can be frustrating with hardware that may not be recognized at all by JACK but fully operational otherwise by the OS.JACK is a sound daemon, not a driver stack. So JACK doesn't "recognize" soundcards, it merely acts as a throughput to the different driver stacks it can talk to (ALSA, FFADO). If JACK doesn't work with your soundcard something is not configured well. That's what imho this forum is for, to get that soundcard to work with JACK (given it is supported by the aformentioned driver stacks), not to express your preference for closed source proprietary platforms and software.

> **steveneddy said:**
> Another point I would like to make is that the recording community regards Ubuntu Studio 8.04 to be a better version of Ubuntu to use for recording due to the fact that it uses the -rt kernel - seemingly performing better than the -preempt kernel that is offered by the latest version of Ubuntu Studio.Then you've been informed by a different recording community I'm part of I guess. I wouldn't recommend an almost three year old release that will make it nearly impossible to run a lot of recent software. Besides, a lot of the rt patchset has been assimilated (resistance was futile) in the mainline kernel, so current non-rt kernels perform quite well for doing audio production.

Sorry if I'm being a bit harsh, normally I don't react to posts like this. But your high postcount triggered an eagerness to reply. I do like to point out that I respect your decision to get yourself the tools you feel comfortable with, to each his own. I just think this is not the right place to express that preference though as we're all trying our very best to promote making music with GNU/Linux as much as possible here.

Best,

Jeremy

---

### Post by sgx on 2011-02-03
Its not good form for one to post about wanting to record economically,
and then quickly turn around and buy the most expensive of alternatives, instead of patiently joining the many successful configuration stories available in the search engines, and forum queries. The process of learning how to configure systems, has inherent value, and carries over into other pursuits. There are professional situations where one might need to make a hurried expensive purchase due to time constraints, but when one is also pondering usb-mics for professional recording... :p ;)

---

