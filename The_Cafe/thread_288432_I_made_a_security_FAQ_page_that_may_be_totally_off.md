---
title: "I made a security FAQ page that may be totally off the mark"
date: 2006-10-29
forum: The Cafe
---

### Post by aysiu on 2006-10-29
I offered a few disclaimers, of course.

I'm not security expert, and this is mainly for desktop home security, not server security, etc.

The idea is for it to answer some simple, basic questions for beginning home users. I'm trying to stay away from more complex security measures that might just look like gibberish to first-time Ubuntu users.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Am I missing anything really big?

---

### Post by slimdog360 on 2006-10-29
I dont remember that seinfeld episode. Good demonstration of security though.

---

### Post by glotz on 2006-10-29
Something you might want to add is a GRUB [password](http://www.gnu.org/software/grub/manual/grub.html#password) and [locking](http://www.gnu.org/software/grub/manual/grub.html#lock) or removing the recovery boot options. Also might be a good idea to set a BIOS password and make BIOS boot HDD before CD or floppy. Also, since you included items as 'don't be a brick' you might also want to emphasize the religious use of the update manager! :)

---

### Post by Sef on 2006-10-29
You wrote up a nice basic intro to security.  For someone who knows nothing about security, it will help a lot.

---

### Post by viper on 2006-10-29
As always aysiu your info and help to us all is A1. Thanks:)

---

### Post by jdong on 2006-10-29
> 
Generally, the consensus seems to be that having a firewall is a good idea. Ubuntu comes with something called IP tables--I'm not exactly sure what it does, but I think it acts as a kind of firewall. There is a graphical user interface to configure it--the interface is called Firestarter, and it's available in the repositories. You can install another program called Guarddog, also available in the repositories.


Hmm, I'd rather say:
> 
By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited.

A firewall, however, adds the benefit of peace-of-mind from accidentally installing a server program that opens up a port by default. Also, it satisfies curiousity by logging potential "hits". Linux comes with a very strong, secure, and powerful firewall called "iptables", but it is relatively difficult-to-use from a new user's standpoint. As a result, there are many graphical tools that give you a simple user interface for configuring IPTables, such as Firestarter for GNOME or Guarddog for KDE. There are many more in the repository too. Remember -- these ALL use iptables in the background, so find your favorite interface -- they all offer the same great protection.


---

### Post by skymt on 2006-10-29
Thank you, jdong, for saying it better than I could.

---

### Post by vayu on 2006-10-29
In keeping with the amazing openness and gentleness you display on all your posts, I would recommend rephrasing "Don't be dumb" to "Be Aware".

---

### Post by maniacmusician on 2006-10-29
eh. "Don't be dumb" has a greater shock factor and makes sure the reader's paying attention (from a psychologist's point of view). It's not too offending, either.

great job on the article, aysiu. Seriously. We should find mirrors for your site. I remember you saying once that you have very limited bandwidth, and I think in the coming months, traffic will only increase as you add more helpful things.

---

### Post by TheMono on 2006-10-29
I love it when you add stuff. Easily the most accessible documentation I've found for a non-techy like myself. Thanks a lot.

---

### Post by aysiu on 2006-10-29
Thanks for the new text, **jdong.** I've made your suggested substitution and gave you credit for those two paragraphs. If that's a problem, let me know.

**glotz,** I'll put something in there about setting a password for the BIOS and/or Grub. I still would like to emphasize, though, that allowing someone physical access to your computer is essentially allowing root access.

**vayu**, thanks for the suggestion about phrasing. I'm going to stay with "Don't be dumb" for now. I can be cheeky sometimes, too.

**maniacmusician,** if someone wants to mirror Psychocats Ubuntu, I'm all for that. I would just ask that if any changes are made, the fact they were made is explicit, just so people know what I've written and what others have written.

What I'd like to see, actually, is a Wiki entry that's a bit more comprehensive. My page is just a basic intro for desktop users, but I'd love to see a comprehensive "Ubuntu Security: Best Practices" on the Wiki that includes encryption methods and security for servers.

I really know little to nothing about those.

---

### Post by argie on 2006-10-30
Perhaps a mention of shortening the time that sudo gives you root permission from 15 to lower?

---

### Post by deepwave on 2006-10-30
Pretty good start, a few things you might want to add:

Checking Logs and Network Traffic
One thing that a security-minded person is check for intrusions.  Checking logs and network traffic, like checking the at home locks is important.  If something looks odd, its better to know sooner than later.  Logs indicate the health of the system.  Looking at network traffic makes sure that nothing on your system, communicates with the outside world in an unexpected way.  Keep an eye on both, it may save you a good deal of pain later on.  Wireshark and tripwire are good tools to use.

