---
title: "aptitude upgrade issue"
date: 2010-09-22
forum: Server Platforms
---

### Post by kendel on 2010-09-22
I have a mail server that I tried aptitude upgrade. However it always starts then get stuck on this screen and does nothing for 30 mins.... It happens each time, but my ns, and web server upgrade fine with no problems....
 
This is the screen it gets stuck on:
 
apache2 (2.2.15-1) unstable; urgency=low
* This release adds and enables mod_reqtimeout, which limits the time
Apache waits for a client to send a complete request. This helps to
mitigate against certain denial of service attacks. In case of problems
with slow clients, the timeout values can be adjusted in
/etc/apache2/mods-available/reqtimeout.conf , or the module can be
disabled with "a2dismod reqtimeout".
-- Chuck Short <[EMAIL="zulcss@ubuntu.com"]zulcss@ubuntu.com[/EMAIL]> Tue, 13 Apr 2010 09:09:34 -0400
/tmp/tmp6PladQ (END)
 
 
 
and It does nothing.... can't to get out of it and Ctrl+C cancels it completely..... is anyone else having this problem??

---

### Post by arrrghhh on 2010-09-22
Is that really all the output you have...?  I don't recognize that from an upgrade statement whatsoever...

---

### Post by kendel on 2010-09-22
yes that is all the output
My only option is to cancel it...

---

### Post by arrrghhh on 2010-09-22
> **kendel said:**
> yes that is all the output
My only option is to cancel it...

I don't see where you enter the aptitude statement, I don't see it looking at the headers for new downloads... nothing.  There has to be more, unless your system is completely borked!

I'd prefer to see the output from the line you type in, to the next prompt on the cli.

---

### Post by kendel on 2010-09-22
Ok let me explain, I enter the command and it begins its standard downloading of the updates... then around 89% this new screen comes up and that is all you see...
 
I can scroll oup if you want and show u where it stopped..

---

### Post by mixasgr on 2010-09-29
> **kendel said:**
> Ok let me explain, I enter the command and it begins its standard downloading of the updates... then around 89% this new screen comes up and that is all you see...
 
I can scroll oup if you want and show u where it stopped..

Hello, i am having the same issue.
Do you have the backports repository enabled?
(because i have it...)

The 2.2.15-1 version does not exist on the other repos, so i guess that there may be a problem with this version package.

Without backports the latest apache package is 2.2.14-5ubuntu8.2.
I disabled the backports repo, updated. The problem still happened when trying to upgrade from terminal and even though it was supposed to upgrade to v2.2.14... this message of 2.2.15 appeared again& again & again...! :confused:

Then i tried upgrading from my webmin panel... and magically it...upgraded!!! :confused:

