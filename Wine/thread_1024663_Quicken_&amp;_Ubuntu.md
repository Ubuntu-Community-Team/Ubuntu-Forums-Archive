---
title: "Quicken &amp; Ubuntu"
date: 2008-12-29
forum: Wine
---

### Post by kyalee on 2008-12-29
I posted a while back about good financial programs for Linux, but apparently my dad doesn't like anything that the Linux community has to offer, at least not for accounting purposes (don't ask me, I can't make heads or tails of that sort of thing). Now he wants to know if he could possibly run Quicken on Linux. I told him about Wine, but given that Quicken is a pretty complex program and that data loss would be kind of a huge deal in this case, I was wondering if anyone has any experience running Quicken through Wine on Ubuntu and could tell me how well it worked out. I've never used Wine personally, so any tips would also be appreciated.

---

### Post by kokkus on 2008-12-29
Have you tried OpenOffice finance?
And MSMoney2006 works fine with Wine.
Or you could try daul boot with windows and ubuntu.

---

### Post by kokkus on 2008-12-29
I did some more research and it seams like gnucash is a clone.
You can install it from terminal with apt-get.
&#8217;sudo apt-get install gnucash&#8217;
If you use kde you can also try kmoney.

Good luck:)

---

### Post by thomasr on 2008-12-29
You can install vmware and run it in an xp virtual machine - that is what my wife has been using. It is on a portable usb hard drive, so she can use it at home and at the office. The virtual machine runs on her lowly p3 900 mhz box - a little slow to load, but after that runs fine.

Would probanly run well in virtualbox also.

---

### Post by ajgreeny on 2008-12-29
> I did some more research and it seams like gnucash is a clone.
You can install it from terminal with apt-get.
’sudo apt-get install gnucash’
If you use kde you can also try kmoney.
I tried gnucash a while ago, but found that it is not at all intuitive to use so gave up quickly.  I then looked at kmymoney2 (not kmoney, as the above poster says) and that was much more like quicken as I remember it; quite simple, but great for setting up straightforward cheque accounts, credit cards etc etc. ie personal finance.  I suspect for business use it will be far too simple, but it depends what use you need it for.

---

### Post by kokkus on 2008-12-29
sorry I ment kmymoney. But yes, give that a try.

---

### Post by kyalee on 2008-12-29
He's tried GNU Cash and found it very hard to use. I also gave him Buddi, Home Bank, and a few others. I think he might have tried kmymoney2 also, but he went through so many that I don't even remember. He's just very used to Quicken, I think, and since he has two businesses plus pretty complicated personal finances, he needs a powerful program. I suspect he's going to end up with a dual boot (XP and Ubuntu, the whole reason he got a Ubuntu machine in the first place was that he hates Vista), but I was hoping maybe there was another way that I hadn't thought of.

---

### Post by madrivereric on 2009-01-01
kyalee,
  I've been using Quicken via wine on my Fiesty box for over a year with no significant issues.  A few versions of wine ago, there were occasional nuisance type problems now and again, but things have been quite stable and quite functional for some time.  At no time did I have any data loss. The things I use (basic accounts, mortgage, 401k, stock portfolio, on-line quote update, budget tracking, report generation) all work fine.
  My installation followed persectoff's post (#5) on [http://ubuntuforums.org/showthread.php?t=194013](http://ubuntuforums.org/showthread.php?t=194013)
  I tweaked things to allow multiple users (myself & my wife) to both run Quicken and access the same file.  To achieve this, I did the install in a separate account and then for each user, I created a .wine directory with links back to the directories in the quicken account's .wine directory.  Each user has their own config files.
  I've now upgraded to Intrepid and all that was needed was the installation of the new wine packages and Quicken came back to life!

Eric

ps - I did try out GnuCash & KMyMoney, but neither had the features I needed.  GnuCash did mention some of my requirements in their development plan but the features were considered a very low priority with no plans to implement.  So, I stuck with Quicken which meets my needs...

---

### Post by kansley on 2009-01-07
wine didn't work for me, mostly because it would do the online update.  and the open source software didn't do it for me, either.  it needs more work.

so, i put sun virtualbox on intrepid ibex.  it's at [http://www.virtualbox.org/](http://www.virtualbox.org/).  it creates a small computer within a computer, onto which you can install xp.  it runs well, and i've been using quicken 2008 now for a month, with online updates.

it took me a day to figure out how to get everything running, but then i'm not a computer geek and everything takes me a day. i wish i'd started with it.

---

### Post by dhochmuth on 2009-05-08
I just tried installing and running Quicken 2008 deluxe last night.  Was able to get it to install and run (on 9.04) using information on wine and winetricks found here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9099&iTestingId=28536](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9099&iTestingId=28536)

There are numerous Quicken versions covered.  See:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=107](http://appdb.winehq.org/objectManager.php?sClass=application&iId=107)

I have not had time to test many features yet.

Dave

---

### Post by gadgetsmom on 2009-05-13
HI - I have a laptop requiring a new OS, and my brilliant son suggested ubuntu (among others) instead if any windows option.   I must have Quicken Premier and Turbo Tax Premier.  It sounds like Wine handles Quicken now.  Does anyone have a clue about Turbo Tax Premier?  Many thanks.

---

