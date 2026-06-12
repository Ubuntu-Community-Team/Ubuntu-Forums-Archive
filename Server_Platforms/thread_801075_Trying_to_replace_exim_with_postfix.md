---
title: "Trying to replace exim with postfix"
date: 2008-05-20
forum: Server Platforms
---

### Post by garg on 2008-05-20
Hello,
I installed Ubuntu 8.04 using the howto forge perfect server tutorial. I also installed request tracker 3.6 using apt-get. It installed fine but it ended up installing exim. 

Now when I try to install postfix, it gives me the following:

```
root@it:/# apt-get install postfix libsasl2-2 sasl2-bin libsasl2-modules procmail
Reading package lists... Done
Building dependency tree
Reading state information... Done
libsasl2-2 is already the newest version.
libsasl2-modules is already the newest version.
The following extra packages will be installed:
  db4.6-util
Suggested packages:
  mail-reader postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql resolvconf
The following packages will be REMOVED:
  exim4-base exim4-config exim4-daemon-light
The following NEW packages will be installed:
  db4.6-util postfix procmail sasl2-bin
0 upgraded, 4 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/1556kB of archives.
After this operation, 201kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: exim4-base: dependency problems, but removing anyway as you request:
 exim4-daemon-light depends on exim4-base (>= 4.69).
(Reading database ... 26826 files and directories currently installed.)
Removing exim4-base ...
 * Stopping MTA                                                                                                                                       [ OK ]
Removing exim4-config ...
dpkg: exim4-daemon-light: dependency problems, but removing anyway as you request:
 rt3.6-clients depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
 request-tracker3.6 depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
Removing exim4-daemon-light ...
 * Stopping MTA                                                                                                                                              /sbin/start-stop-daemon: warning: failed to kill 4318: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-daemon-light (--remove):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 exim4-daemon-light
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems as if exim is listed as a dependency for request tracker. If I try to remove exim-base then it tries to delete request tracker 3.6

Is there a way I can remove it as a dependency so I can uninstall it and replace it with postfix with out deleting request tracker?

---

### Post by MJN on 2008-05-20
Apt tries its very best to not leave you in a state where you have unmet dependencies, yet sometimes doesn't look far enough ahead to realise it will come good if it carries on as requested. Whilst there may be a way around it with apt-get I would suggest the following to remove Exim4 using dpkg being told to ignore the fact that rt3.6-clients and request-tracker3.6 requires a mail-transport-agent:

```
sudo dpkg --simulate --ignore-depends mail-transport-agent -r exim4 exim4-base exim4-daemon-light
```(the --simulate option will allow you to see what will happen with this command without actually doing it - remove it when happy, and I've included all exim4 packages which may or may not have been removed with your previous apt-get attempt)

Then install Postfix (etc) with apt-get (which will in turn satisfy the mail-transport-agent dependency).

Mathew

---

### Post by jayhags on 2008-06-12
I found with the above 'dpkg --ignore-...' command, I still had a failure to remove the exim4-daemon-light package due to a package removal error: Could not stop the MTA.  It actually was not running, but I needed to manually remove the /var/run/exim4/exim4.pid file before the removal command was sucessful.  I could then install postfix via apt-get.

---

