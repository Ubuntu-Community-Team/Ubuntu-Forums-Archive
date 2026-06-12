---
title: "mysql default character set"
date: 2012-01-21
forum: Server Platforms
---

### Post by CapnKirk on 2012-01-21
I'm running mysql on Natty.

My question has to do with UTF-8 handling. On a previous mysql installation (gentoo box) I had a number of settings in my.cnf:
```
default-character-set=utf8
```
and a character set directory was also set.

Are Ubuntu mysql packages compiled so as to handle UTF-8 by default, or are these directives still necessary in my.cnf?

TIA!

Kirk

---

### Post by LHammonds on 2012-01-21
I recently install Ubuntu Server 10.04.3 LTS (64-bit) and used "aptitude" to install MySQL.

When I type "mysql -?" at the prompt, it shows the default character set as latin1

EDIT: If you want to try things out before, use Oracle VirtualBox to setup your OS and application.  It also has a great snapshot feature so you could setup a base OS, create a snapshot and then install whatever packages.  When done testing the packages, simply revert the snapshot and you have a clean OS again. ;)  I have VMware vSphere but it works the same way...however, I have less problems with VMware than VirtualBox, but VirtualBox is free.

LHammonds

---

### Post by CapnKirk on 2012-01-22
That was helpful and told me what I needed to know. It turns out that UTF-8 directives are needed. I used the code I had from my old gentoo box:

```
[mysqladmin]
character-sets-dir       = /usr/share/mysql/charsets
default-character-set    = utf8

[mysqlcheck]
character-sets-dir       = /usr/share/mysql/charsets
default-character-set    = utf8

[mysqldump]
quick
quote-names
max_allowed_packet      = 16M
character-sets-dir       = /usr/share/mysql/charsets
default-character-set    = utf8

[mysqlimport]
character-sets-dir       = /usr/share/mysql/charsets
default-character-set    = utf8

[mysqlshow]
character-sets-dir       = /usr/share/mysql/charsets
default-character-set    = utf8

[mysql]
character-sets-dir       = /usr/share/mysql/charsets
default-character-set    = utf8

[isamchk]
key_buffer              = 16M

[myisamchk]
character-sets-dir       = /usr/share/mysql/charsets

[myisampack]
character-sets-dir       = /usr/share/mysql/charsets


```

Thanks!
Kirk

---

### Post by desconocido on 2012-03-26
I have, as far as I know, default installations of Ubuntu (9.10) and mySQL.

When I use phpMyAdmin and look at the "variables" page of server localhost, I see, amongst other things:

character set client 		utf8				(Global value) 	latin1
character set connection 	utf8				(Global value) 	latin1
character set database 		latin1
character set filesystem 	binary
character set results 		utf8				(Global value) 	latin1
character set server 		latin1
character set system 		utf8
character sets dir 		/usr/share/mysql/charsets/
collation connection 		utf8_general_ci			(Global value) 	latin1_swedish_ci

This mish-mash seems to be a bit odd. Is there any useful reason for having a mixture of Latin1 and utf8?

---

