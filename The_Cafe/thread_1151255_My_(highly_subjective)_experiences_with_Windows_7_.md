---
title: "My (highly subjective) experiences with Windows 7 RC"
date: 2009-05-06
forum: The Cafe
---

### Post by soc on 2009-05-06
[SIZE="3"]1. The Download[/SIZE]
I went to [http://www.microsoft.com/windows/windows-7/download.aspx]("http://www.microsoft.com/windows/windows-7/download.aspx") which explained the necessary steps to obtain a license key and the DVD image.
After setting up a Windows Live account, I received my key and was able to download the DVD image of Windows 7 RC (64bit, German) with my Ubuntu 9.04 (amd64) operating system. Although the download took 10 hours, interrupted by several disconnections from the internet, the download manager (a Java applet provided by Akamai resumed flawlessly and produced a correct image (although the SHA1 hash was hard to find and there was no official way to check if there were any corruptions during the transfer).

[SIZE="3"]2. The Installation[/SIZE]
My first attempts to install Windows 7 RC failed miserably.
When asked to choose the partition, I decided to install Windows 7 to the first partition of my first hard drive. 
> "Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information."
After doing a bit of research I couldn't find some specific reason for this problem.
I burned the image on a new DVD, opened my computer case and unplugged everything except one hard drive and one cd drive which where necessary to install, finally the installation went on.

The installation was pretty OK, although it didn't meet the high standards of an Ubuntu installation (and many other distributions):
- The installation was pretty slow
- Most of the time it was quite hard to see if the routine was still working or if the installation did hang up
- The resolution of my display wasn't configured correctly at the beginning
- The installation took two reboots

[SIZE="3"]3. The First Start[/SIZE]
The user interface looked quite polished with a single panel at the bottom holding a Windows icon (the "Start" menu), icons of the web browser "Internet Explorer 8", the file manager "Explorer" and the "Windows Media Player". Additionally there were a notification icon, a network connection icon, a volume icon, a clock and a transparent area ("Show Desktop" function) available.

One thing that did annoy me was the fact that it wasn't possible to use the scroll wheel on the volume applet directly without clicking on it.

Apart from that, the desktop looked pretty OK and was quite responsive (except the animation when closing a window had a reproducible interruption).

[SIZE="3"]4. The Configuration[/SIZE]
Then I did change my wallpaper (to a set of country-specific pictures (nice idea!) rotating every 2 hours) and reduced the panel height. Both option were easy to understand and to change, but when I dug deeper in the "Control Panel" I also spotted less comfortable user interfaces which looked like they where copied directly from Windows XP.

When exploring the installed fonts I found a ClearType wizard which enabled me to fine-tune the font rendering (which looked quite FreeType-like to me) in a very pleasant way, although the options didn't have that much impact like in Ubuntu.

[SIZE="3"]5. Software Installation[/SIZE]
**Firefox 3.0**
Because the user interface of Internet Explorer 8 looked very chaotic to me I decided to install my favorite browser, Firefox.

After I realized that neither "Activate/Deactivate Windows features" nor "Install Software" were able to install Firefox, I used the Internet Explorer to visit mozilla.com.
Curiously I wasn't able to find the 64bit build of Firefox 3 on that site, but had to resort to some unofficial website to download Firefox for amd64. After some weird security question (I guess because I asked IE8 to open the compressed archive of Firefox in Windows Explorer) the installation was smooth.

The installion of my extensions (FireGestures, AdBlock Plus and Compact Menu 2) was flawless, but finding the 64bit version of Java took me a few minutes. It was not possible to install the Flash plugin, it looks like the 64bit plugin is only available to Linux users.

Later I wanted to install some additional software:
**OpenOffice 3.1**
I couldn't find any file for my architecture and had to resort to download and install the 32bit version.
Apart from some weird UAC questions and an error report about "No Java installed" (maybe a problem with that 64bit Java?) I got Openoffice 3 to run as expected.

**7-zip**
The 64bit msi-package was on the homepage. Great!

**VLC**
I couldn't find the 64bit version, so I gave up and downloaded the 32bit one (7z compressed).
Somehow the extraction failed to some UAC thing, but drag and drop worked.

**Call of Duty 5 - World at War**
No 32bit version on DVD, nothing found online. Installation was without problems, although I hate it when programs try to take over my screen ...

Somehow the transition from 32bit to 64bit is still not completely finished on the Windows operating system.
I wonder why they even sell it, when most software isn't available.

[SIZE="3"]6. Updating[/SIZE]
The update mechanism of Windows 7 is completely integrated into the user interface, which is a very good improvement from the browser-based approach used in Windows XP, but can still only handle software from Microsoft like the operating system, IE or Windows Defender but not Firefox or Java for instance.
It allowed me to install 3 updated drivers and 2 updated compatibility lists for IE8 (one for i386 and one for amd64) and asked me to restart the PC.

[SIZE="3"]7. Conclusion[/SIZE]
Based on my short experience I can suggest Windows 7 to people who need to keep some Windows applications running natively, especially on new hardware where drivers for Windows XP are missing. People who already own Windows XP and are happy with it, won't find many reasons to upgrade to Windows 7.

People used to Ubuntu shouldn't expect too much:
- Windows 7 doesn't have a package manager
- Windows 7 doesn't come with much software ready to use, you will need to install an office suite, a multi-protocol messenger and many other things yourself, unlike Ubuntu.
- The security questions are sometimes triggered by "trivial" operations
- Some dialogs don't have the high usability standards of Gnome (for instance compare gnome-appearance-settings to the many different highly scattered dialogs of Windows 7)
- Installation of Windows 7 RC isn't as sophisticated as we are used from Linux distributions
- The 64bit version comes with a huge amount of 32bit libraries and executables, because the availability of third party software for 64bit isn't that good
- Copy and Paste with a middle click doesn't work
- No virtual desktops
- It is highly recommended to run anti-virus software (not included), but Windows 7 reminds you of that problem
- It doesn't play nice with GRUB, you have to reinstall GRUB after the installation of Windows 7


Have a nice day!

---

### Post by mamamia88 on 2009-05-06
weird i haven't had a single problem with it in fact it's been a joy to use so far even the sound they play during error messages cheers me up

---

### Post by Giant Speck on 2009-05-06
> **soc said:**
> - it is necessary to run anti-virus software (not included)

Wrong!

---

### Post by Polygon on 2009-05-06
> **Giant Speck said:**
> Wrong!

huh? windows yells at you if you are not running an anti virus....and this is windows we are talking about....

---

### Post by Giant Speck on 2009-05-06
> **Polygon said:**
> huh? windows yells at you if you are not running an anti virus....and this is windows we are talking about....

An anti-virus application is ***NOT*** necessary for using Windows.

---

### Post by Polygon on 2009-05-06
true...but its like driving a car without wearing a seatbelt....not necessary...but its HIGHLY recommended. Why else does window itself nag the user endlessly (unless you turn those notifications off) that you don't have one installed?

---

### Post by swoll1980 on 2009-05-06
> **Giant Speck said:**
> An anti-virus application is ***NOT*** necessary for using Windows.

This is all part of the new "I'm to leet to get viruses" trend. Most commonly associated with teenagers. Unfortunately it's not limited to computers.

---

### Post by Happy_Man on 2009-05-06
"Highly subjective" is an understatement. :P

---

### Post by Giant Speck on 2009-05-06
> **swoll1980 said:**
> This is all part of the new "I'm to leet to get viruses" trend. Most commonly assosiated with teenagers. Unfortunatly it's not limited to computers.

Um, *excuse me*?

You are far more likely to prevent an infection on your computer through the use of responsible browsing practices, script-blocking browser plug-ins, and not running your computer as an administrator.  An anti-virus program may be good for scanning files that are already on your computer, but they are useless for protecting your computer from new attacks, *especially *zero-day attacks and exploits.  And an anti-virus program certainly isn't going to help you if you fall for a social engineering scheme.

---

### Post by swoll1980 on 2009-05-06
> **mamamia88 said:**
> weird i haven't had a single problem with it in fact it's been a joy to use so far even the sound they play during error messages cheers me up

I agree even in it's rc stage, it's the best version of Microsoft I've come across. It runs all my programs, and drivers fine which is something Vista could never do.

---

### Post by swoll1980 on 2009-05-06
> **Giant Speck said:**
> Um, *excuse me*?

You are far more likely to prevent an infection on your computer through the use of responsible browsing practices, script-blocking browser plug-ins, and not running your computer as an administrator.  An anti-virus program may be good for scanning files that are already on your computer, but they are useless for protecting your computer from new attacks, *especially *zero-day attacks and exploits.  And an anti-virus program certainly isn't going to help you if you fall for a social engineering scheme.

Well I don't know what virus program you use, but mine has stopped attacks in real time before they happened, and I don't call doing research for a school project irresponsible, nor do I think those people that went to mint's sight were being irresponsible.

---

### Post by Icehuck on 2009-05-06
> **swoll1980 said:**
> This is all part of the new "I'm to leet to get viruses" trend. Most commonly associated with teenagers. Unfortunately it's not limited to computers.

You don't need virus scan to run any version of Windows. You can avoid viruses by not opening email attachments and downloading files from shadey websites, let alone torrents. Use a firewall of some sort to block those open ports. Malware, adware, and trojans are what plague Windows. Most virus scanning software can pick up some trojans and none do malware or adware. 

Virus - self replicating and self distributing program.

Viruses - Plural form of Virus see [here]("http://en.wikipedia.org/wiki/Plural_of_virus")

---

### Post by swoll1980 on 2009-05-06
> **Icehuck said:**
> You don't need virus scan to run any version of Windows. You can avoid viruses by not opening email attachments and downloading files from shadey websites, let alone torrents. Malware, adware, and trojans are what plague Windows. Most virus scanning software can pick up some trojans and none do malware or adware. 

Virus - self replicating and self distributing program.

Viruses - Plural form of Virus see [here]("http://en.wikipedia.org/wiki/Plural_of_virus")

Um... You can get a virus from clicking on a google link, or hovering your mouse over something. I'm not going to argue about this. Any security specialist would tell you your a fool if you don't use anti virus, but what do they know. If your too leet to get viruses, then I bow down to you, and all your leetness, and will continue to use anti virus like the idiot I am.

---

### Post by dragos240 on 2009-05-06
I tried it, it's fine and all, but now grub isn't loaded into the MBR, and now I'm running off a live cd (because windows couldn't pick up my wireless), and man am I frustrated!

---

### Post by LinuxRules1 on 2009-05-06
Did any of you hear about the windows 7 starter edition for netbooks? You can only run 3 programs at a time!. That sucks because you will use up 2 of your 3 program limit just with anti-virus and firewall software.

---

### Post by Icehuck on 2009-05-06
> **LinuxRules1 said:**
> Did any of you hear about the windows 7 starter edition for netbooks? You can only run 3 programs at a time!. That sucks because you will use up 2 of your 3 program limit just with anti-virus and firewall software.

Emerging markets only!

---

### Post by Sealbhach on 2009-05-06
> **dragos240 said:**
> I tried it, it's fine and all, but now grub isn't loaded into the MBR, and now I'm running off a live cd (because windows couldn't pick up my wireless), and man am I frustrated!

