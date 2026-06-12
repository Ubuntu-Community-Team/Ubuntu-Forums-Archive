---
title: "Jynx2 won't compile"
date: 2012-10-03
forum: Security
---

### Post by Stonecold1995 on 2012-10-03
I'm trying to run the Jynx userlevel rootkit in different distros in VirtualBox (just out of curiosity), but I'm having trouble compiling it.

```
alex@virtualbox:~/jynx2$ make
gcc -m64 jynx2.c -Wall -shared -fPIC -ldl -lssl -o jynx2.so
jynx2.c:16:25: fatal error: openssl/ssh.h: No such file or directory
compilation terminated
make: *** [jynx2.so] Error 1
```

I have a very basic understanding of C, but I still don't understand why this header isn't available.  It's coming from this line in jynx2.c:

```
#include <openssl/ssl.h>
```

I looked through the CoC and couldn't find anything against this btw, but correct me if I'm wrong.  I'm not trying to use this for malicious purposes.

---

### Post by SeijiSensei on 2012-10-03
You need to install [libssl-dev]("http://packages.ubuntu.com/precise/libssl-dev").  That includes the various libraries and header files for OpenSSL.

You'll likely encounter other missing -dev dependencies along the way.  You'll need to track them down by hand since there is no version of this program in the Ubuntu repositories.  If you are building a package from source that does have a repository version, you can use the convenient command "apt-get build-dep packagename" which will install all the dependencies associated with "packagename."  For software with no existing Ubuntu build, you're on your own.

---

### Post by Stonecold1995 on 2012-10-03
Thank you.

Also, how realistic of a threat do rootkits like Jynx pose?  It's a userland rootkit so it doesn't even require root access to infect a computer.

---

