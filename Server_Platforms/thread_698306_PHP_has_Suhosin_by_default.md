---
title: "PHP has Suhosin by default?"
date: 2008-02-16
forum: Server Platforms
---

### Post by Jeremy23 on 2008-02-16
I just installed and configured a LAMP server on my Hardy machine (actually, using Lighttpd instead of Apache), ran phpinfo(), and it says that the "server is protected with the Suhosin Patch 0.9.6.2".

I certainly didn't install Suhosin...

```
jeremy@rillian:~$ dpkg -s php5-suhosin 
Package `php5-suhosin' is not installed and no info is available.
```

...which leads me to the conclusion that Ubuntu ships it with Suhosin without any intervention? I have a Feisty server, and that one doesn't have Suhosin -- it only seems to apply to my Hardy machine.

Seems like a good thing to do, but there may be compatibility issues with running non-standard versions of PHP.

---

### Post by faulkes on 2008-02-16
Interesting, could you ouput the phpinfo() section which relates to suhosin.

Having checked launchpad for Hardy I don't see it being listed as a compiled in option or a dependency (and there is a seperate php5-suhosin package as well).

Edit: also the following may give us more information

```

aptitude changelog php5

and 

aptitude changelog libapache2-mod-php5

```

That will probably be a large file, so you may have to spend a bit of time looking through it.

Faulkes

---

### Post by Jeremy23 on 2008-02-16
Yeah, actually, I found it in the changelog yesterday. Here's an abridged version of the changelog entry:

> php5 (5.2.4-1) unstable; urgency=low

  * we shipping with the suhosin patch enabled by default.


And yes, in phpinfo(), it says:

> This server is protected with the Suhosin Patch 0.9.6.2
Copyright (c) 2006 Hardened-PHP Project

---

### Post by ned worcs on 2008-03-31
Ive come up against this too. Ive installed Hardy beta and Suhosin has post.max_vars set at 200 which is the default causing problems with some scripts.

Whats the best way to change the value please?

---

### Post by tubezninja on 2008-05-20
This thread needs to be revived I think.  Has anyone figured out how to remove the suhosin patch from the php5 standard install in Hardy?

---

### Post by Jeremy23 on 2008-05-25
Let me check.

The patch is probably located in the /debian/ directory, so making a new set of debs without Suhosin should be as simple as reversing the patch.

Of course, I haven't checked yet, so this may be more complicated than it seems.

---

### Post by Jeremy23 on 2008-05-25
Before you get your hopes up, please be aware that **I have not even tested to see if the following works**. Seems likely that it will, though. :)

Okay, in the PHP5 source, there is a patch file in "debian/patches/suhosin.patch".

To get to this source, you can do: (without sudo, please)

```
mkdir work && cd work && apt-get source php5 && cd php5-5.2.4
```

Make sure you can build it by doing:

```
sudo apt-get build-dep php5
```

Okay, it looks like the patch isn't applied at this stage (it probably gets applied when you build the package), so just do this:

```
rm debian/patches/suhosin.patch
```

Now, you want to bump up the version number:

```
debchange -v 5.2.4-2ubuntu6~nosuhosin
```

If you've never built a Debian package before, that'll probably fail. To fix it, do this:

```
sudo apt-get install devscripts
```

...and run debchange again.

When you get presented with the nano text editor, just type something like "Hopefully removed Suhosin", and press Ctrl+X and Enter to save.

Should be good to build now. Do this:

```
debuild
```

You should end up with some new .deb packages:

```
ls -l ../*.deb
```

A quick and dirty way to install them (might break stuff) is:

```
sudo dpkg -i ../*.deb
```

---

### Post by Jeremy23 on 2008-05-25
> **ned worcs said:**
> Ive come up against this too. Ive installed Hardy beta and Suhosin has post.max_vars set at 200 which is the default causing problems with some scripts.

Whats the best way to change the value please?
Ned, you can change these things in */etc/php5/apache2/php.ini*.

---

### Post by bjk03 on 2008-06-20
> **Jeremy23 said:**
> Before you get your hopes up, please be aware that **I have not even tested to see if the following works**. Seems likely that it will, though. :)

Okay, in the PHP5 source, there is a patch file in "debian/patches/suhosin.patch".

To get to this source, you can do: (without sudo, please)

```
mkdir work && cd work && apt-get source php5 && cd php5-5.2.4
```

Make sure you can build it by doing:

