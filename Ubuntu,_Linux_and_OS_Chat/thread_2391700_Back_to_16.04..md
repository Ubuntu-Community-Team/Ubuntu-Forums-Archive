---
title: "Back to 16.04."
date: 2018-05-12
forum: Ubuntu, Linux and OS Chat
---

### Post by xubu2 on 2018-05-12
Last weekend i did a fresh install of xubuntu 18.04 and then last thursday it happened.
I booted up xubuntu 18.04 and all i got was a black screen with a cursor in the top left corner.
The screen was switching on and off to constantly.
There was nothing i could do but a new install of xubuntu 18.04.
After installation all went well until a few reboots later the same thing happened.
Black screen turning on and off and nothing else.
The only solution for me was reinstalling 16.04.

Regards from a very disappointed xubuntu user.

This guy had the same thing on ubuntu: [https://www.youtube.com/watch?v=6lbgtZw-pYQ](https://www.youtube.com/watch?v=6lbgtZw-pYQ)

Edit: I'm gonna wait now till 18.04.1 is out.

---

### Post by Frogs Hair on 2018-05-12
Moved to* UL & OS Chat.*

---

### Post by ajgreeny on 2018-05-12
Might be useful to know your hardware.

I've been using Xubuntu 18.04 since well before it was released and had no major problems of any sort on my all Intel machine with no discreet graphics card.

---

### Post by TheFu on 2018-05-12
I have a similar issue on 16.04 (no DE) with Core i3 graphics when coming out of standby.  Bringing another window to the front has always fixed it.  It doesn't happen all the time, about 2x  a month.   Last fall, I was using the 10.org (intel) drivers, as those have been deprecated, I'm using the stock drivers included normally in 16.04.
Package name is: xserver-xorg-video-intel-hwe-16.04   version 2:2.99.917+git20170309-0ubuntu1~16.04.1

```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:e0000000-e0ffffff memory:d0000000-dfffffff ioport:1800(size=64) memory:c0000-dffff
```

---

### Post by PaulW2U on 2018-05-12
> **xubu2 said:**
> Regards from a very disappointed xubuntu user.
Unfortunately the Xubuntu development team and the small number of users that test the Xubuntu final release ISOs can't test on all variations of hardware that might be used by the releases' eventual users.

I forced an upgrade from Xubuntu 16.04 to 18.04 and it didn't go well. My subsequent clean install (on a laptop) has a problem resuming from suspend for which I've found a workaround. Xubuntu like the other [flavours]("https://www.ubuntu.com/download/flavours") really needs testers who report their problems back to the respective development teams most of which are very much smaller than you probably think they are.

Whether the 18.04.1 release will resolve **your** issues remains to be seen but if no one else reports similar problems, giving full details of the hardware that is being used, then they may well remain unfixed.

[Get Involved]("https://xubuntu.org/contribute/") is something that you might want to take a look at.  :)

---

