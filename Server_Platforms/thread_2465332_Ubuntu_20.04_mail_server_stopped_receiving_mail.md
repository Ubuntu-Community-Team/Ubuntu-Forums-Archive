---
title: "Ubuntu 20.04 mail server stopped receiving mail"
date: 2021-07-29
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2021-07-29
Sometime early this morning my mail server stopped accepting mail.
The server is Ubuntu 20.04 LTS running exim4 and dovecot. I use clamav to screen incoming messages
Every incoming messages is rejected with an error like this in /var/log/mainlog for exim4. 

```
 1m98wT-001yKs-Vh malware acl condition: clamd /var/run/clamav/clamd.ctl : unable to connect to UNIX socket (/var/run/clamav/clamd.ctl): Connection refused
2021-07-29 12:31:30 
 1m98wT-001yKs-Vh H=mail01.go.informaconnect01.com [129.145.76.159] X=TLS1.3:ECDHE_X25519__RSA_PSS_RSAE_SHA256__AES_256_GCM:256 CV=no F=<bounce@go.informaconnect01.com> temporarily rejected after DATA
2021-07-29 12:31:30 no host name found for IP address 103.114.105.26
```

Looking at the file referenced above I get this:
```
/var/run/clamav# ls -ld *
srw-rw-rw- 1 clamav clamav 0 Jul 22 13:20 clamd.ctl
-rw-rw-r-- 1 root   root   7 Jul 29 12:30 freshclam.pid
```

Not sure what that is supposed to look like but it doesn't look right to me.

It looks like the clamav-daemon crashed:

```
# systemctl status clamav-daemon
&#9679; clamav-daemon.service - Clam AntiVirus userspace daemon
     Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
    Drop-In: /etc/systemd/system/clamav-daemon.service.d
             &#9492;&#9472;extend.conf
     Active: failed (Result: core-dump) since Thu 2021-07-29 05:22:59 EDT; 7h ago
       Docs: man:clamd(8)
             man:clamd.conf(5)
             https://www.clamav.net/documents/
   Main PID: 1711 (code=dumped, signal=SEGV)

Jul 29 03:20:02 thelma clamd[1711]: Thu Jul 29 03:20:02 2021 -> SelfCheck: Database status OK.
Jul 29 03:24:13 thelma clamd[1711]: Thu Jul 29 03:24:13 2021 -> ~/var/spool/exim4/scan/1m90Oq-001ir7-H7/1m90Oq-001ir7-H7.eml: Win.Worm.Mydoom-5(5>
Jul 29 03:24:16 thelma clamd[1711]: Thu Jul 29 03:24:16 2021 -> ~/var/spool/exim4/scan/1m90Ot-001irF-Vs/1m90Ot-001irF-Vs.eml: Win.Worm.Mydoom-5(5>
[B]Jul 29 04:20:02 thelma clamd[1711]: Thu Jul 29 04:20:02 2021 -> SelfCheck: Database status OK.
Jul 29 05:20:02 thelma clamd[1711]: Thu Jul 29 05:20:02 2021 -> SelfCheck: Database modification detected. Forcing reload.[/B]
Jul 29 05:20:02 thelma clamd[1711]: Thu Jul 29 05:20:02 2021 -> Reading databases from /var/lib/clamav
Jul 29 05:20:25 thelma clamd[1711]: Thu Jul 29 05:20:25 2021 -> Database correctly reloaded (8556719 signatures)
Jul 29 05:20:25 thelma clamd[1711]: Thu Jul 29 05:20:25 2021 -> Activating the newly loaded database...
Jul 29 05:22:59 thelma systemd[1]: clamav-daemon.service: Main process exited, code=dumped, status=11/SEGV
Jul 29 05:22:59 thelma systemd[1]: clamav-daemon.service: Failed with result 'core-dump'.
```

Restarting it seems to have allowed email to begin flowing. However I'd still like to know what caused this. I'll monitor it for a while and if it doesn't happen again I'll mark this thread closed.

```
# systemctl start clamav-daemon
```

Earlier this morning I had hundreds of error messages exactly like this:

```
2021-07-29 00:00:15 SMTP protocol error in "AUTH LOGIN" H=(ylmf-pc) [77.247.110.156] AUTH command used when not advertised
2021-07-29 00:00:15 no host name found for IP address 77.247.110.156
```

This is the information on that message in rejectlog for the error above