```
sudo apt-get build-dep php5
```

Okay, it looks like the patch isn't applied at this stage (it probably gets applied when you build the package), so just do this:

```
rm debian/patches/suhosin.patch
```

Now, you want to bump up the version number:

```
debchange -v 5.2.4-2ubuntu6~nosuhosin
```

If you've never built a Debian package before, that'll probably fail. To fix it, do this:

```
sudo apt-get install devscripts
```

...and run debchange again.

When you get presented with the nano text editor, just type something like "Hopefully removed Suhosin", and press Ctrl+X and Enter to save.

Should be good to build now. Do this:

```
debuild
```

You should end up with some new .deb packages:

```
ls -l ../*.deb
```

A quick and dirty way to install them (might break stuff) is:

```
sudo dpkg -i ../*.deb
```

It did not work for me. Said it couldn't find source. What else can I do to get rid of Suhosin?

---

### Post by Jeremy23 on 2008-06-20
That does not give me *nearly* enough information to let me help you.

Can you at least post the error message with the command you typed?

---

### Post by bjk03 on 2008-06-23
Here is the error I got and what I typed to get it.
```
fairview@Office3ubuntu:~$ mkdir work && cd work && apt-get source php5 && cd php5-5.2.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_source_Sources - open (2 No such file or directory)

```

---

### Post by Jeremy23 on 2008-06-24
Okay. Looks like something is screwy with your repository cache.

Try running:

```
sudo apt-get update
```

...and see if that fixes it. If anything fails to download when running apt-get update, that'll likely be your problem.

You could try selecting a new mirror in System &#8594; Administration &#8594; Software Sources, and in the "Download from", pick a different mirror.

---

