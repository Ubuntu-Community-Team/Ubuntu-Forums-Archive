---
title: "Wine"
date: 2010-08-07
forum: Wine
---

### Post by beew on 2010-08-07
Hi, 

I need WINE for one program (WinBUGS14 ) .After installation it started ok, but all the hyperlinks in the program don't work (So for example, I cannot open the help file or check updates) I wonder if anyone has experienced similar problems? Are there problems in getting on the internet in general with WINE? I think it may have something to do with permissions. 

I have only tried WINE with a few small programs to see what it  is capable of, so far it seems that it is very unstable and horribly broken, nothing ever works. But then maybe I am not setting it up properly because it seems that quite a few people are using it ,

Finally, is there a way to completely get rid of WINE? Even when I have "completely remove" Wine and the .wine folder in the /home directory, Wine and the old programs still appear in the drop down menu and it seems to remember the old settings even when I reinstall Wine and reinstall the  wine programs.

---

### Post by Paddy Landau on 2010-08-07
To reset Wine settings to default, delete the directory .wine from your home directory (note the "." in front of the directory name). *EDIT* I misread your original post, sorry. I don't know how it is that it remembers your settings.

Wine is not guaranteed to run Windows programs. It's not complete.

I recommend that you install [PlayOnLinux]("http://playonlinux.com/"), which is a front-end to Wine, because it makes it really easy to install, run and uninstall Windows programs using Wine.

