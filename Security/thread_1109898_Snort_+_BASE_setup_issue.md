---
title: "Snort + BASE setup issue"
date: 2009-03-29
forum: Security
---

### Post by Dr Small on 2009-03-29
Instead of posting on Bodhi.Zazen's thread and cluttering things with my issue, I thought it would be best if I started my own thread for my specific issue.

I've been following Bodhi.Zazen's Intrusion Detection tutorial for install and setting up Snort + BASE. I've got snort installed and running, but I can't get BASE to install. I'm on this post, by the way:
[http://ubuntuforums.org/showpost.php?p=5786356&postcount=4](http://ubuntuforums.org/showpost.php?p=5786356&postcount=4)

So, I'm on Step 1 of 5:
> Enter the path to ADODB.
This is /usr/share/php/adodb.

Sometimes when setting up base , after this first step I get a white page, just repeat step 1

My problem is, I only ever get a blank white page. I've tried multiple numerous times, and it will not go past it. Also, for the record, the directory "/usr/share/php/adodb" does not exist, and after just having ran "updatedb", I can't find it anywhere on the system.

As far as following the guide, I install snort-mysql from the repositories (I'm on Debian Stable) and downloaded BASE for sourceforge with wget as the tutorial has shown.

I'm sorta stuck at this point, and can't figure out how to get past it. Any suggestions?

Dr Small

---

### Post by bodhi.zazen on 2009-03-29
It appears you need to install [libphp-adobd]("http://packages.debian.org/lenny/libphp-adodb")

Or you can download it from the home page : [http://adodb.sourceforge.net/](http://adodb.sourceforge.net/)

[http://www.debian-administration.org/articles/357#install_adodb](http://www.debian-administration.org/articles/357#install_adodb)

---

### Post by Dr Small on 2009-03-29
> **bodhi.zazen said:**
> It appears you need to install [libphp-adobd]("http://packages.debian.org/lenny/libphp-adodb")


lol, I tried that, and it said: `E: Couldn't find package libphp-adobd`, so I changed that around to libphp-adodb :)

Anyhow, I installed that, got BASE setup sucessfully (I can login, and see the index on it). So, perhaps one last question if I don't sound too stupid; How do I test to make sure it is working? I totally have NO data in it anywhere. Everything is zeros. (Maybe that's a good thing? lol).

---

### Post by bodhi.zazen on 2009-03-29
Hit it with something, a port scanner or some such ;)

---

### Post by Dr Small on 2009-03-29
> **bodhi.zazen said:**
> Hit it with something, a port scanner or some such ;)
Thanks Bodhi, you're a champ :)
I'm sorry for not replying sooner; I've really *really* trying to get Snort to work (which I then found out it wasn't working, by checking the init.d status). I spent soo much time trying to debug it and get it to make the MySQL connection, and it just wouldn't.

I almost gave up on it, and then just decided to actually *follow* your tutorial this time around, and not take any shortcuts (installing from the repositories) this time. I had to do a little bit of upgrading packages to get build-essential and the rest of the dev packages to get snort to compile, but I think it will be worth it :)

In the end, it was really simple to configure and get setup by following your guide. I was shooting myself in the foot to keep from going to the battlefield before, but now found out that the battlefield wasn't all that bad :)

SO, after all of that, I now try your suggestion to portscan the server, and wa-lah! BASE alerts me of a portscan attack. Thanks bodhi, your tutorial and your wisdom has helped me through today :)

Dr Small

---

### Post by bodhi.zazen on 2009-03-29
You are most welcome Dr Small. I am glad you  got it up and working.

And you are too kind :twisted:

I had the same experience with snort and the same impression. I was avoiding installing from source ...

But once I did it seemed fairly straight forward.

---

### Post by harrykar on 2009-06-20
Hi guys i read almost all posts regarding base here. First I have tried repos version but i obtain error regard Mysql connection so i decide use the latest base version. I take a glance on Base's Install doc but not clue.I obtain subsequent errors:
```

**Warning**:  include_once(Mail.php) [[function.include-once]("http://localhost/base/function.include-once")]: failed to open stream: No such file or directory in **/var/www/base/includes/base_action.inc.php** on line **29**

**Warning**:  include_once() [[function.include]("http://localhost/base/function.include")]: Failed opening 'Mail.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/base/includes/base_action.inc.php** on line **29**

**Warning**:  include_once(Mail/mime.php) [[function.include-once]("http://localhost/base/function.include-once")]: failed to open stream: No such file or directory in **/var/www/base/includes/base_action.inc.php** on line **30**

**Warning**:  include_once() [[function.include]("http://localhost/base/function.include")]: Failed opening 'Mail/mime.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/base/includes/base_action.inc.php** on line **30**

**Warning**: Cannot modify header information - headers already sent by (output started at /var/www/base/includes/base_action.inc.php:29) in **/var/www/base/base_common.php** on line **1077**

```base_conf.php is configured like Base Install doc or bodhi.zazen indications
Any workarround here?
TIA

---

