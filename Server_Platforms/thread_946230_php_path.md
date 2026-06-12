---
title: "php path"
date: 2008-10-13
forum: Server Platforms
---

### Post by andyase on 2008-10-13
Hello All

I have a program thats trying to use php. It will not run a certain file and I am trying to find the "php install" is so I can confirm the path is correct.
I type "whereis php" at the console and it comes back  - php: /usr/bin/php /usr/share/man/man1/php.1.gz.

If i go into /usr/bin, there is no php folder?

What do I do? :confused:

Oh , I forgot to say php4 and 5 is installed... ubuntu 7.10

---

### Post by hyper_ch on 2008-10-13
if you want to run php from the cli you need:
```

sudo apt-get install php5-cli

```

---

### Post by andyase on 2008-10-13
Hi
I did that and got:

php5-cli is already the newest version.

---

### Post by hyper_ch on 2008-10-13
then run it
```

php5 /path/to/script.php

```

or it could only be "php"

---

### Post by homemadejam on 2008-10-13
> **andyase said:**
> Hello All

I have a program thats trying to use php. It will not run a certain file and I am trying to find the "php install" is so I can confirm the path is correct.
I type "whereis php" at the console and it comes back  - php: /usr/bin/php /usr/share/man/man1/php.1.gz.

If i go into /usr/bin, there is no php folder?

What do I do? :confused:

Oh , I forgot to say php4 and 5 is installed... ubuntu 7.10

You know you have a space in between /usr/bin/php /usr/share/.... ?
Have you checked in the /usr/share/man/man1/ for the file?

Sorry if I'm totaly wrong here :P

Jam

---

### Post by andyase on 2008-10-13
This is what I am trying to do.

I have a video (youtube clone) app, when a video is uploaded a .php file is supposed to execute to convert the video into another format for viewing, the .php is not executing, I was told by support to check the correct path to php. So when I did the "whereis php" I got php: /usr/bin/php I went to /usr/bin and php is not there, I ran, sudo apt-get install php5-cli, its already installed. So I am none the wiser as to where php is...

my php info: Hope this helps...




> System 	#1 SMP Tue Feb 12 08:27:05 UTC 2008 i686
Build Date 	Jul 23 2008 06:05:56
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/curl.ini, /etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/xsl.ini
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

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

PHP Credits
Configuration
PHP Core
Directive	Local Value	Master Value
allow_call_time_pass_reference	On	On
allow_url_fopen	On	On
allow_url_include	On	On
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
enable_dl	On	On
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
include_path	.:	.:
log_errors	Off	Off
log_errors_max_len	1024	1024
magic_quotes_gpc	On	On
magic_quotes_runtime	Off	Off
magic_quotes_sybase	Off	Off
mail.force_extra_parameters	no value	no value
max_execution_time	1500	1500
max_input_nesting_level	64	64
max_input_time	60	60
memory_limit	128M	128M
open_basedir	no value	no value
output_buffering	no value	no value
output_handler	no value	no value
post_max_size	100M	100M
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
track_errors	Off	Off
unserialize_callback_func	no value	no value
upload_max_filesize	100M	100M
upload_tmp_dir	no value	no value
user_dir	no value	no value
variables_order	EGPCS	EGPCS
xmlrpc_error_number	0	0
xmlrpc_errors	Off	Off
y2k_compliance	On	On
zend.ze1_compatibility_mode	Off	Off

