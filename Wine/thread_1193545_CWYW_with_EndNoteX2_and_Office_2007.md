---
title: "CWYW with EndNoteX2 and Office 2007"
date: 2009-06-21
forum: Wine
---

### Post by showfire on 2009-06-21
I know I am opening up a can of worms that everyone has an opinion on.  Let me start buy asking if anyone has figured out how get this working in wine.  And go further to say I have both programs installed and running just not that part of the 2 and it causes office to crash.  I am running 8.10 with wine 1.1.23  I also have winetricks and cabextract installed.  Now don't get on my case about using office 2007 this is what everyone used in my lab including the professor I work for.  They also all use endnote and ask for the libraries when a paper is given to them.  Because of this I need these applications.  I am not able to do the virtualization because my desktop is an older computer and doesn't have the power to do virtualization and run other applications.  With this said, does anyone have any ideas I am all ears.

---

### Post by NightMKoder on 2009-06-21
There are plenty of guides for office 2007 around. With the latest wine you can just install it. Check the wine's appdb for the other apps ([http://appdb.winehq.org](http://appdb.winehq.org)) and if something doesn't work, read the post above for what you need for us to help you. 

We can't help you with a problem that you don't have yet.

---

### Post by jhoeijao on 2009-06-21
> **showfire said:**
> I know I am opening up a can of worms that everyone has an opinion on.  Let me start buy asking if anyone has figured out how get this working in wine.  And go further to say I have both programs installed and running just not that part of the 2 and it causes office to crash.  I am running 8.10 with wine 1.1.23  I also have winetricks and cabextract installed.  Now don't get on my case about using office 2007 this is what everyone used in my lab including the professor I work for.  They also all use endnote and ask for the libraries when a paper is given to them.  Because of this I need these applications.  I am not able to do the virtualization because my desktop is an older computer and doesn't have the power to do virtualization and run other applications.  With this said, does anyone have any ideas I am all ears.

Try upgrading your wine, the latest version is 1.1.24 and here's the link [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_i386.deb)

---

### Post by showfire on 2009-06-21
> **NightMKoder said:**
> There are plenty of guides for office 2007 around. With the latest wine you can just install it. Check the wine's appdb for the other apps ([http://appdb.winehq.org](http://appdb.winehq.org)) and if something doesn't work, read the post above for what you need for us to help you. 

We can't help you with a problem that you don't have yet.

You are misunderstanding me.  I have both programs installed and running, they just don't run together as they are supposed to.  You can run them at the same time as **individual** programs but when you try to use the "Cite While You Write" feature at least one of the two crashes.  If you had the cwyw addin added to work it crashes at start up but if you add it after its running you crash endnote.  The addin used the EndNote cwyw.dll file that is located in the Program Files/Common Files/ResearchSoft/Cwyw/12/ folder.

---

### Post by showfire on 2009-06-21
> **jhoeijao said:**
> Try upgrading your wine, the latest version is 1.1.24 and here's the link [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24~winehq0~ubuntu~9.04-0ubuntu1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.24%7Ewinehq0%7Eubuntu%7E9.04-0ubuntu1_i386.deb")

Not available for 8.10 that I could find and the 9.04 file says that the libasound2 dependency is not met even though its the latest version.

---

### Post by NightMKoder on 2009-06-21
That's because that's the jaunty version.
[www.winehq.org/download/deb](www.winehq.org/download/deb) for keeping up to date.

---

### Post by pwaltman_1972 on 2009-11-07
> **showfire said:**
> I know I am opening up a can of worms that everyone has an opinion on.  Let me start buy asking if anyone has figured out how get this working in wine.  And go further to say I have both programs installed and running just not that part of the 2 and it causes office to crash.  I am running 8.10 with wine 1.1.23  I also have winetricks and cabextract installed.  Now don't get on my case about using office 2007 this is what everyone used in my lab including the professor I work for.  They also all use endnote and ask for the libraries when a paper is given to them.  Because of this I need these applications.  I am not able to do the virtualization because my desktop is an older computer and doesn't have the power to do virtualization and run other applications.  With this said, does anyone have any ideas I am all ears.

Has anyone has managed to get CWYW working with EndNote & Office 2007?

I'm running the latest version of wine, and my installation order was
1 - playaonlinux (to install office07)
2 - Office07 (via playaonlinux)
3 - endnote

wine version is the latest (wine-1.1.32)
playaonlinux version: PlayOnLinux 3.7.1

According to this page (for EndNote X1), you can't get CWYW working, but it's not clear if the installation order (or method) is important so I just wanted to see if you had any better luck:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9243]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9243")

Thanks!

---

