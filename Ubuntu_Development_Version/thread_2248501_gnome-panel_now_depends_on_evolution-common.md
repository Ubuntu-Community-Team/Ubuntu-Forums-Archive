---
title: "gnome-panel now depends on evolution-common"
date: 2014-10-15
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-10-15
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1381232](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1381232)

And I posted some info here:

[http://ubuntuforums.org/showthread.php?t=2248295&p=13143275#post13143275](http://ubuntuforums.org/showthread.php?t=2248295&p=13143275#post13143275)

---

### Post by kansasnoob on 2014-10-15
I'm going to see what blows up if I do this:

```
sudo apt-get install gnome-panel

sudo apt-get purge evolution evolution-common evolution-plugins libencode-locale-perl liberror-perl libevolution libfile-listing-perl libfont-afm-perl libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkspell3-3-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libio-html-perl liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl libnet-http-perl libnetaddr-ip-perl libpst4 libsys-hostname-long-perl libwww-perl libwww-robotrules-perl libytnef0 re2c sa-compile spamassassin spamc
```

That won't work:

```
The following packages will be REMOVED:
  evolution* evolution-common* evolution-plugins* gnome-applets* gnome-panel*
  gnome-session-flashback* libencode-locale-perl* liberror-perl* libevolution*
  libfile-listing-perl* libfont-afm-perl* libgtkhtml-4.0-0*
  libgtkhtml-4.0-common* libgtkhtml-editor-4.0-0* libgtkspell3-3-0*
  libhtml-form-perl* libhtml-format-perl* libhtml-parser-perl*
  libhtml-tagset-perl* libhtml-tree-perl* libhttp-cookies-perl*
  libhttp-daemon-perl* libhttp-date-perl* libhttp-message-perl*
  libhttp-negotiate-perl* libio-html-perl* liblwp-mediatypes-perl*
  liblwp-protocol-https-perl* libmail-spf-perl* libnet-http-perl*
  libnetaddr-ip-perl* libpst4* libsys-hostname-long-perl* libwww-perl*
  libwww-robotrules-perl* libytnef0* re2c* sa-compile* spamassassin* spamc*
0 upgraded, 0 newly installed, 40 to remove and 39 not upgraded.
After this operation, 38.3 MB disk space will be freed.
Do you want to continue? [Y/n] n

```

---

### Post by zika on 2014-10-15
When trying such stuff do not forget to try it first with -s (--dry-run) switch. It could be very helpfull and time saving. ;)
```
sudo apt-get install -s gnome-panel
sudo apt-get purge -s evolution evolution-common evolution-plugins libencode-locale-perl liberror-perl libevolution libfile-listing-perl libfont-afm-perl libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkspell3-3-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libio-html-perl liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl libnet-http-perl libnetaddr-ip-perl libpst4 libsys-hostname-long-perl libwww-perl libwww-robotrules-perl libytnef0 re2c sa-compile spamassassin spamc
```

---

### Post by kansasnoob on 2014-10-15
I got busy this AM, just now getting back to this and this looks better:

```
lance@lance-desktop:~$ sudo apt-get purge evolution evolution-plugins libencode-locale-perl liberror-perl libevolution libfile-listing-perl libfont-afm-perl libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkspell3-3-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libio-html-perl liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl libnet-http-perl libnetaddr-ip-perl libpst4 libsys-hostname-long-perl libwww-perl libwww-robotrules-perl libytnef0 re2c sa-compile spamassassin spamc -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution* evolution-plugins* libencode-locale-perl* liberror-perl*
  libevolution* libfile-listing-perl* libfont-afm-perl* libgtkhtml-4.0-0*
  libgtkhtml-4.0-common* libgtkhtml-editor-4.0-0* libgtkspell3-3-0*
  libhtml-form-perl* libhtml-format-perl* libhtml-parser-perl*
  libhtml-tagset-perl* libhtml-tree-perl* libhttp-cookies-perl*
  libhttp-daemon-perl* libhttp-date-perl* libhttp-message-perl*
  libhttp-negotiate-perl* libio-html-perl* liblwp-mediatypes-perl*
  liblwp-protocol-https-perl* libmail-spf-perl* libnet-http-perl*
  libnetaddr-ip-perl* libpst4* libsys-hostname-long-perl* libwww-perl*
  libwww-robotrules-perl* libytnef0* re2c* sa-compile* spamassassin* spamc*
0 upgraded, 0 newly installed, 36 to remove and 39 not upgraded.
Purg evolution-plugins [3.12.7-0ubuntu1]
Purg evolution [3.12.7-0ubuntu1]
Purg sa-compile [3.4.0-2ubuntu1]
Purg spamassassin [3.4.0-2ubuntu1]
Purg liblwp-protocol-https-perl [6.06-2] [libwww-perl:i386 ]
Purg libwww-perl [6.08-1]
Purg libhttp-negotiate-perl [6.00-2]
Purg libhttp-message-perl [6.06-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libencode-locale-perl [1.03-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libmail-spf-perl [2.9.0-3] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg liberror-perl [0.17-1.1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libevolution [3.12.7-0ubuntu1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libfile-listing-perl [6.04-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libhtml-format-perl [2.11-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libfont-afm-perl [1.20-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libgtkhtml-editor-4.0-0 [4.8.5-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libgtkhtml-4.0-0 [4.8.5-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libgtkhtml-4.0-common [4.8.5-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libgtkspell3-3-0 [3.0.6-1] [libhtml-form-perl:i386 libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libhtml-form-perl [6.03-1] [libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libhtml-tree-perl [5.03-1] [libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libhtml-parser-perl [3.71-1build2] [libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libhtml-tagset-perl [3.20-2] [libhttp-cookies-perl:i386 libhttp-daemon-perl:i386 ]
Purg libhttp-cookies-perl [6.00-2] [libhttp-daemon-perl:i386 ]
Purg libhttp-daemon-perl [6.01-1]
Purg libhttp-date-perl [6.02-1]
Purg libio-html-perl [1.001-1]
Purg liblwp-mediatypes-perl [6.02-1]
Purg libnet-http-perl [6.07-1]
Purg libnetaddr-ip-perl [4.075+dfsg-1build1]
Purg libpst4 [0.6.59-1build1]
Purg libsys-hostname-long-perl [1.4-3]
Purg libwww-robotrules-perl [6.01-1]
Purg libytnef0 [1.5-6]
Purg re2c [0.13.5-1build2]
Purg spamc [3.4.0-2ubuntu1]

```

I just dropped 'evolution-common' from the packages to be purged - should have thought of that earlier.

---

