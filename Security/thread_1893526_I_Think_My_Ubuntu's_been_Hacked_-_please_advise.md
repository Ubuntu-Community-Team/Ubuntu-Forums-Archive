---
title: "I Think My Ubuntu's been Hacked - please advise"
date: 2011-12-10
forum: Security
---

### Post by Marcus Aurelius on 2011-12-10
Hello,

I probably should have made the title, my windows 7 has been hacked since this is a dual boot issue.  I have a HP pavilion dv4 laptop running windows 7 64-bit and is dual boot with Ubuntu 11.04. The situation is about two months ago I had some printer/scanner problems and found permissions reset, and after scanning found a root kit in windows 7.  I had image backups of my system on an external drive, and knew the right thing to do was to wipe hard drive & restore clean OS backup.  However, I had never trouble shot nor hunted down a root kit issue before and wanted to play around with it.  I cleaned the root kit and knew it was unsafe but rolled with it anyway to see if it was really clean.  It appeared that Windows 7 was the only part of the system that was affected.  I could see no negative affects on the Ubuntu side.  I wondered for the longest time why an attacker would not have destroyed the Ubuntu side?  So two months later, I found that Windows 7 had a root kit again. I assume that whatever vulnerability was exploited to begin with (and was not hardened) was exploited again.  I cleaned the root kit, but a few days later I scanned again and found a trojan.  All this is in windows 7.  Then even after cleaning these all out, when I'd boot into Ubuntu, the computer would run for a while in a power mode similar to when the battery on the laptop is about to die when unplugged.  Then it would just shut off.  However, these symptoms were occurring while the laptop was plugged into the wall.  Therefore, I am attributing the bizarre symptoms in Ubuntu to a virus or trojan or rootkit issue.  Additionally, the password in Windows 7 and Ubuntu were both changed, so I could no longer gain access.  I can access the files however if I take the hard drive out of the laptop and plug it into my SATA HDD esata and USB docking station.  

My questions are:
From the perspective of the cracker, how do you explain this attack from their view point.  How was it carried out?  ie.  Once they attacked windows did they have 100% access to Ubuntu?  Did my dual boot scenario make Ubuntu easier for them to exploit?  If windows was not on the system, would Ubuntu have been more secure?  Ubuntu had its home folder encrypted from install.  Do you see these as advanced crackers who did this?  What kind of a mind set it this. Tell me all you can as I'm curious about these attacks.  Are they happening for some cracking sport or is this a criminal enterprise interested in using my computer as a zombie?  Performance seemed as normal as usual except for the permissions reset.

Thanks.

---

### Post by CharlesA on 2011-12-10
How did you know you had a rootkit in the first place?

Having the machine act like it is running on a dying battery points to a hardware problem, not a trojan or rootkit. The two OS installs are separate, meaning you wouldn't have access to Ubuntu from Windows and vice verse.

---

### Post by Thewhistlingwind on 2011-12-10
> **CharlesA said:**
> The two OS installs are separate, meaning you wouldn't have access to Ubuntu from Windows and vice verse.


Not necessarily, you can mount unencrypted partitions belonging to one OS from the other. This lets you write to these partitions with impunity, these partitions usually include system files.

A very targeted attack could get write privileges on one OS, then install the malware on the other, once you boot the other, the malware infects the first OS.

Of course, doing this attack on windows would require a little more effort, because it has no native EXT support.

---

### Post by CharlesA on 2011-12-10
> **Thewhistlingwind said:**
> 
Of course, doing this attack on windows would require a little more effort, because it has no native EXT support.

That's what I was thinking. You can't really access an EXT file system from Windows without installing a third party driver first.

---

### Post by Thewhistlingwind on 2011-12-10
> **CharlesA said:**
> That's what I was thinking. You can't really access an EXT file system from Windows without installing a third party driver first.

Of course, most windows users use the administrator account. Meaning that write privileges imply write privileges to the system files. One could install an EXT driver from an ftp server and proceed with the rest.

---

### Post by Dangertux on 2011-12-10
> **Marcus Aurelius said:**
> Hello,

