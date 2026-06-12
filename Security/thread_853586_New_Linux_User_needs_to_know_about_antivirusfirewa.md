---
title: "New Linux User needs to know about antivirus/firewall."
date: 2008-07-08
forum: Security
---

### Post by jungleexplorer on 2008-07-08
OK.  I have been using Linux for all of 20 minutes, so yall be kind to me, I am having Windows withdrawals.  Linux is a whole new world to me and I really want to break my Windows habit.

My first concern is security and that is why I am here.  I am some what of a windows security expert and my brain is used to thinking in terms of firewalls and anti-viruses.  I have read a few other post on this forum  from people like me and all the answers seem kind of cryptic, as if there is some special code that only Linux users understand.  For this reason I humbly ask that when responding to my post you take into consideration that I am a windows zombie that just now trying to wake up and you need to speak slow and simple to me.  Thanks.

1. Anti-Virus

I know that the large majority of viruses are created exclusively for windows and will not effect Linux. But I also have read of viruses that will effect both and of other viruses targeted at Linux.  Even though these are extremely rare, it only takes one virus to destroy your computer or your life.  There also exist a danger for dual boot systems running windows and Linux, such as I will have to do until I become comfortable with Linux and am able to find all the Linux software I need to replace my windows software.  In the case of a dual boot system, a person might download a windows virus while using Linux.  The virus will be inactive while Linux is running, but when the person reboots into Windows, the virus will then become active.  Because it is already on the system any windows installed anti-viruses will probably not be able to catch it in time to stop it.

So my question is, are there anti-virus softwares out there for Linux that are equivalent to McAfee, Norton and the like?

2. Firewall

I have a wired and wireless windows based home network consisting 4 computers and 1 server.  I have over 1 terabite of data on my sever and hundreds of gigabites of data on the other connected systems.  If a malicious person were to gain access to my network, it would be devastating to me.  I currently use both hardware and software firewalls to minimize my risk of unauthorized intrusion. Unlike viruses that have to be designed for an operating system, hackers don't care what OS you are using, they just want to gain access to you system so they can steal your data.  How do Linux users protect themselves from hackers?  Do they use firewalls like windows users, or is there some other form of protection?

Thanks you for all your help.

---

### Post by spike_strip on 2008-07-08
It is not the same thing; hear you are comparing Apples to Oranges. 
> **jungleexplorer said:**
> is, are there anti-virus softwares out there for Linux that are equivalent to McAfee, Norton and the like? 

There are plenty of programs that you can implement to provide you [your LAN] with a much great security profile, than you currently have. 

So No; there is nothing like McAfee ... no need. 

Once you begin using Linux you will understand this more clearly. 

The firewall issue is covered in this forum in great detail. 

The way I read your post: 
> **jungleexplorer said:**
>  If a malicious person were to gain access to my network...minimize my risk of unauthorized intrusion

...and you need to protect your assets: > **jungleexplorer said:**
>  I have over 1 terabite of data on my sever and hundreds of gigabites of data on the other connected systems.

Your time might be better spent researching Snort and OSSEC. These are intrusion detection and prevention programs you can run or your Linux system.

---

### Post by LeoSolaris on 2008-07-08
These after shocks of Windows are quite common. Linux is pretty secure out of the box, and with a little googling, and searching of the forums you can get up to speed on some basics to harden it a little if you really want to. It isn't actually needed for normal users, but if it eases your Windows addicted unconscious, then by all means go for it.

There are only a handful of Linux viruses, and none of them have been found in hte wild. Meaning they were all proof of concept work, rather than released to do damage. Linux is immune to Windows viruses, though you may catch something if you use wine (windows emulator). All ya have to do then is delete the wine folder, and your fine.

Linux has a built in firewall, it is part of it's design. You can install a front end (thats the little window you see so you can manipulate it with the mouse) if you want to change things but the default will weather perfectly fine for most peoples needs.

If you stick to programs in the Ubuntu repo, and you don't go making really easy to crack passwords, you should be just fine.

