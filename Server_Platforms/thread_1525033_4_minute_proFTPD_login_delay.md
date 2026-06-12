---
title: "4 minute proFTPD login delay"
date: 2010-07-06
forum: Server Platforms
---

### Post by DarkRanger on 2010-07-06
Hi all,

I recently got a VPS and installed all my apps on it. ProFTPD worked fine for a while but then suddenly started having a 4 minute login delay.

Here is the log:

```
Jul 06 09:10:23 ubuntu.3bm.co.za proftpd[7729] ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]): FTP session opened.
Jul 06 07:14:40 ubuntu.3bm.co.za proftpd[7729] ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]): Preparing to chroot to directory '/var/www'
Jul 06 07:14:40 ubuntu.3bm.co.za proftpd[7729] ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]): USER uploadUser: Login successful.
Jul 06 07:21:01 ubuntu.3bm.co.za proftpd[7729] ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]): FTP session closed.
```

I have been searching for the solution since last month. Google doesn't help much with this as it only gives solutions on IdentLookups off and ReverseDNS off which are both off. After the login, the transfer of files are fast and there is no delay.

Here is my config file for proFTPD:

```
Include /etc/proftpd/modules.conf
UseIPv6				on
IdentLookups			off
AllowOverwrite			on
ServerName			"Debian"
ServerType			standalone
DeferWelcome			on
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off
TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200
DisplayChdir               	.message
ListOptions                	"-l"
DenyFilter			\*.*/
RequireValidShell 		off
RootLogin 			off
UseFtpUsers			off
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log
DefaultRoot			/var/www
DefaultRoot			~
Port				21
MaxInstances			30
User				proftpd
Group				nogroup
Umask				022  022
AllowOverwrite			on
UseReverseDNS			off
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>
<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
</IfModule>
<IfModule mod_delay.c>
DelayEngine off
</IfModule>
<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>
<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>
<Global>
IdentLookups off
ServerIdent on "FTP Server ready."
</Global>
```

Is there anything wrong with this? Any idea how I can remove (or atleast reduce) the delay?

---

### Post by DarkRanger on 2010-07-06
anyone?

---

### Post by DarkRanger on 2010-07-07
Okay so after endless struggling with this, I decided to run through the whole debug again and post a step by step command result here. Maybe someone will be able to help me.

