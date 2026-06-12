---
title: "Getting errors while compiling Tapioca"
date: 2007-11-13
forum: The Cafe
---

### Post by manishsingh4u on 2007-11-13
Hi All,

I am having problems compiling Tapioca. I have followed all the instructions from the page below and after getting all the rest packages to go smooth, I am stuck at the last one "tapioca-python".
[http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide)


I am using Ubuntu 7.04 with the default kernel 2.6.20-15-generic. Here's the text where I encounter the errors. Any ideas?

Please let me know if you need more info. Thanks.


```

mann@manish:/usr/src/tapioca-python$ sudo make
make  all-recursive
make[1]: Entering directory `/usr/src/tapioca-python'
Making all in tapioca
make[2]: Entering directory `/usr/src/tapioca-python/tapioca'
make  all-am
make[3]: Entering directory `/usr/src/tapioca-python/tapioca'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/python2.5 -I/usr/local/include/libtapioca-glib-0.14 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -MT _client_la-tapiocaclient.lo -MD -MP -MF ".deps/_client_la-tapiocaclient.Tpo" -c -o _client_la-tapiocaclient.lo `test -f 'tapiocaclient.c' || echo './'`tapiocaclient.c; \
        then mv -f ".deps/_client_la-tapiocaclient.Tpo" ".deps/_client_la-tapiocaclient.Plo"; else rm -f ".deps/_client_la-tapiocaclient.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/python2.5 -I/usr/local/include/libtapioca-glib-0.14 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -MT _client_la-tapiocaclient.lo -MD -MP -MF .deps/_client_la-tapiocaclient.Tpo -c tapiocaclient.c  -fPIC -DPIC -o .libs/_client_la-tapiocaclient.o
In file included from tapiocaclient.override:5:
generated-tapiocaclient-enums-gtypes.h: In function 'tpa_stream_state_get_type':
generated-tapiocaclient-enums-gtypes.h:193: error: 'TPA_STREAM_STATE_PAUSED' undeclared (first use in this function)
generated-tapiocaclient-enums-gtypes.h:193: error: (Each undeclared identifier is reported only once
generated-tapiocaclient-enums-gtypes.h:193: error: for each function it appears in.)
tapiocaclient.c: In function '_wrap_tpa_contact_list_add':
tapiocaclient.c:2371: warning: assignment discards qualifiers from pointer target type
make[3]: *** [_client_la-tapiocaclient.lo] Error 1
make[3]: Leaving directory `/usr/src/tapioca-python/tapioca'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/tapioca-python/tapioca'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/tapioca-python'
make: *** [all] Error 2
mann@manish:/usr/src/tapioca-python$ 

```

---

