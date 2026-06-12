---
title: "OT: amavisd-new and Spamassassin &quot;Content analysis&quot; headers?"
date: 2006-01-20
forum: Server Platforms
---

### Post by jimwillsher on 2006-01-20
Hi all,

Sorry this is a bit off-topic, but I hope it's the correct forum.

I'm using amavisd-new to invoke spamassasin. All are latest builds from apt-get. I'm running breezy.

Spam notification messages always contain the "Content analysis details" which gives you the breakdown of the scoring, e.g.

pts rule name              description
---- ---------------------- --------------------------------------------------
 0.1 FORGED_RCVD_HELO       Received: contains a forged HELO
 1.7 SARE_SPEC_LEO_PHARM    BODY: obfuscated subject body
 0.5 INFO_TLD               URI: Contains an URL in the INFO top-level domain
 0.0 HTML_MESSAGE           BODY: HTML included in message
 1.7 SARE_SPEC_LEO_LINE03b  RAW: common Leo body text
 1.5 URIBL_JP_SURBL         Contains an URL listed in the JP SURBL blocklist
                            [URIs: zarazs.info]
 3.9 URIBL_SC_SURBL         Contains an URL listed in the SC SURBL blocklist
                            [URIs: zarazs.info]


In normal Spamasssisn you can force this to appear in all messages (in the headers) using the "Add Report" directive, but this doesn't work if amavisd-new invokes spamassassin.

Can anybody tell me what I need to change (probably in amavisd.conf) to force this report to appear in all mails? I already get the "X-Spam-Status" entry but it just gives the summaised version, e.g.

X-Spam-Status: No, hits=0.9 tagged_above=-999.0 required=5.0
     tests=INITIAL_INVEST, US_DOLLARS_3


Many thanks!

Jim

PS Have googled to death on this one!

---

