---
title: "Is there a compelling reason to install MS powershell"
date: 2016-08-21
forum: The Cafe
---

### Post by cariboo on 2016-08-21
I see that powershell is now available for install. Being a very casual windows user, I have Windows 7 & 10 installed on two of my systems, but I very rarely boot into either, powershell seems to me to be just another terminal. What does it do better or different from xterm or any of the other terminals available in the repositories.

---

### Post by Dragonbite on 2016-08-22
I agree with you, trying to figure out why I would use Powershell on Linux.

If I knew/understood/used Powershell, that may be different, but I don't yet.

I guess if you are managing a mixed-OS environment it may be helpful to use fewer tools on all of them.  So no you can use Powershell (Win) on all of them, or Bash on Windows to do the same thing.  

I didn't think Mac's command line capabilities were all that important, but maybe it is and this is the counter?

---

### Post by Omar_Jair on 2016-08-22
The only thing i can think of is for people that are migrating to linux, maybe if they are used to powershell but not bash they can use it to feel more like "home".

---

### Post by Dragonbite on 2016-08-22
I don't know... are there really that many people using Powershell now?  Especially people outside of the IT/Sys Admin industry?

---

### Post by #&amp;thj^% on 2016-08-22
I see no compelling reason for it myself...but from Softpedia
> The company claims that it no longer wants Windows  and Linux teams &#8220;to work separately, but to work together more easily,&#8221;  and this is one of the main reasons it&#8217;s open-sourcing PowerShell.
 &#8220;We started by open sourcing small portions of  PowerShell and talking to a number of our partners who were experienced  with open source to understand what it took to succeed,&#8221; the company  says, adding that &#8220;we fit in well with the architecture because most of  the original PowerShell team had deep Unix backgrounds.&#8221;
 On Linux, PowerShell will initially be available on  Ubuntu, Centos, and Red Hat, and Alpha builds are already available for  download on [GitHub]("https://github.com/PowerShell/PowerShell/tree/master/docs/learning-powershell").