Hey Dragos, maybe try this?

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)


.

---

### Post by Giant Speck on 2009-05-06
> **LinuxRules1 said:**
> Did any of you hear about the windows 7 starter edition for netbooks? You can only run 3 programs at a time!. That sucks because you will use up 2 of your 3 program limit just with anti-virus and firewall software.

> **Icehuck said:**
> Emerging markets only!

That and even if it was for Western markets, anti-virus and firewall software is not included in the three-application limit.

---

### Post by .Maleficus. on 2009-05-06
> **LinuxRules1 said:**
> Did any of you hear about the windows 7 starter edition for netbooks? You can only run 3 programs at a time!. That sucks because you will use up 2 of your 3 program limit just with anti-virus and firewall software.
This is wrong.  Anti-virus/scanners/firewalls/whatever are NOT counted by Windows as the three programs.  Internet/email/media player/IM would be though.

As the for the GRUB problems, well, installing any version of Windows will overwrite the MBR, that shouldn't come as a surprise.

Great little write-up soc.  I've got my ISO and key waiting for me :).

---

### Post by LinuxRules1 on 2009-05-06
> **Giant Speck said:**
> That and even if it was for Western markets, anti-virus and firewall software is not included in the three-application limit.

My bad, i thought that they would be included in the 3 program limit. but only being able to run 3 applications at a time is still pitiful.

