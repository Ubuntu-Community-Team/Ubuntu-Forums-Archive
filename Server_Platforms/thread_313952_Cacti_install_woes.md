---
title: "Cacti install woes"
date: 2006-12-06
forum: Server Platforms
---

### Post by pormogo on 2006-12-06
Hello there everyone recently I have run into some issues trying to get cacti installed on my Ubuntu 6.10 server at work. I was originally trying to get it to run an old G4 Power Mac, however repeated failure at getting graphs to display and a mysql.sock to create has led me back to linux.

So I decided to install cacti just like I would on any other system. First I got LAMP running. (all commands are run as root)

*apt-get -u install apache2*
*apt-get -u install mysql-server*
*apt-get -u install php4*

So now I have apache2 php4 and mysql5 all up and running and by the looks of phpinfo() all playing happily together. So I decided to try installing cacti.

*apt-get -u install cacti*

cacti pulls down and installs (along with some dependencies like dbconf-common, php4-snmp etc). dbconf offers to configure it for me but I decline, as I would rather do it myself. 

So now that everything is installed I get to configuring mysql. First I create the cacti database

*mysqladmin -u root create cacti*

now I create a user to admin that databse

*useradd cactiuser -p userspassword*

I head back into mysql and grant that user permissions to the table 

[i](console)mysql -u root
(mysql)GRANT ALL ON cacti.* TO cactiuser@localhost IDENTIFIED BY 'userspassword';
(mysql)flush privileges;
(mysql)exit[/i]

Looks good to me so far so I head to /usr/shared/cacti/site/include/config.php and add 

$database type = "mysql";
$database_default = "cacti";
$database_hostname = "localhost";
$database_username = "cactiuser";
$database_password = "userspassword";

after that I quickly change the ownership or rra and log to cactiuser

*chown -R cactiuser ./log ./rra*

Now I dump a quick symbolic link in the www root and I'm good to go

[i]cd /var/www
ln -s /usr/share/cacti/site cacti[/i]

done and done, now I run a quick test just to make sure the user is able to connect to the database. 

*mysql -u cactiuser -h localhost -p cacti*

success, it logs into the mysql client and I am able to show tables; and see the cacti table.

