---
title: "spamassassin and Perl_Tstack_sp_ptr"
date: 2009-07-10
forum: Server Platforms
---

### Post by oscarBravo on 2009-07-10
Hi - after an update, spamassassin doesn't work anymore. I think the update brought perl up to 5.10, and the problem is:  ```
/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Razor2/Preproc/deHTMLxs/deHTMLxs.so: undefined symbol: Perl_Tstack_sp_ptr
``` perl: ```
perl:
  Installed: 5.10.0-11.1ubuntu2.3
  Candidate: 5.10.0-11.1ubuntu2.3
  Version table:
 *** 5.10.0-11.1ubuntu2.3 0
        500 http://ie.archive.ubuntu.com intrepid-updates/main Packages
        500 http://security.ubuntu.com intrepid-security/main Packages
        100 /var/lib/dpkg/status
     5.10.0-11.1ubuntu2 0
        500 http://ie.archive.ubuntu.com intrepid/main Packages
``` spamassassin: ```
spamassassin:
  Installed: 3.2.5-1ubuntu1.1
  Candidate: 3.2.5-1ubuntu1.1
  Version table:
 *** 3.2.5-1ubuntu1.1 0
        500 http://ie.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     3.2.5-1ubuntu1 0
        500 http://ie.archive.ubuntu.com intrepid/main Packages
``` Any ideas? I'm buried in spam!

---

### Post by nastsite on 2011-04-23
File ...../Razor2/Preproc/deHTMLxs/deHTMLxs.so owned to Razor, After update Razor smae problem was solved for me. 

Maybe it would be interesting for anyone else

---

