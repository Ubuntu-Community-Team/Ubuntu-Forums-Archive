---
title: "Ready to Buy Postfix/Dovecot Kung Fu"
date: 2007-06-04
forum: Server Platforms
---

### Post by hawzor on 2007-06-04
](*,)

Ladies and Gentlemen, please feel free to refer a friend to me regarding this. I have $$$ and I am ready to part with them for expert help. :(

Set up Dapper Drake just nicely. Everything is all apt-getted on my box. Did this all at home and everything worked fine.

Big issue is the Dovecot and Postfix setup. Worked fine a few days ago. I was able to send mail from behind my router ***without ANY incident.*** Slapped the server into the colo Saturday with only ifconfig changes made and all of a sudden we have the following errors, much of it barfed by logcheck:

[COLOR="Navy"]  -hostname: Host name lookup failure
  -delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused
  -postfix/smtp[27795]: warning: connect #[any number here] to subsystem private/scache: Connection refused
  -postfix/qmgr[3925]: warning: premature end-of-input on private/smtp socket while reading input attribute name
  -postfix/master[3921]: warning: process /usr/lib/postfix/smtp pid 27795 exit status 1
  -postfix/qmgr[3925]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem description[/COLOR]

...and many more chestnuts of the same variety. Losing patience with this and just about ready to hire a qmailrocks guy/gal to come in and save me from myself.

I followed many of the lines here: [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#head-d1c44438762ba7bca99ef9bc9442552531828302](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#head-d1c44438762ba7bca99ef9bc9442552531828302)

But now I must get to it. Anybody care to AIM or email me their price? Tell a friend please! :)

HK

---

### Post by MJN on 2007-06-04
No need for money - there's plenty of help available here... for free!

Post your actual logs, not logcheck's parsed output, and we can start to determine where the fault lies. As you say, it was working before the move so it's going to be a relatively trivial cause.

Mathew

---

### Post by hawzor on 2007-06-04
Mighty kind of you to offer free hlep. I can send pounds sterling or euros too..... :)  Here are relevant excerpts from** /var/log/mail.err**
[COLOR="Navy"]...
Jun  4 08:10:53 [my]host postfix/smtp[1862]: fatal: connect #11 to subsystem private/scache: Connection refused
Jun  4 09:03:59 [my]host postfix/sendmail[2844]: fatal: usage: sendmail [options]
Jun  4 10:07:33 [my]host postfix/smtp[4655]: fatal: connect #11 to subsystem private/scache: Connection refused
...[/COLOR]


**/var/log/mail.info**

[COLOR="navy"]...
Jun  3 07:25:53 [my]host postfix/smtp[14192]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  3 07:25:53 [my]host postfix/smtp[14193]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  3 07:25:53 [my]host postfix/smtp[14195]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  3 07:25:53 [my]host postfix/smtp[14197]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
...[/COLOR]

**/var/log/mail.warn**

