---
title: "Adobe photoshop cs4"
date: 2008-12-07
forum: Wine
---

### Post by qbox on 2008-12-07
Can same one give me good explanation how to install this application on wine. I have ubuntu 8.04 and wine 1.1.10
I follow this steps to install it
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514)
First time when I rin Setup.exe file, installation guide window opened in a small box 100x200 and I only see a "P" letter on it. I wondering what is wrong and I press Tab button. After more tab press I see a Install button in 100x200 box. I click on it. My output window give results all time. Some kind of fixme: and stuff....
Anyway
Somehow I finish the installation but The Photoshop wont run. I Try to make uninstall but Application freeze without any output. I simply delete Adobe folder and try to reinstall again. Now Installation guide wont run.
Can someone help me with this? I also have problems with CS 1.6 on wine. I post them here [http://ubuntuforums.org/showthread.php?p=6327332#post6327332](http://ubuntuforums.org/showthread.php?p=6327332#post6327332)
A lot application wont run on wine on my computer.......:confused:

---

### Post by qbox on 2008-12-11
Any one?

---

### Post by binbash on 2008-12-11
that howto is only for setup, i tried around 20 times to run photoshop  cs4, NO LUCK.you should go for cs2 or just like me use it inside vm.

---

### Post by joey-elijah on 2008-12-11
i ended up using Photoshop 7 (!) under Wine as my CS3 just wouldn't install or would then crash. 

I quickly got racked off and installed cs3 in an XP virtual machine. Having gone back to Vista atm, i'm using cs4 which is so much more impressive - mainly for it's 64bit support - that i'll likely be having a dual boot at best if i decide to install Ubuntu again (have tried via Wubi but it just will not work :( )

---

### Post by qbox on 2008-12-14
So... There is no way to make it work.... I install WinXP on another box. Only photoshop on it :)

---

### Post by alex.rayu on 2008-12-14
> **qbox said:**
> So... There is no way to make it work.... I install WinXP on another box. Only photoshop on it :)

Right. And also Flash and 3DSMax. =)

---

### Post by dannytatom on 2008-12-19
If it doesn't work, how does it have a gold rating on winehq?  Also, in the comments, people are saying it works *perfectly* with the winetricks library installed. ;o

---

### Post by qbox on 2009-01-02
I cant make it work.

---

### Post by alex.rayu on 2009-01-20
Neither CS3 nor CS4 install in 1,1,13

CS2 has been working for a long time now. Have no idea how could app db assign silver to cs2 and gold to cs3 and cs4.

See, I told you app db can't be trusted.

---

### Post by donkyhotay on 2009-01-20
All cs4 programs except illustrator and acrobat will install (though not all of them will launch correctly). You need to use winetricks to install both ie6 and msxml6 in order for the cs4 installers to run properly. You also need to install 0.9 gecko engine manually (winetricks version is out of date). There is a section on the wine appdb just for the adobe installer programs (focuses on suites but applicable to the standalone programs). It has the howto for making them run right. Here is a link:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514) 
Be aware many cs4 programs have problems with the menus not vanishing. There is a patch to fix it but you have to apply the patch to the source code and then compile in order to use it.

---

### Post by sasakitomiya on 2009-01-21
CS4 Didn't install it stopped working at "Preparing to install".  I looked in my wine config and found that I was running msxml3 not msxml6.  I fixed that but haven't run the setup.  Will let you all know if it works.

---

### Post by alex.rayu on 2009-01-21
I managed to install like this only if I select Photoshop and nothing else

But as photoshp starts, the splash hangs.

---

