---
title: "clamAV error message ."
date: 2019-08-11
forum: Security
---

### Post by jedi123 on 2019-08-11
Hi when I update clamAV, I get the following errors. 

```
Sun Aug 11 12:33:28 2019 -> ClamAV update process started at Sun Aug 11 12:33:28 2019
Sun Aug 11 12:33:28 2019 -> ^Your ClamAV installation is OUTDATED!
Sun Aug 11 12:33:28 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.3
Sun Aug 11 12:33:28 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Sun Aug 11 12:33:28 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Sun Aug 11 12:33:32 2019 -> Downloading daily.cvd [100%]
Sun Aug 11 12:35:47 2019 -> daily.cvd updated (version: 25538, sigs: 1709967, f-level: 63, builder: raynman)
Sun Aug 11 12:35:47 2019 -> *Can't query daily.25538.93.1.0.6810DA54.ping.clamav.net
Sun Aug 11 12:35:47 2019 -> Downloading bytecode.cvd [100%]
Sun Aug 11 12:35:49 2019 -> bytecode.cvd updated (version: 330, sigs: 94, f-level: 63, builder: neo)
Sun Aug 11 12:35:50 2019 -> ***Can't query bytecode.330.93.1.0.6810DA54.ping.clamav.net**
Sun Aug 11 12:35:58 2019 -> Database updated (6276310 signatures) from db.local.clamav.net (IP: 104.16.218.84)
Sun Aug 11 12:35:58 2019 -> [B]!NotifyClamd: Can't find or parse configuration file /etc/clamav/clamd.conf
[/B]
```
I know that I have  to  upgrade to the new clamAV,  trying to figure that out , but what do these error messages mean   thanks.

---

### Post by SeijiSensei on 2019-08-12
If you're not running clamd, the daemonized version of ClamAV, then the last error doesn't apply to you.  It means that freshclam tried to notify clamd that the signature databases were updated and needed to be re-read.  Clamd is mostly used on servers.  I use it so [MailScanner]("http://www.mailscanner.info/") can check to see whether incoming mail contains a virus.  At one client site, we use it [in conjunction with the Squid proxy]("http://squidclamav.darold.net/") to scan every object downloaded from the web.

Trying to keep current with clamav is a nearly-impossible task.  I just wait until an update is released by the repository maintainers.  Otherwise you'll need to learn how to compile software from source.  

I don't know what the "can't query bytecode" error means. The line above says that bytecode.cvd was successfully updated, so I'd just ignore that complaint as well. Notice that the error concerns connecting to a network resource in the ping.clamav.net subdomain.  May be a transient network error.

---

### Post by espectro2 on 2019-09-10
[**[COLOR=#000000]SeijiSensei [/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")if he tried to execute the command
**sudo dpkg-reconfigure clamav-freshclam** disabling clamd or trying to activate again wouldn't work out what you think?

---

### Post by SeijiSensei on 2019-09-10
clamd isn't distributed as part of the standard clamav package.  It's packaged as [clamav-daemon]("https://packages.ubuntu.com/xenial/clamav-daemon"). The client is packaged as [clamdscan]("https://packages.ubuntu.com/xenial/clamdscan").

Everything else in his log looks fine other than the bytecode error which I discussed before.

---

