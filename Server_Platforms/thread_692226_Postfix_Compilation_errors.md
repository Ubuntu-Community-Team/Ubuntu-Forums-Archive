---
title: "Postfix Compilation errors"
date: 2008-02-09
forum: Server Platforms
---

### Post by mattc908 on 2008-02-09
I was told to, there are a couple errors and I dont know why


make makefiles 'CCARGS=-DHAS_MYSQL \ 
-I/usr/local/mysql/include/mysql  -DUSE_SASL_AUTH \ 
-I/usr/local/include/sasl -I/usr/local/bdb/include \ 
-DUSE_TLS -I/usr/local/ssl/include/openssl ' \ 
  'AUXLIBS=-L/usr/local/mysql/lib/mysql -lmysqlclient \ 
-lz -lm -L/usr/local/lib -lsasl2  -L/usr/local/bdb/lib\ 
-L/usr/local/ssl/lib -lssl -lcrypto' 

```
mattc908@mattc908:/usr/local/src/postfix-2.4.7$ sudo make makefiles 'CCARGS=-DHAS_MYSQL \ > -I/usr/local/mysql/include/mysql  -DUSE_SASL_AUTH \ 
> -I/usr/local/include/sasl -I/usr/local/bdb/include \ 
> -DUSE_TLS -I/usr/local/ssl/include/openssl ' \ 
make -f Makefile.in MAKELEVEL= Makefiles
(echo "# Do not edit -- this file documents how Postfix was built for your machine."; /bin/sh makedefs) >makedefs.tmp
set +e; if cmp makedefs.tmp conf/makedefs.out; then rm makedefs.tmp; \
	else mv makedefs.tmp conf/makedefs.out; fi >/dev/null 2>/dev/null
set -e; for i in src/util src/global src/dns src/tls src/xsasl src/milter src/master src/postfix src/smtpstone src/sendmail src/error src/pickup src/cleanup src/smtpd src/local src/trivial-rewrite src/qmgr src/oqmgr src/smtp src/bounce src/pipe src/showq src/postalias src/postcat src/postconf src/postdrop src/postkick src/postlock src/postlog src/postmap src/postqueue src/postsuper src/qmqpd src/spawn src/flush src/verify src/virtual src/proxymap src/anvil src/scache src/discard src/tlsmgr; do \
	 (set -e; echo "[$i]"; cd $i; rm -f Makefile; \
	 make -f Makefile.in Makefile MAKELEVEL=) || exit 1; \
	done;
[src/util]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/global]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/dns]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/tls]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/xsasl]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/milter]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/master]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postfix]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/smtpstone]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/sendmail]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/error]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/pickup]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/cleanup]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/smtpd]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/local]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/trivial-rewrite]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/qmgr]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/oqmgr]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/smtp]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/bounce]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/pipe]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/showq]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postalias]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postcat]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postconf]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postdrop]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postkick]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postlock]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postlog]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postmap]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postqueue]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/postsuper]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/qmqpd]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/spawn]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/flush]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/verify]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/virtual]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/proxymap]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/anvil]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/scache]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/discard]
cat ../../conf/makedefs.out Makefile.in >Makefile
[src/tlsmgr]
cat ../../conf/makedefs.out Makefile.in >Makefile
rm -f Makefile; (cat conf/makedefs.out Makefile.in) >Makefile
make: *** No rule to make target ` '.  Stop.
mattc908@mattc908:/usr/local/src/postfix-2.4.7$   'AUXLIBS=-L/usr/local/mysql/lib/mysql -lmysqlclient \ 
> -lz -lm -L/usr/local/lib -lsasl2  -L/usr/local/bdb/lib\ 
> -L/usr/local/ssl/lib -lssl -lcrypto' 
-bash: AUXLIBS=-L/usr/local/mysql/lib/mysql -lmysqlclient \ 
-lz -lm -L/usr/local/lib -lsasl2  -L/usr/local/bdb/lib\ 
-L/usr/local/ssl/lib -lssl -lcrypto: No such file or directory
mattc908@mattc908:/usr/local/src/postfix-2.4.7$ 

```

---

### Post by faulkes on 2008-02-09
It would appear that one of the libraries required to compile is not found.  Ensure that each of the libraries listed exists, especially as you are pointing to /usr/local/lib with the -L argument.

---

