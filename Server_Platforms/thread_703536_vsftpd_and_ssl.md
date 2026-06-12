---
title: "vsftpd and ssl"
date: 2008-02-21
forum: Server Platforms
---

### Post by revival on 2008-02-21
Hi,

I am trying to compile the vsftpd binary with support for ssl.
I changed the builddefs.h to include #define VSF_BUILD_SSL
but I get an error when make tries to to compile the file ssl.c:

A part of the error after the make:

....
gcc -c access.c -O2 -Wall -W -Wshadow -idirafter dummyinc
gcc -c features.c -O2 -Wall -W -Wshadow -idirafter dummyinc
gcc -c readwrite.c -O2 -Wall -W -Wshadow -idirafter dummyinc
gcc -c ssl.c -O2 -Wall -W -Wshadow -idirafter dummyinc
ssl.c:27:25: error: openssl/err.h: No such file or directory
ssl.c:28:26: error: openssl/rand.h: No such file or directory
ssl.c:29:25: error: openssl/bio.h: No such file or directory
ssl.c:32: error: syntax error before '*' token
ssl.c:32: warning: type defaults to 'int' in declaration of 'get_ssl'
....

The ssl files that are needed are located at /usr/local/ssl/include/openssl

I added /usr/local/ssl/include/openssl to the path and the errors did not change. I also included /usr/local/ssl/include/openssl in the INCLUDE environment variable.

I also tried to change the make. Vsftpd make currently has:

**CFLAGS = -O2 -Wall -W -Wshadow**
and I changed it for 
**CFLAGS = -O2 -Wall -W -Wshadow -I/usr/local/ssl/include/**


A chunk of the output after the make:

**From the ssl.c file. ( I added the line numbers at line 24.)**
/*
* ssl.c
* Routines to handle a SSL/TLS-based implementation of RFC 2228, i.e.
* encryption.
*/

#include "ssl.h"
#include "session.h"
#include "ftpcodes.h"
#include "ftpcmdio.h"
#include "defs.h"
#include "str.h"
#include "sysutil.h"
#include "tunables.h"
#include "utility.h"
#include "builddefs.h"

#ifdef VSF_BUILD_SSL

[B]#include <openssl/ssl.h>
#include <openssl/err.h>
#include <openssl/rand.h>
#include <openssl/bio.h>[/B]

static char* get_ssl_error();
static SSL* get_ssl(struct vsf_session* p_sess, int fd);
static int ssl_session_init(struct vsf_session* p_sess);


Any one has any idea? 

Thanks!

---

### Post by revival on 2008-02-25
anyone played with vsftpd and ssl before?

---

### Post by faulkes on 2008-02-25
> **revival said:**
> Hi,

The ssl files that are needed are located at /usr/local/ssl/include/openssl
 
I also tried to change the make. Vsftpd make currently has:

**CFLAGS = -O2 -Wall -W -Wshadow**
and I changed it for 
**CFLAGS = -O2 -Wall -W -Wshadow -I/usr/local/ssl/include/**
!

Try:

```

**CFLAGS = -O2 -Wall -W -Wshadow -I/usr/local/ssl/include/ -I/usr/local/ssl/include/openssl/**

```

---

### Post by revival on 2008-02-25
[COLOR="Black"]ok, now I get the error in another file: 

make
gcc -c sysutil.c -O2 -Wall -W -Wshadow -I /usr/local/ssl/include/openssl/ -I/usr/local/ssl/include/  -idirafter dummyinc
sysutil.c: In function 'vsf_sysutil_wait_exited_normally':
sysutil.c:604: error: assignment of read-only member '__in'
sysutil.c: In function 'vsf_sysutil_wait_get_exitcode':
sysutil.c:614: error: assignment of read-only member '__in'
make: *** [sysutil.o] Error 1
[/COLOR]

---