apache2handler
Apache Version 	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8
Apache API Version 	20051115
Server Administrator 	[email]andy@m57.co.uk[/email]
Hostname:Port 	domain.com:80
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_include mod_mime mod_negotiation mod_perl mod_php5 mod_rewrite mod_setenvif mod_ssl mod_status mod_suexec mod_userdir

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	[www.domain.com](www.domain.com)
HTTP_USER_AGENT 	Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
HTTP_ACCEPT 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
HTTP_ACCEPT_LANGUAGE 	en-gb,en;q=0.5
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_COOKIE 	PHPSESSID=b98e7325c39a99fbbdf89afac43ca322
HTTP_VIA 	1.1 embc-gla-pnc-11.resource.synetrix.local:3128 (squid/2.6.STABLE18)
HTTP_X_FORWARDED_FOR 	10.4.43.254
HTTP_CACHE_CONTROL 	max-age=259200
HTTP_CONNECTION 	keep-alive
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8 Server at [www.domain.com](www.domain.com) Port 80</address>
SERVER_SOFTWARE 	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8
SERVER_NAME 	[www.domain.com](www.domain.com)
SERVER_ADDR 	77.240.0.241
SERVER_PORT 	80
REMOTE_ADDR 	92.43.64.75
DOCUMENT_ROOT 	/var/www/vhosts/domain.com/httpdocs
SERVER_ADMIN 	[email]andy@m57.co.uk[/email]
SCRIPT_FILENAME 	/var/www/vhosts/domain.com/httpdocs/dia.php
REMOTE_PORT 	59526
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.0
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/dia.php
SCRIPT_NAME 	/dia.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /dia.php HTTP/1.0
Host 	[www.domain.com](www.domain.com)
User-Agent 	Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Accept 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language 	en-gb,en;q=0.5
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Cookie 	PHPSESSID=b98e7325c39a99fbbdf89afac43ca322
Via 	1.1 embc-gla-pnc-11.resource.synetrix.local:3128 (squid/2.6.STABLE18)
X-Forwarded-For 	10.4.43.254
Cache-Control 	max-age=259200
Connection 	keep-alive
HTTP Response Headers
X-Powered-By 	PHP/5.2.3-1ubuntu6.4
Connection 	close
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

curl
cURL support 	enabled
cURL Information 	libcurl/7.16.4 OpenSSL/0.9.8e zlib/1.2.3.3 libidn/1.0

date
date/time support 	enabled
"Olson" Timezone Database Version 	2007.5
Timezone Database 	internal
Default timezone 	UTC

Directive	Local Value	Master Value
date.default_latitude	31.7667	31.7667
date.default_longitude	35.2333	35.2333
date.sunrise_zenith	90.583333	90.583333
date.sunset_zenith	90.583333	90.583333
date.timezone	no value	no value

dba
DBA support 	enabled
Supported handlers 	db4

dom
DOM/XML 	enabled
DOM/XML API Version 	20031129
libxml Version 	2.6.30
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.173.2.5.2.19 2007/02/27 03:04:40 iliaa Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

ffmpeg
ffmpeg support (ffmpeg-php)	enabled
ffmpeg-php version 	0.5.3.1
libavcodec version 	Lavc51.62.0
libavformat version 	Lavf52.18.0
ffmpeg-php gd support 	enabled

Directive	Local Value	Master Value
ffmpeg.allow_persistent	0	0
ffmpeg.show_warnings	0	0

filter
Input Validation and Filtering 	enabled
Revision 	$Revision: 1.52.2.39 $

Directive	Local Value	Master Value
filter.default	unsafe_raw	unsafe_raw
filter.default_flags	no value	no value

ftp
FTP support 	enabled

gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.3.5
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled

gettext
GetText Support 	enabled

hash
hash support 	enabled
Hashing Engines 	md2 md4 md5 sha1 sha256 sha384 sha512 ripemd128 ripemd160 ripemd256 ripemd320 whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4 tiger192,4 snefru gost adler32 crc32 crc32b haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4 haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5 haval192,5 haval224,5 haval256,5

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.6.1

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

imap
IMAP c-Client Version 	2001
SSL Support 	enabled
Kerberos Support 	enabled

json
json support 	enabled
json version 	1.2.1

libxml
libXML support 	active
libXML Version 	2.6.30
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

mime_magic
mime_magic support	invalid magic file, disabled

