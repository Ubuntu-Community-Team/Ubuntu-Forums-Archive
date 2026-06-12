---
title: "postfix, sasl, mysql, and working crypt"
date: 2006-09-18
forum: Server Platforms
---

### Post by akutz on 2006-09-18
I run Ubuntu 6.06.1 LTS Dapper Drake Server.

There are a lot of great HowTos online about how to get postfix to authenticate with mysql using sasl.  Unfortunately the sasl libraries that ship with ubuntu do not include the configuration option:

  ```
password_format
```

This option in the smtpd.conf file lets you specify whether or not the password stored in the mysql table is encrypted.  Since I have no desire to store unencrypted passwords I had to do something about it.

I found this page, [http://frost.ath.cx/software/cyrus-sasl-patches/](http://frost.ath.cx/software/cyrus-sasl-patches/).  I downloaded the cyrus-sasl src (2.1.19) and the checkpw.c patch linked on the page.  Before the source will compile you have to do a few things:

1) create a symlink from ./mac/libdes/public/des.h to ./saslauthd/des.h

```
ln -s ./mac/libdes/public/des.h ./saslauthd/des.h
```

2) comment out line #64 from ./lib/client.c so that a grep -nR "// static" looks like:

  ```
lib/client.c:64:// static sasl_global_callbacks_t global_callbacks;
```

This is necessary because the patch redefines the global_callbacks declaration.

3) export new CPPFLAGS to point to the mysqlclient headers (apt-get install libmysqlclient15-dev)

```
CPPFLAGS="-I/usr/include/mysql"
```

Now you should be able to build the source.  I used this configure line:

  ```
./configure --enable-anon --enable-plain --enable-login --enable-sql --disable-digest --with-mysql=/usr/include/mysql/ --with-plugindir=/usr/lib/sasl2/
```

This line turns nothing off except the digest mech (which fails to build in ubuntu by default) and enables some basic options.

Now run make.

Check the webpage I mentioned you will see that one of the password formats that this patch adds to the mix is 'crypt_trad' so we grep for 'crypt_trad' and find that the .so file that contains the new code is none other than the big kahuna libsasl2.so.2.0.19.  libsasl2.so.2.0.19 is located at ./lib/libs/libsasl2.so.2.0.19.

First rename the production copy of this file with:

  ```
mv /usr/lib/libsasl2.so.2.0.19 /usr/lib/libsasl2.so.2.0.19.old

```
Now copy the new file over

  ```
mv ./lib/.libs/libsasl2.so.2.0.19 /usr/lib
```

Now restart postfix

  ```
/etc/init.d/postfix restart
```

Ok.  You should now be able to include the password_format directive in yoru smtpd.conf file and select crypt.

I have done this and it works for me.  I only use SASL for Courier IMAP and Postfix, so I cannot guarantee that replacing the stock libsasl2.so.2.0.19 file won't break what you have, but I can assure you that it does not break Courier IMAP or Postfix.

-- EDIT --

I've attached the end-result libsasl2.so.2.0.19.  You can just copy this to /usr/lib.

---

### Post by chrisfay on 2006-09-18
This may be better suited for the 'HowTo' section.....

---

### Post by pieps on 2007-10-26
I'm trying to get this to work, but I'm having two problems:

First, I needed to softlink to des.h using the full path to the source, otherwise the link was looking for "./mac/libdes/public/des.h" in ./saslauthd/

After fixing that, everything compiles fine, but when I try to run postfix, it gives me the following error repeated a bunch of times:
[B]
postconf: /usr/lib/libsasl2.so.2: no version information available (required by postconf)[/B]


I'll admit that I'm not horribly familiar with Postfix or Linux libraries.  Is there a flag to pass to configure that will add version information to the library? Is this possibly a problem with my Postfix configuration?

Thanks!

---

