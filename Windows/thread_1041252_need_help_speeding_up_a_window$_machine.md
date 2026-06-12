---
title: "need help speeding up a window$ machine"
date: 2009-01-16
forum: Windows
---

### Post by 900donuts on 2009-01-16
Heres the deal at my house there are 2 computers my computer, and the families windows machine. the it has 1Gb of ram and a 2.8ghz cpu its over 4 years olds, and IT IS SLOW!! I don't use it accept when I need a printer, but over the holidays it started showing unstable behavior (I don't remember every thing it did but one of the things is that it lost the wall paper)

about a week ago me and my dad removed a lot of its old software and ran a registry cleaning program which sped it up a little but it still takes over 8 minutes to boot up and around 20 seconds produce a right click menu (my computer does it practical instantaneously)

so I'm wondering if any one has any ideas as to how to speed it up some more

Thanks in advance :)

EDIT: OH! the windows pc runs xp

---

### Post by timcredible on 2009-01-16
ok, i'll resist the obvious answer of putting linux on it, and say reinstall windows.

---

### Post by cardinals_fan on 2009-01-16
Calling it window$ isn't a good way to ask for help.

Anyway, I would advise a clean install.  Something is very wrong if it takes that long with 1 gig of RAM; XP has always been fast for me with 512 MB.  Once it's installed, I recommend the following:

- Set up a [limited user account]("http://www.microsoft.com/windowsxp/using/setup/winxp/accounts.mspx#1")
- Install [suRun]("http://www.dedoimedo.com/computers/surun.html")
- Disable [extraneous services]("http://www.jasonn.com/turning_off_unnecessary_services_on_windows_xp") *cough*themes*cough*
- Install [Firefox]("http://www.mozilla.com/en-US/firefox/") with [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") and [WOT]("https://addons.mozilla.org/en-US/firefox/addon/3456")
- Install [ThreatFire]("http://www.threatfire.com/")
- Set up [Windows Firewall]("http://www.microsoft.com/windowsxp/using/security/internet/sp2_wfintro.mspx")
- Educate, educate, educate.  Make sure everyone in the family understands basic security and the tools above
- Only install additional software when needed

---

### Post by OrangeCrate on 2009-01-16
> **900donuts said:**
> Heres the deal at my house there are 2 computers my computer, and the families windows machine. the it has 1Gb of ram and a 2.8ghz cpu its over 4 years olds, and IT IS SLOW!! I don't use it accept when I need a printer, but over the holidays it started showing unstable behavior (I don't remember every thing it did but one of the things is that it lost the wall paper)

about a week ago me and my dad removed a lot of its old software and ran a registry cleaning program which sped it up a little but it still takes over 8 minutes to boot up and around 20 seconds produce a right click menu (my computer does it practical instantaneously)

so I'm wondering if any one has any ideas as to how to speed it up some more

Thanks in advance :)

EDIT: OH! the windows pc runs xp

1.) Run Trend Micro's Housecall to initially clean the computer of potential viruses and other malware:

[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

2.) You fail to mention if you have an antivirus program installed, and whether you have a firewall enabled. If not, the free versions of avast!, and ZoneAlarm would suffice.

3.) For active protection, download and enable Windows Defender from Microsoft.

4.) For passive protection, download and install SpywareBlaster.

5.) For an on demand malware scanner, install one or both of Spybot Search and Destroy, or the free version of Ad-Aware.

6.) Defrag the hard drive (System Tools).

Once you have everything cleaned up, your computer should run much quicker, unless the "registry cleaner" your father used borked the XP install. Registry cleaners can be problematic, and generally aren't needed. XP manages the registry quite well, without outside interference.

---

### Post by 900donuts on 2009-01-16
> ok, i'll resist the obvious answer of putting linux on it, and say reinstall windows. 

my father doesn't want to do that until he has an external hard drive to back up everything with (which isn't going to happen any time soon)

> Calling it window$ isn't a good way to ask for help.
sorry

> 1.) Run Trend Micro's Housecall to initially clean the computer of potential viruses and other malware:

