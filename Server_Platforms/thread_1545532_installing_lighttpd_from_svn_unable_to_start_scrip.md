---
title: "installing lighttpd from svn unable to start script"
date: 2010-08-04
forum: Server Platforms
---

### Post by tapas_mishra on 2010-08-04
I have followed all the steps exactly as mentioned on  [documentation.]("http://redmine.lighttpd.net/projects/lighttpd/wiki/InstallFromSource")

I logged in as Root on a Ubuntu system
and then 
```

cd /opt
svn checkout svn://svn.lighttpd.net/lighttpd/branches/lighttpd-1.4.x/
cd lighttpd-1.4.x
./autogen.sh
./configure
make 
make install

```

After this what do I need to do to be able to start the lighttpd ?


After this I did not found any script  /etc/init.d/lighttpd
so what more has to be done ?

---

### Post by konsole on 2010-08-04
> **tapas_mishra said:**
> I have followed all the steps exactly as mentioned on  [documentation.]("http://redmine.lighttpd.net/projects/lighttpd/wiki/InstallFromSource")

I logged in as Root on a Ubuntu system
and then 
```

cd /opt
svn checkout svn://svn.lighttpd.net/lighttpd/branches/lighttpd-1.4.x/
cd lighttpd-1.4.x
./autogen.sh
./configure
make 
make install

```

After this what do I need to do to be able to start the lighttpd ?

After this I did not found any script  /etc/init.d/lighttpd
so what more has to be done ?

Did the source checkout complete error free?

Did "configure" or "make" produce any errors?

Does /etc/lighttpd/lighttpd.conf exist?

I installed the same as you apart from "make install". Instead I used "checkinstall" and installed the deb. Worked without a hitch.

---

