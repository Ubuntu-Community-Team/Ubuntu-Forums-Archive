---
title: "amavis-new &amp; spamassassin"
date: 2005-05-22
forum: Server Platforms
---

### Post by lee_connell on 2005-05-22
Hey all looks like i got a working version of amavis-new with postfix, it's also scanning for virus's using clamav, working well.  However I can't seem to get amavis-new to recognize Mail::SpamAssassin.  I do have spamassassin installed, but its not picking it up, therefore it's not detecting spam.

Here is the output of amavis-new startup:

May 22 19:14:00 mail amavis[2645]: starting.  amavisd-new at mail.connell-tech.com amavisd-new-20030616-p10, Unicode aware
May 22 19:14:00 mail amavis[2645]: Perl version               5.008004
May 22 19:14:00 mail amavis[2645]: Module Amavis::Conf        1.15
May 22 19:14:00 mail amavis[2645]: Module Archive::Tar        1.23
May 22 19:14:00 mail amavis[2645]: Module Archive::Zip        1.14
May 22 19:14:00 mail amavis[2645]: Module Compress::Zlib      1.34
May 22 19:14:00 mail amavis[2645]: Module Convert::TNEF       0.17
May 22 19:14:00 mail amavis[2645]: Module Convert::UUlib      1.051
May 22 19:14:00 mail amavis[2645]: Module MIME::Entity        5.417
May 22 19:14:00 mail amavis[2645]: Module MIME::Parser        5.417
May 22 19:14:00 mail amavis[2645]: Module MIME::Tools         5.417
May 22 19:14:00 mail amavis[2645]: Module Mail::Header        1.62
May 22 19:14:00 mail amavis[2645]: Module Mail::Internet      1.62
May 22 19:14:00 mail amavis[2645]: Module Net::Cmd            2.26
May 22 19:14:00 mail amavis[2645]: Module Net::SMTP           2.29
May 22 19:14:00 mail amavis[2645]: Module Net::Server         0.87
May 22 19:14:00 mail amavis[2645]: Module Time::HiRes         1.59
May 22 19:14:00 mail amavis[2645]: Module Unix::Syslog        0.100
May 22 19:14:01 mail amavis[2646]: Found $file       at /usr/bin/file
May 22 19:14:01 mail amavis[2646]: Found $arc        at /usr/bin/arc
May 22 19:14:01 mail amavis[2646]: Found $gzip       at /bin/gzip
May 22 19:14:01 mail amavis[2646]: No $bzip2,        not using it
May 22 19:14:01 mail amavis[2646]: No $lzop,         not using it
May 22 19:14:01 mail amavis[2646]: No $lha,          not using it
May 22 19:14:01 mail amavis[2646]: Found $unarj      at /usr/bin/arj
May 22 19:14:01 mail amavis[2646]: Found $uncompress at /bin/uncompress
May 22 19:14:01 mail amavis[2646]: No $unfreeze,     not using it
May 22 19:14:01 mail amavis[2646]: No $unrar,        not using it
May 22 19:14:01 mail amavis[2646]: Found $zoo        at /usr/bin/zoo
May 22 19:14:01 mail amavis[2646]: Found $cpio       at /bin/cpio
May 22 19:14:01 mail amavis[2646]: Using internal av scanner code for (primary) Clam Antivirus-clamd
May 22 19:14:01 mail amavis[2646]: Found secondary av scanner Clam Antivirus - clamscan at /usr/bin/clamscan
May 22 19:14:01 mail spamd[2648]: spamd starting 
May 22 19:14:02 mail spamd[2652]: server started on port 783/tcp (running version 3.0.2) 
May 22 19:14:02 mail spamd[2652]: server successfully spawned child process, pid 2693 
May 22 19:14:02 mail spamd[2652]: server successfully spawned child process, pid 2694 
May 22 19:14:02 mail spamd[2652]: server successfully spawned child process, pid 2695 
May 22 19:14:02 mail spamd[2652]: server successfully spawned child process, pid 2696 
May 22 19:14:02 mail spamd[2652]: server successfully spawned child process, pid 2697 

Also if anyone knows how to change my primary virus scanner please let me know.

Lee

---

### Post by blueplazma on 2005-05-22
You need to edit your /etc/amavis/amavisd.conf file and turn on spam filtering.  It is turned off by default.  Primary virus scanner should be there too.

---

### Post by lee_connell on 2005-05-22
which paramter/command is it to turn on spam filtering?  same with virus scanner?  I will have alook but i didnt see anything saying it was off and what i do see i don't really understand as it is an acl for it.  I'll try to read up more on it but any help you can provide would be great thanks for the response.

---

### Post by lee_connell on 2005-05-22
@bypass_spam_checks_acl  = qw( . ); needs to be commented out and it will work.

---

