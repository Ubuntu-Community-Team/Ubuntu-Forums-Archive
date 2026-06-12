---
title: "apache2 compile non-standard modules"
date: 2008-06-16
forum: Server Platforms
---

### Post by SpaceTeddy on 2008-06-16
Hi Folks, 

i've setup apache2 servers about a million times... but i have never compiled one. So, as this is my first try, and i am realy hitting my head against a wall here, i thought i might as you guys for some advice. 

**Here is my problem:**
I want to use mod_caldav so that i can have multiple lightning synchronising the same calendar. To compile mod_caldav, i need mod_dav_acl.
To compile mod_dav_acl i need a patched version of apache2...and that is where my problem starts. 

So, i've downloaded the https-2.2.9 package.
untared it, applied the patch, ran configure followed by a make and make install. In other words, the apache2 works now. 

But whenever i try to compile the mod_cal_dav i get the following errors:
> root@davcal:~/mod_dav_acl-0.1.3# make
make  all-am
make[1]: Entering directory `/root/mod_dav_acl-0.1.3'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.    -I**/usr/include/apache2** -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I/usr/include/libxml2 -I/usr/include/apr-1.0    -g -O2 -MT mod_dav_acl_la-mod_dav_acl.lo -MD -MP -MF .deps/mod_dav_acl_la-mod_dav_acl.Tpo -c -o mod_dav_acl_la-mod_dav_acl.lo `test -f 'mod_dav_acl.c' || echo './'`mod_dav_acl.c
 gcc -DHAVE_CONFIG_H -I. -I**/usr/include/apache2** -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I/usr/include/libxml2 -I/usr/include/apr-1.0 -g -O2 -MT mod_dav_acl_la-mod_dav_acl.lo -MD -MP -MF .deps/mod_dav_acl_la-mod_dav_acl.Tpo -c mod_dav_acl.c  -fPIC -DPIC -o .libs/mod_dav_acl_la-mod_dav_acl.o
mod_dav_acl.c: In function 'acl_privilege_error':
mod_dav_acl.c:188: error: 'dav_error' has no member named 'childtags'
mod_dav_acl.c: In function 'acl_exec_error':
mod_dav_acl.c:215: error: 'dav_error' has no member named 'childtags'
mod_dav_acl.c:215: error: 'dav_error' has no member named 'childtags'
mod_dav_acl.c:215: error: 'dav_error' has no member named 'childtags'
mod_dav_acl.c:215: error: 'dav_error' has no member named 'childtags'
mod_dav_acl.c: In function 'dav_acl_is_resource_principal':
mod_dav_acl.c:509: error: 'dav_hooks_repository' has no member named 'get_request_rec'
mod_dav_acl.c: In function 'dav_acl_get_privs':
mod_dav_acl.c:814: error: 'dav_hooks_repository' has no member named 'get_request_rec'
mod_dav_acl.c: In function 'acl_check':
mod_dav_acl.c:944: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:968: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:995: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:1058: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:1083: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:1119: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:1132: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c:1155: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c: In function 'dav_acl_check':
mod_dav_acl.c:1799: error: 'dav_hooks_repository' has no member named 'get_pathname'
mod_dav_acl.c: At top level:
mod_dav_acl.c:2057: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'acl'
mod_dav_acl.c:2066: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
mod_dav_acl.c: In function 'acl_send_principal_props':
mod_dav_acl.c:2208: error: 'dav_resource' has no member named 'acl_hooks'
mod_dav_acl.c: In function 'dav_acl_get_group_membership':
mod_dav_acl.c:2470: error: 'dav_hooks_repository' has no member named 'get_request_rec'
mod_dav_acl.c: In function 'davacl_handler':
mod_dav_acl.c:2522: warning: initialization makes pointer from integer without a cast
mod_dav_acl.c: In function 'acl_initialize_module':
mod_dav_acl.c:2712: error: 'acl' undeclared (first use in this function)
mod_dav_acl.c:2712: error: (Each undeclared identifier is reported only once
mod_dav_acl.c:2712: error: for each function it appears in.)
mod_dav_acl.c: At top level:
mod_dav_acl.c:2785: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'options'
mod_dav_acl.c: In function 'acl_get_resource_type':
mod_dav_acl.c:2798: error: 'dav_hooks_repository' has no member named 'get_request_rec'
mod_dav_acl.c: At top level:
mod_dav_acl.c:2811: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'res_hooks'
mod_dav_acl.c: In function 'acl_register_hooks':
mod_dav_acl.c:2903: error: 'options' undeclared (first use in this function)
mod_dav_acl.c:2905: error: 'res_hooks' undeclared (first use in this function)
make[1]: *** [mod_dav_acl_la-mod_dav_acl.lo] Error 1
make[1]: Leaving directory `/root/mod_dav_acl-0.1.3'
make: *** [all] Error 2

now, i know from this [[COLOR="Blue"]post[/COLOR]]("http://sourceforge.net/forum/forum.php?thread_id=1747658&forum_id=677024") that this has something to do with my apache2 not being patched - but i did patch it. So, my question is, how do i tell the configure where to look for the right apache2 sources, or where do i have to copy what from the apache to compile this.

Also, i have bolded the (probably) wrong path in the make file.. but i can't for the life of it figure out where to set this... the --prefix or --include in the configure seem to be ignored... 

thanks a lot in advance

---

### Post by SpaceTeddy on 2008-06-17
bump

---