### Post by bodhi.zazen on 2009-06-21
> **harrykar said:**
> Hi guys i read almost all post regarding base here. First I have tried repos version but i obtain error regard Mysql connection so i decide use the latest base version. I take a glance on Base's Install doc but not clue.I obtain subsequent errors:
```

**Warning**:  include_once(Mail.php) [[function.include-once]("http://localhost/base/function.include-once")]: failed to open stream: No such file or directory in **/var/www/base/includes/base_action.inc.php** on line **29**

**Warning**:  include_once() [[function.include]("http://localhost/base/function.include")]: Failed opening 'Mail.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/base/includes/base_action.inc.php** on line **29**

**Warning**:  include_once(Mail/mime.php) [[function.include-once]("http://localhost/base/function.include-once")]: failed to open stream: No such file or directory in **/var/www/base/includes/base_action.inc.php** on line **30**

**Warning**:  include_once() [[function.include]("http://localhost/base/function.include")]: Failed opening 'Mail/mime.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/base/includes/base_action.inc.php** on line **30**

**Warning**: Cannot modify header information - headers already sent by (output started at /var/www/base/includes/base_action.inc.php:29) in **/var/www/base/base_common.php** on line **1077**

```base_conf.php is configured like Base Install doc or bodhi.zazen indications
Any workarround here?
TIA

See this post (buried in the original thread).

