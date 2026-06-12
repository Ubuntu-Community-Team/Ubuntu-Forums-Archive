---
title: "Anyone think Yum's UI is better than Apt-get?"
date: 2009-11-26
forum: The Cafe
---

### Post by Luke has no name on 2009-11-26
I much prefer yum's information layout when you "yum install" something to apt-get's lumped together, less informative printout.

Anyone else notice the difference?

---

### Post by the yawner on 2009-11-26
> #yum install openldap
Loading "priorities" plugin
Setting up Install Process
Parsing package install arguments
Resolving Dependencies
--> Running transaction check
--> Processing Dependency: openldap = 2.3.27-8.el5_1.3 for package: openldap-devel
--> Processing Dependency: openldap = 2.3.27-8.el5_1.3 for package: openldap-clients
---> Package openldap.i386 0:2.3.43-3.el5 set to be updated
--> Running transaction check
---> Package openldap-devel.i386 0:2.3.43-3.el5 set to be updated
---> Package openldap-clients.i386 0:2.3.43-3.el5 set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

=============================================================================
 Package                 Arch       Version          Repository        Size
=============================================================================
Updating:
 openldap                i386       2.3.43-3.el5     base              293 k
Updating for dependencies:
 openldap-clients        i386       2.3.43-3.el5     base              214 k
 openldap-devel          i386       2.3.43-3.el5     base              1.5 M

Transaction Summary
=============================================================================
Install      0 Package(s)
Update       3 Package(s)
Remove       0 Package(s)

Total download size: 2.0 M
Is this ok [y/N]: n


Hmm... I think I agree.

---

### Post by Kingsley on 2009-11-26
If only only APT and Yum could have a freak baby containing the good qualities of both. We'd have the speed of apt-get and the wonderful layout of Yum!

---

### Post by Warpnow on 2009-11-27
Yeah, Yum has been slow every time I've tried it. I'd prefer speed.

---

### Post by doorknob60 on 2009-11-27
Know what's better? Pacman :) It's quicker than both by far, and it has output more similar to yum, and with yaourt it makes the perfect package manager.

---

### Post by the yawner on 2009-11-27
What other packaging system has a feature similar to delta rpms?

---

### Post by Xbehave on 2009-11-27
have you tried aptitude it's a more informative UI for apt, while still faster than yum.

Last time i used pacman i thought it was slower than apt, but that's probably a good thing as it took longer to kill my system.

---

### Post by PryGuy on 2009-11-27
GUI UI is better, the whole yum is rubbish! ;)

---

### Post by Excedio on 2009-11-27
Out of curiosity... Is it important? The program is being installed and as others are stating, apt is fast.

Isn't the most important thing... installing the program?

---

### Post by szymon_g on 2009-11-27
> **the yawner said:**
> What other packaging system has a feature similar to delta rpms?

as far i know- only rpm-based distros use deltas.
another nice package manager (which supports deltas) is zypper.
Poldek is also nice- it uses all functionality provided by rpm's (for example: in interactive mode it gives you ability to select necessary packages /if 2 or more of them provide required things, like cron or xorg-drivers/)- unfortunatelly, as far i know, it doesn't use deltas :/

---

### Post by Xbehave on 2009-11-27
There is no reason you couldn't use delta debs, but in my experience the bandwidth savings are counteracted by the slowness of doing a binary diff (it might just be that yum is slow though, anybody done used zypher with &#916;rpms), so unless you have a bandwidth cap it's not worth it. That said it would be nice if ubuntu offered &#916;debs
1) so people can realise this for themselves
2) to speed up updates when servers are being hammered
3) to benefit people with bandwidth caps

---

### Post by gnomeuser on 2009-11-27
The yum command line tools seems so much better designed, at least  for giving output and working with it on a day to day level. I greatly miss it after I switched to Ubuntu.

As for the GUI it doesn't matter that much, PackageKit will save us all regardless and try as they might to avoid it with lies and distortions, Ubuntu will one day follow along here as well. PackageKit also defines a commandline set of tools but I honestly haven't worked much with those, however they were designed in part by the same people who have worked on yum so I hope they share some of those advantages.

---

### Post by zekopeko on 2009-11-27
> **gnomeuser said:**
> As for the GUI it doesn't matter that much, PackageKit will save us all regardless and try as they might to avoid it with lies and distortions, Ubuntu will one day follow along here as well. PackageKit also defines a commandline set of tools but I honestly haven't worked much with those, however they were designed in part by the same people who have worked on yum so I hope they share some of those advantages.

Please don't accuse Ubuntu/Debian devs of being liars. Debian and Ubuntu had a legitimate bug against PK. The author of PK just had a different concept how certain aspects of package management should work and Debian didn't want to have regressions. But that is being fixed now.
Now if we could only kill the horror that is PK-gnome/kde...

---

### Post by RiceMonster on 2009-11-27
> **zekopeko said:**
> Now if we could only kill the horror that is PK-gnome/kde...

what's wrong with Gnome Package Kit?


As for this thread, I prefer yum too. It just feels much cleaner overall.

---

### Post by slakkie on 2009-11-27
I couldn't care less, yum is ok, slower due to some tricky things it does, but aptitude/apt-get are fine. I don't mind the clutter of apt, you also have a logfile (/var/log/aptitude.log and/or /var/log/apt/term.log) where you can have a look at all the data.

---

### Post by docus on 2009-11-27
I'm going to give Fedora a try this weekend (after failing to get my mobile broadband working in Arch... :( ) - is there anything equivalent to Getdebs for Fedora, or any alternative repos?  I ask because I don't think Nicotine+ is in the main Fedora repos, and it's an app I use a lot.

---

### Post by bodhi.zazen on 2009-11-27
On these forums I suspect most prefer apt

With that said, yum has come a long ways and rpm hell has not occurred to me in many years. yum is now much faster as compared to a few years ago and there are a number of plugins which improve yum as well. fastestmirrior and deltarpm aer two.

---

### Post by Xbehave on 2009-12-03
So after moving back to apt i missed yum list, but this very simple alias is still faster/easier than yum :D
```
alias apt-list="apt-cache search all | grep "
```
and the UI is cleaner so i thought i'd share (even though its obvious)

---

