---
title: "Howto: Install Oracle Instant Client and PHP OCI8 module"
date: 2005-11-19
forum: Tutorials
---

### Post by elmicha on 2005-11-19
If you want to connect to an Oracle database with PHP, you can use Oracle's Instant Client and the oci8 module from pear.

Download the Basic and the SDK packages from [http://www.oracle.com/technology/tech/oci/instantclient/instantclient.html](http://www.oracle.com/technology/tech/oci/instantclient/instantclient.html). At the time of this writing, the filenames are *instantclient-basic-linux32-10.2.0.1-20050713.zip* and *instantclient-sdk-linux32-10.2.0.1-20050713.zip*.

Unzip these files in a new directory, e.g. /opt/oracle/instantclient.

```
mkdir -p /opt/oracle/instantclient
cd /opt/oracle/instantclient
unzip instantclient-basic-linux32-10.2.0.1-20050713.zip
unzip instantclient-sdk-linux32-10.2.0.1-20050713.zip
echo /opt/oracle/instantclient >> /etc/ld.so.conf
ldconfig

```

The previous two lines are supposed to create symlinks named libclntsh.so and  libocci.so which we will need later. In my case these symlinks were not created by ldconfig, so I created them manually.

```

ln -s libclntsh.so.10.1 libclntsh.so
ln -s libocci.so.10.1 libocci.so

```

In the next step we will download the oci8 module with pear. Pear is in the php-pear package. 

```
apt-get install php-pear
```

"Normally" we should be able to just use *pear install oci8* now, but apparently pear is not able to figure out where the instantclient libraries are. So we will just download the oci8 module and build it on our own.

```

mkdir -p /usr/local/src
cd /usr/local/src
pear download oci8
tar xzf oci8-1.1.1.tgz
cd oci8-1.1.1
phpize
./configure --with-oci8=shared,instantclient,/opt/oracle/instantclient
make
make install

```
The oci8-1.1.1.tgz filename will of course change for newer releases.
To enable the oci8 module in the php.ini (/etc/php5/apache2/php.ini and /etc/php5/cli/php.ini), add a line
```
extension=oci8.so
``` (put this line after the examples starting with *;extension*).

Now stop and start Apache. You should see the oci8 module in the output of phpinfo().

---

### Post by mthaddon on 2006-03-24
I've followed the instructions, but get the following error when running the ./configure command. Do I need version 3.4 or something (I've seen as a problem elsewhere)?

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check


Thanks, Tom

---

### Post by mthaddon on 2006-03-27
Solved with:

sudo apt-get install build-essential

Thanks, Tom

---

### Post by bjverde on 2006-04-07
for **phpize** use:


sudo apt-get install php5-dev

---

### Post by masonite on 2006-07-19
An excellent howto!  Thanks - you've really saved me!

I tried with the basiclite version that oracle makes available and it didn't work very well (at all) - the issue was that it's missing the libociei.so library.

Be sure to use the full basic client.  Currently instantclient-basic-linux32-10.2.0.2-20060331.zip

I also had to set the environ a little as well:
export LD_LIBRARY_PATH=/opt/oracle/instantclient/

Good luck!

---

### Post by asg123 on 2006-07-20
At least with Ubuntu 6.06 and oci8-1.2.1 you don't need to compile oci8 extension manually. Just run:
```
pecl install oci8
```
and enter "instantclient,/opt/oracle/instantclient" when it'll prompt for the path to ORACLE_HOME dir

---

### Post by ehudokai on 2006-07-24
Is the module supposed to show up in phpinfo after its installed?

---

### Post by ehudokai on 2006-07-24
> **ehudokai said:**
> Is the module supposed to show up in phpinfo after its installed?
OK, in answer to my own question there are two extra things I had to do.

