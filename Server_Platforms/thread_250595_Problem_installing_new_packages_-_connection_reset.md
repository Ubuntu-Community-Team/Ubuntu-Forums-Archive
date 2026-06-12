---
title: "Problem installing new packages - connection reset by peer"
date: 2006-09-04
forum: Server Platforms
---

### Post by JMitchell on 2006-09-04
I am trying to install [RT Request Tracker]("http://bestpractical.com/rt") on a new installation of Ubuntu Server.

I've been following the tutorial [here]("http://ubuntuforums.org/showthread.php?t=202397")

I'm having problems at the point of running the line:
sudo apt-get install request-tracker3.4 rt3.4-apache2 rt3.4-clients apache2-doc postfix postgresql postgresql-doc-7.4 lynx

Throughout the text I'm getting the error:
Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]

And at the end it says:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I've done sudo apt-get update (and upgrade) and tried with --fix-missing (That did something a little different in that it asked me about the setup of postfix)

I initially had the problem of it not finding the package request-tracker3.4 so I removed the gb from the URL [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) in sources.list - do I need to add multiverse? ](*,)

---

### Post by JMitchell on 2006-09-04
Is this the right place for this question or would it be better in the beginners forum (I'm kind of a beginner so...)

---

### Post by Jussi Kukkonen on 2006-09-04
You probably have a problem in your sources.list or the servers were down at the time your tried. Please post your */etc/apt/sources.list* and the output of *apt-get update*.

---

### Post by JMitchell on 2006-09-04
> **Jussi Kukkonen said:**
> You probably have a problem in your sources.list or the servers were down at the time your tried. Please post your */etc/apt/sources.list* and the output of *apt-get update*.
sources.list
```

# 
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#### I removed gb. from between http:// and archive below...
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

```
Part of the installation log:
```

Reading package lists...
Building dependency tree...
The following extra packages will be installed:
  apache apache-common libalgorithm-dependency-perl libapache-dbi-perl
  libapache-mod-perl libapache-request-perl libapache-session-perl
  libapache2-mod-perl2 libcache-cache-perl libcache-simple-timedexpiry-perl
  libclass-accessor-perl libclass-autouse-perl libclass-container-perl
  libclass-data-inheritable-perl libclass-inspector-perl
  libclass-returnvalue-perl libclone-perl libconfig-tiny-perl
  libconvert-binhex-perl libdbix-dbschema-perl libdbix-searchbuilder-perl
  libdevel-stacktrace-perl libdevel-symdump-perl libdigest-sha1-perl
  liberror-perl libexception-class-perl libextutils-autoinstall-perl
  libfcgi-perl libfile-find-rule-perl libfile-flat-perl libfile-ncopy-perl
  libfile-remove-perl libfile-slurp-perl libfont-afm-perl libfreezethaw-perl
  libhtml-format-perl libhtml-mason-perl libhtml-parser-perl
  libhtml-scrubber-perl libhtml-tagset-perl libhtml-tree-perl
  libio-stringy-perl libipc-sharelite-perl liblocale-maketext-fuzzy-perl
  liblocale-maketext-lexicon-perl liblog-dispatch-perl libmailtools-perl
  libmime-perl libmldbm-perl libmodule-versions-report-perl
  libnumber-compare-perl libparams-util-perl libparams-validate-perl
  libpath-class-perl libperl5.8 libpod-tests-perl libpq3 libprefork-perl
  libregexp-common-perl libterm-readkey-perl libtest-classapi-perl
  libtest-inline-perl libtext-autoformat-perl libtext-glob-perl
  libtext-quoted-perl libtext-reform-perl libtext-template-perl
  libtext-wikiformat-perl libtext-wrapper-perl libtime-modules-perl
  libtimedate-perl libtree-simple-perl liburi-perl libwant-perl libwww-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-rss-perl libxml-sax-perl libxml-simple-perl
  postgresql-7.4 postgresql-client postgresql-client-7.4
  postgresql-client-common postgresql-common rt3.4-apache ucf
Suggested packages:
  apache-doc apache-ssl apache-perl apache-dev libapache-mod-perl-doc
  libsort-versions-perl speedy-cgi-perl libhtml-mason-perl-doc
  libmail-audit-perl libio-socket-ssl-perl procmail postfix-mysql
  postfix-pgsql postfix-ldap postfix-pcre sasl2-bin doc-linux-html pgdocs
Recommended packages:
  libcompress-zlib-perl mail-reader resolvconf postgresql-plpython-7.4
  postgresql-plperl-7.4 postgresql-pltcl-7.4 debconf-utils
The following NEW packages will be installed
  apache apache-common apache2-doc libalgorithm-dependency-perl
  libapache-dbi-perl libapache-mod-perl libapache-request-perl
  libapache-session-perl libapache2-mod-perl2 libcache-cache-perl
  libcache-simple-timedexpiry-perl libclass-accessor-perl
  libclass-autouse-perl libclass-container-perl libclass-data-inheritable-perl
  libclass-inspector-perl libclass-returnvalue-perl libclone-perl
  libconfig-tiny-perl libconvert-binhex-perl libdbix-dbschema-perl
  libdbix-searchbuilder-perl libdevel-stacktrace-perl libdevel-symdump-perl
  libdigest-sha1-perl liberror-perl libexception-class-perl
  libextutils-autoinstall-perl libfcgi-perl libfile-find-rule-perl
  libfile-flat-perl libfile-ncopy-perl libfile-remove-perl libfile-slurp-perl
  libfont-afm-perl libfreezethaw-perl libhtml-format-perl libhtml-mason-perl
  libhtml-parser-perl libhtml-scrubber-perl libhtml-tagset-perl
  libhtml-tree-perl libio-stringy-perl libipc-sharelite-perl
  liblocale-maketext-fuzzy-perl liblocale-maketext-lexicon-perl
  liblog-dispatch-perl libmailtools-perl libmime-perl libmldbm-perl
  libmodule-versions-report-perl libnumber-compare-perl libparams-util-perl
  libparams-validate-perl libpath-class-perl libperl5.8 libpod-tests-perl
  libpq3 libprefork-perl libregexp-common-perl libterm-readkey-perl
  libtest-classapi-perl libtest-inline-perl libtext-autoformat-perl
  libtext-glob-perl libtext-quoted-perl libtext-reform-perl
  libtext-template-perl libtext-wikiformat-perl libtext-wrapper-perl
  libtime-modules-perl libtimedate-perl libtree-simple-perl liburi-perl
  libwant-perl libwww-perl libxml-libxml-common-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-rss-perl
  libxml-sax-perl libxml-simple-perl lynx postfix postgresql postgresql-7.4
  postgresql-client postgresql-client-7.4 postgresql-client-common
  postgresql-common postgresql-doc-7.4 request-tracker3.4 rt3.4-apache
  rt3.4-apache2 rt3.4-clients ucf
0 upgraded, 97 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.3MB/18.9MB of archives.
After unpacking 71.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main lynx 2.8.5-2ubuntu1 [1101kB]
Errhttp://gb.archive.ubuntu.com dapper/main lynx 2.8.5-2ubuntu1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libdigest-sha1-perl 2.10-1 [23.7kB]
Errhttp://gb.archive.ubuntu.com dapper/main libdigest-sha1-perl 2.10-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libclass-accessor-perl 0.22-1 [20.8kB]
Errhttp://gb.archive.ubuntu.com dapper/main libclass-accessor-perl 0.22-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libconvert-binhex-perl 1.119-2 [30.8kB]
Errhttp://gb.archive.ubuntu.com dapper/main libconvert-binhex-perl 1.119-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libio-stringy-perl 2.110-1 [88.6kB]
Errhttp://gb.archive.ubuntu.com dapper/main libio-stringy-perl 2.110-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libmailtools-perl 1.62-1 [82.5kB]
Errhttp://gb.archive.ubuntu.com dapper/main libmailtools-perl 1.62-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libmime-perl 5.419-1 [366kB]
Errhttp://gb.archive.ubuntu.com dapper/main libmime-perl 5.419-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libxml-libxml-common-perl 0.13-5 [14.0kB]
Errhttp://gb.archive.ubuntu.com dapper/main libxml-libxml-common-perl 0.13-5
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libxml-namespacesupport-perl 1.09-2 [15.2kB]
Errhttp://gb.archive.ubuntu.com dapper/main libxml-namespacesupport-perl 1.09-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libxml-sax-perl 0.12-5 [79.5kB]
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe apache-common 1.3.34-2 [837kB]
Errhttp://archive.ubuntu.com dapper/universe apache-common 1.3.34-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe apache 1.3.34-2 [385kB]
Errhttp://archive.ubuntu.com dapper/universe apache 1.3.34-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libparams-util-perl 0.10-1 [11.0kB]
Get: 14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libclass-inspector-perl 1.13-1 [17.1kB]
Errhttp://archive.ubuntu.com dapper/universe libclass-inspector-perl 1.13-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libconfig-tiny-perl 2.02-1 [10.8kB]
Errhttp://archive.ubuntu.com dapper/universe libconfig-tiny-perl 2.02-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtest-classapi-perl 1.02-1 [11.0kB]
Errhttp://archive.ubuntu.com dapper/universe libtest-classapi-perl 1.02-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libpath-class-perl 0.12-1 [30.2kB]
Errhttp://archive.ubuntu.com dapper/universe libpath-class-perl 0.12-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libalgorithm-dependency-perl 1.101-1 [37.1kB]
Errhttp://archive.ubuntu.com dapper/universe libalgorithm-dependency-perl 1.101-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libapache-mod-perl 1.29.0.4-2 [489kB]
Errhttp://archive.ubuntu.com dapper/universe libapache-mod-perl 1.29.0.4-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libapache-dbi-perl 0.94-2 [37.1kB]
Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libxml-libxml-perl 1.58-3 [273kB]
Errhttp://gb.archive.ubuntu.com dapper/main libxml-libxml-perl 1.58-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libxml-parser-perl 2.34-4 [292kB]
Errhttp://gb.archive.ubuntu.com dapper/main libxml-parser-perl 2.34-4
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.54 80]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libxml-simple-perl 2.14-3 [69.1kB]
Get: 24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libapache-request-perl 1.33-1 [81.8kB]
Errhttp://archive.ubuntu.com dapper/universe libapache-request-perl 1.33-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libapache-session-perl 1.80-2 [99.7kB]
Errhttp://archive.ubuntu.com dapper/universe libapache-session-perl 1.80-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe liberror-perl 0.15-8 [15.5kB]
Errhttp://archive.ubuntu.com dapper/universe liberror-perl 0.15-8
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libipc-sharelite-perl 0.09-3 [24.5kB]
Errhttp://archive.ubuntu.com dapper/universe libipc-sharelite-perl 0.09-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libcache-cache-perl 1.04-1 [81.8kB]
Errhttp://archive.ubuntu.com dapper/universe libcache-cache-perl 1.04-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libcache-simple-timedexpiry-perl 0.21-1 [5298B]
Errhttp://archive.ubuntu.com dapper/universe libcache-simple-timedexpiry-perl 0.21-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libextutils-autoinstall-perl 0.61-1 [25.0kB]
Errhttp://archive.ubuntu.com dapper/universe libextutils-autoinstall-perl 0.61-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libclass-autouse-perl 1.23-1 [24.1kB]
Errhttp://archive.ubuntu.com dapper/universe libclass-autouse-perl 1.23-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libparams-validate-perl 0.77-1 [59.1kB]
Errhttp://archive.ubuntu.com dapper/universe libparams-validate-perl 0.77-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libclass-container-perl 0.12-1 [28.5kB]
Get: 34 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libclass-data-inheritable-perl 0.04-1 [7250B]
Errhttp://archive.ubuntu.com dapper/universe libclass-data-inheritable-perl 0.04-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 35 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libdevel-stacktrace-perl 1.11-1 [12.5kB]
Errhttp://archive.ubuntu.com dapper/universe libdevel-stacktrace-perl 1.11-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 36 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libclass-returnvalue-perl 0.53-1 [9768B]
Errhttp://archive.ubuntu.com dapper/universe libclass-returnvalue-perl 0.53-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 37 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libclone-perl 0.16-1 [10.9kB]
Errhttp://archive.ubuntu.com dapper/universe libclone-perl 0.16-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 38 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfreezethaw-perl 0.43-2 [16.3kB]
Errhttp://archive.ubuntu.com dapper/universe libfreezethaw-perl 0.43-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 39 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libdbix-dbschema-perl 0.28-1 [40.7kB]
Errhttp://archive.ubuntu.com dapper/universe libdbix-dbschema-perl 0.28-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 40 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libwant-perl 0.09-1 [27.0kB]
Errhttp://archive.ubuntu.com dapper/universe libwant-perl 0.09-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 41 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libdbix-searchbuilder-perl 1.38-1 [101kB]
Errhttp://archive.ubuntu.com dapper/universe libdbix-searchbuilder-perl 1.38-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 42 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libexception-class-perl 1.21-1 [22.9kB]
Errhttp://archive.ubuntu.com dapper/universe libexception-class-perl 1.21-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 43 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfcgi-perl 0.67-2 [37.1kB]
Errhttp://archive.ubuntu.com dapper/universe libfcgi-perl 0.67-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 44 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-glob-perl 0.06-1 [7578B]
Get: 45 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libnumber-compare-perl 0.01-1 [5784B]
Errhttp://archive.ubuntu.com dapper/universe libnumber-compare-perl 0.01-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 46 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfile-find-rule-perl 0.28-1 [29.5kB]
Errhttp://archive.ubuntu.com dapper/universe libfile-find-rule-perl 0.28-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 47 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfile-ncopy-perl 0.34-1 [14.2kB]
Get: 48 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfile-remove-perl 0.31-1 [8968B]
Errhttp://archive.ubuntu.com dapper/universe libfile-remove-perl 0.31-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 49 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libprefork-perl 1.00-1 [11.9kB]
Errhttp://archive.ubuntu.com dapper/universe libprefork-perl 1.00-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 50 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfile-slurp-perl 9999.09-1 [14.8kB]
Get: 51 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfile-flat-perl 0.95-2 [19.8kB]
Errhttp://archive.ubuntu.com dapper/universe libfile-flat-perl 0.95-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 52 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libfont-afm-perl 1.19-1 [13.6kB]
Get: 53 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libhtml-format-perl 2.04-1 [37.9kB]
Errhttp://archive.ubuntu.com dapper/universe libhtml-format-perl 2.04-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 54 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libhtml-mason-perl 1:1.32-1 [361kB]
Errhttp://archive.ubuntu.com dapper/universe libhtml-mason-perl 1:1.32-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 55 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libhtml-scrubber-perl 0.08-2 [13.5kB]
Get: 56 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe liblocale-maketext-fuzzy-perl 0.02-2 [11.9kB]
Errhttp://archive.ubuntu.com dapper/universe liblocale-maketext-fuzzy-perl 0.02-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 57 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe liblocale-maketext-lexicon-perl 0.53-1 [41.0kB]
Errhttp://archive.ubuntu.com dapper/universe liblocale-maketext-lexicon-perl 0.53-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 58 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe liblog-dispatch-perl 2.11-1 [61.9kB]
Errhttp://archive.ubuntu.com dapper/universe liblog-dispatch-perl 2.11-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 59 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libmldbm-perl 2.01-1 [18.3kB]
Errhttp://archive.ubuntu.com dapper/universe libmldbm-perl 2.01-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 60 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libmodule-versions-report-perl 1.02-2 [8984B]
Errhttp://archive.ubuntu.com dapper/universe libmodule-versions-report-perl 1.02-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 61 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libpod-tests-perl 0.18-1 [16.6kB]
Get: 62 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libpq3 1:7.4.12-3 [184kB]
Errhttp://archive.ubuntu.com dapper/universe libpq3 1:7.4.12-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 63 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libregexp-common-perl 2.120-1 [177kB]
Errhttp://archive.ubuntu.com dapper/universe libregexp-common-perl 2.120-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 64 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libterm-readkey-perl 2.30-2 [32.1kB]
Errhttp://archive.ubuntu.com dapper/universe libterm-readkey-perl 2.30-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 65 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtest-inline-perl 2.103-1 [58.8kB]
Errhttp://archive.ubuntu.com dapper/universe libtest-inline-perl 2.103-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 66 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-reform-perl 1.11-3 [34.7kB]
Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 67 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-autoformat-perl 1.12-3 [29.0kB]
Errhttp://archive.ubuntu.com dapper/universe libtext-autoformat-perl 1.12-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 68 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-quoted-perl 1.8-2 [9316B]
Errhttp://archive.ubuntu.com dapper/universe libtext-quoted-perl 1.8-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 69 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-wikiformat-perl 0.76-1 [26.4kB]
Errhttp://archive.ubuntu.com dapper/universe libtext-wikiformat-perl 0.76-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 70 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-wrapper-perl 1.000-2 [7598B]
Errhttp://archive.ubuntu.com dapper/universe libtext-wrapper-perl 1.000-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 71 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtime-modules-perl 2003.1126-2 [35.1kB]
Errhttp://archive.ubuntu.com dapper/universe libtime-modules-perl 2003.1126-2
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 72 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtree-simple-perl 1.15-1 [39.7kB]
Errhttp://archive.ubuntu.com dapper/universe libtree-simple-perl 1.15-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 73 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libxml-rss-perl 1.05-1 [47.9kB]
Errhttp://archive.ubuntu.com dapper/universe libxml-rss-perl 1.05-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 74 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe postgresql-client-7.4 1:7.4.12-3 [942kB]
Errhttp://archive.ubuntu.com dapper/universe postgresql-client-7.4 1:7.4.12-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 75 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe postgresql-7.4 1:7.4.12-3 [3247kB]
Errhttp://archive.ubuntu.com dapper/universe postgresql-7.4 1:7.4.12-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 76 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe postgresql-client 7.5.16.1 [4036B]
Get: 77 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe postgresql 7.5.16.1 [6318B]
Errhttp://archive.ubuntu.com dapper/universe postgresql 7.5.16.1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Media Change: Please insert the disc labelled
 â€˜Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)â€™
in the drive â€˜/cdrom/â€™ and press enter
Get: 78 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe postgresql-doc-7.4 1:7.4.12-3 [1158kB]
Errhttp://archive.ubuntu.com dapper/universe postgresql-doc-7.4 1:7.4.12-3
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 79 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe rt3.4-clients 3.4.4-1 [111kB]
Errhttp://archive.ubuntu.com dapper/universe rt3.4-clients 3.4.4-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 80 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe rt3.4-apache 3.4.4-1 [85.1kB]
Errhttp://archive.ubuntu.com dapper/universe rt3.4-apache 3.4.4-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 81 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe rt3.4-apache2 3.4.4-1 [85.0kB]
Errhttp://archive.ubuntu.com dapper/universe rt3.4-apache2 3.4.4-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 82 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libtext-template-perl 1.44-1.1 [53.5kB]
Errhttp://archive.ubuntu.com dapper/universe libtext-template-perl 1.44-1.1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Get: 83 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe request-tracker3.4 3.4.4-1 [1180kB]
```

---

### Post by JMitchell on 2006-09-04
Could the problem be at my end in terms of the network? I'm getting frustrated now!

---

### Post by gsdefender on 2006-09-04
I would try enabling all the repositories (even the universe ones) and changing from

```

deb gb.archive.ubuntu.com ...
deb-src gb.archive.ubuntu.com ...

```

to

```

deb en.archive.ubuntu.com
deb-src en.archive.ubuntu.com ...

```

that is still in a place near you (== fast downloads), but should never be down (since it would probably be even the Italian mirror is :-D). After that apt-get update your sources, then install it again.

---

### Post by JMitchell on 2006-09-04
Thanks for your help gsdefender. It didn't work unfortunately. I'm giving up and installing the standard version of Ubuntu with a GUI and everything! See if that helps. I've half a mind to give Fedora Core 5 a spin (My only previous experience of Linux before this week is with FC3)

---

### Post by Jussi Kukkonen on 2006-09-04
> I'm giving up

Easy now... This is probably not a hard problem, however frustrating it may seem now. 

You might have a problem with your machine, but if you can ping other urls (say google.com), then I doubt it... Please test if you haven't already.

"104 reset by peer" does imply a network problem, as far as I can see... It's a linux error code, not a http error. Still, you could try changing all "http://"s into "ftp://"s.

---

### Post by jason sanche on 2006-09-10
I'm having a similar problem on a new install of unbuntu 6.06. Many package downloads end in failed: 104 connection reset by peer. Is there something I can do? I'm very new to linux so Im not sure how to edit the sources if thats the problem... thx ;)

---

