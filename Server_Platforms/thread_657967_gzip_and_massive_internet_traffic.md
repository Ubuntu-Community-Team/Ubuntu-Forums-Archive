---
title: "gzip and massive internet traffic"
date: 2008-01-04
forum: Server Platforms
---

### Post by ihatethatguy on 2008-01-04
I just happaned to wake up to go to the bathrrom last night and had a mind to check the results in iowa when i noticed that there was a lot of network activity.

Long story short, it was gzip, running as root, the final count of things that were uploaded/downloaded was about 2.5gb/7.5 gb, though i had spent the entire evening watching video off of the network, so i suspect that th number is much smaller than that.

The only think that i can think of that might cause this is that i downloaded a game from a link at linux-gamers.net which led me here.

[http://cor.planetquake.gamespy.com/omen/download.html](http://cor.planetquake.gamespy.com/omen/download.html)

to a .run file that i had tried to install, but for some reason never did.

I do spend a certain amount of time on less reputable sites, but i have noscript and addblock both installed, though i suppose that it is possible to get something from an infected .rar

I run guarddog, and do have clam installed, and the network computer that i had been using showed no signs 

Several questions that i have:


1: Does gzip always run as root, and if not, why would it be now.

2: I know that linux by nature is not prone to virii or most malware, but with root access, gzip could have easily injected a script or keylogger or something into my system, is there any way to check?  I checked the system logs and everything seemed fine, but i am fairly new to linux, so im not sure that i would know what i am looking for.

3: i have data sitting on another partition that was ntfs, if i were to reinstall the os, what are the chances that those files would be infected as well....i think this time around i am going to use lvm encryption.

---

### Post by ihatethatguy on 2008-01-04
it should also be noted that i my network is behind smoothwall with no extra ports forwarded.

Another question:  is it just coincidental that when i killed gzip that the internet activity stopped, or was there perhaps some reason that it was accessing the internet?  I am not sure how long it was going, but there was full activity on system monitor so it must have been at least two minutes....


thanks again.

---

### Post by cdenley on 2008-01-04
I'm no expert, but I think it sounds like something running on your machine was compressing files to send somewhere over the network or internet. That amount of upload traffic sounds unusually high unless your were uploading large files or running a server. Since it was running as root, it was probably started by something you ran as root, possibly the .run file you mentioned. The fact that you mentioned it seemed to fail to install sounds suspicious. If you run software from someone you can't trust, especially as root, then all the security in the world isn't going to help you.

Gzip will run under whatever account you start it as. "sudo gzip myfile" will run as root. Since you probably don't have any Linux software on your ntfs partition, I wouldn't worry too much about Linux viruses. I suppose it could have infected your windows install, assuming there is one, but who would hack a Linux system to infect a possibly unused windows partition? Are you sure you're not running any scheduled backup software or scripts?

---

### Post by Maxtorm on 2008-01-04
> **ihatethatguy said:**
> 2: I know that linux by nature is not prone to virii or most malware, but with root access, gzip could have easily injected a script or keylogger or something into my system, is there any way to check?  I checked the system logs and everything seemed fine, but i am fairly new to linux, so im not sure that i would know what i am looking for. Rootkit Hunter does a decent job. ```
apt-get install rkhunter
```

---

### Post by ihatethatguy on 2008-01-04
I think that i can reasonably be sure that i can trust gamespy and linux-gamers, i had a thought; i think that that i have updates set to download and install automatically, which would, i would think, spawn a copy of gzip as root....maybe not.

The owner of the file in question that i ran was just a user, not root, and was ran in a terminal, as that user, which is likely why it never installed, now that i think on it.

Checking for enabled inetd services             [ Warning ]
[13:40:33] Warning: Found enabled inetd service: ident

 Info: Starting test name 'startup_files'
[13:40:43]   Checking for local host name                    [ Found ]
[13:40:44] Info: Starting test name 'startup_malware'
[13:40:44] Info: Found local startup file: /etc/rc.local
[13:40:44]   Checking for local startup files                [ Found ]

 Info: Starting test name 'group_accounts'
[13:40:45]   Checking for passwd file                        [ Found ]

  Checking for hidden files and directories       [ Warning ]
[13:40:59] Warning: Hidden directory found: /etc/.java
[13:40:59] Warning: Hidden directory found: /dev/.static
[13:40:59] Warning: Hidden directory found: /dev/.udev
[13:40:59] Warning: Hidden directory found: /dev/.initramfs
[13:40:59] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)

if someone could provide some help in interpreting this, that would be most appreciated...
looking at this, as well as the summary, it seesm that everything is is pretty much status quo

[13:41:00] File properties checks...
[13:41:00] Files checked: 126
[13:41:00] Suspect files: 0
[13:41:00]
[13:41:00] Rootkit checks...
[13:41:00] Rootkits checked : 109
[13:41:00] Possible rootkits: 0
[13:41:00]
[13:41:00] Applications checks...
[13:41:00] Applications checked: 3
[13:41:00] Suspect applications: 0


I think that the upload/download ratio is misleading since i watched several gb over the network, as well as doing some browsing and various online stuff...


Is there a logfile generated by the system update process that tells exactly when it was doing something and what?  If my suspicions are correct, it might have just been normal background updating. since i should not have run anything in root that would have spawned a rooted gzip....i did install a bunch of stuff via synaptic and "add/remove programs".

---

### Post by ihatethatguy on 2008-01-08
I think that i have it figured out....

I installed a backup utility and just left it at the default settings.  It just so happens that one of the directories that it is supposed to backup also houses mounted network drives.  I figured this out when i found that i was out of hard drive space and had to go searchign to find the reason.  A ton of data was in the backup directory.

Long story short, there was not breach of security that i could find, and i just made a mistake, problem solved.

---