### Post by tapas_mishra on 2010-08-04
> **konsole said:**
> Did the source checkout complete error free?

 
here is the output 
```

root@tapas-laptop:/opt# svn checkout svn://svn.lighttpd.net/lighttpd/branches/lighttpd-1.4.x/
A    lighttpd-1.4.x/cmake
A    lighttpd-1.4.x/cmake/LighttpdMacros.cmake
A    lighttpd-1.4.x/AUTHORS
A    lighttpd-1.4.x/src
A    lighttpd-1.4.x/src/data_config.c
A    lighttpd-1.4.x/src/configfile-glue.c
A    lighttpd-1.4.x/src/fdevent.h
A    lighttpd-1.4.x/src/mod_cgi.c
A    lighttpd-1.4.x/src/network_write.c
A    lighttpd-1.4.x/src/joblist.c
A    lighttpd-1.4.x/src/mod_cml.c
A    lighttpd-1.4.x/src/joblist.h
A    lighttpd-1.4.x/src/mod_secure_download.c
A    lighttpd-1.4.x/src/connections-glue.c
A    lighttpd-1.4.x/src/array.c
A    lighttpd-1.4.x/src/mod_cml.h
A    lighttpd-1.4.x/src/base.h
A    lighttpd-1.4.x/src/mod_rewrite.c
A    lighttpd-1.4.x/src/lempar.c
A    lighttpd-1.4.x/src/status_counter.c
A    lighttpd-1.4.x/src/connections.c
A    lighttpd-1.4.x/src/array.h
A    lighttpd-1.4.x/src/data_integer.c
A    lighttpd-1.4.x/src/mod_staticfile.c
A    lighttpd-1.4.x/src/status_counter.h
A    lighttpd-1.4.x/src/connections.h
A    lighttpd-1.4.x/src/mod_alias.c
A    lighttpd-1.4.x/src/network.c
A    lighttpd-1.4.x/src/network.h
A    lighttpd-1.4.x/src/fdevent_freebsd_kqueue.c
A    lighttpd-1.4.x/src/configfile.c
A    lighttpd-1.4.x/src/mod_trigger_b4_dl.c
A    lighttpd-1.4.x/src/mod_evhost.c
A    lighttpd-1.4.x/src/chunk.c
A    lighttpd-1.4.x/src/splaytree.c
A    lighttpd-1.4.x/src/configfile.h
A    lighttpd-1.4.x/src/lemon.c
A    lighttpd-1.4.x/src/fdevent_solaris_devpoll.c
A    lighttpd-1.4.x/src/splaytree.h
A    lighttpd-1.4.x/src/chunk.h
A    lighttpd-1.4.x/src/etag.c
A    lighttpd-1.4.x/src/data_count.c
A    lighttpd-1.4.x/src/mod_skeleton.c
A    lighttpd-1.4.x/src/mod_scgi.c
A    lighttpd-1.4.x/src/fastcgi.h
A    lighttpd-1.4.x/src/etag.h
A    lighttpd-1.4.x/src/keyvalue.c
A    lighttpd-1.4.x/src/mod_mysql_vhost.c
A    lighttpd-1.4.x/src/request.c
A    lighttpd-1.4.x/src/network_backends.h
A    lighttpd-1.4.x/src/bitset.c
A    lighttpd-1.4.x/src/keyvalue.h
A    lighttpd-1.4.x/src/request.h
A    lighttpd-1.4.x/src/mod_magnet_cache.c
A    lighttpd-1.4.x/src/mod_flv_streaming.c
A    lighttpd-1.4.x/src/bitset.h
A    lighttpd-1.4.x/src/mod_magnet_cache.h
A    lighttpd-1.4.x/src/lighttpd-angel.c
A    lighttpd-1.4.x/src/sys-socket.h
A    lighttpd-1.4.x/src/sys-mmap.h
A    lighttpd-1.4.x/src/inet_ntop_cache.c
A    lighttpd-1.4.x/src/mod_rrdtool.c
A    lighttpd-1.4.x/src/inet_ntop_cache.h
A    lighttpd-1.4.x/src/mod_ssi_expr.c
A    lighttpd-1.4.x/src/stat_cache.c
A    lighttpd-1.4.x/src/response.c
A    lighttpd-1.4.x/src/plugin.c
A    lighttpd-1.4.x/src/mod_ssi_expr.h
A    lighttpd-1.4.x/src/plugin.h
A    lighttpd-1.4.x/src/response.h
A    lighttpd-1.4.x/src/stat_cache.h
A    lighttpd-1.4.x/src/SConscript
A    lighttpd-1.4.x/src/data_array.c
A    lighttpd-1.4.x/src/mod_cml_funcs.c
A    lighttpd-1.4.x/src/buffer.c
A    lighttpd-1.4.x/src/mod_simple_vhost.c
A    lighttpd-1.4.x/src/mod_userdir.c
A    lighttpd-1.4.x/src/mod_cml_funcs.h
A    lighttpd-1.4.x/src/buffer.h
A    lighttpd-1.4.x/src/mod_proxy.c
A    lighttpd-1.4.x/src/mod_extforward.c
A    lighttpd-1.4.x/src/Makefile.am
A    lighttpd-1.4.x/src/config.h.cmake
A    lighttpd-1.4.x/src/network_writev.c
A    lighttpd-1.4.x/src/mod_expire.c
A    lighttpd-1.4.x/src/network_freebsd_sendfile.c
A    lighttpd-1.4.x/src/network_openssl.c
A    lighttpd-1.4.x/src/http_auth_digest.c
A    lighttpd-1.4.x/src/http_auth.c
A    lighttpd-1.4.x/src/mod_redirect.c
A    lighttpd-1.4.x/src/mod_usertrack.c
A    lighttpd-1.4.x/src/http_auth_digest.h
A    lighttpd-1.4.x/src/http_auth.h
A    lighttpd-1.4.x/src/mod_webdav.c
A    lighttpd-1.4.x/src/configparser.y
A    lighttpd-1.4.x/src/crc32.c
A    lighttpd-1.4.x/src/crc32.h
A    lighttpd-1.4.x/src/mod_status.c
A    lighttpd-1.4.x/src/md5.c
A    lighttpd-1.4.x/src/md5.h
A    lighttpd-1.4.x/src/mod_compress.c
A    lighttpd-1.4.x/src/mod_ssi.c
A    lighttpd-1.4.x/src/mod_auth.c
A    lighttpd-1.4.x/src/mod_ssi.h
A    lighttpd-1.4.x/src/mod_auth.h
A    lighttpd-1.4.x/src/settings.h
A    lighttpd-1.4.x/src/mod_cml_lua.c
A    lighttpd-1.4.x/src/fdevent_linux_rtsig.c
A    lighttpd-1.4.x/src/version.h
A    lighttpd-1.4.x/src/http-header-glue.c
A    lighttpd-1.4.x/src/data_string.c
A    lighttpd-1.4.x/src/mod_evasive.c
A    lighttpd-1.4.x/src/mod_setenv.c
A    lighttpd-1.4.x/src/mod_indexfile.c
A    lighttpd-1.4.x/src/mod_uploadprogress.c
A    lighttpd-1.4.x/src/data_fastcgi.c
A    lighttpd-1.4.x/src/mod_fastcgi.c
A    lighttpd-1.4.x/src/fdevent_poll.c
A    lighttpd-1.4.x/src/network_solaris_sendfilev.c
A    lighttpd-1.4.x/src/fdevent_select.c
A    lighttpd-1.4.x/src/stream.c
A    lighttpd-1.4.x/src/CMakeLists.txt
A    lighttpd-1.4.x/src/mod_ssi_exprparser.y
A    lighttpd-1.4.x/src/stream.h
A    lighttpd-1.4.x/src/mod_access.c
A    lighttpd-1.4.x/src/mod_accesslog.c
A    lighttpd-1.4.x/src/fdevent_linux_sysepoll.c
A    lighttpd-1.4.x/src/server.c
A    lighttpd-1.4.x/src/http_chunk.c
A    lighttpd-1.4.x/src/mod_dirlisting.c
A    lighttpd-1.4.x/src/mod_magnet.c
A    lighttpd-1.4.x/src/server.h
A    lighttpd-1.4.x/src/http_chunk.h
A    lighttpd-1.4.x/src/network_linux_sendfile.c
A    lighttpd-1.4.x/src/log.c
A    lighttpd-1.4.x/src/proc_open.c
A    lighttpd-1.4.x/src/log.h
A    lighttpd-1.4.x/src/proc_open.h
A    lighttpd-1.4.x/src/fdevent.c
A    lighttpd-1.4.x/distribute.sh.in
A    lighttpd-1.4.x/README
A    lighttpd-1.4.x/tests
A    lighttpd-1.4.x/tests/mod-auth.t
A    lighttpd-1.4.x/tests/mod-access.t
A    lighttpd-1.4.x/tests/bug-12.conf
A    lighttpd-1.4.x/tests/mod-secdownload.t
A    lighttpd-1.4.x/tests/fastcgi-10.conf
A    lighttpd-1.4.x/tests/bug-06.conf
A    lighttpd-1.4.x/tests/core-response.t
A    lighttpd-1.4.x/tests/mod-extforward.conf
A    lighttpd-1.4.x/tests/symlink.t
A    lighttpd-1.4.x/tests/request.t
A    lighttpd-1.4.x/tests/mod-userdir.t
A    lighttpd-1.4.x/tests/core-keepalive.t
A    lighttpd-1.4.x/tests/var-include.conf
A    lighttpd-1.4.x/tests/cleanup.sh
A    lighttpd-1.4.x/tests/mod-proxy.t
A    lighttpd-1.4.x/tests/core-var-include.t
A    lighttpd-1.4.x/tests/mod-extforward.t
A    lighttpd-1.4.x/tests/404-handler.conf
A    lighttpd-1.4.x/tests/lowercase.conf
A    lighttpd-1.4.x/tests/condition.conf
A    lighttpd-1.4.x/tests/lighttpd.htpasswd
A    lighttpd-1.4.x/tests/CMakeLists.txt
A    lighttpd-1.4.x/tests/mod-redirect.t
A    lighttpd-1.4.x/tests/core-request.t
A    lighttpd-1.4.x/tests/mod-cgi.t
A    lighttpd-1.4.x/tests/mod-setenv.t
A    lighttpd-1.4.x/tests/var-include-sub.conf
A    lighttpd-1.4.x/tests/cachable.t
A    lighttpd-1.4.x/tests/fastcgi-13.conf
A    lighttpd-1.4.x/tests/lowercase.t
A    lighttpd-1.4.x/tests/SConscript
A    lighttpd-1.4.x/tests/fcgi-responder.c
A    lighttpd-1.4.x/tests/fcgi-auth.c
A    lighttpd-1.4.x/tests/wrapper.sh
A    lighttpd-1.4.x/tests/core.t
A    lighttpd-1.4.x/tests/lighttpd.user
A    lighttpd-1.4.x/tests/mod-compress.conf
A    lighttpd-1.4.x/tests/mod-fastcgi.t
A    lighttpd-1.4.x/tests/mod-rewrite.t
A    lighttpd-1.4.x/tests/lighttpd.conf
A    lighttpd-1.4.x/tests/fastcgi-responder.conf
A    lighttpd-1.4.x/tests/fastcgi-auth.conf
A    lighttpd-1.4.x/tests/proxy.conf
A    lighttpd-1.4.x/tests/prepare.sh
A    lighttpd-1.4.x/tests/docroot
A    lighttpd-1.4.x/tests/docroot/www
A    lighttpd-1.4.x/tests/docroot/www/sendfile.php
A    lighttpd-1.4.x/tests/docroot/www/get-header.pl
A    lighttpd-1.4.x/tests/docroot/www/nph-status.pl
A    lighttpd-1.4.x/tests/docroot/www/404.pl
A    lighttpd-1.4.x/tests/docroot/www/crlfcrash.pl
A    lighttpd-1.4.x/tests/docroot/www/ip.pl
A    lighttpd-1.4.x/tests/docroot/www/cgi-pathinfo.pl
A    lighttpd-1.4.x/tests/docroot/www/ssi.shtml
A    lighttpd-1.4.x/tests/docroot/www/index.txt
A    lighttpd-1.4.x/tests/docroot/www/exec-date.shtml
A    lighttpd-1.4.x/tests/docroot/www/redirect.php
A    lighttpd-1.4.x/tests/docroot/www/cgi.php
A    lighttpd-1.4.x/tests/docroot/www/get-post-len.pl
A    lighttpd-1.4.x/tests/docroot/www/phpinfo.php
A    lighttpd-1.4.x/tests/docroot/www/dummydir
A    lighttpd-1.4.x/tests/docroot/www/get-env.php
A    lighttpd-1.4.x/tests/docroot/www/send404.pl
A    lighttpd-1.4.x/tests/docroot/www/expire
A    lighttpd-1.4.x/tests/docroot/www/expire/access.txt
A    lighttpd-1.4.x/tests/docroot/www/expire/modification.txt
A    lighttpd-1.4.x/tests/docroot/www/expire/Makefile.am
A    lighttpd-1.4.x/tests/docroot/www/get-server-env.php
A    lighttpd-1.4.x/tests/docroot/www/prefix.fcgi
A    lighttpd-1.4.x/tests/docroot/www/go
A    lighttpd-1.4.x/tests/docroot/www/go/cgi.php
A    lighttpd-1.4.x/tests/docroot/www/go/Makefile.am
A    lighttpd-1.4.x/tests/docroot/www/indexfile
A    lighttpd-1.4.x/tests/docroot/www/indexfile/rewrite.php
A    lighttpd-1.4.x/tests/docroot/www/indexfile/Makefile.am
A    lighttpd-1.4.x/tests/docroot/www/indexfile/return-404.php
A    lighttpd-1.4.x/tests/docroot/www/indexfile/index.php
A    lighttpd-1.4.x/tests/docroot/www/Makefile.am
A    lighttpd-1.4.x/tests/docroot/www/404.html
A    lighttpd-1.4.x/tests/docroot/www/index.html
A    lighttpd-1.4.x/tests/docroot/www/cgi.pl
A    lighttpd-1.4.x/tests/docroot/www/404.fcgi
A    lighttpd-1.4.x/tests/docroot/123
A    lighttpd-1.4.x/tests/docroot/123/12345.html
A    lighttpd-1.4.x/tests/docroot/123/dummyfile.bla
A    lighttpd-1.4.x/tests/docroot/123/Makefile.am
A    lighttpd-1.4.x/tests/docroot/123/phpinfo.php
A    lighttpd-1.4.x/tests/docroot/123/12345.txt
A    lighttpd-1.4.x/tests/docroot/Makefile.am
A    lighttpd-1.4.x/tests/Makefile.am
A    lighttpd-1.4.x/tests/core-404-handler.t
A    lighttpd-1.4.x/tests/mod-compress.t
A    lighttpd-1.4.x/tests/LightyTest.pm
A    lighttpd-1.4.x/tests/mod-ssi.t
A    lighttpd-1.4.x/tests/core-condition.t
A    lighttpd-1.4.x/tests/run-tests.pl
A    lighttpd-1.4.x/configure.ac
A    lighttpd-1.4.x/doc
A    lighttpd-1.4.x/doc/redirect.txt
A    lighttpd-1.4.x/doc/performance.txt
A    lighttpd-1.4.x/doc/ssl.txt
A    lighttpd-1.4.x/doc/secdownload.txt
A    lighttpd-1.4.x/doc/accesslog.txt
A    lighttpd-1.4.x/doc/setenv.txt
A    lighttpd-1.4.x/doc/traffic-shaping.txt
A    lighttpd-1.4.x/doc/security.txt
A    lighttpd-1.4.x/doc/trigger_b4_dl.txt
A    lighttpd-1.4.x/doc/webdav.txt
A    lighttpd-1.4.x/doc/scripts
A    lighttpd-1.4.x/doc/scripts/spawn-php.sh
A    lighttpd-1.4.x/doc/scripts/Makefile.am
A    lighttpd-1.4.x/doc/scripts/rrdtool-graph.sh
A    lighttpd-1.4.x/doc/userdir.txt
A    lighttpd-1.4.x/doc/features.txt
A    lighttpd-1.4.x/doc/proxy.txt
A    lighttpd-1.4.x/doc/status.txt
A    lighttpd-1.4.x/doc/mysqlvhost.txt
A    lighttpd-1.4.x/doc/compress.txt
A    lighttpd-1.4.x/doc/fastcgi-state.txt
A    lighttpd-1.4.x/doc/access.txt
A    lighttpd-1.4.x/doc/cgi.txt
A    lighttpd-1.4.x/doc/fastcgi-state.dot
A    lighttpd-1.4.x/doc/configuration.txt
A    lighttpd-1.4.x/doc/lighttpd.8
A    lighttpd-1.4.x/doc/evhost.txt
A    lighttpd-1.4.x/doc/dirlisting.txt
A    lighttpd-1.4.x/doc/oldstyle.css
A    lighttpd-1.4.x/doc/cml.txt
A    lighttpd-1.4.x/doc/magnet.txt
A    lighttpd-1.4.x/doc/authentication.txt
A    lighttpd-1.4.x/doc/state.txt
A    lighttpd-1.4.x/doc/fastcgi.txt
A    lighttpd-1.4.x/doc/rewrite.txt
A    lighttpd-1.4.x/doc/plugins.txt
A    lighttpd-1.4.x/doc/newstyle.css
A    lighttpd-1.4.x/doc/skeleton.txt
A    lighttpd-1.4.x/doc/scgi.txt
A    lighttpd-1.4.x/doc/rrdtool.txt
A    lighttpd-1.4.x/doc/extforward.txt
A    lighttpd-1.4.x/doc/config
A    lighttpd-1.4.x/doc/config/lighttpd.conf
A    lighttpd-1.4.x/doc/config/conf.d
A    lighttpd-1.4.x/doc/config/conf.d/compress.conf
A    lighttpd-1.4.x/doc/config/conf.d/expire.conf
A    lighttpd-1.4.x/doc/config/conf.d/ssi.conf
A    lighttpd-1.4.x/doc/config/conf.d/auth.conf
A    lighttpd-1.4.x/doc/config/conf.d/secdownload.conf
A    lighttpd-1.4.x/doc/config/conf.d/access_log.conf
A    lighttpd-1.4.x/doc/config/conf.d/cgi.conf
A    lighttpd-1.4.x/doc/config/conf.d/geoip.conf
A    lighttpd-1.4.x/doc/config/conf.d/mod.template
A    lighttpd-1.4.x/doc/config/conf.d/trigger_b4_dl.conf
A    lighttpd-1.4.x/doc/config/conf.d/webdav.conf
A    lighttpd-1.4.x/doc/config/conf.d/dirlisting.conf
A    lighttpd-1.4.x/doc/config/conf.d/evhost.conf
A    lighttpd-1.4.x/doc/config/conf.d/cml.conf
A    lighttpd-1.4.x/doc/config/conf.d/magnet.conf
A    lighttpd-1.4.x/doc/config/conf.d/simple_vhost.conf
A    lighttpd-1.4.x/doc/config/conf.d/userdir.conf
A    lighttpd-1.4.x/doc/config/conf.d/fastcgi.conf
A    lighttpd-1.4.x/doc/config/conf.d/proxy.conf
A    lighttpd-1.4.x/doc/config/conf.d/status.conf
A    lighttpd-1.4.x/doc/config/conf.d/Makefile.am
A    lighttpd-1.4.x/doc/config/conf.d/rrdtool.conf
A    lighttpd-1.4.x/doc/config/conf.d/scgi.conf
A    lighttpd-1.4.x/doc/config/conf.d/debug.conf
A    lighttpd-1.4.x/doc/config/conf.d/mime.conf
A    lighttpd-1.4.x/doc/config/conf.d/mysql_vhost.conf
A    lighttpd-1.4.x/doc/config/vhosts.d
A    lighttpd-1.4.x/doc/config/vhosts.d/vhosts.template
A    lighttpd-1.4.x/doc/config/vhosts.d/Makefile.am
A    lighttpd-1.4.x/doc/config/Makefile.am
A    lighttpd-1.4.x/doc/config/modules.conf
A    lighttpd-1.4.x/doc/state.dot
A    lighttpd-1.4.x/doc/alias.txt
A    lighttpd-1.4.x/doc/simple-vhost.txt
A    lighttpd-1.4.x/doc/Makefile.am
A    lighttpd-1.4.x/doc/expire.txt
A    lighttpd-1.4.x/doc/initscripts
A    lighttpd-1.4.x/doc/initscripts/rc.lighttpd
A    lighttpd-1.4.x/doc/initscripts/sysconfig.lighttpd
A    lighttpd-1.4.x/doc/initscripts/rc.lighttpd.redhat
A    lighttpd-1.4.x/doc/initscripts/Makefile.am
A    lighttpd-1.4.x/doc/ssi.txt
A    lighttpd-1.4.x/INSTALL
A    lighttpd-1.4.x/SConstruct
A    lighttpd-1.4.x/COPYING
A    lighttpd-1.4.x/Makefile.am
A    lighttpd-1.4.x/autogen.sh
A    lighttpd-1.4.x/config.py-sample
A    lighttpd-1.4.x/NEWS
A    lighttpd-1.4.x/CMakeLists.txt
 U   lighttpd-1.4.x
Checked out revision 2744.

```When I executed ./autogen.sh
following warning came
```

configure.ac:30: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:386: AC_USE_SYSTEM_EXTENSIONS is expanded from...
../../lib/autoconf/specific.m4:459: AC_MINIX is expanded from...
configure.ac:30: the top level
configure.ac:30: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.ac:30: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:386: AC_USE_SYSTEM_EXTENSIONS is expanded from...
../../lib/autoconf/specific.m4:459: AC_MINIX is expanded from...
configure.ac:30: the top level
configure.ac:30: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.ac:30: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:386: AC_USE_SYSTEM_EXTENSIONS is expanded from...
../../lib/autoconf/specific.m4:459: AC_MINIX is expanded from...
configure.ac:30: the top level
configure.ac:30: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.ac:18: installing `./compile'
configure.ac:9: installing `./config.guess'
configure.ac:9: installing `./config.sub'
configure.ac:11: installing `./install-sh'
configure.ac:11: installing `./missing'
src/Makefile.am: installing `./depcomp'
configure.ac:30: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:386: AC_USE_SYSTEM_EXTENSIONS is expanded from...
../../lib/autoconf/specific.m4:459: AC_MINIX is expanded from...
configure.ac:30: the top level
configure.ac:30: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS

```I had saved the out put in 
as
```

./autogent.sh > /root/autogen_out.txt


```So here is complete output
```

./autogen.sh: running `libtoolize --copy --force'
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
./autogen.sh: running `aclocal -I m4'
./autogen.sh: running `autoheader'
./autogen.sh: running `automake --add-missing --copy --foreign'
./autogen.sh: running `autoconf'
Now type './configure ...' and 'make' to compile.
~                                                   
```> **konsole said:**
> 
Did "configure" 

No here is the output
```

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for library containing strerror... none required
checking for minix/config.h... (cached) no
checking whether it is safe to define __EXTENSIONS__... (cached) yes
checking for function prototypes... yes
checking for string.h... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking sys/sendfile.h usability... yes
checking sys/sendfile.h presence... yes
checking for sys/sendfile.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/devpoll.h usability... no
checking sys/devpoll.h presence... no
checking for sys/devpoll.h... no
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/event.h usability... no
checking sys/event.h presence... no
checking for sys/event.h... no
checking sys/port.h usability... no
checking sys/port.h presence... no
checking for sys/port.h... no
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sys/syslimits.h usability... no
checking sys/syslimits.h presence... no
checking for sys/syslimits.h... no
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking uuid/uuid.h usability... yes
checking uuid/uuid.h presence... yes
checking for uuid/uuid.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether char is unsigned... no
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for struct tm.tm_gmtoff... yes
checking for struct sockaddr_storage... yes
checking for socklen_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for issetugid... no
checking for inet_pton... yes
checking for MySQL support... no
checking for LDAP support...
checking for extended attributes support...
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing hstrerror... none required
checking for library containing dlopen... -ldl
checking for dlfcn.h... (cached) yes
checking for valgrind... no
checking for OpenSSL... no
checking for perl regular expressions support... yes
checking for pcre-config... /usr/bin/pcre-config
checking for zlib support... yes
checking for deflate in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for bzip2 support... yes
checking for BZ2_bzCompress in -lbz2... yes
checking bzlib.h usability... yes
checking bzlib.h presence... yes
checking for bzlib.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for FAM... no
checking for properties in mod_webdav... no
checking for gdbm... no
checking for memcache... no
checking if lua-support is requested... no
checking for library containing crypt... -lcrypt
checking crypt.h usability... yes
checking crypt.h presence... yes
checking for crypt.h... yes
checking for library containing sendfilev... no
checking for dup2... yes
checking for getcwd... yes
checking for inet_ntoa... yes
checking for inet_ntop... yes
checking for memset... yes
checking for mmap... yes
checking for munmap... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes
checking for strtol... yes
checking for sendfile... yes
checking for getopt... yes
checking for socket... yes
checking for lstat... yes
checking for gethostbyname... yes
checking for poll... yes
checking for sigtimedwait... yes
checking for epoll_ctl... yes
checking for getrlimit... yes
checking for chroot... yes
checking for getuid... yes
checking for select... yes
checking for signal... yes
checking for pathconf... yes
checking for madvise... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for writev... yes
checking for sigaction... yes
checking for sendfile64... yes
checking for send_file... no
checking for kqueue... no
checking for port_create... no
checking for localtime_r... yes
checking for gmtime_r... yes
checking for Large File System support...
checking size of long... 4
checking size of off_t... 8
checking if sendfile works... yes
checking for IPv6 support... yes
checking for FCGI_Accept in -lfcgi... yes
checking fastcgi.h usability... yes
checking fastcgi.h presence... yes
checking for fastcgi.h... yes
checking fastcgi/fastcgi.h usability... no
checking fastcgi/fastcgi.h presence... no
checking for fastcgi/fastcgi.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/config/conf.d/Makefile
config.status: creating doc/config/vhosts.d/Makefile
config.status: creating doc/config/Makefile
config.status: creating doc/scripts/Makefile
config.status: creating doc/initscripts/Makefile
config.status: creating doc/Makefile
config.status: creating tests/Makefile
config.status: creating tests/docroot/Makefile
config.status: creating tests/docroot/123/Makefile
config.status: creating tests/docroot/www/Makefile
config.status: creating tests/docroot/www/go/Makefile
config.status: creating tests/docroot/www/indexfile/Makefile
config.status: creating tests/docroot/www/expire/Makefile
config.status: creating distribute.sh
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