**Step 1 - Know the version**
Command:
```
proftpd -V
```
Result:
```
Compile-time Settings:
  Version: 1.3.2c (maint)
  Platform: LINUX
  Built: Tue Dec 22 14:02:40 UTC 2009
  Built With:
    configure  '--prefix=/usr' '--with-includes=/usr/include/postgresql:/usr/include/mysql' '--mandir=/usr/share/man' '--sysconfdir=/etc/proftpd' '--localstatedir=/var/run' '--libexecdir=/usr/lib/proftpd' '--enable-sendfile' '--enable-facl' '--enable-dso' '--enable-autoshadow' '--enable-ctrls' '--with-modules=mod_readme' '--enable-ipv6' '--enable-nls' '--build' 'x86_64-linux-gnu' '--with-shared=mod_unique_id:mod_site_misc:mod_load:mod_ban:mod_quotatab:mod_sql:mod_sql_mysql:mod_sql_postgres:mod_sql_sqlite:mod_sql_odbc:mod_dynmasq:mod_quotatab_sql:mod_ldap:mod_quotatab_ldap:mod_ratio:mod_tls:mod_rewrite:mod_radius:mod_wrap:mod_wrap2:mod_wrap2_file:mod_wrap2_sql:mod_quotatab_file:mod_quotatab_radius:mod_facl:mod_ctrls_admin:mod_ifsession' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-O2 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_OPENSSL -DUSE_LDAP_TLS ' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'

  CFLAGS: -O2 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_OPENSSL -DUSE_LDAP_TLS  -Wall
  LDFLAGS: -L$(top_srcdir)/lib -Wl,-Bsymbolic-functions
  LIBS: -lacl  -lssl -lcrypto -lcap  -lpam -lsupp -lcrypt

  Files:
    Configuration File:
      /etc/proftpd/proftpd.conf
    Pid File:
      /var/run/proftpd.pid
    Scoreboard File:
      /var/run/proftpd/proftpd.scoreboard
    Header Directory:
      /usr/include/proftpd
    Shared Module Directory:
      /usr/lib/proftpd

  Features:
    + Autoshadow support
    + Controls support
    + curses support
    - Developer support
    + DSO support
    + IPv6 support
    + Largefile support
    - Lastlog support
    + ncurses support
    + NLS support
    + OpenSSL support
    + POSIX ACL support
    + Shadow file support
    + Sendfile support
    + Trace support

  Tunable Options:
    PR_TUNABLE_BUFFER_SIZE = 1024
    PR_TUNABLE_GLOBBING_MAX = 8
    PR_TUNABLE_HASH_TABLE_SIZE = 40
    PR_TUNABLE_NEW_POOL_SIZE = 512
    PR_TUNABLE_SCOREBOARD_BUFFER_SIZE = 80
    PR_TUNABLE_SCOREBOARD_SCRUB_TIMER = 30
    PR_TUNABLE_SELECT_TIMEOUT = 30
    PR_TUNABLE_TIMEOUTIDENT = 10
    PR_TUNABLE_TIMEOUTIDLE = 600
    PR_TUNABLE_TIMEOUTLINGER = 30
    PR_TUNABLE_TIMEOUTLOGIN = 300
    PR_TUNABLE_TIMEOUTNOXFER = 300
    PR_TUNABLE_TIMEOUTSTALLED = 3600
    PR_TUNABLE_XFER_SCOREBOARD_UPDATES = 10
```
Command:
```
proftpd -vv
```
Result:
```
 - warning: handling possibly truncated configuration data at line 55 of '/etc/proftpd/proftpd.conf'
ProFTPD Version: 1.3.2c (maint)
  Scoreboard Version: 01040002
  Built: Tue Dec 22 14:02:40 UTC 2009

Loaded modules:
  mod_ifsession/1.0
  mod_dynmasq/0.2.1
  mod_wrap2_file/1.2
  mod_wrap2/2.0.6
  mod_ban/0.5.3
  mod_load/1.0.1
  mod_rewrite/0.7
  mod_wrap.c
  mod_quotatab_radius.c
  mod_quotatab_file.c
  mod_quotatab/1.3.0
  mod_radius/0.9
  mod_tls/2.2.2
  mod_ctrls_admin/0.9.5
  mod_lang/0.9
  mod_ctrls/0.9.4
  mod_cap/1.0
  mod_readme.c
  mod_auth_pam/1.1
  mod_ident/1.0
  mod_dso/0.4
  mod_facts/0.1
  mod_delay/0.6
  mod_site.c
  mod_log.c
  mod_ls.c
  mod_auth.c
  mod_auth_file/0.8.3
  mod_auth_unix.c
  mod_xfer.c
  mod_core.c
```
Step 2 - Know The Modules
Command:
```
proftpd -l
```
Result:
```
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_facts.c
  mod_dso.c
  mod_ident.c
  mod_auth_pam.c
  mod_readme.c
  mod_cap.c
  mod_ctrls.c
  mod_lang.c
```
**Step 3 - Perform Configuration Check**
Command:
```
proftpd -td5
```
Result:
```
Checking syntax of configuration file
 - using TCP receive buffer size of 87380 bytes
 - using TCP send buffer size of 16384 bytes
 - mod_tls/2.2.2: using OpenSSL 0.9.8k 25 Mar 2009
 - disabling runtime support for IPv6 connections
 - DenyFilter: compiling deny regex '\*.*/'
 - <IfModule>: using 'mod_dynmasq.c' section at line 31
 - <IfModule>: using 'mod_quotatab.c' section at line 34
 - <IfModule>: skipping 'mod_ratio.c' section at line 37
 - <IfModule>: using 'mod_delay.c' section at line 40
 - <IfModule>: using 'mod_ctrls.c' section at line 43
 - <IfModule>: using 'mod_ctrls_admin.c' section at line 50
 - warning: handling possibly truncated configuration data at line 55 of '/etc/proftpd/proftpd.conf'
ubuntu.3bm.co.za -
ubuntu.3bm.co.za - Config for VCE National Server:
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - AllowOverwrite
ubuntu.3bm.co.za - DeferWelcome
ubuntu.3bm.co.za - DefaultServer
ubuntu.3bm.co.za - ShowSymlinks
ubuntu.3bm.co.za - TimeoutNoTransfer
ubuntu.3bm.co.za - TimeoutStalled
ubuntu.3bm.co.za - TimeoutIdle
ubuntu.3bm.co.za - DisplayLogin
ubuntu.3bm.co.za - DisplayChdir
ubuntu.3bm.co.za - ListOptions
ubuntu.3bm.co.za - DenyFilter
ubuntu.3bm.co.za - ExtendedLog
ubuntu.3bm.co.za - TransferLog
ubuntu.3bm.co.za - DefaultRoot
ubuntu.3bm.co.za - DefaultRoot
ubuntu.3bm.co.za - UserID
ubuntu.3bm.co.za - UserName
ubuntu.3bm.co.za - GroupID
ubuntu.3bm.co.za - GroupName
ubuntu.3bm.co.za - Umask
ubuntu.3bm.co.za - DirUmask
ubuntu.3bm.co.za - AllowOverwrite
ubuntu.3bm.co.za - QuotaEngine
ubuntu.3bm.co.za - DelayEngine
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - ServerIdent
ubuntu.3bm.co.za - mod_lang/0.9: using C messages
ubuntu.3bm.co.za - mod_lang/0.9: binding to text domain 'proftpd' using locale path '/usr/share/locale'
ubuntu.3bm.co.za - mod_lang/0.9: using locale files in '/usr/share/locale'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'ru': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'ko_KR': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'bg_BG': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'en_US': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'zh_TW': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'zh_CN': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'it': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'fr_FR': not supported by setlocale(3); see `locale -a'
Syntax check complete.
ubuntu.3bm.co.za - mod_ban/0.5.3: error detaching shm: Invalid argument
ubuntu.3bm.co.za - mod_ban/0.5.3: error removing shmid -1: Invalid argument
```
**Step 4 - Collect Debug Information**
Command:
```
proftpd -nd6
```
Result:
```
 - using TCP receive buffer size of 87380 bytes
 - using TCP send buffer size of 16384 bytes
 - mod_tls/2.2.2: using OpenSSL 0.9.8k 25 Mar 2009
 - disabling runtime support for IPv6 connections
 - DenyFilter: compiling deny regex '\*.*/'
 - <IfModule>: using 'mod_dynmasq.c' section at line 31
 - <IfModule>: using 'mod_quotatab.c' section at line 34
 - <IfModule>: skipping 'mod_ratio.c' section at line 37
 - <IfModule>: using 'mod_delay.c' section at line 40
 - <IfModule>: using 'mod_ctrls.c' section at line 43
 - <IfModule>: using 'mod_ctrls_admin.c' section at line 50
 - warning: handling possibly truncated configuration data at line 55 of '/etc/proftpd/proftpd.conf'
