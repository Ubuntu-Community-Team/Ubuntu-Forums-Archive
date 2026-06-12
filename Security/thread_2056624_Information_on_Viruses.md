---
title: "Information on Viruses?"
date: 2012-09-11
forum: Security
---

### Post by MrHalfBlood on 2012-09-11
I have recently installed the Ubuntu OS 12.04 and part of the reason I got it was because I heard it was rare to get viruses, btw I have it along side windows. 
My question is could I get a virus from downloading music from ...? 
Will they Virus somehow get into the "Windows XP" part of my computer?
What really specifies a computer Virus? 
and If I don't get a virus on my computer but I transfer it on a USB will the virus be there? so if I plug it in to a windows computer will the virus affect it even if i don't move it on it?

---

### Post by claracc on 2012-09-12
There is a good ubuntu security sticky in the security subforum: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by GeForce 9500GT on 2012-09-12
I came across [this post]("http://forum.linuxmint.com/viewtopic.php?f=61&t=108103&p=619687#p618715") on a Linux Mint forum which describes (IMHO) on a fair level if Virusscanners are required.
 
On several websites and blogs messages pop up telling that there are more Linux virusses found. I'm not sure if those messages can be trusted but thats up to you.

---

### Post by oldos2er on 2012-09-12
Moved to Security Discussions.

---

### Post by Ms. Daisy on 2012-09-12
> **MrHalfBlood said:**
> I have recently installed the Ubuntu OS 12.04 and part of the reason I got it was because I heard it was rare to get viruses, btw I have it along side windows.  
In regards to viruses on Linux, you can read a brief discussion about the basics on the Basic Security Wiki. 
 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
 
