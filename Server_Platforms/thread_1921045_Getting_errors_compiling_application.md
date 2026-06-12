---
title: "Getting errors compiling application"
date: 2012-02-06
forum: Server Platforms
---

### Post by qhedberg on 2012-02-06
I am trying to compile an application on ubuntu server, but it keeps failing. This is the return:
```
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c acl.cpp -o .objs/acl.o
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c gre.cpp -o .objs/gre.o
gre.cpp: In member function &#8216;void Proxy::greThread()&#8217;:
gre.cpp:38: error: &#8216;memset&#8217; was not declared in this scope
gre.cpp:121: error: &#8216;memcpy&#8217; was not declared in this scope
make: *** [.objs/gre.o] Error 1
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c link.cpp -o .objs/link.o
acl.cpp: In member function &#8216;void Proxy::addACL(char*)&#8217;:
acl.cpp:21: error: &#8216;strdup&#8217; was not declared in this scope
make: *** [.objs/acl.o] Error 1
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c log.cpp -o .objs/log.o
link.cpp: In constructor &#8216;Proxy::Link::Link(Proxy*, int)&#8217;:
link.cpp:107: error: &#8216;memset&#8217; was not declared in this scope
link.cpp: In member function &#8216;bool Proxy::Link::tcpPacket(bool)&#8217;:
link.cpp:306: error: &#8216;memset&#8217; was not declared in this scope
link.cpp:310: error: &#8216;strcmp&#8217; was not declared in this scope
link.cpp:330: error: &#8216;strcpy&#8217; was not declared in this scope
make: *** [.objs/link.o] Error 1
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c options.cpp -o .objs/options.o
log.cpp: In member function &#8216;void Proxy::fail(const char*, int32_t, const char*, bool, const char*, const char*, ...)&#8217;:
log.cpp:140: error: &#8216;strerror&#8217; was not declared in this scope
log.cpp:168: error: &#8216;exit&#8217; was not declared in this scope
make: *** [.objs/log.o] Error 1
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c pairs.cpp -o .objs/pairs.o
options.cpp: In function &#8216;void help(bool)&#8217;:
options.cpp:44: error: &#8216;exit&#8217; was not declared in this scope
options.cpp: In member function &#8216;void Proxy::options(char**)&#8217;:
options.cpp:71: error: &#8216;exit&#8217; was not declared in this scope
options.cpp:94: warning: deprecated conversion from string constant to &#8216;char*&#8217;
pairs.cpp: In member function &#8216;bool Proxy::parseAddress(uint32_t*, uint32_t*, const char*)&#8217;:
pairs.cpp:21: error: &#8216;strdup&#8217; was not declared in this scope
pairs.cpp:37: error: &#8216;free&#8217; was not declared in this scope
pairs.cpp:44: error: &#8216;free&#8217; was not declared in this scope
pairs.cpp: In member function &#8216;void Proxy::addProxyPair(char*)&#8217;:
pairs.cpp:63: error: &#8216;strdup&#8217; was not declared in this scope
make: *** [.objs/options.o] Error 1
pairs.cpp: In constructor &#8216;Proxy::Pair::Pair(Proxy*, const char*, uint32_t, uint32_t, const char*, uint32_t, uint32_t)&#8217;:
pairs.cpp:204: error: &#8216;memset&#8217; was not declared in this scope
c++ -MD -I.  -g0 -O6 -Winline -fno-check-new -fno-exceptions -fomit-frame-pointer -fexpensive-optimizations  -c utils.cpp -o .objs/utils.o
make: *** [.objs/pairs.o] Error 1
utils.cpp: In member function &#8216;bool Proxy::resolve(uint32_t*, const char*, bool)&#8217;:
utils.cpp:33: error: &#8216;sscanf&#8217; was not declared in this scope
utils.cpp: In member function &#8216;void Proxy::daemonize()&#8217;:
utils.cpp:132: error: &#8216;exit&#8217; was not declared in this scope
utils.cpp:138: error: &#8216;exit&#8217; was not declared in this scope
make: *** [.objs/utils.o] Error 1
make: Target `all' not remade because of errors.
```

Does anybody know what is going wrong and how to fix it?

---

### Post by shumifan50 on 2012-02-06
How long have you been programming?
You need several include files e.g. <string.h>

---

