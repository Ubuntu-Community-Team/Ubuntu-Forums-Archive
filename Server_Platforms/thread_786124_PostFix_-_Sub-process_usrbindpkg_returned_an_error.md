---
title: "PostFix - Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2008-05-07
forum: Server Platforms
---

### Post by KevinD_Atl on 2008-05-07
Ubuntu Server 6.0.6

When trying to install Postfix --- Get These Errors

[HTML]
root@ubuman:~# apt-get -f install postfix libsasl2 sasl2-bin libsasl2-modules libdb3-util procmail
Reading package lists... Done
Building dependency tree... Done
postfix is already the newest version.
libsasl2 is already the newest version.
sasl2-bin is already the newest version.
libsasl2-modules is already the newest version.
libdb3-util is already the newest version.
procmail is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.10-1ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: ubuman.hsd1.ga.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: ubuman.hsd1.ga.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuman:~#[/HTML]

---

### Post by MJN on 2008-05-08
It looks like Postfix was already installed (and configured by the looks of it) - howcome you are attempting (re)install? (or is it because it's not working?)
 
Check the hostname directive in /etc/postfix/main.cf - it's hard to tell from the error but it could be that you have a dot at the end of the hostname (conventionally error output does not include full stops at the end of sentences).
 
Alternatively, post your config (postconf -n) and we can take a look.
 
Mathew

---

### Post by KevinD_Atl on 2008-05-08
[FONT="Georgia"]Booya, you the man. It was a period after my hostname. Deleted and re-installed.
Newaliases stopped and started fine[/FONT]

---

### Post by bloodfilledwater on 2009-04-19
I have the same issue...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.5.5-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)


I did install it originally, which worked fine, than removed it to use another MTA, but didn't like it so I tried to re-install postfix and now get this error. Any ideas?

---

### Post by gnik1 on 2010-06-02
> **MJN said:**
> It looks like Postfix was already installed (and configured by the looks of it) - howcome you are attempting (re)install? (or is it because it's not working?)
 
Check the hostname directive in /etc/postfix/main.cf - it's hard to tell from the error but it could be that you have a dot at the end of the hostname (conventionally error output does not include full stops at the end of sentences).
 
Alternatively, post your config (postconf -n) and we can take a look.
 
Mathew


This fixed my postfix problem. There was a period at the end of myhostname in the main.cf file.
Switch to the directory 
cd /
then cd etc
then cd postfix
then sudo gedit main.cf 
then take the dot off the end of myhostname line

 I had that problem for a month. Was worried things weren't installing correctly but now I know they were installing just fine. 

Thanks!!!!

---

### Post by MJN on 2010-06-03
You're welcome - good to see such an old thread still of some use!

Mathew

---

### Post by Coplen on 2011-04-07
Go into /var/lib/dpkg/info and delete everything that had the name of the program giving you errors. :D

---