Plugins:

enabled:
  mod_access
  mod_accesslog
  mod_alias
  mod_auth
  mod_cgi
  mod_compress
  mod_dirlisting
  mod_evhost
  mod_expire
  mod_extforward
  mod_fastcgi
  mod_flv_streaming
  mod_indexfile
  mod_proxy
  mod_redirect
  mod_rewrite
  mod_rrdtool
  mod_scgi
 mod_secdownload
  mod_setenv
  mod_simple_vhost
  mod_ssi
  mod_staticfile
  mod_status
  mod_trigger_b4_dl
  mod_userdir
  mod_usertrack
  mod_webdav
disabled:
  mod_cml
  mod_magnet
  mod_mysql_vhost

Features:

enabled:
  auth-crypt
  compress-bzip2
  compress-deflate
  compress-gzip
  large-files
  network-ipv6
  regex-conditionals
disabled:
  auth-ldap
  network-openssl
  stat-cache-fam
  storage-gdbm
  storage-memcache
  webdav-locks
  webdav-properties



```> **konsole said:**
> 
or "make" produce any errors?

No
here is the output of
```

root@tapas-laptop:/opt/lighttpd-1.4.x# make > /root/light_make.txt

```there were some warnings
```

mod_accesslog.c: In function &#8216;mod_accesslog_free&#8217;:
mod_accesslog.c:411: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
mod_accesslog.c: In function &#8216;log_access_cycle&#8217;:
mod_accesslog.c:589: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
mod_accesslog.c: In function &#8216;log_access_write&#8217;:
mod_accesslog.c:900: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
server.c: In function &#8216;show_version&#8217;:
server.c:364: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
server.c: In function &#8216;show_help&#8217;:
server.c:511: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
server.c: In function &#8216;main&#8217;:
server.c:916: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
configfile.c: In function &#8216;config_parse_cmd&#8217;:
configfile.c:1008: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result
configfile.c:1022: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result
log.c: In function &#8216;log_error_write&#8217;:
log.c:369: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result


