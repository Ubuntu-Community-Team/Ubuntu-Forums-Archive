---
title: "Wine appears to be a quitter"
date: 2010-11-10
forum: Wine
---

### Post by CrispyFriedUke on 2010-11-10
For at least a week and a half now, I have been fighting with wine and pulling my hair out. I have attempted vigilance, but so far any tries I've made have proven utterly useless. So, my last resort is you kind folks here at the forums.

I'm sure my story isn't new. I had a friend fix my computer, expecting it to come back with windows, and I ended up with Ubuntu. I love having a computer again, but I hate having something that's about as worth my while as a several hundred dollar paper weight. I am grateful for what was done for me, but Ubuntu has proved to be useless to me, so far.
I want to work with it though.
So I tried to download Wine so I could put my Wacom tablet driver and my Photoshop on the computer. That's all I've been trying to do (aside from install iTunes)
The problem is when I open the .exe files with Wine, for Photoshop it won't even open the installer, it's like I never gave it a command, and for the tablet driver it opens the installer then instantly shuts it down. I've grown too frusterated for words. Is there anything I can do to fix this problem?

Long story short: How do I keep Wine from shutting out of my installers, if it will even open them in the first place?

---

### Post by dankegel on 2010-11-11
First off: the appdb is your friend.  Have you checked what it says
about installing Photoshop yet?
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)
CS3, CS4, and CS5 don't install easily, and you have to jump through some
hoops.

Second: not too many people use tablets, so they aren't especially
well debugged in Wine.  I have used them, and had them work, but
I don't recall it being easy.  See e.g.
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/151448](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/151448)
for a problem report. 

I did my best to improve those two problems, but I couldn't focus
enough firepower on them, and they remain unsolved. 

My rule with Wine is: if it doesn't work straight off, don't put
yourself through lots of grief trying to make it work (unless you're
a developer/masochist like me).  

Time to find your windows media CDs that came with your computer
and go get your friend to put windows back on!

---

### Post by CrispyFriedUke on 2010-11-11
Thank you for your help!
I've thought about getting windows back on, but I can't find the disc, and despite my grief, trials, and all of the explicit words that have spewed out of my mouth in anger because of this computer I find myself hoping to beat it. I will certainly visit both of those links, and if no one can help me then, well, I suppose I have to admit that ubuntu beat me this round!

---

### Post by marl30 on 2010-11-11
> **CrispyFriedUke said:**
> For at least a week and a half now, I have been fighting with wine and pulling my hair out. I have attempted vigilance, but so far any tries I've made have proven utterly useless. So, my last resort is you kind folks here at the forums.

I'm sure my story isn't new. I had a friend fix my computer, expecting it to come back with windows, and I ended up with Ubuntu. I love having a computer again, but I hate having something that's about as worth my while as a several hundred dollar paper weight. I am grateful for what was done for me, but Ubuntu has proved to be useless to me, so far.
I want to work with it though.
So I tried to download Wine so I could put my Wacom tablet driver and my Photoshop on the computer. That's all I've been trying to do (aside from install iTunes)
The problem is when I open the .exe files with Wine, for Photoshop it won't even open the installer, it's like I never gave it a command, and for the tablet driver it opens the installer then instantly shuts it down. I've grown too frusterated for words. Is there anything I can do to fix this problem?

Long story short: How do I keep Wine from shutting out of my installers, if it will even open them in the first place?

The problem you're having with Wine... first of all, your OS is not set to use  Wine to open .exe files. You need to right click on the .exe file - go  to properties, then open with... select open with Wine. It will open all  exe files when you click on them after setting it to Wine. Next thing, Wine is not a replacement for  Windows; and currently it only runs about 60% of Windows applications  successfully. It's better you look for native Linux alternatives to your  Windows programs. For Photoshop, you might get C4 working perfectly through Wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)  If not, and you only use it for personal use, you might want to try Gimp, the open source Photoshop alternative. 

As for the driver you want to install for your tablet... you may need to check around the forum to see how to set it up Linux, or start a support thread in the support section. There are several great Linux alternatives for itunes: Rhythmbox, Banshee, along with others. Based on your needs in itunes, it's possible to find other suggestions from searching the forum.   

You need to look through the Ubuntu software Center for whatever software you want. If you keep trying to install all of the same Windows software you had on Windows, you'll be disappointed and can't wait to Dump Ubunut. Remember Windows programs were made for Windows, and not for Linux, so look for the Linux alternatives that will suite your needs.  Have a look through these sites to find the Linux alternatives for the softwares you are use to using in Windows. [http://alternativeto.net/software/?profile=linux](http://alternativeto.net/software/?profile=linux), [http://www.linuxalt.com/](http://www.linuxalt.com/)

---