> **MrHalfBlood said:**
> My question is could I get a virus from downloading music from ...?  Is mp3crank. com legitimate? Is it legal? (I have no idea myself- I've never heard of it.) If you're getting some hot new song for "free" chances are it's not legitimate and it could contain viruses. A large part of avoiding viruses and malware is **the user practicing common sense**. That means when you download free stuff that usually isn't free, it's way more likely to be hiding something malicious than the same thing purchased through normal channels (like itunes).
 
> **MrHalfBlood said:**
> Will they Virus somehow get into the "Windows XP" part of my computer? ... and If I don't get a virus on my computer but I transfer it on a USB will the virus be there? so if I plug it in to a windows computer will the virus affect it even if i don't move it on it?  If you share folders between Windows & Linux, then you could share something malicious. Using a USB drive is not a way to circumvent viruses. All you have to do is run a malicious executable on the windows machine- doesn't matter if it is stored on a USB drive.
> **MrHalfBlood said:**
> What really specifies a computer Virus? 
 When most people talk about "viruses" what they're really referring to is general malware. A virus is one of many kinds of malware out there. Read this to understand what a virus is (along with other types of malware): [http://en.wikipedia.org/wiki/Malware](http://en.wikipedia.org/wiki/Malware)

---

### Post by mike acker on 2012-09-14
"Be Advised" ::twisted:

there are virus attacks in Windows that can update your master boot record or even re-flash your BIOS (one specific BIOS was affected if I remember right )

[https://www.net-security.org/malware_news.php?id=1837](https://www.net-security.org/malware_news.php?id=1837)

[http://www.scmagazine.com.au/News/310777,highly-persistent-backdoor-infects-bios-peripherals.aspx](http://www.scmagazine.com.au/News/310777,highly-persistent-backdoor-infects-bios-peripherals.aspx)

these attacks are obviously carried out after the Windows system has been "pwned" and the attacker has code executing in kernel mode

these components would be common to any O/S that you boot up on your box

I am facing this right now. Rather than create a partition and add Ubuntu to my HP 6620 I'm going to build a new box  for my Ubuntu system ( well OK i want to do that anyway ) 

when I have the U-box up I'll install a switch for the KB, Monitor and Mouse so I can control both machines from my desk.

then I will take the Windows system offline.  I think it is best that a Windows box be restricted to running offline-- based on what I've learned...
[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

the article is a bit dated but nonetheless insightful.

so far I'm absolutely delighted with everything I've learned about Linux and Ubuntu.   Particularly the SUDO setup.

Some of you may remember, after Google got hacked (back in 2010?) they changed their Corporate policy for Google employees: Windows not allowed: Linux or Mac   ( Mac is based on FreeBSD If I remember rightly ) .

---

### Post by contributor on 2012-09-17
If you are downloading stuff from the internet including that mp3crank.com, then there are  some chances that your system may get infected files. I too don't have much knowledge about mp3crank.com whether it is legal or not to download the music files from this site. If you want to download the files then it is recommendable to scan it first. You can use many services for this like [https://www.virustotal.com/](https://www.virustotal.com/). By this, your both the OS will remain protected from viruses.
> Will they Virus somehow get into the "Windows XP" part of my computer?

It depends upon the what kind of infection you have.

---

### Post by 0011235813 on 2012-09-17
> **MrHalfBlood said:**
> I have recently installed the Ubuntu OS 12.04 and part of the reason I got it was because I heard it was rare to get viruses, btw I have it along side windows. 
My question is could I get a virus from downloading music from ...? 
Will they Virus somehow get into the "Windows XP" part of my computer?
What really specifies a computer Virus? 
and If I don't get a virus on my computer but I transfer it on a USB will the virus be there? so if I plug it in to a windows computer will the virus affect it even if i don't move it on it?
(visits mp3crank.com, sees Green WOT rating).
According to WOT, a site that has an active user base of 43 00 as of 17 December, the site is clean.  You should install the add-on; [http://www.mywot.com/](http://www.mywot.com/) I use it personally and find it very useful.
Secondly, the most probable answer is no. The only way a virus could infect your XP partition if you're using Ubuntu/Linux is if you transfer the infected file to the WinXP partition, and THEN EXECUTE IT. The last bit is pretty important- you can STORE infected files on a computer, as long as you don't run them.
A computer virus has a specific definition, but more commonly, it is used to describe *malware* ("**Mal**icious Soft**ware**, sometimes called *warez*) which is basically any type of electronically stored file that is considered malicious by the user (not the coder). 
If you store an infected file on a USB, you can view the USB with a Windows computer as long as you don't execute the infected file.
As usual, I recommend you follow Ms Daisy's advice and read THOSE BLASTED SECURITY WIKIS THAT PEOPLE SHOULD READ BUT NEVER DO. Sorry, I had to get that out of my system..

---

### Post by wacky_sung on 2012-09-17
Definition of a [computer virus]("http://en.wikipedia.org/wiki/Computer_virus").Very often people get all mix up.

> An example of a virus which is not a malware, but is putatively benevolent, is Fred Cohen's theoretical compression virus.[2] However, antivirus professionals do not accept the concept of benevolent viruses, as any desired function can be implemented without involving a virus (automatic compression, for instance, is available under the Windows operating system at the choice of the user). Any virus will by definition make unauthorised changes to a computer, which is undesirable even if no damage is done or intended. On page one of Dr Solomon's Virus Encyclopaedia, the undesirability of viruses, even those that do nothing but reproduce, is thoroughly explained.[1]

---

### Post by 0011235813 on 2012-09-17
> **wacky_sung said:**
> Definition of a [computer virus]("http://en.wikipedia.org/wiki/Computer_virus").Very often people get all mix up.

> An example of a virus which is not a malware, but is putatively benevolent, is Fred Cohen's theoretical compression virus.[2] However, antivirus professionals do not accept the concept of benevolent viruses, as any desired function can be implemented without involving a virus (automatic compression, for instance, is available under the Windows operating system at the choice of the user). Any virus will by definition make unauthorised changes to a computer, which is undesirable even if no damage is done or intended. On page one of Dr Solomon's Virus Encyclopaedia, the undesirability of viruses, even those that do nothing but reproduce, is thoroughly explained.[1]
Yup. It's like I said; the coder may not consider they're program malicious, it's all down to what the user thinks. 
Of course, you may not consider having your computer botneted by anonymous to be malicious, so it's all subjective (PS. Anon do not make botnets as far as I'm aware. Isn't there LOIC for that?).

---

### Post by wacky_sung on 2012-09-17
> **0011235813 said:**
> Yup. It's like I said; the coder may not consider they're program malicious, it's all down to what the user thinks. 
Of course, you may not consider having your computer botneted by anonymous to be malicious, so it's all subjective (PS. Anon do not make botnets as far as I'm aware. Isn't there LOIC for that?).

Personally i find that you got it all mix up and i do not recommend people to use [WOT]("http://www.mywot.com/") in which it is not reliable.

---

### Post by 0011235813 on 2012-09-17
> **wacky_sung said:**
> Personally i find that you got it all mix up. Beside that, personally i do not recommend people to [WOT]("http://www.mywot.com/") in which it is not reliable.
I've found it to be more reliable than any other "blacklist" utility (unless you know of a better one?). In any case, I don't think people realize how blind you are on the Internet without WOT. Sure, it might not have ALL the malicious websites known, but it has A LOT of them, ya know? 
In any case, it can't hurt.

---

### Post by wacky_sung on 2012-09-17
> **0011235813 said:**
> I've found it to be more reliable than any other "blacklist" utility (unless you know of a better one?). In any case, I don't think people realize how blind you are on the Internet without WOT. Sure, it might not have ALL the malicious websites known, but it has A LOT of them, ya know? 
In any case, it can't hurt.

FYI i used none which you have commended and what i need is my common sense. Most malicious sites are usually equipped with auto script injection using vulnerability and cookies by running my browser in virtual drive which has zero impact on my system. 

[Vx Heavens]("http://vx.netlux.org/index.html") is gone which have a great fun through the years.

---

### Post by bodhi.zazen on 2012-09-17
> **MrHalfBlood said:**
> I have recently installed the Ubuntu OS 12.04 and part of the reason I got it was because I heard it was rare to get viruses, btw I have it along side windows. 
My question is could I get a virus from downloading music from ...? 
Will they Virus somehow get into the "Windows XP" part of my computer?
What really specifies a computer Virus? 
and If I don't get a virus on my computer but I transfer it on a USB will the virus be there? so if I plug it in to a windows computer will the virus affect it even if i don't move it on it?

I have used Linux exclusively for a long time and have never had a virus. I share a Flash drive with Windows (work <--> home) and with the beefy anti-virus @ work, never found a virus on the flash drive.

The "problem" with all of the Linux anti virus scanners, IMO, it that all they seem to report is false positives.

IMO, if you run Windows I would run antiviurs on Windows. If you run Linux, check the antivirus scanners at the door and learn apparmor (or selinux).

---

### Post by HermanAB on 2012-09-19
+1 for Bodhi's comments.

Relax and enjoy your Linux system.

---

