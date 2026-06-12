---
title: "ReactOS windows Alternative?"
date: 2010-01-30
forum: The Cafe
---

### Post by mikeannike on 2010-01-30
I was doing some research the other day and found something really cool.  Its called reactos.  According to what i read on the website it is essentially trying to be and open source alternative to windows. It is based of NT.  If this os matures this could really be something great.  That means for all those people who choose to duel boot and not use linux full time, at least they could duel boot with a open soucre os and get all the features of windows. 

Ps:  No I am not affiliated with reactos. I'm just a technology lover.

---

### Post by beastrace91 on 2010-01-30
> **mikeannike said:**
> I was doing some research the other day and found something really cool.  Its called reactos.  According to what i read on the website it is essentially trying to be and open source alternative to windows. It is based of NT.  If this os matures this could really be something great.  That means for all those people who choose to duel boot and not use linux full time, at least they could duel boot with a open soucre os and get all the features of windows. 

Ps:  No I am not affiliated with reactos. I'm just a technology lover.

Yes and no. ReactOS project moves historically slow (and understandably so - its a huge undertaking!). That being said it also uses/borrows much of it's code from the Wine project, meaning that if it runs on React it typically runs equally well on *nix under Wine. So why dual boot?

ReactOS is a fun idea, but at this point its not even usable/a viable alternative to anything IMO

Regards,
~Jeff

---

### Post by mister_playboy on 2010-01-30
> **beastrace91 said:**
> ReactOS is a fun idea, but at this point its not even usable/a viable alternative to anything IMO

That sums it up.  You can play around with it in a VM or on a spare computer, but that's about it.

---

### Post by NightwishFan on 2010-01-31
I could not get it to boot on my hardware. I was able to install Windows Xp Guest Extensions in Virtualbox though. It resembles Windows installer a great deal, but in normal use it is a bit different.

---

### Post by mikeannike on 2010-01-31
I haven't tried it personally myself.  Although it does seem very buggy.  I hope they continue to develop it.  It would really be cool to see a open source alternative to windows that runs using the same platform.  That way no one could say things like "I can only run windows because of ..............."

---

### Post by Artemis3 on 2010-01-31
Actually they just announced a complete rewrite and merge stuff from current wine, so its not a good moment to try it ^_^!

At some point ReactOS could be used to replace the OS for an ancient machine running win9x or NT4.

---

### Post by beastrace91 on 2010-01-31
> **beastrace91 said:**
> it also uses/borrows much of it's code from the Wine project, meaning that if it runs on React it typically runs equally well on *nix under Wine.

... Why not just use Linux? If it works on React it should work under Wine - plus if React works with Windows drivers it also means it will work with Windows viruses

~Jeff

---

### Post by gsmanners on 2010-02-01
*Why not just use Linux?* Because ReactOS is simpler and more efficient. ReactOS is also free, so there's nothing stopping you from dual-booting (except maybe their boot loader).

*it also means it will work with Windows viruses* ReactOS is not Windows. AFAIK, ReactOS does not give you admin access rights by default. Most software will run nowadays with normal user privilege. Certain networking services are not turned on by default. ReactOS does not come bundled with Norton, which IMO is one of the main reasons people get viruses (the false sense of security).

---

### Post by mikeannike on 2010-02-01
> **beastrace91 said:**
> ... Why not just use Linux? If it works on React it should work under Wine - plus if React works with Windows drivers it also means it will work with Windows viruses

~Jeff
  

    I'm using ubuntu full time on my netbook (which is my main machine at the moment)and I'm loving it.  The reason why i was asking about react os is for other people.  I have friends whose computers i work on and when i try to pitch linux to them, they complain how they need to be able use a specific program. So i figured that whenever that reactos becomes polished and stable, they would have no excuses not to move to an open-source os.

---

