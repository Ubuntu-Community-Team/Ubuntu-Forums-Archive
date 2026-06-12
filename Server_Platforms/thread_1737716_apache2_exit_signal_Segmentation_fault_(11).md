---
title: "apache2: exit signal Segmentation fault (11)"
date: 2011-04-23
forum: Server Platforms
---

### Post by zelegolas on 2011-04-23
Hi

Does anyone can help me?

On my server I installed:
```
[Sat Apr 23 11:56:07 2011] [notice] Apache/2.2.16 (Ubuntu) DAV/2 SVN/1.6.12 mod_gnutls/0.5.6 PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch mod_python/3.3.1 Python/2.6.6 configured -- resuming normal operations
```

When I try to load a web page it takes quite some time. And if I look at the Apache logs I have a lot of line like this:
```
[Sat Apr 23 11:56:53 2011] [notice] child pid 1466 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Sat Apr 23 11:59:11 2011] [notice] child pid 1465 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Sat Apr 23 11:59:19 2011] [notice] child pid 1463 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Sat Apr 23 11:59:19 2011] [notice] child pid 1464 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Sat Apr 23 11:59:19 2011] [notice] child pid 1467 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Sat Apr 23 11:59:19 2011] [notice] child pid 1469 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
```

If I look at the core dump with gdb this is what I have:
```
# gdb /usr/sbin/apache2 -c /tmp/apache2-gdb-dump/core
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/sbin/apache2...done.
[New Thread 1801]

warning: Can't read pathname for load map: Input/output error.
Reading symbols from /lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /usr/lib/libaprutil-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libaprutil-1.so.0
Reading symbols from /usr/lib/libapr-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libapr-1.so.0
Reading symbols from /lib/libpthread.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libpthread.so.0
Reading symbols from /lib/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/libc.so.6
Reading symbols from /lib/libuuid.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libuuid.so.1
Reading symbols from /lib/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/librt.so.1
Reading symbols from /lib/libcrypt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libcrypt.so.1
Reading symbols from /lib/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libdl.so.2
Reading symbols from /lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libexpat.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libdb-4.8.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdb-4.8.so
Reading symbols from /lib/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libnsl.so.1
Reading symbols from /lib/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libnss_compat.so.2
Reading symbols from /lib/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libnss_nis.so.2
Reading symbols from /lib/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libnss_files.so.2
Reading symbols from /usr/lib/apr-util-1/apr_dbm_db-1.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apr-util-1/apr_dbm_db-1.so
Reading symbols from /usr/lib/apache2/modules/mod_alias.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_alias.so
Reading symbols from /usr/lib/apache2/modules/mod_auth_basic.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_auth_basic.so
Reading symbols from /usr/lib/apache2/modules/mod_auth_digest.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_auth_digest.so
Reading symbols from /usr/lib/apache2/modules/mod_authn_file.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_authn_file.so
Reading symbols from /usr/lib/apache2/modules/mod_authz_default.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_authz_default.so
Reading symbols from /usr/lib/apache2/modules/mod_authz_groupfile.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_authz_groupfile.so
Reading symbols from /usr/lib/apache2/modules/mod_authz_host.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_authz_host.so
Reading symbols from /usr/lib/apache2/modules/mod_authz_user.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_authz_user.so
Reading symbols from /usr/lib/apache2/modules/mod_autoindex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_autoindex.so
Reading symbols from /usr/lib/apache2/modules/mod_cgi.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_cgi.so
Reading symbols from /usr/lib/apache2/modules/mod_dav.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_dav.so
Reading symbols from /usr/lib/apache2/modules/mod_dav_fs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_dav_fs.so
Reading symbols from /usr/lib/apache2/modules/mod_dav_svn.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_dav_svn.so
Reading symbols from /usr/lib/libsvn_repos-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_repos-1.so.1
Reading symbols from /usr/lib/libsvn_fs-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_fs-1.so.1
Reading symbols from /usr/lib/libsvn_delta-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_delta-1.so.1
Reading symbols from /usr/lib/libsvn_subr-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_subr-1.so.1
Reading symbols from /usr/lib/libsvn_fs_fs-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_fs_fs-1.so.1
Reading symbols from /usr/lib/libsvn_fs_base-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_fs_base-1.so.1
Reading symbols from /usr/lib/libsvn_fs_util-1.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsvn_fs_util-1.so.1
Reading symbols from /usr/lib/libldap_r-2.4.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libldap_r-2.4.so.2
Reading symbols from /usr/lib/liblber-2.4.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/liblber-2.4.so.2
Reading symbols from /lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libz.so.1
Reading symbols from /usr/lib/libsqlite3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsqlite3.so.0
Reading symbols from /lib/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libresolv.so.2
Reading symbols from /usr/lib/libsasl2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsasl2.so.2
Reading symbols from /usr/lib/libgssapi_krb5.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgssapi_krb5.so.2
Reading symbols from /usr/lib/libgnutls.so.26...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnutls.so.26
Reading symbols from /usr/lib/libkrb5.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkrb5.so.3
Reading symbols from /usr/lib/libk5crypto.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libk5crypto.so.3
Reading symbols from /lib/libcom_err.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libcom_err.so.2
Reading symbols from /usr/lib/libkrb5support.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkrb5support.so.0
Reading symbols from /lib/libkeyutils.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libkeyutils.so.1
Reading symbols from /usr/lib/libtasn1.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtasn1.so.3
Reading symbols from /lib/libgcrypt.so.11...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcrypt.so.11
Reading symbols from /lib/libgpg-error.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libgpg-error.so.0
Reading symbols from /usr/lib/apache2/modules/mod_authz_svn.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_authz_svn.so
Reading symbols from /usr/lib/apache2/modules/mod_deflate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_deflate.so
Reading symbols from /usr/lib/apache2/modules/mod_dir.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_dir.so
Reading symbols from /usr/lib/apache2/modules/mod_env.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_env.so
Reading symbols from /usr/lib/apache2/modules/mod_gnutls.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_gnutls.so
Reading symbols from /usr/lib/apache2/modules/mod_mime.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_mime.so
Reading symbols from /usr/lib/apache2/modules/mod_negotiation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_negotiation.so
Reading symbols from /usr/lib/apache2/modules/libphp5.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/libphp5.so
Reading symbols from /lib/libssl.so.0.9.8...(no debugging symbols found)...done.
Loaded symbols for /lib/libssl.so.0.9.8
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /lib/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/libm.so.6
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /lib/libcrypto.so.0.9.8...(no debugging symbols found)...done.
Loaded symbols for /lib/libcrypto.so.0.9.8
Reading symbols from /usr/lib/apache2/modules/mod_proxy.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_proxy.so
Reading symbols from /usr/lib/apache2/modules/mod_python.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_python.so
Reading symbols from /usr/lib/libpython2.6.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpython2.6.so.1.0
Reading symbols from /lib/libutil.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libutil.so.1
Reading symbols from /usr/lib/apache2/modules/mod_reqtimeout.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_reqtimeout.so
Reading symbols from /usr/lib/apache2/modules/mod_rewrite.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_rewrite.so
Reading symbols from /usr/lib/apache2/modules/mod_setenvif.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_setenvif.so
Reading symbols from /usr/lib/apache2/modules/mod_status.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_status.so
Reading symbols from /usr/lib/apache2/modules/mod_vhost_alias.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_vhost_alias.so
Reading symbols from /usr/lib/php5/20090626+lfs/gd.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/php5/20090626+lfs/gd.so
Reading symbols from /usr/lib/libgd.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgd.so.2
Reading symbols from /usr/lib/libt1.so.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libt1.so.5
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXpm.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXpm.so.4
Reading symbols from /lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libpng12.so.0
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/php5/20090626+lfs/mcrypt.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/php5/20090626+lfs/mcrypt.so
Reading symbols from /usr/lib/libmcrypt.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmcrypt.so.4
Reading symbols from /usr/lib/php5/20090626+lfs/mysql.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/php5/20090626+lfs/mysql.so
Reading symbols from /usr/lib/libmysqlclient_r.so.16...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmysqlclient_r.so.16
Reading symbols from /usr/lib/php5/20090626+lfs/mysqli.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/php5/20090626+lfs/mysqli.so
Reading symbols from /usr/lib/php5/20090626+lfs/pdo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/php5/20090626+lfs/pdo.so
Reading symbols from /usr/lib/php5/20090626+lfs/pdo_mysql.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/php5/20090626+lfs/pdo_mysql.so
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Core was generated by `/usr/sbin/apache2 -k start'.
Program terminated with signal 11, Segmentation fault.
#0  0xb6fbcecd in _gnutls_recv_int () from /usr/lib/libgnutls.so.26
```

I feel that it is gnutls crash but I do not see what I can do to fix it :confused:

Any ideas???

---

### Post by iglablues on 2011-04-25
Interestingly enough, I'm struggling with the same thing, although your system appears to at least have been set up with core dumps enabled which is nice. Took me forever to get them working. 

I think in order to truly know what's going on, you have to actually install the debugging symbols. Did you run the bt or bt full command from within gdb? I don't see that in the output so I was curious, because my understanding is that that's the next step in order to find the actual faulting module, but I'm not sure if you'll get any useful info without debugging tools installed. Unfortunately, I tried to install the apache2-dbg package but it's not in the repository and I'm still trying to work out how to get it. 

Have a look at /usr/share/doc/apache2.2-common/README.backtrace for some info.

---

### Post by zelegolas on 2011-04-25
> **iglablues said:**
> Interestingly enough, I'm struggling with the same thing, although your system appears to at least have been set up with core dumps enabled which is nice. Took me forever to get them working. 

I think in order to truly know what's going on, you have to actually install the debugging symbols. Did you run the bt or bt full command from within gdb? I don't see that in the output so I was curious, because my understanding is that that's the next step in order to find the actual faulting module, but I'm not sure if you'll get any useful info without debugging tools installed. Unfortunately, I tried to install the apache2-dbg package but it's not in the repository and I'm still trying to work out how to get it. 

Have a look at /usr/share/doc/apache2.2-common/README.backtrace for some info.

I already took a few times to install some debug file but it doesn't help a lot and I don't want install all the debug files for all the libraries.

Anyway I fixed the pb: I disable GnuTLS and enable SSL module. Now everything is working well.

Conclusion: It's really an issue with GnuTLS. I sent to them an email but I didn't receive any answers.

---

### Post by Mercedes_Cc on 2011-08-11
Hola como estan: 
Les escribo porque tengo un problema parecido y aun no encuentro la solución. El problema es el siguiente.

Tengo un aplicativo Web corriendo en apache 2 dentro de un Server Centos, localmente (LAN) puedo  acceder y procesar información, pero cuando accedo desde la WAN logro  entrar al sistema pero al momento de procesar la información ocurre un  error.
child pid 3791 exit signal segmentation fault(11)
child pid 28458 exit signal segmentation fault(11)
child pid 12630 exit signal segmentation fault(11)

ah un dato más cuando usaba el microtik para el firewall no sucedia esto pero ahora que uso el pfsense sucede el problema que les digo.

Ayúdenme por favorrrrrrrrr

---

### Post by frappyjohn on 2011-09-01
I have had this problem also after migrating a production server from Redhat ES 5 to Ubuntu 10.4 and the LAMP stack. It has occurred erratically after making seemingly innocuous edits to production programs.

So far I have "solved" or at least eliminated each occurrence, but not after a lot of hair pulling. The problem seems to be associated with undefined variables. By consulting my Apache/PHP log for "PHP Notices" (!) of undefined variables which occurred prior to the segmentation fault and eliminating them, I managed to solve the problem tonight, at least for the time being. 

Pay attention to undefined variables which are used in function calls (e.g. substr()) and to undefined indirect variables (e.g. ${$MyUndefinedVariable}).

Still, this appears to be a PHP bug since the segmentation fault is occurring without PHP first throwing an error.

---

### Post by atz6975 on 2012-10-09
Sorry to resurect this but I'm struggling to have coredumps produced on segfaults.
I've setup the Coredumpdirectory apache directive but no dump.

My understanding of documentation is that Apache2 simply requires this directive to create a coredump.

Do I also need to change ulimit for www-data?
In that case I would assume (as root):
su www-data
ulimit -c unlimited <-----change 0 coredump(blocks) to unlimited
exit
service apache2 restart  <----do I need this

Thanks for your help.

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

