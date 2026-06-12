---
title: "trouble taming amavis+clam"
date: 2008-03-17
forum: Server Platforms
---

### Post by otake-tux on 2008-03-17
Hello, I run a mail server using postfix, spamassassin, amavis and clamav on an ubuntu 6.06 LTS box.  It runs great, props to the ubuntu devs for putting together such a fine product.  That said; I am having issues with clamav.

the problem is that I want to quarantine suspected viruses yet I can't. the system always blocks a virus signature.  

here's what I think are the relevant parts of my config file, let me know if you need more:

```
$mydomain='domain.com';
$daemon_user= 'amavis';

$daemon_group= 'amavis';
$inet_socket_port = 10024;

$forward_method = 'smtp:127.0.0.1:10025';

$TEMPBASE = "/var/spool/quarantine";
$log_level = 2;
$warnbannedrecip = 1;
$warn_offsite = 1;
$warnvirusrecip = 1;
$virus_quarantine_to = "admin\@$mydomain";
$sa_local_tests_only = 0;

$final_virus_destiny      = D_PASS;  # (data not lost, see virus quarantine)
$final_banned_destiny     = D_BOUNCE;   # D_REJECT when front-end MTA
$final_spam_destiny       = D_PASS;
#$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)

$virus_admin = "admin\@$mydomain"; # due to D_DISCARD default
$mailfrom_notify_admin     = "admin\@$mydomain";  # notifications sender
$mailfrom_notify_recip     = "admin\@$mydomain";  # notifications sender
$mailfrom_notify_spamadmin = "admin\@$mydomain"; # notifications sender

$X_HEADER_LINE = "Debian $myproduct_name at $mydomain";

```

thanks.

---