Checking Rootkits
While viruses don't manifest themself in Linux, other nasty things do.  An attacker can gain root access by exploiting a weak point in a program.  Attackers try escalating their access to root, and often use a rootkit to keep their account.  Rootkits can provide backdoors, hiding and other nasty features.  A rootkit detector can detect many rootkits, but a well masked rootkit maybe impossible to find on a running system.  Boot a livecd and check for rootkits, and that should find all the rootkits.  DO NOT REBOOT IF YOU RUN A PRODUCTION SERVER AND WANT TO GATHER FORENSIC EVIDENCE.

Update When Possible
Keep your system updated, and an attacker will have a harder time getting.  Reading up on current security risks, helps avoid trouble too.

Small is Beautiful
The less services, and programs running on your system, the less places an attacker can attack.  Ideally ever system should serve only one purpose.

Be Paranoid
Security is a state of mind.  Using good security practice is one thing.  Being security minded is another.  Someone will want to break in at some point into our system.  Be skeptical of strange emails, website and programs.  Many attacks work by convincing you to let your guard down.

Backup
If worst comes to worst, a backup saves a lot of anguish.  Backup your files and system configuration files (/etc) regularly.

Overall
- Run only what you need.
- Be skeptical.
- Check logs, network traffic and signs of intrusion.
- Harden your system, keeping services to a minimum.
- Backup your files regularly.

More Advanced Techniques:
- Set up defences in depth.
- Firewalls to keep unwanted traffic from leaving.

---

### Post by aysiu on 2006-10-30
I've put in some links at the end of the page.

---

### Post by KaroSHi on 2006-10-30
Helpfull guide, thanks for the link! (i dont have any comments about it, v nice overall)

---

### Post by aysiu on 2006-10-30
> **KaroSHi said:**
> Helpfull guide, thanks for the link! (i dont have any comments about it, v nice overall)
Thanks. Good to know it's useful for someone.

Any security experts out there want to create a Wiki for advanced tips?

Mine's sort of a basic page.

---

### Post by user1397 on 2006-10-30
Very nice.  I suggest that in the part where you talk about sudo, to say that you have root access only in the terminal window open at the time fr 15 minutes from the time you first enter your password for a sudo command.  also of course applies to the gksudo nautilus window.

its different than your statment about 'sudo only gives root privileges to that command"  because it actually lasta for 15 minutes, though it is changeable.

---

### Post by aysiu on 2006-10-30
Yeah, I'll clarify a bit with that. Though, I've seen the behavior to not be fully consistent. Sometimes the 15 minutes lasts for only that terminal (if I open a new terminal, I'm prompted for a password again).

---

### Post by raqball on 2006-10-30
Great info on your site! A must for every new user! May I link this site in my sig?

Great job! :)

---

### Post by aysiu on 2006-10-30
> **raqball said:**
> Great info on your site! A must for every new user! May I link this site in my sig?

Great job! :)
Sure thing. Link away.

---

### Post by picpak on 2006-10-30
I guess here is as good as any.

Anyway, aysiu, on your Enabling Extra Repositories page ( [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) ), there's a typo. At the end it says

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo aptitude update
```

when it should say

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
sudo aptitude update
```

Just so that new users aren't confused.

---

### Post by prizrak on 2006-10-30
> **aysiu said:**
> Yeah, I'll clarify a bit with that. Though, I've seen the behavior to not be fully consistent. Sometimes the 15 minutes lasts for only that terminal (if I open a new terminal, I'm prompted for a password again).

Yeah that's how it works. If you open a terminal and sudo from inside of it the sudo only lasts for as long as the window is open. With gksu(do) it will be 15 minutes for any graphical app that needs the access. 

Overall very good article, it covers all the bases a user would need to know (especially in the Linux environment). As for your more advanced tips wiki, there is quite a bit of documentation around for those willing to learn so I don't think it would really be necessary. Your article should be wiki'd and put into Ubuntu installs though. 

I do remember that Seinfeld episode it was hilarious.

---

### Post by aysiu on 2006-10-30
> **picpak said:**
> I guess here is as good as any.

Anyway, aysiu, on your Enabling Extra Repositories page ( [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) ), there's a typo. At the end it says

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo aptitude update
```

when it should say

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
sudo aptitude update
```

Just so that new users aren't confused. Thanks for letting me know about this. It's fixed now.

---

### Post by ice60 on 2006-10-30
keeping everything up-to-date is important, and keeping an eye on recent exploits (but i'm not sure how easy that's suppose to be). 

it could have been very easy to miss the recent nvidia vulnerbility. 

i think you should keep an eye out for updates to programs you have installed yourself, especially things which have excess to the internet internet

---

### Post by gnomeuser on 2006-10-31
As for the question of is the security model in Ubuntu generally superior to Windows.

They have different strengths that don't overlap. The NTFS filesystem e.g. has additional access controls and the likes builtin (however to the best of my knowledge Microsoft don't actually use it). Their proactive security is also superior to what is presented in Ubuntu (Edgy brings us closer with ProPolice strack protection but the recommended platform is Dapper which has nothing of the sort). 