---

### Post by pwnst*r on 2009-05-06
> **soc said:**
> [SIZE="3"]

People used to Ubuntu shouldn't expect too much:
- Windows 7 doesn't have a package manager [COLOR="Red"]yes and? i don't miss it in windows.[/COLOR]
- Windows 7 doesn't come with much software ready to use, you will need to install an office suite, a multi-protocol messenger and many other things yourself, unlike Ubuntu. [COLOR="red"]hm.. office 2007 is superior, and although i do like pigeon, i like digsby better.   [/COLOR]
- Copy and Paste with a middle click doesn't work [COLOR="red"]not sure who does it that way. most don't.[/COLOR]



see red above*

good write up and pretty unbiased for a change.  rare around here.

---

### Post by sharp65 on 2009-05-06
> **LinuxRules1 said:**
> Did any of you hear about the windows 7 starter edition for netbooks? You can only run 3 programs at a time!. That sucks because you will use up 2 of your 3 program limit just with anti-virus and firewall software.

I really doubt you even bothered to read into it given by your name, but that's not how it works. But thanks for trying!

---

### Post by mamamia88 on 2009-05-06
i really like the new taskbar much better than osx dock imo.  also, with a freeware program i can have my scale from compiz all i need now is a way to get multiple workspaces and this might be the best windows ever

---

### Post by bashveank on 2009-05-06
> **swoll1980 said:**
> Um... You can get a virus from clicking on a google link, or hovering your mouse over something. I'm not going to argue about this. **Any security specialist would tell you your a fool if you don't use anti virus**, but what do they know. If your too leet to get viruses, then I bow down to you, and all your leetness, and will continue to use anti virus like the idiot I am.

Steve Gibson, security guru, owner of the Gibson Research Corporation, creator of SpinRite, discoverer of spyware, does not run an anti-virus.

---

### Post by swoll1980 on 2009-05-06
> **bashveank said:**
> Steve Gibson, security guru, owner of the Gibson Research Corporation, creator of SpinRite, discoverer of spyware, does not run an anti-virus.

Do you have a link that confirms this? Also I would ad that Gibson is a human antivirus program. I said a security specialist would say that your a fool if you didn't use antivirus, never said that they used it.

---

### Post by surfed on 2009-05-06
Well I just tried the RC and experienced my first BSOD in years, it was not windows fault but AVG antivirus, took it off (took me 3 tries as you cant uninstall stuff in save mode and in normal mode i would BSOD). Tried Panda and it seems to work... 2 hours later the novelty wore off, i realized it is windows with a new face and so i am back in Ubuntu.... Not convinced.

---

### Post by reyfer on 2009-05-06
Apparently, sarcasm is something most people on this thread don't recognize. The OP made a sarcastic review mocking the way some windows sites depict their experiences trying linux ("I tried linux for a week..." kind of stories found on PC magazines and Windows-centric sites)

---

### Post by pwnst*r on 2009-05-06
except, you're wrong.

---

### Post by monsterstack on 2009-05-06
Subjective is the word, OP. Come on, using an OS you're not that used to using is always going to be a bit weird. Windows != Linux. The whole idea of an intuitive GUI and associated functionality is a myth: you only come to believe a GUI and its tools are intuitive after weeks of use.

---

### Post by Giant Speck on 2009-05-06
> **swoll1980 said:**
> Do you have a link that confirms this?
 
Do you have a link that confirms this:
 
> **swoll1980 said:**
> Any security specialist would tell you your a fool if you don't use anti virus, but what do they know.
 
Also, it's "you're," not "your." Learn to spell.

---

### Post by swoll1980 on 2009-05-07
> **Giant Speck said:**
> Do you have a link that confirms this:
 

 
Also, it's "you're," not "your." Learn to spell.

