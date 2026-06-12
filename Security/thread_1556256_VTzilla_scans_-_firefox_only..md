---
title: "VTzilla scans - firefox only."
date: 2010-08-19
forum: Security
---

### Post by yeleek on 2010-08-19
[http://lifehacker.com/5614928/vtzilla-scans-files-for-malware-before-you-download-them](http://lifehacker.com/5614928/vtzilla-scans-files-for-malware-before-you-download-them)

Seems worthwhile - though not tested myself thoroughly.

---

### Post by OpSecShellshock on 2010-08-19
Well, at a glance I see a number of problems with this. VirusTotal sort of depends on vendors having encountered a file before in order to work. Also, in a lot of cases it's used by malware developers themselves as a "QA" tool before deployment. There are also a number of confirmed malicious files that haven't really been detected as such yet, particularly with packing and encryption routines and things like server-side polymorphism. Then there's the issue that the binary download is not frequently an active process on the part of the user--that is, there are a series of redirections, web-based scripts, exploits and things that happen before the real payload is obtained.

---

### Post by yeleek on 2010-08-19
'VirusTotal sort of depends on vendors having encountered a file before in order to work.' - Thats the same for all AV, unless you rely upon a heuristic approach.

I agree that there are ways of masking or encoding a malicious file - just look at encoding meterpreter.  I do think something like this though is worthwhile, especially if sharing files will less fortunate users (i.e. windows).

---

### Post by cdenley on 2010-08-19
Does VirusTotal do anything to prevent web servers from identifying them? If this type of anti-virus becomes common, the attackers will start serving harmless files to VirusTotal then deliver their payload to the actual user. When you ask VirusTotal to check the hosted file, there is no guarantee that when you attempt to download the same file, it actually is the same file.

---

