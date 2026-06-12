---
title: "PHP5 only from source?"
date: 2004-12-13
forum: Repositories &amp; Backports
---

### Post by Alessio on 2004-12-13
I need PHP5, I have installed apache2 and mysql from apt, but in apt there is only php4. A lot of my code are write for php5, how can i do??
I install php5 only from source? How?

---

### Post by p!=f on 2004-12-13
[QUOTE=Alessio]I need PHP5, I have installed apache2 and mysql from apt, but in apt there is only php4. A lot of my code are write for php5, how can i do??
I install php5 only from source? How?[/QUOTE]
Add this to your sources.list:
```

#deb http://packages.dotdeb.org ./
deb-src http://sources.dotdeb.org ./

```
First line is commented because precompiled packages are for Debian Woody only (feel free to give it a try) so rebuilding from PHP5 source .deb is recommended.
Hope it helps.

---

### Post by Alessio on 2004-12-13
[QUOTE=p!=f]
so rebuilding from PHP5 source .deb is recommended.
[/QUOTE]
how do it? sorry for my newbie about .deb file

---

### Post by p!=f on 2004-12-13
[QUOTE=Alessio]how do it? sorry for my newbie about .deb file[/QUOTE]
No problem, let's get straight on :)

1) :Optional: Create and enter some directory for managing sources so you don't have it all over the profile :)
```

mkdir ~/sources

```
2) Install required packages
```

sudo apt-get install dpkg-dev build-essential fakeroot

```
*fakeroot is optional*
3) 
```

cd ~/sources
sudo apt-get source php5

```
This will download the orig.tar.gz, diff.gz and dsc source files for your package, and unpack and patch the source code in a new source directory.
4) Check the build-depends list in the dsc file, and make sure you have all of those packages installed.
5) 
```

cd php5
*as non-root (use sudo instead of fakeroot if you want to)*
fakeroot debian/rules binary

```
The result(s) should be installable PHP5 package(s).

---

### Post by Alessio on 2004-12-13
Thank you!
But Warty remain stable? Or can I have any problem?

---

### Post by p!=f on 2004-12-13
[QUOTE=Alessio]Thank you!
But Warty remain stable? Or can I have any problem?[/QUOTE]
I don't see any problem. As soon as you rebuild PHP5 against your current setup, the resulted package should fit into your system. You may need some additional -dev packages, though. Feel free to post here if you experience any problems and let us know if it works. :)

---

### Post by Alessio on 2004-12-13
[QUOTE=p!=f]I don't see any problem. As soon as you rebuild PHP5 against your current setup, the resulted package should fit into your system. You may need some additional -dev packages, though. Feel free to post here if you experience any problems and let us know if it works. :)[/QUOTE]
 alessio@Ubuntu:~/sources/php5-5.0.2 $ sudo debian/rules binary
