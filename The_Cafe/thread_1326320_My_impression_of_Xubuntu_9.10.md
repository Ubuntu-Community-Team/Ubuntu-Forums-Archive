---
title: "My impression of Xubuntu 9.10"
date: 2009-11-14
forum: The Cafe
---

### Post by Pogeymanz on 2009-11-14
Short story: I'm impressed.
Less short story: I might have had such low expectations that anything would impress me.

Longer story:

I loaded Xubuntu in Virtualbox with 384 RAM available to it. It booted pretty quickly. No benchmarks or anything, but it was quicker than I got from standard Ubuntu 9.10.

The art is beautiful. Big kudos to Canonical for that. I still don't like the two-panel-gnome-ripoff style, but the artwork is great.

The first thing I did when logged it is open a terminal and check the memory used:
```

             total       used       free     shared    buffers     cached
Mem:           371        173        197          0         17         68
-/+ buffers/cache:         88        282

```

Not bad considering all the newb-friendly stuff that is running, like the auto-updater, network manager, power manager, etc.

Disk space is only 2.3GB after running all the updates, which is also great considering all the tools that are included.

My biggest complaint is the app selection. Why in the WORLD do they have OpenOffice Writer and Abiword both installed? Why do they have all of OpenOffice except for Calc, which is replaced by Gnumeric? Otherwise, the selection is good for a newbie distro.

Conlusion:
Xubuntu 9.10 is probably what it should be. It would be great on a computer that is less than 5-6 years old. It includes all the tools that a newbie would expect from a "just works" distro. Ubuntu is not in the business of lightweight distros, so of course Xubuntu is heavier than other XFCE distros or just minimal Ubuntu + XFCE.

---

### Post by handy on 2009-11-14
How does it compare on the same system with Mint-Xfce?

---

### Post by NightwishFan on 2009-11-14
Abiword has a problem for some users on older machines. The .DOC plugin consumes so much RAM on a large document it brings the system to a near halt. OpenOffice may start slower, but it is actually more reactive in 256mb of RAM.

---

### Post by Naiki Muliaina on 2009-11-14
> **handy said:**
> How does it compare on the same system with Mint-Xfce?

Sucks, Mint XFCE and Zenwalk are still the best implementations of XFCE. But to be fair, Xubuntu = 64bit. Mint only had the main Mint Gnome with 64bit last time i looked.

---

### Post by RaZe42 on 2009-11-14
> **Pogeymanz said:**
> Short story: I'm impressed.

The art is beautiful. Big kudos to Canonical for that. I still don't like the two-panel-gnome-ripoff style, but the artwork is great.



Thank the Xubuntu team, not Canonical.

---

### Post by blueshiftoverwatch on 2009-11-14
I used Xubuntu several releases ago and by the time I got all the libraries for the various apps I wanted to use installed it wasn't that much faster than Ubuntu.

---

### Post by Naiki Muliaina on 2009-11-14
Thats largely my issue with XFCE in general to be honest. I love it and prefer it over Gnome in the way it works. But except for the 2 distros i mentioned (Mint and Zen) XFCE is best used for just odd modules now. Such as when people have the panels in a  fluxbox environment. Its become a full DE not a lightweight DE like it used to be billed as.

---

### Post by XubuRoxMySox on 2009-11-14
I like it so far! LXDE had alot of persistent bugs in Ubuntu and every Ubuntu spin-off I played with, and it's constantly "under heavy development." Which, to me, means that it's immature yet and bugs are to be expected. But it's *definitely* the lightest weight DE available (you can certainly go lighter with a window manager and no DE installed). 

I learned that LXDE takes most of it's code from Xfce, so to my n00bish way of thinking, LXDE will be like Xfce when it "grows up." So just for giggles I thought I'd try Xfce, so I ordered an Xubuntu CD when Karmic was released.

Gorgeous! Fast!! Very customizable and newbie friendly. Abiword always balks when I use it, so I'm glad Open Office was there. In only a matter of a few minutes I had a sweet, quick, customized Karmic Xubuntu. I really really like it! Alot! And I'm really surprised that I do... I was all prepared for it to suck because of some stuff I've read, but whoa!

The only thing that may become a show stopper for me is the CPU useage after the 'puter has been idle for awhile. Not all Xubuntu users experience [this]("https://bugs.launchpad.net/bugs/417778"), but the problem is severe for those that do. I'm hoping it'll be fixed in an update soon.

It's a sweet, newbie-friendly up-to-date, and very pretty alternative to my super-speedy, ultralight Debian Lenny/LXDE "primary distro."

-Robin

---

### Post by handy on 2009-11-14
> **Naiki Muliaina said:**
> Thats largely my issue with XFCE in general to be honest. I love it and prefer it over Gnome in the way it works. But except for the 2 distros i mentioned (Mint and Zen) XFCE is best used for just odd modules now. Such as when people have the panels in a  fluxbox environment. Its become a full DE not a lightweight DE like it used to be billed as.

I run the xfce4-panel with some plugins on top of Openbox on Arch.

Due to Xfce4's modular design, I found that you could run an enormous amount (not that I do now) of Xfce4, on top of Openbox, with no speed penalty.

That is until you run xfce4-session.  Then Openbox slowed down to Xfce speed.

So perhaps those using Xfce could try it without the session manager.  It really should be quite a bit faster.  If you still need a session manager there exist others out there, & the word is that they are faster than the one that comes with Xfce4.

---

### Post by Naiki Muliaina on 2009-11-14
See thats a good use of XFCE, and why i like the idea of it being modular. Its a shame it cant be a 'lightweight' DE on its own though aye?

---

