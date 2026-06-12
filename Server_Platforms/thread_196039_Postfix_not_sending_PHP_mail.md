---
title: "Postfix not sending PHP mail"
date: 2006-06-13
forum: Server Platforms
---

### Post by rem on 2006-06-13
Hi,

I'm using Dapper as a desktop environment and as a PHP / MySQL development local server. I'm having this issues with Postifx which is not sending my PHP emails, thus is making my life awfully miserable because it's impossible for me to test my applications while I'm developing them... As I heard, Postfix should run out-of-the-box default installed but it isn't! I tried to use Sendmail but had problems there too... I searched the forums and googled all this out too but didn't managed to find a fix... Please help me find a method (anything) to help me properly send my PHP mails and do my work...

Thanks a million in advance, next is a part of my mail log:

```
Jun 14 00:09:05 localhost postfix/qmgr[25796]: 973D09E79D: from=<www-data@localhost>, size=333, nrcpt=1 (queue active)
Jun 14 00:09:07 localhost postfix/smtp[25816]: 973D09E79D: to=<test1@eclipsedesign.net>, relay=eclipsedesign.net[194.117.236.18], delay=4, status=bounced (host eclipsedesign.net[194.117.236.18] said: 550-Verification failed for <www-data@localhost> 550-unrouteable mail domain "localhost" 550 Sender verify failed (in reply to RCPT TO command))
Jun 14 00:09:07 localhost postfix/cleanup[25811]: DCA6F9E8F6: message-id=<20060613210907.DCA6F9E8F6@localhost>
Jun 14 00:09:07 localhost postfix/qmgr[25796]: DCA6F9E8F6: from=<>, size=2257, nrcpt=1 (queue active)
Jun 14 00:09:07 localhost postfix/qmgr[25796]: 973D09E79D: removed
Jun 14 00:09:07 localhost postfix/local[25818]: DCA6F9E8F6: to=<rem@localhost>, orig_to=<www-data@localhost>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jun 14 00:09:07 localhost postfix/qmgr[25796]: DCA6F9E8F6: removed
```

---

### Post by linuchsan on 2006-06-13
Have you setup the right user?

Jun 14 00:09:07 localhost postfix/smtp[25816]: 973D09E79D: to=<test1@eclipsedesign.net>, relay=eclipsedesign.net[194.117.236.18], delay=4, status=bounced (host eclipsedesign.net[194.117.236.18] said: 550-Verification failed for <www-data@localhost> 550-unrouteable mail domain "localhost" 550 Sender verify failed (in reply to RCPT TO command))

---

### Post by rem on 2006-06-13
Don't understand ... how can I do that? I don't kow if I set up the right user, I just installed Postfix and did nothing to it... As I heard, there's nothing to be done to it. Should be working with the default installation ... or isn't it so?

---

### Post by linuchsan on 2006-06-14
You have to point the relayhost to the smtp server of your isp.
edit /etc/postfix/main.cf and add:
relayhost = smtpserver.your.isp

---

### Post by rem on 2006-06-14
That's a very good idea, but already tried that and the ISP SMTP server needs authentication too and sort of leads me right from where I started ...

---

### Post by MJN on 2006-06-14
The 'sender verify' bit in the error is the key - it's not happy that you're claiming to be somebody@**localhost**...

Try putting a from address in your PHP command however, if your ISP's server require authentication then you're out of luck as you say. Many (most?) don't as they will allow unauthenticated connections to relay if they're from a netblock owned by them.... your mileage may vary of course.

