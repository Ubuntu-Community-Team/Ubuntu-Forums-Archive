---
title: "Wireshark reveals consistent packets being sent to 78.131.193.150.  How do I stop?"
date: 2008-11-08
forum: Security
---

### Post by kevdog on 2008-11-08
solved sorry

---

### Post by cariboo on 2008-11-08
You should post how you resolved the problem, or at least mark this thread solved.

Jim

---

### Post by kevdog on 2008-11-08
Well it actually revolved around my secondary windows xp installation -- and not specifically ubuntu so its not really applicable but I'll explain so maybe someone else with a mix of machines can benefit too

Ran wireshark
Noticed numerous packets being sent to 78.131.193.150.  I googled this address and also ran a nslookup.  Its some site in Poland.  I closed all open applications except wireshark and noticed packets continued to be sent.  Maybe if someone can tell me how to find the rogue application offering the packets I would be helpful.  Anyway I did the next best thing -- close outgoing communications to the particular ip address.

In order to do this:  Im running WinXP SP3.  I download the Service Pack 2 Service Tools offered by microsoft:
[http://www.microsoft.com/downloads/details.aspx?FamilyId=49AE8576-9BB9-4126-9761-BA8011FABF38&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=49AE8576-9BB9-4126-9761-BA8011FABF38&displaylang=en)

I then added a filter to block the outgoing packets:
cd c:\Program Files\Service Tools
ipseccmd -f [0=78.131.193.150:*:*]

Traffic instantly stopped!!!

Only problem is that using ipseccmd is a dynamic solution -- meaning basically that once the computer is rebooted -- I need to repeat the process.  For now I've added a .bat file to be run on startup, but it would be nice to find the rogue application if possible generating the traffic.  I'm not sure if this is going to be possible :(

---

### Post by Dr Small on 2008-11-08
Is there a netstat type program for Windows? I thought I remember seeing a screenshot with HymnToLife using it awhile back when Chrome was released.

---

### Post by kevdog on 2008-11-08
Yes there is definitely a netstat program, although the options are slightly different in windows than in linux.  I will investigate further and report back.

---

### Post by caljohnsmith on 2008-11-08
Kevdog, I think "[Cports]("http://www.nirsoft.net/utils/cports.html")" might be what you are looking for. Give that a shot and let me know how it goes. :)

---

### Post by persistentstubborn on 2008-11-08
> **kevdog said:**
> Maybe if someone can tell me how to find the rogue application offering the packets I would be helpful.

If I understand you well, and if that's a problem with XP, my guess is that you caught a kind of back orifice - encrypted application that made your box into a server. IP address of the site in Poland is probably spoofed, since it would basically be an encrypted sshd daemon running in you XP box.

If my guess is true, XP can't find it, since it is encrypted, and commanded to kernel to hide it from all other programs, incl. antivirus, antirootkit, etc. The only idea I get to locate it and remove is to take another box and run either ubuntu on it, or some kind of live xp distro, such as [ubcd4win](http://www.ubcd4win.com/), connect it to your box and scan your box from the other one. Clamav should do it fine from ubuntu. Once the ba$tard has been found, exterminate it. 

I don't know how much time it would take to you, or would it actually result in a success. But it must be run from another box, and the infected box ought to be up and running. You might even ask some of your friends, whom you trust, to scan you online.

The other cure, eventually following the clean up in any case, is to format your entire HDD (the ******* will be hiding in MBR) and to clear MBR by

```
dd if=dev/zero of=/dev/ENTIREHDD Bs=512 count=1
```

so all your MBR is cleared (along with all your data which should have been copied to another medium previously).

But, if that's b.o., even after the above process, it would hide himself in XP registry, lying on your processor, so is would be up again any time you install any kind of Micro$oft. To get rid of it permanently, you need to unplug any power from your box (incl. monitor and network cables) and to take off the battery from the motherboard for 30 minutes. Without static electricity, your processor will be cleared after 15 minutes (additional 15 minutes are "just in case").

If your motherboard doesn't allow battery to be taken out (there are some older pieces of hardware I've seen not allowing it), your choices are either to buy a new processor, or to forget about Micro$oft and run Linux only on that box (which isn't a bad choice after all).

Yet another alternative is to kindly ask the hacker to leave you alone.

---

### Post by Dr Small on 2008-11-08
> **persistentstubborn said:**
> Yet another alternative is to kindly ask the hacker to leave you alone.

That never works.

---

### Post by Chayak on 2008-11-08
> **kevdog said:**
> Well it actually revolved around my secondary windows xp installation -- and not specifically ubuntu so its not really applicable but I'll explain so maybe someone else with a mix of machines can benefit too

Ran wireshark
Noticed numerous packets being sent to 78.131.193.150.  I googled this address and also ran a nslookup.  Its some site in Poland.  I closed all open applications except wireshark and noticed packets continued to be sent.  Maybe if someone can tell me how to find the rogue application offering the packets I would be helpful.  Anyway I did the next best thing -- close outgoing communications to the particular ip address.

In order to do this:  Im running WinXP SP3.  I download the Service Pack 2 Service Tools offered by microsoft:
[http://www.microsoft.com/downloads/details.aspx?FamilyId=49AE8576-9BB9-4126-9761-BA8011FABF38&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=49AE8576-9BB9-4126-9761-BA8011FABF38&displaylang=en)

I then added a filter to block the outgoing packets:
cd c:\Program Files\Service Tools
ipseccmd -f [0=78.131.193.150:*:*]

Traffic instantly stopped!!!

Only problem is that using ipseccmd is a dynamic solution -- meaning basically that once the computer is rebooted -- I need to repeat the process.  For now I've added a .bat file to be run on startup, but it would be nice to find the rogue application if possible generating the traffic.  I'm not sure if this is going to be possible :(

It sounds like your windows install is botted.  Blocking the port doesn't solve the underlying issue that you have malware on that machine that's most likely logging what you do on it including keystrokes and sending it home when it can or waiting for commands.  You shouldn't trust the system at all and to be honest the best thing for you to do is wipe it and reinstall.

It's probably not black orifice, there's much more sophisticated tools out there now and countless variants.  It's a name people recognize but it's rare to see it any more.  Poison Ivy seems to be popular of late and there are all kinds of variations to keep from being detected by default AV signatures.

If you want to try and find the software download the Sysinternals suite from Microsoft and open up autoruns.exe

look for entries in ```
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```
That's where most malware likes to drop registry keys to make itself persistent.  *Nothing* has to be running in this for windows to run so if nothing jumps out as strange you can uncheck all of them.  You can also look at the image path and see if something is running from C:\windows or a subdirectory, malware tends to hide there most of the time.  That's not to say you haven't caught something better that has rootkited your system.  Then the only real way to find it is to run in safe mode or more preferred to boot up into a forensics environment.

Though regardless you should get anything valuable off that system and reload it.  I do malware research for a living and after I pull a sample I even reload boxes because things can be missed.

As for the run anti-virus argument.  It's trivial to repack or armor an executable so anti-virus won't detect it.  ClamAV is pretty much worthless as it has the lowest detection rates of anything I've seen.  It's a pity really but they don't have labs of paid experts working to make signatures.  The best at the moment is Kaspersky and Norton 2009's behavioral detection.  I've seen it catch about 90% of samples after they're run.

To reemphasize the point, *reload the system*, it can no longer be trusted.

---

### Post by persistentstubborn on 2008-11-09
> **Chayak said:**
> Then the only real way to find it is to run in safe mode or more preferred to boot up into a forensics environment.

You've already got my thanks for your excellent post above, but being a hog I am, I'll not miss a chance to ask a pro for some clarifications.

a) I think he needs to boot to runlevel 4 (I think) - XP safe mode with networking, if the rat is what we think - an encrypted remote administration tool; I don't think it would run in safe mode without networking.

b) I'd appreciate very much (and I bet I'll not be the only one), if you could emphasize a little bit "booting into forensic environment". A quick search of synaptic after the keyword "forensic" offered autopsy, sleuthkit, scalpel, rdd, unhide, vinetto, tct. Frankly, I can't imagine nothing better from copying the image of his infected HDD and analyzing it afterwards from a clean Linux box, but I've never done any forensic and my guess is that for the insight of what's happening he would be better to start from examining/scanning the infected box from other machine while the rat is still there running - that's how he would see all the processes running and will have better chances to determine what attacked him, so he would learn for sure how to fix it. Though, it would take more time.

BTW, I figured out the way how not to clear the entire HDD and still be safe, following in my next post.

---

### Post by persistentstubborn on 2008-11-09
Note - since compromised box can't be trusted, run everything preferrably from another machine; or from live a CD; or from existing uncompromised Ubuntu - what you described doesn't seem to have compromised your Ubunt, but that's what *seems* to us, miles away from the box.

In case your Linux and XP partitions lay on separate **primary** partitions, there is the way not to format your entire HDD, but only XP primary partition. In case you first installed XP, and did partitioning of your entire HDD from XP installer, and you installed Ubuntu afterwards on a logical partition by resizing XP partition, than, I'm affraid, the advice won't work for you.

Go to [ftp://ftp.openbsd.org/pub/OpenBSD/4.4](ftp://ftp.openbsd.org/pub/OpenBSD/4.4) , choose your architecture, download install floppy image and write it to a floppy drive (fdformat). You have more precise instructions [here](http://openbsd.org/faq/faq4.html#UnixFlop). Then start the install of OpenBSD from floppy, until you reach the program disklabel. It will show you your four primary partitions and posibility to format only those of them you choose, and that formatting include clearing MBR. Once you erased away your XP partition, Ctrl+C and you are out of the install. You have detailed instructions on their site.

That way, your Linux partition would remain intact.

There is yet another aspect that needs to be mentioned, namely, the possibility that the rat messed up with your BIOS (and that you cannot determine unless you do forensic, as kindly pointed by Chayak above (so thanks for him/her are appropriate). If you run some branded machine, or a laptop, they have system partitions preventing from meddling with BIOS. Or perhaps your BIOS settings prevents BIOS update, check it. In case of either, you are safe.

The only way I know how to determine for sure if BIOS had been messed up (mind, that's pure theory, I have no real experience in it), is to flush BIOS. Donwload new version from the manufacturer of your hardware, write the loppy, save your old bios on another medium, and flush existing one. In case it cannot execute flash, BIOS has been messed up. Drop the motherboard out to trash and buy a new one. In case the flash succeeded, it hasn't been messed up and you did your flash for nothing, except for making yourself sure you are safe.

---

### Post by Chayak on 2008-11-09
> **persistentstubborn said:**
> You've already got my thanks for your excellent post above, but being a hog I am, I'll not miss a chance to ask a pro for some clarifications.

a) I think he needs to boot to runlevel 4 (I think) - XP safe mode with networking, if the rat is what we think - an encrypted remote administration tool; I don't think it would run in safe mode without networking.

b) I'd appreciate very much (and I bet I'll not be the only one), if you could emphasize a little bit "booting into forensic environment". A quick search of synaptic after the keyword "forensic" offered autopsy, sleuthkit, scalpel, rdd, unhide, vinetto, tct. Frankly, I can't imagine nothing better from copying the image of his infected HDD and analyzing it afterwards from a clean Linux box, but I've never done any forensic and my guess is that for the insight of what's happening he would be better to start from examining/scanning the infected box from other machine while the rat is still there running - that's how he would see all the processes running and will have better chances to determine what attacked him, so he would learn for sure how to fix it. Though, it would take more time.

BTW, I figured out the way how not to clear the entire HDD and still be safe, following in my next post.

I've never bothered with the term runlevel for a windows machine.  You want to boot in vanilla safe mode, not with networking because there are a couple of nasty samples out there that will patch the network drivers and run at kernel level. It's a very slick way to get full kernel access and be persistent since the driver is loaded every time the system boots.  It can then use some rootkit techniques to hide from anti-virus if a signature is ever deployed for it.

I use the Helix live forensics disk most of the time if I can't or don't care to pull the drive and put it in a forensics bay to run Encase on it.  There are a lot of forensics tools out there that have known good files hash tables that you can download and then can filter out those files to find the questionable ones.  I've found malware that had patched itself system files that way.

I don't get many opportunities to examine an already infected box.  I normally receive the actual malware executable or the dropper(meaning it generally drops actual malware in a different directory and then deletes itself)/downloader (calls out and downloads files for more functionality) for it.  I get to spend time staring at it in IDA Pro with Hex Rays and Ollydbg for static analysis to find out what makes it tick and what exactly it does.  I do run the malware in virtual machines that have process monitor and process explorer running to tell me what it does as well.  After it runs I can watch the virtual network with Wireshark to see what IP addresses it calls back to and start picking apart it's communication methods.  I can go on and on with all the methods used from debugging the VM to diffing the system but that's the basics.

---

### Post by Kinstonian on 2008-11-09
Stick with the facts guys.  Basically all the OP said was his computer was communicating with another computer in Poland, and he couldn't figure out what process was responsible for it.

You don't know the process responsible, or that the traffic was encrypted, you don't even know what protocols or ports were used, if it was possible for the traffic to be spoofed, it's capabilities, or if it was even malicious.

The fact is the OP didn't provide enough information to come to any reasonable conclusion.  Recommending he reformat is a bit premature.  We need more info.

---

### Post by kevdog on 2008-11-09
Yes I do know it was using http over port 80.  And that's about all I know.  I followed the tcp stream, however none of it was in ASCII.  There was about 1 packet send every 1-2 seconds.  That's about all I know.  I really haven't had time to research it from once I first posted, other than the antivirus scans (not that I really think it is a virus) are coming up blank.  Sysinternals scan also came up blank, as did Microsoft Forefront Security.

I haven't rebooted in about a day to investigate farther however can tell you at least in 24 hours after blocking outgoing packets to the specific ip address, nothing has been sent on perusal of the wireshark logs, which has been continuously running. (No other unknown addresses have appeared either).

---

### Post by Chayak on 2008-11-09
> **kevdog said:**
> Yes I do know it was using http over port 80.  And that's about all I know.  I followed the tcp stream, however none of it was in ASCII.  There was about 1 packet send every 1-2 seconds.  That's about all I know.  I really haven't had time to research it from once I first posted, other than the antivirus scans (not that I really think it is a virus) are coming up blank.  Sysinternals scan also came up blank, as did Microsoft Forefront Security.

I haven't rebooted in about a day to investigate farther however can tell you at least in 24 hours after blocking outgoing packets to the specific ip address, nothing has been sent on perusal of the wireshark logs, which has been continuously running. (No other unknown addresses have appeared either).

Just because it doesn't show up on anti-virus doesn't mean your not infected with something, as I explained in a previous post.

Download the Norton AV 2009 demo or the Kaspersky demo and try them.  It might have hidden itself so it won't show up on AV but the behavioral stuff may catch it.  After you install them reboot and see one of them can catch it.

As for jumping the gun I see this stuff every day.  There are zero reasons a machine should be calling out that much to an IP in Poland.

---

### Post by zenial on 2009-01-16
Repsot

---

### Post by bodhi.zazen on 2009-01-16
sudo iptables -A OUTPUT -d 78.131.193.150 -j DROP

Or for incoming packets

sudo iptables -A INPUT -s 78.131.193.150 -j DROP

Or blacklist the IP in a blacklist

---

### Post by nitrogensixteen on 2009-01-17
AVG Linkscanner blacklists traffic to the ip you identified, this would confirm it is involved with some type of malicious activity, as perceived by AVG.

TCPView from sysinternals will identify the program which is transmitting the packets, UNLESS the virus has rootkit features which are hooking the routines returning this information or using DKOM to filter this information inside the kernel. You cannot trust what your computer is reporting to you if you think it is compromised. You cannot trust the output of autoruns because the registry services may be hooked as above, or because the registry viewer you are using is incapable of viewing the offending strings because they have null unicode characters inserted (registry viewer is based on win32 api). You may be able to use sysinternals rootkitrevealer to detect these null strings, but if a rootkit is installed, you should not trust this either...
I highly recommend against installing demo versions of anti-virus software, or any anti-virus software you need to pay for period. Too many people think they have an adequate level of protection from viruses once their subscriptions run out.

I am unaware of any virus or malware technology which can remain resident in any form of memory on a CPU once power is removed, does anyone know of a technology which can do this? I am aware that shadow walkers and HVM rootkits use advanced processor features to become indetectable except by inferrence or subroutine benchmarking, but am unaware of what the above poster is talking about?

If the computer is compromised, you cannot trust it in safe mode without networking. You cannot trust it AT ALL once you have run executable files off the hard disk which you have not verified by signature to be uncompromised. Do not assume the level of sophistication of the malware.
Why do you want to continue using a computer which may be exposed to your personal or financial information after control of it has passed to hacker/crackers or cybercriminals.

As for flushing the BIOS...if you think your bios is infected, why do you think you can trust the bios to update itself and not reinfect the new copy, not allow a new update, or misreport version information once you THINK you have updated it. If you want to verify your bios, find another computer which accepts your PROM, boot it with a known good bios, pull the good bios out once it is running, put the suspect one in, and dump it with a floppy update utility. Check it's cryptographic hash against the hash of the copy of that version bios form the vendor's website. I have not had to do this for a long time, but have successfully done it to reflash dead bios's. I realize this may scare people but it works. You can even reflash the bios if it is suspect.

The best solution to your problem is: extract your documents from your old drive by mounting it on another computer or running a livecd, giving any file which may contain malicious code close scrutiny, format the hard disk, and re-install. I would not trust that the malware can be removed with an automated antivirus as many virus's/worms contain downloaders which may install arbitrary software/rootkits/more malware to the machine and not all malware may be detected by any one or any antivirus at all.

It baffles me as to why windows users continue to operate a machine which they have lost control over. I think if people truly appreciated the sophistication and capabilities of modern malware, it might outweigh their fear of losing information/time/resources.
Do yourself a favor and maintain a baseline image of your machine which you trust, and has enough of your required software installed to prevent you from not wanting to restore the backup!

Personally I would grab my documents, wipe the hard disk, install windows again, install free security software, load my documents, and maintain a NIDS or secure gateway on the network to prevent the infiltration and subsequent exfiltration of data or heartbeat back to the malware controller. Until you have your computer updated and all your security software installed, I recommend using an external firewall to prevent communication to or from the computer with any host except microsoft and your software vendors.

---