Directive	Local Value	Master Value
mime_magic.debug	Off	Off
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.45
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
Client API library version 	5.0.45
Client API header version 	5.0.45
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
OpenSSL Version 	OpenSSL 0.9.8e 23 Feb 2007

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	7.4 2007-09-21

PDO
PDO support	enabled
PDO drivers 	mysql

pdo_mysql
PDO Driver for MySQL, client library version	5.0.45

posix
Revision 	$Revision: 1.70.2.3.2.15 $

Reflection
Reflection	enabled
Version 	$Id: php_reflection.c,v 1.164.2.33.2.39 2007/05/29 08:44:05 helly Exp $

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
session.gc_maxlifetime	10800	10800
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
Revision 	$Revision: 1.151.2.22.2.26 $
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
libxml2 Version 	2.6.30

xmlreader
XMLReader 	enabled

xmlwriter
XMLWriter 	enabled

xsl
XSL 	enabled
libxslt Version 	1.1.21
libxslt compiled against libxml Version 	2.6.30
EXSLT 	enabled
libexslt Version 	1.1.21

zip
Zip 	enabled
Extension Version 	$Id: php_zip.c,v 1.1.2.33 2007/05/19 22:25:11 pajoye Exp $
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
PATH 	/usr/local/bin:/usr/bin:/bin
LANG 	C
PWD 	/home/hhomelist

PHP Variables
Variable	Value
_REQUEST["PHPSESSID"]	b98e7325c39a99fbbdf89afac43ca322
_COOKIE["PHPSESSID"]	b98e7325c39a99fbbdf89afac43ca322
_SERVER["HTTP_HOST"]	[www.domain.com](www.domain.com)
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
_SERVER["HTTP_ACCEPT"]	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en-gb,en;q=0.5
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_COOKIE"]	PHPSESSID=b98e7325c39a99fbbdf89afac43ca322
_SERVER["HTTP_VIA"]	1.1 embc-gla-pnc-11.resource.synetrix.local:3128 (squid/2.6.STABLE18)
_SERVER["HTTP_X_FORWARDED_FOR"]	10.4.43.254
_SERVER["HTTP_CACHE_CONTROL"]	max-age=259200
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["PATH"]	/usr/local/bin:/usr/bin:/bin
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8 Server at [www.domain.com](www.domain.com) Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8
_SERVER["SERVER_NAME"]	[www.domain.com](www.domain.com)
_SERVER["SERVER_ADDR"]	77.240.0.241
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	92.43.64.75
_SERVER["DOCUMENT_ROOT"]	/var/www/vhosts/domain.com/httpdocs
_SERVER["SERVER_ADMIN"]	[email]andy@m57.co.uk[/email]
_SERVER["SCRIPT_FILENAME"]	/var/www/vhosts/domain.com/httpdocs/dia.php
_SERVER["REMOTE_PORT"]	59526
_SERVER["GATEWAY_INTERFACE"]	CGI/1.1
_SERVER["SERVER_PROTOCOL"]	HTTP/1.0
_SERVER["REQUEST_METHOD"]	GET
_SERVER["QUERY_STRING"]	no value
_SERVER["REQUEST_URI"]	/dia.php
_SERVER["SCRIPT_NAME"]	/dia.php
_SERVER["PHP_SELF"]	/dia.php
_SERVER["REQUEST_TIME"]	1223898524
_SERVER["argv"]	

Array
(
)

_SERVER["argc"]	0
_ENV["PATH"]	/usr/local/bin:/usr/bin:/bin
_ENV["LANG"]	C
_ENV["PWD"]	/home/hhomelist

PHP License

This program is free software; you can redistribute it and/or modify it under the terms of the PHP License as published by the PHP Group and included in the distribution in the file: LICENSE

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

If you did not receive a copy of the PHP license, or have any questions about PHP licensing, please contact [email]license@php.net[/email].

