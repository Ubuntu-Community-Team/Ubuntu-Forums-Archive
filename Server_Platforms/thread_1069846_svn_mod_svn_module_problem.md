---
title: "svn ?mod_svn module problem"
date: 2009-02-14
forum: Server Platforms
---

### Post by pdc124 on 2009-02-14
im trying to get suversion/webdav set up to move a working gentoo setup .
i get this 
root@server:/var/svn/conf# /etc/init.d/apache2 reload
Syntax error on line 31 of /etc/apache2/sites-enabled/xxxx
Invalid command 'SVNParentPath', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
root@server:/var/svn/conf#             

root@server:/var/svn/conf# /etc/init.d/apache2 reload
Syntax error on line 31 of /etc/apache2/sites-enabled/xxxx
Invalid command 'SVNPath', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
root@server:/var/svn/

[http://ubuntuforums.org/showthread.php?t=1068765](http://ubuntuforums.org/showthread.php?t=1068765)
DAV svn           

and google tells me i havent got mod_svn module loaded
the  loaded modules are

root@server:/etc/apache2/mods-enabled# ls
alias.conf       authz_default.load    autoindex.conf  dav_fs.load    ?dir.load   negotiation.conf  setenvif.conf
alias.load       authz_groupfile.load  autoindex.load  dav.load       env.load   negotiation.load  setenvif.load
auth_basic.load  authz_host.load       cgi.load        dav_lock.load  mime.conf  php5.conf         status.conf
authn_file.load  authz_user.load       dav_fs.conf     dir.conf       mime.load  php5.load         status.load
root@server:/etc/apache2/mods-enabled#  

so what else do I need ?


and the relevant module isnt listed here
root@server:~# ls /usr/lib/apache2/modules/
httpd.exp               mod_cgid.so          mod_mem_cache.so
libphp5.so              mod_cgi.so           mod_mime_magic.so
mod_actions.so          mod_charset_lite.so  mod_mime.so
mod_alias.so            mod_dav_fs.so        mod_negotiation.so
mod_asis.so             mod_dav_lock.so      mod_proxy_ajp.so
mod_auth_basic.so       mod_dav.so           mod_proxy_balancer.so
mod_auth_digest.so      mod_dbd.so           mod_proxy_connect.so
mod_authn_alias.so      mod_deflate.so       mod_proxy_ftp.so
mod_authn_anon.so       mod_dir.so           mod_proxy_http.so
mod_authn_dbd.so        mod_disk_cache.so    mod_proxy.so
mod_authn_dbm.so        mod_dumpio.so        mod_rewrite.so
mod_authn_default.so    mod_env.so           mod_setenvif.so
mod_authn_file.so       mod_expires.so       mod_speling.so
mod_authnz_ldap.so      mod_ext_filter.so    mod_ssl.so
mod_authz_dbm.so        mod_file_cache.so    mod_status.so
mod_authz_default.so    mod_filter.so        mod_substitute.so
mod_authz_groupfile.so  mod_headers.so       mod_suexec.so
mod_authz_host.so       mod_ident.so         mod_unique_id.so
mod_authz_owner.so      mod_imagemap.so      mod_userdir.so
mod_authz_user.so       mod_include.so       mod_usertrack.so
mod_autoindex.so        mod_info.so          mod_version.so
mod_cache.so            mod_ldap.so          mod_vhost_alias.so
mod_cern_meta.so        mod_log_forensic.so
root@server:~#

---