For one, it's not misspelled it's just the wrong word all together. An easy mistake to make when you're quickly typing responses on a forum. For two, it's common knowledge that you should use anti virus software, as some one else said Windows it's self harasses you to install it. I'm going to school now for information system security, and it was taught to us there.
I don't have to prove that which is common knowledge. If some one says that the sky is blue, I don't ask for a link. Surely someone of your obvious intellectual superiority can tell the difference.

---

### Post by Giant Speck on 2009-05-07
What the hell is up with your attitude that I'm supposedly "holier than thou"?  I never once insinuated that I am more intelligent or knowledgeable than you. 
 
All I said was that an anti-virus application is not *necessary* when using Windows.  Sure, anti-virus programs can be handy and offer some level of protection and security, but they should *never *be used as your first line of defense.  In addition, if Windows needed an anti-virus program so badly, it would be impossible to use it without one.  Not using an anti-virus program does not make Windows inoperable.

---

### Post by swoll1980 on 2009-05-07
> **Giant Speck said:**
> What the hell is up with your attitude that I'm supposedly "holier than thou"?  I never once insinuated that I am more intelligent or knowledgeable than you. 
 

You told me I need to learn how to spell. 

> **Giant Speck said:**
> All I said was that an anti-virus application is not necessary when using Windows. Sure, anti-virus programs can be handy and offer some level of protection and security, but they should never be used as your first line of defense. In addition, if Windows needed an anti-virus program so badly, it would be impossible to use it without one. Not using an anti-virus program does not make Windows inoperable. 

I agree that it shouldn't be the first line of defense, all the things you listed should be, but I don't agree that it isn't necessary. When all those things fail(which some times they do) the anti virus is a valuable tool to alert you of the virus, and help you remove it safely, or prevent it from infecting you in the first place.

add: I'm sorry if I took the "learn to spell" thing out of context, but it sounded like an insult to me.

---

### Post by schauerlich on 2009-05-07
Now, children, let's play nice...

---

### Post by Giant Speck on 2009-05-07
> **EDavidBurg said:**
> Now, children, let's play nice...
 
You can't tell me what to do; you're not my *real* mom!
 
*slams door and blasts stereo*

---

### Post by bashveank on 2009-05-07
> **swoll1980 said:**
> Do you have a link that confirms this? Also I would ad that Gibson is a human antivirus program. I said a security specialist would say that your a fool if you didn't use antivirus, never said that they used it.

I don't have a direct link. But I can assure you that he has said such in many episodes of Security Now, which can be downloaded in audio or text form here: [http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm) if you really feel like perusing through them for an exact quote.

---

### Post by wersdaluv on 2009-05-07
> **swoll1980 said:**
> This is all part of the new "I'm to leet to get viruses" trend. Most commonly associated with teenagers. Unfortunately it's not limited to computers.
Haha. I'm too leet to get a virus but whenever I do so, it's fine because I'm too leet not to reformat. hehe

---

### Post by k2t0f12d on 2009-05-07
> **soc said:**
> there was no official way to check if there were any corruptions during the transferInternet protocols constantly check and recheck pieces during transfer. Its more likely that data you have received from your modem will be okay and any corruption will occur on its way to, when it gets to, or after its written to your HDD.

> **soc said:**
> The installation was pretty slowIt had an acceptable speed to me. The virtual machine passed my personal settings directly to the Windows installer, so it was totally hands-free for me. However, removing the dialog between me and my computer is not something that I want. :P

> **soc said:**
> One thing that did annoy me was the fact that it wasn't possible to use the scroll wheel on the volume applet directly without clicking on it.That's not the only usability feature that Windows misses out.

> **soc said:**
> - Windows 7 doesn't have a package manager
- Windows 7 doesn't come with much software ready to use, you will need to install an office suite, a multi-protocol messenger and many other things yourself, unlike Ubuntu.
- The security questions are sometimes triggered by "trivial" operations
- Some dialogs don't have the high usability standards of Gnome (for instance compare gnome-appearance-settings to the many different highly scattered dialogs of Windows 7)
- Installation of Windows 7 RC isn't as sophisticated as we are used from Linux distributions
- The 64bit version comes with a huge amount of 32bit libraries and executables, because the availability of third party software for 64bit isn't that good
- Copy and Paste with a middle click doesn't work
- No virtual desktops
- It is highly recommended to run anti-virus software (not included), but Windows 7 reminds you of that problem
- It doesn't play nice with GRUB, you have to reinstall GRUB after the installation of Windows 7[COLOR="Blue"][SIZE="4"]++[/SIZE][/COLOR]

---

### Post by soc on 2009-05-07
- Windows 7 doesn't have a package manager
> **pwnst*r said:**
> yes and? i don't miss it in windows.
OK, that's your POV. I personally missed it very much, it would have given me the chance to do something different while letting the package manager download and install. Instead I clicked "Next" and "Finish" quite some time that evening. (And I didn't check if the setups have been tampered by a malicious third party, Ubuntu does that automatically.)

- Windows 7 doesn't come with much software ready to use, you will need to install an office suite, a multi-protocol messenger and many other things yourself, unlike Ubuntu. 
> **pwnst*r said:**
> hm.. office 2007 is superior, and although i do like pigeon, i like digsby better.
I won't argue if OpenOffice.org or MS Office 2007 are better.
But fact is: after the installation of Windows 7 RC there was no office suite available although Windows 7 came on a DVD (and Ubuntu comes on a CD). That was (in my humble opinion) a valid point.

- Copy and Paste with a middle click doesn't work
> **pwnst*r said:**
> not sure who does it that way. most don't.
OK, most people I know use that feature ... But I usually show them this functionality when I explain them Gnome.


