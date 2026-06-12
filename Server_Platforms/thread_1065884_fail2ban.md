---
title: "fail2ban"
date: 2009-02-10
forum: Server Platforms
---

### Post by CrimsonRider on 2009-02-10
I've recently begun using fail2ban as a means to stop overzealous  spammers.

Unfortunatly, I can't seem to get it to work with spamd/spamassassin. A positive spam match looks like thist

```
Feb 10 17:25:43 ruby spamd[6581]: spamd: result: Y 22 - HTML_IMAGE_ONLY_32,HTML_MESSAGE,MIME_HTML_ONLY,RCVD_IN_BL_SPAMCOP_NET,RCVD_IN_PBL,RCVD_IN_XBL,RDNS_NONE,SPF_HELO_NEUTRAL,URIBL_AB_SURBL,URIBL_BLACK,URIBL_JP_SURBL,URIBL_OB_SURBL,URIBL_RHS_DOB,URIBL_SBL scantime=15.0,size=3482,user=spamchecker,uid=1018,required_score=5.0,rhost=localhost,raddr=127.0.0.1,rport=34905,mid=<20090210162527.625BC11B3D83@ruby>,autolearn=spamp.
```

And there is no sender IP there. Now fail2ban can do a reguler expression there, but can't find the host. The host, with an ID is in another line. 

Is there any way to make spamc/spamd log the sender ip?
Is there any way to make fail2ban use a value from one line to do an expression on other line?

---

