---
title: "Skipping XP SP3"
date: 2008-05-23
forum: Windows
---

### Post by Kernel Sanders on 2008-05-23
Is anyone else here skipping XP SP3?

SP2 got a lot of attention from MS, and really was quite a good update IMHO.

SP3 has been rushed, and is basically a collection of fixes from 2004, plus WGA and other spyware and some features backported from Vista. There has been many problems, not least of which is system instability.

I don't really trust MS, and I don't want to add spyware and instability to a currently excellent XP SP2 install I have here. So I will be ignoring XP SP3 entirelly.

Thoughts?

---

### Post by LaRoza on 2008-05-23
> **Kernel Sanders said:**
> Is anyone else here skipping XP SP3?

SP2 got a lot of attention from MS, and really was quite a good update IMHO.

SP3 has been rushed, and is basically a collection of fixes from 2004, plus WGA and other spyware and some features backported from Vista. There has been many problems, not least of which is system instability.

I don't really trust MS, and I don't want to add spyware and instability to a currently excellent XP SP2 install I have here. So I will be ignoring XP SP3 entirelly.

Thoughts?

I don't use XP, but I don't see a reason why people should use SP3 if everything works to their satisfaction.

---

### Post by hellion0 on 2008-05-23
> **LaRoza said:**
> I don't use XP, but I don't see a reason why people should use SP3 if everything works to their satisfaction.Exactly the reason I'm not going to use SP3. It just works at the moment... why fix it if it ain't broke?

---

### Post by smoker on 2008-05-23
i've installed it on quite a few computers this week, and had no problems, though i've heard some amd pcs will continually restart!

i'd rather do that and sort out any problems before a sale, than have a customer bring a pc back a week later when/if sp3 borks their system.

personally i don't use xp, so don't give a toss about the spyware:-)

---

### Post by Paqman on 2008-05-23
I had a catastrophic fail with the RC, took down my whole Windows installation. Since then i've installed the final version and had absolutely no problems, the system is just as rock-solid as ever. 

Turns out the speed increase some people were talking about is only limited to certain versions of MS Office, though. General benchmarks show no improvement.

---

### Post by sayakb on 2008-05-23
Just as I didn't go for Vista SP1 on my sister's laptop. It's a Dell Inspiron 1520 with a 512MB GPU, but it got awfully slow when I installed SP1. So I just did another clean install for Vista and skipped SP1. Looks like MS is getting into practice of releasing useless service packs..!

---

### Post by myusername on 2008-05-23
i haven't seen one problem with sp3 on my system it works without fail

---

### Post by ch_123 on 2008-05-23
Been running it here since they released it on Windows Update. Ive had no problems, and the flipside, it doesnt really do much more. Still, best to be up to date with all the security bugs.

---

### Post by macstl on 2008-05-24
A friend of mine at work installed sp3 and his norton security didnt work . He uninstalled norton and it would'nt let him reinstall it.  He then unintalled sp3 and reinstalled norton ok and everything is ok.
I read where sp3 does not add much of anything to mention of importance.

---

### Post by sayakb on 2008-05-24
I read somewhere that SP3 restricts the installation of certain 3rd party Antiviruses.. Looks like MS "thinks" that SP3 would somehow make Windows less vulnerable to virus threats.. ;)

---

### Post by r76 on 2008-05-24
There are a few threads started here about XP SP3.  Some people are skipping it, others have had problems, and others are enjoying it.  Some issues are documented, for example ["HP begs AMD PC owners to put XP SP3 on ice"]("http://www.theregister.co.uk/2008/05/16/hp_xp_sp3_amd/") in *The Register*.  Understandably, some people here will be considering it but unsure, so I thought I'd share my experience :)

I didn't skip XP SP3, but did run into one (albeit easily solved from the command line) problem.  After the update, when I went to Microsoft Update (or Windows Update), I could select updates and they would be downloaded but not installed (get a "installation failed" message for each update).  A google search led me to [this page]("http://support.microsoft.com/kb/943144") on the Microsoft website.

Although the page describes recovery from a repair using the Windows CD, it worked for me following the SP3 upgrade.

I followed the first method
> Method 1: Register the Wups2.dll file in Windows
To register the Wups2.dll file in Windows, follow these steps:1.	Stop the Automatic Updates service. To do this, follow these steps:	a. 	Click Start, click Run, type cmd, and then click OK.
b. 	At the command prompt, type the following command, and then press ENTER:
net stop wuauserv

2.	Register the Wups2.dll file. To do this, follow these steps:	a. 	At the command prompt, type the following command, and then press ENTER:
regsvr32 %windir%\system32\wups2.dll
Note For a computer that is running Windows XP Professional x64 Edition, type the following command, and then press ENTER:
regsvr32 %windir%\syswow64\wups2.dll 
b. 	Click OK on each verification message that you receive.

3.	Start the Automatic Updates service. To do this, type the following command at the command prompt, and then press ENTER:
net start wuauserv
4.	Exit the command prompt. To do this type exit, and then press ENTER.

Now all is well.  Hope this helps anyone else.

---

### Post by ardvark71 on 2008-05-25
> **Kernel Sanders said:**
> Is anyone else here skipping XP SP3?

SP2 got a lot of attention from MS, and really was quite a good update IMHO.

SP3 has been rushed, and is basically a collection of fixes from 2004, plus WGA and other spyware and some features backported from Vista. There has been many problems, not least of which is system instability.

I don't really trust MS, and I don't want to add spyware and instability to a currently excellent XP SP2 install I have here. So I will be ignoring XP SP3 entirelly.

Thoughts?

I had a look at the white paper from Microsoft, "Overview of Windows XP Service Pack 3," and I didn't see anything that I really needed, although a couple features looked handy. However, considering the reports I've been hearing about the problems SP3 is having on some systems, I think I'll pass. ;)

Best Regards...

---

### Post by Reshin on 2008-05-25
Updated it on my old pc(AMD Sempron 3100+, MSI K8N NEO3). It received the reboot issues, alright. Down to rebooting on non-sp3 platforms also, even linux. It seems BIOS was busted beyond repair with SP3. Mind you, it's been showing signs of misbehavior before but I think this one was the final nail.

---

### Post by Musky Melon on 2008-05-25
Isn't SP3 just a collection of patches, most of which you've already installed? What's the big deal? It's nice to be able to have all the patches consolidated.

---

### Post by MaxIBoy on 2008-05-26
> **LinuxIsInnovation said:**
> I read somewhere that SP3 restricts the installation of certain 3rd party Antiviruses.. Looks like MS "thinks" that SP3 would somehow make Windows less vulnerable to virus threats.. ;)
Hey, I think disabling Norton *does* make a system safer.

---

### Post by CrazyArcher on 2008-05-28
> **MaxIBoy said:**
> Hey, I think disabling Norton *does* make a system safer.

Hehe, that's probably true. :)

I've got SP3, having Sempron 2200 CPU. No change for the worse. No percievable change for the better either, at the other hand.

---

