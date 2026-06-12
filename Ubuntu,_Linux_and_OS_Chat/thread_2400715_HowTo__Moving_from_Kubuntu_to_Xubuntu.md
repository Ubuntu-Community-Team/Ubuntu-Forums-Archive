---
title: "HowTo:  Moving from Kubuntu to Xubuntu"
date: 2018-09-09
forum: Ubuntu, Linux and OS Chat
---

### Post by undecidable on 2018-09-09
A pool of mostly long-time users disillusioned with KDE,
are looking to move from Kubuntu to Xubuntu.  
(e.g. see [bugs.kde.org/show_bug.cgi?id=341143]("https://bugs.kde.org/show_bug.cgi?id=341143"))

For those such as myself who had been using KDE for 11 years (since 2007)
and were tightly integrated into the KDE desktop
the prospect of making this transition seems at first overwhelming.

Having done it now, it is not that painful,
and I offer the following to help others who want to efficiently make the transition
without wasting time on dead ends.

**The key issues that need to be addressed:**
a.  Xfce apps are mostly too basic.
b.  Configuration is more difficult but possible.

**Four key points:**
1.  You can take many Kde apps to Xubuntu
2.  Some kde apps can be replaced by gtk apps that are as good or better
3.  Some kde apps can be replaced by desktop independent apps that are better or much better
4.  Xfce is quite configurable, but it takes longer, but you waste less time on stuff you don't want

**1.  You can take many Kde apps to Xubuntu**
I use in Xubuntu the following apps from KDE:
kwrite, kate  (much more functional than gedit, mousepad)
dolphin  (much more functional than thunar or nautilus)
yakuake (better than guake)
okular (allows markup)
clementine (allows filesystem browsing, doesn't force to use a library)
gwenview   (allows filesystem browsing, doesn't force to use a library)
Muon (doesn't lock the database as synaptic does)

**Some kde apps can be replaced by gtk apps that are as good or better**
qdirstat to replace kdirstat
gparted has always been better than kparted
gprename to replace krename
meld to replace kdiff3

**3.  Some kde apps can be replaced by desktop independent apps that are better or much better**
thunderbird/lightning/cardbook to replace kmail/korganizer/kaddressbook
doublecmd-gtk to replace krusader
geany (text editor in addition to kate)
recoll (to replace kde desktop search)
QuiteRSS to replace Akregator

**4.  Xfce is quite configurable, but it takes longer, but you waste less time on stuff you don't want**
Xfce is in general very configurable.
Where in KDE much of the configuration can be done through system settings,
in Xfce more of it needs to be done through text files.  
eg removing applications from a list of allowed apps to open a file type:
in kde very easy, in xfce, very clumsy.  

Some things you can make reasonable workarounds:
In kde it is easy to increase window border size to make them easier to grab
in xfce I still don't now how to do this
(and all the non-ugly themes had impossible to grab window borders)
so I configured a shortcut (F10) to enable easy resizing of windows.

There are many other examples of things that were easier to configure in kde than in xfce
but on the other hand, I did not have to spend any time
 trying to stop unwanted kde services which is always a challenge.
 (eg stopping akonadi from autostarting in kubuntu 14.04 required use of a proton accelerator).
 
 Lots of other stuff not important enough to mention,
 but overall, I am guessing my transition form Kubuntu 14.04 to Xubuntu 18.04
 was probably less pain than the transition to Kubuntu 18.04 would have been.
Not as beautiful, but I get to work the way I want.

---

### Post by Frogs Hair on 2018-09-09
Moved to *UL&OS Chat*.

---

### Post by undecidable on 2018-09-10
(thanks for moving this to the right place)

One key tip I forgot:

In Xubuntu, the default and the Tango and Oxygen icon sets which I usually use
were missing many icons for kde programs,
so the toolbars looked wrong.

Changing the icon set to Papirus (Papirus, Papirus-light, Papirus-adapta, papirus-adapta-nokto)
fixed this.

This was the only thing needed to make kde programs work well on Xubuntu.

---

### Post by haiiyaa on 2018-12-14
Hi, 

I am new Xubuntu, in fact coming by ways of Kubuntu -> Ubuntu -> Xubuntu. I am liking it so far. However the first thing I would like to change is the file manager. Dolphin has been my favourite, so I installled it and the basic functionality works fine. However it feels it is not yet quite integrated into the OS as I'd like. 

For example
1. I cannot browse the network. Clicking on the network icon on the left only gives me a blank page. 
2. I cannot drag a folder from an archive tool like engrampa
3. I cannot search files, I get the error message invalid protocol. 

This is just for starters.

I want to know how you integrated Dolphin into your OS. 

Any pointers will help. 

Thanks

---

### Post by haiiyaa on 2018-12-14
I fixed the search files by enabling baloo file indexer. But the other issues still remain.

---

### Post by SagaciousKJB on 2018-12-14
Interesting.  I switched to XFCE years ago, and all but forgot about most of the KDE apps you mentioned.  I wonder how much of the transition is people just not wanting to get used to new things.  I haven't thought about yakuake for years, yet I would have placed it as something "important" before.  I kind of miss kate.  But geany is great for programming.

Honestly as the years have passed, I've found myself turning to the terminal for more tasks than relying on GUI interfaces.  I think one benefit of doing this, is that as time goes on, if XFCE changes in a way I don't like, I don't need to relearn how to do things, or find new GUI tools to do them, since I can just use the same terminal and core utilities to accomplish tasks I need done.

I think to date the only KDE app that I can not find a suitable replacement for on XFCE is kcron.  I didn't really feel like installing all the bloat needed to install kde-libs just to install kcron, so I just got more acquainted with editing cron files by hand.  Now I never have to rely on a graphical cron editor again.

---

### Post by silentstone on 2018-12-27
This is a nice list of program equivalents between XFCE and KDE.  I'm moving in the opposite direction, adding KDE session to Xubuntu, yet this helps!

---

