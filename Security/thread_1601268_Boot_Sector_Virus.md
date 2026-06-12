---
title: "Boot Sector Virus?"
date: 2010-10-20
forum: Security
---

### Post by jsvidyad on 2010-10-20
Hello,

   I run 64 bit ubuntu 9.10 . I recently rebooted my computer with a flash drive plugged into a USB port. My question is, could I have got a boot sector virus because of this? what are the symptoms of a boot sector infection? After the incident, I scanned the flash drive with clamav and it didn't detect any viruses. Also, in the BIOS, the hard drive is higher up in the boot sequence than USB mass storage drives. These two things suggest to me that a boot sector virus is improbable.

    But, recently, when I tried to boot into ubuntu, I got an error message saying that /dev/disk/uuid<some characters here> didn't exist. Is this a symptom of a boot sector virus? So, I ended up re-installing ubuntu and I believe grub was written to the MBR. Will this have erased any boot sector viruses that were on my system?

  Can a boot-sector virus affect linux too? How can I check to see if I have a boot-sector infection? I also have windows xp on my computer. For some reason, windows xp isn't letting me install any updates, but this has been going on for since before the above incident with the flash drive and therefore I don't think that is due to a boot sector virus.

---

### Post by jsvidyad on 2010-10-20
Can a virus scan of the flash drive detect if there is a boot sector virus on it?? Can a boot sector virus be spread from a USB flash drive?? Or are floppies the only vector?

---

### Post by OpSecShellshock on 2010-10-20
Actually, MBR-infecting malware can be installed from the web on Windows systems with little user interaction under poorly-secured conditions. And there are vectors that involve removable storage media, but they also only affect Windows.

However, I don't believe that's what's causing the error that you were getting, and reinstalling made that error go away, so there's nothing to worry about on that side of things. Not being able to update Windows is a pretty big problem, though.

The best way to detect a corrupted boot sector is to compare the most recent known-good version against the current version. Even if you had that information to hand it's fairly tedious to do, and way more difficult than just wiping out the disk and reinstalling the OS. Some AV software might be able to do it, but it's important to understand that the AV software loads after the initial boot--so if the MBR has been corrupted by something designed to hide itself from the Windows API, it will also be invisible to the AV software. Or it could be designed to run entirely in memory with nothing left on disk.

Basically, my advice is to wipe the hard drive and reinstall both operating systems, and restore needed files from backups (after applying all system updates).

---

### Post by jsvidyad on 2010-10-21
Today, after booting into the administrative account, connecting to a wireless network and starting firestarter, firestarter showed that there were 4 active connections over http. One of these was from the program wget. Now, why would wget want to run at the start of a network connection. Could this be symptomatic of a boot sector virus? Also, I just heard about a BIOS virus. How can I detect these viruses?

---

### Post by uRock on 2010-10-21
[s]wget checks for updates.[/s]

If you have a BIOS flash, then you need to download and flash the BIOS with the proper vendor code. If you don't know for sure how to flash your BIOS, then I highly recommend taking your system to a shop. If the flashing of BIOS is not done right, then the chip or motherboard will have to be replaced. **I highly doubt you have a BIOS virus.**

---

### Post by jsvidyad on 2010-10-21
You mean wget checks for updates to ubuntu? 

Also, if I flash the BIOS, will it  destroy all BIOS viruses? What are the symptoms of BIOS/Boot-Sector viruses? Like I mentioned earlier, windows is mot letting me update windows and so I suspect I have a worm. So, if I flash the BIOS, I might unwittingly infect it.

Is there a way to scan for BIOS/boot-sector viruses?

If there is an infection, it must have come from booting with my flash drive plugged in. Is there some way to scan the boot sector of the flash drive? I scanned the partition on the flash drive and did not detect any viruses. But, I guess that doesn't scan the boot-sector.

The only symptom I see is that the ubuntu system seems a bit slow when switching workspaces. I could be just imagining it. I am worried that someone could be stealing information on my ubuntu OS by having a malware in my BIOS/boot-sector

---

### Post by FuturePilot on 2010-10-21
> **uRock said:**
> wget checks for updates.

Apt does not use wget in any way.

---

