---
title: "How good is ClamTK ?"
date: 2015-10-22
forum: Ubuntu, Linux and OS Chat
---

### Post by michael-piziak on 2015-10-22
I know, I know,

Many will argue that *no* anti-virus type program is needed for Linux.   I used the Mac OS X [Unix] for years and didn't have any such program on it

But ClamTK, and I manually use it every few days, it always finds threats and asks me if I want to quarantine them or delete them - takes about 15 minutes to scan the system (and I am curious if one should do this with no other program/apps running - ?).

Most of what ClamTK finds is things "malicious" in the 2 browsers I use (Chromium or Firefox).

So again, the question is, how good is ClamTK.  Every time my system hickups or very rarely locks up, I make sure to run it first on reboot.

Attached is a screenshot of what ClamTK just found on my system after approximately a 15 minutes scan.

Michael

Oh, and here is a link to the ClamTK info on wikipedia:  [https://en.wikipedia.org/wiki/Clam_AntiVirus](https://en.wikipedia.org/wiki/Clam_AntiVirus)

Screenshot below:

---

### Post by night_sky2 on 2015-10-22
There are not enough viruses targeting Ubuntu to make ClamTK relevant, IMO. The vast majority of malicious codes are written for Windows, OSX, iOS and Andoid.
That could change if Linux should rise above the 1.5% of desktop OS users, but so far that's simply not the case. A bit of common sense while browsing the web is still needed though.
Now you might want to scan files that you plan to share with friends and relatives who use Windows.
In that case, I use **VirusTotal**, a malware and URL scanning service (totally free): [https://www.virustotal.com/]("https://www.virustotal.com/fr/")

As for ClamTK and the ''threats'' found in Chromium and Firefox, it's very likely some false positives or tracking cookies labelled as PUA.
I suggest you use BleachBit in normal mode and clean both browsers thoroughly. This will probably make the warnings in ClamTK disappear.[URL="https://www.virustotal.com/fr/"]

[/URL]

---

### Post by michael-piziak on 2015-10-22
> **night_sky2 said:**
> There are not enough viruses targeting Ubuntu to make ClamTK relevant, IMO. The vast majority of malicious codes are written for Windows, OSX, iOS and Andoid.
That could change if Linux should rise above the 1.5% of desktop OS users, but so far that's simply not the case. A bit of common sense while browsing the web is still needed though.
Now you might want to scan files that you plan to share with friends and relatives who use Windows.
In that case, I use **VirusTotal**, a malware and URL scanning service (totally free): [https://www.virustotal.com/]("https://www.virustotal.com/fr/")

As for ClamTK and the ''threats'' found in Chromium and Firefox, it's very likely some false positives or tracking cookies labelled as PUA.
I suggest you use BleachBit in normal mode and clean both browsers thoroughly. Most likely this will make the warnings in ClamTK disappear.[URL="https://www.virustotal.com/fr/"]

[/URL]

Thanks for your very intelligent reply.

As far as using VirusTotal, it just seems like too much work for me to use that everytime I send an attachment to friends/family - I'm sure you can understand that.

I agree with you that the "threats" found by ClamTK are most likely false positives.

I also agree think, and I think you are suggesting it too [correct me if I'm wrong], but the "things" ClamTK finds are no threat to Linux, but can be a threat to our friends that use Windows - thus keeping the Linux system free from viruses/malware/trojan horses, will make our Windows friends happy.  For example, I once had a Windows user email me back and she told me her anti-virus picked up on that I sent her a virus via email.  In such a case, Linux, in my opinion, is like a "carrier" and can't get infected itself but can pass along the nasty critters to our Windows friends - making it look to them that our Linux systems aren't so virus free as we think they are - get it ?

As for BleachBit - is that in the software center or do I need to enter code into terminal to get that?

Thanks again for your prompt and intelligent reply!

Michael

---

### Post by night_sky2 on 2015-10-22
> **michael-piziak said:**
> 

As far as using VirusTotal, it just seems like too much work for me to use that everytime I send an attachment to friends/family - I'm sure you can understand that.
I understand but at the same time, VirusTotal gives you access to 55 AV products and 61 online scan engines at once - with latest definitions - while ClamTK only one.

 They also have browser extensions if needed, which makes it a lot more easier if you need to use the service very often (See: [https://www.virustotal.com/fr/documentation/browser-extensions/](https://www.virustotal.com/fr/documentation/browser-extensions/)). This is undoubtedly a more powerful detection tool (very useful for Linux users who don't need a full-blown antivirus software on their system) and one can easily sort through false positives.

> **michael-piziak said:**
> As for BleachBit - is that in the software center or do I need to enter code into terminal to get that?
Bleachbit is available in the Ubuntu Software Center. Just be careful. It is recommended to use it only for cleaning apps such browsers, Flash plugin, Media players ect. but not the whole system.

So, I wouldn't use it in root mode if I were you.

---

