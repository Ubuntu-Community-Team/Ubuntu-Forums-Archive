---
title: "Ubuntu 9.10 / Xampp - error while loading shared libraries: liblptxn.so"
date: 2009-12-15
forum: Server Platforms
---

### Post by gknight25 on 2009-12-15
Hey guys,

Current setup:

Ubuntu 9.10 Desktop Edition
Xampp Installed
Website in question has Html, Php, Cgi, Mysql going on.  I have been able to link the database, communicate with it through PHP and some of the functions the site has.

However ------>

When for instance the website calls login.cgi    or any .cgi for that matter, it throws up a server error 500... Naturally my .conf  was incorrectly pointing to the wrong directories and was not allowing it. So i changed all that, and went ahead and tried again. Then it was server permission issues, which i then resolved. 

So when i got that finished, the error log started throwing error messages like :
error while loading shared libraries: liblptxn.so

and a couple of others. i was able to find 32-bit libraries for all of them except this one. I google it, and nothing comes up. 

am i missions something? the test-cgi  in cgi-bin works fine, including the /xampp/phpinfo()  and all that.


I have attached my error log / httpd.conf file.

error log:

>  Dec 15 12:47:27 2009] [error] [client 127.0.0.1] (13)Permission denied: exec of '/opt/lampp/htdocs/admin/add_to_store.cgi' failed, referer: [http://127.0.0.1/index.php](http://127.0.0.1/index.php)
[Tue Dec 15 12:47:27 2009] [error] [client 127.0.0.1] Premature end of script headers: add_to_store.cgi, referer: [http://127.0.0.1/index.php](http://127.0.0.1/index.php)
[Tue Dec 15 12:47:42 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/index_old.php](http://127.0.0.1/index_old.php)
[Tue Dec 15 12:47:49 2009] [error] [client 127.0.0.1] (13)Permission denied: exec of '/opt/lampp/htdocs/admin/order_printing.cgi' failed, referer: [http://127.0.0.1/index_old.php](http://127.0.0.1/index_old.php)
[Tue Dec 15 12:47:49 2009] [error] [client 127.0.0.1] Premature end of script headers: order_printing.cgi, referer: [http://127.0.0.1/index_old.php](http://127.0.0.1/index_old.php)
[Tue Dec 15 12:49:22 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/index.php](http://127.0.0.1/index.php)
[Tue Dec 15 12:49:27 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/admin/usage, referer: [http://127.0.0.1/index.php](http://127.0.0.1/index.php)
[Tue Dec 15 12:54:42 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/index.chi
[Tue Dec 15 12:54:46 2009] [error] [client 127.0.0.1] (13)Permission denied: exec of '/opt/lampp/htdocs/index.cgi' failed
[Tue Dec 15 12:54:46 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 12:54:56 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/index.php](http://127.0.0.1/index.php)
[Tue Dec 15 12:55:03 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:55:05 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:55:32 2009] [error] [client 127.0.0.1] PHP Warning:  move_uploaded_file(/home/scripeasy/public_html/myaccount/games_selected.png) [<a href='function.move-uploaded-file'>function.move-uploaded-file</a>]: failed to open stream: No such file or directory in /opt/lampp/htdocs/admin/index.php on line 165, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:55:32 2009] [error] [client 127.0.0.1] PHP Warning:  move_uploaded_file() [<a href='function.move-uploaded-file'>function.move-uploaded-file</a>]: Unable to move '/tmp/phpgd6IhH' to '/home/scripeasy/public_html/myaccount/games_selected.png' in /opt/lampp/htdocs/admin/index.php on line 165, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:55:32 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:55:49 2009] [error] [client 127.0.0.1] (13)Permission denied: exec of '/opt/lampp/htdocs/admin/order_printing.cgi' failed, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:55:49 2009] [error] [client 127.0.0.1] Premature end of script headers: order_printing.cgi, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 12:57:24 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/admin/order_printing.cgi: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
[Tue Dec 15 12:57:24 2009] [error] [client 127.0.0.1] Premature end of script headers: order_printing.cgi
[Tue Dec 15 12:57:25 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/admin/order_printing.cgi: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
[Tue Dec 15 12:57:25 2009] [error] [client 127.0.0.1] Premature end of script headers: order_printing.cgi
[Tue Dec 15 12:58:03 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
[Tue Dec 15 12:58:03 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:01:38 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: libmysqlclient.so.15: wrong ELF class: ELFCLASS64
[Tue Dec 15 13:01:38 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:02:20 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: libmysqlclient.so.15: wrong ELF class: ELFCLASS64
[Tue Dec 15 13:02:20 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:10:57 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: libmysqlclient.so.15: wrong ELF class: ELFCLASS64
[Tue Dec 15 13:10:57 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:15:33 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: libmysqlclient.so.15: wrong ELF class: ELFCLASS64
[Tue Dec 15 13:15:33 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:19:12 2009] [notice] caught SIGTERM, shutting down
[Tue Dec 15 13:19:22 2009] [notice] suEXEC mechanism enabled (wrapper: /opt/lampp/bin/suexec)
[Tue Dec 15 13:19:22 2009] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Dec 15 13:19:22 2009] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Tue Dec 15 13:19:22 2009] [notice] Digest: generating secret for digest authentication ...
[Tue Dec 15 13:19:22 2009] [notice] Digest: done
[Tue Dec 15 13:19:23 2009] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Dec 15 13:19:23 2009] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Tue Dec 15 13:19:23 2009] [notice] Apache/2.2.12 (Unix) DAV/2 mod_ssl/2.2.12 OpenSSL/0.9.8k PHP/5.3.0 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
[Tue Dec 15 13:19:56 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: libiodbc.so.2: cannot open shared object file: No such file or directory
[Tue Dec 15 13:19:56 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:23:43 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory
[Tue Dec 15 13:23:43 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:28:11 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: /usr/lib/liblptxn.so: invalid ELF header
[Tue Dec 15 13:28:11 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:36:47 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: /usr/lib/liblptxn.so: invalid ELF header
[Tue Dec 15 13:36:47 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:37:39 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory
[Tue Dec 15 13:37:39 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 13:39:13 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 13:39:22 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/strategicpartners.htm, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Tue Dec 15 14:04:39 2009] [error] Unrecognized character \\x7F in column 178 at /opt/lampp/htdocs/agent_app.pl line 1.\n
[Tue Dec 15 14:21:45 2009] [notice] caught SIGTERM, shutting down
[Tue Dec 15 14:22:56 2009] [notice] suEXEC mechanism enabled (wrapper: /opt/lampp/bin/suexec)
[Tue Dec 15 14:22:56 2009] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Dec 15 14:22:56 2009] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Tue Dec 15 14:22:56 2009] [notice] Digest: generating secret for digest authentication ...
[Tue Dec 15 14:22:56 2009] [notice] Digest: done
[Tue Dec 15 14:22:57 2009] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Dec 15 14:22:57 2009] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Tue Dec 15 14:22:57 2009] [notice] Apache/2.2.12 (Unix) DAV/2 mod_ssl/2.2.12 OpenSSL/0.9.8k PHP/5.3.0 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
[Tue Dec 15 14:25:34 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory
[Tue Dec 15 14:25:34 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi
[Tue Dec 15 14:28:10 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/cgi-bin
[Tue Dec 15 14:28:30 2009] [error] [client 127.0.0.1] attempt to invoke directory as script: /opt/lampp/cgi-bin/
[Tue Dec 15 14:30:58 2009] [error] [client 127.0.0.1] script not found or unable to stat: /opt/lampp/cgi-bin/agent_app
[Tue Dec 15 14:31:01 2009] [error] [client 127.0.0.1] (13)Permission denied: exec of '/opt/lampp/cgi-bin/agent_app.cgi' failed
[Tue Dec 15 14:31:01 2009] [error] [client 127.0.0.1] Premature end of script headers: agent_app.cgi
[Tue Dec 15 14:31:29 2009] [error] [client 127.0.0.1] (13)Permission denied: exec of '/opt/lampp/cgi-bin/agent_app.cgi' failed
[Tue Dec 15 14:31:29 2009] [error] [client 127.0.0.1] Premature end of script headers: agent_app.cgi
[Tue Dec 15 14:32:21 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/add_agent
[Tue Dec 15 14:32:28 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/style.css, referer: [http://127.0.0.1/add_agent.php](http://127.0.0.1/add_agent.php)
sudo: no tty present and no askpass program specified
sudo: no tty present and no askpass program specified
sh: [EMAIL="jeubank@scripbank.com"]jeubank@scripbank.com[/EMAIL]:alyssa123: not found
[Tue Dec 15 14:32:44 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/admin/style.css, referer: [http://127.0.0.1/admin/add_agent.php](http://127.0.0.1/admin/add_agent.php)
[Tue Dec 15 14:32:47 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/admin/order_printing.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory, referer: [http://127.0.0.1/admin/add_agent.php](http://127.0.0.1/admin/add_agent.php)
[Tue Dec 15 14:32:47 2009] [error] [client 127.0.0.1] Premature end of script headers: order_printing.cgi, referer: [http://127.0.0.1/admin/add_agent.php](http://127.0.0.1/admin/add_agent.php)
[Tue Dec 15 14:32:57 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 14:35:51 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/admin/style.css, referer: [http://127.0.0.1/admin/add_agent.php](http://127.0.0.1/admin/add_agent.php)
[Tue Dec 15 14:36:26 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/admin/header.css, referer: [http://127.0.0.1/admin/style.css](http://127.0.0.1/admin/style.css)
[Tue Dec 15 14:36:31 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/admin/order_printing.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory, referer: [http://127.0.0.1/admin/add_agent.php](http://127.0.0.1/admin/add_agent.php)
[Tue Dec 15 14:36:31 2009] [error] [client 127.0.0.1] Premature end of script headers: order_printing.cgi, referer: [http://127.0.0.1/admin/add_agent.php](http://127.0.0.1/admin/add_agent.php)
[Tue Dec 15 14:38:19 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:38:26 2009] [error] [client 127.0.0.1] PHP Warning:  mysql_free_result() expects parameter 1 to be resource, boolean given in /opt/lampp/htdocs/admin/bill_entry.php on line 163, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:38:26 2009] [error] [client 127.0.0.1] PHP Warning:  mysql_free_result() expects parameter 1 to be resource, boolean given in /opt/lampp/htdocs/admin/bill_entry.php on line 167, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:38:27 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:39:14 2009] [error] [client 127.0.0.1] PHP Warning:  mysql_free_result() expects parameter 1 to be resource, boolean given in /opt/lampp/htdocs/admin/bill_entry.php on line 163, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:39:14 2009] [error] [client 127.0.0.1] PHP Warning:  mysql_free_result() expects parameter 1 to be resource, boolean given in /opt/lampp/htdocs/admin/bill_entry.php on line 167, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:39:14 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/bill_entry.php](http://127.0.0.1/admin/bill_entry.php)
[Tue Dec 15 14:40:03 2009] [error] [client 127.0.0.1] File does not exist: /opt/lampp/htdocs/images/banner1.jpg, referer: [http://127.0.0.1/admin/](http://127.0.0.1/admin/)
[Tue Dec 15 14:40:09 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Tue Dec 15 14:40:09 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Tue Dec 15 14:40:12 2009] [error] [client 127.0.0.1] /opt/lampp/htdocs/index.cgi: error while loading shared libraries: liblptxn.so: cannot open shared object file: No such file or directory, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Tue Dec 15 14:40:12 2009] [error] [client 127.0.0.1] Premature end of script headers: index.cgi, referer: [http://127.0.0.1/](http://127.0.0.1/)




httpd.conf   :

#
> # This is the main Apache HTTP server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs/2.2> for detailed information.
# In particular, see 
# <URL:http://httpd.apache.org/docs/2.2/mod/directives.html>
# for a discussion of each configuration directive.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "logs/foo.log"
# with ServerRoot set to "/opt/lampp" will be interpreted by the
# server as "/opt/lampp/logs/foo.log".

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# Do not add a slash at the end of the directory path.  If you point
# ServerRoot at a non-local disk, be sure to point the LockFile directive
# at a local disk.  If you wish to share the same ServerRoot for multiple
# httpd daemons, you will need to change at least LockFile and PidFile.
#
ServerRoot "/opt/lampp"

#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to 
# prevent Apache from glomming onto all bound IP addresses.
#
#Listen 12.34.56.78:80
Listen 127.0.0.1:80

#
# Dynamic Shared Object (DSO) Support
#
# To be able to use the functionality of a module which was built as a DSO you
# have to place corresponding `LoadModule' lines at this location so the
# directives contained in it are actually available _before_ they are used.
# Statically compiled modules (those listed by `httpd -l') do not need
# to be loaded here.
#
# Example:
# LoadModule foo_module modules/mod_foo.so
#
LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authn_dbm_module modules/mod_authn_dbm.so
LoadModule authn_anon_module modules/mod_authn_anon.so
LoadModule authn_dbd_module modules/mod_authn_dbd.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule authz_dbm_module modules/mod_authz_dbm.so
LoadModule authz_owner_module modules/mod_authz_owner.so
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule file_cache_module modules/mod_file_cache.so
LoadModule cache_module modules/mod_cache.so
LoadModule disk_cache_module modules/mod_disk_cache.so
LoadModule mem_cache_module modules/mod_mem_cache.so
# mod_dbd doesn't work in Apache 2.2.3: getting always heaps of "glibc detected *** corrupted double-linked list" on shutdown - oswald, 10sep06
#LoadModule dbd_module modules/mod_dbd.so
LoadModule bucketeer_module modules/mod_bucketeer.so
LoadModule dumpio_module modules/mod_dumpio.so
LoadModule echo_module modules/mod_echo.so
LoadModule case_filter_module modules/mod_case_filter.so
LoadModule case_filter_in_module modules/mod_case_filter_in.so
LoadModule ext_filter_module modules/mod_ext_filter.so
LoadModule include_module modules/mod_include.so
LoadModule filter_module modules/mod_filter.so
LoadModule charset_lite_module modules/mod_charset_lite.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule logio_module modules/mod_logio.so
LoadModule env_module modules/mod_env.so
LoadModule mime_magic_module modules/mod_mime_magic.so
LoadModule cern_meta_module modules/mod_cern_meta.so
LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule ident_module modules/mod_ident.so
LoadModule usertrack_module modules/mod_usertrack.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
LoadModule mime_module modules/mod_mime.so
LoadModule dav_module modules/mod_dav.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule info_module modules/mod_info.so
LoadModule suexec_module modules/mod_suexec.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule cgid_module modules/mod_cgid.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule imagemap_module modules/mod_imagemap.so
LoadModule actions_module modules/mod_actions.so
LoadModule speling_module modules/mod_speling.so
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule apreq_module modules/mod_apreq2.so
LoadModule ssl_module modules/mod_ssl.so

<IfDefine JUSTTOMAKEAPXSHAPPY>
LoadModule php4_module        modules/libphp4.so
LoadModule php5_module        modules/libphp5.so
</IfDefine>

<IfModule !mpm_winnt_module>
<IfModule !mpm_netware_module>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User nobody
Group nogroup
</IfModule>
</IfModule>

# 'Main' server configuration
#
# The directives in this section set up the values used by the 'main'
# server, which responds to any requests that aren't handled by a
# <VirtualHost> definition.  These values also provide defaults for
# any <VirtualHost> containers you may define later in the file.
#
# All of these directives may appear inside <VirtualHost> containers,
# in which case these default settings will be overridden for the
# virtual host being defined.
#

#
# ServerAdmin: Your address, where problems with the server should be
# e-mailed.  This address appears on some server-generated pages, such
# as error documents.  e.g. [EMAIL="admin@your-domain.com"]admin@your-domain.com[/EMAIL]
#
ServerAdmin [EMAIL="you@example.com"]you@example.com[/EMAIL]

#
# ServerName gives the name and port that the server uses to identify itself.
# This can often be determined automatically, but we recommend you specify
# it explicitly to prevent problems during startup.
#
# If your host doesn't have a registered DNS name, enter its IP address here.
#
#ServerName [www.example.com:80]("http://www.example.com:80")
# XAMPP
ServerName localhost

#
# DocumentRoot: The directory out of which you will serve your
# documents. By default, all requests are taken from this directory, but
# symbolic links and aliases may be used to point to other locations.
#
DocumentRoot "/opt/lampp/htdocs"

#
# Each directory to which Apache has access can be configured with respect
# to which services and features are allowed and/or disabled in that
# directory (and its subdirectories). 
#
# First, we configure the "default" to be a very restrictive set of 
# features.  
#
<Directory /opt/lampp/*>
    Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec ExecCGI
    AllowOverride None
    #XAMPP
    #Order deny,allow
    #Deny from all
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory "/opt/lampp/*">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
       #Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # [http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)
    # for more information.
    #
    #Options Indexes FollowSymLinks
    # XAMPP
    Options Indexes FollowSymLinks ExecCGI Includes


    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    #AllowOverride None
    # since XAMPP 1.4:
    AllowOverride All


    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>

#
# DirectoryIndex: sets the file that Apache will serve if a directory
# is requested.
#
<IfModule dir_module>
    #DirectoryIndex index.html
    # XAMPP
    DirectoryIndex index.html index.html.var index.php index.php3 index.php4
</IfModule>

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
</FilesMatch>

#
# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog logs/error_log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

<IfModule log_config_module>
    #
    # The following directives define some format nicknames for use with
    # a CustomLog directive (see below).
    #
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common

    <IfModule logio_module>
      # You need to enable mod_logio.c to use %I and %O
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>

    #
    # The location and format of the access logfile (Common Logfile Format).
    # If you do not define any access logfiles within a <VirtualHost>
    # container, they will be logged here.  Contrariwise, if you *do*
    # define per-<VirtualHost> access logfiles, transactions will be
    # logged therein and *not* in this file.
    #
    CustomLog logs/access_log common

    #
    # If you prefer a logfile with access, agent, and referer information
    # (Combined Logfile Format) you can use the following directive.
    #
    #CustomLog logs/access_log combined
</IfModule>

<IfModule alias_module>
    #
    # Redirect: Allows you to tell clients about documents that used to 
    # exist in your server's namespace, but do not anymore. The client 
    # will make a new request for the document at its new location.
    # Example:
    # Redirect permanent /foo [http://www.example.com/bar](http://www.example.com/bar)

    #
    # Alias: Maps web paths into filesystem paths and is used to
    # access content that does not live under the DocumentRoot.
    # Example:
    # Alias /webpath /full/filesystem/path
    #
    # If you include a trailing / on /webpath then the server will
    # require it to be present in the URL.  You will also likely
    # need to provide a <Directory> section to allow access to
    # the filesystem path.

    #
    # ScriptAlias: This controls which directories contain server scripts. 
    # ScriptAliases are essentially the same as Aliases, except that
    # documents in the target directory are treated as applications and
    # run by the server when requested rather than as documents sent to the
    # client.  The same rules about trailing "/" apply to ScriptAlias
    # directives as to Alias.
    #
    ScriptAlias /cgi-bin/ "/opt/lampp/cgi-bin/"

</IfModule>

<IfModule cgid_module>
    #
    # ScriptSock: On threaded servers, designate the path to the UNIX
    # socket used to communicate with the CGI daemon of mod_cgid.
    #
    #Scriptsock logs/cgisock
</IfModule>

#
# "/opt/lampp/cgi-bin" should be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
#
<Directory "/opt/lampp/cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>

#
# DefaultType: the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain

<IfModule mime_module>
    #
    # TypesConfig points to the file containing the list of mappings from
    # filename extension to MIME-type.
    #
    TypesConfig etc/mime.types

    #
    # AddType allows you to add to or override the MIME configuration
    # file specified in TypesConfig for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi
    # XAMPP, since LAMPP 0.9.8:
    AddHandler cgi-script .cgi .pl

    # For files that include their own HTTP headers:
    #AddHandler send-as-is asis

    # For server-parsed imagemap files:
    #AddHandler imap-file map

    # For type maps (negotiated resources):
    #AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    # XAMPP
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# The mod_mime_magic module allows the server to use various hints from the
# contents of the file itself to determine its type.  The MIMEMagicFile
# directive tells the module where the hint definitions are located.
#
#MIMEMagicFile etc/magic

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# EnableMMAP and EnableSendfile: On systems that support it, 
# memory-mapping or the sendfile syscall is used to deliver
# files.  This usually improves server performance, but must
# be turned off when serving from networked-mounted 
# filesystems or if support for these functions is otherwise
# broken on your system.
#
EnableMMAP off
EnableSendfile off

# Supplemental configuration
#
# The configuration files in the etc/extra/ directory can be 
# included to add extra features or to modify the default configuration of 
# the server, or you may simply copy their contents here and change as 
# necessary.

# Server-pool management (MPM specific)
#Include etc/extra/httpd-mpm.conf

# Multi-language error messages
Include etc/extra/httpd-multilang-errordoc.conf

# Fancy directory listings
Include etc/extra/httpd-autoindex.conf

# Language settings
#Include etc/extra/httpd-languages.conf

# User home directories
#Include etc/extra/httpd-userdir.conf

# Real-time info on requests and configuration
#Include etc/extra/httpd-info.conf

# Virtual hosts
#Include etc/extra/httpd-vhosts.conf

# Local access to the Apache HTTP Server Manual
#Include etc/extra/httpd-manual.conf

# Distributed authoring and versioning (WebDAV)
#Include etc/extra/httpd-dav.conf

# Various default settings
Include etc/extra/httpd-default.conf

# Secure (SSL/TLS) connections
<IfModule ssl_module>
# XAMPP
<IfDefine SSL>
Include etc/extra/httpd-ssl.conf
</IfDefine>
</IfModule>
#
# Note: The following must must be present to support
#       starting without SSL on platforms with no /dev/random equivalent
#       but a statically compiled-in mod_ssl.
#
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>

# XAMPP
Include etc/extra/httpd-xampp.conf

---

### Post by gknight25 on 2009-12-15
if you guys need anymore info, please dont hesitate to ask. thanks!

---

### Post by gknight25 on 2009-12-16
I still cant find an exact answer... I have done everything i can think of. the library in question doesnt even seem to exsist in the mass of google.... so strangee

---

### Post by gknight25 on 2009-12-17
errr....bump

---

### Post by gknight25 on 2009-12-17
does nobody know the answer? or am i asking the wrong questions? or in the wrong forum?

---

### Post by oneloveamaru on 2009-12-17
I see a lot of "Permission denied" errors in your logs. Does www-data have read rights for all of these files and read/execute for the directories?

Almost forgot to mention, the reason it may say it can't load liblptxn.so and also says file/directory doesn't exist, it because it can't read it! If apache doesn't have access inside a folder, it will think 0 files are in there, throwing up lots of errors.

---

### Post by gknight25 on 2009-12-17
> **oneloveamaru said:**
> I see a lot of "Permission denied" errors in your logs. Does www-data have read rights for all of these files and read/execute for the directories?
 
Almost forgot to mention, the reason it may say it can't load liblptxn.so and also says file/directory doesn't exist, it because it can't read it! If apache doesn't have access inside a folder, it will think 0 files are in there, throwing up lots of errors.
 
 
awesome,
 
i'll give it a try when i get home, and provide a status update

---

### Post by Vegan on 2009-12-17
I have seen a lot of requests for documents that are not on my server, at one time a Polish university was attempting to find documents on my site that were not there.

I contacted them and got their IT guy and sent him the log and he found the problem was their mainframe was searching for something and unfortunately my server was selected in error.

I only saw about 1 million requests a day. My machine can cope, but my ISP does look down its pointed nose at all the traffic.

I sent then the log and they backed down.

So if this gets out of hand, I can show you how to set up Apache from scratch for a range of scenarios.

---