### Post by bjk03 on 2008-06-24
Ok, made it a bit farther this time. When I ran the debuild command I got this ```
parsechangelog/debian: warning:     debian/changelog(l3): badly formatted heading line
LINE: Hopefully removed Suhosin  *
parsechangelog/debian: warning:     debian/changelog(l5): found trailer where expected start of change data
LINE:  -- Fairview <fairview@Office3ubuntu>  Tue, 24 Jun 2008 07:44:38 -0400
 debian/rules clean
parsechangelog/debian: warning:     debian/changelog(l3): badly formatted heading line
LINE: Hopefully removed Suhosin  *
parsechangelog/debian: warning:     debian/changelog(l5): found trailer where expected start of change data
LINE:  -- Fairview <fairview@Office3ubuntu>  Tue, 24 Jun 2008 07:44:38 -0400
dh_testdir
sed -i -e 's/EXTRA_VERSION="-2ubuntu6~nosuhosin"/EXTRA_VERSION=""/' configure.in
rm -f configure aclocal.m4 config.sub config.guess ltmain.sh
rm -f build/libtool.m4 main/php_config.h.in
rm -f prepared-stamp
QUILT_PATCHES=debian/patches quilt --quiltrc /dev/null pop -a -R || test $? = 2 
No patch removed
rm -rf .pc debian/stamp-patched
dh_testdir
dh_testroot
rm -f configure-apache2-stamp build-apache2-stamp
rm -f configure-cgi-stamp build-cgi-stamp
rm -f configure-cli-stamp build-cli-stamp
rm -f build-pear-stamp
rm -f install-stamp
rm -rf apache2-build
rm -rf cgi-build
rm -rf cli-build
rm -rf pear-build
rm -f debian/copyright
rm -f test-results.txt
dh_clean
# clean up autogenerated cruft
cat debian/modulelist | while read package extname dsoname; do \
		rm -f debian/php5-$package.postinst; \
	done
for sapi in libapache2-mod-php5 php5-cgi php5-cli; do \
		for cruft in postrm links; do \
			rm -f debian/${sapi}.${cruft}; \
		done; \
	done
 dpkg-source -b php5-5.2.4
parsechangelog/debian: warning: ./php5-5.2.4/debian/changelog(l3): badly formatted heading line
LINE: Hopefully removed Suhosin  *
parsechangelog/debian: warning: ./php5-5.2.4/debian/changelog(l5): found trailer where expected start of change data
LINE:  -- Fairview <fairview@Office3ubuntu>  Tue, 24 Jun 2008 07:44:38 -0400
dpkg-source: building php5 using existing php5_5.2.4.orig.tar.gz
dpkg-source: building php5 in php5_5.2.4-2ubuntu6~nosuhosin.diff.gz
dpkg-source: warning: ignoring deletion of file configure
dpkg-source: warning: ignoring deletion of file config.sub
dpkg-source: warning: ignoring deletion of file ltmain.sh
dpkg-source: warning: ignoring deletion of file build/libtool.m4
dpkg-source: warning: ignoring deletion of file main/php_config.h.in
dpkg-source: warning: ignoring deletion of file ext/standard/var_unserializer.c.orig
dpkg-source: warning: ignoring deletion of file ext/standard/url_scanner_ex.c.orig
dpkg-source: warning: ignoring deletion of file ext/date/lib/parse_date.c.orig
dpkg-source: warning: ignoring deletion of file ext/pdo/pdo_sql_parser.c.orig
dpkg-source: warning: ignoring deletion of file aclocal.m4
dpkg-source: warning: ignoring deletion of file config.guess
dpkg-source: building php5 in php5_5.2.4-2ubuntu6~nosuhosin.dsc
 debian/rules build
# quilt exits with 2 as return when there was nothing to do. 
# That's not an error here (but it's usefull to break loops in crude scripts)
QUILT_PATCHES=debian/patches quilt --quiltrc /dev/null push -a || test $? = 2
Patch suhosin.patch does not exist
Applying patch 001-libtool_fixes.patch
patching file TSRM/configure.in
patching file configure.in

Applying patch 002-static_openssl.patch
patching file acinclude.m4

Applying patch 004-ldap_fix.patch
patching file ext/ldap/ldap.c

Applying patch 006-debian_quirks.patch
patching file configure.in
patching file ext/ext_skel
patching file ext/session/session.c
patching file php.ini-dist
patching file php.ini-recommended
patching file sapi/caudium/config.m4
patching file sapi/cli/php.1.in
patching file scripts/Makefile.frag
patching file scripts/php-config.in
patching file scripts/phpize.in

Applying patch 013-force_getaddrinfo.patch
patching file configure.in

Applying patch 017-pread_pwrite_disable.patch
patching file acinclude.m4

Applying patch 019-z_off_t_as_long.patch
patching file ext/zlib/zconf.h
patching file ext/zlib/zlib.h

Applying patch 027-readline_is_editline.patch
patching file ext/readline/config.m4
patching file ext/readline/readline.c
patching file sapi/cli/php_cli.c
patching file sapi/cli/php_cli_readline.c

Applying patch 029-php.ini_paranoid.patch
patching file php.ini-paranoid

Applying patch 033-we_WANT_libtool.patch
patching file build/build2.mk

Applying patch 034-apache2_umask_fix.patch
patching file sapi/apache2handler/sapi_apache2.c

Applying patch 036-fd_setsize_fix.patch
patching file ext/sockets/sockets.c
patching file ext/standard/streamsfuncs.c

Applying patch 043-recode_size_t.patch
patching file ext/recode/recode.c

Applying patch 044-strtod_arm_fix.patch
patching file Zend/zend_strtod.c

Applying patch 045-exif_nesting_level.patch
patching file ext/exif/exif.c

Applying patch 047-zts_with_dl.patch
patching file ext/standard/dl.c

Applying patch 052-phpinfo_no_configure.patch
patching file ext/standard/info.c
patching file ext/standard/tests/general_functions/phpinfo.phpt

Applying patch 053-extension_api.patch
patching file configure.in
patching file scripts/php-config.in

Applying patch 056-mime_magic_liberal.patch
patching file ext/mime_magic/mime_magic.c

Applying patch 057-no_apache_installed.patch
patching file sapi/apache2handler/config.m4
patching file sapi/apache/config.m4
patching file sapi/apache2filter/config.m4
patching file sapi/apache_hooks/config.m4

Applying patch 100-recode_is_shared.patch
patching file ext/recode/config9.m4

Applying patch 101-sqlite_is_shared.patch
patching file ext/sqlite/config.m4

Applying patch 107-reflection_is_ext.patch
patching file ext/reflection/config.m4

Applying patch 108-64_bit_datetime.patch
patching file ext/standard/datetime.c

Applying patch 112-proc_open.patch
patching file ext/standard/proc_open.c

Applying patch 113-php.ini_securitynotes.patch
patching file php.ini-dist

Applying patch disable_dl_by_default.patch
patching file php.ini-dist
patching file php.ini-recommended

Applying patch suhosin.patch
make: *** [debian/stamp-patched] Error 1
debuild: fatal error at line 1247:
debian/rules build failed

```

