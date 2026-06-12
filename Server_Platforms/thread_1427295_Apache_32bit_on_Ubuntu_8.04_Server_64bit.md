---
title: "Apache 32bit on Ubuntu 8.04 Server 64bit"
date: 2010-03-11
forum: Server Platforms
---

### Post by michaelcoon on 2010-03-11
Hi,
i have to setup an a little bit odd server ;-(
It has to be an Ubuntu 8.04 Server 64bit with an Apache 32bit.
I first tested ubuntu 8.04 32bit and apache 32bit which works fine and very easy, also ubuntu 64bit and apache 64bit is easy to install, but i try since 2 days to get the 32bit bit version of apache working on an 64bit ubuntu.

Here is what i have done:
- installing ubuntu 64bit server 8.04, only ssh and samba server ticked during the installation.
- apt-get install build-essential
- apt-get install libc6-dev-i386
- wget [http://archive.apache.org/dist/httpd/httpd-2.2.8.tar.gz](http://archive.apache.org/dist/httpd/httpd-2.2.8.tar.gz)
- tar xvfz httpd-2.2.8.tar.gz
- cd httpd-2.2.8
- export CFLAGS=-m32
- export CPPFLAGS=-m32
- ./configure --prefix=/usr/local/apache2 --build=i686-unknown-linux-gnu --enable-mode-shared=all build_alias=i686-unknown-linux-gnu --enable-modules=all --enable-mods-shared=all

I always get this error message:

checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr

attached is the config.log

I found various things via google but nothing solved my problem to bring 32bit apache on this 64bit system. I hope some of you can help me.

Thanks Michael

---

### Post by HubertB on 2010-03-11
I can't help you with your compilation problem, but another solution would be to create a 32-bit chroot on your 64 bit system and install the 32-bit-apache inside the 32-bit-chroot via apt-get.

---

### Post by michaelcoon on 2010-03-12
Hi HubertB,
i thought about it as well but i finally hope i can get it working without the chroot.
But would it be possible to compile the apache in this chroot on my own or can i only install it via apt-get ?

- Michael

> **HubertB said:**
> I can't help you with your compilation problem, but another solution would be to create a 32-bit chroot on your 64 bit system and install the 32-bit-apache inside the 32-bit-chroot via apt-get.

---

### Post by zander1013 on 2010-03-12
this is only speculation but you might have to pass the compiler a switch to produce 32 bit code for your machine.

consult man gcc for you system.

perhaps there is an option you can add to ./configure that will cause it to produce 32 bit a.out. (this would be the best)

otherwise the error is telling you the compiler cannot produce 32 bit code. 

you have to get a 64 bit gcc that can produce 32 bit code for a 64 bit chip. i don't know if that is available but your man page would tell you for sure.

---

### Post by HubertB on 2010-03-12
> **michaelcoon said:**
> Hi HubertB,
i thought about it as well but i finally hope i can get it working without the chroot.
But would it be possible to compile the apache in this chroot on my own or can i only install it via apt-get ?

- Michael

You should be able to do both ways within the chroot (apt-get install or compile it ourself). I would consider using apt-get since it's not so painfull ;-)

---

### Post by zander1013 on 2010-03-12
after consulting gcc man pages on my system the compiler can be directed to produce 32 or 64 bit executables for specific architectures. specifically i saw that it can be give a switch to produce -m32 or -m64 for mips 32 or 64 bit chips. and similar options for powerpc.

you will have to dig around for the options relevant for your system.

the best way to compile it for yourself is using the ./configure with an option to specify the build for 32 bit eventhough you are on a 64 bit machine.

if you succeed in doing this i am not confident you can run the 32 bit code on you 64 bit machine but i have never had a 64 bit computer so i have no experience running 32 bit a.out on a 64 bit chip.

but i know for sure one cannot run a 64 bit a.out on a 32 bit machine because i have tried.:rolleyes:

---

### Post by michaelcoon on 2010-03-18
Just to let you know, i got it working this way:

installing ubuntu 64bit server 8.04, only ssh and samba server ticked during the installation.
apt-get install g++-multilib --yes
apt-get install build-essential --yes
apt-get install openssl
apt-get install zlib1g-dev
apt-get install libcurl4-openssl-dev --yes
apt-get install ia32-libs --yes
apt-get install zlibc
ln -s /usr/lib32/libz.so.1 /usr/lib32/libz.so

wget http://archive.apache.org/dist/httpd/httpd-2.2.8.tar.gz
tar xvfz httpd-2.2.8.tar.gz
cd httpd-2.2.8

CFLAGS="-m32" CPPFLAGS="-m32" LDFLAGS="-L/usr/lib32" ./configure --prefix=/usr/local/apache2 --build=i686-unknown-linux-gnu --enable-mode-shared=all build_alias=i686-unknown-linux-gnu --enable-modules=all --enable-mods-shared=all --enable-so --enable-rewrite --enable-auth-digest=shared --enable-proxy --enable-deflate
make
make install

---