It's a whole new world...   Welcome!

Leo

---

### Post by 16777216 on 2008-07-08
If you want to clean downloads [clamAV]("http://www.clamav.net/") works great but has no "autoscan" feature, and I believe it is in the Ubuntu repos ( easy install ). [Avira]("http://www.free-av.de/en/products/1/avira_antivir_personal__free_antivirus.html") has a [linux version]("http://www.free-av.com/en/download/download_servers.php"), as well as [Panda]("http://www.pandasoftware.com/download/linux/linux.asp"), [McAfee]("http://www.mcafee.com/us/enterprise/products/anti_virus/file_servers_desktops/linuxshield.html"), and [Sophos]("http://www.sophos.com/products/").
You may have to pay for most of them except clamAV.
As for a firewall, their are plenty of choices as well, but most are just GUI frontends for configuring the built in firewall.

---

### Post by Dr Small on 2008-07-08
First off, Greetings and welcome to Linux. I see that you value Security as a high priority, and I congratulate you for that.



> **jungleexplorer said:**
> [...] I humbly ask that when responding to my post you take into consideration that I am a windows zombie that just now trying to wake up and you need to speak slow and simple to me.  Thanks.
Posts are written, not spoken. So you may go back later and read it at your own pace, for further comprehension :) lol. I just had to say that one :p



> **jungleexplorer said:**
> [...] In the case of a dual boot system, a person might download a windows virus while using Linux.  The virus will be inactive while Linux is running, but when the person reboots into Windows, the virus will then become active.  Because it is already on the system any windows installed anti-viruses will probably not be able to catch it in time to stop it.
This my friend, is speculation. For the first fact, if you download a Windows Virus while on Linux, this virus can not execute (unless you are running it in wine), can not harm your system, and can not spread nor execute onto your Windows partition. There should be no fear here. Booting into Windows will not execute the Windows Virus on your Linux partition, mainly because, it is on the Linux Partition.




> **jungleexplorer said:**
> 
[...] So my question is, are there anti-virus softwares out there for Linux that are equivalent to McAfee, Norton and the like?
There are Antivirus software for Linux, but it only scans for Windows viruses; their signatures. Virus scanners on Linux do not (and can not) scan for Linux viruses, only Windows viruses.

Mainly you will see people run a Anti-virus on a production server (FTP, HTTP or Mail) to protect Windows Users from uploading a known virus and having other Windows Users download it. This is generally a courtesy measure taken by some Server Administrators, as the viruses do not effect their servers nor Linux users.


> **jungleexplorer said:**
> 
[...] Unlike viruses that have to be designed for an operating system, hackers don't care what OS you are using, they just want to gain access to you system so they can steal your data.  How do Linux users protect themselves from hackers?  Do they use firewalls like windows users, or is there some other form of protection?

First off, most and not all hackers are bad. Take me for instance. I am a hacker, but I am a whitehat hacker. So the general viewpoint of all hackers being evil, is a bad mindset.

How do we protect ourselves from the scriptkiddies running bots against our servers and the real attackers attempting to break in? Well, alot of people think that hackers carry this magical wand, and whatever server this wand touches, they are given access too. This is wrong. There is much more to hacking than to magician's tricks.

