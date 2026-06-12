---
title: "Postfix unable to receive from Gmail?"
date: 2012-05-17
forum: Server Platforms
---

### Post by poorangus on 2012-05-17
Hello,

Under Ubuntu 12.04 LTS, Postfix receives all mail 100% of the time from every service, except Gmail. I have researched this problem extensively but so far have come up empty.

This is what gets written to mail.log when GMail tries to deliver the email:

May 17 10:23:29 myhostname postfix/smtpd[3547]: connect from mail-pb0-f51.google.com[209.85.160.51]
May 17 10:23:29 myhostname postfix/smtpd[3547]: warning: TLS library problem: 3547:error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac:s3_pkt.c:1247:SSL alert number 20:
May 17 10:23:29 myhostname postfix/smtpd[3547]: lost connection after EHLO from mail-pb0-f51.google.com[209.85.160.51]
May 17 10:23:29 myhostname postfix/smtpd[3547]: disconnect from mail-pb0-f51.google.com[209.85.160.51]

The connection is being dropped immediately. I'm concerned about the "TLS library problem" but don't know how much this has to do with this particular issue. Any guidance would be appreciated, thanks.

EDIT: It should also be noted that mail sent through GMail's web interface is delivered as expected. Only email sent from an email client using Gmail's SMTP server has this issue. Bizarre.

---

### Post by lambart on 2012-05-17
Having same problems here... exact same error messages BUT for me even mails sent from gmail.com don't work.

I'm still investigating... will post fix here when I figure it out.

Eric

---

### Post by lisati on 2012-05-17
Looks like some kind of SSL (or possibly TLS) error to me. My best guess at the momemnt might be to check your SSL settings.

---

### Post by poorangus on 2012-05-17
Anything specific I should check for? The setup process handles that area of the configuration fairly automatically..

---

### Post by lambart on 2012-05-17
Some research.... no solution yet.

Got as far as to confirm (unsurprisingly) it's not actually limited to google/gmail. It appears to be the cipher type (@poorangus, did you leave out the log line starting with "Anonymous TLS connection established..."?)

From who-knows-who:

May 15 05:47:12 myhostname postfix/smtpd[1366]: Anonymous TLS connection established from unknown[209.85.213.47]: TLSv1 with cipher RC4-MD5 (128/128 bits)
May 15 05:47:12 myhostname postfix/smtpd[1366]: warning: TLS library problem: 1366:error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac:s3_pkt.c:1247:SSL alert number 20:
May 15 05:47:12 myhostname postfix/smtpd[1366]: lost connection after EHLO from unknown[209.85.213.47]


From google:
May 15 05:53:37 myhostname postfix/smtpd[1675]: Anonymous TLS connection established from unknown[209.85.213.47]: TLSv1 with cipher RC4-MD5 (128/128 bits)
May 15 05:53:37 myhostname postfix/smtpd[1675]: warning: TLS library problem: 1675:error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac:s3_pkt.c:1247:SSL alert number 20:
May 15 05:53:37 myhostname postfix/smtpd[1675]: lost connection after EHLO from unknown[209.85.213.47]

TLS connections using with other ciphers including DHE-RSA-AES256-SHA (256/256 bits), ECDHE-RSA-RC4-SHA (128/128 bits) and RC4-SHA (among others, probably) seem to work. mail-*.google.com usually uses RC4-MD5 (always causing a warning/lost collection), but sometimes uses ECDHE-RSA-RC4-SHA (128/128 bits) --maybe that's why you are getting some messages through, @poorangus?

---

### Post by lambart on 2012-05-17
I don't mean to be hijacking your thread, @poorangus, but since we seem to be having the same problem I hope we can figure it out together. By setting smtpd_tls_loglevel=2 and waiting for a mail from google.com, I got this, more detailed logging. Not sure if this will help anyone to help us...

May 17 15:43:02 myhostname postfix/smtpd[28328]: initializing the server-side TLS engine
May 17 15:43:02 myhostname postfix/smtpd[28328]: connect from mail-yw0-f47.google.com[209.85.213.47]
May 17 15:43:03 myhostname postfix/smtpd[28328]: setting up TLS connection from mail-yw0-f47.google.com[209.85.213.47]
May 17 15:43:03 myhostname postfix/smtpd[28328]: mail-yw0-f47.google.com[209.85.213.47]: TLS cipher list "aNULL:-aNULL:ALL:+RC4:@STRENGTH"
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:before/accept initialization
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 read client hello A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 write server hello A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 write certificate A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 write server done A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 flush data
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 read client key exchange A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 read finished A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 write change cipher spec A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 write finished A
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL_accept:SSLv3 flush data
May 17 15:43:03 myhostname postfix/smtpd[28328]: mail-yw0-f47.google.com[209.85.213.47]: save session DC174AEAF16104F9B5ACF53EFD8E242ED70DD37C4957B17780133B84CE85D295&s=smtp to smtpd cache
May 17 15:43:03 myhostname postfix/tlsmgr[28319]: put smtpd session id=DC174AEAF16104F9B5ACF53EFD8E242ED70DD37C4957B17780133B84CE85D295&s=smtp [data 127 bytes]
May 17 15:43:03 myhostname postfix/tlsmgr[28319]: write smtpd TLS cache entry DC174AEAF16104F9B5ACF53EFD8E242ED70DD37C4957B17780133B84CE85D295&s=smtp: time=1337294583 [data 127 bytes]
May 17 15:43:03 myhostname postfix/smtpd[28328]: Anonymous TLS connection established from mail-yw0-f47.google.com[209.85.213.47]: TLSv1 with cipher RC4-MD5 (128/128 bits)
May 17 15:43:03 myhostname postfix/smtpd[28328]: SSL3 alert read:fatal:bad record mac
May 17 15:43:03 myhostname postfix/smtpd[28328]: warning: TLS library problem: 28328:error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac:s3_pkt.c:1247:SSL alert number 20:
May 17 15:43:03 myhostname postfix/smtpd[28328]: lost connection after EHLO from mail-yw0-f47.google.com[209.85.213.47]
May 17 15:43:03 myhostname postfix/smtpd[28328]: disconnect from mail-yw0-f47.google.com[209.85.213.47]

