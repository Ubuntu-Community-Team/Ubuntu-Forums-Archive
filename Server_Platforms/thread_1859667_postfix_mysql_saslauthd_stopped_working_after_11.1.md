---
title: "postfix mysql saslauthd stopped working after 11.10"
date: 2011-10-14
forum: Server Platforms
---

### Post by rabbadabb on 2011-10-14
Hi

I upgraded to 11.10 yesterday and all of a sudden my postfix/mysql/saslauthd/courier installation stopped working.
saslfinger -s turns up empty in
-- mechanisms on localhost --

might be because /usr/lib/sasl2 looks like:
-- listing of /usr/lib/sasl2 --
total 52
drwxr-xr-x   2 root root  4096 2011-10-11 15:01 .
drwxr-xr-x 102 root root 40960 2011-10-14 08:34 ..
-rw-r--r--   1 root root     1 2011-10-10 14:01 berkeley_db.active
-rw-r--r--   1 root root     1 2011-08-16 01:42 berkeley_db.txt


Tried to reinstall all of saslauthd by purging all installed packages, result is the same.
Postfix log shows:

SASL PLAIN authentication failed: no mechanism available

Anyone else who has this problem or a solution?

Cheers!

---

### Post by croxis on 2011-10-15
I have this problem as well for using saslauthd with user accounts.

---

### Post by emunson on 2011-10-15
Just opened [this]("http://ubuntuforums.org/showthread.php?t=1861692") thread on the same topic, mods please close my duplicate.

---

