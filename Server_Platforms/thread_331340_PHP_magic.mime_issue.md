---
title: "PHP magic.mime issue"
date: 2007-01-04
forum: Server Platforms
---

### Post by pormogo on 2007-01-04
I've been having an odd issue with php4 (I think this is a php error) that is causing cacti's poller to give me the following error

*PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0*

I've been trying to get cacti up and running for quite a while now and this appears to be the last hurdle that I have to cross. The below 2 posts chronicle what I have done up to this point if anyone happens to want some overly long reading =P

[http://forums.cacti.net/about18666.html](http://forums.cacti.net/about18666.html)
[http://ubuntuforums.org/showthread.php?t=313952](http://ubuntuforums.org/showthread.php?t=313952)

A friend of mine just pointed out that it is a warning and not necessarily an error and very well might not be the reason why my graphs are not showing up, however the other 2 logs in /var/log/cacti are totally empty. But since this is the only thing in the poller-error.log this is all I have to go with. I have racked my brain and google on this one so I'm just going to give you as much output as I can praying that someone more knowledgeable then me might be able to solve the issue. First here is a list of what php packages I have installed from dpkg

```
ii  libapache2-mod-php4          4.4.2-1.1               server-side, HTML-embedded scripting languag
ii  libphp-adodb                 4.72-0.1ubuntu1         The 'adodb' database abstraction layer for p
ii  php4                         4.4.2-1.1               server-side, HTML-embedded scripting languag
ii  php4-cli                     4.4.2-1.1               command-line interpreter for the php4 script
ii  php4-common                  4.4.2-1.1               Common files for packages built from the php
ii  php4-mysql                   4.4.2-1.1               MySQL module for php4
ii  php4-snmp                    4.4.2-1.1               SNMP module for php4
```

libmagic is also installed and is current

*ii  libmagic1                    4.17-2ubuntu1           File type determination library using "magic*

here is my output from a php -i from the console

```
# php -i
PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0
phpinfo()
PHP Version => 4.4.2-1.1

System => Linux minerva 2.6.17-10-server #2 SMP Tue Dec 5 22:29:32 UTC 2006 i686
Build Date => Jun 20 2006 02:32:09
Server API => Command Line Interface
Virtual Directory Support => disabled
Configuration File (php.ini) Path => /etc/php4/cli/php.ini
PHP API => 20020918
PHP Extension => 20020429
Zend Extension => 20050606
Debug Build => no
Zend Memory Manager => enabled
Thread Safety => disabled
Registered PHP Streams => php, http, ftp, https, ftps, compress.bzip2, compress.zlib  


This program makes use of the Zend Scripting Language Engine:
Zend Engine v1.3.0, Copyright (c) 1998-2004 Zend Technologies


 _______________________________________________________________________


Configuration

PHP Core

Directive => Local Value => Master Value
allow_call_time_pass_reference => On => On
allow_url_fopen => On => On
always_populate_raw_post_data => Off => Off
arg_separator.input => & => &
arg_separator.output => & => &
asp_tags => Off => Off
auto_append_file => no value => no value
auto_prepend_file => no value => no value
browscap => no value => no value
default_charset => no value => no value
default_mimetype => text/html => text/html
define_syslog_variables => Off => Off
disable_classes => no value => no value
disable_functions => no value => no value
display_errors => On => On
display_startup_errors => Off => Off
doc_root => no value => no value
docref_ext => no value => no value
docref_root => no value => no value
enable_dl => On => On
error_append_string => no value => no value
error_log => no value => no value
error_prepend_string => no value => no value
error_reporting => 2039 => 2039
expose_php => On => On
extension_dir => /usr/lib/php4/20050606 => /usr/lib/php4/20050606
file_uploads => On => On
gpc_order => GPC => GPC
highlight.bg => #FFFFFF => #FFFFFF
highlight.comment => #FF8000 => #FF8000
highlight.default => #0000BB => #0000BB
highlight.html => #000000 => #000000
highlight.keyword => #007700 => #007700
highlight.string => #DD0000 => #DD0000
html_errors => Off => On
ignore_repeated_errors => Off => Off
ignore_repeated_source => Off => Off
ignore_user_abort => Off => Off
implicit_flush => On => Off
include_path => .:/usr/share/php:/usr/share/pear => .:/usr/share/php:/usr/share/pear
log_errors => Off => Off
log_errors_max_len => 1024 => 1024
magic_quotes_gpc => On => On
magic_quotes_runtime => Off => Off
magic_quotes_sybase => Off => Off
max_execution_time => 0 => 30
max_input_time => 60 => 60
memory_limit => 8M => 8M
open_basedir => no value => no value
output_buffering => 0 => no value
output_handler => no value => no value
post_max_size => 8M => 8M
precision => 12 => 12
register_argc_argv => On => On
register_globals => Off => Off
report_memleaks => On => On
safe_mode => Off => Off
safe_mode_exec_dir => no value => no value
safe_mode_gid => Off => Off
safe_mode_include_dir => no value => no value
sendmail_from => no value => no value
sendmail_path => /usr/sbin/sendmail -t -i  => /usr/sbin/sendmail -t -i 
serialize_precision => 100 => 100
short_open_tag => On => On
SMTP => localhost => localhost
smtp_port => 25 => 25
sql.safe_mode => Off => Off
track_errors => Off => Off
unserialize_callback_func => no value => no value
upload_max_filesize => 2M => 2M
upload_tmp_dir => no value => no value
user_dir => no value => no value
variables_order => EGPCS => EGPCS
xmlrpc_error_number => 0 => 0
xmlrpc_errors => Off => Off
y2k_compliance => On => On

bcmath

BCMath support => enabled

bz2

BZip2 Support => Enabled
BZip2 Version => 1.0.3, 15-Feb-2005

calendar

Calendar support => enabled

ctype

ctype functions => enabled

dba

DBA support => enabled
Supported handlers => gdbm cdb cdb_make db4 inifile flatfile 

dbx

dbx support => enabled
dbx version => 1.0.0
supported databases => MySQL
ODBC
PostgreSQL
Microsoft SQL Server
FrontBase
Oracle 8 (oci8)
Sybase-CT

Directive => Local Value => Master Value
dbx.colnames_case => unchanged => unchanged

exif

EXIF Support => enabled
EXIF Version => 1.4 $Id: exif.c,v 1.118.2.37.2.4 2006/01/01 13:46:52 sniper Exp $
Supported EXIF Version => 0220
Supported filetypes => JPEG,TIFF

ftp

FTP support => enabled

gettext

GetText Support => enabled

iconv

iconv support => enabled
iconv implementation => glibc
iconv library version => 2.4

Directive => Local Value => Master Value
iconv.input_encoding => ISO-8859-1 => ISO-8859-1
iconv.internal_encoding => ISO-8859-1 => ISO-8859-1
iconv.output_encoding => ISO-8859-1 => ISO-8859-1

mbstring

Multibyte Support => enabled
Japanese support => enabled
Simplified chinese support => enabled
Traditional chinese support => enabled
Korean support => enabled
Russian support => enabled
Multibyte (japanese) regex support => enabled

                                        mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.                                        

Directive => Local Value => Master Value
mbstring.detect_order => no value => no value
mbstring.encoding_translation => Off => Off
mbstring.func_overload => 0 => 0
mbstring.http_input => pass => pass
mbstring.http_output => pass => pass
mbstring.internal_encoding => ISO-8859-1 => no value
mbstring.language => neutral => neutral
mbstring.substitute_character => no value => no value

mime_magic

mime_magic support => enabled

Directive => Local Value => Master Value
mime_magic.magicfile => /usr/share/file/magic.mime => /usr/share/file/magic.mime

ncurses

ncurses support => enabled
ncurses library version => 5.5
color support => yes

openssl

OpenSSL support => enabled
OpenSSL Version => OpenSSL 0.9.8a 11 Oct 2005

overload

User-Space Object Overloading Support => enabled

pcntl

pcntl support => enabled

pcre

PCRE (Perl Compatible Regular Expressions) Support => enabled
PCRE Library Version => 6.4 05-Sep-2005

posix

Revision => $Revision: 1.51.2.4.2.1 $

session

Session Support => enabled
Registered save handlers => files user 

Directive => Local Value => Master Value
session.auto_start => Off => Off
session.bug_compat_42 => On => On
session.bug_compat_warn => On => On
session.cache_expire => 180 => 180
session.cache_limiter => nocache => nocache
session.cookie_domain => no value => no value
session.cookie_lifetime => 0 => 0
session.cookie_path => / => /
session.cookie_secure => Off => Off
session.entropy_file => no value => no value
session.entropy_length => 0 => 0
session.gc_divisor => 100 => 100
session.gc_maxlifetime => 1440 => 1440
session.gc_probability => 0 => 0
session.name => PHPSESSID => PHPSESSID
session.referer_check => no value => no value
session.save_handler => files => files
session.save_path => /var/lib/php4 => /var/lib/php4
session.serialize_handler => php => php
session.use_cookies => On => On
session.use_only_cookies => Off => Off
session.use_trans_sid => Off => Off

shmop

shmop support => enabled

snmp

NET-SNMP Support => enabled
NET-SNMP Version => 5.2.2

sockets

Sockets Support => enabled

standard

Regex Library => Bundled library enabled
Dynamic Library Support => enabled
Path to sendmail => /usr/sbin/sendmail -t -i 

Directive => Local Value => Master Value
assert.active => 1 => 1
assert.bail => 0 => 0
assert.callback => no value => no value
assert.quiet_eval => 0 => 0
assert.warning => 1 => 1
auto_detect_line_endings => 0 => 0
default_socket_timeout => 60 => 60
safe_mode_allowed_env_vars => PHP_ => PHP_
safe_mode_protected_env_vars => LD_LIBRARY_PATH => LD_LIBRARY_PATH
url_rewriter.tags => a=href,area=href,frame=src,input=src,form=,fieldset= => a=href,area=href,frame=src,input=src,form=,fieldset=
user_agent => no value => no value

sysvmsg

sysvmsg support => enabled
Revision => $Revision: 1.4.2.5.2.2 $

tokenizer

Tokenizer Support => enabled

wddx

WDDX Support => enabled
WDDX Session Serializer => enabled

xml

XML Support => active
XML Namespace Support => active
EXPAT Version => expat_1.95.8

xmlrpc

core library version => xmlrpc-epi v. 0.51
php extension version => 0.51
author => Dan Libby
homepage => http://xmlrpc-epi.sourceforge.net
open sourced by => Epinions.com

yp

YP Support => enabled

zip

Zip support => enabled

zlib

ZLib Support => enabled
Compiled Version => 1.2.3
Linked Version => 1.2.3

Directive => Local Value => Master Value
zlib.output_compression => Off => Off
zlib.output_compression_level => -1 => -1
zlib.output_handler => no value => no value

Additional Modules

Module Name
filepro
sysvsem
sysvshm

Environment

Variable => Value
TERM => xterm-color
SHELL => /bin/bash
SSH_CLIENT => 192.168.1.223 60044 22
SSH_TTY => /dev/pts/0
USER => root
LS_COLORS => no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
MAIL => /var/mail/root
PATH => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
PWD => /var/log/cacti
LANG => en_US.UTF-8
SHLVL => 1
HOME => /root
LOGNAME => root
SSH_CONNECTION => 192.168.1.223 60044 192.168.1.17 22
LESSOPEN => | /usr/bin/lesspipe %s
LESSCLOSE => /usr/bin/lesspipe %s %s
_ => /usr/bin/php
OLDPWD => /usr/share/file

PHP Variables

Variable => Value
_SERVER["TERM"] => xterm-color
_SERVER["SHELL"] => /bin/bash
_SERVER["SSH_CLIENT"] => 192.168.1.223 60044 22
_SERVER["SSH_TTY"] => /dev/pts/0
_SERVER["USER"] => root
_SERVER["LS_COLORS"] => no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
_SERVER["MAIL"] => /var/mail/root
_SERVER["PATH"] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
_SERVER["PWD"] => /var/log/cacti
_SERVER["LANG"] => en_US.UTF-8
_SERVER["SHLVL"] => 1
_SERVER["HOME"] => /root
_SERVER["LOGNAME"] => root
_SERVER["SSH_CONNECTION"] => 192.168.1.223 60044 192.168.1.17 22
_SERVER["LESSOPEN"] => | /usr/bin/lesspipe %s
_SERVER["LESSCLOSE"] => /usr/bin/lesspipe %s %s
_SERVER["_"] => /usr/bin/php
_SERVER["OLDPWD"] => /usr/share/file
_SERVER["PHP_SELF"] => 
_SERVER["SCRIPT_NAME"] => 
_SERVER["SCRIPT_FILENAME"] => 
_SERVER["PATH_TRANSLATED"] => 
_SERVER["DOCUMENT_ROOT"] => 
_SERVER["argv"] => Array
(
)

_SERVER["argc"] => 0
_ENV["TERM"] => xterm-color
_ENV["SHELL"] => /bin/bash
_ENV["SSH_CLIENT"] => 192.168.1.223 60044 22
_ENV["SSH_TTY"] => /dev/pts/0
_ENV["USER"] => root
_ENV["LS_COLORS"] => no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
_ENV["MAIL"] => /var/mail/root
_ENV["PATH"] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
_ENV["PWD"] => /var/log/cacti
_ENV["LANG"] => en_US.UTF-8
_ENV["SHLVL"] => 1
_ENV["HOME"] => /root
_ENV["LOGNAME"] => root
_ENV["SSH_CONNECTION"] => 192.168.1.223 60044 192.168.1.17 22
_ENV["LESSOPEN"] => | /usr/bin/lesspipe %s
_ENV["LESSCLOSE"] => /usr/bin/lesspipe %s %s
_ENV["_"] => /usr/bin/php
_ENV["OLDPWD"] => /usr/share/file

PHP License
This program is free software; you can redistribute it and/or modify
it under the terms of the PHP License as published by the PHP Group
and included in the distribution in the file:  LICENSE

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

If you did not receive a copy of the PHP license, or have any
questions about PHP licensing, please contact license@php.net.
```

and just because it sounds like a good idea here is my phpinfo output through apache

```
PHP Logo
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
HTTP_COOKIE 	PHPSESSID=fc92f1dcad532766b8356a0716e52c63; clickedFoldert2=1%5E; highlightedTreeviewLinkt2=2
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 192.168.1.17 Port 80</address>
SERVER_SOFTWARE 	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
SERVER_NAME 	192.168.1.17
SERVER_ADDR 	192.168.1.17
SERVER_PORT 	80
REMOTE_ADDR 	192.168.1.223
DOCUMENT_ROOT 	/var/www
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/info.php
REMOTE_PORT 	60953
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
Cookie 	PHPSESSID=fc92f1dcad532766b8356a0716e52c63; clickedFoldert2=1%5E; highlightedTreeviewLinkt2=2
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
mbstring.internal_encoding	no value	no value
mbstring.language	neutral	neutral
mbstring.substitute_character	no value	no value

mime_magic
mime_magic support	enabled

Directive	Local Value	Master Value
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	1
Active Links 	1
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
PATH 	/usr/local/bin:/usr/bin:/bin
LANG 	C
PWD 	/root

PHP Variables
Variable	Value
_REQUEST["PHPSESSID"]	fc92f1dcad532766b8356a0716e52c63
_REQUEST["clickedFoldert2"]	1^
_REQUEST["highlightedTreeviewLinkt2"]	2
_COOKIE["PHPSESSID"]	fc92f1dcad532766b8356a0716e52c63
_COOKIE["clickedFoldert2"]	1^
_COOKIE["highlightedTreeviewLinkt2"]	2
_SERVER["HTTP_HOST"]	192.168.1.17
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.1) Gecko/20061018 Camino/1.1a1
_SERVER["HTTP_ACCEPT"]	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en,ja;q=0.9,fr;q=0.9,de;q=0.8,es;q=0.7,it;q=0.7,nl;q=0.6,sv;q=0.5,nb;q=0.5,da;q=0.4,fi;q=0.3,pt;q=0.3,zh-Hans;q=0.2,zh-Hant;q=0.1,ko;q=0.1
_SERVER["HTTP_ACCEPT_ENCODING"]	gzip,deflate
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_KEEP_ALIVE"]	300
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["HTTP_REFERER"]	http://192.168.1.17/
_SERVER["HTTP_COOKIE"]	PHPSESSID=fc92f1dcad532766b8356a0716e52c63; clickedFoldert2=1%5E; highlightedTreeviewLinkt2=2
_SERVER["PATH"]	/usr/local/bin:/usr/bin:/bin
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 192.168.1.17 Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
_SERVER["SERVER_NAME"]	192.168.1.17
_SERVER["SERVER_ADDR"]	192.168.1.17
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	192.168.1.223
_SERVER["DOCUMENT_ROOT"]	/var/www
_SERVER["SERVER_ADMIN"]	webmaster@localhost
_SERVER["SCRIPT_FILENAME"]	/var/www/info.php
_SERVER["REMOTE_PORT"]	60953
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
_ENV["PATH"]	/usr/local/bin:/usr/bin:/bin
_ENV["LANG"]	C
_ENV["PWD"]	/root

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
HTTP_COOKIE 	PHPSESSID=fc92f1dcad532766b8356a0716e52c63; clickedFoldert2=1%5E; highlightedTreeviewLinkt2=2
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at 192.168.1.17 Port 80</address>
SERVER_SOFTWARE 	Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1
SERVER_NAME 	192.168.1.17
SERVER_ADDR 	192.168.1.17
SERVER_PORT 	80
REMOTE_ADDR 	192.168.1.223
DOCUMENT_ROOT 	/var/www
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/info.php
REMOTE_PORT 	60953
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
Cookie 	PHPSESSID=fc92f1dcad532766b8356a0716e52c63; clickedFoldert2=1%5E; highlightedTreeviewLinkt2=2
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
mbstring.internal_encoding	no value	no value
mbstring.language	neutral	neutral
mbstring.substitute_character	no value	no value

mime_magic
mime_magic support	enabled

Directive	Local Value	Master Value
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

mysql
MySQL Support	enabled
Active Persistent Links 	1
Active Links 	1
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

I can't really think of anything else to give you mysql.err and mysql.log are empty, here is the last hour of logs from my syslog

```
Jan  4 09:17:01 minerva /USR/SBIN/CRON[8179]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan  4 09:20:01 minerva /USR/SBIN/CRON[8182]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:25:01 minerva /USR/SBIN/CRON[8187]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:30:01 minerva /USR/SBIN/CRON[8200]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:35:01 minerva /USR/SBIN/CRON[8203]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:39:01 minerva /USR/SBIN/CRON[8206]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Jan  4 09:40:01 minerva /USR/SBIN/CRON[8215]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:45:01 minerva /USR/SBIN/CRON[8218]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:50:01 minerva /USR/SBIN/CRON[8221]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 09:55:01 minerva /USR/SBIN/CRON[8224]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 10:00:01 minerva /USR/SBIN/CRON[8227]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 10:05:02 minerva /USR/SBIN/CRON[8230]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 10:09:01 minerva /USR/SBIN/CRON[8234]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Jan  4 10:10:01 minerva /USR/SBIN/CRON[8243]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Jan  4 10:15:01 minerva /USR/SBIN/CRON[8246]: (www-data) CMD (/usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
```

which is once again pointing back to 

*PHP Warning:  mime_magic: type regex            BEGIN[[:space:]]*[{]    application/x-awk invalid in Unknown on line 0*

Any help would be most appreciated :)

---

