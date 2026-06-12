---
title: "Postfix"
date: 2007-01-08
forum: Server Platforms
---

### Post by nhandler on 2007-01-08
I had attempted to install postfix. Things didn't work out, and I ended up installing/removing it numerous times. Now (I finally found the article in the wiki), I'm trying to install it again. Here is the error I'm getting:
```
$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre resolvconf
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/1067kB of archives.
After unpacking 2494kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 158721 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.3.3-1_i386.deb) ...
Setting up postfix (2.3.3-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ ok ] 
 * Starting Postfix Mail Transport Agent postfix                                postfix: fatal: /etc/postfix/postfix-script: No such file or directory
                                                                         [fail]
invoke-rc.d: initscript postfix, action "restart" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
The last line shows up when I try to install any package. How do I fix this?

---

### Post by rth on 2007-01-08
I'm guessing you could run:

dpkg-reconfigure postfix

Or do a "Mark for complete removal" of Postfix and then reinstall it using Synaptic. And make sure that /etc/postfix has no .cf files for configuration.

---

### Post by nhandler on 2007-01-08
> **rth said:**
> I'm guessing you could run:

dpkg-reconfigure postfix

Or do a "Mark for complete removal" of Postfix and then reinstall it using Synaptic. And make sure that /etc/postfix has no .cf files for configuration.

When I enter sudo dpkg-reconfigure postfix, I get this:
dpkg-reconfigure postfix


If I remove postfix with 'sudo apt-get autoremove postfix', remove the .cf files from /etc/postfix, and then install postfix from synaptic, I get this error 'E: postfix: subprocess post-installation script returned error exit status 1'

---

### Post by sav2005 on 2007-01-09
I'm having the same issue. Is the package broken?

---

### Post by nhandler on 2007-01-09
> **sav2005 said:**
> I'm having the same issue. Is the package broken?

I don't think the package is broken. If you did the same thing I did, chances are we have some files on the computer somewhere that don't get removed with sudo apt-get remove postfix. Now, when it tries to reinstall, it runs into problems.

---