The strength with a UNIX system is that bottom up it's designed to be multiuser, we run default as a restricted user whereas in Windows they do currently offer this they give the default user administrator access. 
This effects the entire system as most software even if you can run as a restricted user will not work correctly or the user will be needlessly restricted and there's no easy way to escalate privilages to say install software. They haven't done the same kind of decade long education of software authors we have on the UNIX front, we only run what needs to be run as root or suid because in UNIX land it's basically a sin to run as a privilaged user whereas it's the standard in Windows. I have a great fear that Windows will never shake this tendency for idiocy.

I'd say we are slightly behind but we have potential to do them over in 6 month if we decide to since the technology is out there and it's well tested. The thing that saves us right now is the short time gap between discovery and fixes being pushed, this won't scale long term nor be enough to prove anything except complacency.

Backups, backups will not save you from security fixes, furthermore if you backup a system that's exploited you are screwed from the word go when you restore it. Backup have nothing to do with security, it's a dataloss safety measure, say if you accidently run rm -rf with the wrong parameter or something similar. Everyone should still do it though but not from some vain effort to stay secure.

---

### Post by aysiu on 2006-10-31
What you're saying makes sense if you're talking about files being **infected**, but what if you're talking about files being **deleted**?

I mention backing up only because of people saying things like these...

From [Linux vs. Windows Viruses](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/): > Further, due to the strong separation between normal users and the privileged root user, our Linux user would have to be running as root to really do any damage to the system. **He could damage his /home directory, but that's about it.** So the above steps now become the following: read, save, become root, give executable permissions, run. The more steps, the less likely a virus infection becomes, and certainly the less likely a catastrophically spreading virus becomes. And since Linux users are taught from the get-go to never run as root, and since Mac OS X doesn't even allow users to use the root account unless they first enable the option, it's obvious the likelihood of email-driven viruses and worms lessens on those platforms. From [Difference between Linux and Windows](http://www.thescripts.com/forum/thread536888.html) > So... in short. The reason viruses don't really exist on linux, is because most users don't run as a user with privaledges that could damage the system, therefore rendering any viruses useless. **The worst a virus in linux could do, is delete the users home directory contents** (akin to deleting your documents and settings folder). From [ Improve security on Feisty?](http://ubuntuforums.org/showthread.php?p=1683338#post1683338): > The music collection on my computer consists of .ogg file rips of the 150+ CDs that I own as well as files purchased from ITMS. It resides in a subdirectory of /home, which has its own partition on my largest hard drive.

The system files for my install of Edgy reside on my smallest hard drive on the / partition.

I can replace / with about 30 minutes spent to reinstall Edgy and another 20 minutes getting particular packages I like to use installed. To replace my music in /home would take me roughly two weeks, given that I'm not going to take off work to sit at my computer and feed it CDs 24/7, nor am I going to spend all weekend doing the same.

The personal cost to me of damage to /home/$(whoami) far far far outweighs damage done to /, even outright corruption of that partition forcing a full reinstall.

**Any application running with my permissions can happily rm -R /home/$(whoami)/Music && rm -R /home/$(whoami)/.Trash/*** For this reason, you bet your britches I'm interested in continued enhancements to security in Ubuntu.

For this reason, running the browser in a chroot jail environment is an appealing thought to me, since the web browser seems to be the largest attack vector currently available to an Ubuntu system being used as a home workstation.

But let's say I browse the web and find some great public domain or Creative Commons licensed tunes that I want to download and listen to at my leisure. I still want the browser to be able to save that file where I want in my ~. Saving to a quarantined directory that the chrooted browser has write access to and then later on dragging files around in Nautilus seems a real kludge. So which wins, my desire for convenience or for security?


---

### Post by jdong on 2006-10-31
It's absolutely correct that just limiting user privileges is not enough nowadays. Deleting, damaging, or uploading a user's data in his home directory can be just as fatal a security breach as handing out free root SSH logins.

The solutions to address this are already being researched in several distributions that employ SELinux or other fine-grained access control mechanisms, and will eventually make it to Ubuntu, too. Right now, they are often so restrictive that they affect the ability to do valid work.

---

### Post by GP_Fish on 2011-06-28
Thanks for the guide! All the links and software have been helpful to me in learning some linux security concepts and implementation. Good job! ^^

---

### Post by sydbat on 2011-06-28
> **GP_Fish said:**
> Thanks for the guide! All the links and software have been helpful to me in learning some linux security concepts and implementation. Good job! ^^Best. Thread. Necro. Ever.

---

