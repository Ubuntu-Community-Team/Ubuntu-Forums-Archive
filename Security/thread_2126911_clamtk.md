---
title: "clamtk"
date: 2013-03-18
forum: Security
---

### Post by gordie69 on 2013-03-18
hey guys just installed ubuntu 12.04 lts 64 bit and installed clamtk and was thinking if I need it or not I know linux is not targeted for viruses but I was thinking on my email contacts that still use Windows keeping everyone safe

---

### Post by Stonecold1995 on 2013-03-19
Linux does not need antivirus software, and ClamTK doesn't scan for the few Linux viruses anyways.  And unless you are often sending attachments from untrustworthy sources to your contacts, you don't need it for that either (because Linux is much more secure, it is unlikely your computer will start sending malicious attachments by itself).  If you are concerned though, you could keep it installed anyways.  It doesn't run realtime (i.e. scan every file as it is written and read), so it won't add to your CPU load, but you'd have to run it manually on a suspicious attachment.

Also note, if you ever install Wine (a program which allows it to run Windows exe programs on Linux), you should be careful of malware.  Because Wine tries its best to run a Windows program, it can also run many viruses and other malware, although an infection is likely to be confined to the .wine directory and not damage the rest of your computer.

---

### Post by sammiev on 2013-03-19
If you share with windows users, I would suggest Avast or Bitdefender. Bitdefender saved me a lot of problems in the past.

---

### Post by Ms. Daisy on 2013-03-20
The most common reason I hear for using AV on Linux is to prevent passing infections on to Windows machines.  But unless you're willing to learn how to manage false positives, it will give you far more trouble than it's worth.

Nope. Linux isn't more secure. If you would like to increase the security of your Ubuntu installation, please see the basic security wiki. We also addressed the AV question as it's common.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Stonecold1995 on 2013-03-20
> **Ms. Daisy said:**
> Nope. Linux isn't more secure. If you would like to increase the security of your Ubuntu installation, please see the basic security wiki. We also addressed the AV question as it's common.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Linux isn't more secure?  Than Windows, really??  Uh, of course it's more secure.  Obviously it won't protect you on its own if you're not willing to learn, but even if you take away the fact that Windows is more popular, Linux DOES have quite a bit more inherent security (mostly due to its open source nature).  That's a fact.  To say that Linux is as secure or less secure than Windows is pretty strange.

---

### Post by Ms. Daisy on 2013-03-20
> **Stonecold1995 said:**
> Linux isn't more secure?  Than Windows, really??  Uh, of course it's more secure.  Obviously it won't protect you on its own if you're not willing to learn, but even if you take away the fact that Windows is more popular, Linux DOES have quite a bit more inherent security (mostly due to its open source nature).  That's a fact.  To say that Linux is as secure or less secure than Windows is pretty strange.
Linux desktops are far less targeted than Windows desktops. That does not indicate either's state of security. An attacker exploits a vulnerability . Both Windows and Linux have vulnerabilities. Simply because no one is actively exploiting Linux desktop vulnerabilities does not mean it's more secure. It means the risk is significantly lower (but not non-existent).

All of that gets tossed out the window if we start talking about Linux and Windows servers. Both are actively exploited by hackers. It is important to take steps to secure any server regardless of OS because of that.

---

### Post by Stonecold1995 on 2013-03-21
> **Ms. Daisy said:**
> Linux desktops are far less targeted than Windows desktops. That does not indicate either's state of security. An attacker exploits a vulnerability . Both Windows and Linux have vulnerabilities. Simply because no one is actively exploiting Linux desktop vulnerabilities does not mean it's more secure. It means the risk is significantly lower (but not non-existent).
Imagine all security patches and security research stopped.  Now imagine you took the default installation of Windows, and the default installation of Linux (any distro), and gave both to a professional hacker.  Which do you think would have the most vulnerabilities exploited?

Of course they have more vulnerabilities, but even after compensating for the popularity of Windows and the computer savvyness of Linux users, Linux still has fewer Vulnerabilities, and they are also patched quicker (e.g. critical Windows vulnerabilities being patched in months, or sometimes not at all vs Linux vulnerabilities often being patched in a matter of hours).

