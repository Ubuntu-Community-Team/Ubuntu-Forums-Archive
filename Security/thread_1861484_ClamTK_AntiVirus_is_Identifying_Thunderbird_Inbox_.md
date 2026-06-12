---
title: "ClamTK AntiVirus is Identifying Thunderbird Inbox as Potential Threat/Infection"
date: 2011-10-15
forum: Security
---

### Post by jcwhite on 2011-10-15
[SIZE=2]Hi folks -

I just took the plunge and got my PC set up as a dual boot with WinXP Pro SP3 and Ubuntu 10.04 LTS and downloaded all the initial security updates after installation.  I also set up my firewall via Firestarter and installed ClamTK Anti-Virus (definitions updated as of today 10/15).

I performed a scan of my /home directory and it came up with this as a potential threat/infection:[/SIZE]  [SIZE=2]

Here is what appears in the warning box:[/SIZE] [SIZE=2]

Under File:[/SIZE] [SIZE=2]
/home/john/.thunderbird/6u3csag8.default/Mail/mail.comcast.net/Inbox

Under Status:[/SIZE] [SIZE=2]
Heuristics.Phishing.Email.SpoofedDomain

Under Action:[/SIZE] [SIZE=2]
None

Mozilla Thunderbird was installed via the Ubuntu Software Center and there are no emails in my inbox that would appear to pose a threat (I know all senders, etc.).  What's interesting is that there is no file or email listed in the warning box, just the inbox itself.  Therefore, I have a few questions:[/SIZE] [SIZE=2]

1. Why would this happen?[/SIZE] [SIZE=2]

2. Is this a false alarm?  [/SIZE] [SIZE=2]

3. If so, is there a way I can change any ClamTK settings to fix this or ignore the inbox on future scans?  I'm very careful to delete any emails from senders I don't recognize, so I could live without scanning the inbox if absolutely necessary.[/SIZE] [SIZE=2]

I appreciate any assistance you can offer.[/SIZE] [SIZE=2]
Thanks very much!
John[/SIZE]

---

### Post by haqking on 2011-10-15
> **jcwhite said:**
> [SIZE=2]Hi folks -

I just took the plunge and got my PC set up as a dual boot with WinXP Pro SP3 and Ubuntu 10.04 LTS and downloaded all the initial security updates after installation.  I also set up my firewall via Firestarter and installed ClamTK Anti-Virus (definitions updated as of today 10/15).

I performed a scan of my /home directory and it came up with this as a potential threat/infection:[/SIZE]  [SIZE=2]

Here is what appears in the warning box:[/SIZE] [SIZE=2]

Under File:[/SIZE] [SIZE=2]
/home/john/.thunderbird/6u3csag8.default/Mail/mail.comcast.net/Inbox

Under Status:[/SIZE] [SIZE=2]
Heuristics.Phishing.Email.SpoofedDomain

Under Action:[/SIZE] [SIZE=2]
None

Mozilla Thunderbird was installed via the Ubuntu Software Center and there are no emails in my inbox that would appear to pose a threat (I know all senders, etc.).  What's interesting is that there is no file or email listed in the warning box, just the inbox itself.  Therefore, I have a few questions:[/SIZE] [SIZE=2]

1. Why would this happen?[/SIZE] [SIZE=2]

2. Is this a false alarm?  [/SIZE] [SIZE=2]

3. If so, is there a way I can change any ClamTK settings to fix this or ignore the inbox on future scans?  I'm very careful to delete any emails from senders I don't recognize, so I could live without scanning the inbox if absolutely necessary.[/SIZE] [SIZE=2]

I appreciate any assistance you can offer.[/SIZE] [SIZE=2]
Thanks very much!
John[/SIZE]

Clam and any other Linux AV is not really needed per se unless for the benefit of shared files with windows.  They (especially clam) throw up lots of false positives. There are no known viruses in the wild for linux.

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild currently, the main reason using AV on linux is to scan incase you share files with windows users.  Malware writers have not as yet targeted Linux as they have other OS, they could do so, it is not to say that Linux is inpenetrable from Malware as it is not, however currently there are no known viruses which could effect it, conversely even though viruses have been known about for a very long time certain OS are still susceptible from viruses written 10 years ago.

No system is 100% secure when on a network or sharing data, security is best in a layered approach and with ongoing vigilence and awareness, the main security flaw in any system is PEBKAP = Problem Exists Between Keyboard And Person

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

**See here for Anti-Virus information:**

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)


A spoofed domain is not malware merely a spoofed domain.  If you know all your senders then dont worry about it as long as you trust the content and can verify it came from them.

as for firestarter, it is out of date and no longer updated and bug rich.  If you feel you need to run a firewall then use UFW/GUFW or straight CLI IPTables, though unless you running services which you need to firewall then it is debateable anyways.

---

### Post by jcwhite on 2011-10-15
[SIZE=2]Thanks very much for the info haqking. . .much appreciated![/SIZE]

---

### Post by oldos2er on 2011-10-15
Thread moved to Security Discussions.

---

