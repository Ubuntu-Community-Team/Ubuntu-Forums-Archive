---
title: "Postfix make install problem"
date: 2010-03-11
forum: Server Platforms
---

### Post by pilotex on 2010-03-11
Hi everyone, First of all sorry for my bad english.

Here is what i do:

make clean

make makefiles CCARGS='-DEF_CONFIG_DIR="/opt/product/postfix-2.6.5/etc"
-DEF_COMMAND_DIR="/opt/product/postfix-2.6.5"
-DEF_DAEMON_DIR="/opt/product/postfix-2.6.5/libexec"
-DEF_MAILQ_PATH="/opt/product/postfix-2.6.5/bin/mailq"
-DEF_DATA_DIR="/opt/product/postfix-2.6.5/lib"
-DEF_NEWALIAS_DIR="/opt/product/postfix-2.6.5/bin/newaliases"
-DEF_QUEUE_DIR="/var/spool/postfix-2.6.5\"
-DEF_SENDMAIL_PATH="/opt/product/postfix-2.6.5/lib/sendmail"
-DHAS_DB="-I/opt/product/[BerkleyDB-4.4.16.NC/include]("http://berkleydb-4.4.16.nc/include")"'
AUXLIBS=\"-R/opt/product/[BerkleyDB-4.4.16.NC/lib]("http://berkleydb-4.4.16.nc/lib") -L/opt/product/[BerkleyDB-4.4.16.NC/lib]("http://berkleydb-4.4.16.nc/lib") -ldb\"'



make install

then i got this error:
postfix: fatal: chdir(/usr/libexec/postfix): No such file or directory
make: *** [install] Error 1

I don't understand why it's checking the usr/libexec folder for the daemons although I've set the folder to /opt/product/postfix-2.6.5/libexec in the makefile.


Here is also the cat of my makedefs.out:
> 
makedefs.out:

# Do not edit -- this file documents how Postfix was built for your machine.
SYSTYPE = SUNOS5
AR      = ar
ARFL    = rv
RANLIB  = echo
SYSLIBS = -lresolv -lsocket -lnsl
CC      = gcc $(WARN) -Dstrcasecmp=fix_strcasecmp                 -Dstrncasecmp=
fix_strncasecmp
OPT     = -O
DEBUG   = -g
AWK     = /usr/xpg4/bin/awk
STRCASE = strcasecmp.o
EXPORT  = AUXLIBS='-R/opt/product/[BerkleyDB-4.4.16.NC/lib]("http://berkleydb-4.4.16.nc/lib") -L/opt/product/Berkley
[DB-4.4.16.NC/lib]("http://db-4.4.16.nc/lib") -ldb' CCARGS='-DEF_CONFIG_DIR="/opt/product/postfix-2.6.5/etc"
-DEF_COMMAND_DIR="/opt/product/postfix-2.6.5"
-DEF_DAEMON_DIR="/opt/product/postfix-2.6.5/libexec"
-DEF_MAILQ_PATH="/opt/product/postfix-2.6.5/bin/mailq"
-DEF_DATA_DIR="/opt/product/postfix-2.6.5/lib"
-DEF_NEWALIAS_DIR="/opt/product/postfix-2.6.5/bin/newaliases"
-DEF_QUEUE_DIR="/var/spool/postfix-2.6.5\"
-DEF_SENDMAIL_PATH="/opt/product/postfix-2.6.5/lib/sendmail"
-DHAS_DB="-I/opt/product/[BerkleyDB-4.4.16.NC/include]("http://berkleydb-4.4.16.nc/include")"' -Dstrcasecmp=fix_strcasec
mp                -Dstrncasecmp=fix_strncasecmp' OPT='-O' DEBUG='-g'


I've folloed the same steps as it was written in the POSTFIX how-to installation but it doesn"t work for me.


Anyone has encountered this error before ?

thanks for your help.

---

### Post by pilotex on 2010-03-12
ok i don't know where the error was in the building of the makefiles but i fixed manually by 
doing postconf -e "daemon_directory=/opt..."

---

