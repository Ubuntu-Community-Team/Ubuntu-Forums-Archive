---
title: "who says that you don't need to reboot for linux?"
date: 2010-10-17
forum: The Cafe
---

### Post by superarthur on 2010-10-17
recently, the workstation in my uni freezes when I try to open the file manager or the terminal.
and reboot works...

---

### Post by Spice Weasel on 2010-10-17
Me. 45 days uptime.

---

### Post by pwnst*r on 2010-10-17
> **superarthur said:**
> recently, the workstation in my uni freezes when I try to open the file manager or the terminal.
and reboot works...

Nobody.  It doesn't happen as often as Windows, but system updates make you reboot as well.

Extremely rare reboots unless it's a server is a myth, unless you're some overzealous fanboy.

---

### Post by Half-Left on 2010-10-17
Well, in general you don't but as the universe is, things can go wrong.

---

### Post by TheNessus on 2010-10-17
> **superarthur said:**
> recently, the workstation in my uni freezes when I try to open the file manager or the terminal.
and reboot works...

I reboot when I get 'segmentation fault' on occasions for no reason when trying to start certain applications. But that's about the only time I reboot. That and dual-booting that is.

---

### Post by Jeroensum on 2010-10-17
My server (converted old workstation) had been up for 327 days until the powersupply died and my laptop currently has an uptime of 14+ days. Last reboot was because I forgot to plug in the power in time. I don't even reboot for kernel updates anymore thanks to ksplice so only really buggy code, a screwup on my part or hardware failure force me to reboot. :)

---

### Post by Frogs Hair on 2010-10-17
I am prompted to reboot after some security updates,  kernel updates , driver installation.

---

### Post by kio_http on 2010-10-17
I say you do not need to reboot in a working linux system. (That means good drivers and bug free software) The only reason to reboot would be to launch a different kernel i.e upgrading the kernel or launching a different kernel flavor.

---

### Post by CraigPaleo on 2010-10-17
> **superarthur said:**
> recently, the workstation in my uni freezes when I try to open the file manager or the terminal.
and reboot works...

You don't have to reboot as often but if you're having these problems every time, it's not normal. I'd do some googling or post in the support section.

---

### Post by superarthur on 2010-10-17
> **CraigPaleo said:**
> You don't have to reboot as often but if you're having these problems every time, it's not normal. I'd do some googling or post in the support section.

the workstation mounted on a network drive that changes its IP address (it's creepy, I didn't know how it happened)
anyway, the workstation was still looking for the drive at the wrong IP address, and refused to let us fix it via the terminal (the terminal freezes)
and rebooting the system works (we can use the terminal again and change the IP address to the new one)

---

### Post by pwnst*r on 2010-10-17
> **kio_http said:**
> I say you do not need to reboot in a working linux system. (That means good drivers and bug free software) The only reason to reboot would be to launch a different kernel i.e upgrading the kernel or launching a different kernel flavor.

You don't NEED to unless you wish to ignore the prompts.

---

### Post by neoargon on 2010-10-17
I have been using Ubuntu for about 3 years. It's my main OS.I don't see that much Advantage in linux as many people say . Ubuntu also freezes ,sometimes ,even ctrl+alt+F1 doesn't bring  terminal . That is complete freeze , need to reset .

---

### Post by Spice Weasel on 2010-10-17
Can we agree that it's a case of **your mileage (and distribution) may vary?**

---

### Post by kaldor on 2010-10-17
From my experience, it's usually Compiz that causes the lock-ups.

When I had compiz running often (Ubuntu 8.04-8.10) I would have freezes everyday. Since disabling that, I can't remember the last time I had a freeze that required me to reboot. If there was a lockup, I would simply ctrl-alt-backspace to re-login and that'd work.

On that note, for some reason OS X requires a reboot after every update.. even if it's just software like Safari or iTunes. Weird.

---

### Post by CraigPaleo on 2010-10-17
> **Spice Weasel said:**
> Can we agree that it's a case of **your mileage (and distribution) may vary?**