### Post by WinstonChurchill on 2010-10-22
> **jsvidyad said:**
> Today, after booting into the administrative account, connecting to a wireless network and starting firestarter, firestarter showed that there were 4 active connections over http. One of these was from the program wget. Now, why would wget want to run at the start of a network connection. Could this be symptomatic of a boot sector virus? Also, I just heard about a BIOS virus. How can I detect these viruses?
Run the following command:
```
sudo netstat -tep --numeric-hosts --numeric-ports
```You'll end up with some output like this:
```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 10.254.254.2:52727      74.125.157.109:993      ESTABLISHED username   16590       2353/evolution  
tcp        0      0 10.254.254.2:55052      74.125.227.6:80         ESTABLISHED username   76346       2260/firefox-bin

```Then, to find out who your system is talking to, do reverse DNS lookups on those IP's like so:
```
host x.x.x.x
```In my case, I get:
```

109.157.125.74.in-addr.arpa domain name pointer gy-in-f109.1e100.net.
Host 6.227.125.74.in-addr.arpa. not found: 3(NXDOMAIN)

```If you get an NXDOMAIN, or if the hostname isn't very descriptive (like the two above), do a whois search:
**EDIT:** You'll probably have to run 'sudo apt-get install whois' - I believe it isn't installed by default.
```

user@host:~$ whois 74.125.227.6
NetRange:       74.125.0.0 - 74.125.255.255
CIDR:           74.125.0.0/16
OriginAS:       
NetName:        GOOGLE
NetHandle:      NET-74-125-0-0-1
Parent:         NET-74-0-0-0-0
NetType:        Direct Allocation
NameServer:     NS2.GOOGLE.COM
NameServer:     NS3.GOOGLE.COM
NameServer:     NS4.GOOGLE.COM
NameServer:     NS1.GOOGLE.COM
RegDate:        2007-03-13
Updated:        2007-05-22
Ref:            http://whois.arin.net/rest/net/NET-74-125-0-0-1


OrgName:        Google Inc.
OrgId:          GOGL
Address:        1600 Amphitheatre Parkway
City:           Mountain View
StateProv:      CA
PostalCode:     94043
Country:        US
RegDate:        2000-03-30
Updated:        2009-08-07
Ref:            http://whois.arin.net/rest/org/GOGL

OrgTechHandle: ZG39-ARIN
OrgTechName:   Google Inc
OrgTechPhone:  +1-650-253-0000 
OrgTechEmail:  arin-contact@google.com
OrgTechRef:    http://whois.arin.net/rest/poc/ZG39-ARIN

```As we can clearly see, both IP's belong to Google, and thus are not something we need to worry about. Do the same with your's - I bet it's something harmless.

---

### Post by AoSteve on 2010-10-22
Honestly; after reviewing the thread here..   I think you may want to run *sudo apt-get update-grub*

>  /dev/disk/uuid<some characters here>


Sounds like the default grub2 error message when an option is set to an incorrect partition...    

/dev/sda1 or similar.


> Also, if I flash the BIOS, will it  destroy all BIOS viruses?

I'll state this once..  if you do not know what you're doing with flashing the BIOS, don't even imagine about doing it.   It can result in a completely dead motherboard if done correctly.   A BIOS is a basic input/output system..   You're not going to get a virus there without extremely low level input into it.   Not to mention the extremely limited space on the BIOS rom is so small; most malicious software wouldn't imagine fitting there.    


I'd try a sudo update-grub and see if it fixes the boot problem.  It sounds like a simple grub issue.

I really hope this helps and the network connections...   I boot up with over 120 reported TCP/UDP connections through my lan port on my router.  So don't be too worried about 4.  :)

---

### Post by AoSteve on 2010-10-22
> **jsvidyad said:**
> You mean wget checks for updates to ubuntu? 

Also, if I flash the BIOS, will it  destroy all BIOS viruses? What are the symptoms of BIOS/Boot-Sector viruses? Like I mentioned earlier, windows is mot letting me update windows and so I suspect I have a worm. So, if I flash the BIOS, I might unwittingly infect it.

Is there a way to scan for BIOS/boot-sector viruses?

If there is an infection, it must have come from booting with my flash drive plugged in. Is there some way to scan the boot sector of the flash drive? I scanned the partition on the flash drive and did not detect any viruses. But, I guess that doesn't scan the boot-sector.