To better understand how one would hack into a server, you must look at it this way. An open port, a service listening on a port. (If, let's say, SSH was running on Port 22, this would give an attacker an access point to begin a bruteforce against the authentication system). Strong passwords are essential, because most of the cracking going on generally are from a simple password on a user called 'root'.

To protect yourself, you should arm yourself with denyhost, tripwire, strong passwords and firewalls. Well, at least one firewall. If everything must go through a router before it can access anything on your network, and this router has a built in firewall, it is generally easier just to depend on this firewall alone. But if you don't, you can always just setup rules on iptables, or use Firestarter to configure them.




> **jungleexplorer said:**
> Thanks you for all your help.

No problem. Glad to be of service to you. If you still have any other questions, please feel free to post them. We are here to help you, assist you, and give you guidance.

Take care,
Dr Small

---

### Post by wdaniels on 2008-07-08
> **jungleexplorer said:**
> In the case of a dual boot system, a person might download a windows virus while using Linux.  The virus will be inactive while Linux is running, but when the person reboots into Windows, the virus will then become active.  Because it is already on the system any windows installed anti-viruses will probably not be able to catch it in time to stop it.

It doesn't really work like that. It's not impossible, but extremely unlikely that any such cross-infection could occur. For starters, many of the means that viruses use to infect a system in the first place rely upon exploiting holes in Windows that will not exist in Linux. For example, embedding malicious code in non-executable files to exploit unchecked buffers would not work on Linux. Probably the only way for the Linux system to acquire a Windows virus is if you were to download a file containing a virus, place it in some shared area, then access it from Windows, in which case the virus is not "already on the system" and would be checked "on access" by the Windows virus scanner, just the same as if you had downloaded it in Windows, because at this point the virus code has not been executed so it will not have been able to install itself into the system.

In the other direction, a Windows virus wouldn't be able to read the Linux filesystem for starters, and even if it could, any of the means by which a virus can "install itself" into a system would not work when applied to a Linux filesystem (e.g. there is no registry file to add itself to the "Run" key and there are no common filenames/locations for automatic execution between the two systems). And that is assuming you are using Wine and that Wine would successfully execute the virus. And even then, unless the virus were to do something so generic as trash the partition table (though I doubt that Wine supports any Win32 API to do that anyway, if there even is one), it would not have the intended effect on the Linux system regardless.

> **jungleexplorer said:**
> hackers don't care what OS you are using, they just want to gain access to you system so they can steal your data.  How do Linux users protect themselves from hackers?

Hackers do care what OS you are using, in fact that is usually the first thing they will try to determine. Brute force attacks over certain standard protocols will apply equally regardless of OS, so the best defence here, as already mentioned, is to use strong passwords. But generally, it is infinitely more difficult for a hacker to gain access to a Linux system if there are no such services running. It should be safe enough to run an SSH server for remote access if needed since SSH has an exceptional security record, but for the most part, unless you want to run Web/FTP/Mail servers etc. you will not need to change any of the default Ubuntu settings to be secure and it would take a capable, dedicated, human attacker, targeting you specifically for some reason, to pose any real threat. This does not apply to 90% of "hackers" and certainly not to 99.99% of the usual intrusion attempts.

In short, although your concerns about cross-infection between dual-boot Linux/Windows systems are largely unfounded, it is still a good idea to follow the suggestions made here (and elsewhere) regarding security under Linux, particularly with respect to strong passwords. But there are not really many "standard" additional security measures needed for Linux systems like there are with Windows. Perhaps intrusion detection (e.g. snort) is something relatively generic that you can add, but most other "additional" security measures that you might like to implement will be specific to whatever additional services you intend to run on your Linux systems, which you would need to specify to receive the relevant advice.

---

### Post by hansdown on 2008-07-08
Welcome jungleexplorer.

---

### Post by hyper_ch on 2008-07-09
(1) generally not antivirus needed

(2) generally you don't need to modify iptables

(3) you should know what you want to protect you (or others against) and then you might want to decide to implement either (1) or (2) or both

---

### Post by jungleexplorer on 2008-07-09
Wow!  Thanks for your help guys.  I really feel much better now.  I do have one additional question.  It probably is a dumb one like my statement about the dual boot danger, but you know what they say, "The only dumb questions, is the one you never ask."  I don't know if that is true or not because a friend of mine called a plumber out the other day to unclog his kitchen sink.  He said "Can you tell what the problem with my sink is?"  The plumber reach over and pulled the stopper out and said "Here is your problem." LOL!  I just had to tell that story!

Anyway, here goes my dumb question for the day.  Taking into consideration everything that has been said (Oh, I'm sorry, "Written") so far, does it make any difference that I used the Linux Wobi installer(I think that is what it is called). If you have no idea what I am talking about, then let me explain.  I have the Hardy Heron version of Ubuntu.  It has a function that allows you to install it as a program from within Windows, and I think that function is called the "Wobi Installer" but I am not sure.  Now I did install Linux on a separate physical drive from my Win XP Pro Corporate installation.  So now when I boot up I am given the option to boot into Windows or Linux.  Supposedly I can uninstall Linux (if I should want to) from the Add/Remove Programs applet in Windows.  So my question is, does this type of installation have any effect on the advice that has been given to me?

Thanks again.

---

### Post by hyper_ch on 2008-07-09
well, a virus or malware could always damage other partitions and files....

while in linux you probably won't ever come accross such a thing (I hope that will also be true for the future) you can come accross malware in windows quite "easily". If they get enough privileges they could format partitions and stuff... with wubi it creates some kind of "ubuntu" file - if I'm not mistaken on the windows installation. So it is quite possible some malware could modify that and render your wubi installation useless.

Golden rule: make regurarly backups of your important data.

---

### Post by damis648 on 2008-07-09
It is DEFINITELY a bigger security risk using Wubi. As the poster above me mentioned outlined, Ubuntu installed in a folder on your main Windows NTFS partition. What this means is that any malware that might affect Windows COULD affect Ubuntu, not in the way that the system is zombie-like and virus-ridden, just that your Ubuntu files could get accessed or deleted. Also, recovering from errors or power loss would be much more difficult in this scenario. I would recommend uninstalling from the Add/Remove Programs and repartitioning and doing a complete install from the liveCD (it will do everything automatically and is very easy). If you are not ready for this or too nervous, that's fine, we all are the first time. You do not have to. Experiment with your Wubi installation. See if you like Ubuntu, and if you do, go for the full install.

PS. In a very short answer to your original post:
There are no anti viruses that I know of that scan files for Linux viruses (you are not likely at all to get one... you have less chance than randomly winning $2 Billion), but ClamAV (can be installed via Applications>Add/Remove) will scan Windows executables for viruses so you do not accidentally give your Windows a virus. As for a firewall, there is one built in, called iptables. All ports are OPEN by default, but you can change this. Install firestarter and run through the configuration.

Welcome to Ubuntu! :popcorn:

---

### Post by hyper_ch on 2008-07-09
no need to run a firewall... iptables is unconfigured - meaning it lets everything pass... but there are no services listening and hence there is nothing that needs protected. Only when you start installing services (apache, ssh server, samba, ...) you might want to consider to limit access to it.

---

### Post by hammondb3 on 2008-07-14
> **16777216 said:**
> If you want to clean downloads [clamAV]("http://www.clamav.net/") works great but has no "autoscan" feature, and I believe it is in the Ubuntu repos ( easy install ). [Avira]("http://www.free-av.de/en/products/1/avira_antivir_personal__free_antivirus.html") has a [linux version]("http://www.free-av.com/en/download/download_servers.php"), as well as [Panda]("http://www.pandasoftware.com/download/linux/linux.asp"), [McAfee]("http://www.mcafee.com/us/enterprise/products/anti_virus/file_servers_desktops/linuxshield.html"), and [Sophos]("http://www.sophos.com/products/").
You may have to pay for most of them except clamAV.
As for a firewall, their are plenty of choices as well, but most are just GUI frontends for configuring the built in firewall.

How do I see the firewall In ubuntu version 8, im looking all over and 
cant seem to find the firewall, I dont even see firestarter where the heck is it, and where can I find it.

---

### Post by Dr Small on 2008-07-14
> **hammondb3 said:**
> How do I see the firewall In ubuntu version 8, im looking all over and 
cant seem to find the firewall, I dont even see firestarter where the heck is it, and where can I find it.
Install Firestarter if you want to monkey with firewall rules from a GUI.
```
sudo apt-get install firestarter
```

---

