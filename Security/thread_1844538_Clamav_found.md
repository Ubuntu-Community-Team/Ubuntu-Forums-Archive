---
title: "Clamav found"
date: 2011-09-15
forum: Security
---

### Post by cssutto on 2011-09-15
I am running Ubuntu 10.4 dual boot with windoze XP.  I m forced to do this because I have two serious requirements for which there is no linux software.

The machine is a Thinkpad manufactured by Lenovo.

Yesterday I updated clamav using synaptic to 0.97.2.

clamav runs every night and this morning I had the following:

/media/Preload/Program Files/ATI Technologies/ATI HYDRAVISION/HydraWizard.exe: Trojan.Agent-193172 FOUND

chkrootkit does not find it.

rkhunter runs every night also and reported nothing.

So is this real or a false positive?

If it is real, what is the fix?

---

### Post by haqking on 2011-09-15
> **cssutto said:**
> I am running Ubuntu 10.4 dual boot with windoze XP.  I m forced to do this because I have two serious requirements for which there is no linux software.

The machine is a Thinkpad manufactured by Lenovo.

Yesterday I updated clamav using synaptic to 0.97.2.

clamav runs every night and this morning I had the following:

/media/Preload/Program Files/ATI Technologies/ATI HYDRAVISION/HydraWizard.exe: Trojan.Agent-193172 FOUND

chkrootkit does not find it.

rkhunter runs every night also and reported nothing.

So is this real or a false positive?

If it is real, what is the fix?

Likely to be a false positive, it is a .exe used by ATI hrydravision.

Not to say it is not a trojan version of the legit, but it wont effect your Linux machine.

---

### Post by cssutto on 2011-09-15
Thanks.

I suspected as much but really did not know.

I never send emails or send information by attachments with windoze, so it should not affect anyone else.

Thanks again.

---

### Post by Johnny3 on 2011-09-15
Can you find it in the file /media/Preload/Program Files/ATI Technologies/ATI HYDRAVISION/HydraWizard.exe:? This is from a newbe so just back up and delete it if it is there. Looks like it mite be for your video card.
God Bless Johnny3

---

### Post by cssutto on 2011-09-15
I can get down to HydraWizard.exe but I can't read it and if I could I would not be able to identify a trojan.

---

### Post by haqking on 2011-09-15
> **cssutto said:**
> I can get down to HydraWizard.exe but I can't read it and if I could I would not be able to identify a trojan.


it exists because you have a ATI card and using hydravision in your windows system correct ?

like i said false positive and if it isnt no need to worry as it is a .exe and wont effect linux

---

### Post by cssutto on 2011-09-15
> **haqking said:**
> it exists because you have a ATI card and using hydravision in your windows system correct ?

like i said false positive and if it isnt no need to worry as it is a .exe and wont effect linux

I understand that and I thank you.

I was only posting a polite reply to the question rather than ignoring it.

There were quite a few other hits that I did not mention and after your post I looked more carefully at them and determined that all of them were windoze items.

Since I despise windoze it is not that much of a concern.

---

### Post by haqking on 2011-09-15
> **cssutto said:**
> I understand that and I thank you.

I was only posting a polite reply to the question rather than ignoring it.

There were quite a few other hits that I did not mention and after your post I looked more carefully at them and determined that all of them were windoze items.

Since I despise windoze it is not that much of a concern.

no worries, as a primer on Linux and Virus and security in general then:

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

[B]See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)[/B]

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by Lars Noodén on 2011-09-16
> **cssutto said:**
> I m forced to do this because I have two serious requirements for which there is no linux software.


Just to go on a bit of a tangent, but have you tried [WINE](https://help.ubuntu.com/community/Wine) with those apps?  Using WINE would eliminate the need for the legacy OS and grant immunity to the viruses.

---

### Post by haqking on 2011-09-16
> **Lars Noodén said:**
> Just to go on a bit of a tangent, but have you tried [WINE]("https://help.ubuntu.com/community/Wine") with those apps?  Using WINE would eliminate the need for the legacy OS and grant immunity to the viruses.

having the virus or infected file in Wine or in a true Windows partition makes no difference ?

it is still an infected file and not likely to infect Linux in anyways, running infected software in Wine does not circumvent the infected file, apart from possibly infecting the Wine environment and seeing as his /home would be mounted in Wine and not in his Dual boot config.

Or perhaps i dont understand what you are saying, it sounds like you mean if run the app in Wine then the virus wouldnt matter if it existed or not ?

---

### Post by Frogs Hair on 2011-09-16
I used Clamav when I first started with Ubuntu and any  file Clam could not scan showed up as a positive .  That included everything except the home folder .  Be cautious with clam . from what I can find you have a false positive .

---

### Post by cssutto on 2011-09-16
> **Frogs Hair said:**
> I used Clamav when I first started with Ubuntu and any  file Clam could not scan showed up as a positive .  That included everything except the home folder .  Be cautious with clam . from what I can find you have a false positive .

Thanks.

As I noted all reported files are windoze files.

I have also noted this:  ATI Technologies/ATI HYDRAVISION/HydraWizard.exe 

is in the preload directory that resides on one of my linux partitions and is of course available when linux is running.

I have just started reading up on how to clean that directory but have not yet learned enough to be of any practical value.

I can't see any reason for the ATF Technologies file to be on the linux partition unless it is part of the dual boot startup.

The preload directory has about every file in it I ever heard of from my photos to the entire boot system for windoze.

I would like to zap the whole thing but at this point I don't understand the ramifications other than it is supposed to speed up directory searches while loading.

Any comments would be appreciated.

---

