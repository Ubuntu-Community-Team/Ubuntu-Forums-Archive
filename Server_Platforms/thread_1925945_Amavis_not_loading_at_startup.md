---
title: "Amavis not loading at startup"
date: 2012-02-15
forum: Server Platforms
---

### Post by train4499 on 2012-02-15
I'm using Ubuntu 11.10 with postfix, amavis, spamassassin, postgrey.

Amavis is set to load at bootup.

The mail.log file shows amavis trying to load with the following message:

amavis[917]: starting.  /usr/sbin/amavisd-new at  amavisd-new-2.6.5 (20110407), Unicode aware

But it doesn't actually start.

If I start it manually "sudo service amavis start" it loads and mail.log has:

amavis[2594]: starting.  /usr/sbin/amavisd-new at holtlapu.ubuntu.lan amavisd-new-2.6.5 (20110407), 
Unicode aware, LANG="en_US.UTF-8"

So it appears when it tries to load on bootup, it's not aware of the machine name?

It loaded fine when I initially installed it. I have removed amavis and reinstalled it. No change.


After searching I found the solution:

Put the following in  /etc/amavis/conf.d/50-user replacing example.com with your domain name and hostname with your hostname.:

$mydomain = 'example.com';
$myhostname = 'hostname.example.com';
@local_domains_maps = ( ['.example.com'] );

---

### Post by liam_p on 2012-05-09
Hi,

If this fixes it, you're a genius and thanks for the post.  Every time the mail server restarts, I'm having to manually start amavis and it has been doing my head in!

Cheers,

Liam

---

