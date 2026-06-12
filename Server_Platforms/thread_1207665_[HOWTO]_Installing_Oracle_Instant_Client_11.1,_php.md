---
title: "[HOWTO] Installing Oracle Instant Client 11.1, php_pdo, &amp; oci8"
date: 2009-07-08
forum: Server Platforms
---

### Post by coolaj86 on 2009-07-08
This tutorial should work for any recent version of the oracle instant client 9.0, 10.0, 10.1, 10.2, 11.1

I recommend that you run this after each step - that way you can see what errors you encounter and notice that they change and that therefore you are making progress
```

#!/usr/bin/env php
# instantclient_test.php
# Usage ORACLE_HOME=/opt/oracle/instantclient TNS_NAMES=ORACLE_HOME=/opt/oracle/instantclient/network/admin php instantclient_test.php
<?php
# Resources
# http://wiki.oracle.com/page/PHP+Oracle+FAQ
# http://download-west.oracle.com/docs/cd/B12037_01/network.101/b10775/naming.htm#i498306
# http://ubuntuforums.org/showthread.php?p=7581997
        $username = 'user';
        $password = 'secret';
        $host = 'example.com';
        $port = '1521';
        $service_name = 'service.example.com';
        $tns_service_name = 'TNSSERVICENAME';

        echo "\nTesting OCI8\n";
        echo "Connecting using dsn for Instant Client EZCONNECT: ";
        oci_connect($username, $password, "//$host:$port/$service_name");
        echo " No Exceptions! Yay!\n";
        echo "Connecting using TNSNAMES service name: ";
        oci_connect($username, $password, $tns_service_name);
        echo " No Exceptions! Yay!\n";
        echo "\n";

        echo "\nTesting PDO_OCI\n";
        echo "Connecting using dsn for Instant Client EZCONNECT: ";
        $dbc = new PDO("oci:dbname=//$host:$port/$service_name", $username, $password);
        echo " No Exceptions! Yay!\n";
        echo "Connecting using TNSNAMES service name: ";
        $dbc = new PDO("oci:dbname=$tns_service_name", $username, $password);
        echo " No Exceptions! Yay!\n";
        echo "\n";
?>

```

