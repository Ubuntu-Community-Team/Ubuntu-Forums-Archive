---
title: "Ubuntu 8 server, Postfix/amavis/sa/clamav problem?"
date: 2008-05-31
forum: Server Platforms
---

### Post by robbrandt on 2008-05-31
I have a brand new installation of Ubuntu 8 Server, did apt-get upgrade on installation.  I have a functioning mail server in stock configuration except I switched to Maildir format.

Problem is that my mail headers are not showing any evidence that SA is touching them.

I installed Amavis-new, spamassassin and clamav per the instructions here:
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

Initially I had a problem with clamav similar to detailed here:
[http://www.howtoforge.com/forums/showthread.php?t=17295](http://www.howtoforge.com/forums/showthread.php?t=17295)
But after restarting all the servers as detailed at the bottom of the PostfixAmavisNew wiki page, it seems to have disappeared.

The only evidence of what amavis is doing is this header:
X-Virus-Scanned: Debian amavisd-new at sub.domain.tld

My mail log looks like this:

May 31 18:47:08 sub postfix/smtpd[16781]: connect from localhost[127.0.0.1]
May 31 18:47:08 sub postfix/smtpd[16781]: 95EC9422E3: client=localhost[127.0.0.1]
May 31 18:47:08 sub postfix/cleanup[16776]: 95EC9422E3: message-id=<4841FF99.3010608@domain.tld>
May 31 18:47:08 sub postfix/qmgr[16623]: 95EC9422E3: from=<rbrandt@domain.tld>, size=1250, nrcpt=1 (queue active)
May 31 18:47:08 sub postfix/smtpd[16781]: disconnect from localhost[127.0.0.1]
May 31 18:47:08 sub amavis[15784]: (15784-02) Passed CLEAN, [206.83.0.42] [206.83.1.2] <rbrandt@domain.tld> -> <rbrandt@sub.domain.tld>, Message-ID: <4841FF99.3010608@domain.tld>, mail_id: quEaSzP2Lljy, Hits: 1.21, size: 788, queued_as: 95EC9422E3, 1758 ms
May 31 18:47:08 sub postfix/smtp[16777]: D2375422D7: to=<rbrandt@sub.domain.tld>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.8, delays=0.03/0.01/0/1.8, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 95EC9422E3)
May 31 18:47:08 sub postfix/qmgr[16623]: D2375422D7: removed
May 31 18:47:08 sub postfix/local[16782]: 95EC9422E3: to=<rbrandt@sub.domain.tld>, relay=local, delay=0.06, delays=0.02/0.02/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
May 31 18:47:08 sub postfix/qmgr[16623]: 95EC9422E3: removed

I've not used amavis before, and am accustomed to seeing spamd and clamd in the mail logs, so I don't know if this means anything (I suspect not).  But the lack of SA headers in the mails themselves tells me it's not being spam scanned.

Any ideas?

---

### Post by quelx on 2008-05-31
spamassassin doesn't add headers by default, Your don't indicate any problem.  What your seeing is postfix passing the message to amavis (of which spamassasin is part) and amavis passing it back to postfix after scanning.

for the SA headers:
[http://ubuntuforums.org/showpost.php?p=1227937&postcount=2](http://ubuntuforums.org/showpost.php?p=1227937&postcount=2)

---

### Post by robbrandt on 2008-05-31
Thanks.

I added those lines in etc/spamassassin/local.cf and restarted SA, and still no SA headers in email.

Here's my local.cf:

# This is the right place to customize your installation of SpamAssassin.
#
# See 'perldoc Mail::SpamAssassin::Conf' for details of what can be
# tweaked.
#
# Only a small subset of options are listed below
#
###########################################################################

#   Add *****SPAM***** to the Subject header of spam e-mails
#
# rewrite_header Subject *****SPAM*****


#   Save spam messages as a message/rfc822 MIME attachment instead of
#   modifying the original message (0: off, 2: use text/plain instead)
#
# report_safe 1


#   Set which networks or hosts are considered 'trusted' by your mail
#   server (i.e. not spammers)
#
# trusted_networks 212.17.35.


#   Set file-locking method (flock is not safe over NFS, but is faster)
#
# lock_method flock


#   Set the threshold at which a message is considered spam (default: 5.0)
#
# required_score 5.0


#   Use Bayesian classifier (default: 1)
#
# use_bayes 1


#   Bayesian classifier auto-learning (default: 1)
#
# bayes_auto_learn 1


#   Set headers which may provide inappropriate cues to the Bayesian
#   classifier
#
# bayes_ignore_header X-Bogosity
# bayes_ignore_header X-Spam-Flag
# bayes_ignore_header X-Spam-Status

use_terse_report 1
report_header 1

add_header spam Flag _YESNOCAPS_
add_header all Status _YESNO_, score=_SCORE_ required=_REQD_ tests=_TESTS_
autolearn=_AUTOLEARN_ version=_VERSION_
add_header all Level _STARS(*)_
add_header all Checker-Version SpamAssassin _VERSION_ (_SUBVERSION_) on _HOSTNAME_
auto_learn 1

---

### Post by quelx on 2008-05-31
Here is the relevant file from my amavis config, if I recall correctly, later amavis config options override earlier (hence the filename).  The website is where I found the info, I paste them into the config files so I can find them later when I inevitably break something.

/etc/amavis/conf.d/50-user
```
#http://www.fatofthelan.com/articles/articles.php?pid=22
$sa_tag_level_deflt  = -999; # add spam info headers if at, or above that level;
                            # undef is interpreted as lower than any spam level
$sa_tag2_level_deflt = 6.31;# add 'spam detected' headers at that level to
                            # passed mail, adding address extensions;
#$sa_kill_level_deflt = $sa_tag2_level_deflt; # triggers spam evasive actions
$sa_kill_level_deflt = 999; # triggers spam evasive actions
                            # at or above that level: bounce/reject/drop,
                            # quarantine
$sa_dsn_cutoff_level = 9;   # spam level beyond which a DSN is not sent,
                            # effectively turning D_BOUNCE into D_DISCARD;
                            # undef disables this feature and is a default;#http://www.fatofthelan.com/articles/articles.php?pid=22
$sa_spam_modifies_subj = 1; # in @spam_modifies_subj_maps, default is true

# Example: modify Subject for all local recipients except user@example.com
#@spam_modifies_subj_maps = ( [qw( !user@example.com . )] );

$sa_spam_level_char = '*';  # char for X-Spam-Level bar, defaults to '*';
                             # undef or empty disables inserting X-Spam-Level
$sa_spam_report_header = 1; # insert X-Spam-Report header field? default false

@local_domains_acl = ( ".$mydomain", "localhost" );

```

I had to add **localhost** to the **@local_domains_acl** line because fetchmail was bypassing the spamchecks.

---

### Post by robbrandt on 2008-06-01
YES! That did it, although your post was terribly hard to read ;)

---

### Post by venol on 2011-04-24
Hello, the problem same with me. SA-Header not shown on my email. I have modify files '/etc/amavisd/amavisd.conf', /ect/amavisd/conf.d/50-user', '/etc/amavisd/conf.d/21-ubuntu', and '20-debian' like configuration above. But, SA-Header not shown. I'm using Ubuntu 10.04 server.

---