[COLOR="navy"]...
Jun  4 12:02:33 [my]host postfix/smtp[6532]: warning: connect #1 to subsystem private/scache: Connection refused
Jun  4 12:02:43 [my]host postfix/smtp[6532]: warning: connect #2 to subsystem private/scache: Connection refused
Jun  4 12:02:53 [my]host postfix/smtp[6532]: warning: connect #3 to subsystem private/scache: Connection refused
Jun  4 12:03:03 [my]host postfix/smtp[6532]: warning: connect #4 to subsystem private/scache: Connection refused
Jun  4 12:03:13 [my]host postfix/smtp[6532]: warning: connect #5 to subsystem private/scache: Connection refused
Jun  4 12:03:23 [my]host postfix/smtp[6532]: warning: connect #6 to subsystem private/scache: Connection refused
Jun  4 12:03:33 [my]host postfix/smtp[6532]: warning: connect #7 to subsystem private/scache: Connection refused
Jun  4 12:03:43 [my]host postfix/smtp[6532]: warning: connect #8 to subsystem private/scache: Connection refused
Jun  4 12:03:53 [my]host postfix/smtp[6532]: warning: connect #9 to subsystem private/scache: Connection refused
Jun  4 12:04:03 [my]host postfix/smtp[6532]: warning: connect #10 to subsystem private/scache: Connection refused
Jun  4 12:04:13 [my]host postfix/smtp[6532]: fatal: connect #11 to subsystem private/scache: Connection refused
Jun  4 12:04:14 [my]host postfix/qmgr[3925]: warning: premature end-of-input on private/smtp socket while reading input attribute name
Jun  4 12:04:14 [my]host postfix/qmgr[3925]: warning: private/smtp socket: malformed response
Jun  4 12:04:14 [my]host postfix/master[3921]: warning: process /usr/lib/postfix/smtp pid 6532 exit status 1
Jun  4 12:04:14 [my]host postfix/qmgr[3925]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem descri$
Jun  4 12:15:44 [my]host postfix/trivial-rewrite[6700]: warning: do not list domain [my]host.com in BOTH mydestination and virtual_mailbox_domains
Jun  4 12:15:44 [my]host postfix/trivial-rewrite[6700]: warning: do not list domain [my]host.com in BOTH mydestination and virtual_mailbox_domains
...[/COLOR]

Does it become clearer what I have wrought wrongly?

---

### Post by MJN on 2007-06-04
We really need the logs from the moment Postfix (re)starts and just stick with mail.log as that'll contain everything (I think).

Just to confirm, you only followed that linked guide (and nothing else) for the Postfix install/config?

Mathew

---

### Post by CaptainMorgan on 2007-06-04
MJN, or anybody... since I know hawzor, I'm sure he won't mind if I ask you to take a look at my problem after his please: [http://ubuntuforums.org/showthread.php?t=462793](http://ubuntuforums.org/showthread.php?t=462793)

Much appreciated,
-Capt

---

### Post by hawzor on 2007-06-04
OK Mathew, thanks.

I restarted Postfix to get fresh stuff for you. Here it is from the top. Notice that without any config changes, all of a sudden, the very last record actually sent mail just like an MTA! :)  BTW, you will note that I anonymized my server name and where mail is queued to be sent to save them from being spammed mercilessly from post aggregation.

