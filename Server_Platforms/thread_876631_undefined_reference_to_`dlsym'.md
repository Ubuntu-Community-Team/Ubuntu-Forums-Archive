---
title: "undefined reference to `dlsym'"
date: 2008-07-31
forum: Server Platforms
---

### Post by darleys on 2008-07-31
When I do a make , while building asterisk 1.4 I get this error
> [AR] hash/hash.o hash/hash_bigkey.o hash/hash_buf.o hash/hash_func.o hash/hash_log2.o hash/hash_page.o hash/ndbm.o btree/bt_close.o btree/bt_conv.o btree/bt_debug.o btree/bt_delete.o btree/bt_get.o btree/bt_open.o btree/bt_overflow.o btree/bt_page.o btree/bt_put.o bt ree/bt_search.o btree/bt_seq.o btree/bt_split.o btree/bt_utils.o db/db.o mpool/mpool.o recno/rec_close.o recno/rec_delete.o recno/rec_g et.o recno/rec_open.o recno/rec_put.o recno/rec_search.o recno/rec_seq.o recno/rec_utils.o -> libdb1.a
[LD] abstract_jb.o acl.o aescrypt.o aeskey.o aestab.o alaw.o app.o ast_expr2.o ast_expr2f.o asterisk.o astmm.o astobj2.o audiohook.o autoservice.o callerid.o cdr.o channel.o chanvars.o cli.o config.o cryptostub.o db.o devicestate.o dial.o dns.o dnsmgr.o dsp.o enum.o file.o fixedjitterbuf.o frame.o fskmodem.o global_datastores.o http.o image.o indications.o io.o jitterbuf.o loader.o logger.o manager. o md5.o netsock.o pbx.o plc.o privacy.o rtp.o say.o sched.o sha1.o slinfactory.o srv.o stdtime/localtime.o strcompat.o tdd.o term.o thr eadstorage.o translate.o udptl.o ulaw.o utils.o editline/libedit.a db1-ast/libdb1.a ../apps/modules.link ../cdr/modules.link ../channel s/modules.link ../codecs/modules.link ../formats/modules.link ../funcs/modules.link ../pbx/modules.link ../res/modules.link -> asterisk
loader.o: In function `load_dynamic_module':
/usr/src/asterisk/main/loader.c:362: warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
asterisk.o: In function `main':
/usr/src/asterisk/main/asterisk.c:2828: warning: Using 'initgroups' in statically linked applications requires at runtime the shared li braries from the glibc version used for linking
asterisk.o: In function `ast_makesocket':
/usr/src/asterisk/main/asterisk.c:1089: warning: Using 'getgrnam' in statically linked applications requires at runtime the shared libr aries from the glibc version used for linking
editline/libedit.a(readline.o_a): In function `username_completion_function':
/usr/src/asterisk/main/editline/readline.c:1296: warning: Using 'getpwent' in statically linked applications requires at runtime the sh ared libraries from the glibc version used for linking
asterisk.o: In function `ast_makesocket':
/usr/src/asterisk/main/asterisk.c:1080: warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libr aries from the glibc version used for linking
editline/libedit.a(readline.o_a): In function `username_completion_function':
/usr/src/asterisk/main/editline/readline.c:1294: warning: Using 'setpwent' in statically linked applications requires at runtime the sh ared libraries from the glibc version used for linking
/usr/src/asterisk/main/editline/readline.c:1300: warning: Using 'endpwent' in statically linked applications requires at runtime the sh ared libraries from the glibc version used for linking
utils.o: In function `ast_gethostbyname':
/usr/src/asterisk/main/utils.c:223: warning: Using 'gethostbyname_r' in statically linked applications requires at runtime the shared l ibraries from the glibc version used for linking
manager.o: In function `accept_thread':
/usr/src/asterisk/main/manager.c:2406: warning: Using 'getprotobyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/libcrypto.a(dso_dlfcn.o): In function `dlfcn_bind_func':
(.text+0x2d6): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/libcrypto.a(dso_dlfcn.o): In function `dlfcn_bind_var':
(.text+0x446): undefined reference to `dlsym'
collect2: ld returned 1 exit status
make[1]: *** [asterisk] Error 1
make: *** [main] Error 2 

I don't know , How to fix it

---

### Post by darleys on 2008-08-01
Nobody  is there to hep me out?

---

### Post by cariboo on 2008-08-01
Give it some time all the people are volunteers.

There are some premade debs here:

[http://www.voip-info.org/wiki-Asterisk+DEB](http://www.voip-info.org/wiki-Asterisk+DEB)

Jim

---

### Post by ryansteele on 2008-10-27
Hi, darleys - 

I'm experiencing the same trouble right now.  I don't know if it will help in your case, but changing the linker flag appears to do the trick.

Problem occurs with 
LD = g++ -static

Problem goes away with
LD = g++

Unfortunately, in my case, I get dynamic library errors when I run without it. :)  Hopefully you'll have better luck.

Ryan

---