So I point my browser to [http://localhost/cacti](http://localhost/cacti) and I get the following error..

*Warning: mysql_pconnect(): Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 372*

hmmmm ok, I'm not exactly the most familiar with ado but I decided to take a look at it anyways, line 372 of adodb-mysql.inc.php reads

* $this->_connectionID = mysql_pconnect($argHostname,$argUsername,$argPassword,$this->clientFlags);*

ummm ok back to being a n00b because I don't know what that means nor how to go about fixing it. thanks for bearing with my lengthy explanation, and thank you in advance for any help you guys are able to provide.

---

### Post by pormogo on 2006-12-13
Still trying to get cacti up and running to no avail I am pretty sure this is an issue I am having with adodb however I don't know how to fix it any help would be most appreciated.

---

### Post by pormogo on 2006-12-18
once more bumping this and praying for some help reposting over to linuxquestions and cacti.net to see if I can get any responses over there.

---

### Post by apoth on 2006-12-20
A couple of things.

Firstly, I'm not sure if you know this or not, but a mysql user with access to database tables is distinct from an operating system level user. So you don't need the useradd command (which adds an OS level user) to have a user account that accesses mysql. The grant privileges command should suffice here.

Next up the error that you're getting is because you've granted privileges for the username cactiuser, but cacti is trying to access the database (through adodb which is just a php->database wrapper here) using the username www-data. This is probably because apache is running as www-data and it's not taken the cactiuser username. Why it hasn't taken the username you put in the config I don't know - maybe you've spelt the variable name they use incorrectly, maybe they've just screwed up their programming.

There's two ways I can see around it for you -
1. Replace $argUsername with "cactiuser" on that line you picked out - to try and force it to use your username (probably a messy path to go down if it uses $argUsername elsewhere to connect - and it probably does).
2. Grant privileges on the database table to www-data - which should be safeish though it's always nice to keep user accounts away from other people's processes.

It'd be nice if the cacti developer(s) fixed it to work with the user you created though.

---

### Post by pormogo on 2006-12-20
I know a mysql user is different then an OS level user however the thought of a user logging in @localhost made me think that perhaps the user would need an account to login @localhost. Thanks for clearing that up though, I'll go ahead and rid myself of that user.

I don't see how I granted permission to cacti and not cactiuser.

[i](console)mysql -u root
(mysql)GRANT ALL ON cacti.* TO cactiuser@localhost IDENTIFIED BY 'userspassword';
(mysql)flush privileges;
(mysql)exit[/i]

I thought that this statement meant something along the lines of, grant all permissions on all tables in the cacti database to the user cactiuser@localhost authenticated by a password. Is this not correct?

you're right apache is running as www-data, in /etc/apache2/apache2.conf there are 2 lines specifying the user and group that apache is running as, if I comment out these lines apache runs unattached to a user account (it runs under ? which i thought was the nobody account but I could be wrong). I don't think that apache is supposed to run under cactiuser, I tried adding a line to apache2.conf telling it to start as that user, but that just ended in it starting as ? again.

I know it uses #argUsername in a whole bunch of other locations within adodb, so I would imagine just chainging that one line would not be sufficient. Would there be any significant risks to using www-data? 

Here's a little update, I think the issue might be due to dbconfig-common something apt installs when you apt-get install cacti to do a database configuration. I found a file called debian.php referenced inside /usr/share/cacti/site/include/config.php

[i]/* make sure these values refect your actual database/host/user/password */
$database_type = "mysql";
$database_default = "cacti";
$database_hostname = "localhost";
$database_username = "cactiuser";
$database_password = "designaire";
**require('/etc/cacti/debian.php');**[/i]

so I located that file in /etc/cacti/debian.php, this file was unpopulated  so I decided to populate the field with relevant data. 

[i]<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/cacti.conf
## by /usr/sbin/dbconfig-generate-include
## Wed, 06 Dec 2006 16:21:12 -0800
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$database_username='cactiuser';
$database_password='password';
$basepath='';
$database_default='';
$database_hostname='localhost';
$dbport='';
$dbtype='mysql';[/i]

Now when I go to [http://address/cacti](http://address/cacti) I just get a blank white page. If I go to the full path [http://address/cacti/install/index.php](http://address/cacti/install/index.php) I get the same thing, I have no idea why, I have php working just fine. Below I pasted my phpinfo();

```
PHP Version 4.4.2-1.1

System 	Linux minerva 2.6.17-10-server #2 SMP Tue Dec 5 22:29:32 UTC 2006 i686
Build Date 	Jun 20 2006 02:24:45
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php4/apache2/php.ini
PHP API 	20020918
PHP Extension 	20020429
Zend Extension 	20050606
Debug Build 	no
Zend Memory Manager 	enabled
Thread Safety 	disabled
Registered PHP Streams 	php, http, ftp, https, ftps, compress.bzip2, compress.zlib

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v1.3.0, Copyright (c) 1998-2004 Zend Technologies

PHP Credits
Configuration
PHP Core
Directive	Local Value	Master Value
allow_call_time_pass_reference	On	On
allow_url_fopen	On	On
always_populate_raw_post_data	Off	Off
arg_separator.input	&	&
arg_separator.output	&	&
asp_tags	Off	Off
auto_append_file	no value	no value
auto_prepend_file	no value	no value
browscap	no value	no value
default_charset	no value	no value
default_mimetype	text/html	text/html
define_syslog_variables	Off	Off
disable_classes	no value	no value
disable_functions	no value	no value
display_errors	On	On
display_startup_errors	Off	Off
doc_root	no value	no value
docref_ext	no value	no value
docref_root	no value	no value
enable_dl	On	On
error_append_string	no value	no value
error_log	no value	no value
error_prepend_string	no value	no value
error_reporting	2039	2039
expose_php	On	On
extension_dir	/usr/lib/php4/20050606	/usr/lib/php4/20050606
file_uploads	On	On
gpc_order	GPC	GPC
highlight.bg	#FFFFFF	#FFFFFF
highlight.comment	#FF8000	#FF8000
highlight.default	#0000BB	#0000BB
highlight.html	#000000	#000000
highlight.keyword	#007700	#007700
highlight.string	#DD0000	#DD0000
html_errors	On	On
ignore_repeated_errors	Off	Off
ignore_repeated_source	Off	Off
ignore_user_abort	Off	Off
implicit_flush	Off	Off
include_path	.:/usr/share/php:/usr/share/pear	.:/usr/share/php:/usr/share/pear
log_errors	Off	Off
log_errors_max_len	1024	1024
magic_quotes_gpc	On	On
magic_quotes_runtime	Off	Off
magic_quotes_sybase	Off	Off
max_execution_time	30	30
max_input_time	60	60
memory_limit	8M	8M
open_basedir	no value	no value
output_buffering	no value	no value
output_handler	no value	no value
post_max_size	8M	8M
precision	12	12
register_argc_argv	On	On
register_globals	Off	Off
report_memleaks	On	On
safe_mode	Off	Off
safe_mode_exec_dir	no value	no value
safe_mode_gid	Off	Off
safe_mode_include_dir	no value	no value
sendmail_from	no value	no value
sendmail_path	/usr/sbin/sendmail -t -i 	/usr/sbin/sendmail -t -i 
serialize_precision	100	100
short_open_tag	On	On
SMTP	localhost	localhost
smtp_port	25	25
sql.safe_mode	Off	Off
track_errors	Off	Off
unserialize_callback_func	no value	no value
upload_max_filesize	2M	2M
upload_tmp_dir	no value	no value
user_dir	no value	no value
variables_order	EGPCS	EGPCS
xmlrpc_error_number	0	0
xmlrpc_errors	Off	Off
y2k_compliance	On	On

apache2handler
Apache Version 	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
Apache API Version 	20020903
Server Administrator 	webmaster@localhost
Hostname:Port 	minerva.berlinerstudio.dom:0
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_cgi mod_php4 mod_userdir

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	192.168.1.17
HTTP_USER_AGENT 	Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.1) Gecko/20061018 Camino/1.1a1
HTTP_ACCEPT 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
HTTP_ACCEPT_LANGUAGE 	en,ja;q=0.9,fr;q=0.9,de;q=0.8,es;q=0.7,it;q=0.7,nl;q=0.6,sv;q=0.5,nb;q=0.5,da;q=0.4,fi;q=0.3,pt;q=0.3,zh-Hans;q=0.2,zh-Hant;q=0.1,ko;q=0.1
HTTP_ACCEPT_ENCODING 	gzip,deflate
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_KEEP_ALIVE 	300
HTTP_CONNECTION 	keep-alive
HTTP_REFERER 	http://192.168.1.17/
PATH 	/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
SERVER_SIGNATURE 	<address>Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 192.168.1.17 Port 80</address>
SERVER_SOFTWARE 	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
SERVER_NAME 	192.168.1.17
SERVER_ADDR 	192.168.1.17
SERVER_PORT 	80
REMOTE_ADDR 	192.168.1.220
DOCUMENT_ROOT 	/var/www
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/info.php
REMOTE_PORT 	53576
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.1
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/info.php
SCRIPT_NAME 	/info.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /info.php HTTP/1.1
Host 	192.168.1.17
User-Agent 	Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.1) Gecko/20061018 Camino/1.1a1
Accept 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language 	en,ja;q=0.9,fr;q=0.9,de;q=0.8,es;q=0.7,it;q=0.7,nl;q=0.6,sv;q=0.5,nb;q=0.5,da;q=0.4,fi;q=0.3,pt;q=0.3,zh-Hans;q=0.2,zh-Hant;q=0.1,ko;q=0.1
Accept-Encoding 	gzip,deflate
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive 	300
Connection 	keep-alive
Referer 	http://192.168.1.17/
HTTP Response Headers
X-Powered-By 	PHP/4.4.2-1.1
Keep-Alive 	timeout=15, max=99
Connection 	Keep-Alive
Transfer-Encoding 	chunked
Content-Type 	text/html; charset=UTF-8

bcmath
BCMath support 	enabled

bz2
BZip2 Support 	Enabled
BZip2 Version 	1.0.3, 15-Feb-2005

calendar
Calendar support 	enabled

ctype
ctype functions 	enabled

dba
DBA support 	enabled
Supported handlers 	gdbm cdb cdb_make db4 inifile flatfile

dbx
dbx support 	enabled
dbx version 	1.0.0
supported databases 	MySQL ODBC PostgreSQL Microsoft SQL Server FrontBase Oracle 8 (oci8) Sybase-CT

Directive	Local Value	Master Value
dbx.colnames_case	unchanged	unchanged

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.118.2.37.2.4 2006/01/01 13:46:52 sniper Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

ftp
FTP support 	enabled

gettext
GetText Support 	enabled

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.4

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

mbstring
Multibyte Support 	enabled
Japanese support 	enabled
Simplified chinese support 	enabled
Traditional chinese support 	enabled
Korean support 	enabled
Russian support 	enabled
Multibyte (japanese) regex support 	enabled

mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.

Directive	Local Value	Master Value
mbstring.detect_order	no value	no value
mbstring.encoding_translation	Off	Off
mbstring.func_overload	0	0
mbstring.http_input	pass	pass
mbstring.http_output	pass	pass
mbstring.internal_encoding	ISO-8859-1	no value
mbstring.language	neutral	neutral
mbstring.substitute_character	no value	no value

mime_magic
mime_magic support	enabled

Directive	Local Value	Master Value
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.24a
MYSQL_MODULE_TYPE 	external
MYSQL_SOCKET 	/var/run/mysqld/mysqld.sock
MYSQL_INCLUDE 	-I/usr/include/mysql
MYSQL_LIBS 	-L/usr/lib -lmysqlclient

Directive	Local Value	Master Value
mysql.allow_persistent	On	On
mysql.connect_timeout	60	60
mysql.default_host	no value	no value
mysql.default_password	no value	no value
mysql.default_port	no value	no value
mysql.default_socket	no value	no value
mysql.default_user	no value	no value
mysql.max_links	Unlimited	Unlimited
mysql.max_persistent	Unlimited	Unlimited
mysql.trace_mode	Off	Off

openssl
OpenSSL support 	enabled
OpenSSL Version 	OpenSSL 0.9.8a 11 Oct 2005

overload
User-Space Object Overloading Support 	enabled

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	6.4 05-Sep-2005

posix
Revision 	$Revision: 1.51.2.4.2.1 $

session
Session Support 	enabled
Registered save handlers 	files user

Directive	Local Value	Master Value
session.auto_start	Off	Off
session.bug_compat_42	On	On
session.bug_compat_warn	On	On
session.cache_expire	180	180
session.cache_limiter	nocache	nocache
session.cookie_domain	no value	no value
session.cookie_lifetime	0	0
session.cookie_path	/	/
session.cookie_secure	Off	Off
session.entropy_file	no value	no value
session.entropy_length	0	0
session.gc_divisor	100	100
session.gc_maxlifetime	1440	1440
session.gc_probability	0	0
session.name	PHPSESSID	PHPSESSID
session.referer_check	no value	no value
session.save_handler	files	files
session.save_path	/var/lib/php4	/var/lib/php4
session.serialize_handler	php	php
session.use_cookies	On	On
session.use_only_cookies	Off	Off
session.use_trans_sid	Off	Off

shmop
shmop support 	enabled

snmp
NET-SNMP Support 	enabled
NET-SNMP Version 	5.2.2

sockets
Sockets Support 	enabled

standard
Regex Library 	Bundled library enabled
Dynamic Library Support 	enabled
Path to sendmail 	/usr/sbin/sendmail -t -i

Directive	Local Value	Master Value
assert.active	1	1
assert.bail	0	0
assert.callback	no value	no value
assert.quiet_eval	0	0
assert.warning	1	1
auto_detect_line_endings	0	0
default_socket_timeout	60	60
safe_mode_allowed_env_vars	PHP_	PHP_
safe_mode_protected_env_vars	LD_LIBRARY_PATH	LD_LIBRARY_PATH
url_rewriter.tags	a=href,area=href,frame=src,input=src,form=,fieldset=	a=href,area=href,frame=src,input=src,form=,fieldset=
user_agent	no value	no value

sysvmsg
sysvmsg support	enabled
Revision 	$Revision: 1.4.2.5.2.2 $

tokenizer
Tokenizer Support 	enabled

wddx
WDDX Support	enabled
WDDX Session Serializer 	enabled

xml
XML Support 	active
XML Namespace Support 	active
EXPAT Version 	expat_1.95.8

xmlrpc
core library version 	xmlrpc-epi v. 0.51
php extension version 	0.51
author 	Dan Libby
homepage 	http://xmlrpc-epi.sourceforge.net
open sourced by 	Epinions.com

yp
YP Support 	enabled

zip
Zip support 	enabled

zlib
ZLib Support 	enabled
Compiled Version 	1.2.3
Linked Version 	1.2.3

Directive	Local Value	Master Value
zlib.output_compression	Off	Off
zlib.output_compression_level	-1	-1
zlib.output_handler	no value	no value

Additional Modules
Module Name
filepro
sysvsem
sysvshm

Environment
Variable	Value
LESSOPEN 	| /usr/bin/lesspipe %s
USER 	root
SSH_CLIENT 	192.168.1.210 53567 22
MAIL 	/var/mail/root
SHLVL 	1
OLDPWD 	/etc/apache2
HOME 	/root
SSH_TTY 	/dev/pts/0
LOGNAME 	root
_ 	/usr/sbin/apache2ctl
TERM 	xterm-color
PATH 	/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
LANG 	en_US.UTF-8
LS_COLORS 	no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SHELL 	/bin/bash
LESSCLOSE 	/usr/bin/lesspipe %s %s
PWD 	/etc/cacti
SSH_CONNECTION 	192.168.1.210 53567 192.168.1.17 22

PHP Variables
Variable	Value
_SERVER["HTTP_HOST"]	192.168.1.17
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.1) Gecko/20061018 Camino/1.1a1
_SERVER["HTTP_ACCEPT"]	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en,ja;q=0.9,fr;q=0.9,de;q=0.8,es;q=0.7,it;q=0.7,nl;q=0.6,sv;q=0.5,nb;q=0.5,da;q=0.4,fi;q=0.3,pt;q=0.3,zh-Hans;q=0.2,zh-Hant;q=0.1,ko;q=0.1
_SERVER["HTTP_ACCEPT_ENCODING"]	gzip,deflate
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_KEEP_ALIVE"]	300
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["HTTP_REFERER"]	http://192.168.1.17/
_SERVER["PATH"]	/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 192.168.1.17 Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
_SERVER["SERVER_NAME"]	192.168.1.17
_SERVER["SERVER_ADDR"]	192.168.1.17
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	192.168.1.220
_SERVER["DOCUMENT_ROOT"]	/var/www
_SERVER["SERVER_ADMIN"]	webmaster@localhost
_SERVER["SCRIPT_FILENAME"]	/var/www/info.php
_SERVER["REMOTE_PORT"]	53576
_SERVER["GATEWAY_INTERFACE"]	CGI/1.1
_SERVER["SERVER_PROTOCOL"]	HTTP/1.1
_SERVER["REQUEST_METHOD"]	GET
_SERVER["QUERY_STRING"]	no value
_SERVER["REQUEST_URI"]	/info.php
_SERVER["SCRIPT_NAME"]	/info.php
_SERVER["PHP_SELF"]	/info.php
_SERVER["PATH_TRANSLATED"]	/var/www/info.php
_SERVER["argv"]	

Array
(
)

_SERVER["argc"]	0
_ENV["LESSOPEN"]	| /usr/bin/lesspipe %s
_ENV["USER"]	root
_ENV["SSH_CLIENT"]	192.168.1.210 53567 22
_ENV["MAIL"]	/var/mail/root
_ENV["SHLVL"]	1
_ENV["OLDPWD"]	/etc/apache2
_ENV["HOME"]	/root
_ENV["SSH_TTY"]	/dev/pts/0
_ENV["LOGNAME"]	root
_ENV["_"]	/usr/sbin/apache2ctl
_ENV["TERM"]	xterm-color
_ENV["PATH"]	/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
_ENV["LANG"]	en_US.UTF-8
_ENV["LS_COLORS"]	no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
_ENV["SHELL"]	/bin/bash
_ENV["LESSCLOSE"]	/usr/bin/lesspipe %s %s
_ENV["PWD"]	/etc/cacti
_ENV["SSH_CONNECTION"]	192.168.1.210 53567 192.168.1.17 22

PHP License

This program is free software; you can redistribute it and/or modify it under the terms of the PHP License as published by the PHP Group and included in the distribution in the file: LICENSE

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

If you did not receive a copy of the PHP license, or have any questions about PHP licensing, please contact license@php.net.

apache2handler
Apache Version 	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
Apache API Version 	20020903
Server Administrator 	webmaster@localhost
Hostname:Port 	minerva.berlinerstudio.dom:0
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_cgi mod_php4 mod_userdir

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	192.168.1.17
HTTP_USER_AGENT 	Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.1) Gecko/20061018 Camino/1.1a1
HTTP_ACCEPT 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
HTTP_ACCEPT_LANGUAGE 	en,ja;q=0.9,fr;q=0.9,de;q=0.8,es;q=0.7,it;q=0.7,nl;q=0.6,sv;q=0.5,nb;q=0.5,da;q=0.4,fi;q=0.3,pt;q=0.3,zh-Hans;q=0.2,zh-Hant;q=0.1,ko;q=0.1
HTTP_ACCEPT_ENCODING 	gzip,deflate
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_KEEP_ALIVE 	300
HTTP_CONNECTION 	keep-alive
HTTP_REFERER 	http://192.168.1.17/
PATH 	/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
SERVER_SIGNATURE 	<address>Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 192.168.1.17 Port 80</address>
SERVER_SOFTWARE 	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
SERVER_NAME 	192.168.1.17
SERVER_ADDR 	192.168.1.17
SERVER_PORT 	80
REMOTE_ADDR 	192.168.1.220
DOCUMENT_ROOT 	/var/www
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/info.php
REMOTE_PORT 	53576
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.1
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/info.php
SCRIPT_NAME 	/info.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /info.php HTTP/1.1
Host 	192.168.1.17
User-Agent 	Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.1) Gecko/20061018 Camino/1.1a1
Accept 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language 	en,ja;q=0.9,fr;q=0.9,de;q=0.8,es;q=0.7,it;q=0.7,nl;q=0.6,sv;q=0.5,nb;q=0.5,da;q=0.4,fi;q=0.3,pt;q=0.3,zh-Hans;q=0.2,zh-Hant;q=0.1,ko;q=0.1
Accept-Encoding 	gzip,deflate
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive 	300
Connection 	keep-alive
Referer 	http://192.168.1.17/
HTTP Response Headers
X-Powered-By 	PHP/4.4.2-1.1
Keep-Alive 	timeout=15, max=99
Connection 	Keep-Alive
Transfer-Encoding 	chunked
Content-Type 	text/html; charset=UTF-8

bcmath
BCMath support 	enabled

bz2
BZip2 Support 	Enabled
BZip2 Version 	1.0.3, 15-Feb-2005

calendar
Calendar support 	enabled

ctype
ctype functions 	enabled

dba
DBA support 	enabled
Supported handlers 	gdbm cdb cdb_make db4 inifile flatfile

dbx
dbx support 	enabled
dbx version 	1.0.0
supported databases 	MySQL ODBC PostgreSQL Microsoft SQL Server FrontBase Oracle 8 (oci8) Sybase-CT

Directive	Local Value	Master Value
dbx.colnames_case	unchanged	unchanged

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.118.2.37.2.4 2006/01/01 13:46:52 sniper Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

ftp
FTP support 	enabled

gettext
GetText Support 	enabled

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.4

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

mbstring
Multibyte Support 	enabled
Japanese support 	enabled
Simplified chinese support 	enabled
Traditional chinese support 	enabled
Korean support 	enabled
Russian support 	enabled
Multibyte (japanese) regex support 	enabled

mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.

Directive	Local Value	Master Value
mbstring.detect_order	no value	no value
mbstring.encoding_translation	Off	Off
mbstring.func_overload	0	0
mbstring.http_input	pass	pass
mbstring.http_output	pass	pass
mbstring.internal_encoding	ISO-8859-1	no value
mbstring.language	neutral	neutral
mbstring.substitute_character	no value	no value

mime_magic
mime_magic support	enabled

Directive	Local Value	Master Value
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.24a
MYSQL_MODULE_TYPE 	external
MYSQL_SOCKET 	/var/run/mysqld/mysqld.sock
MYSQL_INCLUDE 	-I/usr/include/mysql
MYSQL_LIBS 	-L/usr/lib -lmysqlclient

Directive	Local Value	Master Value
mysql.allow_persistent	On	On
mysql.connect_timeout	60	60
mysql.default_host	no value	no value
mysql.default_password	no value	no value
mysql.default_port	no value	no value
mysql.default_socket	no value	no value
mysql.default_user	no value	no value
mysql.max_links	Unlimited	Unlimited
mysql.max_persistent	Unlimited	Unlimited
mysql.trace_mode	Off	Off

openssl
OpenSSL support 	enabled
OpenSSL Version 	OpenSSL 0.9.8a 11 Oct 2005

overload
User-Space Object Overloading Support 	enabled

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	6.4 05-Sep-2005

posix
Revision 	$Revision: 1.51.2.4.2.1 $

session
Session Support 	enabled
Registered save handlers 	files user

Directive	Local Value	Master Value
session.auto_start	Off	Off
session.bug_compat_42	On	On
session.bug_compat_warn	On	On
session.cache_expire	180	180
session.cache_limiter	nocache	nocache
session.cookie_domain	no value	no value
session.cookie_lifetime	0	0
session.cookie_path	/	/
session.cookie_secure	Off	Off
session.entropy_file	no value	no value
session.entropy_length	0	0
session.gc_divisor	100	100
session.gc_maxlifetime	1440	1440
session.gc_probability	0	0
session.name	PHPSESSID	PHPSESSID
session.referer_check	no value	no value
session.save_handler	files	files
session.save_path	/var/lib/php4	/var/lib/php4
session.serialize_handler	php	php
session.use_cookies	On	On
session.use_only_cookies	Off	Off
session.use_trans_sid	Off	Off

shmop
shmop support 	enabled

snmp
NET-SNMP Support 	enabled
NET-SNMP Version 	5.2.2

sockets
Sockets Support 	enabled

standard
Regex Library 	Bundled library enabled
Dynamic Library Support 	enabled
Path to sendmail 	/usr/sbin/sendmail -t -i

Directive	Local Value	Master Value
assert.active	1	1
assert.bail	0	0
assert.callback	no value	no value
assert.quiet_eval	0	0
assert.warning	1	1
auto_detect_line_endings	0	0
default_socket_timeout	60	60
safe_mode_allowed_env_vars	PHP_	PHP_
safe_mode_protected_env_vars	LD_LIBRARY_PATH	LD_LIBRARY_PATH
url_rewriter.tags	a=href,area=href,frame=src,input=src,form=,fieldset=	a=href,area=href,frame=src,input=src,form=,fieldset=
user_agent	no value	no value

sysvmsg
sysvmsg support	enabled
Revision 	$Revision: 1.4.2.5.2.2 $

tokenizer
Tokenizer Support 	enabled

wddx
WDDX Support	enabled
WDDX Session Serializer 	enabled

xml
XML Support 	active
XML Namespace Support 	active
EXPAT Version 	expat_1.95.8

xmlrpc
core library version 	xmlrpc-epi v. 0.51
php extension version 	0.51
author 	Dan Libby
homepage 	http://xmlrpc-epi.sourceforge.net
open sourced by 	Epinions.com

yp
YP Support 	enabled

zip
Zip support 	enabled

zlib
ZLib Support 	enabled
Compiled Version 	1.2.3
Linked Version 	1.2.3

Directive	Local Value	Master Value
zlib.output_compression	Off	Off
zlib.output_compression_level	-1	-1
zlib.output_handler	no value	no value

Additional Modules
Module Name
filepro
sysvsem
sysvshm
```

why would it just give me a plain white screen? I'm not even sure what log I should be checking apache isn't giving any errors.

I have been all through /var/log and I haven't found anything in apache or mysql logs that corrolates with the times when I get the plain white screen (all the time =P). I did find something in the system log just now. this shows up every 5-6 minutes in /var/log/syslog

*Dec 20 11:25:01 minerva /USR/SBIN/CRON[7179]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)*

when I check /var/log/cacti/poller-error.log I see

*PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0*

in there once, in all honesty I get a feeling that chasing this error is going to be barking up the wrong tree, but I figured I would post it anyways. I noticed that it does show that www-data is trying to access the database, this is quite confusing to me =P

---

### Post by pormogo on 2007-01-02
Ok well I have gotten myself a little furhter then last time but I still appear to be running into some issues. I found out that the file /etc/cacti/debian.php is in fact defining what would normally be in /usr/share/cacti/site/include/config.php So I went ahead and filled out the debian.php file as follows.

[i]$database_username='cactiuser';
$database_password='somepassword';
$basepath='';
$database_default='cacti';
$database_hostname='127.0.0.1';
$dbport='';
$dbtype='mysql';[/i]

This was able to resolve the issue I was having with a plain white screen displaying. After making those changes and reloading apache I was able to proceed with the install of cacti as normal. However my graphs don't appear to work.

According to [this](http://forums.cacti.net/about9179.html) thread I should have to wait about 10 minutes for graphs to come up. It's been about 20 and still no dice :(

I checked the log files from within the web interface and found no errors in the cacti log. However when I try and run the poller from the command line I get the following error.

[i]:/usr/share/cacti/site# sudo -u cactiuser php poller.php
PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0

Warning: main(/etc/cacti/debian.php): failed to open stream: Permission denied in /usr/share/cacti/site/include/config.php on line 30

Fatal error: main(): Failed opening required '/etc/cacti/debian.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/cacti/site/include/config.php on line 30[/i]

When I check line 30 in /usr/share/cacti/site/include/config/php I find a blank line directly under the line that reads.

*require('/etc/cacti/debian.php');*

any time I invoke php from the command line I get the 

*PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0*

warning and I have no idea why.... I found a debian bug on it [here](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=361789). And tried the fix listed there only to find *0       regex           BEGIN[[:space:]]*[{]    application/x-awk* already uncommented in the file....

Any help is of course most appreciated.

EDIT: I just checked /var/log/cacti/poller-error.log and had the following output

[i]# cat poller-error.log
PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0[/i]

---

### Post by reison on 2007-01-24
I believe I've figured this out, but I can't say it's the best or most secure way to do it. First of all, I, too tried unsuccessfully to install cacti using apt-get. Of the 3 times I tried it, I couldn't even get localhost to graph.

So, I started with a fresh install of Ubuntu Server with LAMP. Once the server had rebooted, I edited /etc/apt/sources.list to comment-out the cdrom lines, then used apt-get to update and upgrade. I installed ssh, build-essential, and phpmyadmin using apt-get.

From phpmyadmin, I created an empty "cacti" database, granting "cactiuser" full privileges for that database only. I then set a password for "root".

Once that was done, I downloaded the latest version of cacti from cacti.net, expanded it and moved it to /var/www. From there, I creating a very basic /etc/apache2/sites-available/cacti.conf and used "a2ensite cacti.conf" to enable it in apache2. I then followed the steps in cacti/docs/INSTALL to create the database tables and poller.php entry in cron.

Where I differed from other suggestions I've seen is that I also...
[LIST]
[*]chown -R root:root /var/www/cacti
[*]chmod 755 /var/www/cacti/poller.php
[/LIST]

When I browsed to [http://myhost/cacti](http://myhost/cacti), I was presented with the installation wizard, which I followed until I was presented with the paths, most of which I was missing. So, then I...
[LIST]
[*]aptitude install rrdtool php5-cgi snmp
[*]aptitude install php5-cli
[/LIST]

After that, all paths were found, so I finished the wizard.

I read somewhere that I needed to uncomment "mysql.so" in /etc/php5/cli/php.ini, so I did that, then ran /var/www/cacti/poller.php from the command line to see if I got any errors--NONE...in fact, I got actual output. When I went back to my browser, the graphs for my local host had been created.

Just as a test, I also created a new device and graphs--no problems there either. 

Hopefully, this will help you.

---

### Post by Wizkidno on 2007-02-06
I know this thread is kind of old now, but since i had the same problem with a blank page displaying when manually installing Cacti I thought i would input a little comment here.

After about 5 minutes of thinking i struck me.

I had forgot to install php5-mysql module. hehe

Now when i try to access the cacti page i am presented with the installer.

As all the data is stored in the DB no page was displayed not even an error stating that the mysql module was missing.

All is well in Cacti heaven now :)

---

### Post by flickerfly on 2007-02-27
following reison's explanation I found that I had php4's cli and not php5's. This was apparently causing all sorts of problems on my system. I ran 'sudo apt-get install php5-cli' and then went back and recreated my devices and graphs. Now things seem to work fine.

---