Definitely! I've been going between [Pinguy OS]("http://distrowatch.com/pinguy") and KDE. I play with every plasmoid under the sun and one day last week I had three panels going, switching plasmoids all over the place, trying repeatedly to get an "upload to imageshack" plasmoid to work (I downloaded it from KDE-look) and the whole screen froze. There was nothing I could do but reboot. That was the only freeze I've had under 10.10 but I was being hard on the system.

 I've never HAD to reboot under Pinguy OS but that's more modular. Playing with widgets and panels aren't likely to bring the whole OS to a screeching halt.

Edit: That plasmoid that froze the system had a big ? as its icon. I should have had a clue. So that was really my fault.

---

### Post by themarker0 on 2010-10-17
I reboot my laptop maybe once to twice a day when i use it. Then again its a single core 1.4, running 6-7 hours on battery.

---

### Post by inobe on 2010-10-17
if you know specific commands and know how to restart services their is no need unless you upgrade the linux kernel, the kernel upgrade doesn't necessarily mean you have to reboot asap, you can get things done before you reboot.

---

### Post by Sporkman on 2010-10-17
Kernel updates or failed resume-after-suspends (about 10% of the time) force reboots for me.

---

### Post by cariboo on 2010-10-17
The only reason a reboot is asked for when doing driver installs and updates, is it's much easier for the average user to reboot than it is to restart a service. What would you rather do if you installed a new video driver?

Open a console, Ctrl-Alt-F1 and type

```
sudo service gdm restart
```

Or just click the power icon and select reboot.

---

### Post by chriswyatt on 2010-10-17
> **cariboo907 said:**
> The only reason a reboot is asked for when doing driver installs and updates, is it's much easier for the average user to reboot than it is to restart a service. What would you rather do if you installed a new video driver?

Open a console, Ctrl-Alt-F1 and type

```
sudo service gdm restart
```

Or just click the power icon and select reboot.

Well, the command if I could remember it.

---

### Post by Shining Arcanine on 2010-10-17
:P> **pwnst*r said:**
> Nobody.  It doesn't happen as often as Windows, but system updates make you reboot as well.

Extremely rare reboots unless it's a server is a myth, unless you're some overzealous fanboy.

Actually, Linux does not need reboots except in very rare instances. If you know what is being changed on a system and how all of the daemons interact with one another, you can simply restart the daemons for the updates to be applied to your system. If you have a kernel upgrade, most people would need to reboot, but there are ways around that if you know what you are doing. kexec and ksplice are two ways of doing it:

