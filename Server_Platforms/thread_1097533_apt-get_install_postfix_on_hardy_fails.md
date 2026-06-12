---
title: "apt-get install postfix on hardy fails"
date: 2009-03-16
forum: Server Platforms
---

### Post by _coda_ on 2009-03-16
Hello

(I have looked for a similar issue here but found nothing. :)

apt-get install postfix fails as follows:

-- start of quote ------------
xxxx$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql resolvconf
The following packages will be REMOVED:
  exim4 exim4-base exim4-config exim4-daemon-light
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/1160kB of archives.
After this operation, 991kB disk space will be freed.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 37338 files and directories currently installed.)
Removing exim4 ...
dpkg: exim4-base: dependency problems, but removing anyway as you request:
 exim4-daemon-light depends on exim4-base (>= 4.69).
Removing exim4-base ...
 * Stopping MTA                                                                                                                                 [ OK ] 
Removing exim4-config ...
dpkg: exim4-daemon-light: dependency problems, but removing anyway as you request:
 sensible-mda depends on sendmail-bin | mail-transport-agent; however:
  Package sendmail-bin is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
 mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
Removing exim4-daemon-light ...
 * Stopping MTA                                                                                                                                        /sbin/start-stop-daemon: warning: failed to kill 26400: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-daemon-light (--remove):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 exim4-daemon-light
E: Sub-process /usr/bin/dpkg returned an error code (1)
- end of quote -------------

I'm forced to use hardy by the host provider. I've recently installed a couple of intrepid servers with postfix with no problem.

I now have exim running as the MTA but I'd prefer to use postfix.

I have tried switching to some of the us ubuntu repositories (this server is in europe) but these don't even find a package for postfix on hardy!


Any clues?

thanks

---

### Post by volkswagner on 2009-03-16
From what I can see postfix is not the problem.  You may need to purge the system of exim first.  I appears Exim is not completely removed.

You should stop exim from running than remove it.  I am not running exim, not sure of the exact command, try...

```
sudo killall exim
```

```
sudo aptitude purge exim
```

Then see if you have any remaining packages, they will be marked with an "i" for "installed".

```
sudo aptitude search exim
```

If there are still any packages, you may need to remove them manually.

Then try to install postfix.

```
sudo aptitude install postfix
```

---

### Post by _coda_ on 2009-03-17
volkswagner,

Thanks. That seems to have done the trick.

---

