---
title: "Does chkrootkit security scanner give false alarm?"
date: 2010-07-11
forum: Security
---

### Post by wacky_sung on 2010-07-11
I been using chkrootkit security scanner for quite some time and this is my first time got an suspicious directory / files.I just ponder is this a false alarm as i have scanned those directory with clamtk without any issues.

in additional,i have installed both firefox and google chrome,while those suspicious directory found come within the browsers.Probably somebody can enlighten me please.Thank.

[[IMG]http://img708.imageshack.us/img708/2330/screenshotubuntusoftwar.th.png[/IMG]]("http://img708.imageshack.us/i/screenshotubuntusoftwar.png/")

[[IMG]http://img535.imageshack.us/img535/2336/screenshotrootalexlapto.th.png[/IMG]]("http://img535.imageshack.us/i/screenshotrootalexlapto.png/")

---

### Post by cariboo on 2010-07-11
Ideally you should scan a fresh install, and keep a record of the results, that way you can compare results with later scans.

To answer your question, chkrootkit can and does come up with false positives.

---

### Post by Bachstelze on 2010-07-11
> **cariboo907 said:**
> 
To answer your question, chkrootkit can and does come up with false positives.

Actually, judging by the number of alarmed messages we get here, false positives make for a large majority of chkrootkit alerts, to the point that one could question its usefulness.

---

### Post by wacky_sung on 2010-07-11
Actually i did a fresh installation of firefox & google chrome(both without any upgrading).The issue is that it did not prompt during my initial installation of Ubuntu 10.04 luci when i started using it months back.How shall i do about? Uninstall both browsers and scan again?If found nothing,then installed back both firefox and google chrome and scan again?Shall i just simply ignore it as recommended?

---

### Post by Rubi1200 on 2010-07-11
> **wacky_sung said:**
> Shall i just simply ignore it as recommended?

Neither cariboo907 or Bachstelze recommended that you ignore the warning!

What they said was that tools like chkrootkit can, and do, produce false positives.

You know your system better than anyone else. 

It is **your** responsibility to check these warnings and determine whether there is a security issue or not.

From bodhi.zazen's security sticky on chkrootkit:

>  As with all these tools false positives are common, use Google to search for suspicious results.

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)

---

### Post by wacky_sung on 2010-07-11
Thank you all for the help.Much appreciated.

---

### Post by bodhi.zazen on 2010-07-11
> **Bachstelze said:**
> Actually, judging by the number of alarmed messages we get here, false positives make for a large majority of chkrootkit alerts, to the point that one could question its usefulness.

Neither rkhunter or chkrootkit are of any value unless :

1. The first scan is performed on a known good installation. If you are running these tools for the first time because you suspect your system may have been cracked, it is too late (unless you are very familiar with these tools and your system, but those people do not ask questions here ... ).

2. You are willing to do the footwork necessary to interpret the results. This includes reading the documentation, performing google searches of the results, and looking into the results until you understand what they mean.

If you google search any of the warnings or "false positives" you will find your answer, although finding your answer may include learning a bit more about your system.

If you are not willing to put in the time, you should not be running these tools, the results are meaningless if yo do not follow through.

Most people who put in the time stop using these tools, primarily due to the number of false positives, but also because there are better tools available (snort, ossec, OpenVAS, nmap, etc )

---

### Post by Vimmander on 2010-07-15
I think the ubuntu restricted extras (either the entire package or just parts of it being installed as needed, like Java) is what's throwing false positives out there because of where it's contents are installed.  From what I've read on the forums, having a strong password, only installing from the repositories (via Synaptic), being aware of social engineering, and keeping track of the things your doing during a session so that when the system prompts you for your password, you KNOW what it's for are the best things you can do to ensure the safety of your system.  My CS professor has used Ubuntu for quite a while, has NO special settings via iptables or ufw, I assume he only installs from the repositories, and he's never had a problem.

Knowing what's going on when your using ANY operating system is a key part in preventing malicious programs from being installed.

Someone wanna tell me if I'm wrong?

> 1. The first scan is performed on a known good installation.

In fact, this is a good test for me to do.  I have just reinstalled Ubuntu 10.04, and before I get any updates, download restricted extras or Vim, and even before I download the two drivers for my wireless card, I'm going to download chrootkit (sp?) and rkhunter, run both, and email a txt file to myself of the results to compare to future runs.  Would that suffice as a good installation with the knowledge that the LiveUSB is clean and safe, Bodhi.zazen?

---

### Post by bodhi.zazen on 2010-07-15
> **GrogTheDreamer said:**
> Would that suffice as a good installation with the knowledge that the LiveUSB is clean and safe, Bodhi.zazen?

That would suffice, IMO.

For the truly paranoid, disable (unplug) your network card during the installation and confirm the md5sum of the install media.

---

### Post by Vimmander on 2010-07-15
> **bodhi.zazen said:**
> That would suffice, IMO.

For the truly paranoid, disable (unplug) your network card during the installation and confirm the md5sum of the install media.

Where would this be displayed in the LiveUSB/Install session?

---

### Post by bodhi.zazen on 2010-07-15
> **GrogTheDreamer said:**
> Where would this be displayed in the LiveUSB/Install session?

Where would what be displayed ?

---

### Post by Vimmander on 2010-07-15
> **bodhi.zazen said:**
> Where would what be displayed ?

The md5sum

---

### Post by bodhi.zazen on 2010-07-15
> **GrogTheDreamer said:**
> The md5sum

The md5sums are posted:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You can check the iso before you burn it

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

When you boot the CD, one of the options is to check the integrity of the disk.

And , last, the md5sum is also on the disk itself, if you browse the contents.

---

### Post by Vimmander on 2010-07-15
Well, that other verifying stuff is way over my head, but I checked the LiveUSB's md5sum.txt file, and the md5sum for ubuntu-10.04-desktop-i386.iso, my iso on my flash drive, wasn't there.  A bunch of others were, though.

---

### Post by libssd on 2010-08-14
I've been pretty casual about security, but just ran chkrootkit for the first time. The following look like false positives to me, but just looking for confirmation:


Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  

/usr/lib/pymodules/python2.6/.path 
/usr/lib/firefox-3.6.8/.autoreg 
/usr/lib/jvm/.java-6-sun.jinfo 
/usr/lib/jvm/java-6-sun-1.6.0.20/.systemPrefs 
/usr/lib/jvm/.java-6-openjdk.jinfo 
/usr/lib/xulrunner-1.9.2.8/.autoreg

---

### Post by cariboo on 2010-08-14
As has been posted several time, those are false positives, the dates on the files correspond to when they were updated last on my system.

---

### Post by OpSecShellshock on 2010-08-14
You need to establish a baseline on a known-clean system first in order for results from rootkit detection software to have much value.  Presuming that your system was not showing signs of suspicious activity prior to your having run the check, you should now have a "good-enough" baseline. The only way I can think of to do better than good enough would be to reinstall and then run it (and to be really sure, run it before you restore the backup of your home directory).

---