EDIT: I've just tried it and can confirm your ISP doesn't require authentication in this instance - it simply requires you to have a 'valid' From: address (i.e. not @localhost). You should find an e-mail (badly formed - I didn't use a client) sat in your test1 account...

EDIT2: Just realised eclipsedesign.net isn't your ISP is it?! I take it it's you or someone else you know? Either way, if you'll only be sending mail to <someone>@eclipsedesign.net then give a valid From: address as mentioned and you'll be fine.

EDIT3: Okay okay... now I've realised that eclipsedesign is who you work for/as....

Mathew (who clearly wouldn't make a very good detective)

---

### Post by rem on 2006-06-14
Yes indeed MJN I found the test email... that's weird, I just called today and checked with them. They said I need SMTP authentication :) Ok, I'm glad that I don't need such thing!!! Thanks a lot!

The thing is I'm already using a reply-to header in my PHP code... and still... heck, this thing's eating me alive. Don't quite understand why this now, but it properly worked with Breezy???

---

### Post by rem on 2006-06-14
[QUOTE=rem]Yes indeed MJN I found the test email... that's weird, I just called today and checked with them. They said I need SMTP authentication :) Ok, I'm glad that I don't need such thing!!! Thanks a lot!

The thing is I'm already using a reply-to header in my PHP code... and still... heck, this thing's eating me alive. Don't quite understand why this now, but it properly worked with Breezy???[/QUOTE]

On the other hand, the eclipsedesign.net domain is different from my ISP. eclipse is not my ISP. just my development live server, hosted with some other company. I don't have an email account set with my ISP.

---

### Post by MJN on 2006-06-14
You will require authentication to send mail to someone other than eclipsedesign.net however it's not require for someone@eclipse otherwise they'd never receive any e-mail..

Notwithstanding the above, **Reply-To**: is not the same as **From:** (only the latter is used during the SMTP sequence, which is where the address checking is being done)

Mathew

---

### Post by MJN on 2006-06-14
I think we're both typing at the same time here! ;)

Anyway, check back at my 'EDITs' and indeed ignore any of the ISP malarky... Just put a proper From header in your PHP command and you'll be sorted!

Mathew

---

### Post by rem on 2006-06-14
[QUOTE=MJN]The 'sender verify' bit in the error is the key - it's not happy that you're claiming to be somebody@**localhost**...

Try putting a from address in your PHP command however, if your ISP's server require authentication then you're out of luck as you say. Many (most?) don't as they will allow unauthenticated connections to relay if they're from a netblock owned by them.... your mileage may vary of course.

EDIT: I've just tried it and can confirm your ISP doesn't require authentication in this instance - it simply requires you to have a 'valid' From: address (i.e. not @localhost). You should find an e-mail (badly formed - I didn't use a client) sat in your test1 account...

EDIT2: Just realised eclipsedesign.net isn't your ISP is it?! I take it it's you or someone else you know? Either way, if you'll only be sending mail to <someone>@eclipsedesign.net then give a valid From: address as mentioned and you'll be fine.

EDIT3: Okay okay... now I've realised that eclipsedesign is who you work for/as....

Mathew (who clearly wouldn't make a very good detective)[/QUOTE]


You're right! Man so impressive. Try to imagine that for some one like me who doesn't know anything about linux server administration this is pure magic!!! :)

---

### Post by rem on 2006-06-14
[QUOTE=MJN]I think we're both typing at the same time here! ;)

Anyway, check back at my 'EDITs' and indeed ignore any of the ISP malarky... Just put a proper From header in your PHP command and you'll be sorted!

Mathew[/QUOTE]

Let's hope so!!! I'll do that and get back to you here and report. Maybe others will benefit from this too ! Thanks a lot for your involvement! Really appreciate it :)

---

### Post by MJN on 2006-06-14
Doesn't know anything? I wouldn't say that... now you know that some MTAs require a valid From address... ;)

As you no doubt already know given what it appears you work in/as, it's when things *don't* work that you learn something... Heck, maybe that's why Linux seems to teach us so much! ;)

Mathew

---

### Post by rem on 2006-06-14
> 
Doesn't know anything? I wouldn't say that... now you know that some MTAs require a valid From address...

As you no doubt already know given what it appears you work in/as, it's when things don't work that you learn something... Heck, maybe that's why Linux seems to teach us so much! 


Can't agree more... I love Linux and Ubuntu in special. I don't get discouraged when things like this happen but sometimes really can't find a solution no matter what... Obviously I came from Windows and trying hard to ditch old habbits :)

Speaking of.. is not working... I know, I know...
Here are my mail headers:

[PHP]$headers = 'From: rem@eclipsedesign.net';
$headers .= 'Reply-To: rem@eclipsedesign.net'; 
mail("test1@eclipsedesign.net","Subject","Message: TEST!!!",$headers);[/PHP]


and the mail log:

```
Jun 14 23:35:13 localhost postfix/pickup[28087]: 3A05C9E8F0: uid=33 from=<www-data>
Jun 14 23:35:13 localhost postfix/cleanup[28154]: 3A05C9E8F0: message-id=<20060614203513.3A05C9E8F0@localhost>
Jun 14 23:35:13 localhost postfix/qmgr[22172]: 3A05C9E8F0: from=<www-data@localhost>, size=355, nrcpt=1 (queue active)
Jun 14 23:35:16 localhost postfix/smtp[28155]: 3A05C9E8F0: to=<test1@eclipsedesign.net>, relay=eclipsedesign.net[194.117.236.18], delay=3, status=bounced (host eclipsedesign.net[194.117.236.18] said: 550-Verification failed for <www-data@localhost> 550-unrouteable mail domain "localhost" 550 Sender verify failed (in reply to RCPT TO command))
Jun 14 23:35:16 localhost postfix/cleanup[28154]: CA4CD9E978: message-id=<20060614203516.CA4CD9E978@localhost>
Jun 14 23:35:16 localhost postfix/qmgr[22172]: CA4CD9E978: from=<>, size=2279, nrcpt=1 (queue active)
Jun 14 23:35:16 localhost postfix/qmgr[22172]: 3A05C9E8F0: removed
Jun 14 23:35:16 localhost postfix/local[28160]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 14 23:35:17 localhost postfix/local[28160]: CA4CD9E978: to=<rem@localhost>, orig_to=<www-data@localhost>, relay=local, delay=1, status=sent (delivered to command: procmail -a "$EXTENSION")
Jun 14 23:35:17 localhost postfix/qmgr[22172]: CA4CD9E978: removed
```

---

### Post by MJN on 2006-06-14
Get rid of the second $headers line... It doesn't look right. Any joy?

---

### Post by rem on 2006-06-14
The PHP code is correct... the dot in front of the 2nd $headers variable, means that it's value is combined with the first one... sorry i can't explain this better in English :)