I probably should have made the title, my windows 7 has been hacked since this is a dual boot issue.  I have a HP pavilion dv4 laptop running windows 7 64-bit and is dual boot with Ubuntu 11.04. The situation is about two months ago I had some printer/scanner problems and found permissions reset, and after scanning found a root kit in windows 7.  I had image backups of my system on an external drive, and knew the right thing to do was to wipe hard drive & restore clean OS backup.  However, I had never trouble shot nor hunted down a root kit issue before and wanted to play around with it.  I cleaned the root kit and knew it was unsafe but rolled with it anyway to see if it was really clean.  It appeared that Windows 7 was the only part of the system that was affected.  I could see no negative affects on the Ubuntu side.  I wondered for the longest time why an attacker would not have destroyed the Ubuntu side?  So two months later, I found that Windows 7 had a root kit again. I assume that whatever vulnerability was exploited to begin with (and was not hardened) was exploited again.  I cleaned the root kit, but a few days later I scanned again and found a trojan.  All this is in windows 7.  Then even after cleaning these all out, when I'd boot into Ubuntu, the computer would run for a while in a power mode similar to when the battery on the laptop is about to die when unplugged.  Then it would just shut off.  However, these symptoms were occurring while the laptop was plugged into the wall.  Therefore, I am attributing the bizarre symptoms in Ubuntu to a virus or trojan or rootkit issue.  Additionally, the password in Windows 7 and Ubuntu were both changed, so I could no longer gain access.  I can access the files however if I take the hard drive out of the laptop and plug it into my SATA HDD esata and USB docking station.  

My questions are:
From the perspective of the cracker, how do you explain this attack from their view point.  How was it carried out?  ie.  Once they attacked windows did they have 100% access to Ubuntu?  Did my dual boot scenario make Ubuntu easier for them to exploit?  If windows was not on the system, would Ubuntu have been more secure?  Ubuntu had its home folder encrypted from install.  Do you see these as advanced crackers who did this?  What kind of a mind set it this. Tell me all you can as I'm curious about these attacks.  Are they happening for some cracking sport or is this a criminal enterprise interested in using my computer as a zombie?  Performance seemed as normal as usual except for the permissions reset.

Thanks.

Personally, not to discredit your experience (which you admitted was lacking in these matters). I think you're experiencing a comedy of errors. Your Windows install picked up some malware, you detected it, then your hardware started failing and you picked up more malware in the interim.

I honestly don't think you're being targeted and persecuted by a malicious attacker(s). While it is possible to cross platform root a system it is indeed an unlikely scenario, and even less likely that someone took the specific time to target a home system in this manner. Let's be realistic, you were probably compromised through your browser or a file you downloaded. By the time someone set up a crack like what you're talking about they could have owned ten's of thousands of additional systems with little to no effort. Botnets are populated quickly, utilizing common browser and other application flaws. There is no need to dig yourself into a system that is just going to be sitting on a botnet, as you said you clean the malware today, it's back tomorrow.

You may have even re-rooted yourself if you were playing with the malware you obtained, also -- you may not have fully removed it in the first place.

As far as the passwords changing while that is certainly suspicous that's not root kit like activity, a rootkit is exactly that, it hooks the kernel in such a way that changing your password is an irellevancy, it doesn't need your password. Are you the only person who has physical access to this machine? If not do you trust everyone that does?

Hope this helps.

---

### Post by Thewhistlingwind on 2011-12-10
> **Dangertux said:**
> Personally, not to discredit your experience (which you admitted was lacking in these matters). I think you're experiencing a comedy of errors. Your Windows install picked up some malware, you detected it, then your hardware started failing and you picked up more malware in the interim.

I honestly don't think you're being targeted and persecuted by a malicious attacker(s). While it is possible to cross platform root a system it is indeed an unlikely scenario, and even less likely that someone took the specific time to target a home system in this manner. Let's be realistic, you were probably compromised through your browser or a file you downloaded. By the time someone set up a crack like what you're talking about they could have owned ten's of thousands of additional systems with little to no effort. Botnets are populated quickly, utilizing common browser and other application flaws. There is no need to dig yourself into a system that is just going to be sitting on a botnet, as you said you clean the malware today, it's back tomorrow.

You may have even re-rooted yourself if you were playing with the malware you obtained, also -- you may not have fully removed it in the first place.

Hope this helps.

I never did comment on your specific case. I agree with this. The chances that you received an attack like my theoretical approach are slim and none.

---

### Post by CharlesA on 2011-12-10
> **Thewhistlingwind said:**
> Of course, most windows users use the administrator account. Meaning that write privileges imply write privileges to the system files. One could install an EXT driver from an ftp server and proceed with the rest.
Valid point. I was thinking that maybe UAC would have notified the user of something requiring escalated privileges.

---

### Post by mr-woof on 2011-12-11
As said above, it's very difficult to infect the ubuntu os from windows because of the lack of ext support in Windows. Out of interest, what anti-virus, anti-malware do you use on Windows7? What did you use to detect the trojan?

