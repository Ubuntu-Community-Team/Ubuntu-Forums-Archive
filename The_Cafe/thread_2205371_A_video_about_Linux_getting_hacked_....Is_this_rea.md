---
title: "A video about Linux getting hacked ....Is this real ?"
date: 2014-02-13
forum: The Cafe
---

### Post by linuxyogi on 2014-02-13
Hi,

Just found [this video]("https://www.youtube.com/watch?v=ja7hhHsZVNA"). 

He says its a fresh installation inside a VM. 

I guess he is using Xubuntu (I think its the Xubuntu logo on the start menu).

Although he doesnt demonstrate anything what he did from the remote computer but he "shows" that he manages to create and delete a file inside the Home folder.

AFAIK all ports are closed by default. What ufw does is it makes them stealth.

So I wan wondering how he managed to do what he did.

Do you think this is possible ? Or is this fake ?

---

### Post by mattlach on 2014-02-13
I'm not an expert in hacking and security, but the truth is this.

There is no system in the world that is unhackable, if you have sufficient time, talent, dedication and a budget on your side.

Most consumer level security revolves around just making yourself difficult enough to hack, that those who would compromise your system instead go pick on an easier target.

Governments with national security type information, and corporations with trade secrets, etc, don't necessarily have this benefit, as their information might be valuable enough to fund a team of very talented people to go ahead and break in.

Just look at Stuxnet, and what it did to the Iranian nuclear program, a network that wasn't even connected to the outside net.