The only symptom I see is that the ubuntu system seems a bit slow when switching workspaces. I could be just imagining it. I am worried that someone could be stealing information on my ubuntu OS by having a malware in my BIOS/boot-sector\

99% of AV software will first check the MBR(boot sectors) for virus's before even thinking of scanning files....    Read my previous post about the BIOS.   There are very few desktop boards that provide any write access to the BIOS rom on the motherboard.   Actually, 99% of motherboards I've worked with doing BIOS flashing or the like have to use MS-Dos 5.0 or greater boot disks to gain the required access.  (There's literally a GIANT lack of security in an operating system that is nearly 20 years old).

---

### Post by OpSecShellshock on 2010-10-22
It makes very little sense to worry about things like flashing the BIOS and tracking all connections initiated during an Ubuntu session if you haven't tried reinstalling Windows yet. Not being able to update Windows presents a far higher actual risk in terms of regular usage. As long as the Windows copy is licensed and still a supported version (which means XP service pack 3 and up) there should not be any barriers to updating.

With regard to Ubuntu sessions, slow performance is usually related to hardware in some way.

---

### Post by Chayak on 2010-10-22
Anti-virus doesn't detect everything.  I do malware research for a living and I've got a few gigs of samples right now that are not detected.

I have yet to see a boot sector virus that affects linux.

The lab I work in runs on Redhat(on the server side) and Ubuntu(workstations) for good reason.  We run all of our windows enviornments in virutal machines and a few bare metal machines should a sample be VM aware.  We play with the cutting edge of malware and we've yet to have a workstation compromised.  There's realtime monitoring on our network traffic so if anything does try to call home we'd see it.

---

### Post by jsvidyad on 2010-10-22
I am not  saying that I might have got a boot-sector virus through linux. I am afraid that I might have got it by rebooting the computer with the flash drive in the USB port. Also, since my windows OS is behaving strangely, that's also a security issue.

  Assuming I have a boot-sector virus, can I get rid of it by over-writing my hard-drive with DBAN? I am anyway planning to re-install both ubuntu and windows. Is it more secure to run windows as a virtual guest in ubuntu rather than running it in a dual-boot situation with ubuntu?

---

### Post by Chayak on 2010-10-22
> **jsvidyad said:**
> I am not  saying that I might have got a boot-sector virus through linux. I am afraid that I might have got it by rebooting the computer with the flash drive in the USB port. Also, since my windows OS is behaving strangely, that's also a security issue.

  Assuming I have a boot-sector virus, can I get rid of it by over-writing my hard-drive with DBAN? I am anyway planning to re-install both ubuntu and windows. Is it more secure to run windows as a virtual guest in ubuntu rather than running it in a dual-boot situation with ubuntu?

If your hard drive has boot priority then having a flash drive plugged in wouldn't do anything.

Careful with this but if you did have a boot sector virus this would overwrite it
```

_**This will make your computer unbootable, don't restart or shut down until you reinstall GRUB**_
dd if=/dev/zero of=/dev/<drive> bs=512 count=1
<drive> being sda, etc
```

Then [Reinstall GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") 

If you're wiping the drive to reinstall then don't worry about reinstalling GRUB.  You can boot off the live CD and then run this to clear your drive
```
dd if=/dev/urandom of=/dev/<drive>
```
That will scrub your drive

---

### Post by WinstonChurchill on 2010-10-22
> **Chayak said:**
> 
```

dd if=/dev/zero of=/dev/<drive> bs=512 count=1
<drive> being sda, etc
```Then [Reinstall GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") 

Uh... that will overwrite the entire MBR, including the partition table, which effectively erases all the data on the drive. I think you meant to type:
```
dd if=/dev/zero of=/dev/<drive> bs=440 count=1
```

---

### Post by jsvidyad on 2010-10-22
I am going to install newer versions of both ubuntu and windows. So, I might just as well overwrite the entire hard drive. 

Is it more secure to run windows as a virtual guest under ubuntu rather than as part of a dual-boot system?

 Also, I am planning to flash my BIOS to a newer version. Just so that I can get rid of BIOS viruses if any. I know I am being a bit paranoid. Does anyone have any suggestions regarding this?

---

### Post by Chayak on 2010-10-22
If you don't play any games then yes, virtualizing windows is better.  I use VMware workstation but you can just as easily use VirtualBox.  If something happens to the systems then you can revert it to a clean snapshot.

---

### Post by Chayak on 2010-10-22
> **WinstonChurchill said:**
> Uh... that will overwrite the entire MBR, including the partition table, which effectively erases all the data on the drive. I think you meant to type:
```
dd if=/dev/zero of=/dev/<drive> bs=440 count=1
```

Thanks for the correction. I copied it out of some notes.

---

### Post by nitrogensixteen on 2010-10-23
I think that's a bunch of FUD about the dead motherboard.

If you corrupt a BIOS that is soldered to your motherboard, sure it will be a pain to remove it, but if it is socketed, as all that i have seen are, you can just boot the flash utility on a computer with the same socket and hot-swap the bios chips and flash it.

---

### Post by mainerror on 2010-10-23
> **AoSteve said:**
> ... It can result in a completely dead motherboard if done correctly.

I think you meant if done **in**correctly. :D

> **jsvidyad said:**
> Also, I am planning to flash my BIOS to a newer version. Just so that I can get rid of BIOS viruses if any. I know I am being a bit paranoid. Does anyone have any suggestions regarding this?

Yes I have a suggestion. Don't do it unless you have a technical issue with the current BIOS version.

> **nitrogensixteen said:**
> I think that's a bunch of FUD about the dead motherboard.

If you corrupt a BIOS that is soldered to your motherboard, sure it will be a pain to remove it, but if it is socketed, as all that i have seen are, you can just boot the flash utility on a computer with the same socket and hot-swap the bios chips and flash it.

I can't even remember when I've seen a motherboard with socketed BIOS last time so I wouldn't count on that when advising someone to flash it. What I mean is that soldered chips are generally more common due to costs.

---

### Post by jsvidyad on 2010-10-23
> **mainerror said:**
> I think you meant if done **in**correctly. :D



Yes I have a suggestion. Don't do it unless you have a technical issue with the current BIOS version.


I can't even remember when I've seen a motherboard with socketed BIOS last time so I wouldn't count on that when advising someone to flash it. What I mean is that soldered chips are generally more common due to costs.

I don't have a technical issue with the BIOS. I am just worried that I might have a BIOS virus. That's why I thought I'd flash the BIOS with a newer version. Do you see any symptoms if there is a  BIOS virus? I saw some suspicious connections on my firewall as I mentioned earlier in this thread.

---

### Post by willblock on 2010-10-23
First, Hi all, I know this is my first post but please be gentle.

I may be able to offer some help, as I have spent the last 2 weeks, ridding my local network of a particular rootkit.

@jsvidyad  Would you have an award bios or a custom HP bios by anychance?

There is most definately a bootkit alive and well, that affects these two at least. I have Bios dumps to prove it.

However the infection I have been researching needs to be pretty advanced, I.e remote user installs extra programs on an already infected machine, slowly building up the amount of usable xploits to do so.

Have you checked your Hard drive for the presence of hidden partitions?  I have an infection that hides a copy of the user files (c:/documents and settings etc etc of all users in a hidden partition, then symbolic links to the copy when accessed, (causing any data hidden in the normal drive file to be undetected by read/write.(It even hijacked windows recovery hidden partition on windows 7 install)
As far as I can tell the service it uses to hide these is truecrypt or a modified version, and is installed by the bios infection/bypass and can detect the os, and auto run the correct win32/64 or linux 32 version of the driver.

If you are logging connections, sites like pastebin  and addthis.cdn  even some javascript from well known sites. Will show.

Ring any bells?

---

### Post by jsvidyad on 2010-10-25
I have a DELL BIOS. How did you get rid of that BIOS virus? Gnome Partition editor does not show any hidden partitions. Unfortunately I just saw some suspicious connections on my firewall briefly. They disappeared before I could note down the IP addresses.

  What symptoms did you see on your computer due to that BIOS virus?

BTW, I have a linux64 system. Can it be infected too?

---

### Post by mainerror on 2010-10-25
> **jsvidyad said:**
> I have a DELL BIOS. How did you get rid of that BIOS virus? Gnome Partition editor does not show any hidden partitions. Unfortunately I just saw some suspicious connections on my firewall briefly. They disappeared before I could note down the IP addresses.

  What symptoms did you see on your computer due to that BIOS virus?

BTW, I have a linux64 system. Can it be infected too?

You should really calm down. There is no sign of any virus really. You've seen some connections on your firewall you couldn't even investigate on. My recommendation, monitor your firewall and try to track the connections. Only then you can really tell that something nasty is going on. Your fear is totally out of proportions.

---

### Post by nevius on 2010-10-25
> **mainerror said:**
> You should really calm down. There is no sign of any virus really. You've seen some connections on your firewall you couldn't even investigate on. My recommendation, monitor your firewall and try to track the connections. Only then you can really tell that something nasty is going on. Your fear is totally out of proportions.

+1

Think Melman in Madagascar. There is almost certainly nothing wrong with your BIOS or the boot sector of your hard drive. Read the security sticky. Research your problems. When you have problems don't assume its malware.

---

### Post by jsvidyad on 2010-11-23
Hello,

  I ran the command "sudo dd if=/dev/urandom of=/dev/sda" on my computer. That overwrites the entire drive with random characters, right? So, if there were any boot sector viruses, would it erase them too?

---

### Post by jsvidyad on 2010-11-23
Is running the above command just as good as a low level format?? Is there any difference?

---

### Post by cariboo on 2010-11-23
There is no such thing as a low level format, writing all zeros to the drive is what the manufacturers utilities do.

For more information on dd open a terminal and type:

```
info coreutils 'dd invocation'
```

---

### Post by jsvidyad on 2010-11-24
I already ran the command "sudo dd if=/dev/urandom of=/dev/sda". Will this erase boot sector viruses in the drive /dev/sda, if any?

    Thank you in advance for your help.

---

### Post by cariboo on 2010-11-24
This has probably been asked before, but what makes you think you have a boot sector virus?

Have you actually used a boot sector editor to see if there is anything there?

---

### Post by jsvidyad on 2010-11-24
I have a dual boot system and the windows xp OS wouldn't let me upgrade it. I read that it was a symptom of a worm named conficker. But, when I scanned for viruses, none were detected. I also saw some suspicious http connections at login on my ubuntu firewall. Since both OSes seemed to be affected I assumed I had a boot-sector virus and decided to re-install both OSes from scratch.
    In this thread an earlier poster had told me that the command "sudo dd if=/dev/urandom of=/dev/sda" would overwrite the entire drive and would hence also wipe out any boot-sector viruses. I have already run that command from my ubuntu LiveCD. Before re-installing the OSes and booting off that hard drive, I just wanted to make sure that the earlier command would indeed overwrite the boot sector of the drive also and thus get rid of any boot-sector viruses.

Can someone who knows this please confirm if this is correct or not?

---

### Post by jsvidyad on 2010-11-24
Can someone help me with this?

---

### Post by WeAreLinux on 2010-11-24
> **jsvidyad said:**
> I just wanted to make sure that the earlier command would indeed overwrite the boot sector of the drive also and thus get rid of any boot-sector viruses.

Can someone who knows this please confirm if this is correct or not?

Hi

Yes. The DD command you used, wipes the entire HD including the MBR (Master Boot Record).

I'm not 100% sure though. If I'm wrong, somebody will correct me.

You could've also used a program called Shred to wipe your HD. It's easier to use & is also included by default on the Live CD. See "man shred" for more details.

---

### Post by psusi on 2010-11-24
Just do a normal install where you choose to use the whole disk and save yourself a lot of time.

---

### Post by jsvidyad on 2010-11-28
Can someone please help me with this?

---

### Post by cariboo on 2010-11-28
When you install grub2 it over writes the mbr, just go ahead and install Ubuntu.

---

### Post by jsvidyad on 2010-11-28
Oh..OK. 

I also ran the command "sudo dd if=/dev/urandom of=/dev/sda". Does this write the entire drive with random characters? In that case, will it also overwrite the boot-sector and remove any boot-sector viruses?

   I am just curious to know.

Thank you for your help.

---

### Post by psusi on 2010-11-29
> **jsvidyad said:**
> Oh..OK. 

I also ran the command "sudo dd if=/dev/urandom of=/dev/sda". Does this write the entire drive with random characters? In that case, will it also overwrite the boot-sector and remove any boot-sector viruses?

   I am just curious to know.

Thank you for your help.

Yes, but it is a colossal waste of time compared to just reinstalling, which will also wipe the boot sector.

---

### Post by jsvidyad on 2010-11-30
Thanks for letting me know

---

