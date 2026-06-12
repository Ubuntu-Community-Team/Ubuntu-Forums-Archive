---
title: "rkhunter warnings shows exim and openssl out of date and potential risk"
date: 2009-11-30
forum: Security
---

### Post by styxcoverbnd on 2009-11-30
I have two PCs running Hardy and I just ran rkhunter on both (I ran rkhunter --update then rkhunter --check --sk). Both have warnings stating: 

> 
Checking version of Exim MTA                    [ Warning ]
[20:14:43] Warning: Application 'exim', version '4.69', is out of date, and possibly a security risk.

Checking version of OpenSSL                     [ Warning ]
[20:14:43] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.

I did some checking and the latest exim version is 4.71 and the latest version of OpenSSL is 0.9.8i. I don't have any web servers installed and exim was installed with rkhunter and only listens to local ports. Are these warning anything to worry about? No new system updates and the rkhunter update said there were no new updates but I did notice that there were more checks run (especially when checking for backdoor ports) possibly broken .dat update from rkhunter? Anyone else have this issue?

---

### Post by styxcoverbnd on 2009-12-01
I did some more reading into this and looks like people running older versions of Fedora are running into this issue too. Looks like rkhunter recently released a new version (v1.3.6) and it is working correctly stating that these versions are out of date (because technically they are), but the security risk part might be slightly misleading.

I found this on [Mail-Archive](http://www.mail-archive.com/fedora-list@redhat.com/msg58839.html)

> Disable the application checks. I am going to likely push out a new rkhunter package that does this soon. 

The problem is that upstream pushes out a dat file with the versions of those packages that are up to date and proof against known security issues. Fedora often backports fixes for stable releases, so the version isn't very good as an indicator when you are safe or not. 

and also this from [Mail Archive](http://www.mail-archive.com/fedora-list@redhat.com/msg58858.html)

> The 'apps' test was a legacy from previous versions when RKH was
maintained by Michael Boelen. The test has been discussed, and we would
rather get rid of it. As mentioned it only checks a handful of apps, and
trying to maintain the version numbers is not really possible. Whilst
the app itself may change its version number, a distro such as
RHEL/Fedora etc may just patch their version and alter the patch level
number, not the actual version number. So the warnings may well be
false-positives.

The latest release of RKH (1.3.6 came out yesterday) caused the updated
app version file to be pushed out as well. Hence the sudden flurry of
warnings for all 1.3 versions of RKH.

---

### Post by AlanPorter on 2009-12-04
I would think that the default settings for a distro would not be for one package to complain about the other packages being out of date.

That is, either update the pacakges that rkhunter complains about, or change rkhunter so that it does not complain about the most up-to-date packages in the distro.

Every morning, I get an email that says this:
> Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
Warning: Application 'php', version '5.2.4', is out of date, and possibly a security risk.
Warning: Application 'sshd', version '4.7p1', is out of date, and possibly a security risk.


Is there a setting in the rkhunter.conf file where I can over-ride these warnings?

Alan

---

### Post by HermanAB on 2009-12-04
these rootkit hunter programs are a waste of time.  I have been using Unix systems since 1984 and have yet to encounter a rootkit.  So relax and enjoy your Ubuntu system.

---

### Post by jwilliams42 on 2009-12-22
Until rkhunter is updated to not do these checks, you can add application whitelists to your /etc/rkhunter.conf file. I was getting warned for the 3 packages below, and this is how I stopped the warning:

APP_WHITELIST="openssl gpg sshd"

You can also follow each package by :version if you want to only whitelist a specific version of the app.

---

### Post by trigity on 2009-12-22
Nicely put... :)

---

### Post by spiffymap on 2011-01-06
I tried this, I added the following line to /etc/rkhunter.conf:

APP_WHITELIST="exim openssl php sshd"

/var/log/rkhunter.log confirms that this is the config file in use, but I still get the following warnings when running:

arning: Application 'exim', version '4.69', is out of date, and possibly a security risk.
Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
Warning: Application 'php', version '5.2.4', is out of date, and possibly a security risk.
Warning: Application 'sshd', version '4.7p1', is out of date, and possibly a security risk.

It's as though it is ignoring the APP_WHITELIST setting. Or did I miss something?

---

