---
title: "UBUNTU &amp; security"
date: 2008-11-13
forum: Security
---

### Post by aitch56 on 2008-11-13
I've been told that you don't need to install a firewall, antivirus or any form of security with ubuntu because it's the platform used by those who wriet the virus, trojan etc programs.  Is this correct?  If not what security programs do you recommend to run best on this particular platform?

---

### Post by Portmanteaufu on 2008-11-13
There's some truth to that, but it's not entirely accurate. It's true that the threat of a virus affecting your system is practically negligable when compared to the risk of the same thing happening on a Windows machine. Not only are the vast, vast majority of viruses not written to run on Linux, Linux has also been built in such a way that unless a program is run with root privileges, it can have relatively little lasting effect. Also, because so many people have their computer living behind a router, there's significantly less of a reason to have a firewall running on your machine; the router typically plays the role of the firewall.

With these things said, it's important to keep security in mind despite the fact that Ubuntu is inherently safer than Windows. Never run code you don't trust, and certainly don't do so with sudo. Use the system update feature frequently so that when possible security issues are addressed in your favorite software, you automatically have the problem fixed on your machine.

Enjoy not having to tithe your system resources to McAfee or Norton. :D

---

### Post by oilchangeguy on 2008-11-13
> **aitch56 said:**
> I've been told that you don't need to install a firewall, antivirus or any form of security with ubuntu because it's the platform used by those who wriet the virus, trojan etc programs.  Is this correct?  If not what security programs do you recommend to run best on this particular platform?

read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
and this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by doas777 on 2008-11-13
I would install a firewall frontend (I use firestarter), and I do install rkhunter and chkrootkit, to run occasionally, but no, you are essentially correct, you do not need the chorus of security software for ubuntu that you need for windows.

if you want to harden your box, install and run bastille and Harden-Environment. other than that, just be carefull

---

### Post by oilchangeguy on 2008-11-13
> **doas777 said:**
> I would install a firewall frontend (I use firestarter), and I do install rkhunter and chkrootkit, to run occasionally, but no, you are essentially correct, you do not need the chorus of security software for ubuntu that you need for windows.

if you want to harden your box, install and run bastille and Harden-Environment. other than that, just be carefull

as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant.

---

### Post by SleepingProphet on 2008-11-13
If you are sitting behind a router then you're generally going to be protected from most drive-by vulnerability scanners out there. This is not to say its impossible to hack a system behind a router, its just way less easy to do it automagically.