I adjusted the point about the anti virus software ... I hope we can stop arguing about that now.

---

### Post by geoken on 2009-05-07
> **swoll1980 said:**
> Um... You can get a virus from clicking on a google link, or hovering your mouse over something.

Attacks like this (where the browser is completely pwned) are typically fixed much faster by the browser vendors than malware scanners. 

If you wanted to get really technical malware scanners would be completely useless in this situation unless they directly patched the browser since they are only addressing the exploit's payload (which can be easily changed) rather than the attack vector which is being used to distribute that payload (the aforementioned browser flaw).

If we used the recent pwn2own contest as a reference, it is currently impossible for a Chrome user to get a virus from "clicking on a google link, or hovering your mouse over something". The only way you could get a virus is by being fooled into opening awesomesong.mp3.exe because you have file extensions hidden (and even then the UAC prompt should tip you off).

---

### Post by bashveank on 2009-05-07
> **soc said:**
> I won't argue if OpenOffice.org or MS Office 2007 are better.
But fact is: after the installation of Windows 7 RC there was no office suite available although Windows 7 came on a DVD (and Ubuntu comes on a CD). That was (in my humble opinion) a valid point.

Did you look at Wordpad? The Windows 7 version is quite usable and feature-full. I can see lots of people in the future skipping out on buying an office suite for using Wordpad.
It's only one part of an office suite, but for most people it should suffice.

---

### Post by Polygon on 2009-05-07
windows 7 is what windows vista should of been. Not much changed user interface wise, but a lot of programs (like the wireless connect thingy) is much better then the crappy vista one.

---

### Post by mamamia88 on 2009-05-07
i won't say that i would pay $200 for it but ill definitely getting a copy when my college sells it at it's discout price

---

### Post by Slug71 on 2009-05-07
3 questions.

1: Is Windows 7 faster than Vista?

2: Does Windows 7 use less space than Vista on a fresh install?

3: Can you just buy a new license and enter it when the RC one expires or do you have to do a reinstall?

---

### Post by pwnst*r on 2009-05-07
> **Slug71 said:**
> 3 questions.

1: Is Windows 7 faster than Vista?

2: Does Windows 7 use less space than Vista on a fresh install?

3: Can you just buy a new license and enter it when the RC one expires or do you have to do a reinstall?

1) yes
2) dunno
3) dunno

---

### Post by Polygon on 2009-05-07
if you install the RC, microsoft has said that you will have to do a fresh install in order to install the final version, you will not be able to upgrade.

---

### Post by wsonar on 2009-05-07
> **soc said:**
> 

One thing that did annoy me was the fact that it wasn't possible to use the scroll wheel on the volume applet directly without clicking on it.


that is a cool feature we have

---

### Post by wsonar on 2009-05-07
> **Slug71 said:**
> 3 questions.

1: Is Windows 7 faster than Vista?

2: Does Windows 7 use less space than Vista on a fresh install?

3: Can you just buy a new license and enter it when the RC one expires or do you have to do a reinstall?

1.**Debatable**

2. Getting ready to install the Release Candidate
What you'll need:

    *

      A blank DVD
    *

      A PC with a DVD burner
    *

      A PC for testing that meets these minimum system requirements (specific to Windows 7 RC and subject to change in the final version of Windows 7):
          o

            1 GHz or faster 32-bit (x86) or 64-bit (x64) processor
          o

            1 GB RAM (32-bit) / 2 GB RAM (64-bit)
          o

            16 GB available disk space (32-bit) / 20 GB (64-bit)
          o

            DirectX 9 graphics processor with WDDM 1.0 or higher driver


3. Removing the RC

The Windows 7 RC will stop working on June 1, 2010. To continue using your PC, please be prepared to reinstall a prior version of Windows or the final released version of Windows 7 before the expiration date. We recommend doing a custom (clean) installation

---

### Post by growled on 2009-05-07
I was reading last night some new test done by PC World (I think) and they show that now Windows 7 RC is hardly any faster than Vista. I knew MS would find some way to screw 7 up.

---

### Post by pwnst*r on 2009-05-07
> **growled said:**
> I was reading last night some new test done by PC World (I think) and they show that now Windows 7 RC is hardly any faster than Vista. I knew MS would find some way to screw 7 up.

source please, kthx.

---

### Post by mamamia88 on 2009-05-07
> **growled said:**
> I was reading last night some new test done by PC World (I think) and they show that now Windows 7 RC is hardly any faster than Vista. I knew MS would find some way to screw 7 up.

well on a fresh install of both they are both about the same for me with only office installed.  but when installing drivers on vista the blue circle spun for about 2 minutes after i clicked the file to install but on 7 it was almost instantaneously opened.  take that for what it's worth.

---

### Post by swoll1980 on 2009-05-07
> **growled said:**
> I was reading last night some new test done by PC World (I think) and they show that now Windows 7 RC is hardly any faster than Vista. I knew MS would find some way to screw 7 up.

Windows 7, if it stays the way it is, is the best os I've ever used. I hate Microsoft with a passion, so this isn't fanboyism. I wish it was a big stinker like Vista, but it's not. On the same PC Windows 7 boots to a functional desktop in about 20 seconds. This is a huge improvement from the 1 minute + I would get from Vista. Things that drove me nuts about Vista, like the excessive amount of time it took to install software, and updates has been reduced by at least %50, more like 75% though. I love the new taskbar, they took the best things from the taskbar, and doc, and merged them together, into the coolest way to manage windows I've ever seen. I like everything about it. The sounds, the sights, the window animations are, so much smoother than they are in Compiz, though you don't get to customize them. Every program I have runs great, which is something Vista was never able to accomplish. If Microsoft makes one change to this when the final comes out, they're idiots, and deserve to fail again. Hopefully someone finds a way to crack this, in case Microsoft does decide to destroy it, before the final version.

