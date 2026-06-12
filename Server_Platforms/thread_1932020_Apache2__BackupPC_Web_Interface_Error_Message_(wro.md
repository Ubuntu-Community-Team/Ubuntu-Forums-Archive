---
title: "Apache2 / BackupPC Web Interface Error Message (wrong user id)"
date: 2012-02-26
forum: Server Platforms
---

### Post by Starcalc on 2012-02-26
After doing the last "do-release-upgrade" to the current version (oneiric/11.10), my backuppc-Webinterface errors to "Error: Wrong user: my userid is 33, instead of 112(backuppc)".

I did not have this error before the upgrade. Did the apache2.conf change? Or is there another idea?

I don't want to run the whole apache2 on the requested user "backuppc", as www-data is great and used for different directories.

Other articles which I found on the web did not refer to the web interface. Backuppc itself is running and still backing up.

Is there any way that I can see what the (default) apache2.conf for the different Ubuntu versions were? (11.04 to 11.10)

Thanks, any help is appreciated.

Starcalc

---

### Post by Starcalc on 2012-03-07
It needed some time to get behind the real problem and why the upgrade to 11.10 caused the problem. By upgrading, suid-perl was removed.

[http://manpages.ubuntu.com/manpages/lucid/man1/perlsec.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/perlsec.1.html)

> The use of suidperl is considered deprecated, and will be removed in Perl 5.12.0.  It is strongly recommended that all code uses the simplier and more secure C-wrappers described below.

So I wrote a wrapper-script as suggested:

```
#define REAL_PATH "/usr/local/BackupPC/cgi-bin/BackupPC_Admin"            main(ac, av)                char **av;            {                execv(REAL_PATH, av);            }
```

Compiled it:

```
gcc -o index.cgi wrapper.c
```

And set the suid on the newly generated index.cgi:

```
chmod +s index.cgi
```

And everything is working fine again, without changing any configuration at all.

---