[COLOR="Navy"]...
Jun  4 12:58:43 [my] postfix/master[3921]: terminating on signal 15
Jun  4 12:58:44 [my] postfix/postqueue[6977]: warning: Mail system is down -- accessing queue directly
Jun  4 12:58:50 [my] postfix/master[7048]: daemon started -- version 2.2.10, configuration /etc/postfix
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 07CC58105C6: from=<logcheck@[my].com>, size=798, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 0BF9D8105B4: from=<logcheck@[my].com>, size=9700, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 01A108105D0: from=<logcheck@[my].com>, size=1591, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 25DFE8105C4: from=<logcheck@[my].com>, size=4818, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 28AF38105C3: from=<logcheck@[my].com>, size=6861, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 225DA8105C7: from=<logcheck@[my].com>, size=3250, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 2D7478105B0: from=<logcheck@[my].com>, size=648, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 8328C8105B8: from=<logcheck@[my].com>, size=645, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 87E358105BF: from=<logcheck@[my].com>, size=811, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: E8F598105C0: from=<logcheck@[my].com>, size=8143, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: E98778105B9: from=<www-data@[my].com>, size=5538, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 78BB08105BA: from=<www-data@[my].com>, size=5538, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 7DA128105C2: from=<logcheck@[my].com>, size=2642, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: C7F498105BB: from=<logcheck@[my].com>, size=6814, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: D8D1D8105C9: from=<logcheck@[my].com>, size=4818, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: DAB5481047A: from=<root@[my].com>, size=720, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 5CAF38105BD: from=<logcheck@[my].com>, size=795, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 500358105BE: from=<logcheck@[my].com>, size=784, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 597068105CE: from=<logcheck@[my].com>, size=7879, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: BE6F78105C1: from=<logcheck@[my].com>, size=4818, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 145D58105C5: from=<logcheck@[my].com>, size=2642, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 12B2E8105CD: from=<www-data@[my].com>, size=5538, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 37F7C8105C8: from=<logcheck@[my].com>, size=2642, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 3EB5E8105CB: from=<logcheck@[my].com>, size=7177, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 63A358105BC: from=<root@[my].com>, size=720, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 6A95D8105CC: from=<logcheck@[my].com>, size=3678, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 94DDB8105CF: from=<www-data@[my].com>, size=5538, nrcpt=1 (queue active)
Jun  4 12:59:26 [my] postfix/smtp[7128]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  4 12:59:26 [my] postfix/smtp[7129]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  4 12:59:26 [my] postfix/smtp[7131]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  4 12:59:26 [my] postfix/smtp[7133]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  4 12:59:26 [my] postfix/smtp[7135]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jun  4 12:59:26 [my] postfix/smtp[7128]: 07CC58105C6: to=<[my]@[my].com>, relay=none, delay=35831, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/smtp[7129]: 0BF9D8105B4: to=<[my]@[my].com>, relay=none, delay=140395, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/smtp[7131]: 01A108105D0: to=<[my]@[my].com>, relay=none, delay=10632, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/smtp[7135]: 28AF38105C3: to=<[my]@[my].com>, relay=none, delay=57429, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/smtp[7133]: 25DFE8105C4: to=<[my]@[my].com>, relay=none, delay=46630, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 225DA8105C7: to=<[my]@[my].com>, relay=none, delay=32229, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 2D7478105B0: to=<root@[my].com>, orig_to=<root>, relay=none, delay=140394, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 8328C8105B8: to=<root@[my].com>, orig_to=<root>, relay=none, delay=140233, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 87E358105BF: to=<[my]@[my].com>, relay=none, delay=93431, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: E8F598105C0: to=<[my]@[my].com>, relay=none, delay=82630, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: E98778105B9: to=<[my]@my.com>, relay=none, delay=137755, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 78BB08105BA: to=<[my]@my.com>, relay=none, delay=137708, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 7DA128105C2: to=<[my]@[my].com>, relay=none, delay=79030, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: C7F498105BB: to=<[my]@[my].com>, relay=none, delay=133030, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: D8D1D8105C9: to=<[my]@[my].com>, relay=none, delay=25030, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: DAB5481047A: to=<root@[my].com>, orig_to=<root>, relay=none, delay=110038, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 5CAF38105BD: to=<[my]@[my].com>, relay=none, delay=107828, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 500358105BE: to=<[my]@[my].com>, relay=none, delay=97031, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 597068105CE: to=<[my]@[my].com>, relay=none, delay=14228, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: BE6F78105C1: to=<[my]@[my].com>, relay=none, delay=64630, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 145D58105C5: to=<[my]@[my].com>, relay=none, delay=43024, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 12B2E8105CD: to=<[my]@my.com>, relay=none, delay=14377, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:26 [my] postfix/qmgr[7050]: 37F7C8105C8: to=<[my]@[my].com>, relay=none, delay=28629, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:27 [my] postfix/qmgr[7050]: 3EB5E8105CB: to=<[my]@[my].com>, relay=none, delay=21429, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:27 [my] postfix/qmgr[7050]: 63A358105BC: to=<root@[my].com>, orig_to=<root>, relay=none, delay=23661, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:27 [my] postfix/qmgr[7050]: 6A95D8105CC: to=<[my]@[my].com>, relay=none, delay=17831, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 12:59:27 [my] postfix/qmgr[7050]: 94DDB8105CF: to=<[my]@my.com>, relay=none, delay=13902, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jun  4 13:02:22 [my] postfix/pickup[7049]: 2AC8A8105D1: uid=117 from=<logcheck>
Jun  4 13:02:22 [my] postfix/cleanup[8104]: 2AC8A8105D1: message-id=<20070604200222.2AC8A8105D1@[my].com>
Jun  4 13:02:22 [my] postfix/qmgr[7050]: 2AC8A8105D1: from=<logcheck@[my].com>, size=6763, nrcpt=1 (queue active)
Jun  4 13:02:23 [my] postfix/smtp[8108]: 2AC8A8105D1: to=<[my]@[my].com>, relay=mail.[my].com[myIP], delay=1, status=sent (250 ok 1180987411 qp 17833)
Jun  4 13:02:23 [my] postfix/qmgr[7050]: 2AC8A8105D1: removed
...[/COLOR]