in /etc/php5/apache2/php.ini (since I'm using the php_mod) :
```
extension=oci8.so
```
has to be put in there...

For me also, I had to add www-data to the oinstall group to give it access to my oracle files...

Hope that helps someone

---

### Post by arunsub on 2006-07-25
How do I connect to Oracle? I installed everything as said above. I now want to connect to Oracle and see if it works.

ps: I have Oracle XE also installed, so I'm not sure if it will affect the Oracle instant client or it can co-exist with Oracle instant client.

**Edit**:
Sorry for the confusion. I didn't realize that Oracle instant client is to connect PHP to Oracle Databas. I have Oracle XE installed. Are there any environment variable that needs to be set to access the Oracle XE database I installed?

---

### Post by Alf Stockton on 2006-07-26
As mentioned at [http://forums.oracle.com/forums/thread.jspa?threadID=404923&tstart=0](http://forums.oracle.com/forums/thread.jspa?threadID=404923&tstart=0)
you set environment variables for Oracle 10g XE in Linux by :-
source /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh

this could also be done as
. /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh

but don't make the same mistake that I did by leaving out the dot space at the beginning of the above line.

My question is, does this overall solution work for getting OCI8 to access local Oracle databases? I thought instantclient was only for remote DataBases.

---

### Post by arunsub on 2006-07-26
> **Alf Stockton said:**
> As mentioned at [http://forums.oracle.com/forums/thread.jspa?threadID=404923&tstart=0](http://forums.oracle.com/forums/thread.jspa?threadID=404923&tstart=0)
you set environment variables for Oracle 10g XE in Linux by :-
source /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh

this could also be done as
. /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh

but don't make the same mistake that I did by leaving out the dot space at the beginning of the above line.

My question is, does this overall solution work for getting OCI8 to access local Oracle databases? I thought instantclient was only for remote DataBases.
Thanks. I'll try that tonight. Once I set the environment variables, will OCILogon("user","pwd","XE") work?

Thanks for the help.

---

### Post by arunsub on 2006-07-26
I ran the . /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh
 command in a terminal and it went fine (no errors). I then ran this small PHP script named hello.php:
<?php
$db=OCILogon("username", "pwd","XE");
	
?>
I got the following error when I tried [http://localhost/hello.php](http://localhost/hello.php) in a browser:
Warning: ocilogon() [function.ocilogon]: ORA-12154: TNS:could not resolve the connect identifier specified in /var/www/hello.php on line 2.
Any idea?

---

### Post by jaimeiniesta on 2006-08-07
Thanks, I just installed OCI on my Ubuntu Dapper. Now to see if it works... at least it appears when I do a phpinfo() !!! :) 

Just one thing: on the instructions at the beginning of this topic it says you have to unzip two zip files. It should also be noted that the contents of both zip files should be directly under /opt/oracle/instantclient... I lost some minutes wondering why it didn't work and the reason was that the "unzip" command creates folders called something like "instantclient-sdk-linux32-10.2.0.2-20060331.zip_FILES"... ](*,)

---

### Post by belgampaul on 2006-08-13
> **masonite said:**
> An excellent howto!  Thanks - you've really saved me!

I tried with the basiclite version that oracle makes available and it didn't work very well (at all) - the issue was that it's missing the libociei.so library.

Be sure to use the full basic client.  Currently instantclient-basic-linux32-10.2.0.2-20060331.zip

I also had to set the environ a little as well:
export LD_LIBRARY_PATH=/opt/oracle/instantclient/

Good luck!

i had to set up the LD_LIBRARY_PATH with a :

SetEnv LD_LIBRARY_PATH /opt/oracle/instantclient

in  apache.

export LD_LIBRARY_PATH=/opt/oracle/instantclient/ may still work but then you gotta be more precise for what user you do this.

more about this at [http://www.phpfreaks.com/forums/index.php?topic=95498.msg382340](http://www.phpfreaks.com/forums/index.php?topic=95498.msg382340)

---

### Post by underpope on 2006-09-14
I tried doing that, but Apache is disconnecting and throwing a segmentation fault.  How can I fix that?

---

### Post by stashj on 2006-11-02
Thank you! The best Howto I've user used!

I used the pecl oci install

A couple of things in case anyone else comes up against them;

When I unzipped instant client the root directory was /opt/oracle/instantclient/instantclient_10_2 so I had to use this as the root folder I gave to the pecl install

pecl gave me an error saying that the oci8 install was hitting its memory limit, to get round this edit the command line at the bottom of /usr/bin/pecl to include the statement -d memory_limit=20M

Worked fine for me after that.

---

### Post by roleta on 2007-03-27
Hell all,
I really enjoy distribution ubuntu 6.10 for it's simplicity so I want to share my few commands howto for setting up apache for connection to remote oracle database:
root@roleta:/home/rollyboy# uname -a
Linux roleta 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
root@roleta:/home/rollyboy# 

apt-get install oracle-xe-client         #ofcourse you need to set up your /etc/apt/sources.list
  it will install oracle client to /usr/lib/oracle/xe/app/oracle/product/10.2.0/client/   (oracle home directory)

apt-get install php-pear
apt-get install build-essential
In next step you will be asked for oracle home directory, put there the path mentioned above
pecl install oci8
echo "extension=oci8.so" >> /etc/php5/cli/php.ini
 echo "extension=oci8.so" >> /etc/php5/apache2/php.ini
/etc/init.d/apache2 restart


#######simple pease of php code for connection to remote databse
if(!($conn = oci_connect(USERNAME,PASS,SERVER_NAME.":".PORT_NUMBER."/".SEVICE_NAME)))
{
   DisplayErrMsg(sprintf("error connecting to host %s, by user %s",
                             SERVER_NAME, USERNAME)) ;
   exit() ;
}

---

### Post by docker on 2007-08-22
Thank you so much!

A little add-on:

The last parameter is the **SID**

```

oci_connect("user", "password", "10.0.0.x:1521/sid")

```
[Difference between service_name and database_name?]("http://searchoracle.techtarget.com/ateQuestionNResponse/0,289625,sid41_gci1029275_tax294550,00.html")

---

### Post by cRaZyFaCKa on 2007-09-20
Greetings everybody.

First of all let me congratulate you all for the maintenance of this extraordinary forum. You can see that by my low number of posts... I rarely need to ask something.

Now for the big question...
When I try to do "pecl install oci8", I get a "Oracle Instant Client SDK header files not found" error.

Could you please provide some info regarding this item?

Best regards,
CFK

---

### Post by cRaZyFaCKa on 2007-09-21
Problem solved!

There was a directory mismatch somewhere, making impossible to the script to find InstantClient libraries and Oracle SDK.

My final directory arrangement ended up like this:

**/opt/oracle/instantclient/instantclient** (before /opt/oracle/instantclient/instantclient_11_1)
**/opt/oracle/instantclient/sdk** (before /opt/oracle/instantclient/instantclient_11_1/sdk)

After this, I ran the command **pecl install oci8** and gave the following information:

instantclient,/opt/oracle/instantclient/instantclient

Then everything was working fine in PHP right after adding the extra line to load the OCI8 extension. :)

Best Regards,
CFK

---

### Post by msalahat on 2007-10-10
Hi , 
enter I didl this command "pecl install oci8"
I got this error ?
/usr/bin/ld: skipping incompatible /opt/oracle/instantclient//libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status
make: *** [oci8.la] Error 1
ERROR: `make' failed

Could you help me ?

---

### Post by msalahat on 2007-10-10
Hi , 
When I tried  this command "pecl install oci8"
I got this error ?
/usr/bin/ld: skipping incompatible /opt/oracle/instantclient//libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status
make: *** [oci8.la] Error 1
ERROR: `make' failed

Could you help me ?

---

### Post by AmanicA on 2007-10-31
this forum helped me a lot but it was a little incoherent and outdated, so here is the steps that worked for me (mostly copied from other posts):


* sudo apt-get install apache2 php5 php5-dev
* download oracle instant client from oracle and install.
* to get php and oci working: 
```
 su
 echo /opt/oracle/instantclient >> /etc/ld.so.conf
 ldconfig
```

The previous two lines are supposed to create symlinks named libclntsh.so and libocci.so which we will need later. In my case these symlinks were not created by ldconfig, so I created them manually.
```
 ln -s libclntsh.so.10.1 libclntsh.so
 ln -s libocci.so.10.1 libocci.so

 apt-get install php-pear

 pecl install oci8

```

* To enable the oci8 module in the php.ini (/etc/php5/apache2/php.ini and /etc/php5/cli/php.ini), add a line Code:
```
 extension=oci8.so 
```
(put this line after the examples starting with ;extension).

* Now stop and start Apache. You should see the oci8 module in the output of phpinfo().

---

### Post by chrisHHR on 2007-11-05
> **msalahat said:**
> Hi , 
enter I didl this command "pecl install oci8"
I got this error ?
/usr/bin/ld: skipping incompatible /opt/oracle/instantclient//libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status
make: *** [oci8.la] Error 1
ERROR: `make' failed

Could you help me ?

I have the same problem.  I'm pretty much flying blind on CLI, so any help would be appreciated greatly.

Obviously I need to find and load "make", but don't know where to look or what command to run.

UPDATE:  n/m, I ran apt-get build-essential..........resolved the issue.

---

### Post by backwardselvis on 2007-12-18
[COLOR="Red"]**///NOTES///**[/COLOR]

**HOWTO:** Install Apache2 + PHP5 + InstantClient + oci8 on Ubuntu 7.10

**Overall Objective:** Install PHP5, APACHE2, with Instant Client 11.1 and oci8 libraries in order to connect remotely with an Oracle DB.
[B]
Personal Objective:[/B] I use PHP to interface with several Oracle databases. My scripts will run and extract data for me and then perform a multitude of tasks using the data. 
 
**OS Version: **Ubuntu 7.10 i386 Desktop

**Target Audience:** Nerds who have a basic understanding of the command line, compiling, and PHP. If your skill exceeds this then you can still follow along, but you probably could skip some steps.

**SUPPORT: **I will support this document with updates should others post their findings. I will also do my best to answer questions DIRECTLY related to this doc

**Note#1: **After setting this process up, I reinstalled Ubuntu and went through the process again, step by step, in order to maintain accuracy.

**Note#2:** After logging into Ubuntu, I issue a sudo &#8211;i command in order to maintain my root id throughout the installation process.

**Note#3: **I originally worked off Elmicha's doc until I ran into issues. So I created this doc at length to give a little deeper insight.

**Note#4: **Original .txt is attached to this post should others want to work off of it. Please site myself and Elmicha please.

**[COLOR="Red"]///BEGIN SETUP///[/COLOR]**

Login to a Terminal and issue a sudo -i

```

test@ubuntu-desktop:~$ sudo -i

```

Install Apache2

```

root@ubuntu-desktop:~# apt-get install apache2

```

Install required PHP5 modules and libraries

```

root@ubuntu-desktop:~# apt-get install php5-common php5 php5-dev libapache2-mod-php5 php5-cli

```

Install the build-essential and php-pear packages

```

root@ubuntu-desktop:~# apt-get install build-essential php-pear

```

IMPORTANT! Install libaio1 library. This is what I was having serious issues with originally.

```

root@ubuntu-desktop:~# apt-get install libaio1

```

Download the new Instantclient and SDK zip files from Oracle.

[http://www.oracle.com/technology/tech/oci/instantclient/index.html](http://www.oracle.com/technology/tech/oci/instantclient/index.html)

In my case the files are called Basic.zip and Sdk.zip Initially these files will be saved in my home directory under the Documents folder.
```

/home/ubuntu/Documents/

```

create a directory to house the zip files once they are uncompressed

```

root@ubuntu-desktop:~# mkdir /opt/oracle

```

move the .zip files in the &#8220;Documents&#8221; directory to the /opt/oracle directory

```

root@ubuntu-desktop:~# mv /home/ubuntu/Documents/*.zip /opt/oracle

```

Change to the /opt/oracle directory

```

root@ubuntu-desktop:~# cd /opt/oracle

```

Unzip the files

```

root@ubuntu-desktop:/opt/oracle# unzip \*.zip

```

rename instantclient directory 
```

root@ubuntu-desktop:/opt/oracle# mv instantclient_11_1 instantclient

```

Change directory to instantclient, list the files
```

root@ubuntu-desktop:/opt/oracle# cd instantclient

```

Create symbolic links
```

root@ubuntu-desktop:/opt/oracle# ln &#8211;s libclntsh.so.11.1 libclntsh.so
root@ubuntu-desktop:/opt/oracle# ln &#8211;s libocci.so.11.1 libocci.so

```

Create a source directory under /opt/oracle . This is where we will house the oci8 libraries.
```

root@ubuntu-desktop:/opt/oracle# mkdir /opt/oracle/src

```

Change the directory to /opt/oracle/src and download the oci8 tar using pecl
```

root@ubuntu-desktop:/opt/oracle# cd /opt/oracle/src

```
```

root@ubuntu-desktop:/opt/oracle/src# pecl download oci8

```

Untar the oci8 libraries
```

root@ubuntu-desktop:/opt/oracle/src# tar xvf oci8-1.2.4.tgz

```

Change to the newly created oci8-1.2.4 directory and issue the following commands
```

root@ubuntu-desktop:/opt/oracle/src# cd oci8-1.2.4

```
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# phpize

```

Set the ORACLE_HOME  environment variable
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# export ORACLE_HOME=/opt/oracle/instantclient

```
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# echo $ORACLE_HOME
/opt/oracle/instantclient

```

Configure oci8 to install with the necessary parameters
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# ./configure --with-oci8=share,instantclient,/opt/oracle/instantclient

```

run make to compile
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# make

```

install oci8
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# make install

```

insert the extension=oci8.so into the php.ini and cli.ini files
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# echo extension=oci8.so >> /etc/php5/apache2/php.ini
root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# echo extension=oci8.so >> /etc/php5/cli/php.ini

```

restart apache
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# /etc/init.d/apache2 restart 

```

create a phpinfo.php file in /var/www
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# vi /var/www/phpinfo.php

```

Now go to your browser and run the phpinfo file and look for the oci8 module

```

http://localhost/phpinfo.php

```

Create a empty script to test your Oracle Connection
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# vi /home/ubuntu/oratest.php

```

Copy and Paste this PHP code into your script and change the variables accordingly
[PHP]
<?php

//oracle connection variables
$ora_user = 	'YOUR_USERNAME';	//username
$ora_pass =	'YOUR_PASS';			//user password
$ora_host =	'SERVER_IP_OF_ORACLE"';		//host name or server ip address
$ora_db   = 	'YOUR_DATABASE';	//database name

// place variable into oci_connect function, then place funtion in variable
$ora_conn = oci_connect($ora_user,$ora_pass,'//'.$ora_host.'/'.$ora_db);

// error handling
if (!ora_conn){							// if variable $ora_conn fails to connect
// do the following if it fails
$ora_conn_erno = oci_error(); 			// insert oci_error() function into variable
echo ($ora_conn_erno['message']."\n"); 	// print the $ora_conn_erno variable/oci_error() function selecting only the message (human readable)
oci_close($ora_conn); 					// close the connection just in case php doesn't close it
} else {
// if it doesn't fail it will proceed with the rest of the script
echo "Connection Succesful\n"; 	//echo message if connection does not error
oci_close($ora_conn); 			// close the connection
}

?>
[/PHP]                                                                                                                                   
                                                                                                                          
Test the connection
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# php /home/ubuntu/oratest.php
Connection Succesful
root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4#

```

[B]*[COLOR="SeaGreen"]Merry[/COLOR] [COLOR="DarkRed"]Christmas[/COLOR]
elvis[/B]

---

### Post by cRaZyFaCKa on 2007-12-18
Absolutely tremendous!
Thank you! :D

---

### Post by barranco on 2007-12-18
you made my Christmas, thank you

---

### Post by VuDu on 2007-12-19
Thanks Elvis!! :)
Finally got it to work! My problem was the missing libaio1 package :(
But now I'm getting this warning:
```
Warning: oci_connect() [function.oci-connect]: ORA-12541: TNS:no listener in /var/www/lixo.php on line 10
```

Any help?

---

### Post by backwardselvis on 2007-12-19
Glad everyone likes it. It took me almost a week to figure out what the hell was going on.

Vudu, is this a fresh install following the steps? 

Can you query the DB and extract data?

You could suppress the error with the @ symbol but that really would be just to patch it and not a real fix.

---

### Post by VuDu on 2007-12-19
Now i get a
> 
Warning: oci_connect() [function.oci-connect]: ORA-03134: Connections to this server version are no longer supported. in /var/www/lixo.php on line 17

So, it seems to be a server-side issue... :(

and...
> 
Connection Succesful 
Warning: oci_parse() expects parameter 1 to be resource, boolean given in /var/www/lixo.php on line 39

Warning: oci_execute() expects parameter 1 to be resource, null given in /var/www/lixo.php on line 40

Warning: oci_fetch_row() expects parameter 1 to be resource, null given in /var/www/lixo.php on line 42

Warning: oci_close() expects parameter 1 to be resource, boolean given in /var/www/lixo.php on line 52

That's weird :(

---

### Post by backwardselvis on 2007-12-19
What does your script look like minus user/pass/host info?

Also are you able to ping the database server?

---

### Post by VuDu on 2007-12-20
I can acess the server with AquaDataStudio, so connection is not a problem. :(

Btw, do you have any idea how to get odbc working?

---

### Post by backwardselvis on 2007-12-20
Nope, no ODBC experience here.

---

### Post by VuDu on 2007-12-21
How about you taking your experience to the ubuntu help?
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
 ;)
This seems to be way incomplete.
[https://help.ubuntu.com/community/PHPOracle](https://help.ubuntu.com/community/PHPOracle) :)

---

### Post by yacho98 on 2008-04-18
I only can connect to the oracle database using this code. The different from the previous sample is I locate the tnsname like at the host. Anyone can explain why I only can connect only using below sample only and not like as previous sample.

The error that i got from the previous sample is
Warning: oci_connect() [function.oci-connect]: ORA-12514: TNS:listener does not currently know of service requested in connect descriptor in /home/myservice/pick/oratest1.php on line 10
Connection Succesful
Warning: oci_close() expects parameter 1 to be resource, boolean given in /home/myservice/pick/oratest1.php on line 21

thanks

<?php

//oracle connection variables
$ora_user =     'oracle_user';      //username
$ora_pass =     'oracle_pwd';                      //user password
//$ora_host =   '10.x.x.1';           //host name or server ip address
$ora_db   =     'orcl'; //database name
$ora_host='(DESCRIPTION =
           (ADDRESS =
        (PROTOCOL = TCP)
        (HOST = 10.x.x.1)
        (PORT = 1521)
     )
         (CONNECT_DATA =(SID = orcl))
     )';  //tnsnames like

// place variable into oci_connect function, then place funtion in variable
//$ora_conn = oci_connect($ora_user,$ora_pass,'//'.$ora_host.'/'.$ora_db); //previous connection sample
$ora_conn = oci_connect($ora_user,$ora_pass,$ora_host); //new connection sample
// error handling
if (!ora_conn){                                                 // if variable $ora_conn fails to connect
// do the following if it fails
$ora_conn_erno = oci_error();                   // insert oci_error() function into variable
echo ($ora_conn_erno['message']."\n");  // print the $ora_conn_erno variable/oci_error() function selecting only the message (human readable)
oci_close($ora_conn);                                   // close the connection just in case php doesn't close it
} else {
// if it doesn't fail it will proceed with the rest of the script
echo "Connection Succesful\n";  //echo message if connection does not error
oci_close($ora_conn);                   // close the connection
}

?>

---

### Post by Jeroen Marsman on 2008-05-01
Thank you very much, this article helped me out!

---

### Post by Bl4deRunner on 2008-06-10
Thanks! libaio1 was the missing link to make it work!!!
How did you find out?

On my Hardy it was already installed, but was replaced after I manually apt-get(apt-got?) that file.

---

### Post by daniloviz on 2008-07-14
Hello, 
I have just written 2 bash scripts for the installation and configuration of Apache2, PHP5, Oracle Client v10.2 and OCI8. The scripts were tested on Linux Ubuntu 8.04.1 Server and it seems they also work on some previous versions of Linux Ubuntu and Kubuntu Server and Desktop Editions. 

The first script OracleViaPHP.sh downloads, installs and configures all the needed packages. It can be found here [http://www.danilovizzarro.it/script/OracleViaPHP.sh](http://www.danilovizzarro.it/script/OracleViaPHP.sh) 

The second script TNSconnect.sh updates the tnsnames.ora file and creates a PHP test page to connect the Oracle DB. It can be found here [http://www.danilovizzarro.it/script/TNSconnect.sh](http://www.danilovizzarro.it/script/TNSconnect.sh) 

In order to have them working it's required to download the oracle client basic lite and the SDK in the /root directory. 

A step-by-step tutorial + **video demo** can be found here [http://www.danilovizzarro.it/?p=7](http://www.danilovizzarro.it/?p=7) 
I'm curious to know what you think of it.

BR 
DV

---

### Post by bvidinli on 2008-07-24
the script you wrote was very useful for me. 
it did not work right away but i fixed it..

when i run unmodified, 
it raise an error:
checking Oracle Instant Client SDK header directory... configure: error: Oracle Instant Client SDK header files not found


i downloaded sdk files from oracle, and put on my ehcp server,

i added lines:
wget [http://www.ehcp.net/other/sdk.zip](http://www.ehcp.net/other/sdk.zip)  # get oracle sdk from ehcp.net
unzip sdk.zip 
cp -Rvf sdk /opt/oracle/instantclient/


just after phpize,


i renamed instantclient_10_2 to instantclient

then everything worked fine.
now i can use oci_connect on my php programs.
previously i got:
Fatal error: Call to undefined function oci_connect() in



Now everything works fine, 
your script with modifications i made is at:
[http://www.ehcp.net/other/OracleViaPHP.sh](http://www.ehcp.net/other/OracleViaPHP.sh)

Thanks !

---

### Post by daniloviz on 2008-07-25
Hi,
I guess you got that problem just caused for some reason the sdk directory was not unzipped inside the instantclient_10_2 directory. But cool if you solved it but could you tell which version of the operating system you are using?

Thank you
BR
DV

---

### Post by daniloviz on 2008-07-25
I was reading better your post.
I guess is not allowed to publish the oracle sdk or client on other servers then oracle cause of copyrights and authorization reasons. If you see, when you go downloading the sdk and the oracle client it's required to accept an agreement before to be able to start the download.
I know everything would have been easier using wget but that's why I haven't done it.

Cya
DV

---

### Post by bvidinli on 2008-07-25
i use ubuntu 8.04,
now i can connect to oracle from php...

see you

---

### Post by bvidinli on 2008-07-25
i use ubuntu since 2.5 years, on my home, workoffice, personal and work computers, laptops... ubuntu handles %99 of my needs.. ;)
i have no win installed on my computers since 2.5 years...since 2006

---

### Post by daniloviz on 2008-07-25
> **bvidinli said:**
> i use ubuntu 8.04,
now i can connect to oracle from php...


Sounds cool ;D
I suppose you are using the Desktop version. Isn't it?

---

### Post by bvidinli on 2008-07-25
yes,
i use desktop version all the time, for desktop needs and server needs.
i even install ubuntu desktop to my servers, with ehcp.
Because ehcp (Easy Hosting Control Panel) installs everything server related from scratch.. so, desktop version satisfies all my needs... 

i think Ubuntu great, you say aptitude install "anything" it retrieves from net and installs for you, including many games.. 

as a person in past "tried to install a.rpm, a required  b, tried to install b.rpm, b requires c, tried to install c, c required d, and so on, 6 levels of requires... "
Ubuntu / debian apt-get install mechanism is what i look.. i look for many things still... Ubuntu guys has many thing to do yet.. 

see you.

---

### Post by gerhard2001 on 2008-07-28
Hi daniloviz and all Ubuntu friends!

First I tried to install Apache, OracleXE, PHP5 and oci8 and, exept oci8, everything functioned well.

But I have the same problem as 'bvidinli':

checking Oracle Instant Client SDK header directory... configure: error: Oracle Instant Client SDK header files not found.

So I tried do do it with your script and it was the same.
And it was the same with the extended script from 'bvidinli'

I use Ubuntu 8.04 Desktop.

I post here my 'Shell' report of the installation:

**************************************************************************

root@josef-ubuntu:/home/gerhard/Desktop# . ./OracleViaPHP.sh 

Oracle Client Installation...
Script tested an Virtual Machine Ubuntu 8.04.1 Server Edition x86 running on a Mac OS X Leopard 10.5.3.
---
Starting Oracle Client Installation...
---
Ign cdrom://Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/main Translation-en_US
Ign cdrom://Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/restricted Translation-en_US
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg                                 
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en_US            
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en_US        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release                           
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy Release
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates Release                  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/main Packages                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/main Sources  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [45.0kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [10.1kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [26.2kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [3708B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3874B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Fetched 155kB in 5s (30.0kB/s)                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  xulrunner-1.9 xulrunner-1.9-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7788kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main xulrunner-1.9-gnome-support 1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3 [38.5kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main xulrunner-1.9 1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3 [7750kB]
Fetched 7788kB in 1min19s (98.0kB/s)                                           
(Reading database ... 125914 files and directories currently installed.)
Preparing to replace xulrunner-1.9-gnome-support 1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2 (using .../xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb) ...
Unpacking replacement xulrunner-1.9-gnome-support ...
Preparing to replace xulrunner-1.9 1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2 (using .../xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb) ...
Unpacking replacement xulrunner-1.9 ...
Setting up xulrunner-1.9 (1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3) ...

Setting up xulrunner-1.9-gnome-support (1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3) ...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ssh is already the newest version.
unzip is already the newest version.
apache2 is already the newest version.
php5 is already the newest version.
php5-dev is already the newest version.
php-pear is already the newest version.
build-essential is already the newest version.
libaio1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cp: cannot stat `/root/*.zip': No such file or directory
unzip:  cannot find or open *.zip, *.zip.zip or *.zip.ZIP.

No zipfiles found.
bash: cd: /opt/oracle/instantclient_10_2: No such file or directory
ln: creating symbolic link `libclntsh.so': File exists
ln: creating symbolic link `libocci.so': File exists
downloading oci8-1.3.4.tgz ...
Starting to download oci8-1.3.4.tgz (134,240 bytes)
.................done: 134,240 bytes
File /usr/local/src/oci8-1.3.4.tgz downloaded
tar: oci8-1.3.4: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: oci8-1.3.4.tgz: Not found in archive
tar: Error exit delayed from previous errors
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for Oracle (OCI8) support... yes, shared
checking PHP version... 5.2.4, ok
checking for long int... yes
checking size of long int... 4
checking Oracle Instant Client directory... /opt/oracle/instantclient_10_2
checking Oracle Instant Client SDK header directory... configure: error: Oracle Instant Client SDK header files not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
bash: /etc/init.d/apache2: Permission denied

You can now try to connect the page [http://your_ip_address/info.php](http://your_ip_address/info.php)
If everything went fine you should see the module oci8 in the list
root@josef-ubuntu:/etc/init.d# 

***********************************************************************

Has anybody any idea how to fix this problem?

Thanks a lot and greetings from Mexico

---

### Post by daniloviz on 2008-07-29
> **gerhard2001 said:**
> Hi daniloviz and all Ubuntu friends!
cp: cannot stat `/root/*.zip': No such file or directory
unzip:  cannot find or open *.zip, *.zip.zip or *.zip.ZIP.

No zipfiles found.
bash: cd: /opt/oracle/instantclient_10_2: No such file or directory


Hi
which version of Ubuntu are u using?
Did you move all the files in the directory /root before to run the script?

Ciao
DV

---

### Post by gerhard2001 on 2008-07-30
Hi daniloviz!

My system version is: Ubuntu 8.04 (hardy) 
My Kernel: 2.6.24-16-generic

Which files should I move in the directory /root?

Many thanks for your help!

It's really a joyride to work with free software, so you can expect help from every side of the world!

Without any religion conflicts and without any racism!

Gerhard

---

### Post by daniloviz on 2008-07-31
> **daniloviz said:**
> 
A step-by-step tutorial + **video demo** can be found here [http://www.danilovizzarro.it/?p=7](http://www.danilovizzarro.it/?p=7) 


Here you should find all the info you need.
DV

---

### Post by gerhard2001 on 2008-08-04
Hi daniloviz!

I did it like you have shown on your Website!

But it does not function.

Here is a partly report of my shell.

*************************************************************************

Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ssh is already the newest version.
unzip is already the newest version.
apache2 is already the newest version.
php5 is already the newest version.
php5-dev is already the newest version.
php-pear is already the newest version.
build-essential is already the newest version.
libaio1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Archive:  oracle-instantclient-devel-10.2.0.4-1.i386.zip
replace instantclient_10_2/sdk/include/occi.h? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: instantclient_10_2/sdk/include/occi.h  
replace instantclient_10_2/sdk/include/occiCommon.h? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: instantclient_10_2/sdk/include/occiCommon.h  
  inflating: instantclient_10_2/sdk/include/occiControl.h  
  inflating: instantclient_10_2/sdk/include/occiData.h  
  inflating: instantclient_10_2/sdk/include/occiObjects.h  
  inflating: instantclient_10_2/sdk/include/occiAQ.h  
  inflating: instantclient_10_2/sdk/include/oci.h  
  inflating: instantclient_10_2/sdk/include/oci1.h  
  inflating: instantclient_10_2/sdk/include/oci8dp.h  
  inflating: instantclient_10_2/sdk/include/ociap.h  
  inflating: instantclient_10_2/sdk/include/ociapr.h  
  inflating: instantclient_10_2/sdk/include/ocidef.h  
  inflating: instantclient_10_2/sdk/include/ocidem.h  
  inflating: instantclient_10_2/sdk/include/ocidfn.h  
  inflating: instantclient_10_2/sdk/include/ociextp.h  
  inflating: instantclient_10_2/sdk/include/ocikpr.h  
  inflating: instantclient_10_2/sdk/include/ocixmldb.h  
  inflating: instantclient_10_2/sdk/include/odci.h  
  inflating: instantclient_10_2/sdk/include/oratypes.h  
  inflating: instantclient_10_2/sdk/include/ori.h  
  inflating: instantclient_10_2/sdk/include/orid.h  
  inflating: instantclient_10_2/sdk/include/orl.h  
  inflating: instantclient_10_2/sdk/include/oro.h  
  inflating: instantclient_10_2/sdk/include/ort.h  
  inflating: instantclient_10_2/sdk/include/xa.h  
  inflating: instantclient_10_2/sdk/include/nzt.h  
  inflating: instantclient_10_2/sdk/include/nzerror.h  
  inflating: instantclient_10_2/sdk/demo/demo.mk  
  inflating: instantclient_10_2/sdk/demo/cdemo81.c  
  inflating: instantclient_10_2/sdk/demo/occidemo.sql  
  inflating: instantclient_10_2/sdk/demo/occidemod.sql  
  inflating: instantclient_10_2/sdk/demo/occidml.cpp  
  inflating: instantclient_10_2/sdk/demo/occiobj.cpp  
  inflating: instantclient_10_2/sdk/demo/occiobj.typ  
  inflating: instantclient_10_2/sdk/SDK_README  
 extracting: instantclient_10_2/sdk/ottclasses.zip  
  inflating: instantclient_10_2/sdk/ott  

Archive:  basiclite.zip
  inflating: instantclient_11_1/BASIC_LITE_README  
  inflating: instantclient_11_1/adrci  
  inflating: instantclient_11_1/genezi  
  inflating: instantclient_11_1/libclntsh.so.11.1  
  inflating: instantclient_11_1/libnnz11.so  
  inflating: instantclient_11_1/libocci.so.11.1  
  inflating: instantclient_11_1/libociicus.so  
  inflating: instantclient_11_1/libocijdbc11.so  
  inflating: instantclient_11_1/ojdbc5.jar  
  inflating: instantclient_11_1/ojdbc6.jar  

2 archives were successfully processed.
ln: creating symbolic link `libclntsh.so': File exists
ln: creating symbolic link `libocci.so': File exists
downloading oci8-1.3.4.tgz ...
Starting to download oci8-1.3.4.tgz (134,240 bytes)
.................done: 134,240 bytes
File /usr/local/src/oci8-1.3.4.tgz downloaded
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for Oracle (OCI8) support... yes, shared
checking PHP version... 5.2.4, ok
checking for long int... yes
checking size of long int... 4
checking Oracle Instant Client directory... /opt/oracle/instantclient_10_2
checking Oracle Instant Client SDK header directory... /opt/oracle/instantclient_10_2/sdk/include
checking Oracle Instant Client version... configure: error: Oracle Instant Client libraries not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
bash: /etc/init.d/apache2: Permission denied

You can now try to connect the page [http://your_ip_address/info.php](http://your_ip_address/info.php)
If everything went fine you should see the module oci8 in the list
root@josef-ubuntu:/etc/init.d# 




*************************************************************************

I installed Ubuntu Desktop Version and added the 'Server Programs' from the Ubuntu Server CD just to get a GUI on my Computer.

What can I do?

Thanks for your help

Gerhard

---

### Post by daniloviz on 2008-08-05
> **gerhard2001 said:**
> 
bash: /etc/init.d/apache2: Permission denied

It's a bit difficult to understand what went wrong as I didn't test on Ubuntu Desktop so I don't know if something is managed in a different way.

A quick solution comes up in my mind. try to run as root
# /etc/init.d/apache2 restart
or just reboot your machine.

if it doesnt work then try
# chmod 755 /etc/init.d/apache
# /etc/init.d/apache2 restart

BR
DV

---

### Post by bvidinli on 2008-08-05
> **daniloviz said:**
> It's a bit difficult to understand what went wrong as I didn't test on Ubuntu Desktop so I don't know if something is managed in a different way.

A quick solution comes up in my mind. try to run as root
# /etc/init.d/apache2 restart
or just reboot your machine.

if it doesnt work then try
# chmod 755 /etc/init.d/apache
# /etc/init.d/apache2 restart

BR
DV
become root,
then,

chmod a+x /etc/init.d/apache2 
/etc/init.d/apache2 restart

---

### Post by gerhard2001 on 2008-08-06
Hi

First off all: 'Thanks for your help!'

I think, my basic problem is this:

********************************************************************
checking Oracle Instant Client version... configure: error: Oracle Instant Client libraries not found
********************************************************************

Are the following messages a consequence of that?

*********************************************************************
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
bash: /etc/init.d/apache2: Permission denied
*********************************************************************

For I need oci8, and in case I can not fix this problem, what do you think about using 'ZendCore'?

Have you any experience with that?

Thanks a lot for your help!

A German, who lives in Mexico!

---

### Post by saeid on 2008-08-09
Very very thanks. :)

---

### Post by Youresorock on 2008-11-11
There are basically three install methods listed in this thread.  None of them have worked for me.  Why can't we just get oracle in a .deb like everything else?

I'm trying the last method posted.  I'm in the oci8-1.3.4 folder trying to run make.

I get "/usr/bin/ld: cannot find -lclntsh"

Why can't the HR people just use MySQL.......

```
jduffy@dubuntu:/opt/oracle/src/oci8-1.3.4$ sudo make
/bin/bash /opt/oracle/src/oci8-1.3.4/libtool --mode=link gcc -DPHP_ATOM_INC -I/opt/oracle/src/oci8-1.3.4/include -I/opt/oracle/src/oci8-1.3.4/main -I/opt/oracle/src/oci8-1.3.4 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -I/opt/oracle  -DHAVE_CONFIG_H  -g -O2   -o oci8.la -export-dynamic -avoid-version -prefer-pic -module -rpath /opt/oracle/src/oci8-1.3.4/modules  oci8.lo oci8_lob.lo oci8_statement.lo oci8_collection.lo oci8_interface.lo -Wl,-rpath,/opt/oracle -L/opt/oracle -lclntsh
gcc -shared  .libs/oci8.o .libs/oci8_lob.o .libs/oci8_statement.o .libs/oci8_collection.o .libs/oci8_interface.o  -L/opt/oracle -lclntsh  -Wl,-rpath -Wl,/opt/oracle -Wl,-soname -Wl,oci8.so -o .libs/oci8.so
/usr/bin/ld: skipping incompatible /opt/oracle/libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status
make: *** [oci8.la] Error 1

```

---

### Post by Youresorock on 2008-11-12
A lot of google searching has led me to believe my problem is that I'm running ubuntu64.  I did download the 64bit version of the oracle client, both the AMD64 and the x86_64 versions, but it doesn't work.  One forum said, "Why don't you just install Suse32."

I've gone thru this forum three times looking for anything I missed, but I can't find anything.

There has to be an easier way to do this.  I may have to install OpenSUSE32 in a VM.

---

### Post by Youresorock on 2008-11-19
Tried Fresh 8.04 x32 install, as previous posts seem to imply works.. Stuck here:

In the oci8-1.2.4 folder (I'm trying the version listed as working, newer 1.3 does the same thing)

/opt/instantclient/src/oci8-1.2.4# ./configure --with-oci8=share,instantclient,/opt/oracle/instantclient


I get: 
checking Oracle Instant Client SDK header directory... configure: error: Oracle Instant Client SDK header files not found

I copied the SDK files into literally every folder in the /opt/oracle tree.

$ORACLE_HOME is set properly, don't know what to do.

I'm srsly desperate.

---

### Post by Youresorock on 2008-12-18
SUCCESS:

I've lost some hair and a year from my life, but I've got it installed and working.

I believe the 64bit version is broken.  Also the guides on this forum didn't work for me.  I found another guide:

[http://techxplorer.com/2008/09/22/installing-the-oci8-library-for-php-5-on-ubuntu-804-810/](http://techxplorer.com/2008/09/22/installing-the-oci8-library-for-php-5-on-ubuntu-804-810/)


I started with a fresh 8.10 x32 install. I did all updates.  I installed NOTHING prior to starting the guide.  This includes apache.  I followed the guide to the letter, and had no errors (except the broken pecl install explained in the guide).  AFTER the install:

sudo apt-get install apache2
sudo apt-get install libapache2-mod-php5 php5-cli php5-common

Some of which was already installed in the guide.  Can't hurt.

you NEED to restart apache, even tho you just installed it to get php working. 

sudo /etc/init.d/apache2 restart


After you set your index.php in /var/www/    remember that if you get "You have chosen... PHTML" you need to clear your firefox cache and restart it.


:guitar:

---

### Post by prazetyo on 2009-02-05
I already success install oci on my ubuntu. But I another problem. I still can't connect to my oracle. This php script still doesn't work. Even my username and password not corrent, the connection still says successfull.

Is there any example how to try the connection? 

<?php

//oracle connection variables
$ora_user = 	'YOUR_USERNAME';	//username
$ora_pass =	'YOUR_PASS';			//user password
$ora_host =	'SERVER_IP_OF_ORACLE"';		//host name or server ip address
$ora_db   = 	'YOUR_DATABASE';	//database name

// place variable into oci_connect function, then place funtion in variable
$ora_conn = oci_connect($ora_user,$ora_pass,'//'.$ora_host.'/'.$ora_db);

// error handling
	if (!ora_conn){							// if variable $ora_conn fails to connect
		// do the following if it fails
		$ora_conn_erno = oci_error(); 			// insert oci_error() function into variable
		echo ($ora_conn_erno['message']."\n"); 	// print the $ora_conn_erno variable/oci_error() function selecting only the message (human readable)
		oci_close($ora_conn); 					// close the connection just in case php doesn't close it
	} else {
		// if it doesn't fail it will proceed with the rest of the script
		echo "Connection Succesful\n"; 	//echo message if connection does not error
		oci_close($ora_conn); 			// close the connection
	}

?>

---

### Post by JBringolf on 2009-05-09
Excellent information in this thread - but can anyone explain the difference using InstantClient (IC) and the full Oracle-xe. Working on an AMD64 machine, installed Oracle-xe using force-arch... method and Oracle-xe works fantastic. Using directions here also installed IC and it is showing with phpinfo. But now cannot connect to Oracle-xe. Appears to break the listener process somewhere.

Any help appreciated.

---

### Post by cesarianf on 2010-02-01
Thanks for the guide. Just what I need. I have been trying to do this with no luck, gonna try now.

---

### Post by VirtualEdgar on 2010-06-10
after i execute "make"...

/usr/bin/ld: skipping incompatible /opt/oracle/instantclient/libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status
make: *** [oci8.la] Error 1


Can somebody help me please?

---

### Post by guimau67 on 2010-08-17
> **VirtualEdgar said:**
> after i execute "make"...

/usr/bin/ld: skipping incompatible /opt/oracle/instantclient/libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status
make: *** [oci8.la] Error 1


Can somebody help me please?


Same problem :icon_frown: Ubuntu 10.04 32b - tried to find solution - nothing!

---

### Post by guimau67 on 2010-08-17
> **guimau67 said:**
> Same problem :icon_frown: Ubuntu 10.04 32b - tried to find solution - nothing!


Ok, I had installed instant client version 64 bit ](*,)

Reinstalled correct version 32bit, everything works!

---

### Post by ashickur.noor on 2011-01-26
> **guimau67 said:**
> Ok, I had installed instant client version 64 bit ](*,)

Reinstalled correct version 32bit, everything works!

Hello There 
Here it is written 
```
ln –s libclntsh.so.11.1 libclntsh.so
ln –s libocci.so.11.1 libocci.so 
```I think it will be like 
```
ln -s libclntsh.so.11.1 libclntsh.so
ln -s libocci.so.11.1 libocci.so 
```I am getting this while configure oci8 ```
checking Oracle Instant Client version... configure: error: Link from /opt/oracle/instantclient/libclntsh.so to libclntsh.so.10.1 not found
``` error.
Please tell me how you manage to work it in Ubuntu 64 Bit. I can not use 32 Bit for  sound card driver problem. It is argent.
Thank you.

---

### Post by swapii on 2011-10-07
hey the zip files you told are not working.....!! :( :confused:

---

