---
title: "Cannot compile mod_perl 1.30 and apache 1.3.37 from source"
date: 2007-06-06
forum: Server Platforms
---

### Post by hikirsch on 2007-06-06
Hi Guys -

I am a web developer and I compile my version of Apache/mod_perl/php to get certain features I need that I can't get from installing the binaries from the repository. Everything is working out fine but I can't seem to get past this part. Below is the log from when I run "make" for apache.

I thought it would have to do with the fact that the compiler has issues loading the perl modules (i even tried to install it into /usr/lib/perl but that didn't work either). I have no idea and I've been struggling with this for a couple of days.

Version Info below:
Ubuntu Server 6.06.1
mod_perl 1.30
apache 1.3.37
perl is from repository

Any help is much appriciated. I can also supply more info if necessary.

--Adam

```
<=== src/modules/perl
<=== src/modules
gcc -c -I. -I/usr/lib/perl/5.8/CORE -I./os/unix -I./include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DMOD_SSL=208128 -DMOD_PERL -DUSE_PERL_SSI -D_REENTRANT  -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DUSE_HSREGEX -DEAPI -DUSE_EXPAT -I./lib/expat-lite `./apaci` modules.c
gcc -c -I. -I/usr/lib/perl/5.8/CORE -I./os/unix -I./include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DMOD_SSL=208128 -DMOD_PERL -DUSE_PERL_SSI -D_REENTRANT  -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DUSE_HSREGEX -DEAPI -DUSE_EXPAT -I./lib/expat-lite `./apaci` buildmark.c
gcc  -DLINUX=22 -DHAVE_SET_DUMPABLE -DMOD_SSL=208128 -DMOD_PERL -DUSE_PERL_SSI -D_REENTRANT  -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DUSE_HSREGEX -DEAPI -DUSE_EXPAT -I./lib/expat-lite `./apaci` -L/usr/src/openssl-0.9.8b  -rdynamic \
	      -o httpd buildmark.o modules.o modules/standard/libstandard.a modules/ssl/libssl.a modules/perl/libperl.a main/libmain.a ./os/unix/libos.a ap/libap.a regex/libregex.a lib/expat-lite/libexpat.a  -lm -lcrypt  -lssl -lcrypto -Wl,-E  -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -ldl -lm -lpthread -lc -lcrypt  -ldl
modules/standard/libstandard.a(mod_include.o): In function `add_include_vars':mod_include.c:(.text+0x11a): undefined reference to `Perl_Gthr_key_ptr'
:mod_include.c:(.text+0x12c): undefined reference to `Perl_Ireentrant_buffer_ptr'
:mod_include.c:(.text+0x140): undefined reference to `Perl_Gthr_key_ptr'
:mod_include.c:(.text+0x152): undefined reference to `Perl_Ireentrant_buffer_ptr'
:mod_include.c:(.text+0x166): undefined reference to `Perl_Gthr_key_ptr'
:mod_include.c:(.text+0x178): undefined reference to `Perl_Ireentrant_buffer_ptr'
:mod_include.c:(.text+0x18c): undefined reference to `Perl_Gthr_key_ptr'
:mod_include.c:(.text+0x19e): undefined reference to `Perl_Ireentrant_buffer_ptr'
:mod_include.c:(.text+0x1dc): undefined reference to `Perl_Gthr_key_ptr'

....

:DynaLoader.c:(.text+0x9d7): undefined reference to `Perl_newSV'
:DynaLoader.c:(.text+0x9fb): undefined reference to `Perl_sv_setuv'
:DynaLoader.c:(.text+0xa18): undefined reference to `Perl_newSVpvn'
:DynaLoader.c:(.text+0xacf): undefined reference to `Perl_croak'
:DynaLoader.c:(.text+0xaed): undefined reference to `Perl_sv_2pv_flags'
:DynaLoader.c:(.text+0xb1f): undefined reference to `Perl_form'
:DynaLoader.c:(.text+0xb36): undefined reference to `Perl_get_sv'
:DynaLoader.c:(.text+0xb6e): undefined reference to `Perl_form'
:DynaLoader.c:(.text+0xb85): undefined reference to `Perl_get_sv'
:DynaLoader.c:(.text+0xbc9): undefined reference to `Perl_sv_2pv_flags'
collect2: ld returned 1 exit status
make[2]: *** [target_static] Error 1
make[2]: Leaving directory `/usr/src/apache_1.3.37/src'
make[1]: *** [build-std] Error 2
make[1]: Leaving directory `/usr/src/apache_1.3.37'
make: *** [build] Error 2
```

---

### Post by hikirsch on 2007-06-06
bump

---

### Post by hikirsch on 2007-06-06
I figured it out, I had to install more libraries, not sure why they didn't install when I installed perl, must be something specific, not entire sure. The command I ran was

```
sudo apt-get install libcompress-zlib-perl libio-socket-ssl-perl liburi-perl libperl5.8
```

I also had to symlink /usr/lib/libperl-5.8.7.so to /usr/lib/libperl.so and i also created /etc/ld.so.conf and put in 
```
/lib
/usr/lib
/usr/local/lib
```

I re-ran make and all went well.

I read about this problem somewhere else and there was no solution, so hopefully people who have been trying to figure this out will be able to fix it now.

---

