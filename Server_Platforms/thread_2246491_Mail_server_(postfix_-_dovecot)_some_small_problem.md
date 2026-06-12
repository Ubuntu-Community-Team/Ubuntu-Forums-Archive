---
title: "Mail server (postfix - dovecot) some small problem"
date: 2014-10-01
forum: Server Platforms
---

### Post by littleghost on 2014-10-01
Hi everyone!

I have just setup an email system and it works fine. Only some small problem:

1: Use ip address instead domain name:

> [COLOR=#61523A][FONT=monospace]Received: by vps80627.ovh.net (Postfix, from userid 500)	id 7FFC31241590;[/FONT][/COLOR]	Wed,  1 Oct 2014 09:55:48 +0200 (CEST)
X-Spam-Checker-Version: SpamAssassin 3.4.0 (2014-02-07) on mail-tester.com
X-Spam-Level: ***
X-Spam-Status: No/3.7/5.0
X-Spam-Test-Scores: FSL_HELO_BARE_IP_2=1.539,HTML_MESSAGE=0.001,
	RCVD_NUMERIC_HELO=0.865,RDNS_NONE=1.274
X-Spam-Last-External-IP: [COLOR=#ff0000]**103.23.147.35**[/COLOR]
X-Spam-Last-External-HELO: ubuntusrv01.vnstyle.vn
X-Spam-Last-External-rDNS: 
X-Spam-Date-of-Scan: Wed, 01 Oct 2014 09:55:48 +0200
X-Spam-Report: *  0.9 RCVD_NUMERIC_HELO Received: contains an IP address
 used for HELO	*  0.0 HTML_MESSAGE BODY: HTML included in message	*  1.3
 RDNS_NONE Delivered to internal network by a host with no rDNS	*  1.5
 FSL_HELO_BARE_IP_2 No description available.
Received: from ubuntusrv01.vnstyle.vn (unknown [103.23.147.35])
	by vps80627.ovh.net (Postfix) with ESMTP id 9FBBD1240A3C
	for <web-WTWzTU@mail-tester.com>; Wed,  1 Oct 2014 09:55:46 +0200 (CEST)
Received: [COLOR=#ff0000]**from 103.23.147.35**[/COLOR] (localhost [127.0.0.1])
	by ubuntusrv01.vnstyle.vn (Postfix) with ESMTPA id 21E944008F [COLOR=#61523A][FONT=monospace]	for <web-WTWzTU@mail-tester.com>; Wed,  1 Oct 2014 14:55:44 +0700 (ICT)[/FONT][/COLOR]
there are my message was sent from my server. I already fill in /etc/postfix/main.cf that my hostname is ubuntusrv01.vnstyle.vn and my domain name is vnstyle.vn (my email system using multidomain, this message was sent from domain hailien.vn).
[B]Question: how to let postfix send an email with header containt domain name, or HELLO request containt domain name, not IP address? It's let spam guard program think my email is spam.

[/B]2: How i make my email system is signed with DKIM? any tutorial please!

Thank for any suggestion!

---

