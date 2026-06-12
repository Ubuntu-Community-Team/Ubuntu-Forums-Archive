---
title: "Cacti login broken - session problem?"
date: 2009-08-23
forum: Server Platforms
---

### Post by cdpuk on 2009-08-23
Hi,  I've got a cacti installation that I can no longer get in to, but for strange reasons.  If I enter an incorrect username/password, it'll come back and tell me that in the red text, however if I enter the correct combination, I just get sent back to the login screen with no message at all.

After some poking around with the php files, I found that the session data containing my user ID is being saved to the session file (just before the header('Location...') redirect, but after this redirect it seems all session data is lost, so it thinks it needs to start again.

Funny thing is, I remember having this exact problem on another box, but that time I worked out how to fix it.

For the sake of it, phpinfo() taken from just after session_start()

```

PHP Version 5.2.6-2ubuntu4.2

System 	Linux ### 2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 x86_64
Build Date 	Apr 17 2009 14:42:19
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mcrypt.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/pdo_pgsql.ini, /etc/php5/apache2/conf.d/pgsql.ini, /etc/php5/apache2/conf.d/snmp.ini
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
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies

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
extension_dir	/usr/lib/php5/20060613	/usr/lib/php5/20060613
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
sendmail_path	/usr/sbin/sendmail -t -i	/usr/sbin/sendmail -t -i
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
Apache Version 	Apache/2.2.9 (Ubuntu) DAV/2 SVN/1.5.1 PHP/5.2.6-2ubuntu4.2 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2
Apache API Version 	20051115
Server Administrator 	webmaster@localhost
Hostname:Port 	###:80
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dav mod_dav_svn mod_authz_svn mod_deflate mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_python mod_setenvif mod_status mod_userdir

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	10.0.10.1
HTTP_USER_AGENT 	Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13
HTTP_ACCEPT 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
HTTP_ACCEPT_LANGUAGE 	en-gb,en;q=0.5
HTTP_ACCEPT_ENCODING 	gzip,deflate
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_REFERER 	http://10.0.10.1/cacti/index.php
HTTP_COOKIE 	Cacti=a8b0dc8f55f7a1dcc9e411054e184e69
HTTP_VIA 	1.1 ###.local:3128 (squid/2.7.STABLE3)
HTTP_X_FORWARDED_FOR 	10.0.21.6
HTTP_CACHE_CONTROL 	max-age=0
HTTP_CONNECTION 	keep-alive
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.2.9 (Ubuntu) DAV/2 SVN/1.5.1 PHP/5.2.6-2ubuntu4.2 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 Server at 10.0.10.1 Port 80</address>
SERVER_SOFTWARE 	Apache/2.2.9 (Ubuntu) DAV/2 SVN/1.5.1 PHP/5.2.6-2ubuntu4.2 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2
SERVER_NAME 	10.0.10.1
SERVER_ADDR 	10.0.10.1
SERVER_PORT 	80
REMOTE_ADDR 	10.0.10.1
DOCUMENT_ROOT 	/var/www/
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/usr/share/cacti/site/index.php
REMOTE_PORT 	51552
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.0
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/cacti/index.php
SCRIPT_NAME 	/cacti/index.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /cacti/index.php HTTP/1.0
Host 	10.0.10.1
User-Agent 	Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13
Accept 	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language 	en-gb,en;q=0.5
Accept-Encoding 	gzip,deflate
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Referer 	http://10.0.10.1/cacti/index.php
Cookie 	Cacti=a8b0dc8f55f7a1dcc9e411054e184e69
Via 	1.1 ###.local:3128 (squid/2.7.STABLE3)
X-Forwarded-For 	10.0.21.6
Cache-Control 	max-age=0
Connection 	keep-alive
HTTP Response Headers
X-Powered-By 	PHP/5.2.6-2ubuntu4.2
Expires 	Thu, 19 Nov 1981 08:52:00 GMT
Last-Modified 	Sun, 23 Aug 2009 09:43:41 GMT
Cache-Control 	no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma 	no-cache
Vary 	Accept-Encoding
Content-Encoding 	gzip

bcmath
BCMath support 	enabled

bz2
BZip2 Support 	Enabled
Stream Wrapper support 	compress.bz2://
Stream Filter support 	bzip2.decompress, bzip2.compress
BZip2 Version 	1.0.5, 10-Dec-2007

calendar
Calendar support 	enabled

ctype
ctype functions 	enabled

date
date/time support 	enabled
"Olson" Timezone Database Version 	0.system
Timezone Database 	internal
Default timezone 	Europe/London

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
libxml Version 	2.6.32
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.173.2.5.2.25 2008/03/12 17:33:14 iliaa Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

filter
Input Validation and Filtering 	enabled
Revision 	$Revision: 1.52.2.42 $

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
FreeType Version 	2.3.7
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
iconv library version 	2.8.90

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

json
json support 	enabled
json version 	1.2.1

libxml
libXML support 	active
libXML Version 	2.6.32
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
Active Persistent Links 	1
Active Links 	1
Client API version 	5.0.67
MYSQL_MODULE_TYPE 	external
MYSQL_SOCKET 	/var/run/mysqld/mysqld.sock
MYSQL_INCLUDE 	-I/usr/include/mysql
MYSQL_LIBS 	-L/usr/lib -lmysqlclient_r

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
Client API library version 	5.0.67
Client API header version 	5.0.67
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
PCRE Library Version 	7.6 2008-01-28

Directive	Local Value	Master Value
pcre.backtrack_limit	100000	100000
pcre.recursion_limit	100000	100000

PDO
PDO support	enabled
PDO drivers 	mysql, pgsql

pdo_mysql
PDO Driver for MySQL, client library version	5.0.67

pdo_pgsql
PDO Driver for PostgreSQL	enabled
PostgreSQL(libpq) Version 	8.3.7
Module version 	1.0.2
Revision 	$Id: pdo_pgsql.c,v 1.7.2.11.2.2 2007/12/31 07:20:10 sebastian Exp $

pgsql
PostgreSQL Support	enabled
PostgreSQL(libpq) Version 	8.3.7
Multibyte character support 	enabled
SSL support 	enabled
Active Persistent Links 	0
Active Links 	0

Directive	Local Value	Master Value
pgsql.allow_persistent	On	On
pgsql.auto_reset_persistent	Off	Off
pgsql.ignore_notice	Off	Off
pgsql.log_notice	Off	Off
pgsql.max_links	Unlimited	Unlimited
pgsql.max_persistent	Unlimited	Unlimited

posix
Revision 	$Revision: 1.70.2.3.2.18 $

Reflection
Reflection	enabled
Version 	$Id: php_reflection.c,v 1.164.2.33.2.50 2008/03/13 15:56:21 iliaa Exp $

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
session.name	Cacti	PHPSESSID
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
Revision 	$Revision: 1.151.2.22.2.39 $
Schema support 	enabled

snmp
NET-SNMP Support 	enabled
NET-SNMP Version 	5.4.1

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
Revision 	$Revision: 1.20.2.3.2.7 $

tokenizer
Tokenizer Support 	enabled

wddx
WDDX Support	enabled
WDDX Session Serializer 	enabled

xml
XML Support 	active
XML Namespace Support 	active
libxml2 Version 	2.6.32

xmlreader
XMLReader 	enabled

xmlwriter
XMLWriter 	enabled

zip
Zip 	enabled
Extension Version 	$Id: php_zip.c,v 1.1.2.43 2008/01/18 00:51:38 pajoye Exp $
Zip version 	1.8.11
Libzip version 	0.8.0-compatible

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
PWD 	/

PHP Variables
Variable	Value
_REQUEST["Cacti"]	a8b0dc8f55f7a1dcc9e411054e184e69
_COOKIE["Cacti"]	a8b0dc8f55f7a1dcc9e411054e184e69
_SERVER["HTTP_HOST"]	10.0.10.1
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13
_SERVER["HTTP_ACCEPT"]	text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en-gb,en;q=0.5
_SERVER["HTTP_ACCEPT_ENCODING"]	gzip,deflate
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_REFERER"]	http://10.0.10.1/cacti/index.php
_SERVER["HTTP_COOKIE"]	Cacti=a8b0dc8f55f7a1dcc9e411054e184e69
_SERVER["HTTP_VIA"]	1.1 ###.local:3128 (squid/2.7.STABLE3)
_SERVER["HTTP_X_FORWARDED_FOR"]	10.0.21.6
_SERVER["HTTP_CACHE_CONTROL"]	max-age=0
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["PATH"]	/usr/local/bin:/usr/bin:/bin
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.2.9 (Ubuntu) DAV/2 SVN/1.5.1 PHP/5.2.6-2ubuntu4.2 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 Server at 10.0.10.1 Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.2.9 (Ubuntu) DAV/2 SVN/1.5.1 PHP/5.2.6-2ubuntu4.2 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2
_SERVER["SERVER_NAME"]	10.0.10.1
_SERVER["SERVER_ADDR"]	10.0.10.1
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	10.0.10.1
_SERVER["DOCUMENT_ROOT"]	/var/www/
_SERVER["SERVER_ADMIN"]	webmaster@localhost
_SERVER["SCRIPT_FILENAME"]	/usr/share/cacti/site/index.php
_SERVER["REMOTE_PORT"]	51552
_SERVER["GATEWAY_INTERFACE"]	CGI/1.1
_SERVER["SERVER_PROTOCOL"]	HTTP/1.0
_SERVER["REQUEST_METHOD"]	GET
_SERVER["QUERY_STRING"]	no value
_SERVER["REQUEST_URI"]	/cacti/index.php
_SERVER["SCRIPT_NAME"]	/cacti/index.php
_SERVER["PHP_SELF"]	/cacti/index.php
_SERVER["REQUEST_TIME"]	1251020621
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
_ENV["PWD"]	/


```

There must have been an update or new package installed that caused this, as obviously I was able to configure cacti just fine when I first installed the OS last year.

I'm completely out of ideas now, so any suggestions welcome.

Thanks,
-Chris

---