### Post by Pogeymanz on 2009-11-14
I'm really not a fan of LXDE. For one, it's not really a DE. LXTerminal is nothing new, LXPanel is almost a direct copy of Fbpanel, PCManFM is buggier than Thunar, Openbox and leafpad are not theirs.

Just use Openbox with a good panel, like XFCE4-panel.

What machines are you guys on, who are claiming that XFCE is not lightweight? On my machine, it is way faster than Gnome or KDE and it's not noticeably slower than Openbox, except that it uses around 20MB more RAM out of 1GB.

I admit I don't use the saved session option or the power manager, etc. But I don't think I've stripped it bare or anything. The problem with running without the session manager is that the log out options wont work.

---

### Post by BuffaloX on 2009-11-14
Can you drag links from firefox onto the desktop?

---

### Post by sertse on 2009-11-14
My Xfce setups have 3 different variations

Full Xfce, Xfce with lxsession, or Xfce modules through fluxbox. It's more of a personal thing, and speed beinga factor.

Claims that Xfce isn't light have been greatly overstated, especially on memory use. At 512mb it is completely fine, below that, it is still quite manageable.  

CPU wise, a Aspire One with Cpufreq put on powersave (thus stuck at 800mhz) still does Xfce quite well, even with composite on. Off is slighter better though at that point though.

---

### Post by Stan_1936 on 2009-11-15
> **Naiki Muliaina said:**
> Sucks, Mint XFCE and Zenwalk are still the best implementations of XFCE. ...

I have installed(if only for a week or two) every release of Zenwalk(XFCE version) and Mint(XFCE version) since I registered on [www.ubuntuforums.org](www.ubuntuforums.org) 2 years ago.  Over this period, I have ALWAYS had Xubuntu installed in a dual boot setup on the same machine.

Xubuntu has always worked FLAWLESSLY on my hardware(8yr old ~1.0 MHZ AMDK7 2GB DDR WD7200RPM 8MB Cache)!
Xubuntu feels MUCH faster than regular Ubuntu.  People who say that it isn't much faster are kidding themselves.  Those kinds of comments give me a good laugh every time I read them.  **For me**, it's faster...noticeably faster.
Mint crawled.
Zenwalk has NEVER ONCE automatically set up eth0....NOT ONCE!
Zenwalk did not feel much lighter than Xubuntu.
Zenwalk did NOT feel as robust as Xubuntu!

---

### Post by Stan_1936 on 2009-11-15
> **Pogeymanz said:**
> ...My biggest complaint is the app selection. Why in the WORLD do they have OpenOffice Writer and Abiword both installed? Why do they have all of OpenOffice except for Calc, which is replaced by Gnumeric?....

It will take you less than 5 minutes to add/remove what you want to.

---

### Post by Naiki Muliaina on 2009-11-15
They have all used the same specs comfortably for me. My issue is more Mint XFCE and Zenwalk feel better than Xubuntu. They feel like they have been put together properly. Never had you eth0 issues. I never said they were faster. Ive never broken Zenwalk, so cant comment on robustness either.... Mint XFCE is Xubuntu remixed. Im not quite gettin why mint crawled and Xubuntu flies on your PC?

On it being faster than Ubuntu... It normally sits between 192 - 248 ram usage on my PC. Ubuntu hovers about the 248 mark. That really aint much of a difference. It says it should only use 128 ram on the web page but i havent had it that low since Gutsy. 

My issue with XFCE's speed is to do with XFCE NOT Xubuntu. Full XFCE is far closer to Ubuntu / KDE weights nowdays than *Box weight.

---

### Post by majabl on 2009-11-15
I've got Xubuntu running on the 9-and-a-bit-year-old computer noted in my sig.  I put 9.10 on there recently (kind of - see below).  It looks really nice, and overall I'm impressed with how well it runs on such a weedy computer.  Feels snappier than the equivalent Ubuntu, which I also gave a little trial run.  Everybody always seems to compare the RAM usage between Xubuntu and Ubuntu, and recommend the former 'because it uses less RAM'.  At the end of computer power that I have running Xubuntu, the main reason for using Xubuntu rather than Ubuntu is because it seems less processor intensive.  RAM usage, as Naiki Muliaina notes, isn't that different between the two.

My only real gripe with Xubuntu is that the live CDs never work for me, regardless of which version or variant of live CD I use.  To install it I always have to use a Ubuntu Live CD and then follow [Psychocats' Pure XFCE tutorial]("http://www.psychocats.net/ubuntu/purexfce").  As a result I do have only AbiWord installed at the moment, because those instructions completely remove Open Office.

Oh - networking also looks like it will be 'interesting'.  I want to make the computer talk to the other two PCs I have (which run XP) so that documents can be shared across all three.  From the quick skim of search results I made last weekend, this doesn't look as though it will be an easy process.

---

### Post by Pogeymanz on 2009-11-15
> **Naiki Muliaina said:**
> 
On it being faster than Ubuntu... It normally sits between 192 - 248 ram usage on my PC. Ubuntu hovers about the 248 mark. That really aint much of a difference. It says it should only use 128 ram on the web page but i havent had it that low since Gutsy. 


RAM usage inflates based on how much you have. If you tried Xubuntu on a machine with only 128MB RAM it would probably still be tolerable, whereas Ubuntu probably wouldn't be.

---

### Post by Stan_1936 on 2009-11-15
> **Naiki Muliaina said:**
> ...It normally sits between 192 - 248 ram usage on my PC. Ubuntu hovers about the 248 mark. That really aint much of a difference. ...

For me, Ubuntu is around 160 MB RAM, on startup(no apps open).
In comparison, Xubuntu is around 99 MB RAM on startup(no apps open).

As you can tell, for me, it IS a big difference.

---

