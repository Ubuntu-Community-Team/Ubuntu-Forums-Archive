---
title: "Dovecot breaks on upgrade to 14.04LTS. Must install previous version of dovecot."
date: 2016-02-03
forum: Server Platforms
---

### Post by bsgcic on 2016-02-03
--- Addendum after having posted this earlier.  It appears that the issue still occurs though it seems less often.  Maybe it is a problem with Ubuntu itself???? ---

Hi, I have spent the last 3 days trying to get the new version of dovecot to actually work correctly in the upgraded 14.04.3LTS version and it absolutely does not.  The authentication via pam and userdb are unstable and thus broken.  It appears to be an inherent problem in that new version of dovecot 2.2.9.  When clients (e.g., Thunderbird whether on another ubuntu 14.04.3LTS machine or a Win7 machine) try to login via pop3s, the login is sporadic.  Sometimes it works, often it does not even with the identical, correct password.  Sometimes, by logging into the server as the user and logging out (via ssh), then sometimes the pop3s login for that user will temporarily work.  And then later of course it does not.  This was obviously NOT tested prior to release.

Further, moving the start-up from /etc/init.d/ to /etc/init/ was not desirable.  Thus, I removed the /etc/init/ one and restored the previous /etc/init.d/ one so that I can easily do service dovecot start, service dovecot stop, etc.

After wasting an absurd amount of time trying to get the new version to work, finally, I downloaded the closest old stable version of dovecot (dovecot-2.0.21) to the one that was in 12.04LTS (which I think was dovecot-2.0.19), unpacked it in /usr/local/src/dovecot and then performed configured and installed it within the /usr/local/ direcory.  THAT WORKED!!!  Pop3s logins now FINALLY work again!!!  I would imagine that for most users like myself, we really don't want to tinker, play, or learn the intricacies of a mail delivery program like dovecot and just want the thing to work out of the box.

For those for whom it may be of help, these were the steps taken:

0. Did su (to be root)
0.5. Backup (just copy) the /etc/dovecot directory that you used in 12.04LTS.
1. Download: [http://dovecot.org/releases/2.0/dovecot-2.0.21.tar.gz](http://dovecot.org/releases/2.0/dovecot-2.0.21.tar.gz) and unpack it in /usr/local/src/dovecot/  (mkdir dovecot of course)
2. Make sure the pam library is installed: apt-get install libpam0g-dev
3. I ran the ./configure step as follows:
./configure --with-pam --with-shadow --with-ssl=openssl --with-ssldir=/etc/ssl --with-storages=maildir
4. make
5. make install
6. Copy in my /etc/dovecot/ configuration files that I had backed up to the new /usr/local/etc/dovecot/ directory.  I was actually able to use the configuration files that I had converted to 14.04LTS without any issue.  I did go through the configuration files and I think might have tinkered with some; but I the 14.04LTS versions should work per your 12.04LTS customizations that you bring to them.
7. Modify /etc/init.d/dovecot by changing:
DAEMON=/usr/sbin/dovecot
back to:
DAEMON=/usr/local/sbin/dovecot
8. If you have not already done so, then if you have newly restored /etc/init.d/dovecot back to the /etc/init.d/ directory, then you need to do: update-rc.d -f dovecot defaults
9. service dovecot start

The pop3s will now work as before THANK GOD!

---

