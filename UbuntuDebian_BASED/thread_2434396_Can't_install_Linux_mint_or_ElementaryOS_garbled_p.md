---
title: "Can't install Linux mint or ElementaryOS: garbled pixels appear on screen."
date: 2020-01-05
forum: Ubuntu/Debian BASED
---

### Post by behealed on 2020-01-05
I have a brand new OMEN by HP Obelisk Desktop 875-0xxx, which are still available to buy from Best Buy / Conns, and it comes with a monitor and all the works, and I've made no modifications to the PC itself. It has windows 10 and so I'm looking to setup a duel boot. I know how to do it because I just did it successfully on my gaming laptop. Now I'd like to do the same on this desktop, but it's not happening.

Here's the specs on the PC:

Intel(R) Core(TM) i7-9700F CPU @ 3.00GHz (8 CPUs), ~3.0GHz
NVIDIA GeForce RTX 2060
16384MB RAM

I'm installing these linux distros (which are based on Ubantu) to a USB thumb drive, and then attempting to run the first option that appears after boot, which for linux mint is something like "run linux mint" (sorry if that seems overly obvious). I am not yet at the part where I actually install linux to the hard drive. It's still on the thumb drive at this point. I need to boot into linux first, before I can install it. So nothing has been done to the hard drive yet. Nothing to do with the duel boot has been done yet. I'm just attempting the first boot from the usb thumb drive. 

And what happens on the laptop was everything booted up, the desktop appeared, and I could then install linux to the hard drive and setup the duel boot.

But on the desktop, as soon as I select the first option and attempt to boot up linux, there's garbled pixels that appear on the screen and I can't tell if it is successfully making it to the desktop or not. I end up having to hard reset the computer by holding down the power button. The garbled screen is pretty much identical whether it's linux mint, or elementaryOS. So the problem must be that both are based on Ubantu, which is why I'm here on the main Ubantu forum asking about this.

I'm new to linux, btw. So I don't know much.

Here's a screenshot of the garbled pixels. This was with Linux Mint, selecting the "compatability mode" option in its boot up screen. Again, this is running on the USB thumb drive only, prior to making any changes to the hard drive: 

[ATTACH=CONFIG]284753[/ATTACH]

Just to be absolutely sure that the problem wasn't due to a faulty sector on my usb thumb drive, I did run a full test on the drive and I reformmated the drive several times in the process of trying both mint and elementaryos, and in all tests the drive has been found to be clean and free of problems. Also the PC itself runs windows and games flawlessly, so I don't think the problem is with the PC. My guess is that it's a newish PC and Ubantu just doesn't support some of the hardware yet.

But is there a way to see a log or something that would revel what exactly is the cause of this garbled pixels?

---

### Post by CatKiller on 2020-01-05
> **behealed said:**
> NVIDIA GeForce RTX 2060

You may need to use the nomodeset option for the install and initial boot, until you can install the proprietary nvidia driver for your card. With a newer card like that you'll need to use the graphics driver ppa to get a driver new enough. 

I believe you need to press "E" at the first menu to edit the kernel line. Where it says "quiet splash" replace that with "quiet splash nomodeset". It tells the graphics system not to bother trying to set the resolution, which the open source nouveau driver sometimes struggles with.

---

### Post by behealed on 2020-01-05
This totally worked (but... I have other probs now, see below)! You are a guru.

This let me in, and I was able to install linux.

However, now that that's done, when I boot it gets me to the log in page (to enter my password), even though I selected that no password should be required on boot. And if I type my password incorrectly, it fails as expected. But if I type the correct password, it just does nothing, and continues to ask for a password, with no error message. If I click the button to restart or shut down, which is one of the only buttons available from the login screen, then it that also does nothing, and continues to ask for the username and password (the box to shut down disappears, which leaves me back at the login screen). From the perspective of a 30 year windows user, my best guess is that there is literally nothing loaded in the background, so attempting to perform any action (such as typing the correct password, or asking to shut down), results in nothing happening because nothing CAN happen because there's no desktop or api or backend or whatever loaded, so it detects that the password is correct but that's about it and it can't remove the login screen and show the desktop because there is none loaded. But I'm new the linux so this is just a guess.

