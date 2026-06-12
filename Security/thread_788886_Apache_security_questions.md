---
title: "Apache security questions"
date: 2008-05-10
forum: Security
---

### Post by TDK800 on 2008-05-10
Latest Apache 2

Question 1: For securing root directory, which one to use:

<Directory />
    Options None
    AllowOverride None
</Directory>

Or:

<Directory />
           Options None
           AllowOverride None
           Order Deny,Allow 
           Deny from all
</Directory>



Question 2: Should TRACE and TRACK Methods still be separately Disabled in latest Apache for increased security?

RewriteEngine on
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
RewriteRule .* - [F]


Question 3: Are there security implications when all auth modules are, except authz_host_module are disabled (login password prompt for phpMyAdmin seems to be working correctly though all auth modules are disabled).

LoadModule authz_host_module modules/mod_authz_host.so
#LoadModule auth_basic_module modules/mod_auth_basic.so
#LoadModule auth_digest_module modules/mod_auth_digest.so
#LoadModule authn_file_module modules/mod_authn_file.so
#LoadModule authn_alias_module modules/mod_authn_alias.so
#LoadModule authn_anon_module modules/mod_authn_anon.so
#LoadModule authn_dbm_module modules/mod_authn_dbm.so
#LoadModule authn_default_module modules/mod_authn_default.so
#LoadModule authz_user_module modules/mod_authz_user.so
#LoadModule authz_owner_module modules/mod_authz_owner.so
#LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
#LoadModule authz_dbm_module modules/mod_authz_dbm.so
#LoadModule authz_default_module modules/mod_authz_default.so
#LoadModule ldap_module modules/mod_ldap.so
#LoadModule authnz_ldap_module modules/mod_authnz_ldap.so

---

