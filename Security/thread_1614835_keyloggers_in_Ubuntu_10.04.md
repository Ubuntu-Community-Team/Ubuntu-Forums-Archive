---
title: "keyloggers in Ubuntu 10.04"
date: 2010-11-06
forum: Security
---

### Post by agentfortyseven on 2010-11-06
Hello friends,
I was going through this thread on keyloggers today. I'll try to put those three pages of discussion in a nutshell. 
"It is very difficult for a keylogger to install on your system but when it does, you're screwed since there isn't an effective anti-malware that could detect these keyloggers"

Having said that I would like to ask your opinion and suggestions on this.
"Prevention is better that cure" they say. 
Please discuss various ways that would keep people safe from being keylogged.
Right from downloading software packages from a trusted source to testing and removing malware from the system. 

Wishing you a happy and safe networking my friends.:)

---

### Post by Verbeck on 2010-11-06
if any process asks for your system administrator password, make sure you know what the program is before typing in the password.
 also, dont open files ending in .desktop unless you're sure  what it is, to check, open the files in gedit or a similar text editor and see the contents :)

---

### Post by agentfortyseven on 2010-11-06
> **verbeck said:**
> if any process asks for your system administrator password, make sure you know what the program is before typing in the password.
 Also, dont open files ending in .desktop unless you're sure  what it is, to check, open the files in gedit or a similar text editor and see the contents :)
thanks:)

---

### Post by agentfortyseven on 2010-11-06
:?: Come on guys...

---

### Post by peculiar penguin on 2010-11-06
Uh, what sort of threat do you expect?

All the usual advice applies - install the security updates, don't install/run software from untrusted sources, use complex passwords (and don't reuse them for more than one service), lock your desktop when you walk away from the computer, don't let other people use your computer/account (give them their own, limited account if they have to use it), stay current with the general security landscape by following a relevant website or three. If that's not good enough, I guess you could look into keeping your internet activity and other tasks inside different virtual machines, running your system off a (custom) LiveCD, or soft-/hardware products which restore your computer to a known state every restart.

Then there's hardware keyloggers, so you might want a tamper-resistant keyboard and computer case, and verify there's nothing strange plugged in between them every time you enter a password or other sensitive information.

---

### Post by cariboo on 2010-11-06
I would suggest if you want to learn more about key logging, set up a test system, and install a keylogger, there is one in the repositories. Then use the different tools available to try and detect it. I always find that hands on experience is the best way to learn about perceived threats.

---

### Post by arapaho on 2010-11-06
You may also be interested in rkhunter
[http://en.wikipedia.org/wiki/Rkhunter](http://en.wikipedia.org/wiki/Rkhunter)
or anti-viruses for linux like clamav or avast or bitdefender
You know, just in case...

---

### Post by brian_p on 2010-11-06
> **arapaho said:**
> You may also be interested in rkhunter . . . . . .. 

rkhunter's track record on discovering key loggers is on on a par with its ability to detect rootkits.

---

### Post by agentfortyseven on 2010-11-06
> **peculiar penguin said:**
> Uh, what sort of threat do you expect?

All the usual advice applies - install the security updates, don't install/run software from untrusted sources, use complex passwords (and don't reuse them for more than one service), lock your desktop when you walk away from the computer, don't let other people use your computer/account (give them their own, limited account if they have to use it), stay current with the general security landscape by following a relevant website or three. If that's not good enough, I guess you could look into keeping your internet activity and other tasks inside different virtual machines, running your system off a (custom) LiveCD, or soft-/hardware products which restore your computer to a known state every restart.

Then there's hardware keyloggers, so you might want a tamper-resistant keyboard and computer case, and verify there's nothing strange plugged in between them every time you enter a password or other sensitive information.
Thanks... Hope that helps many others beside me.

---

### Post by agentfortyseven on 2010-11-06
> **cariboo907 said:**
> I would suggest if you want to learn more about key logging, set up a test system, and install a keylogger, there is one in the repositories. Then use the different tools available to try and detect it. I always find that hands on experience is the best way to learn about perceived threats.

