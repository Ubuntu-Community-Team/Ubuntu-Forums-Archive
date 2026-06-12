---
title: "sa-update problem"
date: 2010-01-07
forum: Server Platforms
---

### Post by michellez on 2010-01-07
Hi,

I'm trying to run sa-update but am getting the following:

```
channel: SHA1 verification failed, channel failed
```

sa-update -D gives:

```
[19164] dbg: generic: lint check of site pre files succeeded, continuing with channel updates
[19164] dbg: channel: reading MIRRORED.BY file
[19164] dbg: channel: found mirror http://spamassassin.kluge.net/updates/
[19164] dbg: channel: selected mirror http://spamassassin.kluge.net/updates
[19164] dbg: http: GET request, http://spamassassin.kluge.net/updates/895075.tar.gz
[19164] dbg: http: GET request, http://spamassassin.kluge.net/updates/895075.tar.gz.sha1
[19164] dbg: http: GET request, http://spamassassin.kluge.net/updates/895075.tar.gz.asc
[19164] dbg: http: IMS GET request, http://spamassassin.kluge.net/updates/MIRRORED.BY, Fri, 07 Nov 2008 18:52:38 GMT
[19164] dbg: sha1: verification wanted: 895075
[19164] dbg: sha1: verification result: 921449e98c8e6064aa01b0605a333b8fb222e90b
channel: SHA1 verification failed, channel failed
[19164] dbg: generic: cleaning up temporary directory/files
[19164] dbg: diag: updates complete, exiting with code 4

```

SA version: SpamAssassin version 3.2.4 running on Perl version 5.8.8
Ubuntu version: 8.04

Thanks for you help
Michelle

---

### Post by ian dobson on 2010-01-08
Hi,

Looks as if your gpg key is incorrect. Have a look here [http://wiki.apache.org/spamassassin/RuleUpdates](http://wiki.apache.org/spamassassin/RuleUpdates) on how to update/correct it.

Regards
Ian Dobson

---

### Post by michellez on 2010-01-08
Sorry if I'm being dumb but how would I know what the key should be?

I don't know if this is the issue though because spamassassin.kluge.net doesn't actually resolve to an IP so not sure how it "appears" to be connecting to it!

Thanks,
Michelle

---

### Post by ian dobson on 2010-01-09
Hi,

When I run sa-update -d I get this:-

```

[26224] dbg: logger: adding facilities: all
[26224] dbg: logger: logging level is DBG
[26224] dbg: generic: SpamAssassin version 3.2.5
[26224] dbg: config: score set 0 chosen.
[26224] dbg: dns: is Net::DNS::Resolver available? yes
[26224] dbg: dns: Net::DNS version: 0.65
[26224] dbg: generic: sa-update version svn607589
[26224] dbg: generic: using update directory: /var/lib/spamassassin/3.002005
[26224] dbg: diag: perl platform: 5.010000 linux
[26224] dbg: diag: module installed: Digest::SHA1, version 2.12
[26224] dbg: diag: module installed: HTML::Parser, version 3.59
[26224] dbg: diag: module installed: Net::DNS, version 0.65
[26224] dbg: diag: module installed: MIME::Base64, version 3.07_01
[26224] dbg: diag: module installed: DB_File, version 1.816_1
[26224] dbg: diag: module installed: Net::SMTP, version 2.31
[26224] dbg: diag: module installed: Mail::SPF, version v2.006
[26224] dbg: diag: module installed: Mail::SPF::Query, version 1.999001
[26224] dbg: diag: module not installed: IP::Country::Fast ('require' failed)
[26224] dbg: diag: module not installed: Razor2::Client::Agent ('require' failed)
[26224] dbg: diag: module installed: Net::Ident, version 1.20
[26224] dbg: diag: module installed: IO::Socket::INET6, version 2.54
[26224] dbg: diag: module installed: IO::Socket::SSL, version 1.22
[26224] dbg: diag: module installed: Compress::Zlib, version 2.015
[26224] dbg: diag: module installed: Time::HiRes, version 1.9719
[26224] dbg: diag: module not installed: Mail::DomainKeys ('require' failed)
[26224] dbg: diag: module not installed: Mail::DKIM ('require' failed)
[26224] dbg: diag: module installed: DBI, version 1.607
[26224] dbg: diag: module installed: Getopt::Long, version 2.37
[26224] dbg: diag: module installed: LWP::UserAgent, version 5.823
[26224] dbg: diag: module installed: HTTP::Date, version 5.810
[26224] dbg: diag: module installed: Archive::Tar, version 1.44
[26224] dbg: diag: module installed: IO::Zlib, version 1.09
[26224] dbg: diag: module not installed: Encode::Detect ('require' failed)
[26224] dbg: gpg: Searching for 'gpg'
[26224] dbg: util: current PATH is: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
[26224] dbg: util: executable for gpg was found at /usr/bin/gpg
[26224] dbg: gpg: found /usr/bin/gpg
[26224] dbg: gpg: release trusted key id list: 5E541DC959CB8BAC7C78DFDC4056A61A5244EC45 26C900A46DD40CD5AD24F6D7DEE01987265FA05B 0C2B1D7175B852C64B3CDC716C55397824F434CE
[26224] dbg: channel: attempting channel updates.spamassassin.org
[26224] dbg: channel: update directory /var/lib/spamassassin/3.002005/updates_spamassassin_org
[26224] dbg: channel: channel cf file /var/lib/spamassassin/3.002005/updates_spamassassin_org.cf
[26224] dbg: channel: channel pre file /var/lib/spamassassin/3.002005/updates_spamassassin_org.pre
[26224] dbg: channel: metadata version = 895075
[26224] dbg: dns: 5.2.3.updates.spamassassin.org => 895075, parsed as 895075
[26224] dbg: channel: current version is 895075, new version is 895075, skipping channel
[26224] dbg: diag: updates complete, exiting with code 1

```

Looks as if my system is using  updates.spamassassin.org for updates. What version of spamassassin are you running? I'm on 3.2.5.

And have a look here:- [http://forums.freebsd.org/showthread.php?t=3521](http://forums.freebsd.org/showthread.php?t=3521), it's not linux/ubuntu but they have a solution.

Regards
Ian Dobson

---

### Post by michellez on 2010-01-09
Super. Sorted!

Cheers :)

Michelle

---

### Post by ian dobson on 2010-01-09
Hi,

Any chance that you write/edit you last post including how you fixed the problem. It'll help other people in the future maybe.

Regards
Ian Dobson

---

### Post by michellez on 2010-01-10
No prob. Basically followed the advice in the link you gave.

I commented out:
[http://spamassassin.kluge.net/updates/](http://spamassassin.kluge.net/updates/)

and added:
[http://daryl.dostech.ca/sa-update/asf/](http://daryl.dostech.ca/sa-update/asf/)
[http://www.sa-update.pccc.com/](http://www.sa-update.pccc.com/)

to:
/var/lib/spamassassin/3.002004/updates_spamassassin_org/MIRRORED.BY

Thanks,
Michelle

---

