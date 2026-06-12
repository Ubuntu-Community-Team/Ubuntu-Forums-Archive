---
title: "Switching business from Windows to Linux"
date: 2008-07-09
forum: The Cafe
---

### Post by VitaLiNux on 2008-07-09
I have just found this excellent article from PC World and I put it here for those who haven't read it:

Move Your Business From Windows to Linux
----------------------------------------------
[COLOR="Blue"]If the cost of Windows is getting your small business down, consider shifting to Linux.[/COLOR]
----------------------------------------------

Windows Vista debuted to muffled applause, followed by lackluster sales. Up until June 30, cash-strapped businesses looking to avoid the cost of upgrading to new Vista-compatible hardware could still purchase trusty Windows XP. Now, however, Windows XP is available only as a costly "downgrade" from Windows Vista--if you buy a copy of Vista, you can install the 6-year-old XP operating system using the Vista license.

If that feels like a waste of your small business's precious IT budget, and you're still looking for an alternative to Windows Vista, look no further than Linux. The latest distributions are free, easy to install, and highly customizable; they harness your existing hardware without overtaxing it; and they include a wealth of productivity applications and utilities. You may already have a closet Linux expert on staff, but if you don't, paid support is usually available at rates far less than Microsoft's.

Making the switch from Windows to Linux will incur some costs as employees and support staff adjust to the new system's configuration settings, utilities, and applications. Even so, the savings in future hardware and software upgrades could be huge.

[COLOR="Blue"]No License, No Fee, No Problem[/COLOR]

Though you can purchase boxed commercial versions of Linux that include support, every Linux distribution is also available for free under the terms of the open-source Gnu General Public License, or GPL. Once you figure out which distribution you'd like to use (see below), you can simply download, burn, and install it on as many systems as you choose. Your software licensing fee is zero, compared with the $300 per seat for the full version of Windows Vista Business Edition. And, another bonus, Linux lacks Microsoft's intrusive activation requirements.

In addition to thousands of other free applications (see "Linux Replacements for Your Favorite Windows Apps" for some of my favorites), most Linux distributions come with a copy of OpenOffice.org. Though not a feature-for-feature substitute for Microsoft Office, OpenOffice.org definitely does the job, and for $500 less per workstation than the cost of Office Professional 2007. OpenOffice.org lacks an equivalent to Microsoft Outlook, but just about every Linux distribution includes Novell's free Evolution PIM.

A few key Windows-based applications such as AutoCAD and Photoshop lack Linux replacements, but for many office workers the missing functionality hardly merits spending $800 more for Windows and Office. Many Windows applications will run at native speed under Linux via the Wine utility included with most distributions. For those that don't work with Wine, two more options exist: You can install a copy of Windows using one of the available free virtualization utilities, such as KVM (Kernel-based Virtual Machine, built into the Linux kernel) or VMWare Server, or you can install Linux to dual-boot with Windows.

For most distributions, the same disc will contain server applications, including the Apache Web Server, the MySQL database engine, virtualization, and support for leading commercial databases and CRM applications from companies like Oracle, Sybase, and SAP. The Samba networking software emulates Windows Server's networking features admirably, and for free, versus Windows Server 2008's starting price of $999. You can even replace your costly Exchange server installation with the free, open-source Zimbra Collaboration Suite.

Whether you're using desktop or server versions of Linux, the operating system is famous for one other important feature that Microsoft is still gradually adding to Windows: security. Linux is not somehow magically immune to viruses, worms, and other Internet-based attacks. However, the reality is that the vast majority of existing attacks target Windows and Windows applications. Mostly by design, Linux is simply not subject to most of the Internet-based malware that threatens PCs. The overwhelming majority of malware targets Windows.

[COLOR="Blue"]Don't Panic at the Distro[/COLOR]

No two Linux distributions are the same, differing mainly in how user-friendly their installers are, how willing they are to include experimental or nonstable versions of software and utilities, and how they offer access to updates.

The two most popular Linux window managers, the software that controls the look and behavior of the X Window graphical user interface, are Gnome and KDE. Most distributions default to installing one or the other--Ubuntu opts for the former, for example, and OpenSuSE, the latter. However, you could install both window managers (and dozens more) on your system, and choose which to use when you log in. Several window managers, notably Xfce and Blackbox, require less memory and graphics processing than Gnome and KDE, making them a good choice for older hardware. Lightweight Linux distributions, such as Puppy Linux, prune the OS down to its elements, breathing life into even the most ancient PC.

