---
title: "OpenVPN Installation and Configuration"
date: 2005-08-03
forum: Server Platforms
---

### Post by rotten777 on 2005-08-03
I've tried this twice. Just to make sure I'm not doing anything stupid, I figured I'd post it on here.


apt-get install openvpn 
successful

apt-get install openssl
successful


As per [the openvpn guide](http://openvpn.net/howto.html#pki), i've done this:

cd /usr/share/doc/openvpn/examples/easy-rsa
nano -w vars


the only stuff changed is there bottom section (location details)
```
export D=/root/openvpn/20/openvpn/tmp/easy-rsa

# Edit this variable to point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=$D/openssl.cnf

# Edit this variable to point to
# your soon-to-be-created key
# directory.
#
# WARNING: clean-all will do
# a rm -rf on this directory
# so make sure you define
# it correctly!
export KEY_DIR=$D/keys

# Increase this to 2048 if you
# are paranoid.  If you do increase,
# make sure you build OpenVPN with
# pthread support, so you don't incur
# any performance penalty.
export KEY_SIZE=1024

# These are the default values for fields
# which will be placed in the certificate.
export KEY_COUNTRY=US
export KEY_PROVINCE=Florida
export KEY_CITY=Sebring
export KEY_ORG="YDI"         
export KEY_EMAIL="matt@yourdatainc.net" 

``` 

. ./vars

then i run THIS:
./clean-all

and get THIS:
```
mkdir: cannot create directory `/root/openvpn/20/openvpn/tmp/easy-rsa/keys': No such file or directory
``` 

I stop there. It seems as if the "vars" file is pointing to the wrong location. Anyone know where I need to point this thing to?

Any help is appreciated.

---

### Post by clarkie141082 on 2005-08-15
Run it as sudo

---

### Post by rotten777 on 2005-08-15
that was all run as root.

---

### Post by relix42 on 2005-08-17
> 
then i run THIS:
./clean-all

and get THIS:
```
mkdir: cannot create directory `/root/openvpn/20/openvpn/tmp/easy-rsa/keys': No such file or directory
``` 

I stop there. It seems as if the "vars" file is pointing to the wrong location. Anyone know where I need to point this thing to?

Any help is appreciated.

If you can locate the mkdir in the clean-all script and change it to 'mkdir -p' it should create any required parent directories of the ultimate child.

No idea if this will help, but, may get you a step further.

---

### Post by rotten777 on 2005-08-23
that got me one step further. now here is where i stand.

```
root@rbu:/usr/share/doc/openvpn/examples/easy-rsa # ./build-ca 
error on line -1 of /root/openvpn/20/openvpn/tmp/easy-rsa/openssl.cnf
25607:error:02001002:system library:fopen:No such file or directory:bss_file.c:104:fopen('/root/openvpn/20/openvpn/tmp/easy-rsa/openssl.cnf','rb')
25607:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:107:
25607:error:0E064072:configuration file routines:CONF_load:no such file:conf_def.c:197:



root@rbu:/usr/share/doc/openvpn/examples/easy-rsa # cat /root/openvpn/20/openvpn/tmp/easy-rsa/openssl.cnf

cat: /root/openvpn/20/openvpn/tmp/easy-rsa/openssl.cnf: No such file or directory

root@rbu:/usr/share/doc/openvpn/examples/easy-rsa # cat build-ca 
#!/bin/bash

#
# Build a root certificate
#

if test $KEY_DIR; then
        cd $KEY_DIR && \
        openssl req -days 3650 -nodes -new -x509 -keyout ca.key -out ca.crt -config $KEY_CONFIG
else
        echo you must define KEY_DIR
fi
```


looks as if $KEY_DIR is not set. I didn't see this mentioned in the server setup. is this a piece of SSL?

---

### Post by FishFoot on 2005-09-11
I had the same problem.  The solution was to simply gunzip the openssl.cnf.gz file that was in the directory.  I'm not really sure why this wasn't unzipped but... well... whatever.

```

sudo gunzip /etc/openvpn/openssl.cnf.gz
sudo /etc/openvpn/build-ca

```

That got me further.

I'm attempting to write a complete guide to setting up OpenVPN in Ubuntu.  I want to post it to the wiki.  The way I see it, we aren't complete until there is a quick installation of a vpn system.

---

### Post by rotten777 on 2005-09-12
sounds good. I will attempt to get past this tomorrow when I get to the office.

thanks for your help

---

### Post by rotten777 on 2005-09-12
I had to issue this command:

```
cp /usr/share/doc/openvpn/examples/easy-rsa/openssl.cnf /root/openvpn/20/openvpn/tmp/easy-rsa/
```

---