### Post by emunson on 2011-10-15
With others seeing the same problem I opened a bug here: [https://bugs.launchpad.net/ubuntu/+bug/875440](https://bugs.launchpad.net/ubuntu/+bug/875440), please click the "This bug affects me" link if you are still having the same problems.

---

### Post by otlayi on 2011-10-15
I hesitated in upgrading our live machines, finally did it this weekend, same thing, mail won't send.  saslauthd keeps giving "SASL PLAIN authentication failed: no mechanism available
SASL LOGIN authentication failed: no mechanism available"

Reinstalling libraries seems to have absolutely no effect, and there is nothing else being printed in the logs related to this at all

---

### Post by rabbadabb on 2011-10-16
Just a thought, the libs have moved to:
/usr/lib/x86_64-linux-gnu/sasl2

saslfinger -ss shows in it's output that it is looking in /usr/lib/sasl2 which is empty...

Tried to soft link to the new lib instead, still same problem.

---

### Post by otlayi on 2011-10-16
> **rabbadabb said:**
> Just a thought, the libs have moved to:
/usr/lib/x86_64-linux-gnu/sasl2

saslfinger -ss shows in it's output that it is looking in /usr/lib/sasl2 which is empty...

Tried to soft link to the new lib instead, still same problem.

I just did the same, still getting the same error, good find, that's the multiarch vs hardcoded path problem I found on Google last night.  Really need to get my mail back online too :x

Any have any thoughts on the easiest way to downgrade without breaking other things as a temp fix if an update isn't coming out asap?

---

### Post by Jarozas on 2011-10-16
Same problem.
 
I'm able to send and receive mails using Squirrelmail (IMAP).
 
I've readed somewhere that reverting some packages related to sasl libraries can solve the problem, but I'm not sure.
 
We need to wait for a solution or fix... and pray

---

### Post by otlayi on 2011-10-16
> **Jarozas said:**
> We need to wait for a solution or fix... and pray


After going crazy and not giving up, **I HAVE found a solution!!!**

The problem is with the 2.1.24rc1 package of cyrus-sasl.  I tried a bunch of different versions (pre 2.1.24rc1 you have to fix a .c file to compile) and I kept getting errors about libldap.  The CURRENT version of cyrus-sasl is 2.1.25, source can be found at: [ftp://ftp.cyrusimap.org/cyrus-sasl/cyrus-sasl-2.1.25.tar.gz](ftp://ftp.cyrusimap.org/cyrus-sasl/cyrus-sasl-2.1.25.tar.gz)

```

wget ftp://ftp.cyrusimap.org/cyrus-sasl/cyrus-sasl-2.1.25.tar.gz
tar xvfz cyrus-sasl-2.1.25.tar.gz
cd cyrus-sasl-2.1.25
./configure --enable-sql --with-ldap
make
make install
rm -rf /usr/lib/sasl2
ln -s /usr/local/lib/sasl2 /usr/lib/sasl2
/etc/init.d/saslauthd restart
/etc/init.d/postfix restart

```

I totally hate the idea of deviating from an ubuntu installed library, but you can't uninstall it without uninstall postfix and a whole lot of extra necessary programs.  But this is for sure working for me and everyone is able to send mail again.  Whew!

**NOTE:** while messing with this I got a few errors caused by me also having 32bit libs, apt-get remove libsasl2-2:i386 fixed that for me.

---

### Post by Jarozas on 2011-10-16
Hello Otlayi,
 
Your message looks like a light in the dark but ... the make and make install gave a lot of errors and nothing new is installed. 
 
I cannot do "apt-get remove libsasl2-2:i386" they do practically nothing and warns about some dependences with apache2.
 
I've setup my server following [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04) and now I'm in a trouble with my users.
 
But I got wise, next time I'll wait for a few months before to do a release upgrade.
 
Thanks for your contribution.

---

### Post by otlayi on 2011-10-16
> **Jarozas said:**
> Your message looks like a light in the dark but ... the make and make install gave a lot of errors and nothing new is installed.

Care to share what compile errors you're getting?  I'm assuming it's got to be just a dependency or it's something pretty basic.  I was getting some compile errors on previous versions of sasl but it was a simple gcc 3 vs gcc 4 problem that took an update of 2 lines.

---

### Post by Jarozas on 2011-10-16
Hello,
 
I post some errors in hope someone can help:
---------------------------------
 
When do make
....................
db_berkeley.c:371:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
make[2]: *** [db_berkeley.lo] Error 1
make[2]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25'
make: *** [all] Error 2
 
 
 
when do make install
............
db_berkeley.c:371:6: warning: passing argument 3 of 'utils->getcallback' from incompatible pointer type [enabled by default]
db_berkeley.c:371:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
make[1]: *** [db_berkeley.lo] Error 1
make[1]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
make: *** [install-recursive] Error 1

---

### Post by otlayi on 2011-10-16
> **Jarozas said:**
> Hello,
 
I post some errors in hope someone can help:
---------------------------------
 
When do make
....................
db_berkeley.c:371:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
make[2]: *** [db_berkeley.lo] Error 1
make[2]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25'
make: *** [all] Error 2
 
 
 

If 'make' doesn't complete then 'make install' is definitely not going to install, it's still trying to make and runs the same thing.

Can you give a couple lines above that if there is anything useful?  I have a lot of libraries installed on my system already, but you might want to try apt-get install libdb-dev to see if you have the berkeley db library files

---

### Post by Jarozas on 2011-10-16
Here goes the complete output after do make:
---------------------------------------------------------------------------------------
~/cyrus/cyrus-sasl-2.1.25# make
make  all-recursive
make[1]: Entering directory `/root/cyrus/cyrus-sasl-2.1.25'
Making all in include
make[2]: Entering directory `/root/cyrus/cyrus-sasl-2.1.25/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/include'
Making all in sasldb
make[2]: Entering directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
/bin/sh ../libtool   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I../include -I../include   -DOBSOLETE_CRAM_ATTR=1 -I/usr/include/mysql -I/usr/include  -Wall -W -g -O2 -MT db_berkeley.lo -MD -MP -MF .deps/db_berkeley.Tpo -c -o db_berkeley.lo db_berkeley.c
gcc -DHAVE_CONFIG_H -I. -I.. -I../include -I../include -DOBSOLETE_CRAM_ATTR=1 -I/usr/include/mysql -I/usr/include -Wall -W -g -O2 -MT db_berkeley.lo -MD -MP -MF .deps/db_berkeley.Tpo -c db_berkeley.c  -fPIC -DPIC -o db_berkeley.lo
db_berkeley.c: In function 'berkeleydb_open':
db_berkeley.c:82:6: warning: passing argument 3 of 'utils->getcallback' from incompatible pointer type [enabled by default]
db_berkeley.c:82:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
db_berkeley.c:107:2: warning: passing argument 2 of '(*mbdb)->open' from incompatible pointer type [enabled by default]
db_berkeley.c:107:2: note: expected 'struct DB_TXN *' but argument is of type 'const char *'
db_berkeley.c:107:2: warning: passing argument 4 of '(*mbdb)->open' makes pointer from integer without a cast [enabled by default]
db_berkeley.c:107:2: note: expected 'const char *' but argument is of type 'int'
db_berkeley.c:107:2: error: too few arguments to function '(*mbdb)->open'
db_berkeley.c: In function '_sasl_check_db':
db_berkeley.c:371:6: warning: passing argument 3 of 'utils->getcallback' from incompatible pointer type [enabled by default]
db_berkeley.c:371:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
make[2]: *** [db_berkeley.lo] Error 1
make[2]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25'
make: *** [all] Error 2
----------------------------------------------------
 
 
Any clue?
 
Thank you for your atention.
 
(Now I'll go to sleep it's to late here 4:18 am)

---

### Post by otlayi on 2011-10-17
> **Jarozas said:**
> Here goes the complete output after do make:
---------------------------------------------------------------------------------------
~/cyrus/cyrus-sasl-2.1.25# make
make  all-recursive
make[1]: Entering directory `/root/cyrus/cyrus-sasl-2.1.25'
Making all in include
make[2]: Entering directory `/root/cyrus/cyrus-sasl-2.1.25/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/include'
Making all in sasldb
make[2]: Entering directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
/bin/sh ../libtool   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I../include -I../include   -DOBSOLETE_CRAM_ATTR=1 -I/usr/include/mysql -I/usr/include  -Wall -W -g -O2 -MT db_berkeley.lo -MD -MP -MF .deps/db_berkeley.Tpo -c -o db_berkeley.lo db_berkeley.c
gcc -DHAVE_CONFIG_H -I. -I.. -I../include -I../include -DOBSOLETE_CRAM_ATTR=1 -I/usr/include/mysql -I/usr/include -Wall -W -g -O2 -MT db_berkeley.lo -MD -MP -MF .deps/db_berkeley.Tpo -c db_berkeley.c  -fPIC -DPIC -o db_berkeley.lo
db_berkeley.c: In function 'berkeleydb_open':
db_berkeley.c:82:6: warning: passing argument 3 of 'utils->getcallback' from incompatible pointer type [enabled by default]
db_berkeley.c:82:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
db_berkeley.c:107:2: warning: passing argument 2 of '(*mbdb)->open' from incompatible pointer type [enabled by default]
db_berkeley.c:107:2: note: expected 'struct DB_TXN *' but argument is of type 'const char *'
db_berkeley.c:107:2: warning: passing argument 4 of '(*mbdb)->open' makes pointer from integer without a cast [enabled by default]
db_berkeley.c:107:2: note: expected 'const char *' but argument is of type 'int'
db_berkeley.c:107:2: error: too few arguments to function '(*mbdb)->open'
db_berkeley.c: In function '_sasl_check_db':
db_berkeley.c:371:6: warning: passing argument 3 of 'utils->getcallback' from incompatible pointer type [enabled by default]
db_berkeley.c:371:6: note: expected 'int (**)(void)' but argument is of type 'int (**)(void *, const char *, const char *, const char **, unsigned int *)'
make[2]: *** [db_berkeley.lo] Error 1
make[2]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25/sasldb'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cyrus/cyrus-sasl-2.1.25'
make: *** [all] Error 2
----------------------------------------------------
 
 
Any clue?
 
Thank you for your atention.
 
(Now I'll go to sleep it's to late here 4:18 am)


After getting my system up and running last night, aptitude had dependency issues, so I decided to deal with it then instead of putting it off.  I re-broke my smtp, and have been going in loops again.  Repeating the same steps from history and not getting very far.

The GOOD news: I got the exact error you did above, and it was because I had libdb5.1-dev installed (installed libdb-dev did that automatically).  When I replaced it with libdb4.7-dev it instantly compiled.  I have maverick backports installed but I'm pretty sure both versions are available stock intentionally to give you the options (there is also 4.8-dev i did not try).  Try that, and install.


The **current** problem that I keep running into is every time I install a different libsasl version, saslfinger/saslauthd etc gives "libsasl2.so.2: no version information available (required by /usr/lib/libldap...".

In order to get the error to go away, I had to make install cyrus-sasl, apt-get --reinstall the sasl libls, then make uninstall.  Anything else and it wouldn't go away.  I've tried using previous versions of the libsasl and libldap packages but I get the error above "no version information available (required by.." everytime.  

At this point I think I might have just messed around with the packages too much and I'm not sure if I can get my system back the way it was previously.  I tried to install openldap (so it would be directly compiled against/with cyrus-sasl), it doesn't have a 'make uninstall' (how convenient..) and now it gives:
/usr/sbin/saslauthd: /usr/local/lib/liblber-2.4.so.2: no version information available (required by /usr/sbin/saslauthd)
/usr/sbin/saslauthd: /usr/local/lib/libldap_r-2.4.so.2: no version information available (required by /usr/sbin/saslauthd)


I actually thought I waited long enough before upgrading to 11.10..

---

### Post by otlayi on 2011-10-17
For what it's worth, after manually finding and removing all of the openldap files that installed with make install, I've gotten my system back up to the previous problem.

cyrus-sasl-2.1.25 is what I definitely had installed last night that was working, when I make install and then start saslauthd I instantly get **/usr/sbin/saslauthd: /usr/local/lib/libsasl2.so.2: no version information available (required by /usr/lib/x86_64-linux-gnu/libldap_r-2.4.so.2)**  'make uninstall' will get remove the error (went in circles last night where libsasl2 needed reinstalled from app AFTER sasl-2.1.25 was make installed, and the error about 'no version information available' would only go away after 'make uninstall' on sasl-2.1.25 (but if it was uninstalled while libs were reinstalled the error would persist).

---

### Post by Jarozas on 2011-10-17
Thanks Otlayi,

I'll try this night.

Do you have a link for download libdb4.7-dev?

---

### Post by otlayi on 2011-10-17
> **Jarozas said:**
> Thanks Otlayi,

I'll try this night.

Do you have a link for download libdb4.7-dev?

apt-get install libdb4.7-dev libdb4.7
It's part of the standard aptitude packages, [http://packages.ubuntu.com/oneiric/libdb4.7](http://packages.ubuntu.com/oneiric/libdb4.7)

---

### Post by Jarozas on 2011-10-17
Cannot remove libdb5.1, apt-get don't let me do so. 
I've removed libdb5.1-dev with no complain, and installed libdb4.7-dev, but errors are still present and can't compile.

---

### Post by otlayi on 2011-10-17
I was able to get my system back online by grabbing the following packages from natty (compressed to 1 wget command: libsasl2-2, libsasl2-dev, libsasl2-modules, libsasl2-modules-sql and sasl2-bin)
wget [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules-sql_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules-sql_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-dev_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-dev_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/sasl2-bin_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/sasl2-bin_2.1.23.dfsg1-5ubuntu3_amd64.deb)
**EDIT:** If you've got a 32bit system, replace _amd64 in all 5 of the urls with _i386

I'd recommend making a folder, putting the above files into it, and dpkg -i *.deb

I have aptitude running without conflicts now (it would like to upgrade sasl if I let it) and Postfix/SASL is sending and receiving without problems.

---

### Post by Jarozas on 2011-10-17
Hi Otlayi,
 
How do you to remove the libsasl 2.1-24 packages?

---

### Post by otlayi on 2011-10-17
> **Jarozas said:**
> Hi Otlayi,
 
How do you to remove the libsasl 2.1-24 packages?

You don't need to, if dpkg -i is giving you errors, dpkg -i --force-all

Worst case scenario you can apt-get install --reinstall those same 5 packages from aptitude and you should be back to where you are now.

---

### Post by Jarozas on 2011-10-17
Great man!!!!!!!!!!!!!!!!!!!
 
It works!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Jarozas on 2011-10-17
You have a beer paid if you visit Spain someday.
 
Don't forget to post the solution in the bugs page. 
 
It can help a lot of people.

---

### Post by otlayi on 2011-10-17
> **Jarozas said:**
> Great man!!!!!!!!!!!!!!!!!!!
 
It works!!!!!!!!!!!!!!!!!!!!!!!!!!

Awesome, I'm glad that this sleepless weekend went to good use - I was going crazy staring at my monitors compile :)  

> **Jarozas said:**
> You have a beer paid if you visit Spain someday.
 
Don't forget to post the solution in the bugs page. 
 
It can help a lot of people.
I'll go ahead and do that.  Hopefully one of the maintainers of cyrus-sasl's Ubuntu will be able to get it sorted, or one of the libraries will post an update and all will be well in the world saslauthd

---

### Post by rabbadabb on 2011-10-18
Awesome! Finally a working mailserver! I owe you one!

---

### Post by emunson on 2011-10-18
Thank you so much, I have a working mail sever again!

---

### Post by otlayi on 2011-10-18
> **emunson said:**
> Thank you so much, I have a working mail sever again!
Glad I could save some other people from the hell that was my weekend ;)

---

### Post by TravisZ on 2011-10-27
> **otlayi said:**
> I was able to get my system back online by grabbing the following packages from natty (compressed to 1 wget command: libsasl2-2, libsasl2-dev, libsasl2-modules, libsasl2-modules-sql and sasl2-bin)
wget [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules-sql_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules-sql_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-dev_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-dev_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/sasl2-bin_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/sasl2-bin_2.1.23.dfsg1-5ubuntu3_amd64.deb)
**EDIT:** If you've got a 32bit system, replace _amd64 in all 5 of the urls with _i386

I'd recommend making a folder, putting the above files into it, and dpkg -i *.deb

I have aptitude running without conflicts now (it would like to upgrade sasl if I let it) and Postfix/SASL is sending and receiving without problems.

otlayi,

Thank you for this :D

Saved me a bunch of trouble :)

---

### Post by vindolin on 2011-10-31
after installing the natty packages my saslauthd complains about:

/usr/sbin/saslauthd: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: No such file or directory

ps: this is my first try at setting up a mailserver and it took me 4 hours to find out it was a bug in 11.10 and not my config :P


oops.. must have done something wrong.. tried it again and now its working

---

### Post by rabbadabb on 2011-11-09
OK, worked a lot with the configuration and finally got saslfinger to recognize that it has some functions :D:

-- mechanisms on localhost --
250-AUTH PLAIN CRAM-MD5 LOGIN DIGEST-MD5

But still the mail.log shows:

SASL PLAIN authentication failed: no mechanism available

Is there no solution yet? :confused:

---

### Post by swehes on 2011-12-01
So I am having the same issue. So I went through the process and downgraded to 23. I think it works. However I don't know how to check it. What port am I supposed to use to connect to the mail server for SMTP? And how do I check which port it runs on??

---

### Post by phinole on 2012-01-18
> **otlayi said:**
> I was able to get my system back online by grabbing the following packages from natty (compressed to 1 wget command: libsasl2-2, libsasl2-dev, libsasl2-modules, libsasl2-modules-sql and sasl2-bin)
wget [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules-sql_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules-sql_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-dev_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-dev_2.1.23.dfsg1-5ubuntu3_amd64.deb) [http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/sasl2-bin_2.1.23.dfsg1-5ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/sasl2-bin_2.1.23.dfsg1-5ubuntu3_amd64.deb)
**EDIT:** If you've got a 32bit system, replace _amd64 in all 5 of the urls with _i386

I'd recommend making a folder, putting the above files into it, and dpkg -i *.deb

I have aptitude running without conflicts now (it would like to upgrade sasl if I let it) and Postfix/SASL is sending and receiving without problems.

Thank you for posting this solution!  I recently upgraded 11.04 to 11.10 and ran into the dreaded SASL auth bug.  Your fix worked for me and the SMTP server is allowing logins.

---

### Post by DantePasquale on 2012-04-30
Anything else to try???? I've tried the downgrade. I've also updated the smtp.conf file with a new sql-select statement per ispconfig forums. Nothing seems to help.

---

### Post by emunson on 2012-04-30
There is no reason to believe that cannonical/sasl project will fix this, the best suggestion out of the bug report is to convert to dovecot for authentication/encryption.

---

### Post by DantePasquale on 2012-05-01
I hear you ... that's why I really try to avoid any upgrades with Ubuntu in particular -- now I've got dozens of users wanting to kill me and vp's asking why we aren't running windows and I've got no answers for them at all.

Guess I'll try re-installing/rebuilding with 11.04 since that was working. 

I don't like to kvetch too much about Linux, but these upgrades are horrendous. They never work and I've been using many distros for over 12 years.

---

### Post by rabbadabb on 2012-05-04
Anyone tried to upgrade to 12.04? Does it magically fix all previous issues?

---

### Post by emunson on 2012-05-04
The bug is still open and 12.04 uses the same cyrus-sasl packages as 11.10 did so I am assuming that the bug is still present.  I will probably move to using dovecot this weekend if I have the chance.

---

### Post by emunson on 2012-05-04
I haven't ever had trouble with an upgrade hosing things before (beyond the crappy closed graphics drivers from nVidia and ATI), I have a machine that was initially installed with Feisty and is happily running Precise now.  But I do think that it is a little rediculous that we have a comfirmed bug open for 6 months with 0 response from the package maintainer...

---

### Post by rabbadabb on 2012-05-08
I upgraded, still the same issue. But with forcing the installation to fix as mentioned earlier in this tread it works.

---

### Post by AndreyMikhalevich on 2012-08-22
Had the same problem on 12.04. Thanks a lot

---

