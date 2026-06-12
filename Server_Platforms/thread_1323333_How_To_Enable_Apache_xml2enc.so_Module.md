---
title: "How To Enable Apache xml2enc.so Module?"
date: 2009-11-11
forum: Server Platforms
---

### Post by shirubia on 2009-11-11
Hi All,

I am having trouble getting an Apache module to work..

The module I'm trying to use is "xml2enc". Its a *transcoding module that can be used to extend the internationalisation support of [libxml2]("http://xmlsoft.org/")-based filter modules by converting encoding before and/or after the filter has run.  Thus an unsupported input charset can be converted to UTF-8, and output can also be converted to another charset if required.* ([http://apache.webthing.com/mod_xml2enc/](http://apache.webthing.com/mod_xml2enc/))

I have the source codes from that site (mod_xmlenc.c and mod_xmlenc.h) and I tried to compile them (gcc mod_xml2enc.c -o mod_xml2enc), but I get this error:

```
mod_xml2enc.c:54:29: error: libxml/encoding.h: No such file or directory
mod_xml2enc.c:57:27: error: http_protocol.h: No such file or directory
mod_xml2enc.c:58:25: error: http_config.h: No such file or directory
mod_xml2enc.c:59:22: error: http_log.h: No such file or directory
mod_xml2enc.c:60:25: error: apr_strings.h: No such file or directory
mod_xml2enc.c:61:23: error: apr_xlate.h: No such file or directory
mod_xml2enc.c:63:26: error: apr_optional.h: No such file or directory
In file included from mod_xml2enc.c:64:
mod_xml2enc.h:31: error: expected ‘)’ before ‘(’ token
mod_xml2enc.h:34: error: expected ‘)’ before ‘(’ token
mod_xml2enc.h:36: error: expected ‘)’ before ‘int’
mod_xml2enc.c:96: error: expected specifier-qualifier-list before ‘xmlCharEncoding’
mod_xml2enc.c:109: error: expected specifier-qualifier-list before ‘xmlCharEncoding’
mod_xml2enc.c:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mod_xml2enc.c:118: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mod_xml2enc.c:120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xml2enc_filter’
mod_xml2enc.c:157: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:192: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:304: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xml2enc_filter_init’
mod_xml2enc.c:316: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xml2enc_ffunc’
mod_xml2enc.c:527: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xml2enc_charset’
mod_xml2enc.c:538: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:549: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:560: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:576: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:586: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xml2enc_cmds’
mod_xml2enc.c:595: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:601: error: expected ‘)’ before ‘*’ token
mod_xml2enc.c:611: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘AP_MODULE_DECLARE_DATA’
mod_xml2enc.c:620: error: expected ‘)’ before ‘int’
```

I was wondering if anyone has an *_easier_* way to get the "xml2enc" working? Or if this would even resolve my problem..

*_**My Problem**_*: I have 2 servers at 2 different locations. server1 hosts my entire site, server2 hosts a section of my site. I've used ProxyPass, ProxyPassReverse, ProxyHTMLURLMap, (Modules: a2enmod proxy, proxy_http, proxy_html) to keep the same url, links, etc.. to look like its only one site, but I'm having problems rendering trademark symbols (TM). Instead, i get a square box with 0099 in it... I think that the "xml2enc" module would fix that... 

Can anyone confirm? Or is there some other way to render trademark symbols?

Any push in the right direction is appreciated!

---

### Post by mrsteveman1 on 2009-11-11
Looks like you need development headers for apache portable runtime. On 9.10 the package name you'd want for that is libapr1-dev.

May also need the apache2 dev headers for the mpm you are using, so apache2-prefork-dev or apache2-threaded-dev.

As for whether or not you are on the right track, i dunno :)

---

### Post by shirubia on 2009-11-12
Thanks for the reply~

Installed those packages (but couldn't install apache2-prefork-dev), tried to compile the xml2enc.c file but still no luck...

any other suggestions?

I just want trademark symbols to render correctly~ :(

---

### Post by mrsteveman1 on 2009-11-12
Same error?

---

### Post by shirubia on 2009-11-16
> **mrsteveman1 said:**
> Same error?

Yes same error.. my website uses "&#0153", to make TM symbols, I'm wondering if using "&trade" instead would make a difference? Any advice

---

### Post by shirubia on 2009-11-18
TM symbols render correctly when I check on any other computer on my network.. It only happens on the computer hosting Apache.

---

