---
title: "Newer version of Openssh on Ubuntu LTS"
date: 2018-05-09
forum: Security
---

### Post by nelio.oka2 on 2018-05-09
I've read some  tutorials about Ubuntu LTS and it's updates policies. Even so, I'd like to have some confirmation about using the openssh 7.7 (compiled) on Ubuntu 16.04 LTS.
Is it possible? If yes, could someone give me further details about that? If no, this confirmation would be enough for me.
I've tried to do that but had issues.

Thanks and any help will be very appreciated.

---

### Post by raja.genupula on 2018-05-11
Hey, 

Below are the instructions 

```
wget [https://cloudflare.cdn.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-7.7p1.tar.gz](https://cloudflare.cdn.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-7.7p1.tar.gz)
sudo apt-get update
sudo apt-get install build-essential libz-dev libssl-dev -y 
tar -xvzf openssh-7.7p1.tar.gz
cd openssh-7.7p1/
./configure
make
sudo make install
```

and
```

vagrant@ubuntu:~/openssh-7.7p1$ ./ssh -V
OpenSSH_7.7p1, OpenSSL 1.0.1f 6 Jan 2014

```

---

### Post by clearski on 2018-05-23
You might really want to update your OpenSSL first, at least because 1.0.1f is no longer supported.

Also note that due to some API changes, OpenSSL 1.1.x is not supported by OpenSSH 7.7p1, so you could choose to install OpenSSL-1.0.2o and compile OpenSSH against it using *"--with-ssl-dir=DIR" *and *"--with-ssl-engine"*

Here's my quick guide to OpenSSL upgrade (this example uses openssl-1.1.0h):

```
$ sudo apt update && sudo apt upgrade

$ sudo apt install make checkinstall

$ mkdir opensslupgrade

$ cd opensslupgrade

$ wget -4 -c https://www.openssl.org/source/openssl-1.1.0h.tar.gz

$ tar -xzvf openssl-1.1.0h.tar.gz

$ rm openssl-1.1.0h.tar.gz

$ cd openssl-1.1.0h

$ ./config no-deprecated no-ssl no-tls1 no-tls1_1 -no-blake2 -no-camellia -no-cast -no-cmac -no-des -no-dsa -no-idea -no-md4 -no-mdc2 -no-ocb -no-rc2 -no-rc4 -no-rmd160 -no-scrypt -no-seed no-comp enable-ec_nistp_64_gcc_128 enable-egd --prefix=/usr/local/ssl --openssldir=/usr/local/ssl -Wl,-rpath,/usr/local/ssl/lib
```

Edit *./Makefile*, find the line

```
install: install_sw install_ssldirs install_docs

```

and remove *install_docs*.

Test the config:

```
$ make test
```

If everything's fine, create a Debian package that can be easily removed later using *dpkg -r* and install it:

```
All tests successful.
Files=96, Tests=453, 55 wallclock secs ( 0.90 usr  0.20 sys + 40.42 cusr  5.96 csys = 47.48 CPU)
Result: PASS
make[1]: Leaving directory '/home/.../opensslupgrade/openssl-1.1.0h

$ sudo checkinstall

The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: n

Please write a description for the package.
End your description with an empty line or EOF.
>> openssl-1.1.0h-23052018-self-compiled

======================== Installation successful ==========================

Some of the files created by the installation are inside the home directory: /home

You probably don't want them to be included in the package.
Do you want me to list them?  [n]: n
Should I exclude them from the package? (Saying yes is a good idea)  [n]: y

Copying files to the temporary directory...OK
Stripping ELF binaries and libraries...OK
Compressing man pages...OK
Building file list...OK
Building Debian package...OK
Installing Debian package...OK
Erasing temporary files...OK
Writing backup package...OK
OK
Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/.../opensslupgrade/openssl-1.1.0h/openssl_1.1.0h-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r openssl

**********************************************************************
```


List the shared libraries for the newly installed openssl:

```
$ ldd /usr/local/ssl/bin/openssl
    linux-vdso.so.1 (0x00007ffd9538a000)
    libssl.so.1.1 => /usr/local/ssl/lib/libssl.so.1.1 (0x00007fde9ffbe000)
    libcrypto.so.1.1 => /usr/local/ssl/lib/libcrypto.so.1.1 (0x00007fde9fb4f000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fde9f930000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fde9f53f000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fde9f33b000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fdea04c4000)

$ sudo ln -s /usr/local/ssl/bin/openssl /usr/local/bin/openssl

$ openssl version
OpenSSL 1.1.0h  27 Mar 2018
```

To upgrade to a newer OpenSSL version later, repeat the steps above using a newer source archive and don't forget to remove the current version using ```
dpkg -r
```.

You are now ready to install the latest and greatest OpenSSH from source. ;)

---

### Post by deadflowr on 2018-05-23
> You might really want to update your OpenSSL first, at least because 1.0.1f is no longer supported.

Ubuntu Security team patches it.
While it may not be supported by the openssl developers anymore,
as long as the release of Ubuntu is still supported it will get patched.

---

### Post by clearski on 2018-05-26
It's good to know that. :) Thank you.

---