apache2handler
Apache Version 	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8
Apache API Version 	20051115
Server Administrator 	[email]andy@m57.co.uk[/email]
Hostname:Port 	domain.com:80
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_include mod_mime mod_negotiation mod_perl mod_php5 mod_rewrite mod_setenvif mod_ssl mod_status mod_suexec mod_userdir

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	[www.domain.com](www.domain.com)
HTTP_USER_AGENT 	Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
HTTP_ACCEPT 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
HTTP_ACCEPT_LANGUAGE 	en-gb,en;q=0.5
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_COOKIE 	PHPSESSID=b98e7325c39a99fbbdf89afac43ca322
HTTP_VIA 	1.1 embc-gla-pnc-11.resource.synetrix.local:3128 (squid/2.6.STABLE18)
HTTP_X_FORWARDED_FOR 	10.4.43.254
HTTP_CACHE_CONTROL 	max-age=259200
HTTP_CONNECTION 	keep-alive
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8 Server at [www.domain.com](www.domain.com) Port 80</address>
SERVER_SOFTWARE 	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e mod_perl/2.0.2 Perl/v5.8.8
SERVER_NAME 	[www.domain.com](www.domain.com)
SERVER_ADDR 	77.240.0.241
SERVER_PORT 	80
REMOTE_ADDR 	92.43.64.75
DOCUMENT_ROOT 	/var/www/vhosts/domain.com/httpdocs
SERVER_ADMIN 	[email]andy@m57.co.uk[/email]
SCRIPT_FILENAME 	/var/www/vhosts/domain.com/httpdocs/dia.php
REMOTE_PORT 	59526
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.0
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/dia.php
SCRIPT_NAME 	/dia.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /dia.php HTTP/1.0
Host 	[www.domain.com](www.domain.com)
User-Agent 	Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Accept 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language 	en-gb,en;q=0.5
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Cookie 	PHPSESSID=b98e7325c39a99fbbdf89afac43ca322
Via 	1.1 embc-gla-pnc-11.resource.synetrix.local:3128 (squid/2.6.STABLE18)
X-Forwarded-For 	10.4.43.254
Cache-Control 	max-age=259200
Connection 	keep-alive
HTTP Response Headers
X-Powered-By 	PHP/5.2.3-1ubuntu6.4
Connection 	close
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

curl
cURL support 	enabled
cURL Information 	libcurl/7.16.4 OpenSSL/0.9.8e zlib/1.2.3.3 libidn/1.0

date
date/time support 	enabled
"Olson" Timezone Database Version 	2007.5
Timezone Database 	internal
Default timezone 	UTC

Directive	Local Value	Master Value
date.default_latitude	31.7667	31.7667
date.default_longitude	35.2333	35.2333
date.sunrise_zenith	90.583333	90.583333
date.sunset_zenith	90.583333	90.583333
date.timezone	no value	no value

dba
DBA support 	enabled
Supported handlers 	db4

dom
DOM/XML 	enabled
DOM/XML API Version 	20031129
libxml Version 	2.6.30
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.173.2.5.2.19 2007/02/27 03:04:40 iliaa Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

ffmpeg
ffmpeg support (ffmpeg-php)	enabled
ffmpeg-php version 	0.5.3.1
libavcodec version 	Lavc51.62.0
libavformat version 	Lavf52.18.0
ffmpeg-php gd support 	enabled

Directive	Local Value	Master Value
ffmpeg.allow_persistent	0	0
ffmpeg.show_warnings	0	0

filter
Input Validation and Filtering 	enabled
Revision 	$Revision: 1.52.2.39 $

Directive	Local Value	Master Value
filter.default	unsafe_raw	unsafe_raw
filter.default_flags	no value	no value

ftp
FTP support 	enabled

gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.3.5
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled

gettext
GetText Support 	enabled

hash
hash support 	enabled
Hashing Engines 	md2 md4 md5 sha1 sha256 sha384 sha512 ripemd128 ripemd160 ripemd256 ripemd320 whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4 tiger192,4 snefru gost adler32 crc32 crc32b haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4 haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5 haval192,5 haval224,5 haval256,5

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.6.1

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

