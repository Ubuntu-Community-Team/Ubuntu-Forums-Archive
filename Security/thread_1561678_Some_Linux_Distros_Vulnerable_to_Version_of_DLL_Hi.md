---
title: "Some Linux Distros Vulnerable to Version of DLL Hijacking Bug ?"
date: 2010-08-26
forum: Security
---

### Post by newbie2 on 2010-08-26
> In the discussion on Full-Disclosure, one user said he'd been able to reproduce this on the Apache CouchDB database running on Ubuntu 10.04. 
[http://threatpost.com/en_us/blogs/some-linux-distros-vulnerable-version-dll-hijacking-bug-082610](http://threatpost.com/en_us/blogs/some-linux-distros-vulnerable-version-dll-hijacking-bug-082610)
:rolleyes:

---

### Post by pastalavista on 2010-08-26
No operating system is without potential vulnerability. Code can be compromised any time, especially open source, but it won't live long. The user behavior is the biggest risk. Social engineering can make some very tempting offers for you to download if you go outside the approved repositories. I still like my odds with Ubuntu.

---

### Post by Bachstelze on 2010-08-26
> Brown said that the bug looks to have been introduced through a Debian patch in March 2009

OpenSSL all over again?

---

### Post by wacky_sung on 2010-08-26
This is a window OS DLL bugs which affecting most applications running through it.I am very sure if you stop using any wine and it will **[COLOR="Red"]never[/COLOR]** get affected any Ubuntu user using it which solely using Ubuntu alone.

[COLOR="Blue"][Windows DLL exploits boom; hackers post attacks for 40-plus apps]("http://www.networkworld.com/news/2010/082510-windows-dll-exploits-boom-hackers.html?source=nww_rss")[/COLOR]
```
Publish exploits to subvert Firefox, Chrome, Word, Photoshop, Skype, dozens more

By Gregg Keizer, Computerworld 
August 25, 2010 04:01 PM ET
 Share/Email Tweet This 1 Comment Print
Some of the world's most popular Windows programs are vulnerable to a major bug in how they load critical code libraries, according to sites tracking attack code.

Among the Windows applications that can be exploited using a systemic bug that many have dubbed "DLL load hijacking," are the Firefox, Chrome, Safari and Opera browsers; Microsoft's Word 2007; Adobe's Photoshop; Skype; and the uTorrent BitTorrent client.

The Role of the Internet in the Propagation of Malware: Download now
"Fast and furious, incredibly fast," said Andrew Storms, director of security operations for nCircle Security, referring to the pace of exploit postings for the vulnerability in Windows software called "DLL load hijacking" by some, "binary planting" by others.

On Monday, Microsoft confirmed reports of unpatched vulnerabilities in a large number of Windows programs, then published a tool it said would block known attacks. The flaws stem from the way many Windows applications call code libraries -- dubbed "dynamic-link library," or "DLL" -- that give hackers wiggle room they can exploit by tricking an application into loading a malicious file with the same name as a required DLL.
```

_Microsoft DLL Hijacking Exploit in Action_
[Video]("http://www.offensive-security.com/offsec/microsoft-dll-hijacking-exploit-in-action/")

---

### Post by FuturePilot on 2010-08-26
> **wacky_sung said:**
> This is a window OS DLL bugs which affecting most applications running through it.I am very sure if you stop using any wine and it will **[COLOR="Red"]never[/COLOR]** get affected any Ubuntu user using it which solely using Ubuntu alone.

[COLOR="Blue"][Windows DLL exploits boom; hackers post attacks for 40-plus apps]("http://www.networkworld.com/news/2010/082510-windows-dll-exploits-boom-hackers.html?source=nww_rss")[/COLOR]
```
Publish exploits to subvert Firefox, Chrome, Word, Photoshop, Skype, dozens more

By Gregg Keizer, Computerworld 
August 25, 2010 04:01 PM ET
 Share/Email Tweet This 1 Comment Print
Some of the world's most popular Windows programs are vulnerable to a major bug in how they load critical code libraries, according to sites tracking attack code.

Among the Windows applications that can be exploited using a systemic bug that many have dubbed "DLL load hijacking," are the Firefox, Chrome, Safari and Opera browsers; Microsoft's Word 2007; Adobe's Photoshop; Skype; and the uTorrent BitTorrent client.

The Role of the Internet in the Propagation of Malware: Download now
"Fast and furious, incredibly fast," said Andrew Storms, director of security operations for nCircle Security, referring to the pace of exploit postings for the vulnerability in Windows software called "DLL load hijacking" by some, "binary planting" by others.

On Monday, Microsoft confirmed reports of unpatched vulnerabilities in a large number of Windows programs, then published a tool it said would block known attacks. The flaws stem from the way many Windows applications call code libraries -- dubbed "dynamic-link library," or "DLL" -- that give hackers wiggle room they can exploit by tricking an application into loading a malicious file with the same name as a required DLL.
```

_Microsoft DLL Hijacking Exploit in Action_
[Video]("http://www.offensive-security.com/offsec/microsoft-dll-hijacking-exploit-in-action/")

This is different from the Windows DLL hijacking vulnerability. But the same kind of hijacking can be exploited in Linux as well.

[http://seclists.org/fulldisclosure/2010/Aug/278]("http://seclists.org/fulldisclosure/2010/Aug/278")

---

### Post by wacky_sung on 2010-08-26
> **FuturePilot said:**
> This is different from the Windows DLL hijacking vulnerability. But the same kind of hijacking can be exploited in Linux as well.

[http://seclists.org/fulldisclosure/2010/Aug/278]("http://seclists.org/fulldisclosure/2010/Aug/278")

To the extent of what i known of Ubuntu user is affected with Apache CouchDB database.

[http://threatpost.com/en_us/blogs/some-linux-distros-vulnerable-version-dll-hijacking-bug-082610](http://threatpost.com/en_us/blogs/some-linux-distros-vulnerable-version-dll-hijacking-bug-082610)
```
In the discussion on Full-Disclosure, one user said he'd been able to reproduce this on the [COLOR="Red"]Apache CouchDB database running on Ubuntu 10.04[/COLOR]. Tomas Hoger, a member of the Fedora Security Response Team, said on the OSS Security mainling list Thursday that Fedora is in fact vulnerable to this bug.
```

[http://seclists.org/fulldisclosure/2010/Aug/295](http://seclists.org/fulldisclosure/2010/Aug/295)

---

### Post by BkkBonanza on 2010-08-26
Reading the bug discussion it appears this will be trivial to fix. It seems to be a typo introduced to the CouchDB scripting that opens a "current directory" search path allowing for a shared library to be intercepted in a situation where CouchDB is started from a poisioned directory. I'd expect that will be fixed up quickly.

---

### Post by Bachstelze on 2010-08-26
> **BkkBonaza said:**
> Reading the bug discussion it appears this will be trivial to fix. It seems to be a typo introduced to the CouchDB scripting that opens a "current directory" search path allowing for a shared library to be intercepted in a situation where CouchDB is started from a poisioned directory. I'd expect that will be fixed up quickly.

You're totally missing the point. The CouchDB thing was a symptom, not the problem itself. The problem is deeper than that:

[QUOTE="Tim Brown"]The Linux dynamic linker makes use of a variable called LD_LIBRARY_PATH which it consults when a binary is executed and which takes precedence over the OS default as set in ld.so.conf. So where's the problem? Consider the following script:
```

#!/bin/sh
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/path/to/app/lib
app start
```

What happens if LD_LIBRARY_PATH isn't set? Well, in that case, the app binary path is executed with an LD_LIBRARY_PATH of :/path/to/app/lib. This may seem perfectly satisfactory, but here's the rub. When the Linux dynamic linker sees a path with an empty directory specification such as :/valid/path, /valid/path: or /valid::/path, it treats the empty specification as $PWD. This could lead to a library being loaded from the users current working directory but where might it be exploitable.[/QUOTE]

The whole dynamic linker needs to be fixed, that is not trivial.

---

### Post by movieman on 2010-08-26
> **Bachstelze said:**
> The whole dynamic linker needs to be fixed, that is not trivial.

Surely it's trivial because the dynamic linker just has to filter out empty directories?

I only just realised that Ubuntu doesn't set LD_LIBRARY_PATH, making this far more serious than on older Unix versions where it was always set.

---

### Post by BkkBonanza on 2010-08-26
Ah, I see it's not just the :: in the scripted path then, but also cases of empty at start/end of path. This is still a small change to how the library path is parsed. Other than historic usage depending on being able to use the PWD, which really should be considered incorrect, fixing the parser to not treat an empty path as PWD would be simple. I'm saying that as an experienced C programmer, though how many developers have decided to depend on PWD is hard to know. It would appear to be a good idea to discourage that use and make it explicit when required.

---

### Post by movieman on 2010-08-26
Any code that relies on being able to load shared libraries from the current working directory is just broken and should be broken to prevent anyone from doing so :).

---

### Post by wacky_sung on 2010-08-27
I believe that if you **do not** run any server or using wine /dual boot which lead to Microsoft Operating System and you are pretty safe from the vulnerability found.

---

### Post by BkkBonanza on 2010-08-27
Actually the fault found above has nothing to do with Windows or DLLs. It is related to shared libraries (.so files) that may be maliciously loaded by placing them in the current directory where the program is started from. If you create your own hacked version of the .so file then you can potentially force it to be loaded instead fo the official version.

---

### Post by OpSecShellshock on 2010-08-28
As long as the application in question is still in active development, there's a pretty clear way forward that basically just involves everyone fixing things on their own particular end. What I mean is that the OS distribution developers could certainly arrange things so that loading libraries from the current directory can't be done, knowing that it will break certain applications, whose projects will then have bug reports filed so that they can be corrected. Thus the great cycle of the life of development goes on.

I don't think it would be given high priority, though, if only because the circumstances under which it could happen remotely would already be heartbreakingly stupid on the part of the local system owner.

---

