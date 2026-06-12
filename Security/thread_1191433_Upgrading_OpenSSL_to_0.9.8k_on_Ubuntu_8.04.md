---
title: "Upgrading OpenSSL to 0.9.8k on Ubuntu 8.04"
date: 2009-06-18
forum: Security
---

### Post by tvongaza on 2009-06-18
I'm trying to upgrade my OpenSSL to pass a security audit for our merchant provider.  The latest version in 8.04 is 0.9.8g and I need to upgrade to at least 0.9.8h.  When I try to compile the latest source manually and install with checkinstall I get the following error:

```

cd openssl-0.9.8k
./config
make
make test
checkinstall

```

```

created directory `/usr/local/ssl/certs'
created directory `/usr/local/ssl/private'
chmod: changing permissions of `/usr/local/ssl/include/openssl/e_os2.h': No such file or directory
make: *** [install_sw] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

Does anyone know how I can get the latest version installed?  Thanks!

Tys von Gaza

---

### Post by cdenley on 2009-06-19
Why are you installing the latest version from source? What's wrong with ubuntu's *supported* package?

---

### Post by kevdog on 2009-06-21
There is a newer 1.0beta release more recent than the k release.

In my opinion checkinstall is the biggest piece of crap I've ever run across that makes fake .deb files that can then be later dealt with by synaptic,etc.  

Here is what I would do:

./configure
make 
make test
sudo make install

You can always uninstall it later with sudo make uninstall.

It should work this way.

---

