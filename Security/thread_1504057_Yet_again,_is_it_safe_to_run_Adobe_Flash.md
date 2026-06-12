---
title: "Yet again, is it safe to run Adobe Flash?"
date: 2010-06-07
forum: Security
---

### Post by john_spiral on 2010-06-07
"This vulnerability (CVE-2010-1297) could cause a crash and potentially allow an attacker to take control of the affected system..." 

quote from the below recent security advisory.

[http://www.adobe.com/support/security/advisories/apsa10-01.html](http://www.adobe.com/support/security/advisories/apsa10-01.html)

I thought a modern open source browser like Firefox or Chrome would sandbox the flash api?

another source of the same article:

[http://news.bbc.co.uk/1/hi/technology/10257411.stm](http://news.bbc.co.uk/1/hi/technology/10257411.stm)

---

### Post by FuturePilot on 2010-06-07
AFAIK, Firefox has no sandboxing capability. But Apparmoring Firefox should have the same effect.

---

### Post by CharlesA on 2010-06-07
You can install 10.1 RC7 on Linux, no?

---

### Post by uRock on 2010-06-07
NoScript is my best friend when it comes to blocking flash.

---

### Post by john_spiral on 2010-06-07
> **CharlesA said:**
> You can install 10.1 RC7 on Linux, no?

looks like there is a download on the below page. 

[http://labs.adobe.com/downloads/flashplayer10.html#flashplayer10](http://labs.adobe.com/downloads/flashplayer10.html#flashplayer10)

More than likely when one major bug is discovered there are normally more in the pipe line.

Could a nasty flash file really 'take control' of my system?

---

### Post by OpSecShellshock on 2010-06-07
I wouldn't worry too much about it on Ubuntu. The vulnerability can certainly be exploited in the Linux version, but I don't think it will do more than cause the browser to crash. The real danger is in following the Flash exploit up with a heap spray and using that to decode and load another program, which will be a Windows executable. Remember that exploit code, while often used as a tool for loading malware, is not malware itself. There's still a lot of chance/luck involved in these exploits, because anything that happens after even a successful exploit will be constrained by the user's privileges.

---

### Post by bodhi.zazen on 2010-06-07
> **FuturePilot said:**
> AFAIK, Firefox has no sandboxing capability. But Apparmoring Firefox should have the same effect.

I do not think chromium sandboxes Flash either.

As an aside, there are similar vulnerabilities against firefox that do not involve flash, look through the security advisories :

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn") 

So you should ALWAYS secure your browser.

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

In addition I advise you use apparmor.

---

### Post by mihalisla on 2010-06-07
So , if I have a good apparmor profile set for firefox and noscript 
,should I be ok from this vulnerability?

---

### Post by bodhi.zazen on 2010-06-08
> **mihalisla said:**
> So , if I have a good apparmor profile set for firefox and noscript 
,should I be ok from this vulnerability?

Short answer - yes.

Longer answer - You are probably "OK" without it, but it is a potential vulnerability nonetheless and as such apparmor will help, but there are no guarantees apparmor will always work.

Clear as mud ?

---

### Post by Soul-Sing on 2010-06-08
try the opensource variant [COLOR="Red"]gnash[/COLOR], I watch youtube with it.
its in a great project, very much alive.

---

### Post by mihalisla on 2010-06-08
Thank you both for your replies !!!

---

### Post by movieman on 2010-06-08
One thing to be aware of is that even with Apparmor activated I believe a malicious web page exploiting a Flash bug could still install a malicious plugin which would capture passwords in Firefox or redirect your bank account to a phishing site. Apparmor will prevent Firefox from writing to places that it shouldn't touch, but it still has to be able to write to its own configuration files.

It's not likely, but it's one reason why I do all my online banking from a completely different account to normal web-browsing.

---

### Post by rpaco on 2010-06-12
Well I got hit by it this morning on the BBC news page "Help for heroes" there is a flash item re the founders getting the MBE. I ran that and it closed Firefox, then nothing else at all would work, not even a terminal window or system monitor. A hard reboot brought a very long "think" followed by a system caret requesting my login. I did a fsck which wen ton for a good 5 mins with all sorts of errors on the system being corrected. Another boot then gave a system which still did not work. So a third hard boot then using a recovery mode from grub has got me back here after re-configuring my network settings which had been wiped out. BTW I was running both Adblock plus and Noscript when the hit happened, also Flashblock, which held it at bay until I clicked on it to view it.   Now I need to find a Deb or RPM version of the revised/updated flash the tar versions never seem to work for me and always put things in the wrong place or don't make the links.   I am running 9.10 since 10.4 did not allow recovery from sleep or hibernation modes.  Finally how do we test? I used to run clamav but it slowed things down so have not installed it on this system, would it catch the Flash virus?

---

### Post by rookcifer on 2010-06-12
> **rpaco said:**
> Well I got hit by it this morning on the BBC news page "Help for heroes" there is a flash item re the founders getting the MBE. I ran that and it closed Firefox, then nothing else at all would work, not even a terminal window or system monitor. A hard reboot brought a very long "think" followed by a system caret requesting my login. I did a fsck which wen ton for a good 5 mins with all sorts of errors on the system being corrected. Another boot then gave a system which still did not work. So a third hard boot then using a recovery mode from grub has got me back here after re-configuring my network settings which had been wiped out. BTW I was running both Adblock plus and Noscript when the hit happened, also Flashblock, which held it at bay until I clicked on it to view it.   Now I need to find a Deb or RPM version of the revised/updated flash the tar versions never seem to work for me and always put things in the wrong place or don't make the links.   I am running 9.10 since 10.4 did not allow recovery from sleep or hibernation modes.  Finally how do we test? I used to run clamav but it slowed things down so have not installed it on this system, would it catch the Flash virus?

Sounds like a hardware problem and not an exploit.  For good measure please provide the exact link you visited.

---

### Post by jdunn on 2010-06-15
> **CharlesA said:**
> You can install 10.1 RC7 on Linux, no?

Not for 64-bit linux.  Adobe pulled 10.0 and is skipping 10.1 :(

---

### Post by uRock on 2010-06-15
> **jdunn said:**
> Not for 64-bit linux.  Adobe pulled 10.0 and is skipping 10.1 :(
Doesn't it look a bit suspicious? I wonder if they are being paid to leave Linux sitting.

---

### Post by OpSecShellshock on 2010-06-15
> **uRock said:**
> Doesn't it look a bit suspicious? I wonder if they are being paid to leave Linux sitting.

The most reasonable explanation I've run across (though I can't remember where) is that the 64-bit Linux alpha was the only version of 10.0 with 64-bit support, and 10.1 hasn't got a 64-bit build on any platform. Since there were around 32 vulnerabilities in 10.0 and 10.1 wasn't affected, Adobe decided to just have people upgrade to the new version rather than addressing the vulnerabilities of 10.0 (instead just deprecating it). Version 10.1 is fundamentally different from 10.0 in a few ways, but 10.0 is the only version that had a 64-bit build, which was limited to the Linux alpha. So 10.0 (the only one with a 64-bit version) is vulnerable as all heck, and is being resolved by upgrading to 10.1 (which is 32-bit only) rather than an update. I don't think they've stopped work on it entirely; they just don't have a 64-bit upgrade yet and the old version had to be emergency-deprecated.

It's important to note that non-Linux operating systems don't have a 64-bit version available at all, and the 32-bit version works fine on those regardless.

---

