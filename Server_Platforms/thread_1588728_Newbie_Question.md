---
title: "Newbie Question"
date: 2010-10-05
forum: Server Platforms
---

### Post by joek71 on 2010-10-05
Hello Guys

I just installed my apache2, mysql and php5.  I have a php site that my wed guy made i want to run it on my ubuntu server, where would i put the php files and all of my folders?  What do i need to do?

thank you in advance

---

### Post by Crazedpsyc on 2010-10-05
run thefollowing command from a terminal (Applications>Accessories>Terminal)
```
sudo cp *yourfiles* /var/www/
```
woops,  make sure you use /**var**/www/

---

### Post by amauk on 2010-10-05
you need to put all your files under /var/www

Once you've put the files there, you'll also need to change the ownership of the files to the user that apache runs under

You can do this with
```
sudo chown -R www-data:www-data /var/www
```

---

### Post by joek71 on 2010-10-05
i already copied them to that location, when i do localhost/index.php  i get blank screen in my browser

---

### Post by Crazedpsyc on 2010-10-05
which browser are you using? I had lots of trouble getting midori to go to mine, and I havn't tried konqueror. maybe just go to [http://localhost/](http://localhost/) from the browser without the index.php part and see if apache says anything.
if not open that terminal back up and enter:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by joek71 on 2010-10-05
I am using firefox that comes with ubuntu, i tried to restart apache2 and it restarted fine, i still getting only blank page. No errors or anything, strange, i tried the test.html file that works fine but .php is not working.

---

### Post by krishnandu.sarkar on 2010-10-05
Ohh you may not have configured Apache, PHP and MySQL.