dh_testdir
for patch in debian/patches/*.patch; do \
        echo '->'`basename $patch`:; \
        if ! patch -p1 --ignore-whitespace --dry-run < $patch; \
        then \
                exit 1; \
        fi; \
        patch -p1 --ignore-whitespace < $patch; \
done
->006-debian_quirks.patch:
patching file configure.in
patching file php.ini-dist
Hunk #1 succeeded at 447 (offset 12 lines).
patching file scripts/Makefile.frag
patching file scripts/php-config.in
patching file scripts/phpize.in
patching file configure.in
patching file php.ini-dist
Hunk #1 succeeded at 447 (offset 12 lines).
patching file scripts/Makefile.frag
patching file scripts/php-config.in
patching file scripts/phpize.in
perl -i -pe 's/EXTRA_VERSION=""/EXTRA_VERSION="-1.dotdeb.5"/' configure.in
autoconf
make: autoconf: Command not found
make: *** [patch-stamp] Error 127

I have controlled anything, what's wrong?

---

### Post by Alessio on 2004-12-13
> **Alessio]alessio@Ubuntu:~/sources/php5-5.0.2 $ sudo debian/rules binary
dh_testdir
for patch in debian/patches/*.patch said:**
>  Error 127

I have controlled anything, what's wrong?
 I have installed autoconf but during the compile...

Configuring SAPI modules
checking for AOLserver support... no
checking for Apache 1.x module support via DSO through APXS...

Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of /usr/bin/apxs follows
../configure: line 4696: /usr/bin/apxs: No such file or directory
configure: error: Aborting
make: *** [configure-apache-stamp] Error 1


Apache 1.x module?? I use Apache2 :(

---

### Post by p!=f on 2004-12-13
> **Alessio]alessio@Ubuntu:~/sources/php5-5.0.2 $ sudo debian/rules binary
dh_testdir
for patch in debian/patches/*.patch said:**
>  Error 127

I have controlled anything, what's wrong?
You're missing autoconf
```

sudo apt-get install autoconf automake

```

---

### Post by p!=f on 2004-12-13
Could you post that *rules* file here?

---

### Post by Alessio on 2004-12-13
```

#!/usr/bin/make -f
# Sample debian/rules that uses debhelper.
# GNU copyright 1997 by Joey Hess.
#
# This version is for a hypothetical package that builds an
# architecture-dependant package, as well as an architecture-independent
# package.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

# This is the debhelper compatibility version to use.
export DH_COMPAT=3

# This has to be exported to make some magic below work.
export DH_OPTIONS

DEB_HOST_GNU_TYPE       ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
DEB_BUILD_GNU_TYPE      ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)

PHP5_SOURCE_VERSION   = $(shell dpkg-parsechangelog | grep ^Version | sed "s/Ver sion: //")
PHP5_UPSTREAM_VERSION = $(shell echo $(PHP5_SOURCE_VERSION) | sed -e "s/-.*//" - e "s/.*://")
PHP5_DEBIAN_REVISION  = $(shell echo $(PHP5_SOURCE_VERSION) | sed "s/.*-//")

CFLAGS = -O2 -gstabs -Wall -fsigned-char

# Enable IEEE-conformant floating point math on alphas (not the default)
ifeq (alpha-linux,$(DEB_HOST_GNU_TYPE))
  CFLAGS += -mieee
endif

COMMON_CONFIG=  --enable-memory-limit \
                --disable-debug \
                --with-layout=GNU \
                --disable-pear \
                --enable-calendar \
                --enable-sysvsem \
                        --enable-sysvshm \
                        --enable-sysvmsg \
                --enable-track-vars \
                --enable-trans-sid \
                --enable-bcmath \
                --with-bz2 \
                --enable-ctype \
                --with-db2 \
                --enable-dbx \
                --with-iconv \
                --enable-exif \
                --enable-filepro \
                --enable-ftp \
                --enable-dbase \
                --with-gettext \
                --with-mime-magic \
                --enable-mbstring \
                --with-pcre-regex \
                --enable-shmop \
                --enable-soap \
                --enable-sockets \
                --enable-simplexml \
                        --with-libxml-dir=/usr \
                --with-dom=/usr \
                --with-xsl=/usr \
                --with-sqlite \
                        --enable-sqlite-utf8 \
                --enable-tokenizer \
                --enable-yp \
                --with-zlib \
                        --with-zlib-dir=/usr \
                --with-kerberos=/usr \
                --with-openssl=/usr \
                --with-exec-dir=/usr/lib/php5/libexec

apachever=$(shell dpkg -s apache-dev | grep ^Version | cut -d\  -f2 | cut -d- -f 1)
php5ver=$(shell head -1 debian/changelog | cut -d\  -f 2 | sed 's/[()]//g')
phpapiver=$(shell grep '\#define PHP_API_VERSION ' ./main/php.h|sed 's/\#define PHP_API_VERSION //')