### Post by Frak on 2010-02-01
> **beastrace91 said:**
> That being said it also uses/borrows much of it's code from the Wine project, meaning that if it runs on React it typically runs equally well on *nix under Wine.

Not entirely. ReactOS also provides additional Operating System features that Wine doesn't provide, yet, to include those, separations from Wine have to be made, and in turn it is more unstable.

So, some things that run in Wine won't run in ReactOS, but some things that run in ReactOS won't run in Wine. The biggest thing, of course, is that ReactOS can interact with the hardware, where Wine cannot.

---

### Post by Frak on 2010-02-01
> **beastrace91 said:**
> ... Why not just use Linux? If it works on React it should work under Wine - plus if React works with Windows drivers it also means it will work with Windows viruses

~Jeff
Works with drivers != Works with Viruses

If ReactOS can run viruses better than Wine, then ReactOS is further ahead in development than Wine is. A virus is no different than any other program.

---

### Post by t0p on 2010-02-01
> **mikeannike said:**
> I'm using ubuntu full time on my netbook (which is my main machine at the moment)and I'm loving it.  The reason why i was asking about react os is for other people.  I have friends whose computers i work on and when i try to pitch linux to them, they complain how they need to be able use a specific program. So i figured that whenever that reactos becomes polished and stable, they would have no excuses not to move to an open-source os.

For some time I was using Ubuntu exclusively on my desktop machine and my EeePC.  But in the past few months I've had to use some Windows stuff, and I couldn't get it to work with Wine; so I installed VirtualBox on the desktop and I've got XP + guest additions running on it.  It's a pretty good solution - I can use the Windows apps and Ubuntu at the same time, cut-and-paste between the 2 OSes etc - but this solution works only because I already owned a XP disk image and license.  If I'd had to buy a license just for the couple of apps I need to use I would have been well miffed.  And for how much longer is XP available anyway?  If I had to buy a Windows 7 license... agh, I'm not even going there!

Anyway, the point I want to make is: ReactOS would be a perfect solution for my current situation... *if* ReactOS worked.  But it doesn't work.  It's not vaporware, but it may as well be, as far as I'm concerned.  Pull yer finger out, ReactOS people!

---

### Post by phrostbyte on 2010-02-01
> **t0p said:**
> For some time I was using Ubuntu exclusively on my desktop machine and my EeePC.  But in the past few months I've had to use some Windows stuff, and I couldn't get it to work with Wine; so I installed VirtualBox on the desktop and I've got XP + guest additions running on it.  It's a pretty good solution - I can use the Windows apps and Ubuntu at the same time, cut-and-paste between the 2 OSes etc - but this solution works only because I already owned a XP disk image and license.  If I'd had to buy a license just for the couple of apps I need to use I would have been well miffed.  And for how much longer is XP available anyway?  If I had to buy a Windows 7 license... agh, I'm not even going there!

Anyway, the point I want to make is: ReactOS would be a perfect solution for my current situation... *if* ReactOS worked.  But it doesn't work.  It's not vaporware, but it may as well be, as far as I'm concerned.  Pull yer finger out, ReactOS people!

Believe it or not it is not easy for a bunch of volunteers to clone the flagship product that took a Fortune 10 company two decades to develop. The fact that even boots is a testament to their skill.

Btw, if ReactOS ever gets perfect Windows support, it's likely Wine won't be far behind. They share a lot of the same code. 

It's true that Wine does not support running Windows drivers.. but it does provide some access to applications which require hardware level control (which are very few and far in-between anyway), it simply passes this responsibility to the Linux kernel (eg: USB support).

---

### Post by Psumi on 2010-02-01
> **phrostbyte said:**
> It's true that Wine does not support running Windows drivers.. but it does provide some access to applications which require hardware level control (which are very few and far in-between anyway), it simply passes this responsibility to the Linux kernel (eg: USB support).

