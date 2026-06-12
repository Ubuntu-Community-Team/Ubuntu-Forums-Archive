---
title: "Amavis"
date: 2014-06-05
forum: Server Platforms
---

### Post by ken32 on 2014-06-05
I'm running Ubuntu 12.04.4 LTS on a new server that I'm configuring to work in the same way as an older, production server.  After a lot of messing about I finally got the email system working; postfix, mysql, amavis, clamav, spamassassin, courier (and probably some other somponents that I've forgotten).

I then set about trying to install webmin and then things started to fall apart.  I did eventually get it installed, though it doesn't actually seem to work - but I don't care about that... I'll be happy never to see it again!

What has happened is that my email system is no longer working.  It would appear that amavis is not running and declines to start.  No apparent error messages, just nothing happens.

What I THINK may have happened is that when getting webmin installed it downgraded some packages but I'm really not sure where to go from here.

Looking at services I see amavis but also amavis.dpkg-new, while the old server only has the first entry...
```

# service --status-all
 [ - ]  amavis
 [ - ]  amavis.dpkg-new
 [ + ]  apache2
 [ + ]  apparmor
etc...
```

I tried to do a reinstall of amavisd-new and get errors about broken packages but don't know how to fix this...
```

# apt-get install --reinstall amavisd-new
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 amavisd-new : Depends: libconvert-uulib-perl (>= 1.0.8) but it is not going to be installed
               Depends: libunix-syslog-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I did a 'apt-get install -f' but it found nothing to do.

I tried installing using aptitude and found some errors...
```

> aptitude install amavisd-new


     Keep the following packages at their current version:
1)     amavisd-new [Not Installed]
2)     libconvert-uulib-perl [Not Installed]
3)     libunix-syslog-perl [Not Installed]

```

If I decline to accept the proposed solution (because I don't really understand it) then I get
```

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

      Remove the following packages:
1)      libarchive-extract-perl
2)      libcompress-raw-zlib-perl
3)      libperl5.18
4)      libtext-soundex-perl

      Install the following packages:
5)      libmysqlclient16 [5.1.73-0ubuntu0.10.04.1 (lucid-security, lucid-updates)]
6)      libplrpc-perl [0.2020-2 (lucid)]
7)      libssl0.9.8 [0.9.8k-7ubuntu8.15 (lucid-security, lucid-updates)]

      Downgrade the following packages:
8)      apt [0.8.16~exp12ubuntu10.16 (now) -> 0.7.25.3ubuntu9.13 (lucid-security)]
9)      libalgorithm-diff-xs-perl [0.04-3 (now) -> 0.04-1 (lucid)]
10)     libapparmor-perl [2.8.0-5+b1 (now) -> 2.5.1-0ubuntu0.10.04.4 (lucid-security, lucid-updates)]
11)     libapt-pkg-perl [0.1.29+b1 (now) -> 0.1.24 (lucid)]
12)     libauthen-pam-perl [0.16-3 (now) -> 0.16-2 (lucid)]
13)     libberkeleydb-perl [0.54-2 (now) -> 0.39-1ubuntu1 (lucid)]
14)     libcrypt-openssl-bignum-perl [0.04-4+b1 (now) -> 0.04-2build1 (lucid)]
15)     libcrypt-openssl-rsa-perl [0.28-2 (now) -> 0.25-1build2 (lucid)]
16)     libdbd-mysql-perl [4.027-1 (now) -> 4.012-1ubuntu1 (lucid)]
17)     libdbi-perl [1.631-3 (now) -> 1.609-1build1 (lucid)]
18)     libhtml-parser-perl [3.71-1+b1 (now) -> 3.64-1 (lucid)]
19)     libio-pty-perl [1:1.08-1+b3 (now) -> 1:1.07-2build1 (lucid)]
20)     liblist-moreutils-perl [0.33-2 (now) -> 0.25~02-1 (lucid)]
21)     libnet-dns-perl [0.68-1.2 (now) -> 0.65-1build1 (lucid)]
22)     libnet-ssleay-perl [1.63-1 (now) -> 1.35-2ubuntu1 (lucid)]
23)     libnetaddr-ip-perl [4.073+dfsg-1 (now) -> 4.024+dfsg-1build1 (lucid)]
24)     libsocket6-perl [0.25-1 (now) -> 0.23-1 (lucid)]
25)     libterm-readkey-perl [2.32-1 (now) -> 2.30-4build1 (lucid)]
26)     libtext-charwidth-perl [0.04-7+b2 (now) -> 0.04-6 (lucid)]
27)     libtext-iconv-perl [1.7-5+b1 (now) -> 1.7-2 (lucid)]
28)     perl [5.18.2-4 (now) -> 5.10.1-8ubuntu2.4 (lucid-security, lucid-updates)]
29)     perl-base [5.18.2-4 (now) -> 5.10.1-8ubuntu2.4 (lucid-security, lucid-updates)]
30)     perl-modules [5.18.2-4 (now) -> 5.10.1-8ubuntu2.4 (lucid-security, lucid-updates)]

      Leave the following dependencies unresolved:
31)     amavisd-new recommends libcompress-raw-zlib-perl (>= 2.020)
32)     perl-modules recommends libtext-soundex-perl


Accept this solution? [Y/n/q/?]

```

I also tried installing a missing package...
```

# apt-get install libconvert-uulib-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libconvert-uulib-perl : Depends: perlapi-5.10.0
E: Unable to correct problems, you have held broken packages.

```

So now it seems there's something else missing!

I'm getting the feeling that I'm digging myself deeper into a hole and it's time to stop digging and seek help from those more familiar with this.

I have made copies of all my config files that I created before I killed it but it would be nice to get back to a working system by removing rather than purging packages.

What do I do now?

I've just noticed that a number of packages are marked for deinstallation, including amavis.  What's going on here?
```

# dpkg --get-selections |grep deinstall
amavisd-new                                     deinstall
console-setup                                   deinstall
kbd                                             deinstall
keyboard-configuration                          deinstall
language-pack-en-base                           deinstall
language-pack-gnome-en-base                     deinstall
libsnmp-base                                    deinstall
libsnmp15                                       deinstall
locales                                         deinstall
razor                                           deinstall
snmpd                                           deinstall
tasksel                                         deinstall

```

---

