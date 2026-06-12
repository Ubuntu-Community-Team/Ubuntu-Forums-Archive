---
title: "Ubuntu 6.06 LTS and Perl/PCRE"
date: 2007-11-06
forum: Server Platforms
---

### Post by Danos on 2007-11-06
Hi

I note a recent vulnerability was found in Perl/PCRE:
From [http://www.heise-security.co.uk/news/98524](http://www.heise-security.co.uk/news/98524)
> The Perl Regular Expression Engine contains a vulnerability that can cause an application written in Perl to crash and possibly even allow code to be injected. The problem is reportedly the result of a memory allocation error during the handling of an expression. Any code thus injected into a Web server would run with the privileges of the Web server. No further details concerning the flaw have been revealed. The current version 5.8.8 and previous are affected. Linux distributors are already releasing patched packages, but no official Perl update has been released yet.

But there is more bad news. Tavis Ormandy of Google Security has discovered several vulnerabilities in the Perl-Compatible Regular Expressions library (PCRE) that allow attackers to crash an application written in Perl. Debian says that it is possible to execute malicious code on vulnerable systems because some of the problems are due to heap overflows. Many open source projects – Apache, PHP, Postfix, KDE and Exim, among others – use the library. Versions 6.x and 7.x are affected, though the flaws have been remedied in the official version 7.4. Debian has published new packages.

See also:

    * [perl security update]("https://rhn.redhat.com/errata/RHSA-2007-0966.html"), Red Hat security advisory
    * [Updated perl packages fix vulnerability]("http://www.mandriva.com/en/security/advisories?name=MDKSA-2007:207"), Mandrake security advisory
    * [pcre3 -- several vulnerabilities]("http://www.debian.org/security/2007/dsa-1399"), Debian security advisory


I note that no updates are currently available for 6.06, just did an update/upgrade:
> ii  libpcre3                           6.4-1.1ubuntu4                Perl 5 Compatible Regular Expression Library
ii  libpcre3-dev                       6.4-1.1ubuntu4                Perl 5 Compatible Regular Expression Library
ii  libpcrecpp0                        6.4-1.1ubuntu4                Perl 5 Compatible Regular Expression Library
ii  postfix-pcre                       2.2.10-1ubuntu0.1             PCRE map support for Postfix
..
ii  perl                               5.8.7-10ubuntu1               Larry Wall's Practical Extraction and Report
ii  perl-base                          5.8.7-10ubuntu1               The Pathologically Eclectic Rubbish Lister
ii  perl-doc                           5.8.7-10ubuntu1               Perl documentation
ii  perl-modules                       5.8.7-10ubuntu1               Core Perl modules


From what I understand I am vulnerable. Can somebody tell me when  we can expect updates (or that I am wrong)?

---