See the issue?

---

### Post by hawzor on 2007-06-04
In answer to your second query, no, I only followed that guide in broad detail, primarily used it to check whter I am even configured right....which to my estimation, yes I am. (I get proper telnet returns from dovecot and postfix.) All I installed was by **sudo apt-get**. 

I have latest model Webmin installed and used it for the confs that actually worked behind my home router, so I am suspecting Webmin usage isn't the culprit. No Webmin changes have been made since before the colo installation.

Any advices?

---

### Post by craigp84 on 2007-06-05
Hi Hawzor,

I think this is a trivial fix, but just to be sure, can you please post the contents of /etc/hosts, /etc/nsswitch.conf, /etc/resolv.conf and the output of the following command:

```
sudo netstat -antup | grep -i listen
```

Lastly, in case it's not what i think (screwed host mapping in /etc/hosts) can you post your /etc/postfix/master.cf please.

-c

---

### Post by craigp84 on 2007-06-05
Ah cancel that. I just read it again. It's your my_networks in /etc/postfix/main.cf

-c

---

### Post by hawzor on 2007-06-06
OK, I have been groping around the net for more advice and much has changed since my last post.

Dovecot == out in favor of Courier.
Postfix to use MySQL as manager for virtual domains per [http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/)

Craigp84, with regard to your reference to `my_networks` I took that to mean the setting I had  `mynetworks = 127.0.0.0/8` which I have commented out and made instead `mynetworks_style = host` so that postfix is set to trust only itself.

It appears that this has resolved at least one problem. Many others remain. Here is the current postconf -n output (with my actual hostname and virtual domain changed for privacy):

[COLOR="Navy"]append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = [privatedomain]host.com, [fisrtvirtualdomain].com
myhostname = [privatedomain]host.com
mynetworks_style = host
myorigin = [privatedomain]host.com
recipient_delimiter = +
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = /var/lib/urandom/random-seed
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000[/COLOR]

Is there anything glaring there?

---

### Post by hawzor on 2007-06-06
The problem has now evolved into tlsmgr misunderstandings on my part. Any help?

As you can see my mail.log looks a lot cleaner now and test messages are getting through:

