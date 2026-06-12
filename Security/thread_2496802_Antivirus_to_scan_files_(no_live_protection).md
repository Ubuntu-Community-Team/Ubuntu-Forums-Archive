---
title: "Antivirus to scan files (no live protection)"
date: 2024-04-13
forum: Security
---

### Post by gipsyshadow on 2024-04-13
Hi all,
I'd like to use an antivirus in ubuntu 22.04 environment to scan a single file per time and I ask you suggestions based on your experiences.
Sometimes I must move files from an "external" source to my windows partition to execute then, eg. a friend of mine gives me a zip/rar file so I prefer to put it on my storage partition for first, then scan it and after that copy and paste it on my windows partition to unzip and execute it only if it's safe. Usually I run this scan online (eg. on [virustotal]("https://www.virustotal.com/gui/")) but sometimes I get files larger than the max size allowed so I'd like to install an antivirus on my os for that. Though I run dual boot (windows 10 / ubuntu 22.04) I'd rather not to install an antivirus in windows just because I prefer to work in ubuntu :)

---

### Post by TheFu on 2024-04-13
ClamAV is the F/LOSS tool that people use.
There are commercial tools, if you want to spend money.  eSet has something, I think.  [https://www.eset.com/ng/home/antivirus-linux/](https://www.eset.com/ng/home/antivirus-linux/) is what google found.

The only time I used AV on Linux was when our professional E&O Insurance contract mandated it, though it was pretty foolish for our uses.  Contracts are contracts.  Had we not run "current and maintained" AV, the entire insurance would be voided.  It found hundreds of false positives and never found any virii in the 4 yrs we ran it.

I think the best answer is to run AV on Windows if you want to protect Windows computers.  They take AV much more seriously.  On Unix systems, the ability of a virus to damage more stuff than just the end user's files are much less. Plus, on Unix-like OSes, we tend to have daily, automatic, versioned, backups, so if any file gets a virus, we can just revert to the file before the virus infection.

If you haven't reviewed the sticky posts at the top of the Security sub-forum here, it can clarify basic Linux security needs.

---

### Post by gipsyshadow on 2024-04-13
I've just installed clamtk via ubuntu sw and run it scanning a couple of files I already "knew" and it detected nothing! Well I'll go for a windows av, thanks the same :)

---

### Post by TheFu on 2024-04-13
> **gipsyshadow said:**
> I've just installed clamtk via ubuntu sw and run it scanning a couple of files I already "knew" and it detected nothing! Well I'll go for a windows av, thanks the same :)

ClamAV signatures need to be updated. I think updates come every few days.  The installed package doesn't come with current signatures. Could that have been the issue?  IDK.  ClamAV may not be looking for MS-Windows viruses. Why would it?  If the virus doesn't target or run on Linux, why would it look for it?

Do AV programs on Windows look for Linux viruses?  MacOS viruses?  No.

---

### Post by gipsyshadow on 2024-04-13
That has a sense but... in this particular case I've just run an online scan using virustotal and clamav reports "Undetected" as expected, indeed only 23/62 engines detected it as "malicious" or something similar, even some good av for windows I already know as kaspersky. It's interesting that microsoft engine detected it so maybe a good solution for me would be the easiest one, I mean to use windows system av to run my files' scans whenever I can't use virustotal because they're too big.

At the end (and a bit OT) I'd want to ask if you can suggest me a good site where to see if a key (labelled as malware, ransomware, etc) is really malicious or not. I often use joesandbox that I find very reliable; do you know other ones?

---

### Post by TheFu on 2024-04-13
AV tools on Windows tend to be 50% effective.  IF you run 3 of them, you can get to 80% effective for known viruses.
Or you can be selective about the places you visit, things you click, and files you blindly open.  Nothing can replace a smart user.  Just don't expect AV software to work at all and behave accordingly.

---

### Post by hyperlinxe on 2024-04-13
Av tools were useful maybe 10-15 years ago, now things are dramatically different. The virus signatures that make up the basis of AV tools operations are riddled with pro-corporate anti-competitive signatures, that are called false-positive's by third-party analysts, where competitive products to organizations such as google for example, are recognized as trojans, clickjackers, and all manner of malicious sounding software characteristics, regardless of the actual nature of the software, other than the fact that it is alternative to major corporations monopolizing technology.

If you actually want anti-viral activity to support your usage of technology, you are going to have to realize that AV tools and their functionality have already been exploited in advance by organizations that manipulate technology long ago. Now security requires a much more advanced approach to actually accomplish effectively, and briefly, this revolves around how people understand what it means to actually be malware, or a virus, and independently of how monopolies seek to define programs, and further impose those definitions onto people en masse.

I'll give you an example, we are directed to be afraid of the foreign internet, foreign from the internet incorporated with google's technology, and there are dangerous websites there, so we might understand that to be true, but if we possessed an independent understanding of what it means to be a virus, or malware, we might recognize that people using google products have a severe viral infection, and that makes them very sick, and they can't easily get rid of it.

---

### Post by stephan4 on 2024-08-27
ClamAV ... since CISCO took over, it's really powerful.

---

