---
title: "Relocating TWiki missing perl.conf"
date: 2009-02-14
forum: Server Platforms
---

### Post by volkswagner on 2009-02-14
I am trying to upgrade to a new server machine.

Old server is 6.06 on pent2, new server is 8.04.1 on Intel Atom.

I have an existing TWiki install, I would like to relocate.  I followed the recommended steps by tar twiki dir. and relocate then utar.

I seem to be having a problem running perl scripts.  

Potential problems:
I don't see perl.conf but I do have perl.load in mods-available. 
It seems apache won't run perl scripts that don't have a file extension like .pl

I confirmed this with simple script with both a .pl and no extension.  In fact the file icon in firefox is listed with a "?" when no extension is given.

Before I reconfigure twiki to rename files with .pl does anyone have a clue what I am missing?
```

 ls /etc/apache2/mods-available
actions.conf          dav.load           negotiation.load
actions.load          dav_lock.load      perl.load
alias.conf            dbd.load           php5.conf
alias.load            deflate.conf       php5.load
asis.load             deflate.load       proxy_ajp.load
auth_basic.load       dir.conf           proxy_balancer.load
auth_digest.load      dir.load           proxy.conf
authn_alias.load      disk_cache.conf    proxy_connect.load
authn_anon.load       disk_cache.load    proxy_ftp.load
authn_dbd.load        dump_io.load       proxy_http.load
authn_dbm.load        env.load           proxy.load
authn_default.load    expires.load       rewrite.load
authn_file.load       ext_filter.load    ruby.load
authnz_ldap.load      file_cache.load    setenvif.conf
authz_dbm.load        filter.load        setenvif.load
authz_default.load    headers.load       speling.load
authz_groupfile.load  ident.load         ssl.conf
authz_host.load       imagemap.load      ssl.load
authz_owner.load      include.load       status.conf
authz_user.load       info.conf          status.load
autoindex.conf        info.load          substitute.load
autoindex.load        ldap.load          suexec.load
cache.load            log_forensic.load  unique_id.load
cern_meta.load        mem_cache.conf     userdir.conf
cgid.conf             mem_cache.load     userdir.load
cgid.load             mime.conf          usertrack.load
cgi.load              mime.load          version.load
charset_lite.load     mime_magic.conf    vhost_alias.load
dav_fs.conf           mime_magic.load
dav_fs.load           negotiation.conf

```

```
ls /etc/apache2/mods-enabled
alias.conf            autoindex.conf  mime.load         setenvif.conf
alias.load            autoindex.load  negotiation.conf  setenvif.load
auth_basic.load       cgi.load        negotiation.load  ssl.conf
authn_file.load       dir.conf        perl.load         ssl.load
authz_default.load    dir.load        php5.conf         status.conf
authz_groupfile.load  env.load        php5.load         status.load
authz_host.load       include.load    rewrite.load      suexec.load
authz_user.load       mime.conf       ruby.load
```

libapache2-mod-perl2 is installed and latest version 

I also tried various things with httpd.conf:

AddHandler cgi-script .pl
AddHandler cgi-script .pl *
#AddHandler cgi-script .pl

and 
AddHandler cgi-script

The above returns error when restarting apache because no extensions were listed.

---

