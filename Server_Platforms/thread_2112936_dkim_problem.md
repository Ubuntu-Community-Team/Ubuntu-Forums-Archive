---
title: "dkim problem"
date: 2013-02-06
forum: Server Platforms
---

### Post by mirceabondar on 2013-02-06
Hy. I install opendkim in ubuntu server and when send mail from my server to yahoo for test dkim signature, in yahoo header dkim is no pass why?

My opendkim conf:
```
# This is a basic configuration that can easily be adapted to suit a standard
# installation. For more advanced options, see opendkim.conf(5) and/or
# /usr/share/doc/opendkim/examples/opendkim.conf.sample.

# Log to syslog
Syslog                  yes
# Required to use local socket with MTAs that access the socket as a non-
# privileged user (e.g. Postfix)
UMask                   002

# Sign for example.com with key in /etc/mail/dkim.key using
# selector '2007' (e.g. 2007._domainkey.example.com)
Domain                  andortipo.ro
KeyFile         /etc/mail/dkim.key
Selector                2013

# Commonly-used options; the commented-out versions show the defaults.
#Canonicalization       simple
#Mode                   sv
#SubDomains             no
#ADSPDiscard            no

# Always oversign From (sign using actual From and a null From to prevent
# malicious signatures header fields (From and/or others) between the signer
# and the verifier.  From is oversigned by default in the Debian pacakge
# because it is often the identity key used by reputation systems and thus
# somewhat security sensitive.
OversignHeaders         From

# List domains to use for RFC 6541 DKIM Authorized Third-Party Signatures
# (ATPS) (experimental)

#ATPSDomains            example.com
KeyTable           /etc/opendkim/KeyTable
SigningTable       /etc/opendkim/SigningTable

```

dkim signature in dns zone:
```
2013._domainkey.andortipo.ro. IN TXT "v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBfTkt/u7AGYBzsICTDHNDmhZzYE3QFArcOt/otFWika8J8pT1mojnQGnq+DIHhLV/hVdShxEb+i3DngWUCFc368HhzOiT3dROdVGDsKTLxECdgitwmfpJ6pgbnVcmRhCYfjgczPTWTUjJETgOuWFlgzZT1iuJoRzbBmqa5TdScwIDAQAB"
```

In [http://dkimcore.org/c/keycheck](http://dkimcore.org/c/keycheck) (This is a valid DKIM key record) but in yahoo mail header
```
Authentication-Results: mta1054.mail.ac4.yahoo.com  from=andortipo.ro; domainkeys=neutral (no sig);  from=andortipo.ro; dkim=permerror (no key)
Received: from 127.0.0.1  (EHLO mail.andortipo.ro) (95.77.176.146)
  by mta1054.mail.ac4.yahoo.com with SMTP; Wed, 06 Feb 2013 00:28:22 -0800
Received: by mail.andortipo.ro (Postfix, from userid 33)
	id 6C57A24432F; Wed,  6 Feb 2013 10:28:19 +0200 (EET)
DKIM-Signature: v=1; a=rsa-sha256; c=simple/simple; d=andortipo.ro;
	s=default; t=1360139299;
	bh=yNBcG5+nIkwAIrZrKcWf8cZvq6e8tsWjimu2zpxPiAI=;
	h=To:Subject:Date:From:From;
	b=cjqxbrpdOqnjVSTJ7MdfUb1iI123FidnwxBfCu9Q4Lc1uD0bnikT/pwqu9eyjqNSo
	 qQm6neEJtMvNPLIoAD6CftvTXMvjyu6FkpsZUWVgd5U6kK0pgK5zTkd5jas7n8CJi7
	 NGjCgRtomelpo3cX0Pjb/jJceVWjco6pnjrOOsEA=
```

---