---

### Post by Jeremy23 on 2008-06-24
Are you *sure* you deleted the suhosin.patch file?

---

### Post by bjk03 on 2008-06-24
I am not 110% certain that I did. The command to remove it is ```
rm debian/patches/suhosin.patch
```correct??

---

### Post by Jeremy23 on 2008-06-24
Correct. If you must, view it in a file browser to make sure.

---

### Post by bjk03 on 2008-06-24
I'll try it tomorrow, I am trying this on 8.04 at work.

---

### Post by bjk03 on 2008-06-25
I guess it IS removed, when I ran the command it came back with ```
rm: cannot remove `debian/patches/suhosin.patch': No such file or directory

```

---

### Post by darkorb on 2008-06-29
You don't infact need to delete the suhosin.patch file (it is however neater if you do).

To fix the error above (bjk03's error)

```
nano debian/patches/series
```
and remove the suhosin.patch line (it's near the bottom of the file).

Once this is done you'll be able to run debuild without any issues.

One thing, you might want to use a diffrent version tag for your package as it seems some scripts catch the "nosuhosin" part of the version tag and assume that it is installed....

I'm currently testing some .deb's that I have rolled myself and as stated in another thread I will upload them for people to use if they are interested (x86 only I'm afraid for the moment - I don't have access to my x86_64 machine).

---

### Post by Jeremy23 on 2008-06-29
Aha. Thanks a lot, darkorb! I wasn't aware of that file. When I've made Debian packages, I've just dumped files in debian/patches, and they've automatically applied before, so I assumed Suhosin would be the same thing.

You've taught me something, too!

---

### Post by darkorb on 2008-06-29
I have put the .deb's I have built for x86 on one of my servers, if there's any issues feel free to drop me a PM on here and I'll get back to you.

[http://debs.got-root.me.uk/php5/i386/](http://debs.got-root.me.uk/php5/i386/)

If you want to download all of the .deb's in one go there is a "bundle" tar.gz here;

[http://debs.got-root.me.uk/php5/i386/php5-bundle_5.2.4-2ubuntu6~darkorb.tar.gz](http://debs.got-root.me.uk/php5/i386/php5-bundle_5.2.4-2ubuntu6~darkorb.tar.gz)

It does not include the php5-dev deb as this has dependencys that are not installed on a normal php5 install.

I'll try to keep upto date with PHP releases if people wish me to do so.

Also, using "suhosin" in any part of the tag name can fool some scripts into thinking it is installed - causing them to throw up an error even though it isn't installed.... so if you do roll your own deb's make sure you don't use that in any part of the version tagging (even if it's nosuhosin it still get's detected by some scripts....)

Please note however, I have tested them on 2 diffrent servers and it seems to work fine, YMMV however (insert standard disclaimer here). If you have any feedback please let me know.

**These have only been tested on Hardy (8.04 LTS)** I have no idea what will happen if you try them on a diffrent Ubuntu version. If you need a build for an older version (I don't know if the issue affects anything aside from 8.04) then PM me and I'll sort something out for you.

> PHP 5.2.4-2ubuntu6~darkorb (cli) (built: Jun 29 2008 15:44:59)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

Quick and easy way to install;

```
cd ~; mkdir temp; cd temp; wget http://debs.got-root.me.uk/php5/i386/php5-bundle_5.2.4-2ubuntu6~darkorb.tar.gz; tar xvzf php5-bundle_5.2.4-2ubuntu6~darkorb.tar.gz; sudo dpkg -i *.deb; cd ..; rm temp/ -r
```

---

### Post by bjk03 on 2008-06-29
> **darkorb said:**
> 

Quick and easy way to install;

```
cd ~; mkdir temp; cd temp; wget http://debs.got-root.me.uk/php5/i386/php5-bundle_5.2.4-2ubuntu6~darkorb.tar.gz; tar xvzf php5-bundle_5.2.4-2ubuntu6~darkorb.tar.gz; sudo dpkg -i *.deb; cd ..; rm temp/ -r
```


I just tried this on a machine running 8.04 here at home and it works!! Thank you SO much!!!

---

### Post by darkorb on 2008-06-30
> **bjk03 said:**
> I just tried this on a machine running 8.04 here at home and it works!! Thank you SO much!!!

No problems at all, let me know if you have any issues with it.

---