[http://www.ksplice.com/](http://www.ksplice.com/)

In theory, you should be able to avoid rebooting, but in practice, rebooting is easier.

---

### Post by superarthur on 2010-10-17
I am talking about rebooting when something freeze, not rebooting when there's an update...

---

### Post by CraigPaleo on 2010-10-17
> **chriswyatt said:**
> Well, the command if I could remember it.

Exactly! That's why, whenever possible, we should teach the GUI way if/when applicable along with the CLI way. 

If you have a problem that can be rectified by either method, six months down the road, most people will remember the graphical way.

Many newbies are turned off because they think they HAVE to use the command line since that's what they're used to hearing in response to support questions. The CLI is a great tool but most of the time, there's a GUI way to deal with things.

---

### Post by mordoc on 2010-10-17
I can think of a small numbers of time that I was very thankful either for the virtual consoles or being able to ssh into the "frozen" box to kill whatever X application crashed...

I would like to see something that was user accessible in the use of ksplice, making it part of a server release would be fantastic to show up the windows people...

---

### Post by pwnst*r on 2010-10-17
> **Shining Arcanine said:**
> :P

Actually, Linux does not need reboots except in very rare instances. If you know what is being changed on a system and how all of the daemons interact with one another, you can simply restart the daemons for the updates to be applied to your system. If you have a kernel upgrade, most people would need to reboot, but there are ways around that if you know what you are doing. kexec and ksplice are two ways of doing it:

[http://www.ksplice.com/](http://www.ksplice.com/)

In theory, you should be able to avoid rebooting, but in practice, rebooting is easier.

When zealots spew on about how you don't have to reboot ubuntu, they're lying to new users.  New users aren't going to restart daemons, come on, lol.

---

### Post by NightwishFan on 2010-10-17
My life for Aiur! It still needs to reboot less however quite recently this issue is moot. I find it a lot easier to suggest a reboot rather than anything else on updates or problems.
[IMG]http://riphoenix.com/Zealot2.JPG[/IMG]

---

### Post by Shining Arcanine on 2010-10-17
> **CraigPaleo said:**
> Exactly! That's why, whenever possible, we should teach the GUI way if/when applicable along with the CLI way. 

If you have a problem that can be rectified by either method, six months down the road, most people will remember the graphical way.

Many newbies are turned off because they think they HAVE to use the command line since that's what they're used to hearing in response to support questions. The CLI is a great tool but most of the time, there's a GUI way to deal with things.

It is called the terminal. CLI is a Windows term. Anyway, let new users install Linux without an installer. They will learn how to use the terminal with only a few installations.

> **pwnst*r said:**
> When zealots spew on about how you don't have to reboot ubuntu, they're lying to new users.  New users aren't going to restart daemons, come on, lol.

Well, I use Gentoo Linux, so I likely have more experience with daemons than most Ubuntu Linux users. In my opinion, the details of how things work are well enough hidden with Ubuntu that it is difficult to do the things on Ubuntu Linux that I do on Gentoo Linux.

---

### Post by billcSailor on 2010-10-17
> **CraigPaleo said:**
> Exactly! That's why, whenever possible, we should teach the GUI way if/when applicable along with the CLI way. 

If you have a problem that can be rectified by either method, six months down the road, most people will remember the graphical way.

Many newbies are turned off because they think they HAVE to use the command line since that's what they're used to hearing in response to support questions. The CLI is a great tool but most of the time, there's a GUI way to deal with things.


I agree with you 100%, or at least I *would*.  Problem is there is no one GUI way usually.  Each distro and often version of each distro has another GUI application to make system changes.  But the command line version usually has more broad compatibility, heck in some cases it may work with SystemV or BSD.  There are network setup commands for instance that work on pretty much all nix's, but the GUI stuff has 75 different programs a distro might include.  

Even if the user has the right GUI program you give instructions for he may not have the right *version*. I've found myself reading instructions for utilities that were TEN YEARS out of date, with no indication of that on the web page.  Using instructions for a long dead previous version can cause a lot of problems.  Your instructions are going to be on the web long after you've forgotten about them (please date them).  The words *latest version* always seem to accompany 15 year old help files. :(

Old command line programmers are no more disciplined about interfaces than their GUI younger brothers, but often their apps are depended on by shell scripts or exec'd by other software (often GUI's) so they HAVE to keep a stable interface.  And likewise because other software calls standard setup utilities distros have to include these standards.  The system works *toward* standards for command line apps.

---

### Post by Artemis Fowl on 2010-10-17
I've only needed to reboot during weird glitches caused by minecraft where keyboard input becomes ignored, once because of a freeze, and during updates.

---

### Post by toupeiro on 2010-10-17
> **superarthur said:**
> I am talking about rebooting when something freeze, not rebooting when there's an update...

I must say, this is such an extreme rarity when compared to other OSes that to hold all linux based OSes accountable to the rare combination of events that has to transpire for this to happen is not realistic.  Sure, linux CAN freeze to the point you don't even have tty responsiveness but in 12 years, I've seen that happen once or twice, and not coincidentally it was tied to failing or not-completely-supported hardware..

I've seen filesystems in linux become completely corrupt, and the OS will still remount itself read only and allow you to shut other services down as gracefully as possible.  It's more fault tolerant than any other desktop OS or server OS out there, but NOTHING is failproof.  I'm sorry you had a bad experience and your 'puter froze but that doesn't mean Linux is failure prone and reboot happy.

---

### Post by Shining Arcanine on 2010-10-17
> **superarthur said:**
> I am talking about rebooting when something freeze, not rebooting when there's an update...

Assuming that you run Ubuntu and you are having something freeze on you, it is probably an issue with X. You can restart X without restarting your computer. It is faster and less potentially destructive to your file system.

---

### Post by Ahava591 on 2010-10-17
I royally fouled up I think three times in the first couple of months when I started using 9.10.

I don't know that there's been a case *with my usage* where a reboot has been required; rebooting after updates has simply been easiest for me up to this point. 


Yes, I have made mistakes which necessitated reboots; I haven't read online or in print that with Linux, any distribution, you will only need to restart after updates.
-Never have I seen the claim that you can screw up and not need a restart.

---

### Post by CharlesA on 2010-10-17
I only reboot my server after updates that bug me with*** *** Restart Required ******

If I really wanted 99.9% uptime, I would check out ksplice, but I don't feel like paying for it since I am running Ubuntu Server at home and uptime really doesn't matter all that much, as long as everyone is notified before it's rebooted.

---

### Post by Khakilang on 2010-10-18
My computer hang once when I process my image in Gimp for no reason and I had to press that reset button which I haven't touch it since I install Ubuntu. Most of the time it had to reboot when its update the kernel and the hardware drivers. Compare to Window I had more reboot than I could remember.

---

### Post by MisterGaribaldi on 2010-10-18
I've known of people who will go to extraordinary lengths just to have huge uptime stats to brag about.

Personally, I think it's all very over-rated.

My Debian-based server I will reboot from time to time as needed by what I do with it. I could care less about its "uptime" stats. As long as in general I can leave it up and running, I don't mind about the occasional reboot.

---

### Post by NightwishFan on 2010-10-18
> **Khakilang said:**
> My computer hang once when I process my image in Gimp for no reason and I had to press that reset button which I haven't touch it since I install Ubuntu. Most of the time it had to reboot when its update the kernel and the hardware drivers. Compare to Window I had more reboot than I could remember.

Some gimp plugins can fill up ram really quick.

---

### Post by msandoy on 2010-10-18
I need to reboot my laptop and workstation quite regularly, my laptop a few times a week, since I just pull the plug and let it drain the battery over night for maintenance reasons, and my workstation is switched off in the evening when I'm finished with it for the day. My server is continously powered on, It's and Asus eee box, consuming minimal ammounts of power, while doing its job. 
Some folks here mentioned that most reboots occur due to X freezing. I agree with that, but someone decided to make it harder to get out of that mess by disabling "ctrl+Alt+Backspace" by default. I think that was a bad decision.

---

### Post by CraigPaleo on 2010-10-18
> **Shining Arcanine said:**
> It is called the terminal. CLI is a Windows term. Anyway, let new users install Linux without an installer. They will learn how to use the terminal with only a few installations.

[CLI]("http://en.wikipedia.org/wiki/Command-line_interface") a general term much as GUI. Anyway there's also [CLI Companion]("http://okiebuntu.homelinux.com/okwiki/clicompanion/") for Terminal virgins.

@billcSailor, Very good points.

---

### Post by mainerror on 2010-10-18
> **superarthur said:**
> recently, the workstation in my uni freezes when I try to open the file manager or the terminal.
and reboot works...

Well most people don't understand that faulty hardware can cause any system to lockup. It doesn't matter if it is Windows or any Linux distribution. There is nothing you can do about such things.

On the other hand if something is mis-configured (Gnome, KDE, etc.) then of course your visual (click-able) part of the system might lockup and won't respond. Of course also the virtual terminal application. If you hit Ctrl + Alt + F1 for example you will most likely get to a real terminal where you can restart/fix your desktop manager or other faulty software.

> **TheNessus said:**
> I reboot when I get 'segmentation fault' on occasions for no reason when trying to start certain applications. But that's about the only time I reboot. That and dual-booting that is.

Sounds like some hardware problems. Have you tried to run a Memtest already?

> **neoargon said:**
> Ubuntu also freezes ,sometimes ,even ctrl+alt+F1 doesn't bring  terminal . That is complete freeze , need to reset .

Faulty hardware?

---