---

### Post by poorangus on 2012-05-17
In confirming the absence of "Anonymous TLS connection established...", I initially arrived at DIFFERENT results.

Here's what was written to mail.log:

May 17 15:34:57 myhostname postfix/smtpd[4282]: connect from mail-pz0-f51.google.com[209.85.210.51]
May 17 15:34:57 myhostname postfix/master[3316]: warning: process /usr/lib/postfix/smtpd pid 4282 killed by signal 11
May 17 15:34:57 myhostname postfix/master[3316]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

When I tried again, the previous behavior returned:

May 17 15:37:14 myhostname postfix/smtpd[4289]: connect from mail-pz0-f51.google.com[209.85.210.51]
May 17 15:37:14 myhostname postfix/smtpd[4289]: warning: TLS library problem: 4289:error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac:s3_pkt.c:1247:SSL alert number 20:
May 17 15:37:14 myhostname postfix/smtpd[4289]: lost connection after EHLO from mail-pz0-f51.google.com[209.85.210.51]
May 17 15:37:14 myhostname postfix/smtpd[4289]: disconnect from mail-pz0-f51.google.com[209.85.210.51]

I'll take a closer look at the ones that are making it through ..

---

### Post by poorangus on 2012-05-17
No worries on the hijack :) .. though I'm wondering whether we do have the same problem, since you're getting "Anonymous TLS connection established..." and I'm not.

---

### Post by lambart on 2012-05-17
> **poorangus said:**
> No worries on the hijack :) .. though I'm wondering whether we do have the same problem, since you're getting "Anonymous TLS connection established..." and I'm not.

I expect that's a result of slightly different postfix configurations, maybe just a difference in logging config? It seems your setup isn't loging the cipher type at all, which certainly seems relevant.

Except for the cert/key/CA file settings, this is everything in my /etc/postfix/main.cf file that is related to TLS:

smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtp_tls_security_level = may
smtpd_tls_security_level = may
#smtpd_tls_auth_only = yes
smtp_tls_note_starttls_offer = yes
# TODO increase this loglevel if necessary for testing:
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
smtp_use_tls = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium

debug_peer_list = .google.com

That last line isn't TLS-related but I added it to try to debug this issue, and it doesn't appear to be helping at all. Note that the tls_loglevel was originally 1.

---

### Post by poorangus on 2012-05-17
@lambart - I synced my config with yours to make sure I arrived at the same result .. and I do not. To sync, I commented smtpd_tls_auth_only, and added tls_random_source, smtp_tls_security_level, smtpd_tls_security_level, smtp_tls_note_starttls_offer, and tls_random_source, then restarted the service.

Unfortunately this did not affect the behavior :confused:

---

### Post by lambart on 2012-05-17
I suppose we should have established this before, but are you using Dovecot SASL or Cyrus? I am using Dovecot. Ultimately I believe they both use openssl libraries to do the crypto stuff.

---

### Post by poorangus on 2012-05-17
Which one is set up by default? I didn't explicitly enable either one. How can I check?

Also, I'm now getting quite a few of the "smpd killed" messages .. this was just written to mail.log when I attempted to send a message from GMail web mail:

May 17 16:10:27 myhostname postfix/smtpd[4644]: connect from mail-gg0-f179.google.com[209.85.161.179]
May 17 16:10:27 myhostname postfix/master[4638]: warning: process /usr/lib/postfix/smtpd pid 4644 killed by signal 11

---

### Post by lambart on 2012-05-17
> **poorangus said:**
> Which one is set up by default? I didn't explicitly enable either one. How can I check?

Sorry, my mistake. Cyrus vs. Dovecot is for SASL, not TLS.

---

### Post by poorangus on 2012-05-17
Stumped ......

---

### Post by lambart on 2012-05-17
Well the forums are the first place I look for help... useful when there's a simple solution and/or someone else has already found it. But it appears this is a new issue. The fact that both of us are encountering it on the same day means it's probably a new issue either with postfix or how google is sending mail.