Install the Oracle Client
* All your bases are belong to Oracle (that's code for: You must register :mad:)
* Then download the instantclient and SDK from [http://www.oracle.com/technology/software/tech/oci/instantclient/index.html](http://www.oracle.com/technology/software/tech/oci/instantclient/index.html) 
```

sudo su -
mkdir -p /opt/oracle/instantclient
cd /opt/oracle/instantclient
# place oracle zip files here
unzip instantclient-basic-*-*.zip
unzip instantclient-sdk-*-*.zip
mv instantclient*/* ./
rmdir instantclient*/

# Just do this because I say so
ln -s libclntsh.so.* libclntsh.so
ln -s libocci.so.* libocci.so
echo /opt/oracle/instantclient >> /etc/ld.so.conf
ldconfig

# Set up your sqlnet.ora & tnsnames.ora
mkdir -p network/admin
cat - <<EOF > network/admin/sqlnet.ora
# sqlnet.ora Network Configuration File
NAMES.DIRECTORY_PATH= (TNSNAMES, EZCONNECT)
EOF

cat - <<EOF > network/admin/tnsnames.ora
# TNSNAMES.ORA Network Configuration File
THETNSNAME =
  (DESCRIPTION =
    (ADDRESS_LIST =
      (ADDRESS = (PROTOCOL = TCP)(HOST = example.com)(PORT = 1521))
    )
    (CONNECT_DATA =
      (SERVICE_NAME = service.example.com)
    )
  )
EOF

```

* Now ready your Ubuntu box for oci8 (easier than php_pdo by far)
```

# run the test script
apt-get install --yes php5 php5-cli php5-dev php-db php-pear
apt-get install --yes build-essential libaio1
# run the test script

```
* Now here comes the hardest part, pay close attention: Ignore what the screen says and just do what I tell you. If you do this right you will only get 3 prompts. 2 shalt thou not answer except that thou proceedest to 3. 5 is right out.
```

pecl install oci8
# prompt 1: all
# prompt 2: shared,instantclient,/opt/oracle/instantclient
# prompt 3: [enter]

# skin a cat...
cat - <<EOF > /etc/php5/apache2/conf.d/oci8.ini
# configuration for php OCI8 module
extension=oci8.so
EOF

# And just because there's more than one way to skin a cat...
echo "# configuration for php OCI8 module" > /etc/php5/cli/conf.d/oci8.ini
echo "extension=oci8.so" >> /etc/php5/cli/conf.d/oci8.ini

# run the test script - it should work

```

* Installing pdo_oci is a little more tricky since it has not been updated since 2005
# First we have to fake it out because it's set up to work for the rpm installation of the client
```

cd /usr/include/
ln -s php5 php

cd /opt/oracle/instantclient

mkdir -p include/oracle/11.1/
cd include/oracle/11.1/
ln -s ../../../sdk/include client
cd -

mkdir -p lib/oracle/11.1/client
cd lib/oracle/11.1/client
ln -s ../../../../ lib
cd -

pecl channel-update pear.php.net
# I'm pretty sure it's safe to skip this step, but I did it
#pecl install pdo # this breaks pdo_mysql if you had it installed prior
#apt-get install libmysqlclient15-dev && pecl install pdo_mysql
mkdir -p /tmp/pear/download/
cd /tmp/pear/download/
pecl download pdo_oci
tar xvf PDO_OCI*.tgz
cd PDO_OCI*

##### Can't do this with cat #####
### copy the lines below into the file "config.m4.patch"
*** config.m4	2005-09-24 17:23:24.000000000 -0600
--- /home/myuser/Desktop/PDO_OCI-1.0/config.m4	2009-07-07 17:32:14.000000000 -0600
***************
*** 7,12 ****
--- 7,14 ----
    if test -s "$PDO_OCI_DIR/orainst/unix.rgs"; then
      PDO_OCI_VERSION=`grep '"ocommon"' $PDO_OCI_DIR/orainst/unix.rgs | sed 's/[ ][ ]*/:/g' | cut -d: -f 6 | cut -c 2-4`
      test -z "$PDO_OCI_VERSION" && PDO_OCI_VERSION=7.3
+   elif test -f $PDO_OCI_DIR/lib/libclntsh.$SHLIB_SUFFIX_NAME.11.1; then
+     PDO_OCI_VERSION=11.1    
    elif test -f $PDO_OCI_DIR/lib/libclntsh.$SHLIB_SUFFIX_NAME.10.1; then
      PDO_OCI_VERSION=10.1    
    elif test -f $PDO_OCI_DIR/lib/libclntsh.$SHLIB_SUFFIX_NAME.9.0; then
***************
*** 119,124 ****
--- 121,129 ----
      10.2)
        PHP_ADD_LIBRARY(clntsh, 1, PDO_OCI_SHARED_LIBADD)
        ;;
+     11.1)
+       PHP_ADD_LIBRARY(clntsh, 1, PDO_OCI_SHARED_LIBADD)
+       ;;
      *)
        AC_MSG_ERROR(Unsupported Oracle version! $PDO_OCI_VERSION)
        ;;
#EOF


patch --dry-run -i config.m4.patch && patch -i config.m4.patch && phpize
ORACLE_HOME=/opt/oracle/instantclient ./configure --with-pdo-oci=instantclient,/opt/oracle/instantclient,11.1
make && make test && make install && mv modules/pdo_oci.so /usr/lib/php5/*+lfs/

cat - <<EOF > /etc/php5/apache2/conf.d/pdo_oci.ini
# configuration for php PDO_OCI module
extension=pdo_oci.so
EOF

cat - <<EOF > /etc/php5/apache2/conf.d/pdo_oci.ini
# configuration for php PDO_OCI module
extension=pdo_oci.so
EOF

```

Sanity check:
```

php --info | grep oci

```


I just did this all on a mostly fresh install of another system.
Guaranteed to work on 9.10 or your money back!

---

### Post by coolaj86 on 2009-07-08
It's also worth noting that if you are using Doctrine through Symfony or any other means that you will need to purge your recycle bin (or patch Doctrine) before running building your code from the live Schema.

```

SELECT * FROM USER_RECYCLEBIN;
select * from user_indexes;

```

```

PURGE RECYCLEBIN;

```

---

### Post by angiebb.dm on 2009-08-18
Hello coolaj86, I followed your instructions to install pdo_oci but I'm stuck in[FONT=monospace] 

ORACLE_HOME=/opt/oracle/instantclient ./configure --with-pdo-oci=instantclient,/opt/oracle/instantclient,10.1 

because thrown this error:

.
checking for PDO includes... checking for PDO includes... 
configure: error: Cannot find php_pdo_driver.h

this file is located in /usr/include/php5/ext/pdo/php_pdo_driver.h

how can I solve this problem?

thanks in advance
[/FONT]

---

### Post by coolaj86 on 2009-08-18
Ah, I made a typo. Try this:

```

cd /usr/include/
ln -s php5 php

```

---

### Post by angiebb.dm on 2009-08-19
:), I think I didn't follow all the instructions after all...#-othanks, this howto save me, jeje it's working wonderful now, thank you.

---

### Post by mcorbelle on 2011-09-13
The information was very helpful, but I have a problem is that I get this error when wanting to connect with test page Warning: oci_connect (): ORA-12543: TNS: destination host unreachable using TNSNAMES Connecting service name: Warning: oci_connect () : ORA-12154: TNS: could not resolve the connect identifier Specified
All environment variables are correct, and which can not be the problem. Could you please help me?
thank you very much

---

### Post by 0n_a_mission on 2011-11-23
Sorry to reply to such an old thread, but after 2 days of trying to get the PDO_OCI drivers to configure pdo_oci, I found this thread very useful to me. Plus, I have found that some changes since it's first posting and I wanted to capture that. I also have not quite gotten it working yet and would love for someone to let me know what I am doing wrong so I can get this running.

To start with, coolaj86's first post got me very close to done, but instead of the patch he recommends in the section on installing pdo_oci, I found that there is a new config.m4 in the php svn ([click here]("http://svn.php.net/viewvc/php/php-src/branches/PHP_5_3/ext/pdo_oci/config.m4?view=markup&pathrev=294487")) especially written for php5 and up to InstantClient 11.2.  So, when I replaced the config.m4 I was able to phpize, configure, make and make install it.  I moved pdo_oci.so to /usr/lib/php5/20090626+lfs and made the recommended edits to the php.ini files [actually to pdo_oci.ini in /etc/php5/conf.d which my php.ini references], and have restarted Apache.  My sanity check runs fine:
```
dev@dev-desktop:/tmp$ php --info | grep oci
Configure Command =>  './configure'  '--with-apxs2=/usr/bin/apxs2' '--with-mysql' '--with-pdo-mysql' '--with-pdo-oci=instantclient,/opt/oracle/instantclient/,11.2.0.2' '--enable-soap' '--with-zlib' '--with-gd' '--enable-gd-native-ttf' '--with-mcrypt' '--enable-zip' '--enable-mbstring' '--with-mysqli'
oci8
oci8.connection_class => no value => no value
oci8.default_prefetch => 100 => 100
oci8.events => Off => Off
oci8.max_persistent => -1 => -1
oci8.old_oci_close_semantics => Off => Off
oci8.persistent_timeout => -1 => -1
oci8.ping_interval => 60 => 60
oci8.privileged_connect => Off => Off
oci8.statement_cache_size => 20 => 20
PDO drivers => mysql, oci, sqlite, sqlite2

```

Another sanity check also verifies that php knows it should have a module called PDO_OCI as follows:
```
dev@dev-desktop:/tmp$ php -m
[PHP Modules]
ctype
date
dom
filter
gd
hash
iconv
json
libxml
mbstring
mcrypt
mysql
mysqli
oci8
pcre
PDO
pdo_mysql
PDO_OCI
pdo_sqlite
posix
Reflection
session
SimpleXML
soap
SPL
SQLite
standard
tokenizer
xml
xmlreader
xmlwriter
zip
zlib

[Zend Modules]


```

Yet, my phpinfo() call does not have a PDO_OCI section like I think that it should and my site gets the following error:
[HTML]CDbException

CDbConnection failed to open the DB connection: could not find driver[/HTML]

Thus, my php still doesn't have the drivers needed for pdo_oci to run properly.  

Any help on this would be greatly appreciated.

Thanks,
Tim 
- Ubuntu 10.04.3 LTS
- Oracle 9 & 10
- PHP 5.2.17
- InstantClient 11.2.0.2.0

---

### Post by 0n_a_mission on 2011-11-27
OK, I think I have a clue to what might be going on, but I have no idea how to fix it.  What I have found is that from a command line I get this:
```
dev@dev-desktop:~$ php -info |more
phpinfo()
PHP Version => 5.2.17

System => Linux dev-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686
Build Date => Sep 22 2011 16:26:24

```

But from a browser I get this:[INDENT] **PHP Version 5.3.2-1ubuntu4.10**
**System** Linux dev-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 
**Build Date** Oct 14 2011 23:57:47
[/INDENT]What this tells me is that I have two different PHP instances running and, so, when I try to add pdo-oci to my install by the command line it goes to the wrong instance.

Does this make sense?

If not, what does?

If so, how do I "uninstall" the older one and get only one version on my machine?

Please help.

Thanks,
Tim 
- Ubuntu 10.04.3 LTS
- Oracle 9 & 10
- PHP 5.2.17 **& 5.3.2**
- InstantClient 11.2.0.2.0

---

### Post by 0n_a_mission on 2011-11-28
So the question is:  "Does no one respond because this is really THAT hard or is it that no one is reading this thread because the title is too specific and no one is interested in such things?"

I am going to try to start a new thread and see if I can't get some response.  

Thanks,
Tim 
- Ubuntu 10.04.3 LTS
- Oracle 9 & 10
- PHP 5.2.17 **& **5.3.2
- InstantClient 11.2.0.2.0

---

### Post by 0n_a_mission on 2011-11-28
Fixed. 

I started over from scratch with a new Ubuntu install and the process described here worked without a hitch. Thank you coolaj86 for a great 'How To".

---

### Post by ionplay on 2011-12-16
works perfectly on 10.0.4

nice work on the script and overall HOWTO - Kudos and thank you - very helpful getting php running and connected to an Oracle Server that was not localhost.

vi basic_oci_connect.php

```
 
<?php

// Connects to the XE service (i.e. database) on the "localhost" machine
$conn = oci_connect('user', 'pass', '192.168.0.99/XE');
if (!$conn) {
    $e = oci_error();
    trigger_error(htmlentities($e['message'], ENT_QUOTES), E_USER_ERROR);
}

$stid = oci_parse($conn, 'SELECT * FROM space.existingtable');
oci_execute($stid);

echo "<table border='1'>\n";
while ($row = oci_fetch_array($stid, OCI_ASSOC+OCI_RETURN_NULLS)) {
    echo "<tr>\n";
    foreach ($row as $item) {
        echo "    <td>" . ($item !== null ? htmlentities($item, ENT_QUOTES) : "&nbsp;") . "</td>\n";
    }
    echo "</tr>\n";
}
echo "</table>\n";

?>


```

---

