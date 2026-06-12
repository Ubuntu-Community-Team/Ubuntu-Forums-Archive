---
title: "Compiling Squid? How to run it?"
date: 2010-09-11
forum: Server Platforms
---

### Post by xtrmsound on 2010-09-11
Hi..

I am continuing my journey into the Linux world and I got to say it's kinda great doing things on your own and seeing that everything is working great. 
But here is something that I really don't know what is wrong.

I read Squid's Wiki. I want to add authentication from MYSQL. I succeeded doing the authentication via NCSA_AUT but I want to do it via MYSQL.

I found this line tells me to compile it using this option:
```
**Squid Installation**

 Install squid using your distro package management system or using source. 
Make sure squid is compiled with **--enable-basic-auth-helpers=DB** option. 
```So I removed Squid from my computer via apt-get (I installed it via apt-get)

```
apt-get remove squid squid3
* I tried both
```It removed everything.

I downloaded squid.tar.gz file and extracted it.

and started the compiling like that

```
[B][B]
./configure --enable-basic-auth-helpers=DB --with-logdir=/var/log --with-pidfile=/var/run/squid.pid

[/B][/B]
[B]
It started working and it stopped without any error at all.

after that
[B]make
again no error at all. It took some time as it should.

and 
make install

[/B][/B]
```This is the end of make install

```
/usr/bin/install -c -m 644 ./cachemgr.conf /usr/local/squid/etc/cachemgr.conf.default
install-data-local will not overwrite existing /usr/local/squid/etc/cachemgr.conf
test -z "/usr/local/squid/share/man/man1" || /bin/mkdir -p "/usr/local/squid/share/man/man1"
 /usr/bin/install -c -m 644 './squidclient.1' '/usr/local/squid/share/man/man1/squidclient.1'
make[3]: Leaving directory `/home/almog/squid-3.1.8/tools'
make[2]: Leaving directory `/home/almog/squid-3.1.8/tools'
make[1]: Leaving directory `/home/almog/squid-3.1.8/tools'
make[1]: Entering directory `/home/almog/squid-3.1.8'
make[2]: Entering directory `/home/almog/squid-3.1.8'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/almog/squid-3.1.8'
make[1]: Leaving directory `/home/almog/squid-3.1.8'

```I have 2 folders /etc/squid /etc/squid3  that i renamed the file squid.conf to another name before compiling.

I restored the files when no new file was created. Now I am trying to start it like that

sudo /etc/init.d/squid and with squid3 

It just skips a line

What I did wrong?
Maybe it installs it to a different location and I need to edit the file?

I couldn't find it in the WIKI 

[Compile WIKI]("http://wiki.squid-cache.org/SquidFaq/CompilingSquid#Debian.2C_Ubuntu")
[MYSQL WIKI]("http://wiki.squid-cache.org/ConfigExamples/Authenticate/Mysql")

How do I start it?

---

### Post by xtrmsound on 2010-09-11
I installed it again via apt-get and skipped the part of compiling.
just built a db and set a user and password added the info to the conf file and  it did work and authenticate itself so I succeeded doing it via Mysql.

But still I would like to know what I did wrong with the compile and how to start it.

Thanks

---