Here's the main.cf file and /etc/aliases

================
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, localhost.localdomain, , localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
==============================

postmaster: root
root: rem

daemon: root
bin: root
sys: root
sync: root
games: root
man: root
lp: root
mail: root
uucp: root
proxy: root
www-data: root
backup: root
list: root
irc: root
gnats: root
nobody: root

hostmaster: root
usenet: root
news: root
webmaster: root
www: root
ftp: root
abuse: root
noc: root
security: root

mailer-daemon: postmaster
=============================


Many thanks!

---

### Post by MJN on 2006-06-14
Oops... changed my message since you read it.

Anyway, as it says now, get rid of that second line as whilst I don't know the first thing about PHP I do know it's possibly the cause of the problem! ;)

If you want to keep it in (there's no need if the address is the same as that in the From line) I would expect you would need a <SPACE> before the Reply-To bit or else it'll merge them otherwise?

Mathew

---

### Post by MJN on 2006-06-14
If that doesn't work, try setting **myorigin = eclipsedesign.net **in main.cf as then this'll be appended to your outgoing mail (instead of @localhost). Note however I still want you to keep that second $headers line out! ;)

Mathew

---

### Post by rem on 2006-06-14
ummm, that's not it...
forgot to say i already tried it that way...

the log's the same
```

Jun 15 00:29:07 localhost postfix/pickup[28087]: 3FB919E8F0: uid=33 from=<www-data>
Jun 15 00:29:07 localhost postfix/cleanup[29604]: 3FB919E8F0: message-id=<20060614212907.3FB919E8F0@localhost>
Jun 15 00:29:07 localhost postfix/qmgr[22172]: 3FB919E8F0: from=<www-data@localhost>, size=292, nrcpt=1 (queue active)
Jun 15 00:29:09 localhost postfix/smtp[29606]: 3FB919E8F0: to=<test1@eclipsedesign.net>, relay=eclipsedesign.net[194.117.236.18], delay=2, status=bounced (host eclipsedesign.net[194.117.236.18] said: 550-Verification failed for <www-data@localhost> 550-unrouteable mail domain "localhost" 550 Sender verify failed (in reply to RCPT TO command))
Jun 15 00:29:10 localhost postfix/cleanup[29604]: E51F49E978: message-id=<20060614212909.E51F49E978@localhost>
Jun 15 00:29:10 localhost postfix/qmgr[22172]: E51F49E978: from=<>, size=2216, nrcpt=1 (queue active)
Jun 15 00:29:10 localhost postfix/qmgr[22172]: 3FB919E8F0: removed
Jun 15 00:29:10 localhost postfix/local[29610]: E51F49E978: to=<www-data@localhost>, relay=local, delay=1, status=sent (delivered to command: procmail -a "$EXTENSION")
Jun 15 00:29:10 localhost postfix/qmgr[22172]: E51F49E978: removed

```

---

### Post by MJN on 2006-06-14
I take it that's not with myorigin set? (and Postfix restarted with sudo /etc/init.d/postfix restart)

---

### Post by rem on 2006-06-14
Weeeee!!! Working!!! Victory!!! Yesssss!!!
Oh, man... thanks a mil! I don't know what I would done without your help!
"myorigin = eclipsedesign.net" did the trick and finally, I'm rolling!!! 

Thanks MJN, you really know your stuff :):):)

---

### Post by MJN on 2006-06-14
Well, to be fair, I should've mentioned the myorigin directive right at the beginning - I just completely forgot about it.

Anyway, glad you're now sorted! And, as a bonus, I've now learnt how to do my very first PHP function so we've both benefitted! ;)

Mathew

---

### Post by rem on 2006-06-14
Glad u feel this way... but can't compare with what you just did for me... I was on hold for last couple of days... wow! can't believe is actually working :)

---

