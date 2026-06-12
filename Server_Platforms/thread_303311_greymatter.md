---
title: "greymatter"
date: 2006-11-20
forum: Server Platforms
---

### Post by billybag on 2006-11-20
I tried getting help in the actual greymatter forum, but i got no help. if you think i will have better luck by posting the following problem under a different catagory, let me know please. My problem is this:

after uploading and chmoding everything(and i did this correctly, i rechecked over and over)the next step is to run the gm.cgi script in my browser ([http://mysitename.org/cgi-bin/gm.cgi](http://mysitename.org/cgi-bin/gm.cgi). i should get a login screen and instead i get the following:

Software error:

Can't locate Gm_Constants.pm in @INC (@INC contains: libs /usr/lib/perl5/5.8.7/i686-linux /usr/lib/perl5/5.8.7 /usr/lib/perl5/site_perl/5.8.7/i686-linux /usr/lib/perl5/site_perl/5.8.7 /usr/lib/perl5/site_perl/5.8.5 /usr/lib/perl5/site_perl/5.8.4 /usr/lib/perl5/site_perl/5.8.3 /usr/lib/perl5/site_perl/5.8.2 /usr/lib/perl5/site_perl/5.8.1 /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl .) at gm.cgi line 27.
BEGIN failed--compilation aborted at gm.cgi line 27.

Here is my general server info:
Operating system Linux
Kernel version 2.6.9-22.ELsmp
Machine Type i686
Apache version 1.3.36 (Unix)
PERL version 5.8.7
<b>Path to PERL /usr/bin/perl</b>
Path to sendmail /usr/sbin/sendmail
PHP version 5.1.4
MySQL version 5.0.24-standard
cPanel Build 10.9.0-RELEASE 57
Theme cPanel X v2.6.0
cPanel Pro 1.0 (RC36)

---

### Post by geek_Man on 2006-11-20
I think you need module called Gm_Constants.pm. That happens a lot with scripts gotten off of CPAN (which I'm guessing you did). Look around for the file and then install it. It should work then.

---