---

### Post by breimer273 on 2011-12-12
Although I am not an expert in this area, this is my area of study in school. I do agree that this is not rootkit behavior as rootkits already have elevated privileges and do their best not to loose the elevation. I suppose it could be characteristic of a trojan but then again, trojan are disguised in legitimate programs and you the user would have given it elevated privileges when you executed the compromised program. Not too sure about the whole one OS compromising the other but the lack of ext support makes sense in my mind.

If you were asking for my opinion I would say that the issues are not necessarily related and if you feel that you have fallen victim to two separate rootkits (although without a clean OS install you can't be sure it was two separate times) and a trojan I would question your security habits. Do you have a firewall on Windows other than the default firewall, what AV software do you use? Did you recently download and programs, PDFs, emails from interesting places? Lots of things could have caused this and honestly it was probably something that you did to initiate the infection, I'm not trying to make you sound stupid or anything but I would say that most attacks on personal computers are not very directed, as in an attacker would send out thousands of phishing emails in hopes that maybe a 100 people would actually bite and get infected. Then he could use those computers either for a larger attack else where or somehow get that users money.

Again, I am not an expert but I have been studying computer security for three years for my degree. I guess I want you to just take away that I think you're thinking in to it too much and that the problems are most likely unrelated, like everyone else has already said.

---

### Post by Marcus Aurelius on 2011-12-13
Thank you for all the considerate posts.  You were all right in your replies.  It was an amalgam of separate issues.  

ISSUE #1: (Recurrent rootkit issue)

The gist of how I tackled that is below.  I used 95% of these successfully.  I can't remember which ones didn't work.  I think black light was discontinued.  Maybe DDS or OTL I didn't understand the log it printed out.  But the rest I used successfully:

I cleaned up with CCleaner, then MBAM, Dr. Web Cure It, ComboFix, I used a Kaspersky Live CD AV disk, then after pulled out my HD and scanned it in external esata USB docking station,        SFC, trend micro scan actually found the root kit.  Tried f-secure black light, sophos anti-root kit, stinger, helios, gmer, rootkit revealer, unhackme.  Sent weird files one by one to virustotal.com, ran DDS, OTL Old timers list. Avast, Avira, Eset online scanner, bit defender, panda security, spybot search and destroy, I removed a bunch of 6 to 4 adapters, and tunnel adapters which were a result of the malware.

ISSUE #2: Dual boot issue...

I was never "SURE" ubuntu was affected.  The weird battery thing was odd. I removed the RAM and replaced them again and got it to kick back on.  It didn't charge in ubuntu but I booted into 7 and charged the battery.  I think my recent upgrade to Ubuntu 11.10 has some problem charging the battery. It's still not charging properly. It drains down and then shuts my computer off.  Really weird.  I haven't found a fix for that yet.  I was curious about the risk to the dual boot setup.  Incidentally I have a separate  partition in FAT32 format unencrypted which both the win7 and ubuntu OS's share.  I can read files in win7 from ubuntu, but not the other way around with ext4 as people said this makes it hard to attack both, and the effort to do so would make a target attack on a lone system unlikely.  All good points. 

ISSUE #3:  Passwords changed

This was all me.  I had taken the keyboard off the night before off the laptop to blow down the fan and components inside and it had 3 screws holding it down. One of the 3 didn't screw in properly, and when I typed in ************* the password apparently some of the keys were typing in the wrong letters.  I didn't know at the time because of the ***** but I figured it out the next morning.  Haste makes waste.  I screwed it in tight and it was ok.  sry.

Thanks for patience and good advice.  I'm still thinking of scrapping win7 because the rootkit came back a second time. Unlikely I'm targeted, but I don't go to many places I shouldn't be.  

Thanks to all.









Tried

---

### Post by OpSecShellshock on 2011-12-13
Ah, good to know you've gotten it figured out. Not sure what to tell you about the battery issue apart from that some manufacturers opt to use non-standard ways of communicating their status to the software on the machines they're connected to, and when that happens it's more likely to be a problem for Linux than for Windows.

As for the Windows 7 installation, it is likely that from the moment of initial infection it was basically no longer salvageable. Such is the state of modern malware. My advice is to re-install the OS and restore files and some application settings from backups. There are lots of malware removal tools out there, but as you've probably seen they all find something different and give you an incomplete analysis. Most of them have already been tested by the malware authors themselves as part of their QA process before they ever hit the servers.

---

### Post by Marcus Aurelius on 2011-12-27
My battery issue has also been solved.  It turned out to be the plug that runs from the wall outlet to the laptop which charges the battery.  If you lay the plug in the wrong direction it doesn't charge.  If you turn it over it does charge. LOL.  This was the LAST thing I thought to check but eventually I caught it.  Apparently the wires inside the plug are getting worn and there is a loose hence intermittent connection.  Thanks again for replies.

---

### Post by emiller12345 on 2011-12-27
> **CharlesA said:**
> Valid point. I was thinking that maybe UAC would have notified the user of something requiring escalated privileges.
For what it's worth, I've already seen a couple of examples where UAC is already defeated, and there is no notification.

MS11-011 : Windows UAC Bypass 0day
[http://www.youtube.com/watch?v=R1BHkQYDsx0](http://www.youtube.com/watch?v=R1BHkQYDsx0)

---

### Post by CharlesA on 2011-12-27
> **emiller12345 said:**
> For what it's worth, I've already seen a couple of examples where UAC is already defeated, and there is no notification.

MS11-011 : Windows UAC Bypass 0day
[http://www.youtube.com/watch?v=R1BHkQYDsx0](http://www.youtube.com/watch?v=R1BHkQYDsx0)

That's a zero-day exploit. That wouldn't happen everyday.

In any case, it would need to be a targeted attack in order to bypass UAC in order to install a ext driver with something like that.

---

### Post by |{urse on 2011-12-27
Well, a very very common rootkit called tdss will emulate many hardware issues on windows, the conficker worm also emulates bsod errors. There is little to no possibility of this traversing your win partition to your nix partitions. However, if you want it gone and dead run a nice little prog called combofix.

First, uninstall your antivirus (guarantee its hacked anyways) 

[http://www.bleepingcomputer.com/download/anti-virus/combofix](http://www.bleepingcomputer.com/download/anti-virus/combofix) <-- download and run on your windows side

[http://www.malwarebytes.org/](http://www.malwarebytes.org/) <-- then scan with malwarebytes

Install Avira antivirus. [http://www.avira.com/en/avira-free-antivirus](http://www.avira.com/en/avira-free-antivirus)

Scan with Avira to remove all the leftovers.

You can keep Avira if you'd like (which is a good choice) or remove it and install your favorite av.

---

### Post by Unguidedone on 2011-12-28
your hardware is dieing (i was in the same boat like in 2009 and totally freaked out)
hp did a recall for your computer model it was produced with faulty processor

check this link out:
[http://www.ehow.com/about_5564683_hp-pavilion-laptop-problems.html](http://www.ehow.com/about_5564683_hp-pavilion-laptop-problems.html)

When it died i was in collage writing a big paper....HP IS DEAD TO ME!!!! (dont buy hp stuff theyare evil)

please back up your files to a external drive before the computer quits 

i hope your computer is still under warranty :(

---

### Post by Dangertux on 2011-12-30
> **|{urse said:**
> Well, a very very common rootkit called tdss will emulate many hardware issues on windows, the conficker worm also emulates bsod errors. There is little to no possibility of this traversing your win partition to your nix partitions. However, if you want it gone and dead run a nice little prog called combofix.

First, uninstall your antivirus (guarantee its hacked anyways) 

[http://www.bleepingcomputer.com/download/anti-virus/combofix](http://www.bleepingcomputer.com/download/anti-virus/combofix) <-- download and run on your windows side

[http://www.malwarebytes.org/](http://www.malwarebytes.org/) <-- then scan with malwarebytes

Install Avira antivirus. [http://www.avira.com/en/avira-free-antivirus](http://www.avira.com/en/avira-free-antivirus)

Scan with Avira to remove all the leftovers.

You can keep Avira if you'd like (which is a good choice) or remove it and install your favorite av.

Just a note malwarebytes is really good too. If you're using windows I highly recommend it. It does amazing in heuristics compared to most other commercial AV. Just my 2 cents.

---

### Post by |{urse on 2012-01-01
> **Dangertux said:**
> Just a note malwarebytes is really good too. If you're using windows I highly recommend it. It does amazing in heuristics compared to most other commercial AV. Just my 2 cents.

Yeah, It was already included in the post you just commented on. :) Seriously though, if you run combofix and you dont follow up with Malwarebytes then the process is useless. Mbam is awesome.

---

### Post by Dangertux on 2012-01-01
> **|{urse said:**
> Yeah, It was already included in the post you just commented on. :) Seriously though, if you run combofix and you dont follow up with Malwarebytes then the process is useless. Mbam is awesome.

Yeah I know I for some reason put a too in there, should have just been is really good lol :-P

---