[COLOR="Navy"]Jun  6 10:08:21 [privatedomain]host postfix/master[7636]: terminating on signal 15
Jun  6 10:08:22 [privatedomain]host postfix/master[8665]: daemon started -- version 2.2.10, configuration /etc/postfix
Jun  6 10:10:42 [privatedomain]host postfix/smtpd[8694]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun  6 10:10:43 [privatedomain]host postfix/smtpd[8694]: warning: connect to private/tlsmgr: Connection refused
Jun  6 10:10:43 [privatedomain]host postfix/smtpd[8694]: warning: problem talking to server private/tlsmgr: Connection refused
Jun  6 10:10:44 [privatedomain]host postfix/smtpd[8694]: warning: connect to private/tlsmgr: Connection refused
Jun  6 10:10:44 [privatedomain]host postfix/smtpd[8694]: warning: problem talking to server private/tlsmgr: Connection refused
Jun  6 10:10:44 [privatedomain]host postfix/smtpd[8694]: warning: no entropy for TLS key generation: disabling TLS support
Jun  6 10:10:44 [privatedomain]host postfix/smtpd[8694]: connect from [privatedomain]host.com[138.100.238.199]
Jun  6 10:11:12 [privatedomain]host postfix/smtpd[8694]: 36AB58105B7: client=[privatedomain]host.com[138.100.238.199]
Jun  6 10:11:22 [privatedomain]host postfix/cleanup[8702]: 36AB58105B7: message-id=<20070606171112.36AB58105B7@[privatedomain]host.com>
Jun  6 10:11:22 [privatedomain]host postfix/qmgr[8668]: 36AB58105B7: from=<test@workaround.org>, size=378, nrcpt=1 (queue active)
Jun  6 10:11:22 [privatedomain]host postfix/virtual[8705]: 36AB58105B7: to=<user@virtual.test>, relay=virtual, delay=18, status=sent (delivered to maildir)
Jun  6 10:11:22 [privatedomain]host postfix/qmgr[8668]: 36AB58105B7: removed
Jun  6 10:11:24 [privatedomain]host postfix/smtpd[8694]: disconnect from [privatedomain]host.com[138.100.238.199][/COLOR]

---

### Post by Mr. C. on 2007-06-06
> **hawzor said:**
> 

mydestination = [privatedomain]host.com, [fisrtvirtualdomain].com

Is there anything glaring there?

Never list your virtual alias or virtual mailbox domains in mydestination.  This is mixing addresses classes, and creates problems.  See:

[http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)

MrC

---

### Post by Mr. C. on 2007-06-06
> **hawzor said:**
> The problem has now evolved into tlsmgr misunderstandings on my part. Any help?

...

Jun  6 10:10:43 [privatedomain]host postfix/smtpd[8694]: warning: connect to private/tlsmgr: Connection refused
Jun  6 10:10:43 [privatedomain]host postfix/smtpd[8694]: warning: problem talking to server private/tlsmgr: Connection refused
Jun  6 10:10:44 [privatedomain]host postfix/smtpd[8694]: warning: connect to private/tlsmgr: Connection refused
...



See: [http://tinyurl.com/22fwr4](http://tinyurl.com/22fwr4)

MrC

---

### Post by hawzor on 2007-06-06
OK, yeah, so this isn't frustrating at all. It has been 5 days of worthless hacking on this problem. Is everybody out there sure they don't want $$$ to streamline this for me? There must be an easier way, and apt-get was supposed to be the deal....

Mr. C, thanks for the tips. I have read both of those references. I removed the virtual host from **mydestination**, which, I was previously told ***could ***be added by comma separation, but OK, removed.

The second link you gave "Viktor" asks:

[COLOR="DarkGreen"]Why is the tlsmgr(8) service not running? Perhaps it fails to start, 
and records the problem in the logs... Perhaps you never restarted 
Postfix after updating master.cf... [/COLOR]

Er, for me, I restart postfix after every teeny change.

So here is the output of **sudo ldd /usr/libexec/postfix/smtpd**
       [COLOR="Navy"] linux-gate.so.1 =>  (0xffffe000)
        libpostfix-master.so.1 => /usr/lib/libpostfix-master.so.1 (0xb7f02000)
        libpostfix-tls.so.1 => /usr/lib/libpostfix-tls.so.1 (0xb7ef7000)
        libpostfix-dns.so.1 => /usr/lib/libpostfix-dns.so.1 (0xb7ef3000)
        libpostfix-global.so.1 => /usr/lib/libpostfix-global.so.1 (0xb7ecc000)
        libpostfix-util.so.1 => /usr/lib/libpostfix-util.so.1 (0xb7ea6000)
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7e68000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7d39000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d25000)
        libdb-4.3.so => /usr/lib/libdb-4.3.so (0xb7c49000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7c34000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7c21000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7af1000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7aee000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7ada000)
        /lib/ld-linux.so.2 (0xb7f11000)[/COLOR]