### Post by alex.rayu on 2009-01-21
I have reported a bug at Wine-HQ. After having installed the CS4, any app hangs after displaying a splash screen. [http://bugs.winehq.org/show_bug.cgi?id=17062](http://bugs.winehq.org/show_bug.cgi?id=17062)

For those capable of understanding, attached is a terminal output.

---

### Post by donkyhotay on 2009-01-21
Not certain about running photoshop, I maintain the installer and indesign for wine but don't really use photoshop itself. One thing I've found useful running many adobe programs in wine is installing the GDIplus through winetricks. If you still have problems running photoshop in wine after doing that post the contents of the terminal here and I'll take a look at it for you.


//edit: according to winehq photoshop should run with gdiplus installed. Take a look at:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318)

---

### Post by donkyhotay on 2009-01-21
Just out of boredom I installed photoshop and then gdiplus. Photoshop cs4 launched without any problems. I didn't really do much with it because I don't know how to use photoshop, the only obvious problem I found was the menu not vanishing which is a known issue and there is a patch for but requires recompiling wine to implement.

---

### Post by alex.rayu on 2009-01-21
Well I have no idea what causes the problem. I have tried both with MS gdi+ and the builtin. Same results.

---

### Post by donkyhotay on 2009-01-21
How did you install gdiplus? Are you using version 1.1.13 of wine? I tested using the 1.1.13 version of wine which is whats available from the winehq repositories (not necessarily the official ubuntu ones). Did you install the 0.9 gecko engine manually rather then with winetricks? This is important for cs4 as the winetricks version of gecko is out of date. Information on how to do this can be found at [http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko). I also installed gdiplus & msxml6 & ie6 using winetricks. Thats all I had to do from a fresh install of wine to run photoshop cs4.

---

### Post by alex.rayu on 2009-01-21
Yes I actually did that a number of times during the week. I reinstalled CS4 a number of times now. I will apply the patch the guy in Wine Bugzilla gave me. It appears my case is not very spread. 

Thank you for your support of the installer. You got the tough part!

---

### Post by donkyhotay on 2009-01-21
Yeah, the installer has been pretty straightforward for me once I figured out exactly what it needed to run (that took a bit of trial and error). Admittedly when I'm experimenting I use a new username where I can delete my .wine folder between installs to make certain there are no wierd registry keys or files floating around to interfere without affecting the programs I use all the time with wine. You might have something from another installation doing something unusual to your wine. Try creating a new user account (which of course will give you a fresh .wine folder without erasing whats already installed) and then run the steps I gave before and try again. That will determine if it's either a conflict with something in your wine configuration (i.e. registry problem) or with your version of wine/system as a whole.

---

### Post by alex.rayu on 2009-01-21
I have applied tha patch that the has offered. It did not help. I have then removed all wine, the .wine folder, and reinstalled as per your instructions. The installation went smooth but the same problem persisted. That is driving me nuts. Why should I be so special that it works for others but not for me =)

---

### Post by donkyhotay on 2009-01-21
> **alex.rayu said:**
> I have applied tha patch that the has offered. It did not help. I have then removed all wine, the .wine folder, and reinstalled as per your instructions. The installation went smooth but the same problem persisted. That is driving me nuts. Why should I be so special that it works for others but not for me =)

