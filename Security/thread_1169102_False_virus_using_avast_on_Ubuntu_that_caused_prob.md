---
title: "False virus using avast on Ubuntu that caused problems with vista"
date: 2009-05-24
forum: Security
---

### Post by Ubersci on 2009-05-24
I have Vista on my first HDD and Ubuntu on my 2nd, does anyone know how to stop any direct access by both, so virus that are picked up ubuntu are not spread to vista. I also tried Avast virus scanner and it caused problems with vista by detecting a false positive and removing it.

Also i tried to install mcafee siteadvisor on ubuntu but it does'nt seem to work any help please with both.

p.s. I'am very new to ubuntu.

---

### Post by The Tronyx on 2009-05-25
Any kind of infection you encounter using Ubuntu is more likely than not, not going to mess with your Vista partition/drive.  The kinds of viruses, trojans and malware which are all designed for Windows will not be handled or executed the same way on Ubuntu **if** they will be executed at all.

Since the stickies love to be ignored, from [http://ubuntuforums.org/showthread.php?t=510812:](http://ubuntuforums.org/showthread.php?t=510812:)

> 
Viruses

The fact of the matter is: viruses/worms take advantage of flaws or holes in the code. At this time of this writing, there are no significant Linux viruses "in the wild". Linux boxes are no less targets than any other OS, many of the large (ie valuable) Internet sites run on *nix so there is no lack of motivation to crack into *nix.

Do not believe the suggestion that the Linux community is complacent or "behind the times" in terms of viruses, or any other security issue. Linux developers have not "ignored" viruses, rather the OS is built to be highly resistant to them and since the code is "Open" there are literally thousands of eyes watching ...

This is an example of what it would take to install malware on an Ubuntu box :

Install evilmalware

(Don't worry, that link will NOT install anything )

For the most part, Linux anti-virus programs scan for Windows viruses which do not run on Linux. There are increasing reports, however, that Windows malware may run in wine, as such I added a section reviewing what I feel you should know about security if you choose to install and run wine (see below).

Please understand, anti-virus programs, and in fact most HIDS, are "reactive" in that they can only protect you from known viruses. They can only protect you against malware after it is developed and incroporated into HIDS, not before. Furthermore the "fix" will be to close any hole(s) in the code, these fixes will be available through security updates (which are more frequent in Linux then your previous OS if you are coming from Windows).

Reasons AGAINST antivirus on Ubuntu:

   1. They scan primarily for Windows viruses.
   2. There is a high rate of false positives.
   3. Isolation/inoculation is poor.
   4. And currently there are no known active Linux viruses (so there is essentially nothing to detect).


Reasons FOR antivirus on Ubuntu:

    * You are running a file or mail server with Windows clients.
    * You wish to scan files before transferring them, by email, flash drive, etc., to a Windows machine.


Running antivirus can make some sense if you are intending to "protect" Windows users, however, IMO, for a variety of reasons, it is best if Windows users learn to protect themselves.

Note: There have been many documented cases in Windows and Linux that a buffer overflow in an antivirus product has been an attack vector!

If you would like to run an antivirus program on Ubuntu you have several choices :

    * Antivirus
    * ClamAV
    * [http://www.avast.com/eng/avast-for-l...rkstation.html](http://www.avast.com/eng/avast-for-l...rkstation.html)
    * [http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)
    * [http://www.centralcommand.com/linux_server.html](http://www.centralcommand.com/linux_server.html)
    * [http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)


A few comments on wine

Discussions about running Windows viruses on wine crop up from time to time and it is possible to run some Windows viruses on wine.

See these links :

    * McAfee Avert Labs Blog
    * Running Windows viruses in wine


So what do you need to know about Windows viruses if you want to run wine?

1. First, the "golden rule" : DO NOT RUN WINE AS ROOT. If you are NOT running wine as root then wine will not have the necessary permissions to affect system files.

2. So, if you are running wine as a user, a Windows virus will be confined to your home directory.

3. You can further confine the "fake c drive" located at ~/.wine if you remove any symbolic links outside ~/.wine. With a default installation there is link with a default installation / configuration of wine :

    * ~/.wine/dosdevices/z: -> links to /


A link from ~/.wine/dosdevices to the root directory ( / ) should concern you for obvious reasons.

You can remove it with :

Code:

unlink ~/.wine/dosdevices/z:

Do not worry, that command will not affect wine at all, I run it all the time

You may need to make a link in ~/.wine/dosdevices to your cdrom and/or you may be tempted to link to your home directory, but I advise against keeping using these links (beyond the time needed for actually installing applications).

I advise against any links to removable devices (it should not be *that* difficult to copy files needed to the appropriate location in ~/.wine/drive_c ).

4. Consider running an antivirus program and scanning ~/.wine and any removable devices or other locations you use outside of ~/.wine to store programs or data to be used with wine. Scan any data / applications you use with Windows.

5. Consider confining wine with Apparmor.

6. Be sure to file a bug report with the wine project as they have a very active security team (it is unrealistic, however, to expect the wine team to be able to protect you from all Windows viruses all the time). Wine Bug Reports

7. Take the same precautions with wine as you would with Windows. Do not install untrusted applications from untrusted sources.

If you follow the above advice, Windows viruses will be confined to ~/.wine and they do not have permission to change system files. This means to remove them you simply:

Code:

rm -rf ~/.wine

Please take care, this command deletes everything in your wine directory including all data and all applications.

You then need to restore your wine directory from a known good backup (you do keep backups ?).


---

