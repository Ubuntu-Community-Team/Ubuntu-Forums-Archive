---
title: "China cyberattack on Google used PDF Flaw.  Has Ubuntu been patched?"
date: 2010-01-14
forum: Security
---

### Post by DodgeV83 on 2010-01-14
Source:

[http://www.msnbc.msn.com/id/34855470/ns/technology_and_science-washington_post/](http://www.msnbc.msn.com/id/34855470/ns/technology_and_science-washington_post/)

> The attackers, experts said, followed the familiar "phishing" ruse: A recipient opens an e-mail that purports to be from someone he knows and, not suspecting malicious intent, opens an attachment containing a "sleeper" program that embeds in his computer. That program can be controlled remotely, allowing the attacker to access e-mail, send confidential documents to a specific address &#8212; even turn on a Web camera or microphone to record what is going on in the room.

In many cases, a user does not know he has been the victim of an attack.

**One type of attack exploits a flaw in Adobe Reader, a popular free program that allows e-mail users to read .pdf document files. The flaw was made public Dec. 15 but fixed only on Tuesday &#8212; the day Google announced that its systems had been compromised. **

It took nearly a month for Adobe to patch a PDF vulnerability which allows an attacker to take over your computer.  One of the big talking points of Ubuntu and open-source in general, is that these type of vulnerabilities are extremely quick to be patched, unlike their closed-source competitors.

So I ask, is Ubuntu vulnerable to this PDF flaw?

---

### Post by cdenley on 2010-01-14
Apparently, the flaw is in Adobe Reader, so it shouldn't affect ubuntu.

---

### Post by arubislander on 2010-01-14
> **DodgeV83 said:**
> So I ask, is Ubuntu vulnerable to this PDF flaw?

Are you asking 
[LIST=1]
[*]if the Linux version of Adobe Reader is vulnerable?
[*]or if Evince or one of the other document viewers available for Ubuntu is vulnerable?
[*]or maybe if Ubuntu as an OS itself is vulnerable?
[/LIST]

The answer to 1 is: Only Adobe knows for sure... but it if so, it can only be fixed by Adobe, since the software is closed source.
The answer to 2 is maybe, though it's not likely since they are not based on Acrobat Reader.
The answer to 3 is a definite no, just as Windows is not vulnerable to the exploit.

---

### Post by tubbygweilo on 2010-01-14
The biggest flaw is the person clicking on and opening a suspect email and attachment. This is a two stage attack, the first is the social engineering that tempts the target to open the suspect email, the second is the faulty attachment and package. General user eduction about clicking on and opening unknown object would go along way to curing this type of attack.

---

### Post by running_rabbit07 on 2010-01-14
That is what makes Linux so bloody awesome. One doesn't have to worry about crap like that unless one is dumb enough to run as root, which, thankfully, the Ubuntu devs have made it a little harder to do. Though it is easy to find the documentation and set up the root account for Karmic, I don't think anyone would actually create that account to use for surfing.

---

### Post by Sarmacid on 2010-01-14
> **DodgeV83 said:**
> 
So I ask, is Ubuntu vulnerable to this PDF flaw?

It was discussed yesterday, and yes, it affects Unix systems as well.
[http://ubuntuforums.org/showthread.php?t=1380322](http://ubuntuforums.org/showthread.php?t=1380322)

> **running_rabbit07 said:**
> That is what makes Linux so bloody awesome. One doesn't have to worry about crap like that unless one is dumb enough to run as root, which, thankfully, the Ubuntu devs have made it a little harder to do. Though it is easy to find the documentation and set up the root account for Karmic, I don't think anyone would actually create that account to use for surfing.

The attack was targeted at information, not to use the machine in any way so the root access was not really necessary. As long as the user with the information the attackers want runs the malware, they've achieved their goal.

---

### Post by running_rabbit07 on 2010-01-14
> **Sarmacid said:**
> It was discussed yesterday, and yes, it affects Unix systems as well.
[http://ubuntuforums.org/showthread.php?t=1380322](http://ubuntuforums.org/showthread.php?t=1380322)



The attack was targeted at information, not to use the machine in any way so the root access was not really necessary. As long as the user with the information the attackers want runs the malware, they've achieved their goal.

I never knew there was and Adobe PDF reader for Linux. I haven't had a PDF open within a browser since changing over to Ubuntu. They only did that in IE.

---

### Post by rookcifer on 2010-01-15
The thread title is incorrect.  It was [recently discovered]("http://www.computerworld.com/s/article/9144844/Hackers_used_IE_zero_day_not_PDF_in_China_Google_attacks") that this China attack was done with a flaw in **Internet Explorer** and not Adobe PDF.

So, all you windoze users out there, no matter what version of Windows you are on or what version of IE, you are at risk.  There is no fix and no workaround.  And the researchers who found the flaw are not talking.  This is what you get in the closed-source, proprietary world.

At any rate, there is nothing for Ubuntu to patch -- this **is not** an Adobe flaw and **does not** affect Linux users.

---