If you're using wine 1.1.13, created a new .wine folder, installed the 0.9 gecko engine, installed msxml6, installed gdiplus, installed ie6, and it *still* doesn't work then you have me completely stumped. I've never had a problem installing/running photoshop cs4 in that type of environment. Remember, the patch doesn't help with program launching (I don't have the patch and it launches just fine for me), it just fixes an annoying bug where the menu's don't go away if you have more then one open at a time.

---

### Post by alex.rayu on 2009-01-22
Yes I am also stumped. Will keep my ears open maybe will discover something in the future how to solve that. I am working on my windows desktop currently for production and am trying to set up my HP laptop to run Photoshop, Flash, and DreamWeaver.

Wait a minute! Can it be because I use ReiserFS? Can anything in Linux distro be influincing the Wine CS4 - like, my Interl X3100 video card, etc?

---

### Post by donkyhotay on 2009-01-22
Not that I know of but admittedly I always use ext3 for all my linux partitions and have never used reiserFS. The best way to test that out would be on a virtual machine. Try creating a VM of ubuntu with ext3 and see what happens.

---

### Post by birlindo on 2009-01-22
i guess only c2 works fine but c3 and c4 not but you can try vm ware or install win on other pc

---

### Post by donkyhotay on 2009-01-22
Photoshop cs4 does run, not perfectly and takes some tweaking but it does run. I know because I've done it on my own system and because of the reports on winehq. I'm not certain why alex can't get it to run right and it's the first instance I've personally seen where it wouldn't run after going through the specific steps I posted previously. I will admit though that wine can be pretty fickle and will occasionally do wierd things that makes no sense. It's something you have to put up with when you try running software in ways it was never designed for.

---

### Post by alex.rayu on 2009-01-23
Yeah it may appear something weird and foolish in the end that prevents it from running. But no way to figure it out now. I also know that when CS4 runs (for others), it crashes when using text tool. That has been confirmed and they are working on it but it appears to be tricky for them - they will need to implement at least one new function.

I have tried also to install CS3 meanwhile, but it fails after installing some of the Shared Components, and provides no reason whatsoever. It;s not Wine that fails, but the installer, so there is no output in wine debug.

That drives me nuts, because I once managed to install CS3 - and I did nothing special to install it. It just installed once, but that was it. Pure mystics!

---

### Post by AllRadioisDead on 2009-02-08
> **alex.rayu said:**
> Yeah it may appear something weird and foolish in the end that prevents it from running. But no way to figure it out now. I also know that when CS4 runs (for others), it crashes when using text tool. That has been confirmed and they are working on it but it appears to be tricky for them - they will need to implement at least one new function.

I have tried also to install CS3 meanwhile, but it fails after installing some of the Shared Components, and provides no reason whatsoever. It;s not Wine that fails, but the installer, so there is no output in wine debug.

That drives me nuts, because I once managed to install CS3 - and I did nothing special to install it. It just installed once, but that was it. Pure mystics!

I'm in the same struggle you are, I just tried installing CS3 and got the same thing.

---

### Post by jrusso2 on 2009-02-08
> **alex.rayu said:**
> Neither CS3 nor CS4 install in 1,1,13

CS2 has been working for a long time now. Have no idea how could app db assign silver to cs2 and gold to cs3 and cs4.

See, I told you app db can't be trusted.

Heck I can't even get Office 2000 to run it just keeps asking for the serial number each time it starts and that's platinum.

---

### Post by alex.rayu on 2009-02-09
Office 2000? :D What's it doing on your computer anyway? Can office 2000 be better than OpenOffice?

---

### Post by donkyhotay on 2009-02-09
Only if you think paying for an office suite makes it better somehow. (c;

---

### Post by arthpix on 2009-03-21
I've just installed Photoshop CS4 on my Ubuntu Hardy 64bit and it works pretty good, except for some strange behavior with the menus. Will try to explain all steps I did.

**Requirements:**
wine 1.1.17
msttcorefonts
winetricks
atmlib.dll

**Steps:**
1. Install wine or upgrade it to version 1.1.17
2. Install msttcorefonts from the repositories, either via synaptic or aptitude
3. Download winetricks and copy it to /usr/local/bin or just to your home folder if you don't want to mesh with your system.
4. chmod a+x winetricks
5. Execute winetricks msxml6 gdiplus gecko
6. download atmlib.dll from any download site, search google
7. Copy atmlib.dll to ~/.wine/drive_c/windows/system32/
8. Use wine configurator to set atmlib.dll to native
9. Install Photoshop normally
10. Load Photoshop, It should work - at least is working fine to me.
11. Aditionally, if you use a language other than English and receive a message saying something like "module not found amtsomething..." note the name of the dll and location displayed and copy it to ~/.wine/drive_c/windows/system32/ and set as native on wine's configurator

Those are the steps I followed, much based on Apdb's comments. Hope this work for someone else.

---