It all has to do with the fact that Linux is open source, and that there are far more people working on the Linux kernel (hell, even I could report a 0day if I found one, whereas if I found one on Windows chances are it wouldn't get patched for a long time, if ever) and dedicated to making it run well and securely rather than making it run the most profitably.

> **Ms. Daisy said:**
> All of that gets tossed out the window if we start talking about Linux and Windows servers. Both are actively exploited by hackers. It is important to take steps to secure any server regardless of OS because of that.
Yeah, both are being actively exploited.  But Windows (and the servers it can run, like IIS) is definitely more vulnerable, especially in its default configuration, than Linux.  That's just a fact.  Just because both CAN be exploited doesn't mean they're both just as easy to exploit.


Let me just get this straight.  You are saying Linux is NOT intrinsically more secure than Windows, even a little?  It's a very common myth that Linux is only secure because either it's less popular, or it's users are smart enough not to run "hawt_pr0n.avi.ext", but the myth is just that, a myth.  Not that Linux will protect you if you're foolish, it won't, but it does offer more protection by default (even if it's only advantage was superior privilege separation it would still be more secure).


This explains a lot of it:
[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

You still think Windows is just as secure?

---

### Post by Ms. Daisy on 2013-03-21
> You still think Windows is just as secure?Windows can be configured to be just as INSECURE as Linux. 

Fact: they both have vulnerabilities.
Fact: a beginning to moderately skilled hacker can crack both.
Fact: they have different vulns that are exploited in different ways (not more or less complex, just different)
Fact: you use default passwords or other stupid configurations on either you can get owned by the neighbor's teenager.
Fact: Windows and Linux can both be configured by users to improve security.

Ultimately securing any system is the responsibility of the administrator (at home that's probably you). Relying on inherent perceived security can be dangerous, especially if you think it will protect you from clicking and downloading any old thing.

---

### Post by Elfy on 2013-03-21
Please take the never ending which is more secure conversations to a thread in recurring discussion.

This thread is about post #1

---

### Post by haqking on 2013-03-21
> **gordie69 said:**
> hey guys just installed ubuntu 12.04 lts 64 bit and installed clamtk and was thinking if I need it or not I know linux is not targeted for viruses but I was thinking on my email contacts that still use Windows keeping everyone safe

Linux AV soultios are pretty poor to be honest but then so are most windows products.

It does not do any harm to run an AV solution on Linux especially if sharing files with windows users, pay it forward and all that.

Most people will say you "dont need" it on Linux which is subjective, IMO then no you dont for Linux for itself, but if sharing files then at least you are being proactive which is always a good thing.

As for the "more secure or less secure" argument above, it is pointless argument done to death, Linux and Windows are encompassing terms, to have the discussion you need to be specific about distros. kernels, versions, configurations etc and and then how to define "secure" as it is unquantifiable entity.

exploit-db, cve-mitre etc etc all list many entry points and Ubuntu specifically at [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) which if you look at the most recent from 21 March concerns ClamAV so is pertinent and ironic ;-)

Both in all versions and shapes and sizes are compromisable.

The end.

Peace

---

### Post by Ms. Daisy on 2013-03-21
> **haqking said:**
> Both in all versions and shapes and sizes are compromisable.

The end.

PeaceThat.

---

### Post by tancrackers on 2013-03-21
Linux OSes run on ~75+% of servers. Linux OSes have been proven to be more secure. Also, since there aren't any viruses out in the wild, the open source community has the advantage that it can in fact be patched up before any severe outbreaks take place.
Of course you have to worry about your security. Google Drive, iTunes, Adobe Reader and other ridiculous programs get security updates. It's on the user to make sure that a computer is safe. If you do that, you can even run Windows without an antivirus.

---

### Post by gordie69 on 2013-03-24
Thanks guys I installed the clamtk thinking receiving emails from my Windows user freinds I am not worried on myself only good old Windows 

Thanks guys
that wiki was a good hint to read

---

### Post by gordie69 on 2013-04-08
Thanks guys so I don't need to have a AV on Linux unless your receiving files from windows contacts or wine
correct

---

