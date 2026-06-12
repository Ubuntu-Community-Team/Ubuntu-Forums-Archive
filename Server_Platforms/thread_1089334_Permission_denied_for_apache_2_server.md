---
title: "Permission denied for apache 2 server"
date: 2009-03-07
forum: Server Platforms
---

### Post by g1d2r3 on 2009-03-07
Hi,

I am totally new to linux and ubuntu.Previously i was using WAMP on my windows machine.In that I couls access all my php,html and xml files through the index on the web browser.Usually use server for just checking php scripts locally.

I have installed LAMP on my machine.I am able to access all the folders in my /var/www folder.

But when i try to execute php scripts i get following error on browser


Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/bookmarks/bookmarks.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

and the corresponding error in log:

[Sat Mar 07 11:51:41 2009] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /var/www/bookmarks/bookmarks(2).xml, referer: [http://localhost/bookmarks/](http://localhost/bookmarks/)

For xml files it shows on browser:
Forbidden

You don't have permission to access /bookmarks/bookmark.xml on this server.

Corresponding entry in log:
[Sat Mar 07 12:00:44 2009] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /var/www/bookmarks/bookmark.xml, referer: [http://localhost/bookmarks/](http://localhost/bookmarks/)

For html files on browser:
Forbidden

You don't have permission to access /bookmarks/community.html on this server.

Corresponding entry in log:
[Sat Mar 07 12:01:30 2009] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /var/www/bookmarks/community.html, referer: [http://localhost/bookmarks/](http://localhost/bookmarks/)

I have tried with following things to rectify this:

sudo chown gauresh /var/www/ -R
sudo chmod u=rwx /var/www/ -R

The permissions given for all folders in /var/www/ are
access: Create and delete file

Applied permissions to all files in folder


Also I will mention that it can :
it displays
<?phpinfo()?>
it/s output is:

PHP Logo
PHP Version 5.2.4-2ubuntu5.5

System 	Linux gauresh-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date 	Feb 11 2009 19:49:37
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini
PHP API 	20041225
PHP Extension 	20060613
Zend Extension 	220060519
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
IPv6 Support 	enabled
Registered PHP Streams 	zip, php, file, data, http, ftp, compress.bzip2, compress.zlib, https, ftps
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, convert.iconv.*, bzip2.*, zlib.*

Suhosin logo This server is protected with the Suhosin Patch 0.9.6.2
Copyright (c) 2006 Hardened-PHP Project

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

PHP Credits
Configuration
PHP Core
Directive	Local Value	Master Value
allow_call_time_pass_reference	On	On
allow_url_fopen	On	On
allow_url_include	Off	Off
always_populate_raw_post_data	Off	Off
arg_separator.input	&	&
arg_separator.output	&	&
asp_tags	Off	Off
auto_append_file	no value	no value
auto_globals_jit	On	On
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
enable_dl	Off	Off
error_append_string	no value	no value
error_log	no value	no value
error_prepend_string	no value	no value
error_reporting	6135	6135
expose_php	On	On
extension_dir	/usr/lib/php5/20060613+lfs	/usr/lib/php5/20060613+lfs
file_uploads	On	On
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
mail.force_extra_parameters	no value	no value
max_execution_time	30	30
max_input_nesting_level	64	64
max_input_time	60	60
memory_limit	16M	16M
open_basedir	no value	no value
output_buffering	no value	no value
output_handler	no value	no value
post_max_size	8M	8M
precision	12	12
realpath_cache_size	16K	16K
realpath_cache_ttl	120	120
register_argc_argv	On	On
register_globals	Off	Off
register_long_arrays	On	On
report_memleaks	On	On
report_zend_debug	On	On
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
suhosin.log.phpscript	0	0
suhosin.log.phpscript.is_safe	Off	Off
suhosin.log.phpscript.name	no value	no value
suhosin.log.sapi	no value	no value
suhosin.log.script	no value	no value
suhosin.log.script.name	no value	no value
suhosin.log.syslog	no value	no value
suhosin.log.syslog.facility	no value	no value
suhosin.log.syslog.priority	no value	no value
suhosin.log.use-x-forwarded-for	Off	Off
track_errors	Off	Off
unserialize_callback_func	no value	no value
upload_max_filesize	2M	2M
upload_tmp_dir	no value	no value
user_dir	no value	no value
variables_order	EGPCS	EGPCS
xmlrpc_error_number	0	0
xmlrpc_errors	Off	Off
y2k_compliance	On	On
zend.ze1_compatibility_mode	Off	Off

apache2handler
Apache Version 	Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch
Apache API Version 	20051115
Server Administrator 	webmaster@localhost
Hostname:Port 	127.0.1.1:0
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_setenvif mod_status

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	localhost
HTTP_USER_AGENT 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
HTTP_ACCEPT 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
HTTP_ACCEPT_LANGUAGE 	en-us,en;q=0.5
HTTP_ACCEPT_ENCODING 	gzip,deflate
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_KEEP_ALIVE 	300
HTTP_CONNECTION 	keep-alive
HTTP_REFERER 	[http://localhost/untitled%20folder/](http://localhost/untitled%20folder/)
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch Server at localhost Port 80</address>
SERVER_SOFTWARE 	Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch
SERVER_NAME 	localhost
SERVER_ADDR 	127.0.0.1
SERVER_PORT 	80
REMOTE_ADDR 	127.0.0.1
DOCUMENT_ROOT 	/var/www/
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/untitled folder/testphp.php
REMOTE_PORT 	34422
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.1
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/untitled%20folder/testphp.php
SCRIPT_NAME 	/untitled folder/testphp.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /untitled%20folder/testphp.php HTTP/1.1
Host 	localhost
User-Agent 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
Accept 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language 	en-us,en;q=0.5
Accept-Encoding 	gzip,deflate
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive 	300
Connection 	keep-alive
Referer 	[http://localhost/untitled%20folder/](http://localhost/untitled%20folder/)
HTTP Response Headers
X-Powered-By 	PHP/5.2.4-2ubuntu5.5
Keep-Alive 	timeout=15, max=94
Connection 	Keep-Alive
Transfer-Encoding 	chunked
Content-Type 	text/html

bcmath
BCMath support 	enabled

bz2
BZip2 Support 	Enabled
Stream Wrapper support 	compress.bz2://
Stream Filter support 	bzip2.decompress, bzip2.compress
BZip2 Version 	1.0.4, 20-Dec-2006

calendar
Calendar support 	enabled

ctype
ctype functions 	enabled

date
date/time support 	enabled
"Olson" Timezone Database Version 	0.system
Timezone Database 	internal
Default timezone 	Asia/Calcutta

Directive	Local Value	Master Value
date.default_latitude	31.7667	31.7667
date.default_longitude	35.2333	35.2333
date.sunrise_zenith	90.583333	90.583333
date.sunset_zenith	90.583333	90.583333
date.timezone	no value	no value

dba
DBA support 	enabled
Supported handlers 	cdb cdb_make db4 inifile flatfile

dom
DOM/XML 	enabled
DOM/XML API Version 	20031129
libxml Version 	2.6.31
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.173.2.5.2.20 2007/06/10 20:12:45 iliaa Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

filter
Input Validation and Filtering 	enabled
Revision 	$Revision: 1.52.2.39 $

Directive	Local Value	Master Value
filter.default	unsafe_raw	unsafe_raw
filter.default_flags	no value	no value

ftp
FTP support 	enabled

gettext
GetText Support 	enabled

hash
hash support 	enabled
Hashing Engines 	md2 md4 md5 sha1 sha256 sha384 sha512 ripemd128 ripemd160 ripemd256 ripemd320 whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4 tiger192,4 snefru gost adler32 crc32 crc32b haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4 haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5 haval192,5 haval224,5 haval256,5

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.7

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

json
json support 	enabled
json version 	1.2.1

libxml
libXML support 	active
libXML Version 	2.6.31
libXML streams 	enabled

mbstring
Multibyte Support 	enabled
Multibyte string engine 	libmbfl
Multibyte (japanese) regex support 	enabled
Multibyte regex (oniguruma) version 	4.4.4
Multibyte regex (oniguruma) backtrack check 	On

mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.

Directive	Local Value	Master Value
mbstring.detect_order	no value	no value
mbstring.encoding_translation	Off	Off
mbstring.func_overload	0	0
mbstring.http_input	pass	pass
mbstring.http_output	pass	pass
mbstring.internal_encoding	no value	no value
mbstring.language	neutral	neutral
mbstring.strict_detection	Off	Off
mbstring.substitute_character	no value	no value

mcrypt
mcrypt support	enabled
Version 	2.5.7
Api No 	20021217
Supported ciphers 	cast-128 gost rijndael-128 twofish arcfour cast-256 loki97 rijndael-192 saferplus wake blowfish-compat des rijndael-256 serpent xtea blowfish enigma rc2 tripledes
Supported modes 	cbc cfb ctr ecb ncfb nofb ofb stream

Directive	Local Value	Master Value
mcrypt.algorithms_dir	no value	no value
mcrypt.modes_dir	no value	no value

mime_magic
mime_magic support	invalid magic file, disabled

Directive	Local Value	Master Value
mime_magic.debug	Off	Off
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.51a
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

mysqli
MysqlI Support	enabled
Client API library version 	5.0.51a
Client API header version 	5.0.51a
MYSQLI_SOCKET 	/var/run/mysqld/mysqld.sock

Directive	Local Value	Master Value
mysqli.default_host	no value	no value
mysqli.default_port	3306	3306
mysqli.default_pw	no value	no value
mysqli.default_socket	no value	no value
mysqli.default_user	no value	no value
mysqli.max_links	Unlimited	Unlimited
mysqli.reconnect	Off	Off

openssl
OpenSSL support 	enabled
OpenSSL Version 	OpenSSL 0.9.8g 19 Oct 2007

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	7.4 2007-09-21

Directive	Local Value	Master Value
pcre.backtrack_limit	100000	100000
pcre.recursion_limit	100000	100000

PDO
PDO support	enabled
PDO drivers 	mysql

pdo_mysql
PDO Driver for MySQL, client library version	5.0.51a

posix
Revision 	$Revision: 1.70.2.3.2.16 $

Reflection
Reflection	enabled
Version 	$Id: php_reflection.c,v 1.164.2.33.2.45 2007/08/20 17:01:22 sebastian Exp $

session
Session Support 	enabled
Registered save handlers 	files user
Registered serializer handlers 	php php_binary wddx

Directive	Local Value	Master Value
session.auto_start	Off	Off
session.bug_compat_42	On	On
session.bug_compat_warn	On	On
session.cache_expire	180	180
session.cache_limiter	nocache	nocache
session.cookie_domain	no value	no value
session.cookie_httponly	Off	Off
session.cookie_lifetime	0	0
session.cookie_path	/	/
session.cookie_secure	Off	Off
session.entropy_file	no value	no value
session.entropy_length	0	0
session.gc_divisor	100	100
session.gc_maxlifetime	1440	1440
session.gc_probability	0	0
session.hash_bits_per_character	4	4
session.hash_function	0	0
session.name	PHPSESSID	PHPSESSID
session.referer_check	no value	no value
session.save_handler	files	files
session.save_path	/var/lib/php5	/var/lib/php5
session.serialize_handler	php	php
session.use_cookies	On	On
session.use_only_cookies	Off	Off
session.use_trans_sid	0	0

shmop
shmop support 	enabled

SimpleXML
Simplexml support	enabled
Revision 	$Revision: 1.151.2.22.2.35 $
Schema support 	enabled

soap
Soap Client 	enabled
Soap Server 	enabled

Directive	Local Value	Master Value
soap.wsdl_cache	1	1
soap.wsdl_cache_dir	/tmp	/tmp
soap.wsdl_cache_enabled	1	1
soap.wsdl_cache_limit	5	5
soap.wsdl_cache_ttl	86400	86400

sockets
Sockets Support 	enabled

SPL
SPL support	enabled
Interfaces 	Countable, OuterIterator, RecursiveIterator, SeekableIterator, SplObserver, SplSubject
Classes 	AppendIterator, ArrayIterator, ArrayObject, BadFunctionCallException, BadMethodCallException, CachingIterator, DirectoryIterator, DomainException, EmptyIterator, FilterIterator, InfiniteIterator, InvalidArgumentException, IteratorIterator, LengthException, LimitIterator, LogicException, NoRewindIterator, OutOfBoundsException, OutOfRangeException, OverflowException, ParentIterator, RangeException, RecursiveArrayIterator, RecursiveCachingIterator, RecursiveDirectoryIterator, RecursiveFilterIterator, RecursiveIteratorIterator, RecursiveRegexIterator, RegexIterator, RuntimeException, SimpleXMLIterator, SplFileInfo, SplFileObject, SplObjectStorage, SplTempFileObject, UnderflowException, UnexpectedValueException

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
sysvmsg support 	enabled
Revision 	$Revision: 1.20.2.3.2.6 $

tokenizer
Tokenizer Support 	enabled

wddx
WDDX Support	enabled
WDDX Session Serializer 	enabled

xml
XML Support 	active
XML Namespace Support 	active
libxml2 Version 	2.6.31

xmlreader
XMLReader 	enabled

xmlwriter
XMLWriter 	enabled

zip
Zip 	enabled
Extension Version 	$Id: php_zip.c,v 1.1.2.38 2007/08/06 22:02:32 bjori Exp $
Zip version 	2.0.0
Libzip version 	0.7.1

zlib
ZLib Support 	enabled
Stream Wrapper support 	compress.zlib://
Stream Filter support 	zlib.inflate, zlib.deflate
Compiled Version 	1.2.1.1
Linked Version 	1.2.3.3

Directive	Local Value	Master Value
zlib.output_compression	Off	Off
zlib.output_compression_level	-1	-1
zlib.output_handler	no value	no value

Additional Modules
Module Name
sysvsem
sysvshm

Environment
Variable	Value
APACHE_PID_FILE 	/var/run/apache2.pid
PATH 	/usr/local/bin:/usr/bin:/bin
LANG 	C
APACHE_RUN_GROUP 	www-data
APACHE_RUN_USER 	www-data
PWD 	/home/gauresh

PHP Variables
Variable	Value
_SERVER["HTTP_HOST"]	localhost
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
_SERVER["HTTP_ACCEPT"]	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en-us,en;q=0.5
_SERVER["HTTP_ACCEPT_ENCODING"]	gzip,deflate
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_KEEP_ALIVE"]	300
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["HTTP_REFERER"]	[http://localhost/untitled%20folder/](http://localhost/untitled%20folder/)
_SERVER["PATH"]	/usr/local/bin:/usr/bin:/bin
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch Server at localhost Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch
_SERVER["SERVER_NAME"]	localhost
_SERVER["SERVER_ADDR"]	127.0.0.1
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	127.0.0.1
_SERVER["DOCUMENT_ROOT"]	/var/www/
_SERVER["SERVER_ADMIN"]	webmaster@localhost
_SERVER["SCRIPT_FILENAME"]	/var/www/untitled folder/testphp.php
_SERVER["REMOTE_PORT"]	34422
_SERVER["GATEWAY_INTERFACE"]	CGI/1.1
_SERVER["SERVER_PROTOCOL"]	HTTP/1.1
_SERVER["REQUEST_METHOD"]	GET
_SERVER["QUERY_STRING"]	no value
_SERVER["REQUEST_URI"]	/untitled%20folder/testphp.php
_SERVER["SCRIPT_NAME"]	/untitled folder/testphp.php
_SERVER["PHP_SELF"]	/untitled folder/testphp.php
_SERVER["REQUEST_TIME"]	1236408353
_SERVER["argv"]	

Array
(
)

_SERVER["argc"]	0
_ENV["APACHE_PID_FILE"]	/var/run/apache2.pid
_ENV["PATH"]	/usr/local/bin:/usr/bin:/bin
_ENV["LANG"]	C
_ENV["APACHE_RUN_GROUP"]	www-data
_ENV["APACHE_RUN_USER"]	www-data
_ENV["PWD"]	/home/gauresh

PHP License

This program is free software; you can redistribute it and/or modify it under the terms of the PHP License as published by the PHP Group and included in the distribution in the file: LICENSE

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

If you did not receive a copy of the PHP license, or have any questions about PHP licensing, please contact [email]license@php.net[/email].



Also it prints simple echo lines;

Thanks.

---

### Post by beno1990 on 2009-03-07
Try running these commands

```

sudo chown -R www-data /var/www
sudo chmod -R u=rwx /var/www

```

That changes the ownership of all files in the directory to Apache and gives the owner read, write and execute permissions.

---

### Post by g1d2r3 on 2009-03-07
thanks beno

The things are working

---

### Post by mysoogal on 2009-03-15
> **beno1990 said:**
> Try running these commands

```

sudo chown -R www-data /var/www
sudo chmod -R u=rwx /var/www

```

That changes the ownership of all files in the directory to Apache and gives the owner read, write and execute permissions.

it locked my var/www how to unluck it when i go into [http://127.0.0.1](http://127.0.0.1) see nothing,:(

how to change it back to normal my account is mysoogal on xubuntu

---

### Post by mysoogal on 2009-03-15
i've fixed it with sudo chown user : user folder example /var/www/

---

### Post by ktritty on 2009-05-12
> **beno1990 said:**
> Try running these commands

```

sudo chown -R www-data /var/www
sudo chmod -R u=rwx /var/www

```That changes the ownership of all files in the directory to Apache and gives the owner read, write and execute permissions.

I am also fairly new to Ubuntu.  I have been working out of "Practical Guide to Ubuntu Linux 8.10" which seems to be 99% unchanged in the 9.04 release.  However, I am having trouble making it so that I don't need to sudo in order to write changes to my /var/www/ tree.

The manual I have suggests the following (approximately quoted):
Create a new group to administer web stuff
[FONT=Courier New]$ sudo addgroup webadmin
$ sudo chmod g+s /var/www
$ sudo chown :webadmin /var/www
$ sudo usermod -aG webadmin webmaster
[FONT=Arial]where "webmaster" is the user I want to not need to sudo anymore.

However, I still need to sudo after all of that.  Any idea how I can troubleshoot this?  Or are any of the "ch" options wrong?  If so, should I undo anything?

Thanks
[/FONT][/FONT]

---

### Post by spiderbatdad on 2009-05-12
By default apache runs as an unprivileged user www-data. No need to create any other groups or users. If using sudo or sudo -i (for root session) is so inconvenient...rather than trying to circumvent the security model with repeated recursive permission changes, just point vhosts file to your own /var/www tree in your home directory, ie., /home/user/var/www
That is; edit /etc/apache2/sites-available/your-site and change the document root.

---

### Post by ktritty on 2009-05-13
> **spiderbatdad said:**
> If using sudo or sudo -i (for root session) is so inconvenient...

I would rather not have to "sudo" over an ssh connection, that is why I'm trying to get my own access, which would enable me to upload via ssh with more confidence of security.

I like your idea of creating an alternate directory for the root of the apache server, one that is below the home folder of another user.  The only concerns I have are what I might need to do to accomplish all of that, meanwhile, keeping apache safely in jail so that opening port 80 does not become the end of me!

I am new to the concept of jailing, and I have read that it is crucial to make sure that a jailed daemon has no shell, no home directory, and no owned documents outside from the jailed tree.  I would imagine that this issue has already been discussed, and wonder if you could link me to a good place.

Thanks

---

### Post by wojox on 2009-05-13
Correct me if i'm wrong but aren't your sudo credentials the same as your login credentials ? So why not SuperUserDO ?

---

### Post by ktritty on 2009-05-13
> **wojox said:**
> Correct me if i'm wrong but aren't your sudo credentials the same as your login credentials ? So why not SuperUserDO ?

Well, I'm not 100% certain of the workings of sudo, but I do understand that if I use a sudo command in my ssh connection, than anybody who hijacks the connection can do anything root could do without needing to enter a password for about 10 minutes.  Whereas, if I setup permissions where my "webadmin" ssh user (the user I normally log in when I run ssh for uploading to web servers) can upload to my web server, than anybody hijacking the connection cannot do anything more than webadmin could, which certainly does not include super-user access.

Essentially, what I am trying to do is create a special user that I only login as when I want to upload to my http, ftp, and so forth servers (jailed areas) that way even if my ssh session got hijacked, the hijacker would still be jailed.  webadmin would have home folder and all ownerships inside of the jail, and would have a shell, but no entry in sudoers.  The special user should, however, have write priveliges to the /var/www directory.  The worst damage a hacker could do, even if they hacked an upload session, would be to disrupt my website, not compromise the whole system.

I may be a bit obsessive about security, but I've seen first hand the horrors of idendity theft and DoS.

---

