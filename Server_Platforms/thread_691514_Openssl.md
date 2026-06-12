---
title: "Openssl"
date: 2008-02-08
forum: Server Platforms
---

### Post by mattc908 on 2008-02-08
Hey i have been trying to install OpenSSL but when I follow these steps I get an error
OPENSSL
$tar -zxf openssl-0.9.8b.tar.gz 
$cd openssl-0.9.8b 
$./config shared 
$make 
$make test 
#make install 
# echo "/usr/local/ssl/lib" >> /etc/ld.so.conf 
#ldconfig

I get past .config part but when I do sudo make, I get the following errors:
sudo make
```
making all in crypto...
make[1]: Entering directory `/usr/local/src/openssl-0.9.8b/crypto'
gcc -I. -I.. -I../include -fPIC -DOPENSSL_PIC -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o cryptlib.o cryptlib.c
make[1]: gcc: Command not found
make[1]: *** [cryptlib.o] Error 127
make[1]: Leaving directory `/usr/local/src/openssl-0.9.8b/crypto'
make: *** [build_crypto] Error 1

```

Anyone know why?

---

### Post by faulkes on 2008-02-08
> 
make[1]: gcc: Command not found


you do not have gcc in your path or it is not installed on your server.

GCC being the gnu c compiler.

Faulkes

---

### Post by mattc908 on 2008-02-08
Note: Before installing CYRUS, you should know that mysql libraries are assumed to be 
stored in /usr/local/mysql/lib/mysql and header files  are in /usr/local/mysql/include/mysql 
directories. If you are using Redhat, your mileage may differ a little bit. Yours will be probably 
in /usr/lib/mysql or something like that. So don't panic if cyrus displays errors about libraries then start 
looking for where your libraries are stored.

I dont think its stored there for ubuntu is it?

---

### Post by faulkes on 2008-02-08
You shouldn't be compiling as root or setting variables as root, the "make install" will or
should take care of setting appropriate permissions and what not.

export is a shell (sh/bash) command and not relevant for sudo purposes, you should just try

```

export CPPFLAGS="-I/usr/local/mysql/include/mysql"

```

If you are hand compiling software and need to set an environment variable, use the above.

Faulkes

---

### Post by mattc908 on 2008-02-08
Okay and another question: It says to run the following:
$./configure \ 
--enable-anon \ 
--enable-plain \ 
--enable-login \ 
--enable-sql \ 
--disable-krb4 \ 
--disable-otp \ 
--disable-cram \ 
--disable-digest \ 
--with-mysql=/usr/local/mysql/lib/mysql \ 
--without-pam \ 
--without-saslauthd \ 
--without-pwcheck \ 
--with-dblib=berkeley \ 
--with-bdb-libdir=/usr/local/bdb/lib \ 
--with-bdb-incdir=/usr/local/bdb/include \ 
--with-openssl=/usr/local/ssl \ 
--with-plugindir=/usr/local/lib/sasl2 

Should I just paste that into the command window?

---

### Post by faulkes on 2008-02-08
If those are the options it suggests you pass to configure (or the options you have selected) then yes, you paste that into your terminal window and that should start the configuration process.

Is there a reason you are hand comipling the software?

---

### Post by mattc908 on 2008-02-08
Wait what you do mean how would you go about compiling the software?

---

### Post by faulkes on 2008-02-08
> **mattc908 said:**
> Wait what you do mean how would you go about compiling the software?

I'm just wondering if a cyrus-imapd package already exists which could be installed, rather than a hand compile.

Edit: url changed, this is for feisty, which seems the last compile.
i.e.
[https://launchpad.net/ubuntu/feisty/i386/cyrus21-imapd/2.1.18-5ubuntu1](https://launchpad.net/ubuntu/feisty/i386/cyrus21-imapd/2.1.18-5ubuntu1)

Faulkes

---

### Post by faulkes on 2008-02-08
and a little more searching on my part turned up the gutsy version

[https://launchpad.net/ubuntu/gutsy/i386/cyrus-imapd-2.2/2.2.13-11ubuntu1](https://launchpad.net/ubuntu/gutsy/i386/cyrus-imapd-2.2/2.2.13-11ubuntu1)

Faulkes

---

### Post by mattc908 on 2008-02-08
How would I make a symbolic link for this * WARNING:
* Plugins are being installed into /usr/local/lib/sasl2,
* but the library will look for them in /usr/lib/sasl2.
* You need to make sure that the plugins will eventually
* be in /usr/lib/sasl2 -- the easiest way is to make a
* symbolic link from /usr/lib/sasl2 to /usr/local/lib/sasl2,
* but this may not be appropriate for your site, so this
* installation procedure won't do it for you.

Would this be correct coding? 
ln -s /usr/local/lib/sasl2 /usr/lib/sasl2

---

### Post by faulkes on 2008-02-08
> **mattc908 said:**
> 
Would this be correct coding? 
ln -s /usr/local/lib/sasl2 /usr/lib/sasl2

That would be the correct syntax for what it is asking.

Faulkes

---

