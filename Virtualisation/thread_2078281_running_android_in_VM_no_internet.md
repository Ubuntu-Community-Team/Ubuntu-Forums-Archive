---
title: "running android in VM no internet"
date: 2012-10-30
forum: Virtualisation
---

### Post by cmcanulty on 2012-10-30
I have installed android in my VM but can't get a wired or wireless internet connection in it. How should I configure it to work?
I downloaded the android file from this website

[http://www.vmlite.com/index.php?option=com_content&view=article&id=68:android&catid=17:vmlitenewsrotator]("http://www.vmlite.com/index.php?option=com_content&view=article&id=68:android&catid=17:vmlitenewsrotator")

---

### Post by squakie on 2012-10-30
I hadn't heard of this until your post, so I went looking.

It seems internet support is a bit of a problem, but I did find one post in their "forum" that stated you must use bridged networking in the VM.

I also saw a post there about internet not working in the demo version.

I don't know if that will help you any or not.

---

### Post by pandacookie on 2012-10-30
By "VM", do you mean a program like VirtualBox? If so, there are different ways to configure this, depending on the program. Please let us know what program you are using.

---

### Post by squakie on 2012-10-30
......and hence my mention of you *must* use bridged networking in the VM..........

---

### Post by cmcanulty on 2012-10-30
I am trying it in Virtual Box 4.2.4. Other distros connect to net in it but not android. I tried bridged and no change

---

### Post by monkeybrain2012 on 2012-10-30
You need a patched version of Android to get internet in VM. I have set one up in vbox and it works. I will find you the link tonight when I got home. Check back late tonight or early tomorrow.

---

### Post by squakie on 2012-10-30
> **cmcanulty said:**
> I am trying it in Virtual Box 4.2.4. Other distros connect to net in it but not android. I tried bridged and no change

just want to verify - it's not the demo version, right?

---

### Post by monkeybrain2012 on 2012-10-31
[http://www.webupd8.org/2012/07/android-x86-404-ics-rc2-released-with.html](http://www.webupd8.org/2012/07/android-x86-404-ics-rc2-released-with.html)

---

### Post by squakie on 2012-11-01
I just tried the download that monkeybrain2012 recommended, following the link to the download of the patched version so internet would work, so I could try to help figure this out from using it.  Well, I hate to sound dumb - but heh - I installed the iso in virtualbox and all I get is the ANDROID screen and nothing else.  Shouldn't this be jumping into some sort of main screen like my tablet does?

EDIT:  upon further look, it would seem that my cpu/motherboard isn't listed in the supported list.  I'm surprised it even starts.

Asus M5A97 and AMD FX81xx - 64-bit , 8-core, 3.1ghz.


EDIT:  It DOES work - I had to change one of the VM settings.  I have the network set to NAT and I had stupidly thought I was allocating gigabytes to memory when in fact it was megabytes - no wonder it wouldn't run.  I gave it 4gb, started it, it runs and it connects to the net.

Thanks for the post monkeybrain2012, and I hope this helps you  cmcanulty.  Iit's not the same package you were looking at, but it runs in virtualbox itself without being within another OS (if I followed the link you posted originally, that product appears to run in Windows?).

---

### Post by cmcanulty on 2012-11-01
OK will try yours, thanks tomorrow as I work until late today
Sorry I am confused I looked at that page and their are a ton of different files. Which should I download to run android with ethernet in virtual box on my Ubuntu 12.04?

---

### Post by monkeybrain2012 on 2012-11-01
> **cmcanulty said:**
> 
Sorry I am confused I looked at that page and their are a ton of different files. Which should I download to run android with ethernet in virtual box on my Ubuntu 12.04?
  Click the link that says "DOWNLOAD" (thanks to Ron M for this build) :)

---

### Post by squakie on 2012-11-01
On that link that monkeybrain2012 posted, I had to click on the link where it said so and so had a compiled version with all the libs in it and the networking patch - it's kind of in the middle of a paragraph as you read.  I did not install any of the other packages.  As monkeybrain2012 pointed out in his last post above - it's the [COLOR=DarkRed]DOWNLOAD[COLOR=Black] text that shows in that paragraph.

Thanks [/COLOR][/COLOR]monkeybrain2012 for all of your great help!

---

### Post by cmcanulty on 2012-11-02
OK I downloaded it and got a setup.exe file which virtual box won't accept. I am sorry to be so dumb but nothing I try with android works.
I downloaded from the download link in the paragraph below on this web page

[http://www.webupd8.org/2012/07/android-x86-404-ics-rc2-released-with.html]("http://www.webupd8.org/2012/07/android-x86-404-ics-rc2-released-with.html")

The official Android-X86 builds do not have Ethernet support, so you won't have an Internet connection while running Android-X86 in VirtualBox. You can, however, use a custom Android-X86 4.0.4 RC2 build that adds Ethernet support: DOWNLOAD (thanks to Ron M for this build!).

---

### Post by squakie on 2012-11-03
> **cmcanulty said:**
> OK I downloaded it and got a setup.exe file which virtual box won't accept. I am sorry to be so dumb but nothing I try with android works.
I downloaded from the download link in the paragraph below on this web page

[http://www.webupd8.org/2012/07/android-x86-404-ics-rc2-released-with.html](http://www.webupd8.org/2012/07/android-x86-404-ics-rc2-released-with.html)

The official Android-X86 builds do not have Ethernet support, so you won't have an Internet connection while running Android-X86 in VirtualBox. You can, however, use a custom Android-X86 4.0.4 RC2 build that adds Ethernet support: DOWNLOAD (thanks to Ron M for this build!).

First, you are actually going to install this into it's own vm, not an existing one - it's not something you install within another vm.  Then you should just point the virtual macine's cd drive to the iso image that was downloaded, then start the vm.  It needs the actual ISO and needs to boot from that.  Sort of like downloading and installing ubuntu ;)  Once you've installed it, be sure to power down the vm, go to settings and change the cd drive back to the physical drive, then restart the vm.  Not doing so will just get you in a big loop of install, restart, asking me to install again, restart, etc.

I think you got the correct download - just go to the 
**Download for VirtualBox**

 
section and download the ISO as you noted from Ron M. via he big red download right in front of it on the same line.  You are actually making a completely new vm that only has android in it - don't try to install it in something like a vm running Windows.

---

### Post by cmcanulty on 2012-11-03
when I click on the download I get an exe file not an iso I am about to give up a week of total frustration

---

### Post by newb85 on 2012-11-03
> **cmcanulty said:**
> when I click on the download I get an exe file not an iso

Make sure you're clicking the link that says "Click here to start download from sendspace".  I see other links that look like they're for the download, but really, they're ads.

---

### Post by cmcanulty on 2012-11-03
can you please post the link I find nothing on the page saying download from sendspace

---

### Post by newb85 on 2012-11-03
Clicking the link for Ron M's build should take you to [http://www.sendspace.com/file/t5a3aj]("http://www.sendspace.com/file/t5a3aj").

I haven't tried that .iso yet, but I'm downloading it now, and it's definitely an .iso.

---

### Post by cmcanulty on 2012-11-03
OK thanks I was clicking download above that which was an exe will update after I try the install thanks

---

### Post by cmcanulty on 2012-11-03
OK I got it installed and running. 2 issues the mouse isn't operational and I have a very weird desktop on it see screenshot without a mouse I can't access anything to change it

---

### Post by newb85 on 2012-11-03
Machine>Disable Mouse Integration should fix the mouse issue.

---

### Post by uRock on 2012-11-03
Not an ubuntu support question. Moved to Virtualization sub-forum.

---

### Post by cmcanulty on 2012-11-03
the reason I am having so many problems is I don't have any of the menu options people refer to for example there is no devices menu and there is no disable mouse integration even in the greyed out items

---

### Post by newb85 on 2012-11-03
Are you using Unity?

---

### Post by squakie on 2012-11-03
one thing to keep in mind:  it's android, it thinks it's installing on a phone and a phone doesn't have a mouse, etc..  When you boot the vm, does it come up with the box telling/asking about mouse integration?  I have since deleted that vm as it really wasn't much for me compared to my tablet, but I remember getting that screen and having to answer yes.   I did have a working mouse that acted like a stylus.

As far as your screen shot - not sure what you're going to do.  For some reason it seems to think "down" is on the left, and as we all know we don't have the hardware in our PC's to let it determine otherwise.  I would need to go back and look for docs, etc., to try to figure that one out.

I also just got up from bed, so I hope this is making some sense - I haven't had my shot of caffeine yet ;)

---

### Post by squakie on 2012-11-03
> **newb85 said:**
> Are you using Unity?

I think I know where you're going with that - but when I tried this there weren't any entries on the top bar either - maybe (hopefully) it will be different for the OP. ;)

---

### Post by newb85 on 2012-11-03
The menus should be a part of VirtualBox, not the guest OS.  They work for me.  And once I disabled mouse integration, the mouse worked fine for me as well.

Are these menus missing if you install a different guest OS on VB?

Also, what version of VB are you running?

---

### Post by squakie on 2012-11-03
> **newb85 said:**
> The menus should be a part of VirtualBox, not the guest OS.  They work for me.  And once I disabled mouse integration, the mouse worked fine for me as well.

Are these menus missing if you install a different guest OS on VB?

Also, what version of VB are you running?

I just re-downloaded and installed to test again, and this time the menus are on the top bar.  So, don't know what dumb thing I must have done last time (I've actually been running XP and a couple of other linux distros in VB for years now).

So at any rate, that should fix it for the OP. 

Thanks for helping out here!  ;)

---