patch: patch-stamp
patch-stamp:
        dh_testdir
        for patch in debian/patches/*.patch; do \
                echo '->'`basename $$patch`:; \
                if ! patch -p1 --ignore-whitespace --dry-run < $$patch; \
                then \
                        exit 1; \
                fi; \
                patch -p1 --ignore-whitespace < $$patch; \
        done
        perl -i -pe 's/EXTRA_VERSION=""/EXTRA_VERSION="-$(PHP5_DEBIAN_REVISION)" /' configure.in
#       rm -f aclocal.m4
#       ./buildconf --force
        autoconf
        touch patch-stamp

unpatch:
        dh_testdir
        perl -i -pe 's/EXTRA_VERSION="-$(PHP5_DEBIAN_REVISION)"/EXTRA_VERSION="" /' configure.in
        if [ -f patch-stamp ]; then \
                for patch in `ls debian/patches/*.patch | sort -r`; do \
                        patch -p1 -R --ignore-whitespace < $$patch; \
                done; \
        fi
#       rm -f aclocal.m4
#       ./buildconf --force
        autoconf
        rm -f patch-stamp

build: build-apache-stamp build-cgi-stamp build-cli-stamp
build-apache-stamp: configure-apache-stamp
        dh_testdir

        cd apache-build && $(MAKE)

        touch build-apache-stamp

build-cgi-stamp: configure-cgi-stamp
        dh_testdir

        cd cgi-build && mkdir sapi/cgi/libfcgi/ && $(MAKE)

        touch build-cgi-stamp

build-cli-stamp: configure-cli-stamp
        dh_testdir

        cd cli-build && $(MAKE)

        touch build-cli-stamp

configure: configure-apache-stamp configure-cgi-stamp configure-cli-stamp
configure-apache-stamp: patch-stamp
        dh_testdir
        if [ -d apache-build ]; then rm -rf apache-build; fi
        -mkdir apache-build
        cd apache-build && \
        CFLAGS="$(CFLAGS)" ../configure \
                --disable-cli \
                --disable-cgi \
                --with-apxs=/usr/bin/apxs \
                --prefix=/usr \
                --disable-debug \
                --with-config-file-path=/etc/php5/apache --disable-rpath \
                --with-regex=php \
                $(COMMON_CONFIG) --disable-static \
                --without-pear \
                --with-curl=shared,/usr \
                --with-gd=shared \
                        --with-jpeg-dir=shared,/usr \
                        --with-xpm-dir=shared,/usr/X11R6 \
                        --with-png-dir=shared,/usr \
                        --with-freetype-dir=shared,/usr  \
                        --enable-gd-native-ttf \
                        --enable-gd-jis-conv \
                --with-mcrypt=shared,/usr \
                --with-ming=shared,/usr \
                --with-imap=shared,/usr \
                        --with-imap-ssl \
                --with-ldap=shared,/usr \
                --with-mhash=shared,/usr \
                --with-mm \
                --with-mysql=shared,/usr \
                        --with-mysql-sock=/var/run/mysqld/mysqld.sock \
                --with-mysqli=shared,/usr/bin/mysql_config \
                --with-pgsql=shared,/usr \
                --with-unixODBC=shared,/usr \
                --with-tidy=shared \
                --with-snmp=shared \
                        --enable-ucd-snmp-hack \
                --with-sybase-ct=shared,/usr \
                --with-ttf=shared,/usr
        cd apache-build && \
        cp ../Zend/zend_ini_scanner.c ../Zend/zend_language_scanner.c \
           ../Zend/zend_ini_parser.h ../Zend/zend_language_parser.h \
           ../Zend/zend_ini_parser.c ../Zend/zend_language_parser.c \
           Zend/

        touch configure-apache-stamp

configure-cgi-stamp: patch-stamp
        dh_testdir
        if [ -d cgi-build ]; then rm -rf cgi-build; fi
        -mkdir cgi-build
        cd cgi-build && \
        CFLAGS="$(CFLAGS) -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64" ../confi gure \
                --disable-cli \
                --prefix=/usr \
                --with-regex=php \
                --enable-fastcgi \
                --enable-force-cgi-redirect \
                --with-config-file-path=/etc/php5/cgi --disable-rpath \
                $(COMMON_CONFIG) --disable-static \
                --without-pear \
                --without-mm \
                --enable-pcntl \
                --without-mysql --without-sybase-ct
        cd cgi-build && \
        cp ../Zend/zend_ini_scanner.c ../Zend/zend_language_scanner.c \
           ../Zend/zend_ini_parser.h ../Zend/zend_language_parser.h \
           ../Zend/zend_ini_parser.c ../Zend/zend_language_parser.c \
           Zend/
        touch configure-cgi-stamp

configure-cli-stamp: patch-stamp
        dh_testdir
        if [ -d cli-build ]; then rm -rf cli-build; fi
        -mkdir cli-build
        cd cli-build && \
        CFLAGS="$(CFLAGS) -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64" ../confi gure \
                --disable-cgi \
                --prefix=/usr \
                --with-regex=php \
                --with-config-file-path=/etc/php5/cli --disable-rpath \
                $(COMMON_CONFIG) --disable-static \
                --with-pear=/usr/share/php \
                --without-mm \
                --with-ncurses \
                --enable-pcntl \
                --without-mysql --without-sybase-ct
        cd cli-build && \
        cp ../Zend/zend_ini_scanner.c ../Zend/zend_language_scanner.c \
           ../Zend/zend_ini_parser.h ../Zend/zend_language_parser.h \
           ../Zend/zend_ini_parser.c ../Zend/zend_language_parser.c \
           Zend/
        touch configure-cli-stamp

clean: unpatch
        dh_testdir
        dh_testroot
        rm -f configure-apache-stamp build-apache-stamp
        rm -f configure-cgi-stamp build-cgi-stamp
        rm -f configure-cli-stamp build-cli-stamp
        rm -f install-stamp

        rm -rf apache-build
        rm -rf cgi-build
        rm -rf cli-build

        dh_clean
        cat debian/modulelist | while read package extname dsoname; do \
                rm -f debian/php5-$$package.postinst \
                   debian/php5-$$package.prerm \
                   debian/php5-$$package.config \
                   debian/php5-$$package.templates; \
        done

install: DH_OPTIONS=
install: build
        dh_testdir
        dh_testroot
        dh_clean -k
        dh_installdirs

        # install apache DSO module
        cp apache-build/.libs/libphp5.so debian/php5/`apxs -q LIBEXECDIR`
        cp debian/500mod_php5.info debian/php5/`apxs -q LIBEXECDIR`
        # sanitize php.ini file
        cat php.ini-dist | tr "\t" " " > debian/php5/usr/share/doc/php5/examples /php.ini
        cat php.ini-dist | tr "\t" " " > debian/php5-cgi/usr/share/doc/php5-cgi/ examples/php.ini
        cat php.ini-dist | tr "\t" " " > debian/php5-cli/usr/share/doc/php5-cli/ examples/php.ini

        # install the apache modules' files
        cd apache-build && make install-headers install-build install-modules in stall-programs INSTALL_ROOT=$(CURDIR)/debian/php5
        # install PEAR
        cd cli-build && make install-pear PHP_PEAR_PHP_BIN=php5 PHP_PEAR_INSTALL _DIR=/usr/share/php PHP_PEAR_SYSCONF_DIR=/etc/pear INSTALL_ROOT=$(CURDIR)/debian /php5-pear

        ext=`./debian/php5/usr/bin/php-config --extension-dir`;\
        cat debian/modulelist | while read package extname dsoname; do \
                if [ -z "$$dsoname" ]; then dsoname=$$package; fi; \
                mkdir -p debian/php5-$$package$${ext}; \
                install -s -m 644 -o root -g root \
                        debian/php5/$${ext}/$$dsoname.so \
                        debian/php5-$$package$${ext}/$$dsoname.so; \
                rm debian/php5/$${ext}/$$dsoname.so; \
                mkdir -p debian/php5-$$package/usr/share/lintian/overrides; \
                echo "php5-$$package: no-shlibs-control-file $$ext/$$dsoname.so"  > debian/php5-$$package/usr/share/lintian/overrides/php5-$$package; \
        done

        # install CGI
        cp cgi-build/sapi/cgi/php debian/php5-cgi/usr/lib/cgi-bin/php5

        # install CLI
        cp cli-build/sapi/cli/php debian/php5-cli/usr/bin/php5

        # move and install -dev files
        dh_movefiles --sourcedir=debian/php5
        install -m 755 -o root -g root ext/ext_skel debian/php5-dev/usr/bin/ext_ skel

        touch install-stamp

# Build architecture-independent files here.
# Pass -i to all debhelper commands in this target to reduce clutter.
binary-indep: DH_OPTIONS=-i
binary-indep: build install
        # Need this version of debhelper for DH_OPTIONS to work.
        dh_testdir
        dh_testroot
        dh_installdebconf
        dh_installdocs
        dh_installexamples

        cp debian/php5-pear/usr/share/doc/php5-pear/* \
                debian/php5/usr/share/doc/php5/PEAR/

#       dh_installmenu
#       dh_installemacsen
#       dh_installpam
#       dh_installinit
#       dh_installcron
#       dh_installmanpages
        dh_installinfo
#       dh_undocumented
        dh_installchangelogs  -i
        dh_link
        dh_compress
        dh_fixperms
#       # You may want to make some executables suid here.
#       dh_suidregister
        dh_installdeb
#       dh_perl
        dh_gencontrol
        dh_md5sums
        dh_builddeb

# Build architecture-dependent files here.
# Pass -a to all debhelper commands in this target to reduce clutter.
#binary-arch: DH_OPTIONS=-a
binary-arch: build install
        # Need this version of debhelper for DH_OPTIONS to work.
        dh_testdir
        dh_testroot
        cat debian/modulelist | while read package extname dsoname; do \
                if [ -z "$$dsoname" ]; then dsoname=$$package; fi; \
                sed -e"s/@extname@/$$extname/g; s/@dsoname@/$$dsoname/g" \
                  < debian/php5-module.postinst > debian/php5-$$package.postinst ; \
                sed -e"s/@extname@/$$extname/g; s/@dsoname@/$$dsoname/g" \
                  < debian/php5-module.prerm > debian/php5-$$package.prerm; \
                sed -e"s/@extname@/$$extname/g; s/@dsoname@/$$dsoname/g" \
                  < debian/php5-module.config > debian/php5-$$package.config; \
                cp debian/php5-module.templates debian/php5-$$package.templates;  \
        done
        dh_installdebconf
        dh_installdocs -a

        cat debian/modulelist | while read package extname dsoname; do \
                rm -rf debian/php5-$$package/usr/share/doc/php5-$$package; \
                ln -s php5 debian/php5-$$package/usr/share/doc/php5-$$package; \
        done

#       dh_installexamples
#       dh_installmenu
#       dh_installpam
#       dh_installmime
#       dh_installinit
#       dh_installcron
#       dh_installmanpages
#       dh_installinfo
#       dh_undocumented
        dh_installchangelogs
        dh_strip -a
        dh_link -a
        dh_compress -a -Xphp.ini
        dh_fixperms -a
        dh_installdeb -a
#       dh_makeshlibs
#       dh_perl
        LD_LIBRARY_PATH=$(CURDIR)/debian/php5/usr/lib/apache/1.3:$(LD_LIBRARY_PA TH) dh_shlibdeps -a
        echo "apache:Depends=apache-common (>= $(apachever))" >> debian/php5.sub stvars
        echo "php:Provides=phpapi-$(phpapiver)" >> debian/php5.substvars

        echo "php:Provides=phpapi-$(phpapiver)" >> debian/php5-cgi.substvars

        echo "php:Provides=phpapi-$(phpapiver)" >> debian/php5-cli.substvars

        cat debian/modulelist | while read package extname dsoname; do \
                echo "php:Depends=phpapi-$(phpapiver)" >> debian/php5-$$package. substvars; \
        done

        dh_gencontrol -a
        dh_md5sums -a
        dh_builddeb -a

binary: binary-arch binary-indep
.PHONY: build clean binary-indep binary-arch binary install configure

```

---

### Post by Alessio on 2004-12-13
Where is the problem?

---

### Post by Alessio on 2004-12-13
[QUOTE=Alessio]Where is the problem?[/QUOTE]

 :(

---

### Post by p!=f on 2004-12-13
UPDATE: Unable to compile it for parse errors. Will take a closer look at it yesterday. 
UPDATE2: I got rid of parse errors by removing --with-unixODBC=shared,/usr \ from the rules file. Still, the process ends with an error when building the packages so at least good to know it compiles fine. I hope I'll make final touches this evening.

[QUOTE=Alessio]:([/QUOTE]

It takes me some time to answer...

Some notes first:
I'm running Hoary so I can't say if it works on Warty as well.
You will compile PHP5 with plenty of options so you will need plenty of packages. :) The rules file is aimed for Apache1 users so if you don't need some options find the appropriate line in the file and remove it or tweak it to fit your needs.
This setup is quick and dirty (I didn't have enough time to dive into it :)). I suppose you just want to try it. In that case it should be sufficient as a testing webserver, though.

Let's start:
```

sudo gedit debian/rules

```
* replace all apxs with apxs2
* find the lines --with-db2 \ and --with-ming=shared,/usr \ and remove them

Install the following packages...
```

sudo apt-get install lib{tidy,mysqlclient14,curl3,mcrypt,mhash,mm,snmp5,c-client,xslt}-dev {apache2-prefork,freetds}-dev bison

```
You'll be prompted to install additional packages.
When you install libc-client-dev select default choices when prompted unless you know you need to change it.

Build PHP5.
If it still ends with an error, post it here. You will probably need other -dev packages.

---

### Post by michaela on 2006-07-07
](*,) 

I also am having problems compiling PHP5. I finally got ./configure to work but I am failing the make with /usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c. I thought I got all of the source that I needed but I guess not. What am I missing?

I am new to Ubuntu and Linux so this has been a real eye-opener! LOL I am learning Linux the hard way!

All help is appreciated. I'd copy and paste the errors but I cannot get VMWare Tools to work. It wants the C header files for the kernel. Do I have to download the whole ubuntu kernel source?

Thanks.

Mike

---

### Post by skirkpatrick on 2006-07-07
What version of Ubuntu are you using?  I know that PHP 5 is in the repositories for Dapper and Breezy.

---

### Post by michaela on 2006-07-07
Ubuntu 6.06. I downloaded the sources from various locations so they may be setup for Ubuntu. 

I have config.log. Does make also create a log file so I can copy the failing lines from it?

Mike

---

### Post by skirkpatrick on 2006-07-07
Sometimes.  Wouldn't it be easier to use Synaptic or apt-get to install PHP 5?

---

### Post by michaela on 2006-07-10
I may have. I have been installing so many things to get the compile to work that I have lost track of what I've done! When ever I could use apt-get, I have done so. 

But I still have the sapi problem as detailed above. I am hoping that is the last problem that I will have so I can get this php compile done.

What do I need to do to solve the problem?

Mike

---

### Post by skirkpatrick on 2006-07-10
You should be able to have make redirect its output to a file.
**make *any_parameters_needed* > log.txt**

---

### Post by michaela on 2006-07-10
Sure, easy for you to say!! LOL DUH! The obvious. It actually took 2> error.txt but you showed my the light!

Here is my error:

In file included from /usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:26:
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:29: error: syntax error before 'php5_module'
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:29: warning: data definition has no type or storage class
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:38: error: syntax error before 'apr_bucket_brigade'
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:38: warning: no semicolon at end of struct or union
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:47: error: syntax error before '}' token
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:47: warning: data definition has no type or storage class
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:49: error: syntax error before '*' token
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:50: error: syntax error before '*' token
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:54: error: syntax error before '*' token
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:28: error: syntax error before 'module'
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:28: error: conflicting types for 'php5_module'
/usr/src/php-5.1.4/sapi/apache2handler/php_apache.h:29: error: previous declaration of 'php5_module' was here
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:29: error: 'STANDARD20_MODULE_STUFF' undeclared here (not in a function)
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:30: warning: initialization makes integer from pointer without a cast
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:31: warning: initialization makes integer from pointer without a cast
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:34: warning: initialization from incompatible pointer type
/usr/src/php-5.1.4/sapi/apache2handler/mod_php5.c:36: warning: initialization makes integer from pointer without a cast
make: *** [sapi/apache2handler/mod_php5.lo] Error 1

How can I fix that so it compiles?

Thanks.

Mike

---

### Post by skirkpatrick on 2006-07-11
You're going to have to know enough about C programming to fix it.  Did you DL the latest stable release?

---

### Post by michaela on 2006-07-11
Yes. 5.1.4. However, I am not a great C programmer. Why are there errors? Seems like something else must be wrong. 

Please enlighten me.

Thanks.

Mike

---

### Post by skirkpatrick on 2006-07-13
Yes, there shouldn't be errors in the stable release.  I'm not sure what is wrong.  Is there a feature you need that isn't in the repository version?

---

### Post by michaela on 2006-07-13
I have been adding and adding stuff with apt-get. My problem is that I do not know what feature I need to add to resolve this. Here is how I am configuring it.


./configure --with-pdo-sqlite --enable-module=so --with-xsl --with-curl --with-bz2 --with-pdo-mysql --with-imap --with-imap-ssl --with-inifile --with-flatfile --with-xpm-dir --with-openssl --with-jpeg-dir --with-png-dir --disable-cgi --with-config-file-path=/etc/php5/cli --host=i686-pc-linux-gnu --target=i686-pc-linux-gnu --enable-simplexml --with-zlib --enable-bcmath --enable-calendar --enable-dba --enable-dbase --with-libxml-dir=/usr/lib --enable-exif --enable-filepro --enable-ftp --with-openssl-dir --with-gd --with-gettext --with-ldap --enable-mbstring --with-mcrypt --with-mhash --with-mime-magic --with-mssql --with-mysql --with-mysqli --with-ncurses --enable-pcntl --with-pdo-dblib --enable-shmop --enable-soap --enable-sockets --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-wddx --with-xmlrpc --with-apxs2 --with-gnu-ld --with-regex=php --with-pic --with-pear --enable-ctype --with-dom --with-sqlite --enable-sqlite-utf8 --with-pcre-regex --enable-pdo --enable-yp --enable-tokenizer --with-kerberos --with-iconv --enable-dbx --enable-track-vars --enable-trans-sid --with-layout=GNU


As always help is GREATLY appreciated as I need to get this completed for a project and have no idea what to do next. The whole purpose of compiling PHP was to get MS SQL support.

Thanks.

Mike

---

### Post by skirkpatrick on 2006-07-14
Okay, that explains why you have to compile it.

Your configure options shouldn't have anything to do with the compile errors you are seeing.  My best suggestion is to ask on the PHP forums where you should be able to get much better help.

---

### Post by Aleonushka4677 on 2007-05-15
> **Alessio said:**
> I need PHP5, I have installed apache2 and mysql from apt, but in apt there is only php4. A lot of my code are write for php5, how can i do??
I install php5 only from source? How?


[bread mapquest Yahoo mapquest Ebay](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

### Post by technobabe on 2012-07-30
I just fixed this problem! This problem is caused by having the wrong  version of "apxs" installed, which the PHP build process uses. If you  are trying to build PHP to work with Apache 2, you MUST HAVE the newer  version of apxs installed and working. Now it turns out that in  "standard installs" of Apache 2, they put apxs in a different directory  than in Apache 1! In OLDER systems (like Apache 1), it is located in  "/usr/bin" (or someplace similar) and in NEWER installations (like  Apache 2), it is located in "/usr/sbin" (or someplace similar). So, when  you build PHP against an Apache 2 system, sometimes it can use the  OLDER apxs module during the build process! Since I was upgrading to  Apache  2, I had both versions of apxs on my system. I just looked at the  date/time of the 2 apxs files, and saw that one version of it was dated  from the original system install and the other was in the last 24 hours,  and so must have been from my new build. You need to find the older  version and delete it or rename it, so the  newer one will be the only one the system finds when it builds PHP. (In  my installation, I moved  the new apxs program into the old apxs folder, thus deleting the old one  and insuring the build could ONLY find the new one.) 

I hope this helps everyone with this problem. I spent 2 hours tracking this little BEAST down!

---