```and the content of /root/light_configure.txt
are
```

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for library containing strerror... none required
checking for minix/config.h... (cached) no
checking whether it is safe to define __EXTENSIONS__... (cached) yes
checking for function prototypes... yes
checking for string.h... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking sys/sendfile.h usability... yes
checking sys/sendfile.h presence... yes
checking for sys/sendfile.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/devpoll.h usability... no
checking sys/devpoll.h presence... no
checking for sys/devpoll.h... no
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/event.h usability... no
checking sys/event.h presence... no
checking for sys/event.h... no
checking sys/port.h usability... no
checking sys/port.h presence... no
checking for sys/port.h... no
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sys/syslimits.h usability... no
checking sys/syslimits.h presence... no
checking for sys/syslimits.h... no
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking uuid/uuid.h usability... yes
checking uuid/uuid.h presence... yes
checking for uuid/uuid.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether char is unsigned... no
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for struct tm.tm_gmtoff... yes
checking for struct sockaddr_storage... yes
checking for socklen_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for issetugid... no
checking for inet_pton... yes
checking for MySQL support... no
checking for LDAP support... 
checking for extended attributes support... 
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing hstrerror... none required
checking for library containing dlopen... -ldl
checking for dlfcn.h... (cached) yes
checking for valgrind... no
checking for OpenSSL... no
checking for perl regular expressions support... yes
checking for pcre-config... /usr/bin/pcre-config
checking for zlib support... yes
checking for deflate in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for bzip2 support... yes
checking for BZ2_bzCompress in -lbz2... yes
checking bzlib.h usability... yes
checking bzlib.h presence... yes
checking for bzlib.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for FAM... no
checking for properties in mod_webdav... no
checking for gdbm... no
checking for memcache... no
checking if lua-support is requested... no
checking for library containing crypt... -lcrypt
checking crypt.h usability... yes
checking crypt.h presence... yes
checking for crypt.h... yes
checking for library containing sendfilev... no
checking for dup2... yes
checking for getcwd... yes
checking for inet_ntoa... yes
checking for inet_ntop... yes
checking for memset... yes
checking for mmap... yes
checking for munmap... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes
checking for strtol... yes
checking for sendfile... yes
checking for getopt... yes
checking for socket... yes
checking for lstat... yes
checking for gethostbyname... yes
checking for poll... yes
checking for sigtimedwait... yes
checking for epoll_ctl... yes
checking for getrlimit... yes
checking for chroot... yes
checking for getuid... yes
checking for select... yes
checking for signal... yes
checking for pathconf... yes
checking for madvise... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for writev... yes
checking for sigaction... yes
checking for sendfile64... yes
checking for send_file... no
checking for kqueue... no
checking for port_create... no
checking for localtime_r... yes
checking for gmtime_r... yes
checking for Large File System support... 
checking size of long... 4
checking size of off_t... 8
checking if sendfile works... yes
checking for IPv6 support... yes
checking for FCGI_Accept in -lfcgi... yes
checking fastcgi.h usability... yes
checking fastcgi.h presence... yes
checking for fastcgi.h... yes
checking fastcgi/fastcgi.h usability... no
checking fastcgi/fastcgi.h presence... no
checking for fastcgi/fastcgi.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/config/conf.d/Makefile
config.status: creating doc/config/vhosts.d/Makefile
config.status: creating doc/config/Makefile
config.status: creating doc/scripts/Makefile
config.status: creating doc/initscripts/Makefile
config.status: creating doc/Makefile
config.status: creating tests/Makefile
config.status: creating tests/docroot/Makefile
config.status: creating tests/docroot/123/Makefile
config.status: creating tests/docroot/www/Makefile
config.status: creating tests/docroot/www/go/Makefile
config.status: creating tests/docroot/www/indexfile/Makefile
config.status: creating tests/docroot/www/expire/Makefile
config.status: creating distribute.sh
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