You might want to look at this diagram, and show it to others next time you wish to explain something, not saying you're wrong but it's a good ref: [http://en.wikipedia.org/wiki/File:Wine_on_ReactOS.svg](http://en.wikipedia.org/wiki/File:Wine_on_ReactOS.svg)

---

### Post by DOS4dinner on 2010-02-01
Not sure I'd ever use it daily, but I like the possibility of using it in an emulator to be able to use old software. Kinda like a DOSBox, except being able to run Windows programs.

---

### Post by MasterNetra on 2010-02-01
ReactOS is still in its Alpha Stage so lets not make any judgments about it yet eh?

---

### Post by Frak on 2010-02-01
> **MasterNetra said:**
> ReactOS is still in its Alpha Stage so lets not make any judgments about it yet eh?
It's been in Alpha for 10 years, I'm passing judgement.

---

### Post by RiceMonster on 2010-02-02
To be honest, I really think this project is more or less wasted effort. Just use windows if you need it. On the other hand, there's wine which already addresses the problem of running Windows only software on an open source OS.

---

### Post by Eisenwinter on 2010-02-02
> **RiceMonster said:**
> To be honest, I really think this project is more or less wasted effort. Just use windows if you need it. On the other hand, there's wine which already addresses the problem of running Windows only software on an open source OS.
I agree.

The last version of ReactOS I used was 0.3.6, and it couldn't run without crashing for ~30 minutes.

Programs also had many graphical interface bugs in them.

I think WINE works better for those single-program needs than ReactOS, but use Windows anyway for big programs.

---

### Post by toupeiro on 2010-02-02
> **Frak said:**
> It's been in Alpha for 10 years, I'm passing judgement.

I'm with Frak on this one..  In many ways, I think wine is so much closer to producing a full application oriented windows experience, complete with hardware support, than ReactOS will be.  I tried a beta very recently and it leaves much to be desired.  Wine has been in beta for over a decade as well, and its much further along.

---

### Post by murderslastcrow on 2010-02-02
In previous releases, I was disappointed with ReactOS's compatibility compared to Wine.

However, now that they're adding a new module to adopt all of Wine's CURRENT code, they are sure to have a dramatic increase in compatibility, and they'll be able to include Wine test results in their OS, up to whatever release they are at parity with.

Once they improve the driver compatibility, it will be a great benefit to those with dual-boot needs, such as MMO players and people who need more recent versions of DirectX, gameguard drivers, securom, etc. etc.

But really, if ReactOS has about 11 developers or whatever, and Wine has hundreds, and Wine guys don't really have to bother with drivers much at all, just think about how long it would take the ReactOS guys. I think they've done an amazing job so far, quite honestly. I mean, they basically have an open source Windows 98 already.

---

### Post by Sand &amp; Mercury on 2010-02-02
ReactOS is only successful at this point as a proof-of-concept. One day it may be useful in the same way that FreeDOS is now, but I don't envision much more than that coming of it.

---

### Post by Zzl1xndd on 2010-02-02
> **mikeannike said:**
> I have friends whose computers i work on and when i try to pitch linux to them, they complain how they need to be able use a specific program. So i figured that whenever that reactos becomes polished and stable, they would have no excuses not to move to an open-source os.

I few years ago I thought the same thing when I stumbled accross ReactOS. Although I have learned that most people don't really care if its open source or not as long as it works.

I find it is far easier to move people little by little. Most of my friends started out using MSN Messenger, Microsoft works/office, Internet explorer, Windows Media Player, iTunes, and other propritary programs. Where possible I have people to OpenOffice, Pidgin, Firefox, VLC and other opensource programs. (Plus getting them hooked on the games I know work in Linux) Then when I suggest moving to Linux it doesn't seem like a crazy idea any more.

---

### Post by pwnst*r on 2010-02-02
> **gsmanners said:**
> [I]ReactOS is also free, so there's nothing stopping you from dual-booting (except maybe their boot loader).



Lol, this just had to be quoted.

---