So if I restart and select the second option, which I think is the advanced options or whatever, then I can pick the second optionn which is to boot with recovery mode. I select that, and dumps a bunch of text to the screen, and then takes me to a glitchy screen (console-looking text appearing in wrong places on the screen) and gives me me the option to "resume normal boot". If I select that, then it warns that some drivers may malfunction, but then bingo, the desktop appears without asking me for a password (which is what I selected during installation) and seems like everything is working just fine. Welcome to Ubantu I guess? But I hate to use that as a permanent solution though, especially with that warning about the drivers, since odds are something probably isn't working I just haven't seen it yet.

So for now I'm having to boot in recovery mode at first, and then resume normal boot. Tried multiple times just to be sure, but it definitely takes me to a login screen that won't go away if I try a normal boot, with no option on that screen other than to hold down the power button and hard shut down the computer.

You'll probably hate me for this but I installed the 19.10 Ubantu, rather than the long term one. I guess I figured since I was on newer hardware it would be best to go for the latest ubantu, in the hopes it would have more hardware support. That said, I still had to do that fix that you gave in your first post (it gave the same garbled pixels otherwise). So now I'm wondering if the older Ubantu would have worked better. Maybe 19.10 has a bug that snags you forever at a log in screen that won't go away? ;p Somehow I doubt that but I know nothing basically.

---

### Post by coffeecat on 2020-01-05
> **behealed said:**
> You'll probably hate me for this but I installed the 19.10 Ubantu,

No one is going to hate you - simply advise you on the pros and cons of your choice. But please clarify exactly which operating system you have installed. You started with Mint and Elementary, but you now appear to be on the parent Ubuntu. Which have you installed? Those helping need to know.

Ubuntu not Ubantu, by the way. The word has a meaning in its original language.

---

### Post by yancek on 2020-01-05
If I'm reading your post correctly, you seem to be having trouble with a login loop as described at the link below.  If that is the case, you could try the solution explained at this link.  This is not a new problem so if this doesn't work, try an online search for 'login loopg ubuntu' and you should get a number of sites.