I've filed a bug on postfix and hopefully even if I do get "hit with a clue stick" by someone kind enough to point out my naivete, it will at least help me figure out what's going on.

[https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/1001040](https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/1001040)

---

### Post by poorangus on 2012-05-17
Not the conclusion I was hoping for, but I'll keep my fingers crossed. Unexpected bit of nonsense, this is.

---

### Post by poorangus on 2012-05-17
I found this, but won't be able to try for 20-30 minutes:

https://groups.google.com/forum/?fromgroups#!searchin/list.postfix.users/TLS$20library$20problem/list.postfix.users/aFy4I9igQgo/u3nnd0lcPW4J

EDIT: Don't bother. The "smtpd_tls_exclude_ciphers = AES" workaround doesn't work .. the patch might, but I'm not in a position to recompile Postfix right now..

---

### Post by lambart on 2012-05-17
@poorangus, I was about to give up for the day then I got an email with your last post on this thread.

I'm not sure exactly what you were planning to try in 20-30 mins, but that link you posted did give me enough information to "fix" the problem. I say "fix" but it's actually more of a workaround--because I have not fixed the issue with the RC4-MD5 cipher that was initially causing the problem. I've just asked google not to use it. And they were polite enough to choose another.

Here is the "fix". Add this line to /etc/postfix/main.cf:

smtpd_tls_exclude_ciphers = RC4-MD5

...and then run "service postfix reload" (I have used "service postfix restart" in the past but I think that is inadvisable as it kills things rather abruptly).

I have sent several test messages from my gmail account, which arrived immediately in my inbox! Google is now using RC4-SHA instead which seems to work fine.

I know you never saw any logging about the cipher type, but I suggest you try that config option anyway. If it works for you that pretty much confirms that our problems were the same, even if our logging output was slightly different.

Good luck and please let me know if this helped. Thanks for posting that thread from 2007 which inspired the workaround. :)

---

### Post by poorangus on 2012-05-17
Ah, an oldie but goodie eh? Really glad to hear this worked for you, as I'm sure it will for me .. will confirm momentarily. Great find!!

---

### Post by poorangus on 2012-05-17
Success!! My kindergarden teacher would have been proud of such teamwork. Thanks again for your help and for filing the bug report.

---

### Post by lambart on 2012-05-18
Hooray! Glad to hear it worked for you too. Hopefully our experience will help some other suffering soul who finds this thread.

---

### Post by nariub on 2012-05-28
smtpd_tls_exclude_ciphers = RC4-MD5

worked for me too..
just upgraded from 11.10 to 12.04 and noticed I could not receive email from gmail (one of my email tests)

thanks

---

### Post by nariub on 2012-05-28
now my gingerbread android phone is insisting that i dont even have ssl enabled on my mail server..

i should have waited on the 12.04 upgrade.

I see it trying with RC4-SHA

my PC email clients are quite happy with my new server.

---

### Post by lambart on 2012-05-28
> **nariub said:**
> now my gingerbread android phone is insisting that i dont even have ssl enabled on my mail server..

i should have waited on the 12.04 upgrade.

I see it trying with RC4-SHA

my PC email clients are quite happy with my new server.

I would have waited on 12.04, but my old Debian 5 server died two weeks ago and I didn't want to start "fresh" with a 2-year old OS (i.e. Ubuntu 10.04).

So what happens if you try adding RC4-SHA to smtpd_tls_exclude_ciphers? There's probably some cipher in android's arsenal that won't break postfix. 

smtpd_tls_exclude_ciphers = RC4-MD5, RC4-SHA

see [http://www.postfix.org/postconf.5.html#smtpd_tls_exclude_ciphers]("http://www.postfix.org/postconf.5.html#smtpd_tls_exclude_ciphers")

Funny thing is, I checked my server logs and I've received lots of messages authenticated using RC4-SHA and the don't seem to have had a problem.

---

### Post by nariub on 2012-06-04
My phone tries, indicates SSL isn't available on my email server and quits.
Email server sees the attempt come in but times out.

It was working fine on the 11.10 server prior to the upgrade.

I am only excluding RC4-MD5 now..

**smtpd_tls_exclude_ciphers = RC4-MD5**

switch the phone from SSL to TLS gives me a segfault
[I]Jun  4 12:37:03 SERVER kernel: [11873.651582] imap-login[6233]: segfault at 7f4f0dcba82c ip 00007f4b0b9b9031 sp 00007fff8aa73dc0 error 4 in libcrypto.so.1.0.0[7f4b0b930000+19f000]


[/I]Dovecot.log says.
[I]2012-06-04 12:29:14 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-04 12:29:21 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-04 12:29:23 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-04 12:29:28 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-04 12:29:34 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-04 12:29:41 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-04 12:29:48 imap-login: Info: Disconnected (no auth attempts): rip=XXX.XXX.XXX.XXX, lip=YYY.YYY.YYY.YYY, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20[/I]

---