Plugins:

enabled: 
  mod_access
  mod_accesslog
  mod_alias
  mod_auth
  mod_cgi
  mod_compress
  mod_dirlisting
  mod_evhost
  mod_expire
  mod_extforward
  mod_fastcgi
  mod_flv_streaming
  mod_indexfile
  mod_proxy
  mod_redirect
  mod_rewrite
  mod_rrdtool
  mod_scgi
  mod_secdownload
  mod_setenv
  mod_simple_vhost
  mod_ssi
  mod_staticfile
  mod_status
  mod_trigger_b4_dl
  mod_userdir
  mod_usertrack
  mod_webdav
disabled: 
  mod_cml
  mod_magnet
  mod_mysql_vhost

Features:

enabled: 
  auth-crypt
  compress-bzip2
  compress-deflate
  compress-gzip
  large-files
  network-ipv6
  regex-conditionals
disabled: 
  auth-ldap
  network-openssl
  stat-cache-fam
  storage-gdbm
  storage-memcache
  webdav-locks
  webdav-properties


```> **konsole said:**
> 
Does /etc/lighttpd/lighttpd.conf exist?

No
> **konsole said:**
> 
I installed the same as you apart from "make install". Instead I used "checkinstall" and installed the deb. Worked without a hitch.
Ok in the last part I also tried instead of make install checkinstall
```

