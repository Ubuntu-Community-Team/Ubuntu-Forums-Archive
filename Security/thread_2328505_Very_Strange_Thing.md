---
title: "Very Strange Thing"
date: 2016-06-21
forum: Security
---

### Post by tom241 on 2016-06-21
Hello, i would like to ask you about a thing which is related to Ubuntu's security.

I have been using ubuntu for a long time but i has never happend to me before the thing is: 

2 days ago when i was programming i left my room for a while and when i came back , the window i had opened (IDE) was closed (minimized) , i was impressed how could it happend when i was sure i left it oppened , later on i started to be nervous because i still didnot get how could it get closed , i started to think about that someone has gained remote access to my computer and it would hurt me alot , i started to google all the things how to check whether someone has connected to my pc etc.. i didnot find anything suspicious i used sudo last and commands like this , but i still couldnot remove this idea from my mind i still analyzed it etc , i didnot have SERVER on my pc and i didnot allow the SSH to run , i also didnot install software like team viewer i have read that there are still some ways to gain the remote access but i am sure i didnot install anything that could harm my pc , i had just Sublime text installed and some basic official programs like Code Blocks and Wine nothing else , i still couldnot solve this , but i finally realized that the best thing  to make myself sure is to reinstall the system (yes maybe im a bit paranoid) so i reinstalled to ubuntu gnome [http://www.ubuntugnome.org/](http://www.ubuntugnome.org/) i chosed : erase disk and install ubuntu gnome everything was fine but few minutes after installing the new system the exactly same thing happend , exactly the same thing , so i wanted to make sure whether the ubuntu might sometimes close (minimize) the windows unexpectedly or so , or is it possible that someone has infected my "harddrive" in the past without my knowledge and even if i reinstall the system and erase the disk the virus is still binded to hardware and it allows someone to connect to my system ? haha this is very strange and i dont believe it but i just wanted to share this , can someon explain me what is this ? how could this happen? or even if it could happen? maybe i was very tired but i cant sleep because of this. thanks

i cant even image that someone would gain the remote access to my computer , to all my files and would copy them or so so this is why i solve it that much

---

### Post by TheFu on 2016-06-21
All OSes have issues.  WINE, if used, allows many of the same malware created for Windows to impact Linux systems.
X/Windows is also a liability.  The security for X is pretty minimal on a LAN, yet almost every desktop running Unix or Linux uses it.

Security is about having different layers of protection, so that a single layer failing doesn't break the security.

The best security tool that I know is versioned backups stored on a different machine.  Then you could compare all the files on the questioned system against those in the backups from yesterday, last week, last month ... and **Know** what changed.

There are all sorts of known ways to break into an unpatched system. There are probably 50-150 ways which aren't published.

Security is not a checkbox. It is a complicated, process-based, effort that changes constantly as the attackers get sneakier and smarter.

I install ssh on every single system that I run (except containers), but it doesn't allow passwords for authentication.

You should be paranoid. They are out to get you, me, everyone - all the time.  I've been hacked a few times over the years.  The first time, I didn't have any versioned backups. Wiped the disk with the help of a professional UNIX admin.  The 2nd time, I had versioned backups and was able to compare the entire file system, seeing exactly what had been touched by the attackers.  I was extremely confident in what they had and had not touched.  Quickly determined how they'd gotten in and saw their attempts to gain root.  They came in through a daemon account with only 1 program to be run - somehow, they got a shell from it. 

This all happened many years ago, when the internet was just starting to be a dangerous place. Their hack was not successful beyond gaining access to the system. No other corruption was discovered.  I only took it off the internet for about an hour to clean things up. Didn't even reboot it.

The first thing I'd do on your box is to create a new userid and see if that didn't make this issue go away.  It is likely some IDE setting that was tripped.  I don't use IDEs. To me, Linux is the IDE - 1 term for vim, 1 for debugging, and another for make/builds. A slide of the mouse to change windows, up-arrow <enter> - ... 

BTW, Teamviewer's user account DB was reported as hacked a few weeks ago. With a Linux system, there just isn't much need for 3rd party tools like that. Trivial to roll your own.

---

### Post by tom241 on 2016-06-22
thanks for reply :) but can someone hack me right after i install the system haha ? i just reinstalled and it happend . so i guess it wasnot real.

---

### Post by ventrical on 2016-06-22
[s]What version of [U]ubuntn-gnome are you using?

Regards[/s]


[/U]What version of ubuntu gnome are you using?

Regards..

---

### Post by TheFu on 2016-06-22
> **tom241 said:**
> thanks for reply :) but can someone hack me right after i install the system haha ? i just reinstalled and it happend . so i guess it wasnot real.

Sure.  There are always hundreds of unknown hacks out there, plus you haven't described the network security deployed at all.  