imap
IMAP c-Client Version 	2001
SSL Support 	enabled
Kerberos Support 	enabled

json
json support 	enabled
json version 	1.2.1

libxml
libXML support 	active
libXML Version 	2.6.30
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

mime_magic
mime_magic support	invalid magic file, disabled

Directive	Local Value	Master Value
mime_magic.debug	Off	Off
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.45
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
Client API library version 	5.0.45
Client API header version 	5.0.45
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
OpenSSL Version 	OpenSSL 0.9.8e 23 Feb 2007

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	7.4 2007-09-21

PDO
PDO support	enabled
PDO drivers 	mysql

pdo_mysql
PDO Driver for MySQL, client library version	5.0.45

posix
Revision 	$Revision: 1.70.2.3.2.15 $

Reflection
Reflection	enabled
Version 	$Id: php_reflection.c,v 1.164.2.33.2.39 2007/05/29 08:44:05 helly Exp $

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
session.gc_maxlifetime	10800	10800
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
Revision 	$Revision: 1.151.2.22.2.26 $
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
libxml2 Version 	2.6.30

xmlreader
XMLReader 	enabled

xmlwriter
XMLWriter 	enabled

xsl
XSL 	enabled
libxslt Version 	1.1.21
libxslt compiled against libxml Version 	2.6.30
EXSLT 	enabled
libexslt Version 	1.1.21

zip
Zip 	enabled
Extension Version 	$Id: php_zip.c,v 1.1.2.33 2007/05/19 22:25:11 pajoye Exp $
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


---

### Post by cdenley on 2008-10-13
How did you determine that the FILE /usr/bin/php was not there?
```

ls -l /usr/bin/php
ls -l /etc/alternatives/php
ls -l /usr/bin/php5
ls -Ll /usr/bin/php

```
What is the code you are using to execute php? You may need to specify the full path if the environment you are starting it from doesn't have the PATH variable set.
```

system("/usr/bin/php /path/to/myfile.php");

```
If for some reason you deleted files provided by the php5-cli package, reinstall it.
```

sudo apt-get --reinstall install php5-cli

```

---

### Post by andyase on 2008-10-13
If I run those commands I get this...

> 
hhomelist@perilla:/usr/bin$ ls -Ll /usr/bin/php
-rwxr-xr-x 1 root root 5511456 2008-07-23 06:21 /usr/bin/php
hhomelist@perilla:/usr/bin$ cd
hhomelist@perilla:~$ ls -l /usr/bin/php
lrwxrwxrwx 1 root root 21 2008-07-23 13:36 /usr/bin/php -> /etc/alternatives/php
hhomelist@perilla:~$ ls -l /etc/alternatives/php
lrwxrwxrwx 1 root root 13 2008-10-13 12:58 /etc/alternatives/php -> /usr/bin/php5
hhomelist@perilla:~$ ls -l /usr/bin/php5
-rwxr-xr-x 1 root root 5511456 2008-07-23 06:21 /usr/bin/php5
hhomelist@perilla:~$ ls -Ll /usr/bin/php
-rwxr-xr-x 1 root root 5511456 2008-07-23 06:21 /usr/bin/php



---

### Post by andyase on 2008-10-13
This is what I have in the config file to point at php: $path_to_php  = '/usr/bin/php';

looking at my php info and outputs above does this look right?

Thanks

---

### Post by cdenley on 2008-10-13
> **andyase said:**
> This is what I have in the config file to point at php: $path_to_php  = '/usr/bin/php';

looking at my php info and outputs above does this look right?

Thanks

Yes, that is a correct path. Take your pick:
[LIST]
[*]/usr/bin/php
[*]/usr/bin/php5
[*]/etc/alternatives/php
[/LIST]
They all exist, and will execute php scripts. If you want any more help, you are going to have to post the code you are having trouble with.

---

