---
title: "Wine  -- Browse C:\Drive error"
date: 2009-11-17
forum: Wine
---

### Post by Lolpanda on 2009-11-17
Apparently, a fairly common error as Google is turning up a lot of hits with similar stories, but alas, no fixes. 

Just installed Wine under Kubuntu (had these same issues on regular Ubuntu) When I installed Wine, it got the file path wrong and is producing the error..

 p, li { white-space: pre-wrap; }  Unable to run the command specified. The file or folder file:///home/eric/Documents/.wine/dosdevices/c: does not exist.




The directory DOES exist however in file:///home/eric/.wine/dosdevices/c

How can I change the Browse C Drive launcher to have the correct path? Last time when I simply moved the .wine folder to the Documents folder I would occasionally get errors revolving around Wine or at least downgraded performance. 

Any ideas?

---

### Post by beastrace91 on 2009-11-17
How did you install Wine and where did it install to? (By default it should be located in **~/.wine**) Also what is the exact Wine command you are running that is pointing it to your **~/Documents/.wine** for your Wine install?

~Jeff

---

### Post by Lolpanda on 2009-11-17
Installed wine through terminal, I get the error when I go to the KDE start menu > applications > wine > Browse C:\ Drive.

IT installed to ~/.wine, the coding seems to think that it SHOULDVE installed to ~/Documents/.wine

---

### Post by beastrace91 on 2009-11-17
Ahh. That goofy, I'd go file a bug report on that one.

For now if you need to view your drive_c just open your file viewer and go to **~/.wine/drive_c** (press ctrl+h to view hidden file and folders) Its just a issue with the Menu Link.

Regards,
~Jeff

---

### Post by malditonuke on 2009-11-28
> **Lolpanda said:**
> Installed wine through terminal, I get the error when I go to the KDE start menu > applications > wine > Browse C:\ Drive.

IT installed to ~/.wine, the coding seems to think that it SHOULDVE installed to ~/Documents/.wine


I'm using KDE 4.3 and had the same problem.  It's actually quite simple to fix:

1) Right-Click your KDE Kickoff Application Launcher to open the Menu Editor.
2) In the KDE Menu Editor, Find the "Browse C:\ Drive" item (should be under Wine), and select it.
3) On the right, click on the "Advanced" tab and change the Work path: from "/home/*username*/Documents" to "/home/*username*".
4) Click save, let it update system configuration, close the Menu Editor, and the problem should now be fixed.  :)

---

### Post by BigPhill on 2010-05-10
> **malditonuke said:**
> I'm using KDE 4.3 and had the same problem.  It's actually quite simple to fix:

1) Right-Click your KDE Kickoff Application Launcher to open the Menu Editor.
2) In the KDE Menu Editor, Find the "Browse C:\ Drive" item (should be under Wine), and select it.
3) On the right, click on the "Advanced" tab and change the Work path: from "/home/*username*/Documents" to "/home/*username*".
4) Click save, let it update system configuration, close the Menu Editor, and the problem should now be fixed.  :)


Hi guys, I am new in Linux. I love the graphics, I love the performance, I love the idea of no anti-virus I love the support. I believe I am going to ask many questions as I am clueless at to what is going on in Linux :). The only thing I am proud of myself is that I installed my system and all the applications in it (of course I did all this with the "How do I do this?". I stumbled on this problem of not being able to browse the C: Drive in wine. After 3 days of searching I finally to get the help here and that compelled me to be one of the Linux communities as I'm about to quit Windows and join this awesome community of this great OS. I hope to have wonderful time here and be able to contribute once I become familiar to the system. Ooops!! I didn't even know what the KDE Kickoff Application Launcher was, haaa. The application names are still foreign. Thanks.

---

### Post by Hollyecho_Montgomery on 2011-03-02
> **malditonuke said:**
> I'm using KDE 4.3 and had the same problem.  It's actually quite simple to fix:

1) Right-Click your KDE Kickoff Application Launcher to open the Menu Editor.
2) In the KDE Menu Editor, Find the "Browse C:\ Drive" item (should be under Wine), and select it.
3) On the right, click on the "Advanced" tab and change the Work path: from "/home/*username*/Documents" to "/home/*username*".
4) Click save, let it update system configuration, close the Menu Editor, and the problem should now be fixed.  :)
Thank you, thank you, thank you.  That did do the trick.

---

### Post by samtherottman on 2012-06-24
A had the same problem and now I can bowse my c drive. Thanks.

---

