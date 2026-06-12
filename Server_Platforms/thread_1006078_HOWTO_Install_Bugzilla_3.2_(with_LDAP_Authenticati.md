---
title: "HOWTO: Install Bugzilla 3.2 (with LDAP Authentication) on Ubuntu Server 8.04"
date: 2008-12-08
forum: Server Platforms
---

### Post by mongobongo on 2008-12-08
OK.  Did a quick search earlier and couldn't find it on Ubuntu forums so I suppose it hasn't been posted yet.

NOTE: This was on a fresh install of Bugzilla 3.2 on Ubuntu Server 8.04

Options:
LAMP
OpenSSH server
Email server (however you wish to configure)

sudo apt-get update

sudo apt-get upgrade install

**Get dependencies**

sudo apt-get install libapache2-mod-perl2 libtemplate-perl libmime-perl libappconfig-perl libdbd-mysql-perl libtimedate-perl libgd-gd2-perl libgd-text-perl libxml-twig-perl perlmagick libemail-send-perl libemail-mime-modifier-perl libchart-perl libgd-graph-perl libhtml-scrubber-perl libnet-ldap-perl libsoap-lite-perl make

**Download Bugzilla 3.2**

wget [http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-3.2.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-3.2.tar.gz)

Untar it: 

sudo tar -xzf bugzilla-3.2.tar.gz

Move it:

sudo mv bugzilla-3.2 /var/www/bugzilla

**Time to figure out what else we need**

cd /var/www/bugzilla/

Become sudo: 

sudo -s

Run checksetup:

./checksetup.pl

**Get these:**

perl install-module.pl CGI

perl install-module.pl Email::MIME::Attachment::Stripper

perl install-module.pl Email::Reply

**Edit Local Config file:**

vi localconfig

**FIND THESE LINES AND EDIT**

# This is the group your web server runs as.
# If you have a Windows box, ignore this setting.
# If you do not have access to the group your web server runs under,
# set this to "". If you do set this to "", then your Bugzilla installation
# will be _VERY_ insecure, because some files will be world readable/writable,
# and so anyone who can get local access to your machine can do whatever they
# want. You should only have this set to "" if this is a testing installation
# and you cannot set this up any other way. YOU HAVE BEEN WARNED!
# If you set this to anything other than "", you will need to run checksetup.pl
# asroot, or as a user who is a member of the specified group.
$**webservergroup** = 'www-data';

# What SQL database to use. Default is mysql. List of supported databases
# can be obtained by listing Bugzilla/DB directory - every module corresponds
# to one supported database and the name corresponds to a driver name.
$**db_driver** = 'mysql';

# The DNS name of the host that the database server runs on.
$**db_host** = 'localhost';

# The name of the database
$**db_name** = 'bugs';

# Who we connect to the database as.
$**db_user** = 'bugzilla';

____________________

**Create MySQL DB and bugzilla user/password**

mysqladmin -p create bugs

create user 'bugzilla';

set password for 'bugzilla'@'localhost'=password ('**somepassword**');

grant all on bugs.* to 'bugzilla'@'localhost';

flush privileges;

\q

**test MySQL DB connection**

mysql -u bugzilla -p bugs

**Enter the password you specified from above.**

\q


**Run checksetup again and answer questions**

./checksetup.pl

**Edit your sites available so that Bugzilla Main Page answers by your machinename (or however you prefer)**

vi /etc/apache2/sites-available/default

**Find and change**

DocumentRoot /var/www/bugzilla

AND

<Directory /var/www/bugzilla>
                Options Indexes FollowSymLinks MultiViews
                Options +ExecCGI
                AllowOverride Limit
                DirectoryIndex index.cgi
                AddHandler cgi-script .cgi
                Order allow,deny
                allow from all
        </Directory>


/etc/init.d/apache2 reload

[B]Assuming you have DNS setup and configured, browse to *_machinename_* with your favorite browser
[/B]

**Login with the account you created from running checksetup.pl**

**For LDAP Authentication**

After logging-in the first time you will receive a message about configuring your servers parameters.  Configure your required settings... 

For LDAP select "**User Authentication**" in the box on the left.  

Scroll down to **user_verify_class** and under **LDAP** select LDAP and bump it up to just under DB.  This way we can authenticate users created in DB first, then LDAP if not there.

Next, click on LDAP in the box on the left.  Configure your LDAP parameters.

NOTE: for bind dn, you must use semicolons instead of commas and append your "LDAP query account password" to the end of your bind string with a colon ":"

Example:  cn=yourLDAPqueryAcct;cn=Users;dc=your;dc=domain;dc=com:yourLDAPqueryAcctPassword

Extra Note: I had to bind using sAMAccountName (instead of the default uid) in LDAPuidattribute.  Also, turn LDAPstarttls to On.

Configure the rest of your servers parameters.

Good Luck!

---

### Post by Thyagaraj on 2010-10-26
Thanks for the post!. I need some help in configuring bugzilla ldap authentication. I tried this many ways but didn't not do this. I have posted a new thread here [http://ubuntuforums.org/showthread.php?t=1512225](http://ubuntuforums.org/showthread.php?t=1512225)

---

### Post by petermp on 2011-01-29
I had to install gcc in order to install DateTime successfully.

---