You can also look at [CodeWeaver's website]("http://www.codeweavers.com/compatibility/"); it gives a good indication of whether a specific program will run under Wine.

---

### Post by beew on 2010-08-07
I think playonlinux only works with WINE1.2 or above, but WinBUGS (a program for Markov Chain Monte Carlo sampling) wouldn't even install with WINE1.2 and I am using WINE1.0 from the Ubuntu repository. It installed and appears to run but all the hyperlinks are disabled

Yeah, I did remove the ./wine folder but somehow it remember things! (like in a horror movie)

---

### Post by anand_30 on 2010-08-07
> **beew said:**
> Hi, 

I need WINE for one program (WinBUGS14 ) .After installation it started ok, but all the hyperlinks in the program don't work (So for example, I cannot open the help file or check updates) I wonder if anyone has experienced similar problems? Are there problems in getting on the internet in general with WINE? I think it may have something to do with permissions. 

I have only tried WINE with a few small programs to see what it  is capable of, so far it seems that it is very unstable and horribly broken, nothing ever works. But then maybe I am not setting it up properly because it seems that quite a few people are using it ,

Finally, is there a way to completely get rid of WINE? Even when I have "completely remove" Wine and the .wine folder in the /home directory, Wine and the old programs still appear in the drop down menu and it seems to remember the old settings even when I reinstall Wine and reinstall the  wine programs.

I also use Wine for autocad 2004 and it works perfectly but before installing any program you should check at [http://www.winehq.org]("http://www.winehq.org/").Search for your program and check its rating.Gold and silver is good,even bronze works up to your expectations.Regarding internet issue,i may say that you can't have performance of program as same as that in windows,but its very good and its amazing how Wine is developing. 

I think so as to remove entries of programs which you have uninstalled or removed manually,instead of completely removing wine and again installing it you should install CCleaner using wine,and fix all issues of registry and reboot.Entries will be gone,it works for me.

Hope this helps.

---

### Post by beew on 2010-08-07
Thanks anand, so are you saying that the hyperlinks are not supposed to work and wine programs by design cannot go online?

---

### Post by beew on 2010-08-07
If anyone knows of a Linux replacement for WinBUGS I can easily live without WINE. The only reason that I am keeping Windows is because I need SAS, but I am going to shrink the Windows partition so drastically that basically running SAS is all that it does (well I may not have enough ram to use virtualbox even if it works) 

I like R and it runs natively in Linux (so I am not intending to keep a copy of R in windows) But R calls WinBUGS in it so I do need WinBUGS. 

In windows they work with  each other seamlessly but in Linux it would be tricky since WINE is  involved. The WinBUGS people have tried to come up with Linux native  versions (LinBUGS and OpenBUGS) but they couldn't get them to work. If  you visit their websites you will be greeted with a message that  basically says that there is no package to download because they have  not been able to make them work, and that if you know how to fix them  please email them etc and the websites have not been updated  since something like 2007. It appears that they have given up.

---

### Post by beew on 2010-08-07
Ok just figured out a way to really kill Wine. 

1. Completely remove all the wine entries from synaptic. Or better, in  the terminal type

```
 sudo apt-get purge wine 
```  You may want to use wine* instead if there are other wine packages. I read somewhere that the terminal method is more through than synaptic even though they should be the same.

2. Delete /home/usrname/.wine

At this point the settings still remain,  if you go to the Applications drop down menu you would see wine is still there along with all the wine programs you have supposedly uninstalled. If you reinstall wine and reinstall the old programs the old settings would apply.

3. Go to /home/user name/.configs/menus/applications-merged and delete all the wine entries.

Then it seems that you are clean, everything in the drop down menu relating to wine is gone.

If you don't want to kill wine but only want to remove some wine programs with their settings I think you can just do 3 and instead of deleting everything related to wine, delete only those files which are relevant to the programs you want to wipe.

Now I have not attempted to reinstall wine yet. But I think if you do some fresh copies of the files you delete in 3 will be regenerated so you start everything fresh.

The other question still has no solution. Still don't know how to make the links in WinBUGS work in Wine or whether it is possible.

---

### Post by cariboo on 2010-08-07
Moved to the Wine sub-forum

---

### Post by cwwilson721 on 2010-08-07
There are TONS of wine settings in /home/<USER>/.local/share/applications

---

### Post by beew on 2010-08-07
> **cwwilson721 said:**
> There are TONS of wine settings in /home/<USER>/.local/share/applications


I think those are desktop files rather than settings, I could be wrong of course.

---

### Post by cogadh on 2010-08-07
Yeah those are not Wine settings, they are just shortcuts. The only place to find Wine settings is through winecfg, which is essentially a front end for editing the exposed portions of Wine's version of the Windows registry.

OK, a couple of clarifications are needed here:
1. The .wine directory is everything that can be configured in Wine, including the "fake Windows" directories that all applications installed via Wine can be found in. By deleting this directory you are in fact deleting all of Wine's settings and restoring it to its default freshly installed state. Essentially, uninstalling the Wine package, then deleting the .wine directory eliminates all traces of Wine.
2. Shortcuts are always left behind after an uninstall/purge of Wine, but they will not work. The leftover shortcuts in the applications menu can be deleted via the method described above, but sometimes it is just easier to use Gnome's built-in menu editor.

---

### Post by anand_30 on 2010-08-08
> **beew said:**
> Thanks anand, so are you saying that the hyperlinks are not supposed to work and wine programs by design cannot go online?

No thats not the case.Its not that Wine programs by design can not go online.

e.g.I have another CAD called progeCAD smart 2009 from which i CAN go to their official website and also go to for online support which is a forum.

Only thing is that programs don't work completely.My autocad help page is blank same is the case with ProgeCAD,so you have live with them,but in your case i really don't seem to have a solution coz Hyperlinks are essential for you and there is no other alternative for WinBUGS14 for linux.

I will say stick to search maybe you will get one.

---

### Post by Paddy Landau on 2010-08-08
> **beew said:**
> I read somewhere that the terminal method is more through than synaptic even though they should be the same.
If you "Mark for Removal", then indeed; but if you "Mark for Complete Removal", then I understand that it's the same as purge.

> **beew said:**
> If you don't want to kill wine but only want to remove some wine programs with their settings I think you can just do 3 and instead of deleting everything related to wine, delete only those files which are relevant to the programs you want to wipe.
That's why [I recommended PlayOnLinux]("http://ubuntuforums.org/showthread.php?p=9690211#post9690211"). It will handle all that stuff for you.

---

### Post by beew on 2010-08-08
Ok, the hyperlinks appear to be working now after I reinstalled WinBUGS (they link to other manual documents rather than the net as it turns out). Though sometimes it may take many clicks to open them up! It seems to run as well and the result is consistent with the result in windows. So I guess it is working afterall.  I would mark this as solved but for one little wrinkle. I am getting an error message whenever I run  WinBUGS or opening a manual link. (see the screenshot). Does anyone know what it means?

---

### Post by beew on 2010-08-08
Paddy Ladau

> If you "Mark for Removal", then indeed; but if you "Mark for Complete Removal", then I understand that it's the same as purgeThat was my understanding too.But I was reading some threads about removing gnome network manager and installing wicd on these forums. They say wicd wouldn't work properly if there are remnants of nm left in the system. Some people claimed that for some reasons "completely remove" in synaptic doesn't work as advertised and you have to use  "sudo apt-get  purge" to make sure gnm is gone. I don't know if that is true or not,  nor do I remember which version of Ubuntu they were talking about. I mention it just in case.

> That's why [I recommended PlayOnLinux]("http://ubuntuforums.org/showthread.php?p=9690211#post9690211"). It will handle all that stuff for you.To inslall PlayOnLinux you have to install Win1.2 as a dependency and WinBUGS crashes as soon as it opens in wine1.2. That's why I have to install wine1.0 and wgjig-hold all wine updates.

---

### Post by cogadh on 2010-08-08
> **beew said:**
> 
To inslall PlayOnLinux you have to install Win1.2 as a dependency and WinBUGS crashes as soon as it opens in wine1.2. That's why I have to install wine1.0 and wgjig-hold all wine updates.
However, POL has this nifty feature that allows you to maintain two separate versions of Wine installed at the same time. That way you can have 1.2 installed as required, but can also have 1.0 installed for those apps that need it.

---

### Post by Paddy Landau on 2010-08-09
> **beew said:**
> ... I was reading some threads about removing gnome network manager and installing wicd on these forums. They say wicd wouldn't work properly if there are remnants of nm left in the system...
Curious. I have just changed two computers from network-manager to wicd, using the GUI. I had one problem, that of Samba failing to work, for which I'm still seeking a solution. Is that what people were talking about?

> **beew said:**
> To install PlayOnLinux you have to install Win1.2 as a dependency and WinBUGS crashes as soon as it opens in wine1.2. That's why I have to install wine1.0 and wgjig-hold all wine updates.
What a mess! I hope [cogadh's insight]("http://ubuntuforums.org/showthread.php?p=9695520#post9695520") helps you get it right.

---

### Post by beew on 2010-08-09
Paddy Landau

No, it wasn't about Semba. They couldn't even get wicd working. But then they couldn't get nm working either. nm works perfectly for me, but connections with wicd has been unreliable so I was looking around for trouble shooting hints. Not that I need wicd, but I was curious(still am) where the problems might be.

---

### Post by beew on 2010-08-09
> **cogadh said:**
> However, POL has this nifty feature that allows you to maintain two separate versions of Wine installed at the same time. That way you can have 1.2 installed as required, but can also have 1.0 installed for those apps that need it.

I have installed wine1.3 and POL. From POL I clicked to install a copy of wine1.0. It said the installation had been successful but I don't know where it was installed. I checked synaptic and the box for wine1.0 was not checked so it had not been installed system wide (understandable as otherwise synaptic would remove wine1.3) I thought maybe it was a local version  installed inside wine 1.3 but couldn't find it in the .wine folder either.

Now if I have two versions of wine how do I run commands like "$ wine programname"? I mean, how does linux know which wine? Should I do something like "$ wine wine1.0 program"? as wine1.0 presumably lives inside wine1.3 which is the system wide version?

---

### Post by beew on 2010-08-09
I have two Ubuntu installations. In one I have wine1.3 (and supposedly wine1.0 too but I don't know where it is, see above) and in another I have wine 1.0.

WineBUGS appears to work in wine1.0 but not on wine1.2 or wine.1.3.  When I run WinBUGS in wine1.0 it prints out some error messages but otherwise works. Even those hyperlinks work now. Turns out they don't work with the touch pad,--or it took  many clicks to open a link hence I thought they didn't work at first,-- but  they work with the mouse nicely, except that you have to click in a peculiar way with one left click followed by a right click almost immediately but not simultaneously.:confused:

In wine 1.3 though whenever I open WinBUGS it just crashes (apparently with the same error messages that I got when running it in wine1.0, have to check to make sure..) 

Here are the error messages, any thought?
```
fixme:keyboard:RegisterHotKey (0x20056,13,0x00000002,3): stub
err:ole:CoGetClassObject class {0003000a-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject class {0003000a-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {0003000a-0000-0000-c000-000000000046} could be created for context 0x3


```


Thanks

---

### Post by cogadh on 2010-08-09
Regarding the multiple Wine versions, have you checked the POL documentation? It should explain everything (yes, I am basically saying "RTFM", sorry).

---

### Post by Paddy Landau on 2010-08-09
> **beew said:**
> Now if I have two versions of wine how do I run commands like "$ wine programname"?
You don't. Use PlayOnLinux to install, run and uninstall.

If you've already installed programs through Wine, I recommend that you uninstall them, and reinstall through PlayOnLinux.

When you install a program through PlayOnLinux, you specify which version of Wine to use for that program.

PlayOnLinux hides a lot of the complexity of Wine from you. I personally haven't the faintest idea how to use Wine. I only use PlayOnLinux.

---

