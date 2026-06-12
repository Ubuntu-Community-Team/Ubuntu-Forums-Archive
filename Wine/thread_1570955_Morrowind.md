---
title: "Morrowind"
date: 2010-09-08
forum: Wine
---

### Post by Saronn on 2010-09-08
I installed Morrowind through Steam, and when I try and start it up, it shows the "Preparing to Launch Morrowind..." box, but after that nothing happens. 

I'm using Wine 1.2-rc6.

---

### Post by cwwilson721 on 2010-09-08
Hmm....

Here's the answer:


[LIST]
[*]Goto [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
[*]Click on "Search This Forum"
[*]In the box, type in "Morrowind"
[/LIST]
Answer is in there.

Try a search FIRST, then ask. (Not being a jerk, but it took me all of 2 minutes to search, and find the answer)

---

### Post by Saronn on 2010-09-08
> **cwwilson721 said:**
> Hmm....

Here's the answer:


[LIST]
[*]Goto [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
[*]Click on "Search This Forum"
[*]In the box, type in "Morrowind"
[/LIST]
Answer is in there.

Try a search FIRST, then ask. (Not being a jerk, but it took me all of 2 minutes to search, and find the answer)

I just tried what you said... I didn't find anything that helped at all. :-s

---

### Post by Saronn on 2010-09-09
Well... I got Morrowind working, I ran it in the terminal and found out I was missing a DLL file. I downloaded it, and it works. Although, after I start a new game and all, the game crashes when I try exiting the hatch. The one right when you start the game.

I've tried editing my registry, changing my winecfg settings, changing morrowind.ini, and nothing works. I don't think theres much else to do.

---

### Post by cwwilson721 on 2010-09-09
You DID check the winehq db, right?

---

### Post by Saronn on 2010-09-09
I just checked the morrowind winehq and looked at all of the posts and bugs for almost all of the reports, and nothing fixed it.

---

### Post by Saronn on 2010-09-09
bump...

---

### Post by spoons on 2010-09-11
Have you updated to the latest wine release?

---

### Post by borth92 on 2010-09-11
wine is very buggy to use for gaming. I would suggest a windows partition (even a really small one) for games. o and btw be careful installing windows after ubuntu, it will wipe out grub.

---

### Post by Saronn on 2010-09-11
> **spoons said:**
> Have you updated to the latest wine release?

I'll try that now.

EDIT: Well that did't help...

---

### Post by Saronn on 2010-09-12
bump, anybody have anything useful for me to try?

---

### Post by beastrace91 on 2010-09-13
Current Wine version? Graphics card? Graphics card driver version? Terminal output when the game crashes?

Help us, help you,

~Jeff

---

### Post by Simian Man on 2010-09-13
Wine is a crap-shoot at best.  I think the suggestion of a Windows partition is the best help you are likely to get.

---

### Post by Saronn on 2010-09-13
I can't get a Windows partition, so that's out of the question. I wouldn't make this thread if Morrowind COULDN'T run on Linux.

There isn't any terminal output. I ran morrowind.exe and morrowind launcher.exe in the terminal and neither give any output.

I'm using the latest Wine version. 1.3.2 I think?

And my graphics card is definitely capable of running Morrowind.

---

### Post by cwwilson721 on 2010-09-13
> **Saronn said:**
> I can't get a Windows partition, so that's out of the question. I wouldn't make this thread if Morrowind COULDN'T run on Linux.

There isn't any terminal output. I ran morrowind.exe and morrowind launcher.exe in the terminal and neither give any output.

I'm using the latest Wine version. 1.3.2 I think?

And my graphics card is definitely capable of running Morrowind.AND > **beastrace91]              **Re: Morrowind**
         Current Wine version? Graphics card? Graphics card driver version? Terminal output when the game crashes?

Help us, help you,

 ~Jeff     [/QUOTE] If you run wine in the cli, it ALWAYS gives output.

What is your vidcard? driver? You have been rather obstinate this entire thread.

I'm assuming you don't WANT help.

From the sticky: [QUOTE][SIZE=5]**Things you should try before asking for help:**[/SIZE]
[LIST=1]
[*]***Check AppDB*** - Wine's [Application Database]("http://appdb.winehq.org/")  is one of the best sources for help with running apps in Wine. First  and foremost, it will tell you when an application is not worth trying  at all. Secondly, but almost as important, an application's AppDB entry  may include how-to information on the proper way to install and run your  application.
[*]***Never run Wine with sudo*** - Do not run Wine as root or  by using sudo.  Doing so doesn't help anything and will break your fake  Windows installation entirely.
[*]***Do not try and install DirectX*** - Wine already has its own implementation of DirectX, and attempting to install the Windows version will simply break things.
[*]***Reinstalling Wine won't help*** - Reinstalling the same  Wine package in Synaptic won't do anything - your virtual Windows drive  and applications will be just the same unless you manually remove them.   What you probably wanted to do is erase your fake Windows install  entirely said:**
> ***Use the restricted drivers for your video card*** - many  graphics issues in Wine are due to missing features in the free drivers  for various video cards.  Try enabling the proprietary drivers for your  video card, if available, using the restricted drivers manager.
[*]***Update Wine*** - Unless the information you obtained from  AppDB told you the latest version of Wine won't work, you should try  updating to the most current version of Wine. Each update includes many  bugfixes that can correct your issue. However, it is important to note  that an update could include new bugs or regressions that will cause  problems with some applications.  If you are manually selecting  versions, please note that they are two digit numbers: Wine 1.1.10 is  newer than 1.1.9.
[*]***Search the forums*** - There are many, many posts on  running specific applications in Wine already. Chances are really good  that someone has already asked the same question you have.
[*]***Try different Windows versions*** - Even though the  application you are trying to run was made for Windows 98, it may work  better if you set the OS version in Wine to Windows XP or Windows Vista.
[*]***Check the terminal output*** - Perhaps I should say "*Use the terminal*"  first. When run from the terminal, Wine outputs any error messages to  the terminal window, which may tell you exactly what is wrong. This is  especially useful for identifying when a DLL is missing and an override  may be needed. Check the output for details like that and anything else  that may identify where your error is occurring.
[/LIST]

[SIZE=5]**Things to include when asking for help:**[/SIZE]
[LIST=1]
[*]***Wine version***  - Wine is updated roughly every two weeks. Each update includes  numerous changes and fixes. Knowing which version you are using can  often lead to very specific fixes for whatever problem you may be having
[*]***Terminal output*** - Run your application from the  terminal and include the output in your post (make sure you use the  forum CODE tags). The informational and error messages provided in the  terminal can be very helpful in pinpointing where the problem is  occurring
[*]***Wine configuration*** - How you have Wine configured  changes how Wine behaves greatly and may be the cause of whatever issue  you may be having. Configuration items to consider including are :
[LIST]
[*]OS version
[*]Library overrides
[*]Sound settings, all options
[*]Graphics settings, all options
[*]Registry edits
[/LIST]
[*]***Hardware specs/drivers*** - This is especially important if the application you are having issues with is a 3D game.
[*]***Other Wine applications*** - Include any other apps you  may have installed in your Wine directory.  Be sure to mention if you've  used third party tools like winetricks or PlayOnLinux.
[/LIST]
Providing this info will greatly increase the chances that someone on these forums will be able to help solve your problem.

[SIZE=5]**If Wine is causing complete system crashes:**[/SIZE][INDENT]If  using Wine causes very nasty problems like system freezes requiring a  hardware reset or the xserver crashing and dumping you back to the login  screen, then there is a deeper problem with your system that Wine is  simply exposing.  The most common cause of this is problematic drivers.   Upgrading to the latest Ubuntu release can often solve these problems.
Did you do all the above?
[/INDENT]

---

### Post by Half-Left on 2010-09-13
> **borth92 said:**
> wine is very buggy to use for gaming. I would suggest a windows partition (even a really small one) for games. o and btw be careful installing windows after ubuntu, it will wipe out grub.

It's not that it's buggy, it's that well, directX isn't open source so they cannot or it takes them a long time to implement directX functions. A lot of WINE developement has been a shot in the dark but it works great considering.

---