Done. The new package has been installed and saved to

 /opt/lighttpd-1.4.x/lighttpd_1.4.x-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r lighttpd

```and when i did 
```

dpkg -i lighttpd_1.4.x-1_i386.deb

```Got following output
```

 dpkg -i lighttpd_1.4.x-1_i386.deb 
(Reading database ... 157434 files and directories currently installed.)
Preparing to replace lighttpd 1.4.x-1 (using lighttpd_1.4.x-1_i386.deb) ...
Unpacking replacement lighttpd ...
Setting up lighttpd (1.4.x-1) ...
Processing triggers for man-db ...

```and upon checking
```

root@tapas-laptop:~# dpkg -s lighttpd_1.4.x-1_i386.deb 
Package `lighttpd_1.4.x-1_i386.deb' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


```I mentioned above all steps there is no error any where but it is not starting also this time.

---

### Post by konsole on 2010-08-05
> **tapas_mishra said:**
> ```

root@tapas-laptop:~# dpkg -s lighttpd_1.4.x-1_i386.deb 
Package `lighttpd_1.4.x-1_i386.deb' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


```I mentioned above all steps there is no error any where but it is not starting also this time.

Try this```
dpkg -s lighttpd
```

---

### Post by tapas_mishra on 2010-08-07
Here is the output
```
root@tapas-laptop:/opt/lighttpd-1.4.x# dpkg -s lighttpd
Package: lighttpd
Status: deinstall ok config-files
Priority: optional
Section: web
Installed-Size: 944
Maintainer: Debian lighttpd maintainers <pkg-lighttpd-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1.4.26-1.1~backport1~ppa1~karmic1
Config-Version: 1.4.26-1.1~backport1~ppa1~karmic1
Provides: httpd, httpd-cgi
Depends: libattr1 (>= 2.4.41-1), libbz2-1.0, libc6 (>= 2.4), libfam0, libldap-2.4-2 (>= 2.4.7), libpcre3 (>= 7.7), libssl0.9.8 (>= 0.9.8f-5), zlib1g (>= 1:1.1.4), lsb-base (>= 3.2-14), mime-support, libterm-readline-perl-perl
Recommends: spawn-fcgi
Suggests: openssl, rrdtool, apache2-utils
Conflicts: cherokee (<= 0.6.1-1)
Conffiles:
 /etc/cron.daily/lighttpd 9d80b77e98ff86be248cc60e141d89cd
 /etc/logrotate.d/lighttpd ad52e407befda5a5dc742818d393858d
 /etc/init.d/lighttpd 40648e70997d95546bac6a3cd237c541
 /etc/lighttpd/conf-available/05-auth.conf 421219cb4a04a693e191ff6a32fa432a
 /etc/lighttpd/conf-available/10-proxy.conf 7b4265f5aed9bd2a7622580016677911
 /etc/lighttpd/conf-available/10-fastcgi.conf 9dbc734d1cfd0e8c56f82ef0ba6b7724
 /etc/lighttpd/conf-available/10-rrdtool.conf 4d4cf11dee72b4cbb51d96340958362e
 /etc/lighttpd/conf-available/10-status.conf 1c0ae0a098d5022fad8dcdf5dcae5a95
 /etc/lighttpd/conf-available/10-cgi.conf 9e475f4cb9d747b1cfea7dfe45cf9ecc
 /etc/lighttpd/conf-available/10-ssl.conf 168706fe944890fa44b74461403da731
 /etc/lighttpd/conf-available/10-userdir.conf 761e9bd64422f802c248f69d1fc504a0
 /etc/lighttpd/conf-available/README c376c00aeaa5aa71fba021b15b1bf45e
 /etc/lighttpd/conf-available/10-simple-vhost.conf cded76d5e184a21bbcf4b651f0ed745f
 /etc/lighttpd/conf-available/10-ssi.conf a0b0b83fe6060ec23e2d4e4b57a89936
 /etc/lighttpd/lighttpd.conf 26fad7baafe71f2ff3586134a7423664