---

### Post by Slug71 on 2009-05-07
Its really stupid that they wont allow you to purchase and enter a new key when final is released instead of having to do a reinstall.


Now just to know if its smaller than Vista?

---

### Post by linuxgeek123 on 2009-05-07
i tried it and after 30 hours of download the iso fas corrupt...
**** you windows!!!!

---

### Post by geoken on 2009-05-07
> **Slug71 said:**
> Its really stupid that they wont allow you to purchase and enter a new key when final is released instead of having to do a reinstall.


They also said you wouldn't be able to upgrade Beta to RC, but if you edited one config file it worked perfectly. I'm guessing the final release will be like this to. The restriction is artificial, the installer itself is capable handling the upgrade.

---

### Post by swoll1980 on 2009-05-07
> **linuxgeek123 said:**
> i tried it and after 30 hours of download the iso fas corrupt...
**** you windows!!!!

I hope you didn't try downloading a 2 GiB + file over a dial up connection. The chances of it being successful, w/o bit torrent, would be near near zero.

---

### Post by pwnst*r on 2009-05-07
> **linuxgeek123 said:**
> i tried it and after 30 hours of download the iso fas corrupt...
**** you windows!!!!

yes, it's window's fault.

---

### Post by TheLastDodo on 2009-05-07
> **soc said:**
> - Windows 7 doesn't have a package manager

OK, that's your POV. I personally missed it very much, it would have given me the chance to do something different while letting the package manager download and install.

Both Windows and OS X would greatly benefit from a package manager that synced with several major download sites; having to manually install a lot of software on a new machine is a pain in the *** without one.

---

### Post by swoll1980 on 2009-05-07
> **TheLastDodo said:**
> Both Windows and OS X would greatly benefit from a package manager that synced with several major download sites; having to manually install a lot of software on a new machine is a pain in the *** without one.

Somebody actually wrote a program called[ Win-get]("windows-get.sourceforge.net/") that does that.

---

### Post by soc on 2009-05-08
A package manager is a bit more than that.
- Cryptographic security
- Package maintainers which patch applications to improve integartion
- Works for the whole operating system, not only some selected applications
- Depending on the repository, a trustworthy promise, that security problems will be patched in a timely manner
etc...

---

### Post by sultanoswing on 2009-05-08
Everyone is going on about how fast Windows 7 is...and that may be so, and seems that way on my machine too.

As we all know, however, Win XP is also damn fast on a _fresh_ install. I'm looking forward to how fast all these Windows 7 installations will be after a few months as the registry starts getting bogged down, and it all starts running slower, and slower, and slower until eventually you're forced to reinstall.

No such slowdown's on *nix.

---

### Post by Giant Speck on 2009-05-08
> **sultanoswing said:**
> No such slowdown's on *nix.
 
I beg to differ.

---

### Post by swoll1980 on 2009-05-08
> **sultanoswing said:**
> Everyone is going on about how fast Windows 7 is...and that may be so, and seems that way on my machine too.

As we all know, however, Win XP is also damn fast on a _fresh_ install. I'm looking forward to how fast all these Windows 7 installations will be after a few months as the registry starts getting bogged down, and it all starts running slower, and slower, and slower until eventually you're forced to reinstall.

No such slowdown's on *nix.
[reg cleaner]("http://majorgeeks.com/downloadget.php?id=460&file=15&evp=918d178ce8f53361a121db92cc3c7d2e")

---

### Post by wsonar on 2009-05-09
so I just installed WIn7RC on my trip boot I replaced the vista went pretty quick just had to go to dell's site and grab the nvidea driver for my laptop grabed the vista version everything seems pretty normal installed flash tested some video's, no printers here to test currently Seems pretty snappy came with a lot of pretty theme's and stuff also

one neat thing on install gave a list of wireless networks to connect to so I could put in my passkey and already be connected to my wireless.


Now the fun of reinstalling Grub :)

---

### Post by monsterstack on 2009-05-09
> **Giant Speck said:**
> I beg to differ.

This hasn't been my experience at all. I actually completely ran out of space on my disks a couple of times under the sheer weight of crufty applications, films and music that one acquires over a series of time. It freaked me out the first time it happened. When I ran Windows years ago I had to nuke the partition every six months or so. I'm now a year deep in an Ubuntu installation that has been upgraded four times and it's still working pretty well with no noticeable slow-down. Contiguous filesystems turn out to be pretty good.

---

### Post by Abhinavhardikar on 2009-05-14
> **surfed said:**
> Well I just tried the RC and experienced my first BSOD in years, it was not windows fault but AVG antivirus, took it off (took me 3 tries as you cant uninstall stuff in save mode and in normal mode i would BSOD). Tried Panda and it seems to work... 2 hours later the novelty wore off, i realized it is windows with a new face and so i am back in Ubuntu.... Not convinced.

Try Quick heal for Vista in compatibility mode. It worked for me;)

---

### Post by Abhinavhardikar on 2009-05-14
> **Slug71 said:**
> 3 questions.

1: Is Windows 7 faster than Vista?

2: Does Windows 7 use less space than Vista on a fresh install?

