---
title: "Possible virus in Ubuntu boot? Help appreciated."
date: 2009-09-09
forum: Security
---

### Post by ZehnTech on 2009-09-09
Earlier today, my office was hit by some kind of nasty virus. 
Four computers, one windows XP machine, two Windows 7 machines and my laptop with the newest version of Ubuntu all shut down and since then automatically shut down upon booting. 
 
All the machines can boot into whatever variety of safe mode they have and so far, no antivirus program has been able to identify the problem. My linux machine doesn't have one, as I understood Linux was immune to most forms of malware. 
 
I can get to my recovery menu, but if I try to boot normally it goes through the load bar and either immediately changes to the shut down bar and shuts down or just shuts down as soon as the load bar has completed.
 
Does anyone have any idea what might have caused this? If so, any solutions other than backing up what I can and reinstalling?
 
Thanks
 
ZT

---

### Post by phillw on 2009-09-09
Boot your machine with the LiveCD (Usually the one you use for install) - That should give you a clean machine. When you have access to your machine things can be progressed.

IMHO, I can't see how u and windows machines managed to get hit with what sounds like a root-kit. Is it a 100% Ubuntu install, or do you have windows on it as well ?

But, see how booting with the liveCD goes.

Phill.

---

### Post by ZehnTech on 2009-09-09
Booting with the Live CD won't give me the graphic interface though, right? I can access my root menu and suchwhatnot through recovery mode, so I'm not sure how the Live CD can help me. If you can be more specific as to what you mean, I'd appreciate it. 
 
Thanks.
 
ZT

---

### Post by phillw on 2009-09-09
Select the option to try out ubuntu without installing -that will give you the full Graphical interface - it'll just run a bit slow, as it's usuing the CD and not a hard-drive.

**Try Ubuntu without any change to your computer**

---

### Post by ZehnTech on 2009-09-09
Thanks for trying to help, Phill, but I'm looking for possible causes, not a way to access my data. My partner is fairly experienced with Linux and he has no clue. We know how to back up my data and deal with any run of the mill Linux concerns. But this problem and a permanent solution are beyond us. 
 
Thanks again, though, for your efforts.

---

### Post by phillw on 2009-09-09
That Is why I wanted you to boot to live CD - then you could use chkrootkit & rkhunter to track down some information ....

without some information no-one can assist in finding out how & why it happened - your new install could quite easily go the same way UNLESS you take steps to prevent it.

---

### Post by The Cog on 2009-09-09
I wild thought - try booting with the network unplugged
 / wireless disabled. It might just be that something in the network is still transmitting something that causes the machine to shut down as soon as the network comes up. 

Also, AV companies might be interested in seeing one of those machines.

phillw is right - the live CD lets you try a full GUI, although it won't load proprietary drivers like nvidia acceleration or wireless drivers.

---

### Post by ZehnTech on 2009-09-09
So, an update. We went into my computer with a juntu recovery CD. The startup file contained only an exit line, somehow. We rewrote the file, the linux machine booted up but my desktop file is gone. 
 
The windows machines still only run in safemode. No antivirus I've run can find anything. Tried mbam, avast, spybot even. 
 
The problems still occured when disconnected from the network. This is pretty f*ed. Haha.
 
Backed up my pertinent data and am reinstalling Jaunty now. I'll let you know if it happens again.

---

### Post by phillw on 2009-09-09
This one is still in beta ... but seems promising

