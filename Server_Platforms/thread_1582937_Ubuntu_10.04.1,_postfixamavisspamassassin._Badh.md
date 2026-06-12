---
title: "Ubuntu 10.04.1, postfix/amavis/spamassassin. Badh"
date: 2010-09-27
forum: Server Platforms
---

### Post by LarsEriksson on 2010-09-27
As the title is saying, im using postfix with amavis and spamassassin as spam/virus filtering and its working great.

However, i get a "lot"(1-5/day) of "bad header" messages beeing quarantined by the server. And most of theese bad headers are false positives that i manually have to deliver to the correct mailbox.

How can i make amavis/spamassassin deliver bad header messages to the correct mailbox and not place them in quarantine?

Theese are my amavis settings.  (which file is used, 20-debian or 21-ubuntu??)

Settings in < /etc/amavis/conf.d/20-debian_defaults >
```
$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)
$final_banned_destiny     = D_REJECT;   # D_REJECT when front-end MTA
$final_spam_destiny       = D_DISCARD;
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)
```
Settings in < /etc/amavis/conf.d/21-ubuntu_defaults >
```
$final_virus_destiny      = D_DISCARD; # (defaults to D_BOUNCE)
$final_banned_destiny     = D_DISCARD;  # (defaults to D_BOUNCE)
$final_spam_destiny       = D_DISCARD;  # (defaults to D_REJECT)
$final_bad_header_destiny = D_PASS;  # (defaults to D_PASS), D_BOUNCE suggested
```

---

### Post by LarsEriksson on 2010-10-26
So, is there no solution to this? I cant possibly be the only one with this problem.

---

### Post by Blues- on 2010-10-26
Both my files have $final_bad_header_destiny = D_PASS
and mail with bad headers gets delivered.

Maybe the senders are already on your blacklist ?
Paste the X-SPAM headers in the message that your server bounces .. 
It could contain some leads ..

Here is an example ..

X-Spam-Flag: YES
X-Spam-Score: 7.182
X-Spam-Level: *******
X-Spam-Status: Yes, score=7.182 tagged_above=4 required=6.31 tests=[AWL=0.269,
	BAYES_99=3.5, HTML_MESSAGE=0.001, MIME_HTML_ONLY=1.457,
	URIBL_BLACK=1.955] autolearn=no

---

### Post by LarsEriksson on 2010-10-27
```
X-Envelope-From: <post@sender.biz>
X-Envelope-To: <info@ourserver.se>
X-Envelope-To-Blocked: 
X-Quarantine-ID: <E2CmWKroYt6E>
X-Amavis-Alert: BAD HEADER SECTION Non-encoded 8-bit data (char D6 hex):
	Subject: \326ka F\366rtj\344nsten [...]
```

Thats all X-something rows in the header


I dont use any blacklists, and this affects ALL messages marked as bad header, even internally and those are definitely not on any blacklist. 


Another example just popped in:    this is from our printer, telling me its out of paper. only it gets stuck in the spam filter.
```
X-Envelope-From: <print@ourcompany.se>
X-Envelope-To: <me@ourcompany.se>
X-Envelope-To-Blocked: 
X-Quarantine-ID: <S1XzLVkrL2dt>
X-Amavis-Alert: BAD HEADER SECTION Missing required header field: "Date"
```

btw:
Delivered-To: bad-header-quarantine

---

### Post by hawk2010 on 2010-11-16
I have the same issue my client's complained that they are not able to get the attachments from a particular sender. I saw the following error in the mail.log. The body seems OK but the attachment is disposed.

Nov 15 17:28:29 mail amavis[4211]: (04211-09) Passed BAD-HEADER,

Hope someone can help!

---

### Post by LarsEriksson on 2011-03-25
So, im still having this problem. Is there noone out there who can help?

---

### Post by LarsEriksson on 2011-03-28
I found a solution and a reason for this behavior.
My bad header mails are delivered BOTH to receiving address AND quarantine.
So..
$final_bad_header_destiny = D_PASS;
just means "Save a copy of bad header mails in quarantine folder".

I solved this by adding:
$bad_header_quarantine_to = undef;

to my Amavis conf., now bad header mails are delivered to recipient and no copy is saved to quarantine. The mail is however tagged with a "X-Amavis-Alert: BAD HEADER SECTION" in the header.

I hope this can help someone.

---

### Post by venol on 2011-04-07
thanks for the tutorial. Useful for me.

---

### Post by eagle1maledetto on 2011-04-10
Really useful, thanks.

---

### Post by duceduc on 2012-03-06
> **LarsEriksson said:**
> I found a solution and a reason for this behavior.
My bad header mails are delivered BOTH to receiving address AND quarantine.
So..
$final_bad_header_destiny = D_PASS;
just means "Save a copy of bad header mails in quarantine folder".

I solved this by adding:
$bad_header_quarantine_to = undef;

to my Amavis conf., now bad header mails are delivered to recipient and no copy is saved to quarantine. The mail is however tagged with a "X-Amavis-Alert: BAD HEADER SECTION" in the header.

I hope this can help someone.

I am having the same issue with my internal mail being tagged as bad-header. Where do we input the line? Is it the 50-user file in amavis?

---

