---
title: "No outbound firewall :( [rant]"
date: 2009-04-06
forum: The Cafe
---

### Post by Xbehave on 2009-04-06
On a default windows XP install, if a program got exploited or you run untrusted software, it will prompt you to allow it access to network.
On ubuntu, because of the lack of inbound exploits, there is no firewall.

In no way am i saying XP is safer or even that its firewall works, but:
*No application is 100% secure ( zero day exploits, closed source, known vulnerabilities,etc)
*Most malware doesn't need root, but does need to phone home
*The user should be informed of there security.

A well designed notification (nothing requiring a password or anything modal) with a couple of clever options would be all that is needed to protect users from:
*exploits in offline programs (openoffice is trying to access $URL:PORT , forbid,check against bad sites list¹,allow once,allow always)
*running bad scripts (terminal is trying to access $URL, forbid,check against bad sites,allow once,allow always)

¹This could check take advantage of Google's badsite list or a user compiled list.

Ofc if your sure you know what your doing, such protection could be disabled, but for most new users or security conscious users an outbound firewall (in place by default for new users) would really help lock down ubuntu and make us safer.

[http://brainstorm.ubuntu.com/idea/3704/](http://brainstorm.ubuntu.com/idea/3704/) is the solution, unfortunately due to the arrogance of many linux users i doubt it will be implemented any time soon :(

---

### Post by swoll1980 on 2009-04-06
There is a firewall.

---

### Post by smartboyathome on 2009-04-06
We do have one, called IPTables. All ports are closed by default.

---

### Post by Barrucadu on 2009-04-06
I was under the impression that, by default, the XP firewall doesn't block any outbound connections.

---

### Post by swoll1980 on 2009-04-06
> **Barrucadu said:**
> I was under the impression that, by default, the XP firewall doesn't block any outbound connections.

For the programs that are preinstalled it wont, but if you add programs like bitlord it will block them, and ask permission.

---

### Post by Tews on 2009-04-06
Try 
```
sudo ufw enable
sudo ufw default deny
```

You now have ports blocked by default...

---

### Post by BGFG on 2009-04-06
> **Tews said:**
> Try 
```
sudo ufw enable
sudo ufw default deny
```

You now have ports blocked by default...

Thanks Tews, i was about the ask the OP if he/she was high. This is the best uninformed rant i have seen in a bit.

as for firewall popups, i don't need to know everytime ufw blocks something. I just need to know that it's on and i trust that it works.

---

### Post by Xbehave on 2009-04-06
To the posts regarding iptables, i didn't originally realize that iptables even supported per application blocking at all. The reason I liked the XP firewall is because port based blocking only works on well behaved aplications all malware/exploited software can safely call home on port80. After some googling i came across " --cmd-owner /path/to/application" (it wasn't in man iptables honest!), it sure as hell wasn't in the majority of the tutorials i looked up.
While it does provide the technology needed, it still lacks the end user interaction: 
*If the computer has to block a program making an outbound connection, the user should be informed (at least the 1st time) that something is wrong (either with the application or with the firewall)
*Users should be able to allow application access **without** requiring root access (any exploit will only hit their user), while i think iptables **may** allow this, I wouldn't no how to start setting that up, so i guess most new users wouldn't. (OFC if the core firewall blocks access that would override any user decision.)

Remember that with sensible defaults, your average user wouldn't have to worry about opening ports for managed applications, only when "weird" stuff happens would they be asked what to do; openoffice/statups-scripts/etc accessing the network.

@smartboyathome, by default no ports are closed (as the firewall is off), but as very few services are running this doesn't matter. In practice it makes little different, but the usual states for ports are:
allow -> service responds 
unused-> nothing responds (this is what happens by default)
Deny  -> kernel responds with "closed" message

thx for the replies btw, i relize i didn't really go into why none of the current solutions don't cover what i said. its 
> but if you **add programs** like bitlord it will block them, and **ask permission**. 
that i was looking for

[rant]===============================================================================================================
> **BGFG said:**
> Thanks Tews, i was about the ask the OP if he/she was high. This is the best uninformed rant i have seen in a bit.
Wow thats the most uninforative reply ive seen in a while too.
ufw works on using basic iptables rules which employ port based blocking, which to all intense and purposes is USELESS, infact its worse than useless because people like yourself think locking down ports stops malware/spyware/hackers.
While locking down ports defends well against inbound traffic (not aswell as not running services which is what ubuntu does by default), and if used by routers (what iptables was designed for) can lock down legitimate services, it does **nothing** to stop malware/spyware/expliots, because they can always phone home on port 80.

