---
title: "New with Lubuntu, about security and safe browsing online."
date: 2014-07-15
forum: Security
---

### Post by FrontHQ on 2014-07-15
Hi, I use the lastest version of Lubuntu in a Pendrive and I wonder if I need to activate something else because I don't know if the OS without touching it a lot is safe, I have all the updates and in the console I activated the UFW, I want to use this OS for safe browsing and shopping online mostly.

Thank you if you take the time to read this.

---

### Post by TheFu on 2014-07-15
Online security isn't just about running or not running some software. There are many, many considerations - mostly user behavior and risk factors based on what else the computer does.  Linux alone is not enough to be "safe" anymore, but it is still 95% safer than OSX or 99.999% safer than Windows (purely due to market share). IMHO.

I run a VM off an ISO for online banking. That VM is not used for any other purpose and nothing is saved between reboots.  For most people, booting off a CDROM with a lightweight Linux - like TinyCore - is the easiest, best, security for their online banking, provided the machine is NOT directly connected to the internet (i.e. behind a router/firewall).

[http://krebsonsecurity.com/online-banking-best-practices-for-businesses/](http://krebsonsecurity.com/online-banking-best-practices-for-businesses/) is a short article about online banking security from an expert.

If you wonder what crackers (I'm a hacker, not a cracker!) do when they take over a system ... [http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/) makes for interesting reading.  I don't think any on-system security tool would discover these techniques.

---

### Post by ibjsb4 on 2014-07-15
Don't what you mean by safe; are you talking about shopping on line?  I find linux safe.

Edit: TheFu; has the better answer

---

### Post by patrikmellq on 2014-07-16
Make the settings that your computer check for updates each day.
One secure way is always to have your operating system up to date.

I also run UFW and have a router between my internet and computer.
But still i had the same feeling as you, is my Ubuntu secure?

There is no answer to that, because if some one want to crack or make an intrusion to your system, they will do so.
We can just make it more harder for them to do so.
There is no 100% protection.
My opinion.

BUT
You can know if some one has made an intrusion on your Ubuntu and the cracker or the person who made the intrusion can not hide from that fact.
It is a intrusion detection system with the name Tripwire.

It does not prevent some one from cracking or making intrusion into your computer, but it tells you when and how it happen, so you can act upon that.

Tripwire sign each existing file on your operating system with one unique key or algorithm and save the print into a database.
If some one change, modifies or replace any file on your system, then Tripwire will notice this.

They can not delete Tripwire, because you save the database with all secure information on a usb-stick.
So you can check your system daily and see if you have a clean running system with no intrusions.

---

### Post by at_first_light on 2014-07-19
There are several different elements that can be used to secure a system, but not all operating systems use all of these.

1. Permissions:
File and folder permissions are a method of controlling who can access what, and what restrictions are imposed on that access. Lubuntu uses this feature as it's primary defense, and even goes beyond with the addition of Sudo to reduce unneccessary use of root privilidges. On Lubuntu the operating system files are owned by root, without root privilidges viruses and hackers can't damage the operating system. They can get these privilidges either through a security hole, a bug, or from something silly the user does. Being careful when using your computer, and installing updates can help prevent this happening.

2. Physical Access:
Danger comes from the outside world. When you connect to networks, the internet, or plug a usb stick in you are presenting an opportunity. Lets face it, hackers don't come to you door they come in through your lan cable. You can help protect your system by disconnecting from the network when you don't need it, and being cautious about external storage devices. One of the easiest ways to get around permissions is to connect a usb stick to someones computer, boot it up, and use it to access the operating system partition, or boot files from outside the operating system.

3. Firewalls:
A firewall is very important on computers that are connected to a network, or internet. They control what can come in/go out of these connections. The computer equivalent of going through a border. Ideally a firewall will give you control of destinations, sources, and what/who can send/recieve from those destinations/sources. Lubuntu comes with IPTables and Uncomplicated Firewall. Once turned on these can give basic-medium protection. Lubuntu gets a low grade for firewalls in my books. 

4. Antivirus:
Antiviral software scans files for dangerous code. Ideally an antivirus product will support manual and automatic scanning. It should also support signature based, and heuristic scanning modes so that it can identify known, and unknown threats. The most important thing to remember about antivirus software is that if you scan a file and it doesn't flag it as dangerous that doesn't mean the file is safe, it means the file doesn't contain any known dangerous code, or suspicious code; perhaps you are patient zero. There are a few antiviral products for Lubuntu, but most only scan for Windows viruses not Linux ones. There are very few Linux viruses so that's not a huge deal. It's still important to run antivirus on Linux; even though Windows viruses can't infect a Linux system without the aid of Wine that doesn't mean you want viral code sitting on your hard drive undetected waiting to infect your dual boot or be sent to a friend. For most a manual scanning software to check downloads is enough.

5. Disk Protection:
Disk protection is where through the aid of software, or physical setup changes to the system are erased on demand or at reboot. Software disk protection can be worked around by some viruses. There are a few products for Windows operating systems. I don't think there are any for Lubuntu, but running a customized Lubuntu live-cd would be a make-shift equivalent.

6. Backup Images:
Some operating systems have auto imaging features, but for most this responsibility falls to the user. Creating a backup image of your system is a great way to protect yourself. Doing periodic refreshes is a great way to eliminate things that may have slipped past other security measures. Lubuntu has a program dd pre-installed, and there are others like Clonezilla that can be.

In general when using computers it basically boils down to being cautious, running things as a user, having some kind of firewall, and clearing your browser files.

---