So???
Source: [http://news.softpedia.com/news/microsoft-makes-powershell-open-source-releases-it-on-linux-and-mac-507466.shtml](http://news.softpedia.com/news/microsoft-makes-powershell-open-source-releases-it-on-linux-and-mac-507466.shtml)

---

### Post by Dragonbite on 2016-08-22
> **1fallen said:**
> I see no compelling reason for it myself...but from Softpedia
> The company claims that it no longer wants Windows and Linux teams “to work separately, but to work together more easily,” and this is one of the main reasons it’s open-sourcing PowerShell.  “We started by open sourcing small portions of PowerShell and talking to a number of our partners who were experienced with open source to understand what it took to succeed,” the company says, adding that “we fit in well with the architecture because most of the original PowerShell team had deep Unix backgrounds.” On Linux, PowerShell will initially be available on Ubuntu, Centos, and Red Hat, and Alpha builds are already available for download on GitHub.
So???
Source: [http://news.softpedia.com/news/microsoft-makes-powershell-open-source-releases-it-on-linux-and-mac-507466.shtml](http://news.softpedia.com/news/microsoft-makes-powershell-open-source-releases-it-on-linux-and-mac-507466.shtml)

They worked well with a team of people experienced with Linux and open source to open source Powershell bit-by-bit but it still doesn't tell much about _how_ people will benefit from it (beyond the handful working on it) or how it will be used (in real-world scenarios).

But then again, like I said before I do not use Powershell much so there is a LOT I can be missing.

---

### Post by #&amp;thj^% on 2016-08-22
> **Dragonbite said:**
> They worked well with a team of people experienced with Linux and open source to open source Powershell bit-by-bit but it still doesn't tell much about _how_ people will benefit from it (beyond the handful working on it) or how it will be used (in real-world scenarios).

But then again, like I said before I do not use Powershell much so there is a LOT I can be missing.

Yes it is still very early in development and very rough as is ATM, but like cariboo I am waiting to see any benefit for installing it.
This is not meant to start a flame war or any bad direction here...but I started using Linux with Novel Suse and their partnership with Microsoft, and we all know how that ended.
**Pure Linux suits me just fine.**..My Opinion only (To be noted only):)
There are other sites with more info on this but I just don't care enough (or enough interest) to provide them here.

---

### Post by buzzingrobot on 2016-08-23
If you don't use Powershell on Windows, you'd have no reason to use it on Linux.

Powershell is a scripting language/environment primarily intended for use by Windows sys admins, devs, etc.  Microsoft ported it to Linux to support those kinds of users who work in a mixed Windows/Linux environment.

---

### Post by LastDino on 2016-08-23
If you're a casual windows user, you will probably not even hear about power shell, thats how rare it is for a windows user to go terminal. Very few people know about cmd and know couple of handy commands, mainly to ping IP's and all, but thats about what people use terminal for on windows, and beyond that its usually only IT/sys engineers. However, power-shell is indeed very powerful tool, but only if you're into scripting for windows environment.   

Unless you're into that, there is no real need for any of the Linux user to have Powershell on their system. Imo terminal does whatever we need quite efficiently.

---

### Post by coldraven on 2016-08-23
It seems that Microsoft have already made their terminal commands incompatible with the FOSS world.
[http://www.theregister.co.uk/2016/08/23/your_wget_is_broken_and_should_die_powershellers_tell_microsoft/](http://www.theregister.co.uk/2016/08/23/your_wget_is_broken_and_should_die_powershellers_tell_microsoft/)

---

### Post by Dragonbite on 2016-08-25
> **1fallen said:**
> ...but I started using Linux with Novel Suse and their partnership with Microsoft, and we all know how that ended.

They have all (Red Hat, SUSE and Canonical) reached agreements with Microsoft, though mostly technical and not with sales.  

When SUSE and Microsoft reached  this deal, SUSE was owned by Novell before they sold everything to *Attache*(?).  Their newest owners returned SUSE to Germany and has given it mostly free reign to do what they do best.

So SUSE's failings may be the deal with Microsoft, or management issues with Novell.

> **coldraven said:**
> It seems that Microsoft have already made their terminal commands incompatible with the FOSS world.
[http://www.theregister.co.uk/2016/08/23/your_wget_is_broken_and_should_die_powershellers_tell_microsoft/](http://www.theregister.co.uk/2016/08/23/your_wget_is_broken_and_should_die_powershellers_tell_microsoft/)

MS should say "my bad! let me change it" since wget and curl have been staples of *nix for years!

---

### Post by HermanAB on 2016-08-26
The advantage is being able to run the same scripts on multiple platforms.

Same as with Java: 
Write once, debug everywhere.

---

### Post by kurt18947 on 2016-08-27
> **Dragonbite said:**
> They have all (Red Hat, SUSE and Canonical) reached agreements with Microsoft, though mostly technical and not with sales.  

When SUSE and Microsoft reached  this deal, SUSE was owned by Novell before they sold everything to *Attache*(?).  Their newest owners returned SUSE to Germany and has given it mostly free reign to do what they do best.

So SUSE's failings may be the deal with Microsoft, or management issues with Novell.



**MS should say "my bad! let me change it"** since wget and curl have been staples of *nix for years!

They SHOULD. Let's see if they do, or if this is part of their infamous "extend" phase.

---

### Post by Wadim_Korneev on 2016-09-03
I agree with you, trying to figure out why I would use Powershell on Linux.

---

### Post by ventrical on 2016-09-05
> **cariboo said:**
> I see that powershell is now available for install. Being a very casual windows user, I have Windows 7 & 10 installed on two of my systems, but I very rarely boot into either, powershell seems to me to be just another terminal. What does it do better or different from xterm or any of the other terminals available in the repositories.
  

Powershell now comes installed by default on Windows 10 free version.

Regards..

---

### Post by kurt18947 on 2016-09-05
> **Wadim_Korneev said:**
> I agree with you, trying to figure out why I would use Powershell on Linux.

I've read that 20% of Azure VMs are Linux. Microsoft is placing a pretty large bet on Azure and trying to make it easier to Windows admins to work with Linux on Azure. At least that's what seems to be the reason for Powershell on Linux, not for 'native' Linux users.

---

### Post by TheFu on 2016-09-05
PowerShell is not a terminal. Is it a shell, like ksh, sh, bash, tsch, zsh. Sorry to be pedantic.

If you use powershell on Windows and haven't used all the .NET extensions for dealing with files and directories and "libraries", then those scripts might be useful on a Linux system (probably not).

---