[http://ubuntuforums.org/showpost.php?p=7088432&postcount=117](http://ubuntuforums.org/showpost.php?p=7088432&postcount=117)

---

### Post by harrykar on 2009-06-21
> **bodhi.zazen said:**
> See this post (buried in the original thread).

[http://ubuntuforums.org/showpost.php?p=7088432&postcount=117](http://ubuntuforums.org/showpost.php?p=7088432&postcount=117)

Thanks a lot bodhi.zazen. I see the post and  finally i resolve(almost i hope!).
So i resume the instalation steps of latest Base version 1.4.3 (gabi) on latest Ubuntu Jaunty [ after have succefully installed snort-mysql (on purpose i have debpacked the latest snort-mysql (mean with mysql support) release and posted it on [Launchpad]("http://launchpadlibrarian.net/27625540/snort-mysql_2.8.4.1-1_i386.deb") on [that ]("https://bugs.launchpad.net/ubuntu/+source/snort/+bug/222091")page for who's interested) and mysql (repos version just goes) ]:

[LIST=1]
[*][ Download]("http://sourceforge.net/project/showfiles.php?group_id=103348") base-x.y.z.tgz
[*]   pear install Image_Color Image_Canvas-alpha Image_Graph-alpha Mail Net_SMTP Auth_SASL Mail_Mime
[*]tar zvxf /base-x.y.z.tar.gz (uncompres where you want)
mv base-x.y.z base (rename base directory)
[*]sudo cp base /var/www (copy base to /var/www )
[*]BASE CONFIGURATION (from base install docs. But You must change*  $DBlib_path* like below and eventually set your mysql related values like in *snort.conf*)
[*]  Copy the base_conf.php.dist to base_conf.php
[*]  Basic install requires configuration of key options in the base_conf.php file 
    Those options are: 
    the path to the BASE files in the webserver/php directory 
        $BASE_urlpath = "/base";  
    the location of the db library files 
        $DBlib_path = "/usr/share/php/adodb";  
    the type of database 
        $DBtype = "mysql";  
    the name of the database 
        $alert_dbname = "snort"; 
    the location of the database "localhost" if local or ip/hostname if remote  
        $alert_host = "localhost";  
    the SQL port the database is listening on 
        $alert_port = "";  
    the username used to access the databae 
        $alert_user = "snort";  
    the password for the username to used to access the database 
        $alert_password = "password_from_snort_conf";
[*]We're ready to go:popcorn: :guitar:
[/LIST]
PS1: For who's interested on my blog i insert a [context post]("http://harrykar.blogspot.com/2009/05/snort-ids-ips-nsm-andbeyond.html") (for newbies sysops as target, beyond that for everyone) regard snort & the alike.

PS2: (for bodhi.zazen as forums admin )I have noticed that for IM exist all VIPs protocols but not XMPP(alias Jabber). We're for Open systems or not?:D


Best Regards
Harry

---

### Post by coCoKNIght on 2009-07-08
Hi all

I've followed the [SnortIDS]("https://help.ubuntu.com/community/SnortIDS") tutorial in the Community Docs but while installing **acidbase** I got the following message:
> libphp-adodb is no longer installed in /usr/share/adodb. New installation path is now /usr/share/php/adodb.

Please update your php.ini file. Maybe you must also change your web-server configuraton.
php.ini doesn't however apear to contain anything related to adodb...

When I go to [http://localhost/acidbase/base_db_setup.php](http://localhost/acidbase/base_db_setup.php) I get:
> Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'snort'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 382

Error (p)connecting to DB : snort@

Check the DB connection variables in base_conf.php

               = $alert_dbname   : MySQL database name where the alerts are stored 
               = $alert_host     : host where the database is stored
               = $alert_port     : port where the database is stored
               = $alert_user     : username into the database
               = $alert_password : password for the username
              

Database ERROR:Access denied for user 'snort'@'localhost' (using password: YES)
So I searched for base_conf.php
```
locate base_conf.php
```
but nothing's found...

Any hints?

---

### Post by rootlinuxusr on 2009-07-15
> **coCoKNIght said:**
> Hi all

I've followed the [SnortIDS]("https://help.ubuntu.com/community/SnortIDS") tutorial in the Community Docs but while installing **acidbase** I got the following message:

php.ini doesn't however apear to contain anything related to adodb...

When I go to [http://localhost/acidbase/base_db_setup.php](http://localhost/acidbase/base_db_setup.php) I get:

So I searched for base_conf.php
```
locate base_conf.php
```
but nothing's found...

Any hints?

I'm getting the same errors - However base_conf.php at least in my install is located in:
```
/etc/acidbase/base_conf.php
```

---

### Post by bodhi.zazen on 2009-07-16
Part 1.

The locate command uses a data base and so is not up to date imediatly after you install new software.

To manually update the database

```
sudo updatedb
```

locate should then work.

Part 2. Is mysql installed and configured ? Post the contents of  [FONT=monospace][/FONT]/etc/acidbase/base_conf.php

you can change or xxx out username and password, so long as you confirm that you are using teh proper username and password for mysql.

---

### Post by coCoKNIght on 2009-07-16
Thanks! Once I knew where base_conf.php is, I was able to adjust the configuration in order for base to access the snort database.
Then I could create the Base AG tables and it all works fine now.
Does anybody know why you're not supposed to let the snort install create and configure the snort database (according to [SnortIDs]("https://help.ubuntu.com/community/SnortIDS"))?

---

### Post by a2brute on 2009-07-30
I realize this thread is pretty old, but it is the only one that came up in my search for the issue I'm having.

I installed the acidbase package in hardy (8.0.4 LTS) and configured it to use my existing postgresql server using the database config tool included with the package.

When I go to  [http://[myserver]/acidbase](http://[myserver]/acidbase) I get this same error posted earlier in the thread:

"Error (p)connecting to DB : acidbase_db@[mydbserver]

Check the DB connection variables in base_conf.php

               = $alert_dbname   : MySQL database name where the alerts are stored 
               = $alert_host     : host where the database is stored
               = $alert_port     : port where the database is stored
               = $alert_user     : username into the database
               = $alert_password : password for the username
              

Database ERROR:Database connection failed"

When I check base_conf.php, I find none of the listed variables, but I did find the line "require('/etc/acidbase/database.php');". So I checked database.php and the values are all correct.  Though there some other variables in database.php not listed above.  The contents are as follows:

$alert_user='acidbase';
$alert_password='************';
$basepath='';
$alert_dbname='acidbase_db';
$alert_host='[mydbserver]';
$alert_port='';
$DBtype='pgsql';

(the password and the hostname of my database server are spelled out in the actual file, omitted here for security purposes)

I attemped to log in to my database server using:
"psql -U acidbase -h [mydbserver] -d acidbase_db"
it prompted me for the password, and then logged in just fine.  The only thing I noticed was that acidbase_db was a blank database.

So if I can log in to the database from the command line, I've no clue why acidbase is giving me the connection error on the php page.

If anyone has any suggestions it would save my *** and my client's network.

Thanks.

---

### Post by coCoKNIght on 2009-07-31
I think you're supposed to use the snort db info for the alert_db parameters

---

### Post by vladunkov on 2011-01-10
Hey guys,

Probably I am a bit late with my problem, but I hope you will manage to give me an advice about my issue. I managed to install/run everything, also to "create BASE AG" but when I try to open [http://localhost/acidbase/base_main.php](http://localhost/acidbase/base_main.php) I am getting the error below:
The underlying database snort@ appears to be incomplete/invalid
Database ERROR:Table 'snort.iphdr' doesn't exist

It might be an older version. Only alert databases created by Snort 1.7-beta0 or later are supported

I checked my snort db and I can't find this iphdr. Shouldn't be created by the script I run "create BASE AG" or I need to do it manually? Your help will be really appriciated! Thank you!

Best regards,
Vladimir

---

### Post by vladunkov on 2011-01-10
Hey guys,

Probably I am a bit late with my problem, but I hope you will manage to give me an advice about my issue. I managed to install/run everything, also to "create BASE AG" but when I try to open [http://localhost/acidbase/base_main.php](http://localhost/acidbase/base_main.php) I am getting the error below:
The underlying database snort@ appears to be incomplete/invalid
Database ERROR:Table 'snort.iphdr' doesn't exist

It might be an older version. Only alert databases created by Snort 1.7-beta0 or later are supported

I checked my snort db and I can't find this iphdr. Shouldn't be created by the script I run "create BASE AG" or I need to do it manually? Your help will be really appriciated! Thank you!

Best regards,
Vladimir

---

