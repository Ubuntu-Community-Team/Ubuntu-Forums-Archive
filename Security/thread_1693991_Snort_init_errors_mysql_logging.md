---
title: "Snort init errors mysql logging?"
date: 2011-02-23
forum: Security
---

### Post by tbaror on 2011-02-23
Hello All,

I have just complied Snort 2.9.0.4 under Ubuntu 10.10 x86_64 installed with all Lamp package.
The syntax i used to compile Snort as follows below
*********************************************
~/snort-2.9.0.4# ./configure --with-mysql —prefix=/usr/local/snort  —enable-ipv6 —enable-gre \-enable-mpls -enable-targetbased  —enable-decoder-preprocessor-rules \-enable-ppm -enable-perfprofiling  —enable-zlib —enable-active-response \-enable-normalizer —enable-reload  —enable-react —enable-flexresp3
***********************************************
in snort.conf i set log as follow
**************************************************  ******************
output database: log, mysql, user=snort password=password dbname=snort host=localhost sensor_name=gfn-sec-sn1
**************************************************  ******************

now when i run snort " /usr/local/snort/bin/snort -c /etc/snort/snort.conf -i eth2"

I get following error
**************************************************  **********
Log directory = /var/log/snort
database: ‘mysql’ support is not compiled into this build of snort

ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
‘mysql’ support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the ‘—with-mysql’ switch.
For non-standard installations of a database, the ‘—with-mysql=DIR’
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..
**************************************************  **********

Since i am not so expert with Linux should i point somewhere for MySQL or i missed something.
should i fill something with following below section 
```

--with-mysql=DIR               Support for MySQL
  --with-mysql-includes=DIR      MySQL include directory
  --with-mysql-libraries=DIR     MySQL library directory

```
when i am using ```
whereis mysql
``` i get this but i dont know wich is the right to add
```
mysql: /usr/bin/mysql /etc/mysql /usr/lib/mysql /usr/lib64/mysql /usr/include/mysql /usr/share/mysql /usr/share/man/man1/mysql.1.gz
```

Please Advice

Thanks         
                                                                                                                                                [URL="http://www.howtoforge.com/forums/editpost.php?do=editpost&p=251999"]
[/URL]

---

### Post by bodhi.zazen on 2011-02-23
Just add --with-mysql to the list, you do not need to specify the rest unless you are using a non-default location for the various libs / includes (which you are not).

---

### Post by tbaror on 2011-02-24
> **bodhi.zazen said:**
> Just add --with-mysql to the list, you do not need to specify the rest unless you are using a non-default location for the various libs / includes (which you are not).

but this is what i did in the first place only simple --with-mysql ant yet.

---