There are many people out there that are foolish and believe Linux/unix and even OS X to be unhackable or immune to viruses and malware.   Nothing could be further from the truth.  Every system ever made by man, regardless of operating system or running programs in vulnerable to some extent or another.  its just up to us to make ourselves more difficult targets by making wise choices, and paying attention to the security of our networks, as well as looking out for social attacks.  (People are usually the weakest link.  It doesn't matter how secure your system is, if you can trick a person into circumventing it and giving you data)

Just some thoughts.

---

### Post by mikewhatever on 2014-02-13
I am not quite sure what you are asking. 
Are you wondering how he got it installed in a VM, and connected to it? If so, then that's what VMs are for - nothing extraodinary here.
What exactly do you suggest that video proves?

---

### Post by Frogs Hair on 2014-02-13
Hacking Linux is of course  possible but, without knowing what was done it's impossible to know if it's an FYI or FUD video.

---

### Post by mips on 2014-02-13
Without any details it's kinda pointless debating this.

---

### Post by linuxyogi on 2014-02-13
> **mikewhatever said:**
> I am not quite sure what you are asking. 
Are you wondering how he got it installed in a VM, and connected to it? If so, then that's what VMs are for - nothing extraodinary here.
What exactly do you suggest that video proves?


 He specifically says that he is using a **fresh installation** on Linux inside a VM. Which means he has not opened any ports. Even if its inside a VM afaik one needs to open ports so that a remote PC can connect. 

> **Frogs Hair said:**
> Hacking Linux is of course  possible but, without knowing what was done it's impossible to know if it's an FYI or FUD video.

Yes thats really frustrating. I have no interest in learning hacking but if buy a second computer I will at least once install Kali Linux and do some penetration testing of some other major Linux distros including Ubuntu and find out myself.

---

### Post by Portaro on 2014-02-13
He can simply put a file with mv command on the folder of /user eheh, its impossible to know if this is a real job or joke and I think honestly why the windows is on the same path at all video time ?

Its impossible know if this is a real hack method or a simply discourse about some.

---

### Post by david98 on 2014-02-13
In my opinion that video is impossible to be proven if it is legitimate. I have practise a little bit pen testing over the years and yes giving time and determination any system can be hacked. It does not matter how secure your system can be it all depend's on the knowledge of the person in front of the keyboard. But the question is is linux secure and the simple answer is yes highly secure especially for the end user who and why would someone bother to try to penetrate joe blogs's home computer it is a a lot of work for little or no gain. People who want to steal your details for financial gain would much rather just skip a computer with linux on it and concentrate on ones that take little or no effort at all therefore gaining thousand's if not ten's of thousands more details in the time it takes to gain remote access to a linux system. Bottom line no system will ever be 100% secure.

---

### Post by sammiev on 2014-02-13
If he would have made it to the root instead of just the home directory it would have made things a little more fun.

Any system is hackable, some are just easier than others.

---

### Post by Old_Grey_Wolf on 2014-02-13
> **Frogs Hair said:**
> Hacking Linux is of course  possible but, without knowing what was done it's impossible to know if it's an FYI or FUD video.

> **mips said:**
> Without any details it's kinda pointless debating this.

+1 to both.

---

### Post by sffvba[e0rt on 2014-02-13
I call BS.

---

### Post by deadflowr on 2014-02-14
> **not found said:**
> I call BS.

probably is, but I want to believe in magic.

---

### Post by The Cog on 2014-02-15
I also call BS. He has comfigured the Linux PC to accept incoming connections. He doesn't say what sort though. He probably thinks that SSH is hacking.

---

### Post by Old_Grey_Wolf on 2014-02-15
The video is over three years old! 

The only comment was from the video poster himself! 

Edit: The video poster had 2 other videos. They were also not about computer security.

:lolflag:

---

### Post by sammiev on 2014-02-15
> **Old_Grey_Wolf said:**
> The video is over three years old! 

The only comment was from the video poster himself! 

Edit: The video poster had 2 other videos. They were also not about computer security.

:lolflag:

Well I guess post # 11 is correct! :popcorn:

---

### Post by bashiergui on 2014-02-15
I learned a few truly useless things from that video:

1- He is a mouth breather
2- He can't spell "yourhacked"
3- He figured out how to create files on the command line. 
4- He has not figured out how to size his VMs :(

Beyond that it's just a guy talking out of his ass on video.

---

### Post by pqwoerituytrueiwoq on 2014-02-15
anyone could fake that using ssh, and yea that looked like a xubuntu/xfce default desktop
without knowing for sure what was done, nobody can be sure so debating is pointless and a waste of time much better spent curing the common cold or making a cat purr
that is from 2010, assuming he did exploit a real vulnerability it is probably been patched by now

step one don't use a weak password to guess if you are running a ssh server
step 2 don't set a root password (password is required for root login, but if there is no password there is no correct password)
if root is the only known existing username and there is no password for root hacking becomes significantly harder as you need a valid username to even begin to hack in (you can get a username from uploaded screenshots usually)

---

### Post by 1clue on 2014-02-16
I can't believe this is where the thread has gone.

While the video is not even slightly convincing, the threat of being hacked is extremely real, and you don't necessarily need an open port.

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

The fact that that site exists proves that Canonical, at least, knows that Ubuntu can be hacked even if most of the forum members deny it as though their life depended on it.  While most of the CVEs on that list have patches and Ubuntu should be relatively safe, you have to consider a few things:
[LIST=1]
[*]The patch comes out after the exploit is known.
[*]It takes awhile to come up with a patch.
[*]It takes awhile for everyone to apply the patch.
[*]Some of the malware transforms itself over time, meaning that defense against it might not be bullet-proof.
[*]The patch fixes the hole, but does not repair damage on a system where the exploit was used.
[*]There are lots more points, and if you think about it I'm sure you can come up with some of them.
[/LIST]

Now, regarding things NOT handled by that site:
[LIST=1]
[*]Most malware happens because a user is careless and clicks on a link, or performs some other action which makes them vulnerable.
[*]It doesn't matter what OS you're on, if you have a careless or uneducated user you just can't protect the system against that.
[*]If the user has superuser access then your system cannot possibly be protected.
[*]I've been using Linux since the 90s.  I've been hacked multiple times.  Each time I learn a bit more.
[*]In spite of what the guy in the video says, there are all sorts of reasons why someone would hack a Linux box.
[/LIST]

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by linuxyogi on 2014-02-16
> **1clue said:**
> 
[LIST=1]
[*]I've been using Linux since the 90s.  I've been hacked multiple times.  Each time I learn a bit more.
[/LIST]


How did you realize that someone hacked your system ? Files got deleted ? 

Did you keep any port open ? 


I am behind my router's firewall. I checked at grc.com and found all ports are stealth but when I do

```
dmesg | tail
``` I find ufw blocking multiple incoming connections which means the router's firewall is not good enough.

---

### Post by 1clue on 2014-02-16
The indications are different every time.  I've maintained a lot of boxes over the years, and generally they are accessed by a bunch of people.  Even so some of my problems were on my own hardware, at home, in a supposedly secure situation with no open ports.

Back in the early days, people just used modems and you were looking at 2400 baud.  Linux was not sophisticated, nor were the attacks.  A noisy hard drive and nobody on the terminal was a good indicator for the first time, the thing started making racket when I wasn't using it, I logged in and discovered more than one active session.  Probably a brute force telnet attack.

I've had at least one brute force ssh attack, and in those cases yes ssh was open because it was a remotely administered server.  In one case (the one I know was ssh brute force) my system became a spambot and I could barely log in to shut it down.

I've had several cases when I knew of malware only because I'd installed nonstandard tools like tripwire.  Nonstandard in that it isn't automatically installed.  I started using these tools years ago, but it took me awhile to figure out how to configure them properly.  You have to, or it's not nearly as effective.

One time the guy was really good:  He covered all his tracks, except he removed the system logs and recreated them rather than the typical way of copying them to a backup and **cat /dev/null > /var/log/whatever**.  Tripwire noticed that the inode changed and when I did a reboot I noticed a fishy line during startup.  It wasn't /etc/init.d, but it was a file in a directory that one of my init scripts checks for and executes from, and that wasn't configured in tripwire.

Most of the times I've been owned, I don't know what caused it.  You can spend a few hours to figure it out, or you can wipe your system and get on with it.  I suspect some of these were user error.  Maybe an excel virus or whatever, and the script worked well enough on Linux.

That's another thing:  Operating as a normal user like you should keeps most of the malware from damaging your system, but it doesn't prevent something like a keyboard logger or spambot from working under some user's account.

---

### Post by 1clue on 2014-02-16
@linuxyogi,

Small office/home office (SOHO) routers are notoriously buggy.  To a determined black hat, most of them could just as well not have security at all.  The most common Linux-based SOHO router distros are not much better.  DD-WRT is terrible in my own personal experience.

The best solution is defense in depth.  That means multiple pieces of hardware and treating each outer layer as hostile to every inner layer, and treating each system as though they were exposed entirely on the Internet.

---

### Post by bashiergui on 2014-02-16
> **1clue said:**
> I can't believe this is where the thread has gone.

While the video is not even slightly convincing, the threat of being hacked is extremely real, and you don't necessarily need an open port.

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

The fact that that site exists proves that Canonical, at least, knows that Ubuntu can be hacked even if most of the forum members deny it as though their life depended on it.  While most of the CVEs on that list have patches and Ubuntu should be relatively safe, you have to consider a few things:
[LIST=1]
[*]The patch comes out after the exploit is known.
[*]It takes awhile to come up with a patch.
[*]It takes awhile for everyone to apply the patch.
[*]Some of the malware transforms itself over time, meaning that defense against it might not be bullet-proof.
[*]The patch fixes the hole, but does not repair damage on a system where the exploit was used.
[*]There are lots more points, and if you think about it I'm sure you can come up with some of them.
[/LIST]

Now, regarding things NOT handled by that site:
[LIST=1]
[*]Most malware happens because a user is careless and clicks on a link, or performs some other action which makes them vulnerable.
[*]It doesn't matter what OS you're on, if you have a careless or uneducated user you just can't protect the system against that.
[*]If the user has superuser access then your system cannot possibly be protected.
[*]I've been using Linux since the 90s.  I've been hacked multiple times.  Each time I learn a bit more.
[*]In spite of what the guy in the video says, there are all sorts of reasons why someone would hack a Linux box.
[/LIST]

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)All valid points. The fatal flaw is that the moron in the video demonstrated the point using FUD. He didn't even bother making up a lame hack, just basically said "trust me." Credibility is everything when trying to convince the world of a fact.

I am 100% positive that any box can get hacked given an attacker with enough time, resources & desire. But the guy in this video kind of proved the opposite. His ultimate message was "I don't know how to hack it so I'll make something up and post that as evidence." He tried to help but probably caused more harm than good.

---

### Post by linuxyogi on 2014-02-16
> **1clue said:**
> @linuxyogi,

Small office/home office (SOHO) routers are notoriously buggy.  To a determined black hat, most of them could just as well not have security at all.  The most common Linux-based SOHO router distros are not much better.  DD-WRT is terrible in my own personal experience.

The best solution is defense in depth.  That means multiple pieces of hardware and treating each outer layer as hostile to every inner layer, and treating each system as though they were exposed entirely on the Internet.


Which means a home user who maintains only 1 PC cant do much to protect himself. 

Frankly I am not sure but I have heard that PF (BSD) is superior to iptables. 

Again, I dont know for sure.

---

### Post by 1clue on 2014-02-16
I think the basic Linux network security is up to par with most operating systems.  Iptables and routing, all that.  Commercial routers with big price tags might offer a few more features, but that's not the point.

The SOHO router firmwares I've tried (most notably DD-WRT) have glaring bugs in the part that distinguishes them from basic Linux.

On top of that, SOHO router hardware is just not up to the task of being a VPN endpoint.  The best you could hope for is a pass-through and have a VPN endpoint on something more muscular inside.

You COULD do more to protect yourself, especially if you have an old box that's just sitting there and had two or more network cards in it.

---