ubuntu.3bm.co.za -
ubuntu.3bm.co.za - Config for VCE National Server:
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - AllowOverwrite
ubuntu.3bm.co.za - DeferWelcome
ubuntu.3bm.co.za - DefaultServer
ubuntu.3bm.co.za - ShowSymlinks
ubuntu.3bm.co.za - TimeoutNoTransfer
ubuntu.3bm.co.za - TimeoutStalled
ubuntu.3bm.co.za - TimeoutIdle
ubuntu.3bm.co.za - DisplayLogin
ubuntu.3bm.co.za - DisplayChdir
ubuntu.3bm.co.za - ListOptions
ubuntu.3bm.co.za - DenyFilter
ubuntu.3bm.co.za - ExtendedLog
ubuntu.3bm.co.za - TransferLog
ubuntu.3bm.co.za - DefaultRoot
ubuntu.3bm.co.za - DefaultRoot
ubuntu.3bm.co.za - UserID
ubuntu.3bm.co.za - UserName
ubuntu.3bm.co.za - GroupID
ubuntu.3bm.co.za - GroupName
ubuntu.3bm.co.za - Umask
ubuntu.3bm.co.za - DirUmask
ubuntu.3bm.co.za - AllowOverwrite
ubuntu.3bm.co.za - QuotaEngine
ubuntu.3bm.co.za - DelayEngine
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - IdentLookups
ubuntu.3bm.co.za - ServerIdent
ubuntu.3bm.co.za - mod_lang/0.9: using C messages
ubuntu.3bm.co.za - mod_lang/0.9: binding to text domain 'proftpd' using locale path '/usr/share/locale'
ubuntu.3bm.co.za - mod_lang/0.9: using locale files in '/usr/share/locale'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'ru': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'ko_KR': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'bg_BG': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'en_US': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'zh_TW': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'zh_CN': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'it': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - mod_lang/0.9: skipping possible language 'fr_FR': not supported by setlocale(3); see `locale -a'
ubuntu.3bm.co.za - ProFTPD 1.3.2c (maint) (built Tue Dec 22 14:02:40 UTC 2009) standalone mode STARTUP
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - session requested from client in unknown class
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - mod_lang/0.9: using C messages
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - mod_lang/0.9: using C messages
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - mod_cap/1.0: adding CAP_AUDIT_WRITE capability
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - mod_ident/1.0: ident lookup disabled
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - connected - local  : 41.72.132.170:21
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - connected - remote : 41.134.44.209:49866
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - FTP session opened.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'USER uploadUser' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'USER uploadUser' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'USER uploadUser' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'USER uploadUser' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'USER uploadUser' to mod_delay
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'USER uploadUser' to mod_auth
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'USER uploadUser' to mod_auth << Waits around 2 minutes
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'USER uploadUser' to mod_delay
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'USER uploadUser' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_wrap2
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_ban
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_wrap
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_radius
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_delay
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASS (hidden)' to mod_auth
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'PASS (hidden)' to mod_auth << Waits around 2 minutes
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - user 'uploadUser' authenticated by mod_auth_pam.c
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) -
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - Config for VCE National Server:
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - IdentLookups
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - IdentLookups
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - AllowOverwrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DeferWelcome
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DefaultServer
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - ShowSymlinks
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - TimeoutNoTransfer
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - TimeoutStalled
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - TimeoutIdle
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DisplayLogin
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DisplayChdir
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - ListOptions
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DenyFilter
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - ExtendedLog
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - TransferLog
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DefaultRoot
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DefaultRoot
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - UserID
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - UserName
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - GroupID
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - GroupName
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - Umask
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DirUmask
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - AllowOverwrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - QuotaEngine
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - DelayEngine
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - IdentLookups
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - IdentLookups
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - ServerIdent
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - CURRENT-CLIENTS
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - USER
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - opening TransferLog '/var/log/xferlog'
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - Preparing to chroot to directory '/var/www'
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - Environment successfully chroot()ed
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_ifsession
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_wrap2
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_quotatab
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_radius
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_cap
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - mod_cap/1.0: capabilities '= cap_net_bind_service,cap_audit_write+ep'
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_readme
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_delay
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_ls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_auth
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - unable to display DisplayLogin file 'welcome.msg': No such file or directory
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_xfer
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching POST_CMD command 'PASS (hidden)' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'PASS (hidden)' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'PASS (hidden)' to mod_auth
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - USER uploadUser: Login successful.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'SYST' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'SYST' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'SYST' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'SYST' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'SYST' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'SYST' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'FEAT' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'FEAT' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'FEAT' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'FEAT' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'FEAT' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'FEAT' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS UTF8 ON' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS UTF8 ON' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS UTF8 ON' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS UTF8 ON' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'OPTS UTF8 ON' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS_UTF8 ON' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS_UTF8 ON' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS_UTF8 ON' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'OPTS_UTF8 ON' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'OPTS_UTF8 ON' to mod_lang
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - mod_lang/0.9: enabling use of UTF8 encoding as per client's request
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'OPTS_UTF8 ON' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'OPTS UTF8 ON' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PWD' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PWD' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PWD' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PWD' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'PWD' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'PWD' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'TYPE I' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'TYPE I' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'TYPE I' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'TYPE I' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'TYPE I' to mod_xfer
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'TYPE I' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASV' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASV' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASV' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'PASV' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'PASV' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - Entering Passive Mode (41,72,132,170,163,174).
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'PASV' to mod_log
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'MLSD' to mod_rewrite
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'MLSD' to mod_tls
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'MLSD' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching PRE_CMD command 'MLSD' to mod_core
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching CMD command 'MLSD' to mod_facts
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - passive data connection opened - local  : 41.72.132.170:41902
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - passive data connection opened - remote : 41.134.44.209:49880
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/travel', fullpath = '/var/www/travel'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/ldaptest.php', fullpath = '/var/www/ldaptest.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/qms', fullpath = '/var/www/qms'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/finances', fullpath = '/var/www/finances'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/userinfo.php', fullpath = '/var/www/userinfo.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/input_files', fullpath = '/var/www/input_files'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/menu', fullpath = '/var/www/menu'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/Thumbs.db', fullpath = '/var/www/Thumbs.db'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/images', fullpath = '/var/www/images'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/projects', fullpath = '/var/www/projects'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/iboss', fullpath = '/var/www/iboss'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/deltainfrastructure', fullpath = '/var/www/deltainfrastructure'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/osh', fullpath = '/var/www/osh'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/style.css', fullpath = '/var/www/style.css'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/monthly_stats', fullpath = '/var/www/monthly_stats'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/social', fullpath = '/var/www/social'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/world_cup', fullpath = '/var/www/world_cup'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/getInfo.php', fullpath = '/var/www/getInfo.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/home.php', fullpath = '/var/www/home.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/human_resources', fullpath = '/var/www/human_resources'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/security_code', fullpath = '/var/www/security_code'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/phones', fullpath = '/var/www/phones'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/start.php', fullpath = '/var/www/start.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/news', fullpath = '/var/www/news'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/dynam_code', fullpath = '/var/www/dynam_code'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/', fullpath = '/var/www/'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/info.php', fullpath = '/var/www/info.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/it', fullpath = '/var/www/it'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/suppliers', fullpath = '/var/www/suppliers'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/index.php', fullpath = '/var/www/index.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/phpinfo.php', fullpath = '/var/www/phpinfo.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/calender', fullpath = '/var/www/calender'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/backup.php', fullpath = '/var/www/backup.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/favicon.ico', fullpath = '/var/www/favicon.ico'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/links', fullpath = '/var/www/links'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/marketing', fullpath = '/var/www/marketing'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/info', fullpath = '/var/www/info'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - in dir_check_full(): path = '/serverinfo.php', fullpath = '/var/www/serverinfo.php'.
ubuntu.3bm.co.za (41.134.44.209[41.134.44.209]) - dispatching LOG_CMD command 'MLSD' to mod_log
```

In the above results I have marked exactly where the delay occurs. Hope this helps...

---

### Post by DJYoshaBYD on 2010-07-07
to be honest, i had nothing but problems running helllllaaaaa different FTP servers on my server.. the one that worked was vsftpd

vsftpd was very easy to configure, i never had any timeout issues, and its nice and lightweight.. no GUI, but hey.. who needs one? lol.

give that a shot.. make sure you uninstall proFTPD, then install vsftpd.. for me, its the easiest solution.. It also has lots of security features in it.. i dig it.. it works for what i need..

---

### Post by Hety on 2010-07-07
I second that. It takes approximately 1/5 minutes to install and config it for basic usage. And its fast as hell.

---

### Post by DJYoshaBYD on 2010-07-07
for reals.. its the easiest one I have used, and i have tried them all, multiple times.. lol..

you install it, start it, port forward (if needed), log in.. thats it.. configs are easy as well.

---

