---
title: "Apache2.2 modules - mostly authorization"
date: 2006-07-20
forum: Server Platforms
---

### Post by mdecler2 on 2006-07-20
Apache2.2 documentation has said that the most significant change between Apache2.0 and 2.2 was the authorization modules ([http://httpd.apache.org/docs/2.2/upgrading.html)](http://httpd.apache.org/docs/2.2/upgrading.html)).
However, I cannot find any of those authorization modules in my /etc/apache2/mods-available/ folder.

Specifically, I do not find mod_auth_basic, mod_authn_file, mod_authz_user, mod_authz_groupfile, or mod_authnz_ldap as the documentation listed would be available in the new release of Apache2.2 (see link).

My Apache2.2 install on WindowsXP has all these authorization modules and the mod_authnz_ldap module in question.

I did find a mod_auth_ldap package (which the above link says was replaced by mod_authnz_ldap in the Apache2.2 release), but upon trying to load it using "sudo a2enmod mod_auth_ldap.so" I recieved the message "That module does not exist!" :neutral: 
Unfortunately the man page on a2enmod leaves more to be desired. :-? 

I have been searching around in the Ubuntu Dapper servertalk and howto forums, and asked for help on the apache user mailing list, but have found nothing as yet about where I can download standard Apache2.2 modules. 

If anyone has found anywhere to download standard Apache2.2 modules such as mod_auth_basic, mod_authn_file, mod_authz_user, mod_authz_groupfile, and mod_authnz_ldap please let me know.

I worried this may turn into a "howto," but if I am blindly missing something important, like about installing modules with the Apache install, please tell me.
Your help is always appreciated. :) 

Michael DeClerck

---

### Post by az on 2006-07-20
what apache2-mod-* packages do you have installed?

---

### Post by mdecler2 on 2006-07-20
Under my /etc/apache2/mods-enabled folder I have three symbolic links (to files with the same name in the mods-available folder) ldap_userdir.load, userdir.conf, userdir.load. But I have no idea what they do :-D . 
I am assuming those are bare-bones apache modules?

I think I found the mod_authnz_ldap package under my httpd-2.2.2 unzipped folder (where you first install Apache) then under modules/ldap.   :rolleyes:  
If that's what I need, then all I need to do is follow the readme I guess.
"./configure --with-ldap --enable-ldap --enable-authnz-ldap"

If this module is the correct module,
do I need to configure Apache again with "./configure --prefix=PREFIX", then install the module, then make and install Apache?

If that sequence is correct,
will that blow any of my httpd.conf files or Apache root folders away?

---

### Post by mdecler2 on 2006-07-24
I looked at several online sources since my last post, most encourage recomiling Apache with the module in question _statically_. However, I know that there is such thing as a dynamically installed module (DSO?).

In any case, I downloaded some OpenLDAP libraries, and while running the ./configure --enable-ldap --with-ldap --enable-authnz-ldap --prefix=%HOME%/apache line, it cannot seem to find the neccessary ldap libraries. ](*,) 

There has to be some way to configure where it is looking for libraries, but I don't even know where they are or how to find them. They should be called libldap2.

---

### Post by mdecler2 on 2006-07-27
My current situation of mod_authnz_ldap is still not good.

The issue was the ldap libraries which I had downloaded from the OpenLDAP source.
The libraries were being installed in /usr/local/lib.
I had to point LDFLAGS to -L/usr/local/lib, and CPPFLAGS and CFLAGS to -I/usr/local/include.
The Apache configure had no errors with these environment variables.

Unfortunately,
I get these errors during the Apache make:

```
server/.libs/libmain.a(exports.o):(.data+0xe48): undefined reference to `apr_ldap_ssl_init'
server/.libs/libmain.a(exports.o):(.data+0xe4c): undefined reference to `apr_ldap_ssl_deinit'
server/.libs/libmain.a(exports.o):(.data+0xe50): undefined reference to `apr_ldap_init'
server/.libs/libmain.a(exports.o):(.data+0xe54): undefined reference to `apr_ldap_info'
server/.libs/libmain.a(exports.o):(.data+0xe58): undefined reference to `apr_ldap_get_option'
server/.libs/libmain.a(exports.o):(.data+0xe5c): undefined reference to `apr_ldap_set_option'
server/.libs/libmain.a(exports.o):(.data+0xe60): undefined reference to `apr_ldap_is_ldap_url'
server/.libs/libmain.a(exports.o):(.data+0xe64): undefined reference to `apr_ldap_is_ldaps_url'
server/.libs/libmain.a(exports.o):(.data+0xe68): undefined reference to `apr_ldap_is_ldapi_url'
server/.libs/libmain.a(exports.o):(.data+0xe6c): undefined reference to `apr_ldap_url_parse_ext'
server/.libs/libmain.a(exports.o):(.data+0xe70): undefined reference to `apr_ldap_url_parse'
modules/aaa/.libs/libmod_authnz_ldap.a(mod_authnz_ldap.o): In function `mod_auth_ldap_parse_url':mod_authnz_ldap.c:(.text+0x1e84): undefined reference to `apr_ldap_url_parse'
collect2: ld returned 1 exit status
make[1]: *** [httpd] Error 1
```

I have very little idea of what to do.
Any help at all is appreciated.

---

### Post by mdecler2 on 2006-07-31
I got it installed! The issue was two flags: --with-ldap-include and --with-ldap-lib, where --with-ldap-include points to the ldap header files, and the --with-ldap-lib points to the ldap libraries.
I've decided to install SSL as well, which I had no problem with.

Oh, and a note: I had to go have all my old environment variables CCFLAGS, CFLAGS, and LDFLAGS removed. I just moved to a new environment and ran the configure script there with the flags as mentioned above.

---

