---
title: "Finding a keylogger on the network"
date: 2011-05-17
forum: Security
---

### Post by MGMorden on 2011-05-17
Hey guys.  I recently had both my iTunes account compromised and my Google Gmail account compromised.  The iTunes account resulted in some fraudulent charges that I was able to catch and have taken care of.  The Google account worries me more though as I had some sensitive documents on that account.  As a precaution I froze my credit reports with all 3 major agencies and have changed all passwords used for anything important.

Now, I think that these breaches are the result of a keylogger.  Problem is, I've got several systems I use fairly often.  2 Linux systems (laptop and main desktop), 2 Windows systems (1 virtual on the Linux desktop for iTunes, and 1 for gaming).  I've also got a Windows system at work.

At one time or another I've had iTunes on all the Windows systems - given that it was compromised I'm going to guess that one of the systems with iTunes has the keglogger on it, but a scan with ClamScan, Avast, Spybot, and Adaware have all turned up relatively empty - no keyloggers.  To be safe I also have scanned the Linux systems with chkrootkit and rkhunter.  

At this point I'm a bit paranoid to use any of the systems for anything until I identify which has the issue.  Is there anyway to setup a packet sniffer of some sort on my home LAN to search for a keyword that I could then type just in a file on each system, and then see which IP address sends any packets containing that keyword?

Thanks.

---

### Post by Kinstonian on 2011-05-17
> **MGMorden said:**
> Hey guys.  I recently had both my iTunes account compromised and my Google Gmail account compromised.  The iTunes account resulted in some fraudulent charges that I was able to catch and have taken care of.  The Google account worries me more though as I had some sensitive documents on that account.  As a precaution I froze my credit reports with all 3 major agencies and have changed all passwords used for anything important.

Now, I think that these breaches are the result of a keylogger.  Problem is, I've got several systems I use fairly often.  2 Linux systems (laptop and main desktop), 2 Windows systems (1 virtual on the Linux desktop for iTunes, and 1 for gaming).  I've also got a Windows system at work.

At one time or another I've had iTunes on all the Windows systems - given that it was compromised I'm going to guess that one of the systems with iTunes has the keglogger on it, but a scan with ClamScan, Avast, Spybot, and Adaware have all turned up relatively empty - no keyloggers.  To be safe I also have scanned the Linux systems with chkrootkit and rkhunter.

1.  Were your passwords strong?  Were the answers to the cognitive based questions used when you forget your password easy to guess?

2.  Did you use the same passwords?  How about similar passwords like gmail#$k6 and itunes#$k6?

3.  Did your iTunes password ever get sent to your Gmail account?  Could your Gmail account of gotten compromised and your iTunes password compromised or reset through Gmail?

4.  Did you fall victim to a phishing attack?

5.  Do you go to questionable sites or run questionable software that could install malware?

6.  Have you logged into those accounts over a wireless network?

7.  Did you ever log into those sites using an untrusted computer, such as one in a public place?

