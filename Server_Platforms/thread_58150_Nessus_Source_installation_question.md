---
title: "Nessus Source installation question"
date: 2005-08-19
forum: Server Platforms
---

### Post by Aussiein on 2005-08-19
Hi All,

I would like to know the experience of anyone who has done Nessus installation from source on Ubuntu 5.04 and possibly help as well.

I know I did Nessus installation with apt-get but the package is not current. According to Nessus book it may be bit slow and difficulty in getting updated plugins in case of installation via distribution package.

 Thanks in advance.

Best regards

Aussiein

---

### Post by gruepig on 2005-08-20
Here's what I did on Debian a few months ago.  I'd be surprised if it's much different in Ubuntu:

get the source

tar xzvf nessus-libraries.tar.gz
cd nessus-libraries
less INSTALL*
./configure
make
make install

cd ..
tar xzvf libnasl.tar.gz
cd libnasl
less INSTALL*
./configure
make
make install

cd ..
tar xzvf nessus-core.tar.gz
cd nessus-core
less INSTALL*
./configure (use --disable-gtk if appropriate)
make
make install

cd ..
tar xzvf nessus-plugins.tar.gz
cd nessus-plugins
less INSTALL*
./configure
make
make install

echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig

/usr/local/bin/nesus-fetch --register <key> (key is obtained by registering via the nessus.org website)
/usr/local/sbin/nessus-update-plugins -v

/usr/local/sbin/nessus-adduser
edit /usr/local/var/nessus/users/nessus/auth/rules

review /usr/local/etc/nessus/nessusd.conf and /usr/local/etc/nessus/nessusd.rules and edit as needed

create /etc/init.d/nessusd (I used the script from the Debian package and modified the  paths as needed: DAEMON=/usr/local/sbin/nessusd, PIDFILE=/usr/local/var/nessus/nessusd.pid)
update-rc.d nessusd defaults
/etc/init.d/nessusd start

Hope this helps.  Let me know if you need anything else.

---

### Post by Aussiein on 2005-08-20
Hi gruepig,

Many thanks for the efforts taken to write to me. 

When I tried doing the same I got several errors for example "configure error: could not find openssl and openssl header on your system". ./configure stopped processing afterwards.


Best regards

Naveen

---

### Post by gruepig on 2005-08-20
Install the ssl header files with 'apt-get install libssl-dev' and try again. You may also need to install the openssl package and some version of libssl.

---

### Post by PyMeH on 2008-03-26
Where can I find the nessus sources?

---

### Post by Griff on 2008-03-26
> **PyMeH said:**
> Where can I find the nessus sources?
This is a super ancient thread, but you can find it here:
[http://www.nessus.org/download/](http://www.nessus.org/download/)

---

