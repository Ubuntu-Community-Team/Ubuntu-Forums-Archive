---
title: "everyone please read, I'm getting viruses"
date: 2010-01-10
forum: Security
---

### Post by mdquince on 2010-01-10
ok so everyone is saying you do not need any anti virus protection for linux but 2 out of 3 times I have run the anti virus program that came with ubuntu it finds a virus.  I have not been to any porn sites or installed any file sharing program as of yet.  so whats up with that??
most of the viruses have been found in opera which is what I use and it crashed eariler and when i restarted it all my bookmarks were gone.

---

### Post by Enigmapond on 2010-01-10
There is virtually no way a virus can install itself in Ubuntu. How did you install Opera? Did you also install add-ons? If so, from what source? Sounds like a malware issue..also what "viruses" have been found and where did it say they were located?

---

### Post by llawwehttam on 2010-01-10
I don't know what antivirus you are using but it is obviously throwing up false positives which means your computer is fine but your antivirus believes it has viruses and is removing important files so really its your antivirus thats giving you problems.

What antivirus are you using and what viruses does it believe you have?
I have been using linux for 7 years and have never had a virus.

---

### Post by FuturePilot on 2010-01-10
Definitely sounds like an issue of false positives.

---

### Post by cascade9 on 2010-01-10
Might not be false positives, p2p stuff can quite often come with a virus. Programs and cracks for programs are the worst offenders for that. BTW, its only this thread that makes me guess that OP is using p2p- 

[http://ubuntuforums.org/showthread.php?t=1377460](http://ubuntuforums.org/showthread.php?t=1377460)

---

### Post by kerry_s on 2010-01-10
opera has mail, mail coming from windows machines can be infected . do you have mail setup ?

---

### Post by rookcifer on 2010-01-10
Since the AV scanners scan almost exclusively for **windows** viruses, it is likely that the AV found a signature hit of some **windows** spyware or a trojan in your browser cache.  I have seen reports of this on here before.

Basically, nothing to worry about.

---

### Post by BigCityCat on 2010-01-10
It's obviously user error. No doubt about it. There is absolutely no system that can protect a person from their own mistakes.

---

### Post by running_rabbit07 on 2010-01-10
It is likely that you may have Windows viruses in your temp folder from sites you have browsed. They are harmless.

The only file that Clam reports as being a virus on my machine, is a cheesy program that asks if you want buttons, if you click yes, you get 50 small windows that have a button for closing them, completely harmless and only works on Windows.

---

### Post by OpSecShellshock on 2010-01-10
Any advice you see about avoiding porn and file sharing as a way to protect yourself from malicious code is out-of-date. It's not that you can browse such content without worry (far from it), but that malware distributors prefer to hijack more innocuous content now. For the most part, it's easy to put in iframes, javascript, redirections, and other things in poorly-protected websites. Also, banner ad affiliate networks are frequently compromised and almost entirely outside a main site administrator's control. Those things are somewhat immaterial on a Linux system because of how permissions tend to be set up. Arbitrary code might execute following a successful exploit under certain circumstances, but it won't affect the OS or cause software to be installed automatically.

The worst you'll probably see is a browser crash, or maybe a fake anti-virus warning from a mysterious program you haven't heard of or installed, that looks like a Windows file browser (and uses Windows drive letters and file paths) but is nonetheless telling you that "viruses" or "spyware" have been found and can be removed for a $50 "full version." Even then, if you believe the warning and try to install the program it will fail because it will be a Windows executable. ClamAV will still probably call it malware, but it won't be able to do anything.

---

### Post by running_rabbit07 on 2010-01-10
> **OpSecShellshock said:**
> Any advice you see about avoiding porn and file sharing as a way to protect yourself from malicious code is out-of-date. It's not that you can browse such content without worry (far from it), but that malware distributors prefer to hijack more innocuous content now. For the most part, it's easy to put in iframes, javascript, redirections, and other things in poorly-protected websites. Also, banner ad affiliate networks are frequently compromised and almost entirely outside a main site administrator's control. Those things are somewhat immaterial on a Linux system because of how permissions tend to be set up. Arbitrary code might execute following a successful exploit under certain circumstances, but it won't affect the OS or cause software to be installed automatically.

The worst you'll probably see is a browser crash, or maybe a fake anti-virus warning from a mysterious program you haven't heard of or installed, that looks like a Windows file browser (and uses Windows drive letters and file paths) but is nonetheless telling you that "viruses" or "spyware" have been found and can be removed for a $50 "full version." Even then, if you believe the warning and try to install the program it will fail because it will be a Windows executable. ClamAV will still probably call it malware, but it won't be able to do anything.

I agree totally, 

A. [The internet is for]("http://www.youtube.com/watch?v=eWEjvCRPrCo") and,

B. I've encountered more viruses on Myspace than any other site.

---

### Post by BigCityCat on 2010-01-10
I was sitting here talking to my room-mate about this thread, and she said her Norton was having problems this morning so I went in there and started a scan with malwarebytes. She didn't even know she had malwarebytes cause I put it on there a couple months ago and she forgot. So far 20 infected objects.

If I see anything serious I will check back.

---

### Post by BigCityCat on 2010-01-10
A bunch of adware and trojan.vundo.

---