Description: A fast webserver with minimal memory footprint
 lighttpd is a small webserver and fast webserver developed with
 security in mind and a lot of features.
 It has support for
   * CGI, FastCGI and SSI
   * virtual hosts
   * URL rewriting
   * authentication (plain files, htpasswd, ldap)
   * transparent content compression
   * conditional configuration
 and configuration is straight-forward and easy.
Homepage: http://www.lighttpd.net

```

---

### Post by tapas_mishra on 2010-08-07
I was able to solve the above problem.



I did all the steps from starting again.Deleted all the files which lighttpd had installed and repeated the steps as in the first post of mine.
Also I checked 

```
find / -wholename /home -prune -o -name lighttpd -print 

```
I executed the above command after make install 
the result was 

```
/usr/local/sbin/lighttpd
/opt/lighttpd-1.4.x/src/lighttpd

```
Then I created four directories 

```
/var/log/lighttpd
/var/log/lighttpd/htdocs
/var/lighttpd
/etc/lighttpd

```

The config file after you do 
```
make install

```
is in

```
/opt/lighttpd-1.4.x/doc/config/lighttpd.conf

```

The values of lighttpd.conf as above are here
[http://pastebin.com/vUwhBzuJ](http://pastebin.com/vUwhBzuJ)
If you do not wish to go through the complete file 
I only changed the following
```
var.server_root = "/var/lighttpd"

