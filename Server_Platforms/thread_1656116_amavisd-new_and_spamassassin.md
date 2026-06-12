---
title: "amavisd-new and spamassassin"
date: 2010-12-30
forum: Server Platforms
---

### Post by Skaperen on 2010-12-30
Mail is basically working.  And amavisd does catch some obvious bad email.  But it does not appear to be invoking or accessing spamassassin at all.  Documentation is quite sparse for amavisd and that seems like it might be where something needs to change.

/etc/amavis/conf.d/75-local```
use strict;

# Turn on spamassassin:
@spam_scanners = ( ['SpamAssassin', 'Amavis::SpamControl::SpamAssassin'], );

# Turn off the extra Received header:
# $allowed_added_header_fields{lc('Received')} = 0;

# Specify disposition of junk classes:
$final_virus_destiny      = D_PASS;
$final_banned_destiny     = D_DISCARD;
$final_spam_destiny       = D_PASS;
$final_bad_header_destiny = D_PASS;

#------------ Do not modify anything below this line -------------
1;  # insure a defined return
```/etc/spamassassin/local.cf```
###########################################################################
# This is the right place to customize your installation of SpamAssassin.
#
# See 'perldoc Mail::SpamAssassin::Conf' for details of what can be
# tweaked.
#
# Only a small subset of options are listed below
###########################################################################

#   Add *****SPAM***** to the Subject header of spam e-mails
rewrite_header Subject *****SPAM*****

#   Save spam messages as a message/rfc822 MIME attachment instead of
#   modifying the original message (0: off, 2: use text/plain instead)
# report_safe 1

#   Set which networks or hosts are considered 'trusted' by your mail
#   server (i.e. not spammers)
trusted_networks 172.30.

#   Set file-locking method (flock is not safe over NFS, but is faster)
# lock_method flock

#   Set the threshold at which a message is considered spam (default: 5.0)
required_score 1.0

#   Use Bayesian classifier (default: 1)
use_bayes 1

#   Bayesian classifier auto-learning (default: 1)
bayes_auto_learn 1

#   Set headers which may provide inappropriate cues to the Bayesian
#   classifier
# bayes_ignore_header X-Bogosity
# bayes_ignore_header X-Spam-Flag
# bayes_ignore_header X-Spam-Status
```What I have installed (Ubuntu 9.10 amd64):```
meitner/root/x0 /root 260# dpkg -l | egrep -i 'amavis|clamav|dovecot|postfix|spamassassin'
ii  amavisd-new                       1:2.6.4-1ubuntu3                  Interface between MTA and virus scanner/cont
ii  clamav                            0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - command-line i
ii  clamav-base                       0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - base package
ii  clamav-daemon                     0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - scanner daemon
ii  clamav-docs                       0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - documentation
ii  clamav-freshclam                  0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - virus database
ii  clamav-getfiles                   2.0-6                             Update script for clamav
ii  clamav-testfiles                  0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - test files
ii  dovecot-antispam                  1.1+20090218.git.g28075fa-2       a Dovecot plugin that helps train spam filte
ii  dovecot-common                    1:1.1.11-0ubuntu11                secure mail server that supports mbox and ma
ii  dovecot-dev                       1:1.1.11-0ubuntu11                header files for the dovecot mail server
ii  dovecot-imapd                     1:1.1.11-0ubuntu11                secure IMAP server that supports mbox and ma
ii  dovecot-pop3d                     1:1.1.11-0ubuntu11                secure POP3 server that supports mbox and ma
ii  dovecot-postfix                   1:1.1.11-0ubuntu11                full mail server stack provided by Ubuntu se
ii  libclamav6                        0.95.3+dfsg-1ubuntu0.09.10.3      anti-virus utility for Unix - library
ii  postfix                           2.6.5-3                           High-performance mail transport agent
ii  postfix-cdb                       2.6.5-3                           CDB map support for Postfix
ii  postfix-doc                       2.6.5-3                           Documentation for Postfix
ii  postfix-pcre                      2.6.5-3                           PCRE map support for Postfix
ii  postfix-pgsql                     2.6.5-3                           PostgreSQL map support for Postfix
ii  spamassassin                      3.2.5-4ubuntu0.1                  Perl-based spam filter using text analysis
ii  spamc                             3.2.5-4ubuntu0.1                  Client for SpamAssassin spam filtering daemo
meitner/root/x0 /root 261# 
```

---

### Post by stmiller on 2010-12-30
I've got this working, but I can't remember exactly what I did to get it working. :)

I do remember the only file for amavisd I altered was /etc/amavis/conf.d/50-user :

(I had to comment out 'use strict' / 'use warnings' because it would not run with those for some reason.) :/



```
#use strict;
#use warnings;

#
# Place your configuration directives here.  They will override those in
# earlier files.
#
# See /usr/share/doc/amavisd-new/ for documentation and examples of
# the directives you can use in this file
#
$log_level = 0;

@local_domains_maps =
   ( [ ".$mydomain", 'stmiller.org' ] ); 

$sa_spam_subject_tag = '*SPAM* ';
$sa_tag_level_deflt  = -999;  # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 5.0; # add 'spam detected' headers at that level
$sa_kill_level_deflt = 999; # triggers spam evasive actions
$sa_dsn_cutoff_level = 7;   # spam level beyond which a DSN is not sent

$virus_admin = "postmaster@$mydomain"; # due to D_DISCARD default
$spam_admin = "postmaster@$mydomain";
$dsn_bcc = "maildebug@$mydomain";

$mailfrom_notify_admin     = "virusalert@$mydomain";
$mailfrom_notify_recip     = "virusalert@$mydomain";
$mailfrom_notify_spamadmin = "spamalert@$mydomain";

$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)
$final_banned_destiny     = D_REJECT;   # D_REJECT when front-end MTA
$final_spam_destiny       = D_PASS;
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)

$max_servers = 1;

#------------ Do not modify anything below this line -------------
1;  # ensure a defined return
```

My /etc/postfix/main.cf has this:

```


# Amavis ClamAV+SpamAssassin
content_filter = smtp-amavis:[127.0.0.1]:10024

```

And /etc/postfix/master.cf:

```


smtp-amavis     unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20


```

I'm not sure if this is any help,

---

