---
title: "What Mailserver do I use?"
date: 2007-11-07
forum: Server Platforms
---

### Post by wh33t on 2007-11-07
I'm using webmin to manage a Ubuntu 6.06 dedicated server.

When I try to install sendmail, I get this

```
Reading package lists...
Building dependency tree...
Package sendmail is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

So... what do I use on ubuntu for mail server?

EDIT**

I should clarify, all i want to do is send out notification emails to my users from a PHP script. I do not need inbox's or anything of the sort.

---

### Post by bmathis on 2007-11-07
Postfix... derived from sendmail but easier to configure and more secure. You can set it up in less than 10 minutes.

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

---

### Post by wh33t on 2007-11-07
Thank you!

---

### Post by wh33t on 2007-11-07
Do I need to set it up as an SMTP secure ?

---

### Post by bmathis on 2007-11-07
If you follow the guide it will set you up to be secure and not a relay. I use my own variation of the guide on business systems with absolutely no issues.

---

### Post by wh33t on 2007-11-07
Ok, well I will follow the guide to make sure I don't become a relay. But this is what I get when I try to isntall postfix.

```
root@server:~# apt-get install postfix
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  exim4-base: Depends: exim4-config (>= 4.30) but it is not going to be installed or
                       exim4-config-2
E: Broken packages
root@sp4929:~# apt-get install exim4-config
Reading package lists... Done
Building dependency tree... Done
exim4-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

it appears that exim4-config in the repos is not high enough version... :(

---

### Post by bmathis on 2007-11-07
Try doing a "apt-get install" to see if it'll fix itself. 

I also recommend using aptitude, it will remember the dependencies and remove them from your system while removing a program.

---

### Post by wh33t on 2007-11-07
```
root@server:~# aptitude install postfix
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  exim4 exim4-config
The following NEW packages will be automatically installed:
  emacs21 emacs21-bin-common emacs21-common emacsen-common libice6 libsm6 libtiff4 libungif4g libxext6 libxmu6 libxt6 xaw3dg
The following packages will be automatically REMOVED:
  exim4-daemon-light
The following NEW packages will be installed:
  emacs21 emacs21-bin-common emacs21-common emacsen-common libice6 libsm6 libtiff4 libungif4g libxext6 libxmu6 libxt6 postfix xaw3dg
The following packages will be REMOVED:
  exim4-daemon-light
0 packages upgraded, 13 newly installed, 1 to remove and 0 not upgraded.
Need to get 15.0MB of archives. After unpacking 48.0MB will be used.
The following packages have unmet dependencies:
  exim4-config: Conflicts: postfix but 2.2.10-1ubuntu0.1 is to be installed.
  exim4: Depends: exim4-daemon-light but it is not installable or
                  exim4-daemon-heavy but it is not installable or
                  exim4-daemon-custom which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
exim4-daemon-light [4.60-3ubuntu3.1 (dapper-updates, dapper-security, now)]
postfix [Not Installed]

Score is 8

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
```

Still no worky :(

```
root@server:~# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