Generally there is very little malware for Linux because there are very few people running Linux as a desktop OS. Before any fanboys get offended, I mean in aggregate terms. See here:
[http://en.wikipedia.org/wiki/Usage_share_of_desktop_operating_systems](http://en.wikipedia.org/wiki/Usage_share_of_desktop_operating_systems)

I know Linux is getting more popular but its still like 1% of the desktop world.

Most malware is made to try and make money.
If you're trying to make money and you want to ensure a return on your investment of time developing and deploying the nastyware, are you going to do on Windows (90+% of the world) or Linux (1% of the world)?

---

### Post by SleepingProphet on 2008-11-13
holy moly, this forum is busy! One other point of consideration in favor of the "Linux = more secure" argument is this: On Windows a lot of the time malware rides into your system as part of some other program you downloaded and installed. Since the vast majority of the stuff you're going to install in Ubuntu comes to you via secure connection from secure repositories, there's a lot less chance for rogue code to get into your machine.

---

### Post by bodhi.zazen on 2008-11-13
> **SleepingProphet said:**
> If you are sitting behind a router then you're generally going to be protected from most drive-by vulnerability scanners out there. This is not to say its impossible to hack a system behind a router, its just way less easy to do it automagically.

Generally there is very little malware for Linux because there are very few people running Linux as a desktop OS. Before any fanboys get offended, I mean in aggregate terms. See here:
[http://en.wikipedia.org/wiki/Usage_share_of_desktop_operating_systems](http://en.wikipedia.org/wiki/Usage_share_of_desktop_operating_systems)

I know Linux is getting more popular but its still like 1% of the desktop world.

Most malware is made to try and make money.
If you're trying to make money and you want to ensure a return on your investment of time developing and deploying the nastyware, are you going to do on Windows (90+% of the world) or Linux (1% of the world)?

I do not buy that argument one bit. Security by obscurity is no security at all.

*nix is built from the ground up to be multi-user and secure, Microsoft trades "security" for "convenience". The open source community patches known bugs with some semblance of timeliness, Microsoft has left known vulnerabilities unpatched for decades.

---

### Post by doas777 on 2008-11-13
> **oilchangeguy said:**
> as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant.

unless you wanna run even the most trivial of services. besides firewalls protect more than just ports, but the full stack.

---

### Post by oilchangeguy on 2008-11-13
> **doas777 said:**
> unless you wanna run even the most trivial of services. besides firewalls protect more than just ports, but the full stack.

By default, Ubuntu includes a firewall, iptables

---

### Post by doas777 on 2008-11-13
> **oilchangeguy said:**
> By default, Ubuntu includes a firewall, iptables

yes, it does. funny that.

---

### Post by hyper_ch on 2008-11-14
> **doas777 said:**
> yes, it does. funny that.

however iptables has by default no rules and hence restricts nothing - which is good behaviour.

---

### Post by koenn on 2008-11-14
> **aitch56 said:**
> I've been told that you don't need to install a firewall, antivirus or any form of security with ubuntu because it's the platform used by those who wriet the virus, trojan etc programs.  Is this correct?  If not what security programs do you recommend to run best on this particular platform?
Re. the need for anti-virus, firewall, etc - see what the others have said.

Re "no need ... **because [Linux] is the platform used by those who write the virus, trojan etc programs**.", I'm pretty sure that's nonsense.
If you're going to write a program (virus, trojan, worm, malware script, ..., any other program), you're going to write it on Windows. Especially so if it's a compiled program, but even for simple scripts (some of the more famous email viruses/worms were written in VBscript; although technically you could create a .vbs text file on Linux, you can't run, test and debug it, cause it simply won't execute).

From an other angle : although the malware scene is getting more and more commercialized, there's still some ego and prestige involved in creating viruses, trojans,  etc. Imagine what an ego boost it would give and the prestige you would gain if you'd create a successful virus for the platform that has remained practically virus-free for 20 years.

---

### Post by cariboo on 2008-11-14
The only way a virus can be installed on Linux is by social engineering. The authot of the virus has to convince the user to install the malware as root or it will not be able to do it's job. 

Jim

---

### Post by 5nak3 on 2008-11-15
Ok I've spent a good few hours reading about Ubuntu and security, I decided to get a GUI for iptables, so i can check which ports are open without fuss.

But i am still not sure if a virus scanner is needed. I understand that it is essentially the users that allows for a virus to run, but my question is this:

Coming from a Windows background it has become second nature to scan anything i download, whether it be a jpeg, a video, a word document. Anything i downloaded I checked without fail.

right click -> scan with...

I understand that it is unlikely for a virus to be aimed at Linux users, but say if I download a sound file, a document, a video clip etc...how can i check to make sure the file is clean?

Obviously you make sure you trust your sources, but since all my contacts use Windows, they could pass on a file to me which is not clean, which i then may forward onto someone else. How could i make sure the file is clean?

Is there no virus scanner out there which you can invoke when needed to scan a file. 

From my understanding to have a scanner watching over the system in real time is nothing but a waste of system memory as the virus/vulnerability count is low/negligible but how can we check the files we download to ensure they are problem free?

I looked into avast, but the GUI was horrible and there wasn't a real time scanner as there is with the Windows version. So what other alternatives are good for Ubuntu?

---

### Post by mikewhatever on 2008-11-15
You may want to check AVG.
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by cariboo on 2008-11-15
You shouldn't worry about files you downloaded and use in Linux as a windows virus won't have any affect. If you decide to use the file in Windows, you still don't have to worry as you've already got a virus scanner installed and it will catch the virus.

Jim

---

### Post by jakupl on 2008-11-16
Go to (add/remove) and install clamtk witch is a virusscanner.
Go to terminal and enter

```
gksudo clamtk
``` 

this will opem clamtk as root. goto help - update signatures.

Now you can check any file for viruses.

---

### Post by 5nak3 on 2008-11-16
Hi guys, thank you all for your help so far. 

I have avast installed at the moment, considering CalmAV instead to tell you the truth.
Not too sure which is the better of the two, because Avast has worked fine for me on Vista, had a Nod32 subscription on XP, but this isn't a great concern at the moment. Will read up on this matter in the future.

In any case because I am now thinking of taking the laptop into University it is required that I have an AV running when connected to the university network (so as not to pass on any viruses etc...) 

Avast works as far as i can tell as an AV that you invoke as and when needed (great for me as that is what I want just to scan files before i send them).

The university requires active AV at all times (how they check this i don't know, but I'd rather follow the rules to avoid any problems), so essentially I need a real-time protection scanner. Does CalmAV actually do this, i couldn't find any information in that regard and I also couldn't find any information on AVG in terms of what type of protection it offers on Linux.

So basically the problem comes down to which, if any, of the linux anti-virus programs offer real time protection?

Such a stupid question I know because linux has no viruses in the wild, but it is a silly university requirement. Unless the whole I'm on linux argument is sufficient for them hehe.

---

### Post by jonobe on 2008-11-17
It's possible, probably, that for instance, you could have a virus attached to an email, and while it does not affect your machine (as it won't recognize an .exe file as an executable by default)  you may be able to pass this on in a FWD etc.  Your university would probably not thank you if you infected the site, but then went on to tell them 'if only you had Linux, you wouldn't have been infected - look, I wasn't.'
I use Clam AV, and it scans one file or the whole directory fine.  I don't trust AVG, as when I was a Windows user, a nasty Trojan got past it.  Norton then fixed it, but only after I gave them remote control of my computer while their technician removed it.

Check out Shields Up website and whatismyipaddress if you want to see an example of how exposed you are (or not) on your machine.  They know where you live...

---

### Post by aysiu on 2008-11-17
Antivirus is more of a placebo than an effective security measure.

Read more here:
[Does Ubuntu need antivirus?](http://www.psychocats.net/ubuntucat/does-ubuntu-need-antivirus/)

As for the notion that we need to protect Windows users, [this post](http://ubuntuforums.org/showthread.php?p=5222252#post5222252) explains well why Windows users who need protection won't be helped that much by us trying to protect them by not passing viruses on.

---