[https://www.maketecheasier.com/fix-ubuntu-login-loop/](https://www.maketecheasier.com/fix-ubuntu-login-loop/)

Have you installed the proprietary Nvidia drivers as explained at the link below?  Open Software and Updates and select the Additional Drivers option and wait for it to finish.

[https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/](https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/)

---

### Post by CatKiller on 2020-01-05
> **behealed said:**
> From the perspective of a 30 year windows user, my best guess is that there is literally nothing loaded in the background, so attempting to perform any action (such as typing the correct password, or asking to shut down), results in nothing happening because nothing CAN happen because there's no desktop or api or backend or whatever loaded, so it detects that the password is correct but that's about it and it can't remove the login screen and show the desktop because there is none loaded. 

And you'd be wrong. Windows user concepts do not transfer to using Linux. Windows power users have, by far, the hardest time making the transition because their instincts are all wrong. 

In this case, some misconfiguration is causing your X server to crash (or a Wayland session to fail to start, since Wayland doesn't really work on nvidia hardware) and the very first thing that you see when an X session (re)starts is the login screen. 

You've not said whether or not you've got round to installing the proprietary driver. Especially on new nvidia hardware that is a must. Your Windows user instincts will tell you to go to some website and download some random thing, which would be exactly wrong. 

Instead you should add the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) as a source of packages for your package manager to choose from. Should you still not be able to log in normally to do that, it is possible to do both steps (add the PPA, install the driver) from the command line, but it sounds like you've managed to stumble on a workaround for getting to the desktop. Once your package manager knows about the existence of that PPA the software from it will show up in all the package management places - Software Centre, Additional Drivers, Synaptic, apt-get, whatever you prefer. The 440 branch is the one that you should probably prefer.

---

### Post by behealed on 2020-01-06
Thanks all of you for the help.

I did switch to the regular Ubuntu distro. I thought it looked more beefy, and those other distros seemed like "lite" versions. But that was just my assumption after like an hour, so I could be wrong. lol.

Also, I was on a proprietary nvidia driver already (which it seemed to have done automatically when I installed). I forgot the version number but it was the latest "verified" proprietary nvidia driver, which comes automatically with the version 19 ubuntu (it might not come automatically with ubuntu 18). However as you all recommended I did install the PPA and switched to a slightly more recent version which was 440, which for some reason it says is "open source". I also downloaded the 440.44 directly from the nvidia (from [https://www.nvidia.com/Download/driverResults.aspx/156086/en-us](https://www.nvidia.com/Download/driverResults.aspx/156086/en-us)), which gave me a .run file that I don't really know how to run (the instructions looked difficult). So I didn't use the .run file and all I did was download the PPA and go to drivers and switch to the 440 open source version that it added, and rebooted, and the change could be seen in the nvidia configuration window thingie. Note that the "open source" didn't say 440.44, it just says "440", so I donno if that's a problem I should be concerned about.

But switching to the 440 open source version changed nothing and I'm still stuck in the login loop. So I tried the link that yancek gave, which suggested to change permissions on .Xauthority file, but I'm unable to do that because there doesn't seem to BE an .Xauthority file in my home folder. Here's screenshot of my home folder:

[ATTACH=CONFIG]284754[/ATTACH]

As you can see, there's no .Xauthority file. I tried this from the desktop (using my workaround of first booting in compatibility mode, and then exiting compatibility mode, which reveals the desktop), and also I tried it as the website recommends, by not logging in and going straight from the login screen to the terminal (via ctrl + alt + f4). Both ways failed the same, due to there not being any .Xauthority file. Also, typing** ls -lah | grep -i Xauthority **seemed to do nothing.... it would just act like I had pressed Return without typing anything at all. Not experienced enough with linux to even guess as to why. 

As a 30 year user of Windows, and a first time user of linux, I must say that this whole installation process has raised my respect for Windows stability. I'm not installing linux because I think it's more stable. Obviously the advantage of windows is that, at least it usually installs and boots up on the first try. I'm coming to linux because I'm trying to get into some disassembly work (blue hat), and Windows has too many features that you can't control, such as mandatory ASLR. But linux is more flexible and lets you control pretty much everything. I guess for now I'm just gonna have to use my workaround to get to the desktop through the compatibility mode, until maybe Ubuntu is updated to work on my newer hardware or something, unless any of you has any further suggestions.

---

### Post by CatKiller on 2020-01-07
> **behealed said:**
> I did switch to the regular Ubuntu distro. I thought it looked more beefy, and those other distros seemed like "lite" versions. But that was just my assumption after like an hour, so I could be wrong. lol. 

It's more that they cater to different people and different workflows. 

>  Also, I was on a proprietary nvidia driver already (which it seemed to have done automatically when I installed).  

Yep, that's possible. Canonical have been testing including it with the install image with 19.10. 

>  I forgot the version number but it was the latest "verified" proprietary nvidia driver, which comes automatically with the version 19 ubuntu (it might not come automatically with ubuntu 18). 

It would have been the 435 branch, I think. There's a much longer process to put things through the Stable Release Upgrade path than just packaging it for the PPA. 

440 is a "long lived branch" in Nvidia's view, and fixed some bugs for me. 435 is a "short lived branch." 

>  However as you all recommended I did install the PPA and switched to a slightly more recent version which was 440, which for some reason it says is "open source".  

Yep, that's a packaging issue that's been there a while. Whichever packaging flag it is that the main repositories use to say "this package is proprietary," the PPA build process doesn't set 

>  I also downloaded the 440.44 directly from the nvidia (from [https://www.nvidia.com/Download/driverResults.aspx/156086/en-us](https://www.nvidia.com/Download/driverResults.aspx/156086/en-us)), which gave me a .run file that I don't really know how to run (the instructions looked difficult).  

Yeah, don't use that. It's really there so that package maintainers can package it up into their native packaging system. Not for end users. 

>  So I didn't use the .run file and all I did was download the PPA and go to drivers and switch to the 440 open source version that it added, and rebooted, and the change could be seen in the nvidia configuration window thingie. Note that the "open source" didn't say 440.44, it just says "440", so I donno if that's a problem I should be concerned about. 

You shouldn't be concerned about that at all. The driver branches are maintained as distinct packages, but each package gets upgraded within the branch. So you might have installed the 440 branch a couple of weeks ago and got 440.26, and then recently that would have been upgraded to 440.44, but someone that had installed the 435 branch wouldn't generally have been upgraded to either of those. 

>  But switching to the 440 open source version changed nothing and I'm still stuck in the login loop. So I tried the link that yancek gave, which suggested to change permissions on .Xauthority file, but I'm unable to do that because there doesn't seem to BE an .Xauthority file in my home folder.  

There are quite a few ways that an X session can fail: there are a lot of moving parts. We're only able to make educated guesses about what's causing your issue - we're just other users like you - but a user breaking things by naïvely messing up their permissions is a realistic cause of an X session failing to start. In your case, because it hasn't worked for you at all and you don't appear to have been fiddling with stuff or running things as root, I think the cause lies elsewhere. 

>  Also, typing** ls -lah | grep -i Xauthority **seemed to do nothing.... it would just act like I had pressed Return without typing anything at all. Not experienced enough with linux to even guess as to why.  

What that command does is run ls, which shows a list of the files in a directory, and then *pipes* the output of that command into grep, which displays any matching strings. There weren't any, so you got no output. 

>  Obviously the advantage of windows is that, at least it usually installs and boots up on the first try. 

More accurately, the advantage of Windows is that someone else does the installation and setup for you. It definitely doesn't always work on the first try, and requires a lot of setup before it's fully functional. 

There are two causes that seem likely to me for the issue you're experiencing. The first would be Wayland. Some versions of Gnome defaulted to Wayland even though Wayland doesn't really work well with Nvidia hardware. I have no idea if 19.10's version of Gnome does that (I stick to LTS releases and I don't use Gnome). It's also possible to manually select a Wayland session. Either way, using Wayland would be much more likely to fail than using the older X server.

The other potential reason is a combination of factors; there may have been some reason why the 435 branch wasn't working for you. It doesn't actually matter what that reason is in this scenario. The confounding second factor is that changing branches of the Nvidia driver often doesn't happen cleanly: the presence of one branch stops the second branch from being properly installed. Had the initial problem been the lack of any proprietary driver, installing the 440 branch would have been fine and would have fixed that. If the issue is that there's a non-functional 435 branch then the 440 branch might still not be installed properly.

The most straightforward solution would be to install Kubuntu instead (since you're not desperate to be using Gnome in particular), and *not* select to install the proprietary driver as part of the install. KDE haven't been pushing Wayland as hard as Gnome have, so it wouldn't be an accidental option. Then you can add the PPA and install the 440 branch without any contamination from another branch. An install takes about 20 minutes.

Otherwise, you can investigate those two potential causes. Check that you haven't specifically chosen to use Wayland, check that GDM hasn't done it for you, purge all the nvidia stuff (either using the command line or in Synaptic, since the simplified front ends are a bit too simplified) so that you can install the 440 branch without conflicts.

---

### Post by behealed on 2020-01-07
It sounds like everything you suggested could be accomplished with fewer steps by simply deleting the partition, reinstalling linux without nvidia, and then installing PPA. I'll try that, when I have the time, maybe tomorrow. And if that doesn't work, maybe the next day I'll try the same thing, but with version 18 instead. If that doesn't work, then RIP I guess.

PS you can run windows for an entire year without ever having to hold down the power button. Trying to get linux working, in just the last week I've probably had to hold down the power button 20 times. That's like as many hard resets as I've ever had to do on windows in the last 30 years, lol. But when you need to turn off ASLR, what choice do you have except linux. ;p

---

### Post by CatKiller on 2020-01-07
> **behealed said:**
> It sounds like everything you suggested could be accomplished with fewer steps by simply deleting the partition, reinstalling linux without nvidia, and then installing PPA. 

If the issue *is* with GDM's configuration, that wouldn't be enough to eliminate it. I don't know that it would be, but there were similar issues with a previous release. KDE uses SDDM rather than GDM, so it rules it out as a factor

---

### Post by slickymaster on 2020-01-07
Thread moved to [B]Ubuntu/Debian BASED

[/B]_@behealed:_
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