```
In the orignial file it is 
```
var.server_root = "/srv/www"

```



```
cp /opt/lighttpd-1.4.x/src/lighttpd /usr/sbin

```

Also I created a directory 
```
/etc/lighttpd/
```
and then
```
cp /opt/lighttpd-1.4.x/doc/config/lighttpd.conf /etc/lighttpd/
```


Now this time I did
```
/usr/local/sbin/lighttpd -f /opt/lighttpd-1.4.x/doc/config/lighttpd.conf

```
still it did not worked then
 

Also need to make 
```

chown -R lighttpd:lighttpd /var/lighttpd/
chown -R lighttpd:lighttpd /var/log/lighttpd/

```

Then you need to:
```
cp /opt/lighttpd-1.4.x/doc/config/modules.conf /etc/lighttpd
cp -rp /opt/lighttpd-1.4.x/doc/config/doc/config/conf.d /etc/lighttpd
```



and if I do 
```

root@tapas-laptop:~# lighttpd -f /etc/lighttpd/lighttpd.conf start

```

I do not get any error message but when I check in browser [http://localhost](http://localhost) I don't get any thing.

Then
checked if lighttpd is running:
```
ps -ef|grep lighttpd
```
and if yes, find the listening port:
```
netstat -tanpl|grep lighttpd
```

Now try to start the daemon as 

```

/usr/local/sbin/ligttpd -D -f /etc/lighttpd/lighttpd.conf

```
On your screen the cursor should blink and in browser you should get [http://localhost](http://localhost) what ever is in the document root of lighttpd.

If the step upto here does not work then check the strace log of lighttpd

in my case when I did 

```

strace /usr/local/sbin/ligttpd -D -f /etc/lighttpd/lighttpd.conf

```
I got following error
```

open("/var/log/lighttpd/access.log", O_WRONLY|O_CREAT|O_APPEND|O_LARGEFILE, 0644) = -1 EACCES (Permission denied)

```
and I saw 
```

ls -ld /var/log/lighttpd
ls -l /var/log/lighttpd/

```

I got 
```

ls -l ld /var/log/lighttpd/
ls: cannot access ld: No such file or directory
/var/log/lighttpd/:
total 4
-rw-rw-rw- 1 root root 2618 2010-08-07 22:08 error.log

```
then I did 
```

/usr/local/sbin/lighttpd -D -f /etc/lighttpd/lighttpd.conf

```
the cursor blinked and this time I could see it working.
I am having problem with an init script for this to work.
Let me know if you are still reading this thread.

---

### Post by konsole on 2010-08-09
It sounds like you've sorted everything apart from a startup script.

There should be a rc.lighttpd script in /usr/share/doc/lighttpd/doc/ which you copy to /etc/init.d and run ```
update-rc.d lighttpd defaults
```If you can't find one there let me know and I'll post mine.

You may need to make some changes to it as you've changed directories from the default.

Good Luck.

---