My current **postconf -n **:

[COLOR="Navy"]alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = [private]host.com
myhostname = [private]host.com
mynetworks_style = host
myorigin = [private]host.com
recipient_delimiter = +
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_loglevel = 7
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/random  [COLOR="Black"]**(tried urandom also)**[/COLOR]
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000[/COLOR]

**mail.log** looking like this, now set to level 7 (last issue /me hopes):

[COLOR="navy"]Jun  6 15:17:34 [private]host postfix/master[14834]: daemon started -- version 2.2.10, configuration /etc/postfix
Jun  6 15:17:43 [private]host postfix/smtpd[14839]: initializing the server-side TLS engine
Jun  6 15:17:43 [private]host postfix/smtpd[14839]: warning: connect to private/tlsmgr: Connection refused
Jun  6 15:17:43 [private]host postfix/smtpd[14839]: warning: problem talking to server private/tlsmgr: Connection refused
Jun  6 15:17:44 [private]host postfix/smtpd[14839]: warning: connect to private/tlsmgr: Connection refused
Jun  6 15:17:44 [private]host postfix/smtpd[14839]: warning: problem talking to server private/tlsmgr: Connection refused
Jun  6 15:17:44 [private]host postfix/smtpd[14839]: warning: no entropy for TLS key generation: disabling TLS support[/COLOR]

Seems like more than one person has experienced this BS.

Others on the net  have said, oh add this: **tlsmgr    unix  -       -       n       1000?   1       tlsmgr** or uncomment it from a non-existent line in my default **main.cf** file.

Here is what  **postfix check **barfs when you add that line to **main.cf**:

[COLOR="navy"]postfix: fatal: /etc/postfix/main.cf, line 65: missing '=' after attribute name: "tlsmgr  unix - - n 1000? 1 tlsmgr"[/COLOR]

OK, so add the `=` that it seems to be requesting and guess what? All the stuff I show in logs above, reports the exact same thing. No help.

Going to try to install qmailrocks from src if this keeps up....

---

### Post by Mr. C. on 2007-06-06
The tlsmgr line goes in master.cf, not main.cf.

A good part of your troubles are that you are trying to accomplish too much before getting the basic setups down.  Mail systems are very complex and powerful.  Postfix is exceptional.

Once you have the line in *master.cf*, you should see :

postfix  17852 23527  0 Jun03 ?        00:00:00 tlsmgr -l -t unix -u

in your ps output.  Get tlsmgr running and we'll go from there.

MrC

---

### Post by hawzor on 2007-06-06
*geez*

Granted Mr. C I am trying to do a lot at once, but missing `master.cf` that was just an unforgivable stupidity on my part. :redface:  Thanks for your kindness.

OK have done insert into master.cf and restarted postfix. Minor issue:

**ps fax | grep postfix**

[COLOR="Navy"] 4087 ?        Ss     0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
 4090 ?        S      0:00  \_ /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
 4091 ?        S      0:00  \_ /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
 4092 ?        S      0:00  \_ /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
 4093 ?        S      0:00  \_ /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
15164 pts/0    S+     0:00  |                   \_ grep postfix
15141 ?        Ss     0:00 /usr/lib/postfix/master[/COLOR]

No tlsmgr. Hoping this is not important.

Will proceed to test and look at the logs.

---

### Post by hawzor on 2007-06-06
OK, I believe this is as it should be, no? (irrespective of whether we see it in **ps**?)

