---
title: "PHP 5.2.13 and Oracle threads.c krb5init_key_register error"
date: 2010-03-20
forum: Server Platforms
---

### Post by #Reistlehr- on 2010-03-20
```
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.
httpd: threads.c:321: krb5int_key_register: Assertion `keynum >= 0 && keynum < K5_KEY_MAX' failed.

```
PHP5 was having an issue compiling, (started with trying to compile in OCI8 support, which is the biggest nightmare i've ever dealt with). I finally just ran it with ./configure --prefix and no other options. It installs successfully, but when restarting Apache 2 it fails with krb5int_key_register.

PHP was working fine previously before rebuilding to include oracle. 

First error i included with Oracle was redefinitions from ldap.h within the Oracle/sdk/include directory. I need LDAP support, so i removed the ldap.h files since im using the library from openldap. LDAP was previously working perfectly fine before reconfigure. 

Tried to load shared module via pecl/pear, but PHP would not init the module even though it was added to php.ini. 

Any ideas?

Working from sources on this, no repo's

Thanks

---

### Post by #Reistlehr- on 2010-03-20
Here's some error's thrown when using --with-oci=instantclient,/path/to/oracle

```

/bin/sh /home/splug/Desktop/php-5.2.13/libtool --silent --preserve-dup-deps --mode=compile /home/splug/Desktop/php-5.2.13/meta_ccld -DLDAP_DEPRECATED=1 -Iext/ldap/ -I/home/splug/Desktop/php-5.2.13/ext/ldap/ -DPHP_ATOM_INC -I/home/splug/Desktop/php-5.2.13/include -I/home/splug/Desktop/php-5.2.13/main -I/home/splug/Desktop/php-5.2.13 -I/home/splug/Desktop/php-5.2.13/ext/date/lib -I/usr/include/libxml2 -I/usr/include/freetype2 -I/usr/include/c-client -I/home/splug/Desktop/php-5.2.13/ext/mbstring/oniguruma -I/home/splug/Desktop/php-5.2.13/ext/mbstring/libmbfl -I/home/splug/Desktop/php-5.2.13/ext/mbstring/libmbfl/mbfl -I/usr/include/mysql -I/opt/oracle/instantclient/sdk/include -I/usr/local/mysql/include/mysql -I/usr/include/pspell -I/home/splug/Desktop/php-5.2.13/TSRM -I/home/splug/Desktop/php-5.2.13/Zend  -D_REENTRANT  -I/usr/include -g -O2 -pthread -DZTS  -prefer-non-pic -c /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c -o ext/ldap/ldap.lo 
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:68:1: warning: "LBER_CLASS_UNIVERSAL" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:52:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:69:1: warning: "LBER_CLASS_APPLICATION" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:53:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:70:1: warning: "LBER_CLASS_CONTEXT" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:54:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:71:1: warning: "LBER_CLASS_PRIVATE" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:55:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:72:1: warning: "LBER_CLASS_MASK" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:56:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:75:1: warning: "LBER_PRIMITIVE" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:59:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:76:1: warning: "LBER_CONSTRUCTED" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:60:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:77:1: warning: "LBER_ENCODING_MASK" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:61:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:79:1: warning: "LBER_BIG_TAG_MASK" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:63:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:80:1: warning: "LBER_MORE_TAG_MASK" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:64:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:88:1: warning: "LBER_ERROR" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:74:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:89:1: warning: "LBER_DEFAULT" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:75:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:92:1: warning: "LBER_BOOLEAN" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:78:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:93:1: warning: "LBER_INTEGER" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:79:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:94:1: warning: "LBER_BITSTRING" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:80:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:95:1: warning: "LBER_OCTETSTRING" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:81:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:96:1: warning: "LBER_NULL" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:82:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:97:1: warning: "LBER_ENUMERATED" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:83:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:98:1: warning: "LBER_SEQUENCE" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:84:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:99:1: warning: "LBER_SET" redefined
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:27,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/usr/include/lber.h:85:1: warning: this is the location of the previous definition
In file included from /home/splug/Desktop/php-5.2.13/ext/ldap/php_ldap.h:29,
                 from /home/splug/Desktop/php-5.2.13/ext/ldap/ldap.c:45:
/opt/oracle/instantclient/sdk/include/ldap.h:183: error: redefinition of ‘struct berval’
make: *** [ext/ldap/ldap.lo] Errorl

```

removing ldap.h from oracleroot/sdk/include/ldap.h resolves that issue, as there are re-declares from the header files within /usr/include/. Why does OCI try to install LDAP?

---

### Post by #Reistlehr- on 2010-03-20
using the older 10.2.0.4-1 libs from Oracle (Basic and SDK) resolved the issue.

Appears to be related only to 11.x instant client. Stuck right together without an issue.

---

### Post by otyler on 2010-03-27
Thank you very much for this posting,  Reistlehr.

Not sure how many more days I would have worked on this before thinking to try earlier versions of the insta-client. I was having the same issues on 64 instant client ... went back to 10.4.0.2 and it happily configured and compiled.

---

### Post by #Reistlehr- on 2010-04-13
Glad it helped. Always gotta share the fix whenever you find one :D

---

