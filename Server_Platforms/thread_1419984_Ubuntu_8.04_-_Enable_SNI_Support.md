---
title: "Ubuntu 8.04 - Enable SNI Support"
date: 2010-03-02
forum: Server Platforms
---

### Post by ka4bo on 2010-03-02
Hey,

I hope that this thread will not encounter on disapproval. But all my trying had no success, in about 2 month, including searching the web and posting in other forums (nobody answers).

I have an Ubuntu Server 8.04 and I really need SNI Support in this version. So I tried to compile a newer version of the Apache Server ( > 2.2.12 or 2.2.8 with a patch) in conjunction with a compatible OpenSSL Version that supports the tlsext option. It just did not work - in all combinations.

I also found this thread:
[http://ubuntuforums.org/showthread.php?t=1145086](http://ubuntuforums.org/showthread.php?t=1145086)

But it seems, that the instructions are not for 8.04, at least it doesn't work, too.

Can someone give me a description on how to get SNI Support in 8.04, please? Each tip would help me a lot.

Thank you in advance!

Best regards!
ka4bo

---

### Post by ka4bo on 2010-03-04
Perhaps, somebody has a better solution. But this is the way I did:

The Prerequisites to compile are:

```
sudo apt-get install build-essential linux-headers-`uname -r` zlib1g-dev libssl-dev
```I prefered this directory for work:

```

cd /usr/src
sudo -s

```I choose the newest Version of Apache and OpenSSL:

```
wget http://www.openssl.org/source/openssl-0.9.8m.tar.gz
wget http://ftp.halifax.rwth-aachen.de/apache/httpd/httpd-2.2.14.tar.gz

tar zxf openssl-0.9.8m.tar.gz
tar zxf httpd-2.2.14.tar.gz

```Beginning with OpenSSL:

```
cd openssl-0.9.8m
```On 32-Bit choose this configuration:

```
./config no-shared no-dso --openssldir=/usr/lib/ssl
```And on 64-Bit:

```
./config -fPIC no-shared no-dso --openssldir=/usr/lib/ssl
```The options no-shared and no-dso ensures, that the compiler generates only static libraries without any additional Dependencies - this will avoid problems with an existing libssl.so.

Next step compiles OpenSSL and creates a link which is needed to compile the Apache:

```
make build_libs
ln -s . lib
```Then go on with the Apache:

```
cd ../httpd-2.2.14
./configure --enable-layout=Debian --enable-ssl --with-ssl=../openssl-0.9.8m --enable-mods-shared=all --enable-deflate --with-program-name=apache2

```Important are --enable-ssl and --with-ssl. The rest can be configured as you like.

Last but not least you might to compile and install the Apache on your system:

```
make
make install
```Unfortunately log_config_module is missing. So in most case you couldn't start the Apache, because Attributes like LogFormat are used in apache2.conf. To solve this problem you can add this line to your apache2.conf:

```
LoadModule log_config_module /usr/lib/apache2/modules/mod_log_config.so
```After all you have an SNI-Enabled Apache on your system. The disadvantage is, that you will not receive any updates. This might be a problem on a productive machine. So be carefull!

Best Regards,
ka4bo

---