>  i don't need to know everytime ufw blocks something. I just need to know that it's on and i trust that it works.
Obviously as you are so well informed about matters (ufw doesn't block anything, netfilter/iptables does most of the blocking) you are a security guru, and this doesn't apply to you, **but** us mere mortals think its nice to get a gui warning when programs stop working. As an uninformed moran i was under the impression that denying an application access to the network means something is wrong because i've either got bad firewall rules (due to not being a security guru) or i've installed a program that is misbehaving (I probably installed ratpoison while i was high).
[/rant]

---

### Post by krakk2k on 2009-04-06
just run this script to get a firewall tool =}

---

### Post by Xbehave on 2009-04-06
krakk2k i appreciate the effort, but before i go off installing a random iptables front end, does it actually support per application blocks not just per port ones?

---

### Post by krakk2k on 2009-04-06
> **Xbehave said:**
> krakk2k i appreciate the effort, but before i go off installing a random iptables front end, does it actually support per application blocks not just per port ones?

yes =}

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> just run this script to get a firewall tool =}
This is actually an excellent test.  Anyone who ran this without reading it first should immediately throw away their computer and buy a slide rule before they get their identity stolen.

---

### Post by swoll1980 on 2009-04-06
> **cardinals_fan said:**
> This is actually an excellent test.  Anyone who ran this without reading it first should immediately throw away their computer and buy a slide rule before they get their identity stolen.

I wouldn't have downloaded that script if it were the last one on earth. No offense to the poster.

---

### Post by FuturePilot on 2009-04-06
> **cardinals_fan said:**
> This is actually an excellent test.  Anyone who ran this without reading it first should immediately throw away their computer and buy a slide rule before they get their identity stolen.

I didn't run it but I looked at it. Would it even run? It doesn't even call a shell e.g.
```
#!/bin/bash
```

---

### Post by swoll1980 on 2009-04-06
> **FuturePilot said:**
> I didn't run it but I looked at it. Would it even run? It doesn't even call a shell e.g.
```
#!/bin/bash
```

It's harmless, but It will run I think. could have just posted the command. ```
sudo apt-get install gufw
```

edit: If you```
 sudo chmod a+x firewall.sh
