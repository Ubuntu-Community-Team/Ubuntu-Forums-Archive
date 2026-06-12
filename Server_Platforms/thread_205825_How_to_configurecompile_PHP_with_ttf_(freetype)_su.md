---
title: "How to configure/compile PHP with ttf (/freetype) support?"
date: 2006-06-29
forum: Server Platforms
---

### Post by djvishnu on 2006-06-29
I'm having problems with compiling (php5) with gd and ttf (/freetype) support

This is how i configure my php:
```
'./configure' '--with-mysql' '--prefix=/opt/php5' 
'--with-config-file-path=/etc/php5-conf/php.ini' 
'--with-config-file-scan-dir=/etc/php5-conf' 
'--with-apxs2=/usr/bin/apxs2' '--with-pear' '--with-gd' 
'--with-libxml-dir=/usr/lib' '--with-jpeg-dir=/usr/lib' 
'--with-zlib-dir=/usr/lib' '--with-png-dir=/usr/lib' 
'--with-gettext' '--enable-ftp' '--enable-magic-quotes' 
'--with-mcrypt' '--with-imap' '--with-kerberos' 
'--with-imap-ssl' '--with-ttf' '--enable-gd-native-ttf'
```

I have these packages installed:
```
0 vishnu@sensation:/usr/src/php-5.1.2> agl ttf
ii  freetype2                              1.4pre.20030402-1.1               Dummy package for transition to libttf2
ii  libttf-dev                             1.4pre.20030402-1.1               FreeType 1 development files (static library
ii  libttf2                                1.4pre.20030402-1.1               FreeType 1, The FREE TrueType Font Engine, s
ii  ttf-bitstream-vera                     1.10-3ubuntu1                     The Bitstream Vera family of free TrueType f
```

But when i run phpinfo(), it says this about gd:
```
gd
GD Support 	enabled
GD Version 	bundled (2.0.28 compatible)
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled
XBM Support 	enabled

```

I have never used fonts with gd before, so im not sur im using the configure options right, could someone please help me? Any help would be greatly appreceated!

Thank you!

---