Most routers need to be patched weekly just like normal systems, but we're lucky of the vendors make new patches/firmware available yearly for the first 3 yrs. After that, vendors don't provide **any** firmware updates for their routers.  To combat that, many people move to aftermarket firmware like dd-wrt, openwrt, tomato, pfsense .... each has their own issues.  dd-wrt's last "stable" release is over 8 yrs old.  There have been lots of bugs, critical, bad, terrible, bugs found in the Linux kernel and tiny tools that are part of their userland tools since then.  Short of rolling my own NetBSD (or is it freebsd?) router, I really don't have any good answer to remain patched, secured, at the network layer.  Buying a $250 home router doesn't solve this issue either, but for $150, you can buy a PCEngines raw device (get an APU model) and load BSD or a lite version of Linux, configure it as a router and perform weekly patches like you do for all your other systems. These are not plug-n-play devices.

There is an Ars article about this. Saw the author speak a few weeks ago on the topic and I need to swap out  my router ASAP. 
* [http://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/](http://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/)
* [http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)

* PCEngines: [http://www.pcengines.ch/apu.htm](http://www.pcengines.ch/apu.htm) - be certain to get the Intel NICs plus the case and PSU for a complete router box.  

A Ubiquiti router might be a good, cheap, option too. I've been impressed with their patching of WAPs, but haven't seen their routers.

About 18 months ago, I took a completely patched Ubuntu Server to a hacker conference for use in a **Capture the Flag** competition. This server was NOT the target, rather, it  was my desktop to use for my attempts to CTF.  In the 4 hrs I was on that network, the box wasn't running a full DE, just minimal X, not running any public services except openssh-server on the LAN, someone hacked in, changed the password file, and removed my account.  This box was NOT on the internet, so it was one of the other competitors who hacked in.  I was using a yubikey+pin for logins - that's about 30 characters for the password (no special PAM module loaded) and the yubikey was never off my person.  I wasn't sleeping at the same hotel, so they didn't hack it overnight.

Did I mention the machine was fully patched 1 day earlier with 14.04?

So - yes, your freshly installed Ubuntu box **could** have been hacked.  As unlikely as this is, it is still a possibility.

---

### Post by bashiergui on 2016-06-22
> **TheFu said:**
> About 18 months ago, I took a completely patched Ubuntu Server to a hacker conference for use in a **Capture the Flag** competition. This server was NOT the target, rather, it  was my desktop to use for my attempts to CTF.  In the 4 hrs I was on that network, the box wasn't running a full DE, just minimal X, not running any public services except openssh-server on the LAN, someone hacked in, changed the password file, and removed my account.  This box was NOT on the internet, so it was one of the other competitors who hacked in.  I was using a yubikey+pin for logins - that's about 30 characters for the password (no special PAM module loaded) and the yubikey was never off my person.  I wasn't sleeping at the same hotel, so they didn't hack it overnight.

Did I mention the machine was fully patched 1 day earlier with 14.04?Yah I always wipe and reinstall after a hacker conference - phones and laptops. I'm bringing burner phones this time. Were you out of the competition completely or did you get back in? Did you figure out how they got in?

---

### Post by TheFu on 2016-06-22
> **bashiergui said:**
> Yah I always wipe and reinstall after a hacker conference - phones and laptops. I'm bringing burner phones this time. Were you out of the competition completely or did you get back in? Did you figure out how they got in?

There was only an hour left and I had a talk to give, so I powered off and wiped it that night back in the hotel.
Nothing replaces know-you-can-restore, versioned, backups.  Didn't have time to so any analysis.  At a different con, they came in via bluetooth.  I put my smartphone in a faraday cage at these places.  

At CarolinaCon last year, they showed how to hack android and i-whatever devices. Live demonstrations.  It is just scary how much some people are tied to these insecure devices.  The only sensitive thing i do on these is email and I need to stop doing even that. No chat, no social networking, definitely NO banking or financial anything. Just too dangerous, IMHO.  Average people don't know how bad it is. Scary doesn't really cover it.  It all comes down to the libraries being used on these devices not being updated. Over time, lots and lots of old, broken, libraries are full of hackable bugs. Worse, lots of app developers don't bother to pull the old, broken packages, so they are being pushed years after the ad-network libraries inside them have known, huge, critical, bugs being exploited in the wild.

The same can happen with all programs, but smartphones tend to be on the internet without much protection. Most desktops are behind a router, so attacks tend to be email attachment or click-n-run style.  Disable flash and javascript in those tools.  Run your browser using firejail in private mode when you need them.  

It is a dangerous world out there.

As a programmer, be certain to learn about the OWASP Top 10 list for your programming languages. Don't allow admin access to the broad internet, limit that to just the subnets which need it, or localhost so you use an authenticated ssh tunnel to get at it.  VNC has this option, but I'm amazed at how many people don't know or simply decide not to use it.

---