``` then ```
./firewall.sh it works fine
```

---

### Post by GreyGeek on 2009-04-06
The 2.4 and 2.6 kernels have XFrames, a packet filtering ability which is controled by rules configured into IPTABLES.  Most "firewall" applications are really just a GUI setting between the user and IPTABLES which allows an easier way to configure IPTABLES and thus control how XFrames filters packets.

IPTABLES is installed by default and blocks all ports.  That's why you can take a fresh install of Kubuntu and go to the grc.com website, run "ShieldsUp!" and get an all green board for the first 1056 ports, which indicates that none of your ports responds in any way to  probes from the Internet, you are invisible to other Internet users unless they can infer your presences by time-to-live values in the packets.  If any of the 1056 ports are partially (blue) or completely (red) open it will be visibly obvious.  You can right click on that port and it will tell you what the port does.

Some wireless routers which use the Linux kernel also configure IPTABLES to protect the router.

---

### Post by cardinals_fan on 2009-04-06
> **FuturePilot said:**
> I didn't run it but I looked at it. Would it even run? It doesn't even call a shell e.g.
```
#!/bin/bash
```
No, it wouldn't.  But the principle remains the same.

---

### Post by krakk2k on 2009-04-06
lol...

right click firewall.sh
goto properties > permissions > and tick "allow executing file as program" if it isnt already....

then double click and click "run in terminal", surely anyone who has run linux since 2006 would know this? O,o

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> lol...

right click firewall.sh
goto properties > permissions > and tick "allow executing file as program" if it isnt already....

then double click and click "run in terminal", surely anyone who has run linux since 2006 would know this? O,o
EDIT: I see what you did there.  I wasn't aware that nautilus had an option for executability.

Anyway, running scripts without reading them first is an extremely bad idea under any circumstances.

---

### Post by swoll1980 on 2009-04-06
> **krakk2k said:**
> lol...

right click firewall.sh
goto properties > permissions > and tick "allow executing file as program" if it isnt already....

then double click and click "run in terminal", surely anyone who has run linux since 2006 would know this? O,o

I didn't know you could use Nautilus to change the permissions. I always used chmod. Assuming people should know what you know is arrogant.

---

### Post by krakk2k on 2009-04-06
> **cardinals_fan said:**
> No, that's wrong.  You have to start a script with #! or execute it with the shell (ie "sh firewall.sh").

Anyway, running scripts without reading them first is an extremely bad idea under any circumstances.

no you dont for such a simple script....

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> no you dont for such a simple script....
I edited that post.  You are correct, although it is better practice to use a crunchbang at the start.

---

### Post by krakk2k on 2009-04-06
> **swoll1980 said:**
> I didn't know you could use Nautilus to change the permissions. I always used chmod. Assuming people should know what you know is arrogant.

arrogance nothing. the user has been registered with this forum since 2006. thats a pretty long time to get to know the basics =}

---

### Post by swoll1980 on 2009-04-06
> **krakk2k said:**
> arrogance nothing. the user has been registered with this forum since 2006. thats a pretty long time to get to know the basics =}

The user has been a member for along time, and is very respectful to everyone, which is why he doesn't deserve to be attacked by some one like you.

---

### Post by krakk2k on 2009-04-06
> **swoll1980 said:**
> The user has been a member for along time, and is very respectful to everyone, which is why he doesn't deserve to be attacked by some one like you.

attacked? what the hell are you talking about?

---

### Post by swoll1980 on 2009-04-06
> **krakk2k said:**
> attacked? what the hell are you talking about?

Most normal people, including my self, will see a statement like "Well you've been using it for 2 years you should know how to do it" as a personal attack.

---

### Post by krakk2k on 2009-04-06
> **swoll1980 said:**
> Most normal people, including my self, will see a statement like "Well you've been using it for 2 years you should know how to do it" as a personal attack.

ugh, you arent worth even replying to. goodbye ):P

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> arrogance nothing. the user has been registered with this forum since 2006. thats a pretty long time to get to know the basics =}
First, the behavior of Nautilus isn't really a "basic".  I haven't used GNOME for about two years.  What is obvious on your system may not be on mine or anyone else's.
> **krakk2k said:**
> ugh, you arent worth even replying to. goodbye ):P
Let's keep it friendly.

---

### Post by gn2 on 2009-04-06
> **krakk2k said:**
> surely anyone who has run linux since 2006 would know this? O,o

I didn't. Why would I?

---

### Post by krakk2k on 2009-04-06
> **cardinals_fan said:**
> First, the behavior of Nautilus isn't really a "basic".  I haven't used GNOME for about two years.  What is obvious on your system may not be on mine or anyone else's.

Let's keep it friendly.

yeah your absolutely right. i didn't consider kde etc.... but i think they would still accept it. i dont know i only use the cookie cutter gnome version.

and i am being "friendly" by not replying with a stronger answer =}

> **gn2 said:**
> I didn't. Why would I?

sorry, again this was my mistake. i've only used linux for three months for very basic stuff, and i already knew that(nautilus executing), so i just assumed people who had been using it for a number of years would have a more instinctual understanding. sorry again!

---

### Post by MasterNetra on 2009-04-06
I personally perfer firestarter to control IPTable although I wish you could set it to allow programs Outbound/Inbound Access when rules are set to restrictive ... Even if there isn't a popup for it like with comodo in Windows, it still be nice to have the option. Would make running AssaultCube and other such games in restrictive easier, especially if you can't find out all the ports they need...

---

### Post by krakk2k on 2009-04-06
> **MasterNetra said:**
> I personally perfer firestarter to control IPTable although I wish you could set it to allow programs Outbound/Inbound Access when rules are set to restrictive ... Even if there isn't a popup for it like with comodo in Windows, it still be nice to have the option. Would make running AssaultCube and other such games in restrictive easier, especially if you can't find out all the ports they need...

thats why i prefer gufw

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> yeah your absolutely right. i didn't consider kde etc.... but i think they would still accept it. i dont know i only use the cookie cutter gnome version.

and i am being "friendly" by not replying with a stronger answer =}

It's all good.  I personally prefer mc (midnight commander) for managing my files, so I would change executability with "C-x c" and then my preferred chmod options.

---

### Post by krakk2k on 2009-04-06
> **cardinals_fan said:**
> It's all good.  I personally prefer mc (midnight commander) for managing my files, so I would change executability with "C-x c" and then my preferred chmod options.

fair enough, i prefer the more comfortable "windowyness" of nautilus :lolflag:

---

### Post by wolfen69 on 2009-04-06
> **smartboyathome said:**
> We do have one, called IPTables. All ports are closed by default.

technically, iptables is not a firewall. just because all unused ports are closed does not make it a firewall.

---

### Post by albinootje on 2009-04-06
> **Xbehave said:**
> for most new users or security conscious users an outbound firewall (in place by default for new users) would really help lock down ubuntu and make us safer.

I have been wondering myself since long why such a firewall-config tool didn't exist or was not recommended.

I like to see what my programs are doing..
I know that since a while the update-manager will contact the Ubuntu  repositories to check for updates, but an optional pop-up to allow or deny that would be pleasant to have.

People have been mentioning that Firestarter can do that, so that's one answer already. I wish that gufw could supply the same function though.

---

### Post by BGFG on 2009-04-06
> **Xbehave said:**
> 

[rant]===============================================================================================================

Wow thats the most uninforative reply ive seen in a while too.
ufw works on using basic iptables rules which employ port based blocking, which to all intense and purposes is USELESS, infact its worse than useless because people like yourself think locking down ports stops malware/spyware/hackers.
While locking down ports defends well against inbound traffic (not aswell as not running services which is what ubuntu does by default), and if used by routers (what iptables was designed for) can lock down legitimate services, it does **nothing** to stop malware/spyware/expliots, because they can always phone home on port 80.


Obviously as you are so well informed about matters (ufw doesn't block anything, netfilter/iptables does most of the blocking) you are a security guru, and this doesn't apply to you, **but** us mere mortals think its nice to get a gui warning when programs stop working. As an uninformed moran i was under the impression that denying an application access to the network means something is wrong because i've either got bad firewall rules (due to not being a security guru) or i've installed a program that is misbehaving (I probably installed ratpoison while i was high).
[/rant]

OOg, I keep forgetting that according to the thread you need your post to reflect your knowledge level :) I know that ufw is a conveinent frontend to iptables. I've got the pdf's on iptables to prove it :)

But now you know better and will probably research a little better before your next rant.

You may also want to check out apparmour:
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by BGFG on 2009-04-06
> **albinootje said:**
> I have been wondering myself since long why such a firewall-config tool didn't exist or was not recommended.

I like to see what my programs are doing..
I know that since a while the update-manager will contact the Ubuntu  repositories to check for updates, but an optional pop-up to allow or deny that would be pleasant to have.

People have been mentioning that Firestarter can do that, so that's one answer already. I wish that gufw could supply the same function though.

an iptables/ufw hook into the new notification system would be nice.

---

### Post by krakk2k on 2009-04-06
> **BGFG said:**
> an iptables/ufw hook into the new notification system would be nice.

good idea, you should post that at brainstorm

---

### Post by Xbehave on 2009-04-06
> **GreyGeek said:**
> IPTABLES is installed by default and blocks all ports.Are you sure? I'm on debian atm (me and kde4 had some issues) so i cant confirm this, but from what i remember running
```
sudo iptables -L
```
on a clean install would return no rules. meaning the firewall is off its just that ubuntu doesn't need an inbound firewall by default.

> 2006. that's a pretty long time to get to know the basics =}  It is true, that **I**'m know how to execute your script, but the internet is a big place and you never know if somebody who didn't is reading it. 

Unfortunately im not on ubuntu atm so i cant really talk about ufw/gufw from anything but their docs online, which say nothing about per application filtering.

@swoll1980 unfortunately with my ubuntu-age comes little wisdom (at least of network related matters), but thx.

@albinootje I think ufw is the firewall-config tool, as i said above im unsure about gufw, but im playing with Firestarter (1.0.3) now and it lacks the ability to define warning/actions on a per application basis, and as apt-get update runs on port 80 its indistinguishable from firefox.

From what ive read on firewalls there was fireflier which had multiple guis and did what i wanted in 2007, however its been discontinued due to a lack of interest and wont compile on my box.

@BGFG, apologies, it appears we got of on the wrong foot (on account of me obviously being high), im interested that you mention apparmor, i was aware that it is used to lock down applications but i thought it was mainly for local things. Unfortunately it fair to step up to the challenge on 3 counts:
1) it only applies to stuff that you manually build profiles for (if your going to go to that effort, you know what your doing and probably trust the app)
2) no gui 
3) all changes must be done as root.

OT: if 2/3 were overcome then apparmor would be prefect for tightly sandboxing user applications from each other **&** the network. e.g if when flash tried writing to disk other than in your .flash dir you got a little notification (allow/deny), then linux would once again be miles more secure than windows/mac.

> an iptables/ufw hook into the new notification system would be nice.unfortunately AFAICanTell ufw only locks ports not apps and as most network traffic is on port 80 its not much use.

---

### Post by jdong on 2009-04-06
Outbound application network control is best accomplished using mandatory access control mechanisms such as SELinux or Apparmor (SELinux based user type enforcement is particularly helpful) -- see Fedora's "xguest" user type; the only type of network access allowed is HTTP access via Firefox.


Unfortunately IPTables is not granular enough to control traffic on a per-application level with all that great of precision.

---

### Post by BGFG on 2009-04-06
@Xbehave, apologies man. Clearly in my first post i was too quick to pass judgment and you were specific with your needs.

As to what Jdong posted, after coming across Bhodi.Zazen's comprenehsive tutorial and some research of my own i decided to try out SELinux using Segatex as a front end(because I too like a GUI for security) but from my link below, you'll see how that ended :)

note the cascade of replies :P

[http://ubuntuforums.org/showthread.php?t=1030914](http://ubuntuforums.org/showthread.php?t=1030914)

Quite honestly, my current browsing habits would not necessarily place me in harms way, but SELinux and Apparmour are clearly tools we should be familiar with.

Edit: You may want to try Fedora and test out their security centre.

---

### Post by Xbehave on 2009-04-07
> **BGFG said:**
> Quite honestly, my current browsing habits would not necessarily place me in harms way, but SELinux and Apparmour are clearly tools we should be familiar with.
Yeah, I just find it annoying that in one sense i'm less secure under linux, without putting a fair bit of effort in myself.

> Edit: You may want to try Fedora and test out their security centre.I've been planning on installing fedora 11 and jaunty, it will be interesting to see which is easier to setup securely. 

Im not too fussed about a gui for setting it up, although its obviously nice to have one to start with, its in the everyday running, i'd like the notifications that currently tell me "you have mail" or "msn connected" to give me/users useful security information "x just tried to access y", "openoffice is trying to install a startup script", etc.

Ive got some exams comming up but i will definatly use what ive learn't in this thread to figure out a nice sandboxed computer linux install and once i switch to kde4 i may even try and add gui notifications myself :D

thx, for the info/tolerance guys

---

### Post by jdong on 2009-04-07
> **Xbehave said:**
> Yeah, I just find it annoying that in one sense i'm less secure under linux, without putting a fair bit of effort in myself.



Well I wouldn't call outbound firewall control security per se. It's great when you are containing the actions of black box (i.e. closed source / proprietary) apps but not necessary when you can audit exactly what every application can do.

Remember that GMail backup tool scandal where the author sent back a copy of your e-mail logins as an e-mail to his own GMail account? An outbound firewall wouldn't have been useful -- all you see is an HTTPS connection to GMail, which looks pretty legit.

I strongly recommend looking into SELinux if you need that level of security due to running untrusted applications on your system, and potentially also traffic logging and auditing on your machines. SELinux is one of the most incredibly powerful tools for defining confinement domains of any secure operating system I've used out there...

But in all seriousness, IMO the problem with untrustable phone-homes is not as major with a 100% FOSS OS stack. I'd focus your security efforts on your #1 threat: 0-day privilege escalation and arbitrary command execution vulnerabilities. AppArmor and SELinux can help you define fine-grained constraints on what programs are allowed to do to get their job done (i.e. ntpdate should be able to set the time. It should not be able to read /home/jdong).

AppArmor is a lot simple conceptually and in practice than SELinux but is not as capable of defining overly complex confinement domains as SELinux.

---

### Post by cariboo on 2009-04-07
THe OP began his rant because of. As jdong said FOSS his worries about malware, If you stick with the repositories to install software, you have no worries about getting malware. Not any joe programmer can have their program included in the repositories without having to go through a review process. Have a look at the Ubuntu Development [wiki]("http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") to see what it takes to get a program included in the repositories. As jdong said FOSS is more inherently more secure than similar software in the Windows world, because of peer review.

Jim

---

### Post by frodon on 2009-04-07
For the OP i have a tutorial for full firewall filtering but beware it's targeted to advanced users :
[http://ubuntuforums.org/showthread.php?t=668148](http://ubuntuforums.org/showthread.php?t=668148)

---

### Post by macogw on 2009-04-07
So much misinformation in this thread!

1. The firewall is netfilter/iptables
2. UFW is a front-end to iptables
3. UFW's "default" command sets the *inbound* policy
4. Ubuntu defaults to UFW being off, though of course iptables is still running (so if you have separate config files...)
5. Ubuntu defaults to all ports ACCEPT on inbound, outbound, and forward, but since there are no services running, there's nothing to connect to on inbound connections
6. On outbound connections, if you want to make sure you can get through a restrictive outbound firewall (ex: because you're doing something malicious), you'll just use port 80 or 443 anyway because who blocks HTTP and HTTPS?  Blocking all outbound except what you need will only work for the dumbest of attackers.

---

### Post by albinootje on 2009-04-07
> **macogw said:**
> 
5. Ubuntu defaults to all ports ACCEPT on inbound, outbound, and forward, but since there are no services running, there's nothing to connect to on inbound connections

You're talking about the desktop installation here. The people who use the Ubuntu server installation cdrom might have some services running after the initial installation ;-)
> 
6. On outbound connections, if you want to make sure you can get through a restrictive outbound firewall (ex: because you're doing something malicious), you'll just use port 80 or 443 anyway because who blocks HTTP and HTTPS?  Blocking all outbound except what you need will only work for the dumbest of attackers.
I'm a bit confused about this, what do you mean with that last sentence ?

---

### Post by 3rdalbum on 2009-04-07
I once used a computer where somebody had installed one of those two-way firewalls. It made UAC on Vista feel like a polite program that keeps out of your way.

---

### Post by jdong on 2009-04-07
> **3rdalbum said:**
> I once used a computer where somebody had installed one of those two-way firewalls. It made UAC on Vista feel like a polite program that keeps out of your way.


Back in the Windows world on serious systems, I used to run outbound firewall control and foreign application control too, and yes, when a new user to my system runs a foreign application he's going to CRY at the 20+ alert dialogs he'll have to click through.


Then at some point I realized it was still pretty easy to fool a user into agreeing to something that sounded harmless but wasn't. How DO you know, for instance, that while Skype is recording your calls it isn't sending your active list of applications back home, or that Flash isn't allowing Amazon's DRM video service to do the same?


Point of the matter is, for the most part you have to assume if you're running an application you cannot see the source to, that it can do whatever it wants on your system. That is, unless you have an SELinux type full confinement policy, then you can much more specifically define exactly what an application is and is not allowed to do.

---

### Post by BGFG on 2009-04-07
@Jdong, I know that a request like this exists in brainstorm already, but is there even a murmur of a GUI for apparmour or SELinux in Ubuntu ? seems like the one thing missing from the OS.

---

### Post by Koori23 on 2009-04-07
Perhaps I'm reading this incorrectly.. The OP wants to know exactly what is listening to what port... That's easy

sudo netstat -tunlp

that will tell you what process is listening to what port and what it's actually connected to at any given point in time.

If you want to know what applications are connecting to an address that's anything but *.* or 0.0.0.0, that command above will tell you.

---

### Post by jdong on 2009-04-07
> **BGFG said:**
> @Jdong, I know that a request like this exists in brainstorm already, but is there even a murmur of a GUI for apparmour or SELinux in Ubuntu ? seems like the one thing missing from the OS.

Well, SUSE has a GUI for AppArmor nobody's ported yet, Fedora also has SELinux GUI tools some of which we've ported, others not. IMO the barrier with these two systems is the complexity of understanding your software and how Linux program / kernel interactions work, not how to express a certain relationship in textual form vs GUI form.

---