[http://rootrepeal.googlepages.com/](http://rootrepeal.googlepages.com/)

If the others are finding zilch - You have nothing to lose trying it !!

Stinger, as a standalone, is also one to try.

It's a while since I've been 'a hunting' on windows, but I do recall this company being pretty decent....

[http://www.sophos.com/products/free-tools/sophos-anti-rootkit.html](http://www.sophos.com/products/free-tools/sophos-anti-rootkit.html)

Phill.

---

### Post by pbulteel on 2009-09-09
You could run the Ubuntu Live CD on the Windows machines, then mount the C, etc drives from that machine and check them through the Linux environment (virus scan, etc.) You may have a rootkit on the Windows machines that is still loaded even in Safe Mode. 

However, you mentioned that all 4 machines shut down at the same time?

-P

---

### Post by theozzlives on 2009-09-09
You know it's beyond me why people ask for help, then don't do as advised. If you have a Linux expert, have him fix it.

---

### Post by ZehnTech on 2009-09-09
First off, Ozzlives, there's no need to be rude. If you don't have anything worth saying, don't waste my time. Second, I wasn't asking for *obvious* solutions, I was introducing a problem to see if anyone else had encountered it and what the problem might be. Go be a troll elsewhere.

pbulteel, 

Thanks for a helpful, productive answer that engages my problem. Three of the four computers shut down within minutes of each other if not simultaneously.  The other was off already. 

We discovered one solution that can fix the problem if anyone else encounters it, Juntu can be used to delete the old system restore files. One of our windows 7 machines has been operating normally since system restore was turned off and the old restore files manually deleted.

---

### Post by theozzlives on 2009-09-09
I've been silent up to now because you were given sound advise. Advise that you ignored. If you and your Linux expert can fix it, let us help people that need help. I'm glad you got most of your boxes up and running.

---

### Post by rookcifer on 2009-09-09
So, let me get it straight, the OP is alleging that some virus entered his network and wiped out all of his Windows *and* Linux boxes simultaneously.  Sorry, but I am skeptical that a virus would work on both platforms at once.  There must be another explanation, but not enough info was given to make any determination as to what really is going on.

---

### Post by jrusso2 on 2009-09-10
> **ZehnTech said:**
> So, an update. We went into my computer with a juntu recovery CD. The startup file contained only an exit line, somehow. We rewrote the file, the linux machine booted up but my desktop file is gone. 
 
The windows machines still only run in safemode. No antivirus I've run can find anything. Tried mbam, avast, spybot even. 
 
The problems still occured when disconnected from the network. This is pretty f*ed. Haha.
 
Backed up my pertinent data and am reinstalling Jaunty now. I'll let you know if it happens again.

Probably not a virus but some kind of Trojan.  I can see how this could erase stuff in /home but wondering how it got to the boot up files.

Its an interesting case.  One of the more interesting ones I have seen here.  Maybe you should check the logs and see if there is a clue in there.

---

### Post by phillw on 2009-09-10
There area couple of CRITICAL flaws in Microsoft O/S (They call them CRITICAL) - A drive by could quite easily have nuked all the windows machines. It looks quite grim.

[http://www.microsoft.com/technet/security/bulletin/ms09-sep.mspx](http://www.microsoft.com/technet/security/bulletin/ms09-sep.mspx)

But, said beastie should have zero effect on a  secure (i.e. not running as a server, so not listening for incomming connections) machine.
I hadn't realised things were quite that bad, but the windows ones do, indeed, look pretty darn serious.
The only thing I can think of  is if the linux box was connected to a compromised system and thus the attacker could easily tunnel over onto the Linux box.

Just my tuppance worth.

Do report back what you find, it's of interest to me and should be to others - people do run linux/windows systems.

Hope you sort out your headache soon.

Regards,

Phill.

---

### Post by The Cog on 2009-09-10
I agree with phillw - I can't add anything useful, but I'm very interested to hear more as you discover it.

---

### Post by sasho_zl on 2009-09-10
4 machines shutting down in minutes of each other and running different OS?! Dude, check your electricity...

---

### Post by bobince on 2009-09-11
+1 on the power suggestion. A hard power-down can certainly result in corrupted files causing a failure to boot on Windows. The chances of a 'virus' doing this simultaneously to machines running different OSs seems minimal.

---

### Post by some-what-Gnu-2-networks on 2009-12-01
Did the Ubuntu computer have Wine installed? It appears that this was a mainly Windows network making it seem likely that Wine was installed.

---

### Post by teward on 2009-12-01
Okay, I know this is an Ubuntu forum, but I'm also a Windows technician.  Granted, not a super-experienced one, but I've had my share of super-ultra-nasty viruses.

A quick question to the poster of this thread:  Do the computers require network access in order to boot?  Specifically, the Windows computers... do they need network access in order to boot?

---

### Post by lisati on 2009-12-01
Another thought: the way something nasty can affect multiple OSes is through the boot sectors and scrambled partition tables.

---

### Post by teward on 2009-12-01
> **lisati said:**
> Another thought: the way something nasty can affect multiple OSes is through the boot sectors and scrambled partition tables.

This is true, and would explain the auto-crash every time it boots, with or without network access.

---

### Post by OpSecShellshock on 2009-12-02
Wait, one of them was already powered off at the time of the outage? How could that have been written to?

---

### Post by BkkBonanza on 2009-12-02
Have you ruled out sabotage by a disgruntled user or employee? One guy in a room with a few computers could doctor up simultaneous cross platform trouble.

---

### Post by iamgeniusrnti on 2009-12-02
> **BkkBonaza said:**
> Have you ruled out sabotage by a disgruntled user or employee? One guy in a room with a few computers could doctor up simultaneous cross platform trouble.
 
Yea... something isn't adding up...

---

### Post by golusweet on 2009-12-02
Check your hardware.

 Windows viruses won't infect ubuntu.

  It should boot normally.

---

### Post by Some Penguin on 2009-12-02
Sounds like somebody just mangled the init scripts, if XP Safe Mode et al boots fine.  That'd be pretty easy sabotage if somebody had root privileges (and if one can get a command line from grub2, it's usually not hard to get root privileges -- passing init=/bin/sh as an argument to the kernel to skip the normal boot scripts and just jump straight to a root shell for one way).  Adding init=/sbin/reboot or adding a reboot/shutdown command to one of the init scripts would make a 'nix reboot until such command was bypassed (e.g. boot with live CD), located and eliminated -- no 'virus' required, 'just' root privileges.  There's probably something similar that could be added to the Windows startup commands.

If somebody dropped a root kit, there's not much point to having the machines spontaneously shut down or reboot, because then the root kit isn't very useful.  Granted, it could be gross incompetence (didn't mean to cause rebooting) or pure vandalism.  

It'd be possible to write a malicious BIOS update that would cause cross-platform mayhem, but there'd be no reason to write one that wouldn't also affect 'safe mode' boots.

---

### Post by doas777 on 2009-12-02
kinda sounds like a network bourne attack, (if any of it can be taken at face value. OP, you gotta admit, the circumstances as described are pretty unbelievable, unless the problem is power or network.)

if it was malware, it would have to be a worm. viruses take time to spread (and rely on common application software to infect), and trojans are pretty much isolated to the box they are on. additionally the likelyhood that any kind of crossplatform worm exists is minimal, so I'm inclined to look at the common factor: they are all connected to your network.

---

### Post by Sorwen on 2009-12-07
I just wanted to add some things to keep in mind.  If the virus was date/time activated it could cause simultaneous problems.  Another thing is that a lot of viruses that hide like that are key loggers as well.  Part of the point of them hiding is so that they can collect information.  They then trash the computer(s) in an attempt to hid their tracks.  If you monitor network traffic off other than per each computer you might check your logs for around that time and see if anything unusual shows up.  I know very little on ubuntu/linux so I can't comment on the cross platform feasibility of that type of situation.

---

### Post by mr-woof on 2009-12-07
Has the ubuntu machine got access to windows shares and vice versa? Just trying to think of a way something nasty could move across to the ubuntu machine, wine possibly?

---

### Post by cariboo on 2009-12-07
The op hasn't been back since September 9th, so either they resolved the problem, or the system is still down. So we'll never know what really happened.

---

