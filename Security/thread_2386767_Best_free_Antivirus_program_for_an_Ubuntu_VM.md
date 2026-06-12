---
title: "Best free Antivirus program for an Ubuntu VM"
date: 2018-03-10
forum: Security
---

### Post by sam64 on 2018-03-10
Hi. I'm planning to explore the deep/dark web, but I'm taking the  necessary precautions first (using a virtual machine, a VPN, and an  antivirus for the VM).

So I'm trying to figure out what the  best free antivirus program would be for my Ubuntu virtual machine. The  reason is because I've recently learned that VMware still relies on a  so-called Internet Relay Bridge to your main host's internet connection  in order for your VM to access the internet. Is there a specific  antivirus program that would help with that, and that wouldn't interfere  with the functionality of a VPN service provider?

---

### Post by TheFu on 2018-03-10
AV isn't all you need and AV on Linux isn't likely to help much.  Viruses just aren't written for Linux much. There are sticky threads at the top of this forum which explains. Read those.

Don't use WINE.
 
Professional security people use different computers. Breaking out of VMs **is** possible for targeted attacks, like you will be exposing your system.  Best to remove any storage that you don't want compromised - disconnect it.  Unplug the sata cables.

---

### Post by tnthomas on 2018-03-11
The only AV for Linux that I know of is[ ClamAV]("https://www.clamav.net/").    You  also might consider [chkrootkit ]("http://www.chkrootkit.org/") or [rkhunter ]("http://rkhunter.sourceforge.net/")for detecting rootkit files.    They are available in Ubuntu repositories.

---

### Post by 9cddz&amp;mK07%F@ on 2018-04-14
Some antivirus producers such as Avast have products for Linux. If you want your system to be 100% open source, use ClamAV.

---

### Post by monkeybrain20122 on 2018-04-14
Clamav checks for Windows virus and is notoriously crappy. You don't need AV on Linux.

Edited: going to the dark web is not a usual use case, but I doubt that in this instance AV would help much if you expose yourself that way.

---

### Post by monkeybrain20122 on 2018-04-14
> **TheFu said:**
> 
Don't use WINE.
 
.
 Better check with Wine HQ to avoid virus with platinum or gold rating. :)

---

### Post by TheFu on 2018-04-14
> **monkeybrain20122 said:**
> Better check with Wine HQ to avoid virus with platinum or gold rating. :)

Exactly.  Linux systems have gotten Windows viruses through WINE while using other Windows programs.

My point is that looking for trouble and expecting any virtual machine to protect the OS and the hostOS is not likely to be over 70% useful.  If you poke-the-lion, your odds drop 25% more. There are just so many attack vectors available today.

If I were planning to do what the OP is planning, I'd use a chromebook running a freshly loaded chromeOS with a new google account or just the guest account.  The running OS on chromebooks cannot be modified. It is part of the security for the OS.  We can simulate something like that with containers under Linux, so running a VM + a container for the bad VM work is useful.  Don't forget to change all the things that can identify the system too.  Definitely change the MAC(s), but also the things used by super-cookies need to be changed. Using a file system overlay that gets wiped would be good too.  Hard for a supercookie to remain on a system that doesn't store anything to disk.

But for most people, the easiest answer is to run from a burned CD/DVD and have no other storage connected to the computer when performing high-risk activities.

---

### Post by SeijiSensei on 2018-04-14
I don't use VMware, but the default configuration in Virtualbox hides the VM behind the host and connects with NAT ("masquerading") like many routers do. I'd be surprised to learn that VMware only allows bridged networking.

AV isn't worth your time. Just make sure you have a clean snapshot of the VM you can revert to if something goes awry.

---

### Post by HermanAB on 2018-04-15
Hmm, I would build a new system for the experiment and make a backup for easy restore.  AV etc, is simply a waste of time.

---

### Post by kerry_s on 2018-04-15
there are distros built more securely than normal i suggest using 1 of those.
i have my mom on endless os which has a read only /root & apps are flatpack. never had any issues with her system since.

---

### Post by sevendogsbsd on 2018-04-24
To be completely safe, use a read-only file system by booting into a live cd or usb image and don't mount anything while doing that so you are completely disconnected from any existing file systems.

---

### Post by TheFu on 2018-11-10
> **lebort said:**
> Which ones can be used on Linux and how effective is it? I just recently switched from Windows.

Read the Sticky Threads about Linux security here: [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338) - that is the Security Subforum.  The only reason to run AV on Linux is to protect the other machines on your network from Windows viruses passing through Linux.  Scanning for Windows viruses isn't generally needed on Linux, since they have no effect, except in some very strange situations.

Would you worry about an IBM mainframe getting a Windows virus?  No.  The same applies to Linux.

That isn't to say that Linux is 100% secure. No networked OS is.  The ways to secure Linux are different from how to secure Windows, thus an AV tool just isn't needed.

The only reason that I'd run AV on a Linux desktop is if some contract demanded it, which does happen.  For example, my company has E&O Professional insurance.  Under the policy, all computers connected to the company network are required to run currently supported, currently patched, operating systems. Each of those systems is required to have a current, updated AV tool.  The contact was clearly written by Windows-centric environments.  If we didn't run the AV tools on every system, then the insurance is worthless.  

BTW, if you have a question, it is best to open a new thread.  The "me too" posts that other forums prefer isn't how we like to do things.  Each setup is unique.  After searching these forums for answers to a question, if you don't find one that fits, then create a new thread and ask your question.  Usually there is something specific for your setup that makes the question just a little different, but doing a little research first will help you ask a better question, if that makes sense.

---

### Post by mcyber4 on 2018-11-13
> **TheFu said:**
>  I'd use a chromebook running a freshly loaded chromeOS with a new google account or just the guest account.  The running OS on chromebooks cannot be modified. It is part of the security for the OS. 

Interesting, didn't know that. Ideal for travel or lending to other people. Does it run Linux apps like for ex. Steam games?

---

### Post by TheFu on 2018-11-13
> **mcyber4 said:**
> Does it run Linux apps like for ex. Steam games?

Some chromebooks with chromeOS can run Linux apps. Mine cannot, because Google wants to sell new hardware and is in collusion with chromebook makers to sell more hardware, not because it isn't capable.  I don't have any clue about steam games.  Not an interest of mine of any level.

However, if you buy a chromebook that can have chromeOS wiped, then some other OS installed, then you can run pretty much any program you want.  To wipe ChromeOS will require physical modification of the device, which used to break the warranty. I'm unsure if that is still the legal situation in my country due to recent court rulings.  But the required modification for my current chromebook is both breaking an electrical connection AND totally replacing the BIOS. It will never be able to run any version of ChromeOS again without an external EEPROM programmer and a specific sort of screw washer to make the electrical connection again.

The main issue I had with chromeOS were 2 things

1) Google pushed updates whenever they wanted and there was no way to stop it, delay it.  Got screwed just before an overseas trip which broke my setup.

2) No support for non-google kernel modules like NFS.  NFS is something I use heavily, especially on a device with limited storage.

I'm anti-cloud service.  Zero interest in putting my data on systems controlled by someone else. It was bad enough when google found my photo gallery and decided it was fine to make it available to the world without asking.  As soon as I realized that, my entire online world changed from being open to being restricted access.  BTW, don't trust the "friends only" settings on any cloud/social network.

---