[COLOR="Navy"]Jun  6 15:55:41 [private]host postfix/master[15255]: daemon started -- version 2.2.10, configuration /etc/postfix
Jun  6 15:56:04 [private]host postfix/smtpd[15260]: initializing the server-side TLS engine
Jun  6 15:56:04 [private]host postfix/tlsmgr[15262]: open server TLS cache btree:/var/spool/postfix/smtpd_scache
Jun  6 15:56:04 [private]host postfix/tlsmgr[15262]: tlsmgr_srvr_cache_run_event: start TLS server session cache cleanup
Jun  6 15:56:04 [private]host postfix/smtpd[15260]: connect from [private]host.com[38.100.238.99]
Jun  6 15:56:56 [private]host postfix/smtpd[15260]: A37ED810470: client=[private]host.com[138.100.238.199]
Jun  6 15:57:09 [private]host postfix/cleanup[15269]: A37ED810470: message-id=<20070606225656.A37ED810470@[private]host.com>
Jun  6 15:57:09 [private]host postfix/qmgr[15258]: A37ED810470: from=<test@workaround.org>, size=372, nrcpt=1 (queue active)
Jun  6 15:57:09 [private]host postfix/virtual[15272]: A37ED810470: to=<user@virtual.test>, relay=virtual, delay=22, status=sent (delivered to maildir)
Jun  6 15:57:09 [private]host postfix/qmgr[15258]: A37ED810470: removed
Jun  6 15:57:12 [private]host postfix/smtpd[15260]: disconnect from [private]host.com[138.100.238.199][/COLOR]

Mr. C and others, are you happy with this?

If so it is off to Amavis, SpamAssassin, ClamAV, SPF and DomainKeys. Wish me luck or please feel free to offer your service for hire! :)

---

### Post by Mr. C. on 2007-06-06
Excellent!  You're on your way.

Setting up amavis is not very difficult.  But review the docs, especially the INSTALL document ([http://www.ijs.si/software/amavisd/INSTALL.txt](http://www.ijs.si/software/amavisd/INSTALL.txt)) and the excellent README.postfix, by Patrick Ben Koetter at the amavis site:  [http://www.ijs.si/software/amavisd/#doc](http://www.ijs.si/software/amavisd/#doc) .

Start with getting the perl environment and required utilities setup as indicated in the INSTALL.txt file.

ClamAv is next, and simple to install / use.

I personally have not used packages (rpms, debs) in a long time for my servers, and build and configure everything from source.  I find package maintainers end up becoming a roadblock for me.

Btw. You're configuring a more complex system than many - you will find superb help on both the postfix and amavisd-new mailing lists.  If you are having trouble and not getting answers here, you'll get help from the best of the best on both those lists.

You probably won't be happy with my consulting rates.  :-)

Also, grab my postfix-logwatch and amavis-logwatch utilities to help analyze your logs.  They both run standalone and from within logwatch:

   [http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

MrC

---

### Post by hawzor on 2007-06-11
OK, over the weekend I set up the certificates for secure IMAP and secure POP for courier and TLS 1.1 (same certificate usage as SSLv3, don't let anybody tell you differently; and for the coming TLS 1.2 specification, I recommend just avoiding SHA and MD5 encryption wherever possible in making keys and csr's and the like) for Postfix.

I simply post now to warn people that though you can use the same final root CA-signed certificate ***content ***for all three applications, the usage varies between these two programs....and I had a super hard time finding instructionals out there. Yeah, right, Google is so not my friend. :/

This was the ultimate description set that worked first time it was tried (and cheap fast signed SSL certs too):

[http://www.rapidssl.com/resources/install/rapidssl/postfix.htm](http://www.rapidssl.com/resources/install/rapidssl/postfix.htm)

[http://www.rapidssl.com/resources/install/rapidssl/courier.htm](http://www.rapidssl.com/resources/install/rapidssl/courier.htm)

Good luck everybody!

---

### Post by Mr. C. on 2007-06-11
The Book of Postfix is outstanding, and walks you through these things and explains TLS, SASL, content filters, etc.

[http://www.postfix-book.com/](http://www.postfix-book.com/)

MrC

---