```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  apache2 apache2-doc apache2-mpm-prefork apache2-utils apache2.2-bin
  apache2.2-common libavahi-client3 libavahi-common-data libavahi-common3
  linux-libc-dev
10 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 6352kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Get:1 http://security.ubuntu.com/ubuntu/ lucid-security/main libavahi-common-data 0.6.25-1ubuntu6.1 [34.2kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2 2.2.14-5ubuntu8.2 [1486B]
Get:3 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2-mpm-prefork 2.2.14-5ubuntu8.2 [2426B]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2.2-common 2.2.14-5ubuntu8.2 [290kB]
Get:5 http://security.ubuntu.com/ubuntu/ lucid-security/main libavahi-common3 0.6.25-1ubuntu6.1 [25.5kB]
Get:6 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2.2-bin 2.2.14-5ubuntu8.2 [2730kB]
Get:7 http://security.ubuntu.com/ubuntu/ lucid-security/main libavahi-client3 0.6.25-1ubuntu6.1 [56.7kB]
Get:8 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2-utils 2.2.14-5ubuntu8.2 [161kB]
Get:9 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2-doc 2.2.14-5ubuntu8.2 [2257kB]
Get:10 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-libc-dev 2.6.32-25.44 [794kB]
Reading changelogs...
apache2 (2.2.15-1) unstable; urgency=low

  * This release adds and enables mod_reqtimeout, which limits the time
    Apache waits for a client to send a complete request. This helps to
    mitigate against certain denial of service attacks. In case of problems
    with slow clients, the timeout values can be adjusted in
    /etc/apache2/mods-available/reqtimeout.conf , or the module can be
    disabled with "a2dismod reqtimeout".

 -- Chuck Short  Tue, 13 Apr 2010 09:09:34 -0400

apt-listchanges: Mailing root: apt-listchanges: news for 192.168.1.111
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
Fetched 6352kB in 20s (317kB/s)
(Reading database ... 79602 files and directories currently installed.)
Preparing to replace apache2 2.2.14-5ubuntu8 (using .../apache2_2.2.14-5ubuntu8.2_amd64.deb) ...
Unpacking replacement apache2 ...
Preparing to replace apache2-mpm-prefork 2.2.14-5ubuntu8 (using .../apache2-mpm-prefork_2.2.14-5ubuntu8.2_amd64.deb) ...
 * Stopping web server apache2
 ... waiting    ...done.
Unpacking replacement apache2-mpm-prefork ...
Preparing to replace apache2.2-common 2.2.14-5ubuntu8 (using .../apache2.2-common_2.2.14-5ubuntu8.2_amd64.deb) ...
Unpacking replacement apache2.2-common ...
Preparing to replace apache2.2-bin 2.2.14-5ubuntu8 (using .../apache2.2-bin_2.2.14-5ubuntu8.2_amd64.deb) ...
Unpacking replacement apache2.2-bin ...
Preparing to replace apache2-utils 2.2.14-5ubuntu8 (using .../apache2-utils_2.2.14-5ubuntu8.2_amd64.deb) ...
Unpacking replacement apache2-utils ...
Preparing to replace apache2-doc 2.2.14-5ubuntu8 (using .../apache2-doc_2.2.14-5ubuntu8.2_all.deb) ...
Unpacking replacement apache2-doc ...
Preparing to replace libavahi-common-data 0.6.25-1ubuntu6 (using .../libavahi-common-data_0.6.25-1ubuntu6.1_amd64.deb) ...
Unpacking replacement libavahi-common-data ...
Preparing to replace libavahi-common3 0.6.25-1ubuntu6 (using .../libavahi-common3_0.6.25-1ubuntu6.1_amd64.deb) ...
Unpacking replacement libavahi-common3 ...
Preparing to replace libavahi-client3 0.6.25-1ubuntu6 (using .../libavahi-client3_0.6.25-1ubuntu6.1_amd64.deb) ...
Unpacking replacement libavahi-client3 ...
Preparing to replace linux-libc-dev 2.6.32-24.43 (using .../linux-libc-dev_2.6.32-25.44_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for ufw ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Setting up apache2.2-bin (2.2.14-5ubuntu8.2) ...
Setting up apache2-utils (2.2.14-5ubuntu8.2) ...
Setting up apache2.2-common (2.2.14-5ubuntu8.2) ...

Setting up apache2-mpm-prefork (2.2.14-5ubuntu8.2) ...
 * Starting web server apache2
   ...done.

Setting up apache2 (2.2.14-5ubuntu8.2) ...

Setting up apache2-doc (2.2.14-5ubuntu8.2) ...
 * Reloading web server config apache2
   ...done.

Setting up libavahi-common-data (0.6.25-1ubuntu6.1) ...
Setting up libavahi-common3 (0.6.25-1ubuntu6.1) ...

Setting up libavahi-client3 (0.6.25-1ubuntu6.1) ...

Setting up linux-libc-dev (2.6.32-25.44) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

.. upgrade complete.
```


Hope you fixed it!

---

### Post by GoremanX on 2010-10-19
The message that comes up is displayed in Vi. Simply type:

```
:q!
``` and press enter to close it and continue with the update process.

---

### Post by valugi on 2012-02-20
> **GoremanX said:**
> The message that comes up is displayed in Vi. Simply type:

```
:q!
``` and press enter to close it and continue with the update process.

This works. It would be nice to have this messages somewhere else, not interrupting a process that maybe automatic.

---