You could also try the free version of [Malwarebytes](http://www.malwarebytes.org/products).  However, anti-malware scans can make a good start for an investigation, but do not comprise of the whole investigation.


> 
At this point I'm a bit paranoid to use any of the systems for anything until I identify which has the issue.  Is there anyway to setup a packet sniffer of some sort on my home LAN to search for a keyword that I could then type just in a file on each system, and then see which IP address sends any packets containing that keyword?

Network monitoring can be another part of an investigation.  However, the malware (if it exists) could use a number of methods to exfiltrate data.  For one, it would probably be encrypted or encoded.  Perhaps also only logging when you go to a certain site, and then exfiltrated at a certain time of day.

You should probably find a Windows antivirus forum to continue the investigation because your incident probably didn't come from Ubuntu, and **maybe** it's not even related to Windows...

Good luck!

---

### Post by MGMorden on 2011-05-17
> **Kinstonian said:**
> 1.  Were your passwords strong?  Were the answers to the cognitive based questions used when you forget your password easy to guess?


The iTunes password was admittedly pretty weak.  Gmail was very strong (8+ characters of mixed upper/lower case and numbers).

> **Kinstonian said:**
> 
2.  Did you use the same passwords?  How about similar passwords like gmail#$k6 and itunes#$k6?


Nope, completely different passwords.

> **Kinstonian said:**
> 
3.  Did your iTunes password ever get sent to your Gmail account?  Could your Gmail account of gotten compromised and your iTunes password compromised or reset through Gmail?


Don't think so.  Also, the iTunes account was compromised first.  My first suspicuous login to Gmail occured last night.  The iTunes breach was about a week earlier.

> **Kinstonian said:**
> 
4.  Did you fall victim to a phishing attack?

Highly unlikely.  I'm incredibly careful about that.

> **Kinstonian said:**
> 
5.  Do you go to questionable sites or run questionable software that could install malware?


MOST of my web browsing is done on the Linux machine, but I'll admit I'm guility of popping open a web browser and browsing from the Windows machines sometimes.  I try not to go anywhere too shady, but I think this may have been the attack vector that got me.

> **Kinstonian said:**
> 
6.  Have you logged into those accounts over a wireless network?


That's a yes on the Gmail for sure, though the login is encrypted so I'm not sure a regular sniffer would have picked it up that way.

> **Kinstonian said:**
> 
7.  Did you ever log into those sites using an untrusted computer, such as one in a public place?


No.  I have quite a few devices that I use to access my info, but they're all either mine personally or devices that I control.

> **Kinstonian said:**
> 
You could also try the free version of [Malwarebytes](http://www.malwarebytes.org/products).  However, anti-malware scans can make a good start for an investigation, but do not comprise of the whole investigation.


Thanks.  I'll give that a shot.  None of the scanners I've used have picked up anything definite.


> **Kinstonian said:**
> 
Network monitoring can be another part of an investigation.  However, the malware (if it exists) could use a number of methods to exfiltrate data.  For one, it would probably be encrypted or encoded.  Perhaps also only logging when you go to a certain site, and then exfiltrated at a certain time of day.

You should probably find a Windows antivirus forum to continue the investigation because your incident probably didn't come from Ubuntu, and **maybe** it's not even related to Windows...

Good luck!

Thanks!

---

### Post by cprofitt on 2011-05-17
As a side note on passwords:

8 - 14 characters are pretty weak from the brute force standpoint. I personally am using 24-32 character passwords right now. I do know that some companies do not accept passwords of that length.

Also, from a rainbow table perspective being forced to use 'complexity' can actually make a password less secure due to limiting the size of the passwords.

---

### Post by Larkspur on 2011-05-17
> **MGMorden said:**
> At one time or another I've had iTunes on all the Windows systems - given that it was compromised I'm going to guess that one of the systems with iTunes has the keglogger on it, but a scan with ClamScan, Avast, Spybot, and Adaware have all turned up relatively empty - no keyloggers.

Have you scanned windows in Safe Mode?  The more tricky types of malware can hide themselves if they launch early on during boot.  With Safe Mode, chances are they can't launch, so can't hide.  Does Avast still have a pre-boot scan?  That would be useful as well.

---

### Post by HermanAB on 2011-05-18
ngrep

---

### Post by scorp123 on 2011-05-19
> **MGMorden said:**
>  Now, I think that these breaches are the result of a keylogger.  Could have been a hardware keylogger at work maybe? ... a "very dear friend" (sarcasm!) and business partner of mine once placed one of these diabolic things on each of my keyboards (with business partners like that you don't need enemies ...):

[http://www.keyghost.com/USB-Keylogger.htm#plug](http://www.keyghost.com/USB-Keylogger.htm#plug)
[http://www.keylogger.com/hkkeyboard.htm](http://www.keylogger.com/hkkeyboard.htm)
[http://www.keylogger.com/hkstandalone.htm](http://www.keylogger.com/hkstandalone.htm)

Those hardware keyloggers are totally invisible to any software scanner. There is only one way to find them: Check your PC cabling. And hope you don't find any odd-looking "USB thing" between your keyboard and your PC's USB port ... because that would most likely be a hardware keylogger!

This is what exactly happened to me once.

---

### Post by COMPUTIAC on 2011-05-19
Hello, Avast doe's have the boot scan.  When you open the program > click on scan computer > click on Boot-time scan > click on schedule now > reboot or restart the machine and before anything else, Avast will scan.

---

### Post by emiller12345 on 2011-05-19
Originally Posted by Kinstonian View Post
6. Have you logged into those accounts over a wireless network?
That's a yes on the Gmail for sure, though the login is encrypted so I'm not sure a regular sniffer would have picked it up that way.

I would double check this. If its https, make sure that the HTTP cookies are also incrypted. Things like firesheep can be a real nuance. If you had your cookies hijacked, that means access to you email, though not your password directly. I'd stay away from open wifi hotstops

---