Well that was tried and tested, not by me but someone else on ubuntuforum. Unfortunately the ClamAV could not detect it. 
Bodhi Zazen described such a keylogger as a "keylogger in the wild" and that there are way too many such keyloggers out there.
So I guess this thread is meaningful in a way by sharing views and discussions to avoid this menace in the first place itself.

---

### Post by agentfortyseven on 2010-11-06
> **arapaho said:**
> You may also be interested in rkhunter
[http://en.wikipedia.org/wiki/Rkhunter](http://en.wikipedia.org/wiki/Rkhunter)
or anti-viruses for linux like clamav or avast or bitdefender
You know, just in case...

Yeah sure I'll definitely give it a try :)

---

### Post by cariboo on 2010-11-06
> **agentfortyseven said:**
> Well that was tried and tested, not by me but someone else on ubuntuforum. Unfortunately the ClamAV could not detect it. 
Bodhi Zazen described such a keylogger as a "keylogger in the wild" and that there are way too many such keyloggers out there.
So I guess this thread is meaningful in a way by sharing views and discussions to avoid this menace in the first place itself.

Remember for a key logger to work on a Linux variant, you have to install it yourself. The only place it can be installed with little user intervention is in your home directory. which sort of defeats the purpose, as for it to be effective, it has to be hidden from the average user.

Have a look at the install instruction for [logkeys]("http://code.google.com/p/logkeys/wiki/Documentation"), and tell us how it can be installed as a drive by download, and I have also attached the install instructions for lkl. Again the person installing it will have to have access to the system to do so.

---

### Post by agentfortyseven on 2010-11-07
> **cariboo907 said:**
> Remember for a key logger to work on a Linux variant, you have to install it yourself. The only place it can be installed with little user intervention is in your home directory. which sort of defeats the purpose, as for it to be effective, it has to be hidden from the average user.
Alright that's a good piece of info cariboo907. I guess I'll have to agree with you but would love to see someone contradict your views;)

---

### Post by OpSecShellshock on 2010-11-07
> **agentfortyseven said:**
> Alright that's a good piece of info cariboo907. I guess I'll have to agree with you but would love to see someone contradict your views;)

I wouldn't expect anyone to contradict the view, because it's correct. Even on other operating systems, keyloggers still come in the form of trojans for the most part. It happens because users install it themselves (although they usually don't know it). "Install it themselves" is kind of an elastic concept (still talking about other operating systems, not Linux builds) because it could very well be that they are running a web browser under an administrative account with all scripts enabled and they wouldn't get so much as a prompt. Alternatively, they could open an email attachment without knowing what it is, in a vulnerable application that the attachment is designed to exploit.

On Linux, there would be a privilege elevation prompt prior to installing anything with keystroke logging functions. If someone wanted to intercept password entries in a web browser, they'd be far better served making either a malicious browser extension (which users would have to be tricked into installing) or somehow altering the user's browser profile such that it alters the page as it's viewed on the local machine--perhaps by injecting a script that would send information off site (not by logging keystrokes, but by grabbing form data and sending it). That risk (which is still quite minimal on non-Windows systems) can be mitigated by having a dedicated financial transaction profile in addition to the regular web surfing profile, and then using the standard NoScript/Adblock/BetterPrivacy/CSLite combo. Such a thing would be better than a live CD because it would be updated more regularly. Set the browser to clear all private data on exit, and then always exit when finished.

I should add that I don't personally go that far, and don't think it adds much more than peace of mind, but I do always exit one browser session and start a new one (with the same profile) prior to handling any sensitive business. I then close it and open a new session whenever that's finished. I only suggest dedicated profiles to others since there are many people who find whitelisting in NoScript (and other security steps that are standard routines for me) to be inconvenient or tedious.

---

### Post by agentfortyseven on 2010-11-07
> **OpSecShellshock said:**
> I wouldn't expect anyone...(etc etc ;) etc etc) ...to be inconvenient or tedious.
+10 for you buddy. Thanks a lot.

---

### Post by OpSecShellshock on 2010-11-07
Yeah yeah, I get it, I'm a little wordy sometimes :)

---

### Post by agentfortyseven on 2010-11-07
> **OpSecShellshock said:**
> Yeah yeah, I get it, I'm a little wordy sometimes :)
But honestly that was a great post, thanks again.:)

---