Refer [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to configure them.

But the best would be to install them using tasksel as mentioned there. It will configure everything for you.

---

### Post by Crazedpsyc on 2010-10-05
Ok now I know what the problem is. You have to install the apache2 php5 module
```
sudo apt-get install libapache2-mod-php5
```
then enable it with
```
sudo a2enmod php5
```
then finally restart apache2 again

---

### Post by joek71 on 2010-10-05
Thank you, i followed the instructions to the letter and now it gives me ERROR 403 Forbidden
This is progress, but what did i do wrong?

---

### Post by krishnandu.sarkar on 2010-10-05
I think that's permission error. Did you set required permission as mentioned in previous posts..??

---

### Post by Crazedpsyc on 2010-10-05
what are the permissions and owner of the files in /var/www/? especially index.php? they should be root.
If they are not run
```
sudo nautilus /var/www/
```
to change them

---

### Post by joek71 on 2010-10-05
You mean ' chown ' yes i did

---

### Post by joek71 on 2010-10-05
It should not make any difference if i trying to loaf .html or .php right

---

### Post by krishnandu.sarkar on 2010-10-05
What about permissions of those .html / .php files..??

---

### Post by Crazedpsyc on 2010-10-05
Yes I do mean chown but I find GUIs so much prettier! hummm, I just installed apache2 and it worked instantly. let me see...
according to this guide you ave done everything necessary
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
what version of ubuntu are you using?

the index.php permissions should look like this in text view "-rwxrwxr-x"
and the owner and group should both be root.

---

### Post by joek71 on 2010-10-05
How do i set permission for m files? I have them in /var/www/public_html

---

### Post by krishnandu.sarkar on 2010-10-05
god...that's why...use localhost/public_html/index.html

---

### Post by joek71 on 2010-10-05
tried that says not found :confused:

---

### Post by krishnandu.sarkar on 2010-10-05
Great...!! It's improving. Do you have that index.html file..?? Just replace index.html with the file you want.

I mean the php file that you want. localhost/public_html/filename.php

---

### Post by joek71 on 2010-10-05
i did the ls -l got this;

-rwxr-xr-x  1 root root   472 2010-08-23 10:38 index.php

---

### Post by joek71 on 2010-10-05
Now again got blank white screen, i no need to run .html i need to run index.php
does it make a difference between .html or .php, ?

---

### Post by krishnandu.sarkar on 2010-10-05
yes...of course...then use index.php instead of index.html

---

### Post by joek71 on 2010-10-05
got error 404 NOT FOUND

Thank you for helping with this problem.

---

### Post by krishnandu.sarkar on 2010-10-05
404 Error means the file you are referring to doesn't exist. Did you put the index.php file in /var/www or /var/www/public_html ??

---

### Post by joek71 on 2010-10-05
Yes I did, and got the same error, will try tomorrow when i get in to work.

Thanks

---

### Post by SeijiSensei on 2010-10-05
A totally blank page often means there's an error in the PHP scripts that occurs before any HTML is sent to the browser.  For instance, all my sites run an "init" script before any HTML is displayed that does vital housekeeping tasks like connecting to the database, parsing the request, etc.  If I have an error in that script, I'll get a blank page.

At one time PHP displayed errors on the page, but that was ruled a security risk so now the errors only appear in the logs.  If you look in /etc/php5/apache2/php.ini, find the "display_errors" directive and set it to "on".  Then restart apache with "sudo service apache2 restart".  Now you'll see PHP errors within the HTML documents themselves.  Remember to turn this off again for production.  You should also see the errors PHP throws in /var/log/apache2/error.log.

Here's a simple and useful test to see if PHP is running correctly.  Create a file like this:

```
cd /var/www
echo '<? phpinfo() ?>' > testing.php
```

Now try accessing testing.php instead of index.php.  If everything is working as advertised, you'll see a [long display of PHP options and features]("http://de.php.net/manual/en/function.phpinfo.php").

One more thing, make sure there are no index.html or index.htm files in the same directory as index.php.  By default, Apache will display those as the index page in favor of the PHP script.

---

### Post by joek71 on 2010-10-06
That worked gave me a entire read out of php info

---

### Post by SeijiSensei on 2010-10-06
You might want to check that information to make sure PHP has MySQL connectivity.  You should see a block of information with "mysql" at the top.

Time to start debugging is my guess; look in the logs and turn on display_errors as I mentioned above.

---

### Post by joek71 on 2010-10-06
here is my output:

echo '  body { background-color: rgb(255, 255, 255); color: rgb(0, 0, 0); }body, td, th, h1, h2 { font-family: sans-serif; }pre { margin: 0px; font-family: monospace; }a:link { color: rgb(0, 0, 153); text-decoration: none; background-color: rgb(255, 255, 255); }a:hover { text-decoration: underline; }table { border-collapse: collapse; }.center { text-align: center; }.center table { margin-left: auto; margin-right: auto; text-align: left; }.center th { text-align: center ! important; }td, th { border: 1px solid rgb(0, 0, 0); font-size: 75%; vertical-align: baseline; }h1 { font-size: 150%; }h2 { font-size: 125%; }.p { text-align: left; }.e { background-color: rgb(204, 204, 255); font-weight: bold; color: rgb(0, 0, 0); }.h { background-color: rgb(153, 153, 204); font-weight: bold; color: rgb(0, 0, 0); }.v { background-color: rgb(204, 204, 204); color: rgb(0, 0, 0); }.vr { background-color: rgb(204, 204, 204); text-align: right; color: rgb(0, 0, 0); }img { float: right; border: 0px none; }hr { width: 600px; background-color: rgb(204, 204, 204); border: 0px none; height: 1px; color: rgb(0, 0, 0); }    [[IMG]http://192.168.1.133/testing.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42[/IMG]]("http://www.php.net/")**PHP Version 5.3.2-1ubuntu4.5**

  
 System Linux cupidtest 2.6.32-25-server #44-Ubuntu SMP Fri Sep 17 21:13:39 UTC 2010 x86_64  Build Date Sep 17 2010 13:40:34  Server API Apache 2.0 Handler  Virtual Directory Support disabled  Configuration File (php.ini) Path /etc/php5/apache2  Loaded Configuration File /etc/php5/apache2/php.ini  Scan this dir for additional .ini files /etc/php5/apache2/conf.d  Additional .ini files parsed /etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mcrypt.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini   PHP API 20090626  PHP Extension 20090626  Zend Extension 220090626  Zend Extension Build API220090626,NTS  PHP Extension Build API20090626,NTS  Debug Build no  Thread Safety disabled  Zend Memory Manager enabled  Zend Multibyte Support disabled  IPv6 Support enabled  Registered PHP Streams https, ftps, compress.zlib, compress.bzip2, php, file, glob, data, http, ftp, phar, zip    Registered Stream Socket Transports tcp, udp, unix, udg, ssl, sslv3, sslv2, tls  Registered Stream Filters zlib.*, bzip2.*, convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, dechunk  
  [[IMG]http://192.168.1.133/testing.php?=SUHO8567F54-D428-14d2-A769-00DA302A5F18[/IMG]]("http://www.suhosin.org/") This server is protected with the Suhosin Patch 0.9.9.1
Copyright (c) 2006-2007 [Hardened-PHP Project]("http://www.hardened-php.net/") Copyright (c) 2007-2009 [SektionEins GmbH]("http://www.sektioneins.de/")  
  [[IMG]http://192.168.1.133/testing.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42[/IMG]]("http://www.zend.com/") This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

 **[PHP Credits]("http://192.168.1.133/testing.php?=PHPB8B5F2A0-3C92-11d3-A3A9-4C7B08C10000")**

  **Configuration**

 **apache2handler**

  Apache Version Apache/2.2.14 (Ubuntu)  Apache API Version 20051115  Server Administrator [no address given]  Hostname:Port host:0  User/Group www-data(33)/33  Max Requests Per Child: 0 - Keep Alive: on - Max Per Connection: 100  Timeouts Connection: 300 - Keep-Alive: 15  Virtual Server Yes  Server Root /var/www  Loaded Modules core mod_log_config  mod_logio prefork http_core mod_so mod_alias mod_auth_basic  mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host  mod_authz_user mod_autoindex mod_cgi mod_deflate mod_dir mod_env  mod_mime mod_negotiation mod_php5 mod_reqtimeout mod_rewrite  mod_setenvif mod_status  
 DirectiveLocal ValueMaster Value engine11 last_modified00 xbithack00 
**Apache Environment**

  VariableValue HTTP_HOST 192.168.1.133  HTTP_USER_AGENT Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10  HTTP_ACCEPT text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  HTTP_ACCEPT_LANGUAGE en-us,en;q=0.5  HTTP_ACCEPT_ENCODING gzip,deflate  HTTP_ACCEPT_CHARSET ISO-8859-1,utf-8;q=0.7,*;q=0.7  HTTP_KEEP_ALIVE 115  HTTP_CONNECTION keep-alive  HTTP_CACHE_CONTROL max-age=0  PATH /usr/local/bin:/usr/bin:/bin  SERVER_SIGNATURE <address>Apache/2.2.14 (Ubuntu) Server at 192.168.1.133 Port 80</address>   SERVER_SOFTWARE Apache/2.2.14 (Ubuntu)  SERVER_NAME 192.168.1.133  SERVER_ADDR 192.168.1.133  SERVER_PORT 80  REMOTE_ADDR 192.168.1.133  DOCUMENT_ROOT /var/www/  SERVER_ADMIN [no address given]  SCRIPT_FILENAME /var/www/testing.php  REMOTE_PORT 44309  GATEWAY_INTERFACE CGI/1.1  SERVER_PROTOCOL HTTP/1.1  REQUEST_METHOD GET  QUERY_STRING *no value*  REQUEST_URI /testing.php  SCRIPT_NAME /testing.php  
**HTTP Headers Information**

  HTTP Request Headers HTTP Request GET /testing.php HTTP/1.1  Host 192.168.1.133  User-Agent Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10  Accept text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  Accept-Language en-us,en;q=0.5  Accept-Encoding gzip,deflate  Accept-Charset ISO-8859-1,utf-8;q=0.7,*;q=0.7  Keep-Alive 115  Connection keep-alive  Cache-Control max-age=0  HTTP Response Headers X-Powered-By PHP/5.3.2-1ubuntu4.5  Vary Accept-Encoding  Content-Encoding gzip  
**bcmath**

  BCMath support enabled  
 DirectiveLocal ValueMaster Value bcmath.scale00 
**bz2**

  BZip2 Support Enabled  Stream Wrapper support compress.bz2://  Stream Filter support bzip2.decompress, bzip2.compress  BZip2 Version 1.0.5, 10-Dec-2007  
**calendar**

  Calendar support enabled  
**Core**

  PHP Version 5.3.2-1ubuntu4.5  
 DirectiveLocal ValueMaster Value allow_call_time_pass_referenceOffOff allow_url_fopenOnOn allow_url_includeOffOff always_populate_raw_post_dataOffOff arg_separator.input&& arg_separator.output&& asp_tagsOffOff auto_append_file*no value**no value* auto_globals_jitOnOn auto_prepend_file*no value**no value* browscap*no value**no value* default_charset*no value**no value* default_mimetypetext/htmltext/html define_syslog_variablesOffOff disable_classes*no value**no value* disable_functions*no value**no value* display_errorsOffOff display_startup_errorsOffOff doc_root*no value**no value* docref_ext*no value**no value* docref_root*no value**no value* enable_dlOffOff error_append_string*no value**no value* error_log*no value**no value* error_prepend_string*no value**no value* error_reporting2252722527 exit_on_timeoutOffOff expose_phpOnOn extension_dir/usr/lib/php5/20090626/usr/lib/php5/20090626 file_uploadsOnOn highlight.bg[COLOR=#FFFFFF]#FFFFFF[/COLOR][COLOR=#FFFFFF]#FFFFFF[/COLOR] highlight.comment[COLOR=#FF8000]#FF8000[/COLOR][COLOR=#FF8000]#FF8000[/COLOR] highlight.default[COLOR=#0000BB]#0000BB[/COLOR][COLOR=#0000BB]#0000BB[/COLOR] highlight.html[COLOR=#000000]#000000[/COLOR][COLOR=#000000]#000000[/COLOR] highlight.keyword[COLOR=#007700]#007700[/COLOR][COLOR=#007700]#007700[/COLOR] highlight.string[COLOR=#DD0000]#DD0000[/COLOR][COLOR=#DD0000]#DD0000[/COLOR] html_errorsOffOff ignore_repeated_errorsOffOff ignore_repeated_sourceOffOff ignore_user_abortOffOff implicit_flushOffOff include_path.:/usr/share/php:/usr/share/pear.:/usr/share/php:/usr/share/pear log_errorsOnOn log_errors_max_len10241024 magic_quotes_gpcOffOff magic_quotes_runtimeOffOff magic_quotes_sybaseOffOff mail.add_x_headerOnOn mail.force_extra_parameters*no value**no value* mail.log*no value**no value* max_execution_time3030 max_file_uploads2020 max_input_nesting_level6464 max_input_time6060 memory_limit128M128M open_basedir*no value**no value* output_buffering40964096 output_handler*no value**no value* post_max_size8M8M precision1414 realpath_cache_size16K16K realpath_cache_ttl120120 register_argc_argvOffOff register_globalsOffOff register_long_arraysOffOff report_memleaksOnOn report_zend_debugOnOn request_orderGPGP safe_modeOffOff safe_mode_exec_dir*no value**no value* safe_mode_gidOffOff safe_mode_include_dir*no value**no value* sendmail_from*no value**no value* sendmail_path/usr/sbin/sendmail -t -i /usr/sbin/sendmail -t -i  serialize_precision100100 short_open_tagOnOn SMTPlocalhostlocalhost smtp_port2525 sql.safe_modeOffOff track_errorsOffOff unserialize_callback_func*no value**no value* upload_max_filesize2M2M upload_tmp_dir*no value**no value* user_dir*no value**no value* user_ini.cache_ttl300300 user_ini.filename.user.ini.user.ini variables_orderGPCSGPCS xmlrpc_error_number00 xmlrpc_errorsOffOff y2k_complianceOnOn zend.enable_gcOnOn 
**ctype**

  ctype functions enabled  
**date**

  date/time support enabled  "Olson" Timezone Database Version 0.system  Timezone Database internal  Default timezone America/New_York  
 DirectiveLocal ValueMaster Value date.default_latitude31.766731.7667 date.default_longitude35.233335.2333 date.sunrise_zenith90.58333390.583333 date.sunset_zenith90.58333390.583333 date.timezone*no value**no value* 
**dba**

  DBA support enabled  Supported handlers cdb cdb_make db4 inifile flatfile   
 DirectiveLocal ValueMaster Value dba.default_handlerflatfileflatfile 
**dom**

  DOM/XML enabled  DOM/XML API Version 20031129  libxml Version 2.7.6  HTML Support enabled  XPath Support enabled  XPointer Support enabled  Schema Support enabled  RelaxNG Support enabled  
**ereg**

  Regex Library Bundled library enabled  
**exif**

  EXIF Support enabled  EXIF Version 1.4 $Id: exif.c 293036 2010-01-03 09:23:27Z sebastian $  Supported EXIF Version 0220  Supported filetypes JPEG,TIFF  
 DirectiveLocal ValueMaster Value exif.decode_jis_intelJISJIS exif.decode_jis_motorolaJISJIS exif.decode_unicode_intelUCS-2LEUCS-2LE exif.decode_unicode_motorolaUCS-2BEUCS-2BE exif.encode_jis*no value**no value* exif.encode_unicodeISO-8859-15ISO-8859-15 
**fileinfo**

  fileinfo supportenabled version 1.0.5-dev  
**filter**

  Input Validation and Filtering enabled  Revision $Revision: 294106 $  
 DirectiveLocal ValueMaster Value filter.defaultunsafe_rawunsafe_raw filter.default_flags*no value**no value* 
**ftp**

  FTP support enabled  
**gd**

  GD Support enabled  GD Version 2.0  FreeType Support enabled  FreeType Linkage with freetype  FreeType Version 2.3.11  T1Lib Support enabled  GIF Read Support enabled  GIF Create Support enabled  JPEG Support enabled  libJPEG Version 6b  PNG Support enabled  libPNG Version 1.2.42  WBMP Support enabled  
 DirectiveLocal ValueMaster Value gd.jpeg_ignore_warning00 
**gettext**

  GetText Support enabled  
**hash**

  hash support enabled  Hashing Engines md2 md4 md5 sha1  sha224 sha256 sha384 sha512 ripemd128 ripemd160 ripemd256 ripemd320  whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4  tiger192,4 snefru snefru256 gost adler32 crc32 crc32b salsa10 salsa20  haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4  haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5  haval192,5 haval224,5 haval256,5   
**iconv**

  iconv support enabled  iconv implementation glibc  iconv library version 2.11.1  
 DirectiveLocal ValueMaster Value iconv.input_encodingISO-8859-1ISO-8859-1 iconv.internal_encodingISO-8859-1ISO-8859-1 iconv.output_encodingISO-8859-1ISO-8859-1 
**json**

  json support enabled  json version 1.2.1  
**libxml**

  libXML support active  libXML Compiled Version 2.7.6  libXML Loaded Version 20706  libXML streams enabled  
**mbstring**

  Multibyte Support enabled  Multibyte string engine libmbfl  HTTP input encoding translation disabled  
 mbstring extension makes use of "streamable  kanji code filter and converter", which is distributed under the GNU  Lesser General Public License version 2.1. 
 Multibyte (japanese) regex support enabled  Multibyte regex (oniguruma) backtrack check On  Multibyte regex (oniguruma) version 4.7.1  
 DirectiveLocal ValueMaster Value mbstring.detect_order*no value**no value* mbstring.encoding_translationOffOff mbstring.func_overload00 mbstring.http_inputpasspass mbstring.http_outputpasspass mbstring.http_output_conv_mimetypes^(text/|application/xhtml\+xml)^(text/|application/xhtml\+xml) mbstring.internal_encoding*no value**no value* mbstring.languageneutralneutral mbstring.strict_detectionOffOff mbstring.substitute_character*no value**no value* 
**mcrypt**

  mcrypt supportenabled Version 2.5.8  Api No 20021217  Supported ciphers cast-128 gost  rijndael-128 twofish arcfour cast-256 loki97 rijndael-192 saferplus wake  blowfish-compat des rijndael-256 serpent xtea blowfish enigma rc2  tripledes   Supported modes cbc cfb ctr ecb ncfb nofb ofb stream   
 DirectiveLocal ValueMaster Value mcrypt.algorithms_dir*no value**no value* mcrypt.modes_dir*no value**no value* 
**mhash**

  MHASH support Enabled  MHASH API Version Emulated Support  
**mysql**

  MySQL Supportenabled Active Persistent Links 0  Active Links 0  Client API version 5.1.41  MYSQL_MODULE_TYPE external  MYSQL_SOCKET /var/run/mysqld/mysqld.sock  MYSQL_INCLUDE -I/usr/include/mysql  MYSQL_LIBS -L/usr/lib -lmysqlclient_r   
 DirectiveLocal ValueMaster Value mysql.allow_local_infileOnOn mysql.allow_persistentOnOn mysql.connect_timeout6060 mysql.default_host*no value**no value* mysql.default_password*no value**no value* mysql.default_port*no value**no value* mysql.default_socket/var/run/mysqld/mysqld.sock/var/run/mysqld/mysqld.sock mysql.default_user*no value**no value* mysql.max_linksUnlimitedUnlimited mysql.max_persistentUnlimitedUnlimited mysql.trace_modeOffOff 
**mysqli**

  MysqlI Supportenabled Client API library version 5.1.41  Active Persistent Links 0  Inactive Persistent Links 0  Active Links 0  Client API header version 5.1.41  MYSQLI_SOCKET /var/run/mysqld/mysqld.sock  
 DirectiveLocal ValueMaster Value mysqli.allow_local_infileOnOn mysqli.allow_persistentOnOn mysqli.default_host*no value**no value* mysqli.default_port33063306 mysqli.default_pw*no value**no value* mysqli.default_socket*no value**no value* mysqli.default_user*no value**no value* mysqli.max_linksUnlimitedUnlimited mysqli.max_persistentUnlimitedUnlimited mysqli.reconnectOffOff 
**openssl**

  OpenSSL support enabled  OpenSSL Library Version OpenSSL 0.9.8k 25 Mar 2009  OpenSSL Header Version OpenSSL 0.9.8k 25 Mar 2009  
**pcre**

  PCRE (Perl Compatible Regular Expressions) Support enabled  PCRE Library Version 7.8 2008-09-05  
 DirectiveLocal ValueMaster Value pcre.backtrack_limit100000100000 pcre.recursion_limit100000100000 
**PDO**

  PDO supportenabled PDO drivers mysql  
**pdo_mysql**

  PDO Driver for MySQLenabled Client API version 5.1.41  
**Phar**

  Phar: PHP Archive supportenabled Phar EXT version 2.0.1  Phar API version 1.1.1  SVN revision $Revision: 290435 $  Phar-based phar archives enabled  Tar-based phar archives enabled  ZIP-based phar archives enabled  gzip compression enabled  bzip2 compression enabled  OpenSSL support enabled  
  Phar based on pear/PHP_Archive, original concept by Davey Shafik.
Phar fully realized by Gregory Beaver and Marcus Boerger.
Portions of tar implementation Copyright (c) 2003-2009 Tim Kientzle. 
 DirectiveLocal ValueMaster Value phar.cache_list*no value**no value* phar.readonlyOnOn phar.require_hashOnOn 
**posix**

  Revision $Revision: 293036 $  
**Reflection**

  Reflectionenabled Version $Revision: 293036 $  
**session**

  Session Support enabled  Registered save handlers files user   Registered serializer handlers php php_binary wddx   
 DirectiveLocal ValueMaster Value session.auto_startOffOff session.bug_compat_42OffOff session.bug_compat_warnOffOff session.cache_expire180180 session.cache_limiternocachenocache session.cookie_domain*no value**no value* session.cookie_httponlyOffOff session.cookie_lifetime00 session.cookie_path// session.cookie_secureOffOff session.entropy_file*no value**no value* session.entropy_length00 session.gc_divisor10001000 session.gc_maxlifetime14401440 session.gc_probability11 session.hash_bits_per_character55 session.hash_function00 session.namePHPSESSIDPHPSESSID session.referer_check*no value**no value* session.save_handlerfilesfiles session.save_path/var/lib/php5/var/lib/php5 session.serialize_handlerphpphp session.use_cookiesOnOn session.use_only_cookiesOnOn session.use_trans_sid00 
**shmop**

  shmop support enabled  
**SimpleXML**

  Simplexml supportenabled Revision $Revision: 293036 $  Schema support enabled  
**soap**

  Soap Client enabled  Soap Server enabled  
 DirectiveLocal ValueMaster Value soap.wsdl_cache11 soap.wsdl_cache_dir/tmp/tmp soap.wsdl_cache_enabled11 soap.wsdl_cache_limit55 soap.wsdl_cache_ttl8640086400 
**sockets**

  Sockets Support enabled  
**SPL**

  SPL supportenabled Interfaces Countable, OuterIterator, RecursiveIterator, SeekableIterator, SplObserver, SplSubject  Classes AppendIterator,  ArrayIterator, ArrayObject, BadFunctionCallException,  BadMethodCallException, CachingIterator, DirectoryIterator,  DomainException, EmptyIterator, FilesystemIterator, FilterIterator,  GlobIterator, InfiniteIterator, InvalidArgumentException,  IteratorIterator, LengthException, LimitIterator, LogicException,  MultipleIterator, NoRewindIterator, OutOfBoundsException,  OutOfRangeException, OverflowException, ParentIterator, RangeException,  RecursiveArrayIterator, RecursiveCachingIterator,  RecursiveDirectoryIterator, RecursiveFilterIterator,  RecursiveIteratorIterator, RecursiveRegexIterator,  RecursiveTreeIterator, RegexIterator, RuntimeException,  SplDoublyLinkedList, SplFileInfo, SplFileObject, SplFixedArray, SplHeap,  SplMinHeap, SplMaxHeap, SplObjectStorage, SplPriorityQueue, SplQueue,  SplStack, SplTempFileObject, UnderflowException,  UnexpectedValueException  
**standard**

  Dynamic Library Support enabled  Path to sendmail /usr/sbin/sendmail -t -i   
 DirectiveLocal ValueMaster Value assert.active11 assert.bail00 assert.callback*no value**no value* assert.quiet_eval00 assert.warning11 auto_detect_line_endings00 default_socket_timeout6060 safe_mode_allowed_env_varsPHP_PHP_ safe_mode_protected_env_varsLD_LIBRARY_PATHLD_LIBRARY_PATH url_rewriter.tagsa=href,area=href,frame=src,input=src,form=fakeentrya=href,area=href,frame=src,input=src,form=fakeentry user_agent*no value**no value* 
**sysvmsg**

  sysvmsg support enabled  Revision $Revision: 293036 $  
**tokenizer**

  Tokenizer Support enabled  
**wddx**

  WDDX Supportenabled WDDX Session Serializer enabled  
**xml**

  XML Support active  XML Namespace Support active  libxml2 Version 2.7.6  
**xmlreader**

  XMLReader enabled  
**xmlwriter**

  XMLWriter enabled  
**zip**

  Zip enabled  Extension Version $Id: php_zip.c 294817 2010-02-09 17:51:39Z pajoye $  Zip version 1.9.1  Libzip version 0.9.0  
**zlib**

  ZLib Support enabled  Stream Wrapper support compress.zlib://  Stream Filter support zlib.inflate, zlib.deflate  Compiled Version 1.2.1.1  Linked Version 1.2.3.3  
 DirectiveLocal ValueMaster Value zlib.output_compressionOffOff zlib.output_compression_level-1-1 zlib.output_handler*no value**no value* 
**Additional Modules**

  Module Name sysvsem sysvshm 
**Environment**

  VariableValue APACHE_PID_FILE /var/run/apache2.pid  PATH /usr/local/bin:/usr/bin:/bin  LANG C  APACHE_RUN_GROUP www-data  APACHE_RUN_USER www-data  PWD /home/joe  
**PHP Variables**

  VariableValue _SERVER["HTTP_HOST"]192.168.1.133 _SERVER["HTTP_USER_AGENT"]Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10 _SERVER["HTTP_ACCEPT"]text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 _SERVER["HTTP_ACCEPT_LANGUAGE"]en-us,en;q=0.5 _SERVER["HTTP_ACCEPT_ENCODING"]gzip,deflate _SERVER["HTTP_ACCEPT_CHARSET"]ISO-8859-1,utf-8;q=0.7,*;q=0.7 _SERVER["HTTP_KEEP_ALIVE"]115 _SERVER["HTTP_CONNECTION"]keep-alive _SERVER["HTTP_CACHE_CONTROL"]max-age=0 _SERVER["PATH"]/usr/local/bin:/usr/bin:/bin _SERVER["SERVER_SIGNATURE"]<address>Apache/2.2.14 (Ubuntu) Server at 192.168.1.133 Port 80</address>  _SERVER["SERVER_SOFTWARE"]Apache/2.2.14 (Ubuntu) _SERVER["SERVER_NAME"]192.168.1.133 _SERVER["SERVER_ADDR"]192.168.1.133 _SERVER["SERVER_PORT"]80 _SERVER["REMOTE_ADDR"]192.168.1.133 _SERVER["DOCUMENT_ROOT"]/var/www/ _SERVER["SERVER_ADMIN"][no address given] _SERVER["SCRIPT_FILENAME"]/var/www/testing.php _SERVER["REMOTE_PORT"]44309 _SERVER["GATEWAY_INTERFACE"]CGI/1.1 _SERVER["SERVER_PROTOCOL"]HTTP/1.1 _SERVER["REQUEST_METHOD"]GET _SERVER["QUERY_STRING"]*no value* _SERVER["REQUEST_URI"]/testing.php _SERVER["SCRIPT_NAME"]/testing.php _SERVER["PHP_SELF"]/testing.php _SERVER["REQUEST_TIME"]1286383355 
**PHP License**

    This program is free software; you can redistribute it and/or modify it  under the terms of the PHP License as published by the PHP Group and  included in the distribution in the file:  LICENSE 
 This program is distributed in the hope that it will be useful, but  WITHOUT ANY WARRANTY; without even the implied warranty of  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. 
 If you did not receive a copy of the PHP license, or have any questions about PHP licensing, please contact [email]license@php.net[/email]. 
  

' >

---

### Post by joek71 on 2010-10-06
I tried another site with php and it worked, so all is good.

THANK YOU GUYS FOR ALL YOUR HELP, YOU GUYS ARE AWESOME!!!!!!:):):)

---