```
Message-ID: 20210729163105.318565-1-jsikorski@codeweavers.com
2021-07-29 12:31:30 1m98wT-001yKs-Vh H=mail01.go.informaconnect01.com [129.145.76.159] X=TLS1.3:ECDHE_X25519__RSA_PSS_RSAE_SHA256__AES_256_GCM:256 CV=no F=<bounce@go.informaconnect01.com> temporarily rejected after DATA
Envelope-from: <bounce@go.informaconnect01.com>
Envelope-to: <debbie@steinmetznet.com>
P Received: from mail01.go.informaconnect01.com ([129.145.76.159])
        by smtp.steinmetznet.com with esmtps  (TLS1.3) tls TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
        (Exim 4.93)
        (envelope-from <bounce@go.informaconnect01.com>)
        id 1m98wT-001yKs-Vh
```


Can anyone shed some light on what may have happened?

---

### Post by MAFoElffen on 2021-07-29
I checked the bug reports from Clam AV on the specific error of "clamav-daemon.service: Main process exited, code=dumped, status=11/SEGV" at HowToForge... Seems that people started having this problem intermittently about a year ago, and this problem is still happening and open. Most think this problem occurs when the RAM and Swap runs out or is close to running out, then the Service crashes. Although, some involved don't believe that.
  -  [https://www.howtoforge.com/community/threads/clamav-daemon-keeps-crashing.82511/](https://www.howtoforge.com/community/threads/clamav-daemon-keeps-crashing.82511/)

The work-around they came up with for it was to do a scheduled restart of the service daily in a convenient period of time. That seems to work for people.

---

### Post by TheFu on 2021-07-29
103.114.105.26 is from Vietnam and since they don't have a valid reverse DNS, I'd call it a spam server.
The owner for that IP is "Son Thuy Investment Trading and Service Company Limited". Can you think of any reason that anyone in your company would be getting email from there?   

A small company like that would definitely be a target for spammers to take over and start spamming the world from.

ylmf-pc is a known spammer signature connection that fails on all proper SMTP servers. No valid connection will ever happen from servers with that signature.

I just checked my email gateway boxes.  Seems a few small subnets (/24) from NL were hacked and are being used to flood my spam filters. I don't feel guilty blocking them at all.

---

### Post by rsteinmetz70112 on 2021-07-30
Thanks. 

This has not happened before, I've been running this server for about 15 years, on different versions of Ubuntu and different hardware but the set up is the same. 
I don't think it was running out of RAM or SWAP. I just checked and this is what I got:

```
# free
              total        used        free      shared  buff/cache   available
Mem:       16122812     1882540      228780       10196    14011492    13893032
Swap:      24969208      316160    24653048
```

The numbers above are typical of what I normally see. I didn't think to check yesterday, but after the clamd service dumped I'm pretty sure any memory would have been released.

I restarted exim4, dovcecot and clamd and everything seemed to go back to normal. The email that was temporarily rejected seems to have all been delivered by now. I'll monitor it closer and see if it happens again. I see no evidence that the server was compromised, or that it's generating any spam.

---

### Post by TheFu on 2021-07-30
Wasn't there a CVE against exim last week?  I don't use that MTA, so don't follow it closely.
Clam updates and ubuntu updates sometimes have conflicts.  Usually it is just that new versions of clamd are needed to load the new signature data files. For mail systems that try to update hourly, those errors can be a problem in the logs.
For example:
```
 Last Status:
    WARNING: Your ClamAV installation is OUTDATED!
    WARNING: Local version: 0.102.4 Recommended version: 0.103.3
    DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
    daily.cld database is up to date (version: 26247, sigs: 1964784, f-level: 90, builder: raynman)
    main database available for update (local version: 59, remote version: 61)
    ERROR: cdiff_apply: lseek(desc, -350, SEEK_END) failed
    ERROR: downloadPatch: Can't apply patch
    WARNING: Incremental update failed, trying to download main.cvd
...
```
The old DB is still working, so the updates aren't really THAT critical, at least not for my small email needs.

Logwatch is really handy at having logs filtered to the important points.

---

### Post by rsteinmetz70112 on 2021-07-30
I tend to stay with the versions in the repositories. 

The most recent CVEs for exim4 I see are from May and affects versions before 4.94.2. My version says it is 4.93.3 and was last updated in April 2021. 

As for clamav, I've checked that error message and it seems to be more of a warning than an actual error.  I also checked the version again today and it now reporting 0.103.2. I reinstalled clamav it must have garbed a newer version.

With Ubuntu there may also have been security patches applied to the versions in the repositories.

---