Linux distributions also differ in how well they support your particular hardware, especially wireless networking devices and display adapters. Perhaps the easiest way to directly assess this support on your particular hardware without having to actually install Linux is to download, burn, and boot a live-CD distro. Ubuntu, OpenSuSE, Gentoo, and literally hundreds of other Linux distributions come in live-CD versions.

[COLOR="Blue"]Get Help, If You Need It[/COLOR]

The reality of operating system support is that it costs a lot of money, whether it comes from Microsoft, Apple, Novell, or Canonical. Your copy of Windows Vista comes with 90 days of technical support via phone, e-mail, or chat that starts the day you activate the product. After that, Microsoft charges $60 per support incident.

Commercial Linux distributions offer similar, but less expensive, support options. The $60 packaged version of Novell's community-supported OpenSuSE 11.0 comes with 90 days of installation support. For long-term support, choose SuSE Linux Enterprise Desktop (currently in version 10) for $50 per year, or go with Ubuntu and buy a support contract from maker Canonical starting at $250 per year.

If you're already doing without dedicated support staff for Windows, one year may be all the paid support you need for Linux. Ubuntu users joke that simply googling for technical support usually results in the exact answer you're looking for on Canonical's forums.

Linux is different from Windows, but it isn't an alien life form. The human investment you make in transitioning away from expensive Windows and Office licenses may pay for itself quickly. More important, you'll be free to run the desktop and server software of your choice, on hardware you can afford.

---

### Post by VitaLiNux on 2008-07-09
I think this article is just priceless...:guitar:

---

### Post by Redache on 2008-07-09
It's shockingly well written. I think the apocalypse may be coming to fruition as this is not normal behavior for PC World.:lolflag:

---

### Post by the_darkside_986 on 2008-07-09
But what about an Active Directory replacement? In one company's setup, the user logs into Vista under a domain so that their home files are saved on both the Windows 2003 server and the local machine. Disks tend to fail, but the probability of them both failing at the same time is smaller. What is the GNU/Linux answer to Active Directory?

---

### Post by NxZDr on 2008-07-09
The Answer is the endless lines of Unix/Linux Network Share and Client/Server Applications that have been in existence from the beginning of Corporate Databases? Active Directory isn't anything *new* it just finally brought this sort of functionality to Windows.

Even then, basic PHP scripts can replicate this.

---

### Post by the_darkside_986 on 2008-07-09
I'm not trying to be a troll I was just wondering because I have very little knowledge in either field. My main strength is GNU/Linux desktops and troubleshooting silly Windows problems (which is mainly what they hired me for). But the main IT person, he takes care of Active Directory issues for machines in the whole company.  I installed Ubuntu via Wubi on one of the new machines because Windows XP SP 3 could never use the wireless card and most of the hardware (even with the correct drivers and I can't find a functional ethernet cord anywhere for it). But I've gotta fix that driver issue and put the machine on the domain. What I am wondering is, is it possible to connect Ubuntu to an Active Directory that runs on a Windows 2003 server in a similar way I would connect an XP machine to it? I need a good link to a tutorial on that.

---

### Post by kikoman on 2008-07-09
We should also have to wait, business and government are not changing their systems if its not broken, the term "why fix it when its not broken", even most of them are still using old Win98/NT, Office97. What we can do is show them that alternative is available and waiting.

---

### Post by 50words on 2008-07-09
It is certainly possible. I have been running my business with Linux for nearly four months without any real problems.

My only irritation is that I still need to run Windows in VirtualBox because Fujitsu still does not support Linux and I am not ready to buy a new document scanner, yet.

But I agree with the poster above me. The real test will be the next version of Windows. Most businesses can survive on Windows for a few more years. If the next version of Windows is another uninspiring resource hog, I think we can expect to see more businesses migrating to Linux.

Assuming Apple doesn't go after the business market, that is.

---

### Post by toupeiro on 2008-07-10
> **the_darkside_986 said:**
> But what about an Active Directory replacement? In one company's setup, the user logs into Vista under a domain so that their home files are saved on both the Windows 2003 server and the local machine. Disks tend to fail, but the probability of them both failing at the same time is smaller. What is the GNU/Linux answer to Active Directory?

Nothing stops you from using Active Directory for UNIX/Linux.  We do this today.  8.04 has some built in auth. support.  There is also [Vintela]("http://www.vintela.com/"), which can even handle group policy across multiple flavors of UNIX and Linux.

---

### Post by Lord Xeb on 2008-07-10
> **VitaLiNux said:**
> I think this article is just priceless...:guitar:

^

---

