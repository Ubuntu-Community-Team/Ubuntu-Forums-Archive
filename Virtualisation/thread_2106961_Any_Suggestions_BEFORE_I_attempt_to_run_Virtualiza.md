---
title: "Any Suggestions BEFORE I attempt to run Virtualization?"
date: 2013-01-20
forum: Virtualisation
---

### Post by Fungus on 2013-01-20
Before I try virtualization, are there _any tips or suggestions_ that may keep me out of trouble and avoid some heartaches?

I've been using Ubuntu on and off for a couple of years, but I consider myself pretty much a newbie.  I can cut/paste commands into terminal, and I am learning the command line commands.

I am considering running Vista Home Premium 32 bit as guest for my 64 bit Xubuntu 12.04.  My hardware is a Fujitsu Lifebook A6120 laptop. Core2 duo processor running at 2 GHz, with 3 GB of ram and 500 GB hard disk. I dual boot Xubuntu or Vista.  A third partition is the largest and is NTFS which I use to read/write data accessible to both OS's. Can I read/write to this drive when running Vista in virtualization?

I would like to be able to run Ninja Trader, which is a Microsoft .NET application, as well as Webex for attending webinars.  Webex requires 32 bit browser and 32 bit Java, and works fine for me if reboot into Vista - which is what I am trying to avoid.  (I tried but failed to run Webex with the trick to install 32bit Swiftfox browser and 32bit Java, so now I am thinking to try virtualization.)  Both these applications require internet connections, so I understand virtualization will need some way of connecting to my wireless network, through the host's connection?

I am leaning towards using VirtualBox since it seems to have good clear, simple documentation and tutorials -- but I am open to other suggestions, even Wine.

 Does what I propose sound feasible?  Any tips/suggestions/warnings would really be appreciated!

---

### Post by sanderj on 2013-01-20
Running VirtualBox is really easy and straightforward. So just start it, create a new virtual machine, install Window Vista in it, and run it.

That's it.

---

### Post by Habitual on 2013-01-20
Hey So.Cal:

WebEx in Linux is horrific.
Virtualbox for WebEx is what I do.

Specify Bridged Adapter on the Guest 
for Host OS' internet connection...

DagoMob!

---

### Post by andrew.46 on 2013-01-21
> **Fungus said:**
> Before I try virtualization, are there _any tips or suggestions_ that may keep me out of trouble and avoid some heartaches?

Make sure you have plenty of ram to share with your guest OS.

---

### Post by sanderj on 2013-01-21
> **andrew.46 said:**
> Make sure you have plenty of ram to share with your guest OS.

The OP has "3 GB of ram", so giving 1 - 1.5 GB to Vista should do.

---

### Post by archery on 2013-01-21
Considering your experience, Virtualbox should be quite straightforward to set up. The instructions on their website are excellent. In answer to your question, you can share folders between virtual machines, you'll need to install guest additions after setting Virtualbox up.

If you have the funds and to make for the most pleasant experience, I'd: 

1) Max out the RAM on your laptop
2) Avoid Vista and use Windows 7, better performance and less of a resource hog

Also check if your CPU supports hardware virtalisation, use the following in a terminal:

```
cat /proc/cpuinfo
```

Look for 'vmx' in the flags section, most core 2 duos support VT-x.

Actually, if your dual booting now, install Virtualbox and try it out, if your not happy with the performance, see above.

---

### Post by coldraven on 2013-01-21
Two tips!
In Virtual Box add comments to your VM if you make major changes then take a "snapshot" so you can revert back to a previous state.

Once you get a VM running how you want you can do an "export" to an external drive as a backup. 
If it all goes wrong* you can always "import" your lovely VM in all it's glory :)
*for example,when Windows becomes a virus infested mess!

---

### Post by Paddy Landau on 2013-01-22
> **archery said:**
> 1) Max out the RAM on your laptop
+1. Based on my personal experience, 3Gb to share with Vista is likely to give you a disappointing performance. I would recommend at least 2Gb for Vista and, depending on what you do in Ubuntu, 2-3Gb for Ubuntu. Even more RAM would be strongly advisable. If you can additionally upgrade from Vista to 7, you'll probably enjoy the experience further.

---

### Post by andrew.46 on 2013-01-23
Running 16gig here solely to facilitate multiple vms...

---

### Post by Fungus on 2013-01-29
Thanks for all the replies, folks!

1) I don't think my cpu supports hw virtualization. My procinfo flags are: 

"flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm" 

I don't think the vme flag will help there.

2) Anyway, I ordered a 2 GB ram module to replace the 1 GB in the machine, which will bring it up to 4 GB, so that may help.

3) I know Vista is not a preferred guest, I'll try to do a minimal install with least amount of bells and whistles.  I really don't want to go buy a windows 7 upgrade for this 4.5 year old laptop.

However, I think I have the old Win XP discs from my previous laptop, a Compaq from 2003.  I could try that if Vista is too slow?

4) Whatever Windows version I use, will I need to to all the updates/service packs?  just once, right?   

5) Also, would I need to or should I install anti-virus, firewall, and anti-malware on the windows VM?

---

### Post by Paddy Landau on 2013-01-30
> **Fungus said:**
> 1) I don't think my cpu supports hw virtualization.
I don't know, but you can find out easily. Run VirtualBox, create a VM, and start to run it (even if there's nothing to run). If it starts, you can virtualize.

However, if this is an old computer, I would seriously consider dual-booting instead of using a VM. The systems will run much faster.

> **Fungus said:**
> 2) Anyway, I ordered a 2 GB ram module to replace the 1 GB in the machine, which will bring it up to 4 GB, so that may help.
If you dual-boot, that will give you nice fast system.

> **Fungus said:**
> However, I think I have the old Win XP discs from my previous laptop, a Compaq from 2003.  I could try that if Vista is too slow?
You certainly could. XP would run very fast on 4Gb. Many people prefer XP to Vista, but the problem is that XP will not be supported much longer, so Vista is probably a better idea.

> **Fungus said:**
> 4) Whatever Windows version I use, will I need to to all the updates/service packs?  just once, right?
Yes. Just do the usual updates. If you have broadband, it will take you an entire day :( (Microsoft's "clever" idea to do updates in many stages). Without broadband, it will take even longer.

> **Fungus said:**
> 5) Also, would I need to or should I install anti-virus, firewall, and anti-malware on the windows VM?
Yes, indeed. I would simply go with the standard Microsoft Security Essentials, which works well and fast; it includes the firewall and anti-malware. You could go for other proprietary systems if you prefer, but I have found Security Essentials to do the job.

If you are running behind a router, that will give you extra protection.

If you decide to use a VM instead of dual-boot, once your Windows VM is set up to your satisfaction, snapshot it. That will allow you to regress quickly should it become infected.

---

### Post by NobleYorkshire on 2013-02-02
> **andrew.46 said:**
> Running 16gig here solely to facilitate multiple vms...

Haha how many VM's do you run?

---

### Post by andrew.46 on 2013-02-02
Actually after a recent cleanup perhaps not so many :). I attach a screenshot...

---

