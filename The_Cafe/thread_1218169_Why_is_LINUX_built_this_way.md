---
title: "Why is LINUX built this way?"
date: 2009-07-20
forum: The Cafe
---

### Post by Daremo_06 on 2009-07-20
Not a huge issue, but I am curious as to the thought process behind it.  

When you use the Nvidia hardware drivers GUI and you want to make changes (ie save to your confg file), you have to start it via command line using > gsku nvidia-settings

Why would you not give the default install of the GUI console root permissions to make changes to video?  I am just curious why its done this way.

---

### Post by Tony Flury on 2009-07-20
The reason i think is simple - consistency.

To Linux - every executable is the same - and its behaviour when executed is governed by three things :
1) The code than makes up the executable
2) The permissions set on the file
3) The user who asks for the programm to be executed.

Linux does not know (or care) what nvidia-settings does - and so when it is run it follows the same permissions model as everything else on linux.

To have linux "know" that a particular programm should execute as root without being explicitly told to do so, starts to take you down the path, where in theory someone willing to do so could execute any arbitary code as root, just by mimicing a "known" progamm.

---

### Post by Nevon on 2009-07-20
> **Daremo_06 said:**
> Not a huge issue, but I am curious as to the thought process behind it.  

When you use the Nvidia hardware drivers GUI and you want to make changes (ie save to your confg file), you have to start it via command line using 

Why would you not give the default install of the GUI console root permissions to make changes to video?  I am just curious why its done this way.

Not sure what that last part meant, but I'm guessing you're asking why the program is not given root permission automatically? Well, that would be quite counter productive as you have then negated any security gained from having a separate root account.

