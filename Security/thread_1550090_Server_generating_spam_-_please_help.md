---
title: "Server generating spam - please help"
date: 2010-08-10
forum: Security
---

### Post by JohnDoe78 on 2010-08-10
Hi,

My server hosting company sent me abuse notice stating that my server is generating spam. I thought it was because of some faulty PHP script in CMSs installed on several websites hosted by the server. Anyway, I googled a little bit and checked qmail logs and queue which is constantly growing at the specific time (mostly at night).

I then took desperate measures and stopped qmail and apache for a day but the number of messages in preprocess was still growing (checked with qmHandle tool)??? So I guessing it's not PHP related.

Please advise how to identify the source of the problem. My server is Ubuntu 8.04 LTS.

Thank you

---

### Post by lisati on 2010-08-10
I use postfix on my server, so my knowledge of qmail-specific issues and solutions is limited.

Have you taken a look at what the messages are?

The Spamcop website mentions qmail as being vulnerable to sending out misdirected bounces, which are considered by some people to be spam, and has some suggestions here: [http://www.spamcop.net/fom-serve/cache/329.html#bounces](http://www.spamcop.net/fom-serve/cache/329.html#bounces)

You might also want to check to see what some DNSBL lists have to say about your server - if you're listed, they might be able to provide some clues as to how your server is being perceived. As well as a "home grown" tool mentioned in my sig. there are also tools to help with this available at places like [debouncer.com]("http://debouncer.com") and [blacklistalert.org]("http://blacklistalert.org")

Edit: Is your server configured to act as a relay, where it accepts mail indiscriminately from anywhere and for anywhere? If so, you might want to close it up to accept only emails to/from your own network. Is another machine on your network a Windows machine with a virus?

---

### Post by JohnDoe78 on 2010-08-10
Thanks for quick reply. Tried your suggestions and yes my IP is blacklisted on several sites.

The header from one of the messages looks like this:

```

Received: (qmail 6874 invoked by uid 33); 10 Aug 2010 19:45:31 +0000
Date: 10 Aug 2010 19:45:31 +0000
Message-ID: <20100810194531.6871.qmail@[myserverdomain]>
To: rosevital_srl@yahoo.com
Subject: Contact Andrew Patterson for your payment.
From: FOREIGN & Common Wealth Office. <foreignoperationcommonwealth@live.com>
Reply-To: paymentofficercommonwealth@ciudad.com.ar
MIME-Version: 1.0^
Content-Type: text/plain^
Content-Transfer-Encoding: 8bit

```UID 33 is www-data in passwd. How is this possible if apache is stopped?

---

### Post by noway2 on 2010-08-11
Can you correlate the information in the header with your q-mail logs?
For example, the message has an ID of 20100810194531.6871 and you have a date/time and user id.  Does your qmail log verify that indeed UID 33 (Apache) sent this mail?

---

### Post by JohnDoe78 on 2010-08-11
Thank you guys for your help. I think I have located the source of the problem.
It was some stupid PHP mail script from one of the users. I deleted it and it looks like the queue is not filling up anymore. Just in case I will keep qmail service stopped for a few days to confirm this. Also I checked the logs and discovered multiple FTP sessions from an IP address originating from Brazil and China which seemed impossible. Guess that particular user picked up some nasty Gumblar variant which compromised his FTP account.
I was thinking of installing PHP mail header patch but it seemed unnecessary when the problem existed even with apache stopped. I guess I was wrong ](*,)

---

### Post by HermanAB on 2010-08-12
You'll probably find that your problem user is using a 1334 four character password and that his account got hacked by an automated script.

You got to configure PAM to enforce proper password security.

---