### Post by xubu2 on 2018-05-12
My hardware is a laptop from acer aspire v13 with i5-5257u motherboard.
[https://ark.intel.com/products/84985/Intel-Core-i5-5257U-Processor-3M-Cache-up-to-3_10-GHz](https://ark.intel.com/products/84985/Intel-Core-i5-5257U-Processor-3M-Cache-up-to-3_10-GHz)
That's all i know.
16.04 worked fine, so did 14.04.
The first time i got the black screen was 5 days after intallation of 18.04 (last thursday).

Edit: i don't have a second graphics card, just the onboard intel.

---

### Post by xubu2 on 2018-05-13
I think it's a graphics driver problem.
Had the same experience with arch years ago.

Edit: i don't think it's a Xubuntu problem.
[https://www.youtube.com/watch?v=6lbgtZw-pYQ](https://www.youtube.com/watch?v=6lbgtZw-pYQ)
The guy in this video had the same problem with Ubuntu.
For me the screen was black instead of orange :)
And the screen kept switching on and off constantly.
Rebooted with contol-alt-delete several times with same result.
Didn't even get the login screen.

---

### Post by makitso on 2018-05-13
I had this same problem with xubuntu 17.10 on my Thinkpad T60.  At boot time I added nomodeset to the kernel boot parameter and that fixed it.  After the boot I updated the grub file to make it permanent.

[https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by xubu2 on 2018-05-13
> **makitso said:**
> I had this same problem with xubuntu 17.10 on my Thinkpad T60.  At boot time I added nomodeset to the kernel boot parameter and that fixed it.
And how do you do that?
I'm just a noob  ;)
Edit: Think i'm gonna wait till 18.04.1 is out.
Hopefully the problem is fixed by then.

---

### Post by makitso on 2018-05-13
I edited post #8 to include a link.

---

### Post by xubu2 on 2018-05-13
Yes i've looked at it, but i think my problem is bigger than that.
I always delete quiet splash in grub after a new install.
Thanks for the help.

Edit: it happened for the first time 5 days after installation.

---

### Post by xubu2 on 2018-05-13
Got a few updates in those 5 days, but can't remember what updates.
Maybe that's the problem.

---

### Post by xubu2 on 2018-05-14
> **PaulW2U said:**
> 
Whether the 18.04.1 release will resolve **your** issues remains to be seen but if no one else reports similar problems, giving full details of the hardware that is being used, then they may well remain unfixed.

[Get Involved]("https://xubuntu.org/contribute/") is something that you might want to take a look at.  :)

I've posted my hardware.
If i'm the only one with this problem then i'm seriously screwed.
My suspicion is a fault in [B]acpid.
[/B]Had some problems in the past with it.
HELP!

---

### Post by mörgæs on 2018-05-14
> **xubu2 said:**
> Think I'm gonna wait till 18.04.1 is out.
Hopefully the problem is fixed by then.

Have you reported it properly in Launchpad? Else you can't expect a fix.

---

### Post by xubu2 on 2018-05-14
> **mörgæs said:**
> Have you reported it properly in Launchpad? Else you can't expect a fix.
How am i supposed to do that?
Looked at the site but don't know where to report.

Edit: Think i did it right.
[https://answers.launchpad.net/ubuntu/+question/669013](https://answers.launchpad.net/ubuntu/+question/669013)

---

### Post by xubu2 on 2018-05-15
[COLOR=#000000]Launchpad didn't brought any solutions.
Anybody with the same problems here?
[/COLOR]

---

### Post by mörgæs on 2018-05-15
[https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by xubu2 on 2018-05-15
When i click on [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)[FONT=Ubuntu][COLOR=#333333] i don't know what to do next.
Edit: Thinking off switching to an android tablet.
Problem solved.
Sorry.[/COLOR][/FONT]

---

### Post by xubu2 on 2018-06-06
Still waiting for some news.
I'm pretty sure the black screen at bootup is because of the graphics driver update i received on may 10.
Any news on the intell drivers being updated again since then?
Is the problem fixed?

---

### Post by monkeybrain20122 on 2018-06-06
> I'm pretty sure the black screen at bootup is because of the graphics driver update i received on may 10.
Any news on the intell drivers being updated again since then?


If it was a graphic driver problem then upgrading mesa (could be done in text mode) might fix it [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa) 

Since you have reinstalled 16.04 there is no way to find out. But if you have a spared hd laying around you might want to install xubuntu 18.04 on it so you can do some tests.

---

### Post by xubu2 on 2018-06-07
> **monkeybrain20122 said:**
> If it was a graphic driver problem then upgrading mesa (could be done in text mode) might fix it [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa) 

Since you have reinstalled 16.04 there is no way to find out. But if you have a spared hd laying around you might want to install xubuntu 18.04 on it so you can do some tests.

Thanks for the answer.
But i'll rather wait for an update.

edit: this is all a bit complicated ;)
The system doesn't even bootup.

---

### Post by monkeybrain20122 on 2018-06-07
> **xubu2 said:**
> Thanks for the answer.
But i'll rather wait for an update.

I won't be holding my breath. Normally mesa update won't happen until 04.2 releases though it is kind of strange that you said you had yours updated a few days ago. Are you sure that you didn't have any ppa already activated (such as Oibaf) In that case the course of action would be to purge the ppa in question.

---

### Post by xubu2 on 2018-06-07
> **monkeybrain20122 said:**
> I won't be holding my breath. Normally mesa update won't happen until 04.2 releases though it is kind of strange that you said you had yours updated a few days ago. Are you sure that you didn't have any ppa already activated (such as Oibaf) In that case the course of action would be to purge the ppa in question.

18.04 worked for 5 days.
Then i got the graphics driver update on may 10 and i got a black screen after a cold boot.
I didn't have any ppa's installed.

---

### Post by xubu2 on 2018-06-08
[COLOR=#000000][INDENT]I'm pretty sure the black screen at bootup is because of the graphics driver update i received on may 10.
Any news on the intell drivers being updated again since then?
Is the problem fixed?[/INDENT]

Talking about the  **xserver-xorg-video  **packages.

[/COLOR]

---

### Post by xubu2 on 2018-09-01
Bump.
Time to reboot this old thread :)
Is the package **xserver-xorg-video-intel **updated recently in 18.04?
I'm still waiting.

---

### Post by jeremy31 on 2018-09-01
No, last change was
```
xserver-xorg-video-intel (2:2.99.917+git20171229-1) unstable; urgency=medium

  * New upstream snapshot.

 -- Timo Aaltonen <tjaalton@debian.org>  Wed, 17 Jan 2018 10:13:50 +0200

```
You might want to see if the Intel repo has newer version

---

### Post by xubu2 on 2018-09-01
Ok, thanks for the quick answer.
Guess i'll have to buy a new laptop then :(

---

### Post by monkeybrain20122 on 2018-09-01
> **xubu2 said:**
> Ok, thanks for the quick answer.
Guess i'll have to buy a new laptop then :(

If it is an update that causes the problem and you know exactly which package causes it, you can either reinstall and pin the package or try to find a ppa to upgrade it, this ppa has a newer  xserver-xorg-viedeo-intel [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa) Worth a try before you spend the $$$ to get your new laptop, though you can send me the old one if you do.:popcorn::P

---

### Post by xubu2 on 2018-09-01
Thanks for the info, might give that a try.
Don't want to go back to windows after 5 years with linux  :(

---

### Post by monkeybrain20122 on 2018-09-01
I would first add the ppa and upgrade (which you can do in text mode with networking) then reboot. If that doesn't work, make a fresh install of 18.04 and then pin the problematic package [https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

---

