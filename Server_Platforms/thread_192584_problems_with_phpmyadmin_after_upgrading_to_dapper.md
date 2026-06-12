---
title: "problems with phpmyadmin after upgrading to dapper"
date: 2006-06-08
forum: Server Platforms
---

### Post by bloodroses75 on 2006-06-08
[COLOR="Red"]post redone for correct forum[/COLOR]
orignal post [http://www.ubuntuforums.org/showthread.php?t=189231]("http://www.ubuntuforums.org/showthread.php?t=189231")

I had just recently upgraded from breezy to dapper via modifying the souces list and running synaptic. Overall, the upgrade went very well with only a few minor issues (icons dissapearing in rox-filer). However, there is one issue that I have now regarding phpmyadmin. When i try to access the page via locally, by remote computer, or by 127.0.0.1 I keep getting the same error:

<b>500 Internal Server Error</b>



<b>Internal Server Error</b>

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Ubuntu) DAV/2 mod_jk2/2.0.4 mod_ldap_userdir/1.1.8 PHP/5.1.2 mod_ruby/1.2.5 Ruby/1.8.4(2005-12-24) mod_perl/2.0.2 Perl/v5.8.7 Server at sunfire Port 80


I get this same error when i try to run kplaylist.1.6.401 (which worked fine before the upgrade).

So far, I have tried running the page under root and a complete removal/reinstall of phpmyadmin with no luck in either case. I possibly thought that the php and mysql installation got messed up from the upgrade, but all php scripts I have written before the upgrade still work, along with ones that require SQL access (with the queries working fine).

Should I also try complete removal/reinstalls of php and mysql? I do not want to have to rebuild my databases unless that is my only option. Also, could it be caused from a deb package I dont have installed (or even a bad one that is installed like php4 stuff)?

Any advice would be greatly appreciated

---