However, you're right in that it would be smart to have the launcher run ```
gksu nvidia-settings
``` instead of having users manually launch it or change the command in the launcher.

---

### Post by marco123 on 2009-07-20
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically the less security holes and vulnerabilities the better when it comes to network ready OSs.

Cheers, Marco.

---

### Post by Viva on 2009-07-20
Nothing to do with linux. The software doesn't add a menu item for gksu nvidia-settings. Some software do, but nvidia-settings doesn't.

---

### Post by Daremo_06 on 2009-07-20
So the reason it happens that way is more the fault (per say) of the package designer... 

That makes sense.

Also, obviously I am still some-what naive about Linux in that I did not realize a distro's developers did not necessarily create any given package.  I would bet that is a fairly common misconception.

Thanks for the answer though :)

---

### Post by chris4585 on 2009-07-20
> **Viva said:**
> Nothing to do with linux. The software doesn't add a menu item for gksu nvidia-settings. Some software do, but nvidia-settings doesn't.

On Ubuntu nvidia-settings doesn't make an icon, but on Arch it does.

---

### Post by FuturePilot on 2009-07-20
> **chris4585 said:**
> On Ubuntu nvidia-settings doesn't make an icon, but on Arch it does.

I does now actually. They fixed that problem a while ago.

---

### Post by chris4585 on 2009-07-20
> **FuturePilot said:**
> I does now actually. They fixed that problem a while ago.

Ah, I was just going on what others said, its been a while since I've had ubuntu with an nvidia card setup.

---

### Post by Sealbhach on 2009-07-20
I've got Nvidia Settings in my System/Administration menu - it was added there when I installed the Nvidia driver.


.

---

### Post by sisco311 on 2009-07-20
The related BUG report: [https://bugs.launchpad.net/hundredpapercuts/+bug/200868]("https://bugs.launchpad.net/hundredpapercuts/+bug/200868")

---

### Post by Daremo_06 on 2009-07-22
> **sisco311 said:**
> The related BUG report: [https://bugs.launchpad.net/hundredpapercuts/+bug/200868]("https://bugs.launchpad.net/hundredpapercuts/+bug/200868")

Well, that REALLY answered my question... it appears to be an conflict of opinions on what the right thing to do is.  Been going on for 3 releases now... interesting.

My take on it as a convert from windoze, is that when I am in a GUI app to make changes to my display settings and I see a button that says to save the configuration, then I should be able to click it, type in a PW if thats whats needed to properly protect things, and then save my changes.  Having me try that the 1st time, seeing it fail, doing it again and getting the same result just annoyed the hell out of me.  So then I had to break out the handy dandy google magic 8-ball and it told me to run it from terminal with gksu and presto done.

Thanks for the link, now I understand the actual problem.. human error (in the original design of the package) and disagreement on a solution (not that disagreement is a bad thing).

---

### Post by DoktorSeven on 2009-07-22
You do realize you can add a launcher to the start menu/desktop/panel yourself for any command that isn't there, right?

Sure, the package *should* do it for you, but it doesn't prevent you from doing it yourself.

---

### Post by Daremo_06 on 2009-07-23
> **DoktorSeven said:**
> You do realize you can add a launcher to the start menu/desktop/panel yourself for any command that isn't there, right?

Sure, the package *should* do it for you, but it doesn't prevent you from doing it yourself.

Yep I do, but my original thrust of my question was WHY would you have a package (application) that once its installed with a GUI interface, require then going to terminal to start it instead of it installing that way in the 1st place.  That seemed unnecessarly complex and definately non-intuitive.

So seeing that bug report showed me that its a disagreement about proceedure and not the norm in linux.

---

### Post by mister_pink on 2009-07-23
> **Daremo_06 said:**
> Well, that REALLY answered my question... it appears to be an conflict of opinions on what the right thing to do is.  Been going on for 3 releases now... interesting.

My take on it as a convert from windoze, is that when I am in a GUI app to make changes to my display settings and I see a button that says to save the configuration, then I should be able to click it, type in a PW if thats whats needed to properly protect things, and then save my changes.....

That is entirely possible but would involve the program being rewritten to use policykit. I assume its written by nvidea and isn't open source, so it would take the people at nvidia to fix it.

However, if its in the admin menu, it should probably have gksu in front of it, in the normal menu it shouldn't (as normal users can still use the program to view the settings even if they can't change them.)

It should also have some visual difference when you aren't running as root so its obvious you're not allowed to make changes.

---

### Post by markbuntu on 2009-07-23
The latest ati drivers have two launchers for the Catalyst Control Center which is their configuration app. One does not require root access so the user can change things like screen resolution, adjust colors, and make adjustments to the 3D engine etc. The other launcher is for changes that require admin access like configuring multiple monitors etc. You need an admin password to use this. 

This seems a reasonable approach. Now if they could get the drivers up to snuff...

---

### Post by mmix on 2009-07-24
you can use linux under chmod 1777 environment. :)

---

### Post by Daremo_06 on 2009-07-25
> **markbuntu said:**
> The latest ati drivers have two launchers for the Catalyst Control Center which is their configuration app. One does not require root access so the user can change things like screen resolution, adjust colors, and make adjustments to the 3D engine etc. The other launcher is for changes that require admin access like configuring multiple monitors etc. You need an admin password to use this. 

This seems a reasonable approach. Now if they could get the drivers up to snuff...

Actually the admin access to configure dual monitors is the issue.  I am running dual, and its only going to get more and more popular as flatscreens become more and more popular.

---

### Post by markbuntu on 2009-07-25
> **Daremo_06 said:**
> Actually the admin access to configure dual monitors is the issue.  I am running dual, and its only going to get more and more popular as flatscreens become more and more popular.

2 monitors is not such a problem, I just installed the latest driver from ati, 9.7 and could configure 2 monitors to a big desktop without admin privileges. Earlier drivers did not require admin privileges so any user could reconfigure the driver and it would apply globally which is not really desirable. Any user could use the Catalyst Control Center and disable all the monitors. This is no longer possible.

The thing about admin privileges now is that it is now the only way to reconfigure the login screen. So, there is very solid reasoning behind this privilege escalation scheme. This has only been adopted a few drivers ago and I think the devs are still feeling their way but it is seems to be a good direction.

btw, I now have 3 monitors on 2 gpus working and I definitely would not want someone without admin privileges to attempt that with this driver.

---

### Post by Daremo_06 on 2009-07-27
> **markbuntu said:**
> 2 monitors is not such a problem, I just installed the latest driver from ati, 9.7 and could configure 2 monitors to a big desktop without admin privileges. Earlier drivers did not require admin privileges so any user could reconfigure the driver and it would apply globally which is not really desirable. Any user could use the Catalyst Control Center and disable all the monitors. This is no longer possible.

The thing about admin privileges now is that it is now the only way to reconfigure the login screen. So, there is very solid reasoning behind this privilege escalation scheme. This has only been adopted a few drivers ago and I think the devs are still feeling their way but it is seems to be a good direction.

btw, I now have 3 monitors on 2 gpus working and I definitely would not want someone without admin privileges to attempt that with this driver.

Yes, I did the same thing setting mine up as well.  Its when you want to save the config to xorg, then you need privileges.  A simple fix would have a script pop up saying that if you want to save changes, login to the gui via terminal to be able to have permission to do it.  

Since your running 3 screens, I have a question for you.  I assume you have an aftermarket dual capable card installed plus your using the MOBO video output, correct?  I have an ATI card and an IBM MOBO, how do you get the system to recognize the IBM video?  Last time I played with this, it didn't seem to be able to recognize it.

---

### Post by markbuntu on 2009-07-29
Actually I am using two cards and have the mobo gpu disabled because it was causing me problems whenever I tried to use it with either of the cards. I am pretty sure it is a bios issue. Anyway, I had the two cards, the mobo gpu was never intended to be used anyway but I did give it a try because it was supposed to work with one of the cards at least but I gave up since it was not that important to me.

Unless you have a very recent mobo and even if you do there is a very good chance you will not get the mobo gpu to work with the card. At least that is my experience and I have a TA790GX A2+ mobo with a HD3300 and a HD3450 card and a HD3650 card. Until the latest drivers it was not possible for me to use even the two cards together. If you want three monitors I would suggest another ati card and read the release notes on the driver.

---