[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

2.) You fail to mention if you have an antivirus program installed, and whether you have a firewall enabled. If not, the free versions of avast!, and ZoneAlarm would suffice.

3.) For active protection, download and enable Windows Defender from Microsoft.

4.) For passive protection, download and install SpywareBlaster.

5.) For an on demand malware scanner, install one or both of Spybot Search and Destroy, or the free version of Ad-Aware.

6.) Defrag the hard drive (System Tools).

it has norton anti-virus installed and my father refuses to remove it until the service runs out

we do have spy bot and I'll suggest the other ones to my father (since this should be his problem)

---

### Post by NoSmokingBandit on 2009-01-16
> **900donuts said:**
> 
it has norton anti-virus installed

The cause of your problem. Norton is the worst at sucking up resources and making your computer incredibly slow.

---

### Post by cardinals_fan on 2009-01-16
> **900donuts said:**
> 
sorry
No problem.  I just find such terms rather annoying.  All operating systems have their pros and cons.
> **900donuts said:**
> 
it has norton anti-virus installed and my father refuses to remove it until the service runs out
Purge it.  Norton is the worst of a defective line of products.
> **900donuts said:**
> 
we do have spy bot and I'll suggest the other ones to my father (since this should be his problem)
I don't recommend signature-based AVs *for daily use*.  They are quite useful for cleansing a contaminated system, but they do very little to prevent infections.

Use ThreatFire or NOD32 for the AV, NoScript and WOT in Firefox, and a firewall (I just use Windows Firewall, but Zonealarm is more thorough).  I linked to all of these above.  More important than any of these, however, is a limited user account *and the mindset that accompanies it*.  Your father needs to think carefully about his computer use and use common sense, or his machine will get clogged again.

---

### Post by skern03 on 2009-01-16
> **900donuts said:**
> 
it has norton anti-virus installed and my father refuses to remove it until the service runs out


I've used Norton for years, and it does have it's flaws, and has gradually been getting worse as far as performance goes. HOWEVER, it's optimized for systems more powerful than yours, so you don't need to throw the baby out with the bathwater.

Spybot is a likely contributor as well. I run it on my XP instance on this system also.

When your system boots up, turn on Task Manager, and click the CPU column so you can see what chews up resources.  My bet is you'll see a couple of Norton tasks hogging the resources (like LUCOMM somethingorother), then TeaTimer from Spybot. 

If that's the case, the Norton tasks can be remediated - go online and open a chat for support. Tell them Norton is slowing things down. There's a Norton service they'll disable or modify that will HELP some. I didn't see this until Norton 360 version 2. They'll take over your computer (it's okay) and drive for a few minutes. You'll have to reboot once or twice.

For Spybot, turn off TeaTimer. It watches your system for changes to system files. It's a great idea - on a fast system. Even then, it chews up resources like crazy.

Next, go to My Computer, and right-click your drive. If you have Indexing turned on, TURN IT OFF. It is a system killer.

Also, check how much drive space you have available. If you're down to less than a few GB, delete a bunch of files, like Internet and Windows Temp files. If you have Norton 360 it will do SOME of this for you.

Check the swap file. If it's too small, then you'll see slow performance. It should be something like 2 times the amount of RAM you have, if I remember correctly. Usually, windows is set to manage it; you can manage it yourself and achieve better performance.

Also, in addition to defragging the drive, be sure to run CHKDSK. The easiest way to do this is to right click the drive in My Computer, then click the Tools tab, and click the Check this disk option or whatever it says (sorry, can't remember).

Unless you specifically need Windows apps, the person who said load Linux is right - it will load in less than 2 minutes. At least it does on my system (P4 3.0 ghz, 1.5 GB RAM, 40 GB Western Digital, 250 GB SATA).

> REMEMBER: A cardinal rule of fixes like this is DO ONE thing at a time. If something breaks, and you've made 10 changes, you'll never know what broke the system.

---

### Post by Frak on 2009-01-17
I'd recommend installing CCleaner and wiping out all the unnecessary startup entries, registry errors, conflicts, and maybe free up some RAM in the process.

---