3: Can you just buy a new license and enter it when the RC one expires or do you have to do a reinstall?

1) Yes
2) almost the same
3) reinstall

---

### Post by soc on 2009-05-14
OK, I can confirm that Windows 7 RC is not faster than Vista in almost any test.

But many UI glitches which made Vista **look** slow were fixed, indeed.

---

### Post by Mateo on 2009-05-14
i also don't use antivirus software.  in my 20 years of computer use, i have only had 1 serious virus attack (meaning that i had to do more than a simple virus scan to fix the problems caused).

But that's not the main reason I don't use them (i know it's a risk not using them).  I don't use them because they are **so unbelievably annoying**.  They pop up all the time, seemingly every time you start the computer.  They want to update all of the time (which is fine, just don't tell me that you're doing it or have any type of pop up windows).  They want to remind you that you need to run the scan....

Please give me a antivirus that runs 99% in the background.  Do automatic updates in the background.  Scan my emails in the background.  Scan downloads in the background.  Don't ask me any questions unless you think something has a virus.  I'm willing to do a manual scan once every 3 or 4 months if it's absolutely necessary.

But if i have to chose between running the 0.05% chance of getting a virus or put up with an annoying, usually memory hogging, antivirus application, i'll take the risk.

---

### Post by ukripper on 2009-05-14
Best way to avoid phishing attacks on any system(win/*nix) is use opendns [http://www.opendns.com/](http://www.opendns.com/) and turn on phishing filter and other filters available under opendns account and it is FREE.


[COLOR="Black"][I][COLOR="RoyalBlue"]"Security

    * Industry-leading anti-phishing protects everyone on your network from fraudulent phishing scams.
    * Award-winning Web content filtering gives you the power to block up to 50 categories of content.
    * Detailed statistics empower you to understand your network traffic and spot trends before they become problems."[/COLOR][/I][/COLOR]


Use firestarter or some other firewall to block unwanted ports on your machine.

Use NOSCRIPT ([http://noscript.net/](http://noscript.net/)) firefox extension while browsing, it blocks background scripts.

Use normal user(low privilege)account while surfing or downloading of the net.

Secure your wireless using WPA, not WEP.

Keep your passwords secure. 

Use encryption on your valuable data try truecrypt - [http://www.truecrypt.org/](http://www.truecrypt.org/)

Following above best practices virus attacks can be avoided to 90%

---

### Post by soc on 2009-05-15
Ok, I updated some small parts with experiences when installing OO.o, VLC, CoD5, etc. ...

---

### Post by omar8 on 2009-05-15
Ok, Windows 7 RC is MUCH faster than Vista, and if your going by benchmarks most of them show Windows Vista out performing XP but that isn't the case. Benchmarks are meaningless in this respect. The fact that people running ATI cards still get the same benchmark scores as everyone else but they have 2 second delay. There is much more to performance than just benchmarks - I think I read somewhere that Windows 7's performance increase is due to some new code to use the CPU and GPU more effectively.
Also, Windows cant include any more programs because you guys especially will be the ones posting about Microsoft abusing their position, but now your complaining about not including extra software - Windows Live had to be removed and made a seperate download just to avoid being sued.
Imagine the reaction of you guys if Microsoft made its own package manager - everyone would be running around screaming about how Microsoft is trying to take more control over users Desktops, then there will be made up stories about DRM being put into the programs even though it isn't.
It is always lose-lose for Microsoft and you guys know it.

---

### Post by bakedbeans4life on 2009-05-15
> **omar8 said:**
> Ok, Windows 7 RC is MUCH faster than Vista, and if your going by benchmarks most of them show Windows Vista out performing XP but that isn't the case. Benchmarks are meaningless in this respect. The fact that people running ATI cards still get the same benchmark scores as everyone else but they have 2 second delay. There is much more to performance than just benchmarks - I think I read somewhere that Windows 7's performance increase is due to some new code to use the CPU and GPU more effectively.
Also, Windows cant include any more programs because you guys especially will be the ones posting about Microsoft abusing their position, but now your complaining about not including extra software - Windows Live had to be removed and made a seperate download just to avoid being sued.
Imagine the reaction of you guys if Microsoft made its own package manager - everyone would be running around screaming about how Microsoft is trying to take more control over users Desktops, then there will be made up stories about DRM being put into the programs even though it isn't.
It is always lose-lose for Microsoft and you guys know it.

Do I hear the sound of the smallest violin in the world playing just for you. Microsofties, they are a breed apart.

---

### Post by ralley4 on 2009-06-07
I'm currently dual-booting with W7. I find that it runs quite nicely, and they have done some nice improvements from Vista! I use Comodo which comes with an anti-virus. I have some specific needs to keep running windows, otherwise I'd be full Ubuntu, thanks to this community!

---

### Post by H2SO_four on 2009-06-07
I tried it for a lil while and then deleted it (I don't have any use for Windows).  It looks and functions well enough, but as I have a laptop with vista installed, I have no need for anything other than Linux on the desktop pc.

---

### Post by mxboy15u on 2009-06-07
Windows 7 abolsutely refused to write a partition to my drive, I was not trying to dual boot even it was going to be a complete install on my test computer. It did not work and the disk went in the trash.

---

### Post by CJ Master on 2009-06-07
> **bakedbeans4life said:**
> Do I hear the sound of the smallest violin in the world playing just for you. Microsofties, they are a breed apart.

That's odd, I found his post had very good points, while yours didn't address any of them. ):P

---

### Post by MikeTheC on 2009-06-07
Ok, I'll just ask the same question I asked in an earlier Win7 thread that's now floating about in Recurring Discussions...

Is Win7 really all that much different/faster/better than Vista? It sure doesn't seem any different to me on my system.

Boot time is about the same, app launch and general responsiveness are all about the same... Just not seeing any particular improvement. Where are you guys getting this, exactly?

---

### Post by hoagie on 2009-06-07
I Used Vista for two years for games and Adobe Lightroom and I myself found it quite stable, in contrast with what everyone was arguing. I tried windows 7 and it does perform a little bit better. You won't notice a big difference, if your computer met Microsoft's recommended specifications for Vista. Other than that the other enhancements are positively accepted but, I don't think that 7 are so damn good as everyone else does. Yes they are stable, fast and easy to use but not something entirely new.
Perhaps if I was disappointed by Vista I would be relieved when trying 7 but for me it didn't make such a difference.

---

### Post by donniezazen on 2009-06-07
Win 7 RC installation is flawed. It took me few days to complete the installation. I had hard time installing. But after that i am very impressed with Win 7. I do not have any problem installing any software after the installation.

SK

---

### Post by arcdrag on 2009-06-07
> **MikeTheC said:**
> Ok, I'll just ask the same question I asked in an earlier Win7 thread that's now floating about in Recurring Discussions...

Is Win7 really all that much different/faster/better than Vista? It sure doesn't seem any different to me on my system.

Boot time is about the same, app launch and general responsiveness are all about the same... Just not seeing any particular improvement. Where are you guys getting this, exactly?

Windows 7 runs slightly faster than both Vista and XP for me.  Don't know about boot time...but I only boot up my computer once a day, so I'm not overly concerned if it takes an extra 3 seconds out of my day to boot up.  

For me, the main improvements in Windows 7 are with the general interface and functionality.  It basically combines the good things from Vista and XP, and builds on them.  I won't be paying for it, but since I get a free copy from my college I'll be using it for gaming and Microsoft Onenote.

---

### Post by samjh on 2009-06-07
> **soc said:**
> A package manager is a bit more than that.
- Cryptographic security
- Package maintainers which patch applications to improve integartion
- Works for the whole operating system, not only some selected applications
- Depending on the repository, a trustworthy promise, that security problems will be patched in a timely manner
etc...

In Linux, each distribution project (eg. Ubuntu, Debian, Fedora, etc.) is responsible for maintaining packages for that distribution.

If you want to create an analogous system for Windows, Microsoft will be responsible for maintaining and distributing all software for Windows.  Can you imagine the uproar if that were to happen?  Anti-trust cases?  Privacy advocates blowing steam and molten lava?  The industry will be turned upside-down if Microsoft was given whole responsibility for that.

---

### Post by rookcifer on 2009-06-07
> **samjh said:**
> In Linux, each distribution project (eg. Ubuntu, Debian, Fedora, etc.) is responsible for maintaining packages for that distribution.

If you want to create an analogous system for Windows, Microsoft will be responsible for maintaining and distributing all software for Windows.  Can you imagine the uproar if that were to happen?  Anti-trust cases?  Privacy advocates blowing steam and molten lava?  The industry will be turned upside-down if Microsoft was given whole responsibility for that.

Apples to oranges.  Most software for Windoze is not FLOSS, thus the vendors would probably never allow M$ to set-up such a repository to begin with.  Even if they did, you'd still have the issue that not only is a lot of the software not FLOSS but it's also not even free as in beer.  So, M$ would have to set-up some sort of payment system.  And then you'd have some vendors left out of the mix and complaining about it, threatening anti-trust suits and generally causing all kinds of uproar.

With Linux 99% of the software is FLOSS, GPL'ed, and not for profit.  Therefore, the developers of the software have no problems with allowing distributions to package it, maintain updates and add it to repositories.

---

### Post by samjh on 2009-06-07
Exactly my point.  Such a system is not viable on Windows.  The industry (not to mention consumer groups) won't allow it.

---

### Post by gordintoronto on 2009-06-08
> **Mateo said:**
> ou that you need to run the scan....

Please give me a antivirus that runs 99% in the background.  Do automatic updates in the background.  Scan my emails in the background.  Scan downloads in the background.  Don't ask me any questions unless you think something has a virus.  I'm willing to do a manual scan once every 3 or 4 months if it's absolutely necessary.



AVG is what you want.

From time to time (maybe every year or two) they have a "major version upgrade" which requires manual intervention, and some wide-awake reading to avoid accidentally signing up for the paid version.

One point I haven't seen so far in this thread is that if you're behind a router, any router, it's almost as good as being behind a firewall, because your IP address is not exposed.

---

### Post by y6FgBn)~v on 2009-06-08
+1 for AVG

[Available here]("http://free.avg.com/")

---

### Post by init1 on 2009-06-08
> **Giant Speck said:**
> Um, *excuse me*?

You are far more likely to prevent an infection on your computer through the use of responsible browsing practices, script-blocking browser plug-ins, and not running your computer as an administrator.  An anti-virus program may be good for scanning files that are already on your computer, but they are useless for protecting your computer from new attacks, *especially *zero-day attacks and exploits.  And an anti-virus program certainly isn't going to help you if you fall for a social engineering scheme.
Yes but they still protect your computer from old attacks. Partial protection is better than no protection.

---

### Post by rookcifer on 2009-06-09
> **init1 said:**
> Yes but they still protect your computer from old attacks. Partial protection is better than no protection.

Care to elaborate on what "old attacks" AV will protect you from?

---

