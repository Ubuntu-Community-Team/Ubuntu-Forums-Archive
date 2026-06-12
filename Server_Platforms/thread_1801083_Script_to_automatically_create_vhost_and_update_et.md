---
title: "Script to automatically create vhost and update /etc/hosts?"
date: 2011-07-09
forum: Server Platforms
---

### Post by geraldvillorente on 2011-07-09
Hi Guys,

Do you have any idea on how to achieve my goal? Here is the scenario. As a requirement on our development process for every ticket we have we need to create a branch(svn) so that we can develop without disturbing other developer. Now for every checkout I made I need to create a vhost so that I can develop first in my local before deploying to the branch. 

The site I'm working on is based in Drupal. The files I checked out is just the **all** folder of Drupal. The core files are already in my local. So the script would grab the core files and copy the all folder in my checkout branch then put them in the vhost.

So basically I need a script that will do these automatically for me:

1. Setup a vhost
   Ex: My branch name is 1205googleplusone. Inside that branch has two folders, **all** and d**efault**. What I need only is the DocumentRoot should only point to **all** folder.

2. Update the /etc/hosts
   Ex: The URL should be **1205googleplusone.domain.com**. 

3. Create a new database for the new site
   The script should create a new database and update the configuration.php

Hope somebody will help me. Appreciate all the help coming from you guys.

Thanks

---

### Post by ian dobson on 2011-07-10
Hi,

A simple bash script should be enough:-
echo newhostname ip address to hosts file
run mysqladmin with database structure as input (to create SQL table)
do what ever to config.php

If you provide me with the exact requirements I could bang something together.

Regards
Ian Dobson

---

### Post by geraldvillorente on 2011-07-10
> **ian dobson said:**
> Hi,

A simple bash script should be enough:-
echo newhostname ip address to hosts file
run mysqladmin with database structure as input (to create SQL table)
do what ever to config.php

If you provide me with the exact requirements I could bang something together.

Regards
Ian Dobson

Hi Ian,


First thanks for the quick response. Sorry for being unclear. Hope this information will help you. 

My SVN workspace structure:

**/home/kirksten/workspace**

Under workspace are my branches:

[B]
1105fblikebutton
1106twitterbutton
1107googleplusone
1108linkedinbutton
1109weibobutton
1110renrenwidget
[/B]

Branch structure:

[B]
all
default
[/B]

"all" folder structure:

[B]
libraries
modules
themes
[/B]

My Drupal core files:

**/home/kirksten/drupal** - This includes the following:

[B]
includes
misc
modules
profiles
scripts
sites
themes
and some files....
[/B]

My Drupal shared files:

**/var/files ** - Containing all files(images,videos,and other media files)

My webroot:

**/var/www/vhosts**

DB source:

**/home/kirksten/databases/project_drupal_sql** - Where project_drupal_sql is the sql file

So basically the script will execute the following in order.

1. Create a directory inside vhosts and name it according to branch name. So if the branch name is **1105fblikebutton** the directory name should be 1105fblikebutton.dev-drupal.com

2. Copy the Drupal core from **/home/kirksten/drupal** and put inside **1105fblikebutton.dev-drupal.com** 

3. Copy the **all** folder from the branch(Ex.**1105fblikebutton**) I need to work on and put it inside the sites folder. 

Where sites folder is inside **1105fblikebutton.dev-drupal.com**

4. Create a **default** folder inside **sites** folder and create a link of **files** folder from **/var/files**

5. Generate a new **configuration.php** under **sites/default/**
I'm not sure about this part coz we need to edit the db information part inside the file to use the new database name.

6. Create a new database. Database name should be the branch name.

7. Edit the **hosts** file to add the dev server created.

8. Restart the apache server.

Basically I need a script that will do this like this way:

**createvhost 1105fblikebutton.dev-drupal.com** 

Where **1105fblikebutton** is a branch name and **.dev-drupal.com** is constant.

Thanks a lot.

Gerald

---

### Post by ian dobson on 2011-07-10
Hi,

This is what I've got up til now

```

#!/bin/bash

##Define Varables
webroot=/var/www/vhosts/
DBsource=/home/kirksten/databases/project_drupal_sql
SVNWorkspace=/home/kirksten/workspace
DrupalSharedFiles=/var/files/
VhostsPath=/tmp/
FixedText=.dev-drupal.com
DrupalCore=/home/kirksten/drupal/
ServerIPAddress=192.168.0.1

#Read command line parameter
NewHost=$1

#1. Create a directory inside vhosts and name it according to branch name. So if the branch name is 1105fblikebutton the directory name should be 1105fblikebutton.dev-drupal.com
echo mkdir $webroot$NewHost$FixedText

#2. Copy the Drupal core from /home/kirksten/drupal and put inside 1105fblikebutton.dev-drupal.com
echo cp $DrupalCore* $webroot$NewHost$FixedText/ -R

#3. Copy the all folder from the branch(Ex.1105fblikebutton) I need to work on and put it inside the sites folder. Where sites folder is inside 1105fblikebutton.dev-drupal.com


#4. Create a default folder inside sites folder and create a link of files folder from /var/files

#5. Generate a new configuration.php under sites/default/ I'm not sure about this part coz we need to edit the db information part inside the file to use the new database name.

#6. Create a new database. Database name should be the branch name.

#7. Edit the hosts file to add the dev server created.
echo echo $ServerIPAddress $NewHost $NewHost > /etc/hosts

#8. Restart the apache server
echo /etc/init.d/apache2 restart

```

The code doesn't do anything more than echo the commands that should be executed. You need to explain 3-6 abit more/what commands you would execute to perform the required actions.

Regards
Ian Dobson

---

### Post by geraldvillorente on 2011-07-10
Hi Ian,

Really thanks for shedding light to me. Really appreciate your effort to help me out.

To explain further the #3 - #6. 

3. Copy the all folder from the branch(Ex.1105fblikebutton) I need to work on and put it inside the sites folder. Where sites folder is inside 1105fblikebutton.dev-drupal.com

Ex: 
[B]
cp /home/kirksten/workspace/1105fblikebutton/all /var/www/vhosts/1105fblikebutton/sites/
[/B]

4. Create a default folder inside sites folder and create a link of files folder from **/var/files**

Ex: 
[B]
mkdir /var/www/vhosts/1105fblikebutton/sites/default
ln -s /var/files /var/www/vhosts/1105fblikebutton/sites/default/files
[/B]


5. Generate a new configuration.php under sites/default/ I'm not sure about this part coz we need to edit the db information part inside the file to use the new database name.

I have a configuration.php file. Maybe we could copy it and modify to point to the correct database.

6. Create a new database. Database name should be the branch name. 

The script will create a new db and import the sql file from the backup

Ex:
[B]
mysql>create database drupal_1105fblikebutton;
mysql>use drupal_1105fblikebutton;
mysql>\. /home/kirksten/databases/drupal_database
[/B]

Then there is a part in the configuration.php for db connection.

```
$db_url = 'mysql://root:pass123@localhost/databasename';
```

So basically we just need to alter the databasename to become

```
$db_url = 'mysql://root:pass123@localhost/drupal_1105fblikebutton';
```

Hope this help Sir..really thanks

---

### Post by ian dobson on 2011-07-10
Hi,

OK and how is this:-
```
#!/bin/bash

##Define Varables
webroot=/var/www/vhosts/
DBsource=/home/kirksten/databases/project_drupal_sql
SVNWorkspace=/home/kirksten/workspace
DrupalSharedFiles=/var/files/
VhostsPath=/tmp/
FixedText=.dev-drupal.com
DrupalCore=/home/kirksten/drupal/
ServerIPAddress=192.168.0.1

#Read command line parameter
NewHost=$1

#1. Create a directory inside vhosts and name it according to branch name. So if the branch name is 1105fblikebutton the directory name should be 1105fblikebutton.dev-drupal.com
echo mkdir $webroot$NewHost$FixedText

#2. Copy the Drupal core from /home/kirksten/drupal and put inside 1105fblikebutton.dev-drupal.com
echo cp $DrupalCore* $webroot$NewHost$FixedText/ -R

#3. Copy the all folder from the branch(Ex.1105fblikebutton) I need to work on and put it inside the sites folder. Where sites folder is inside 1105fblikebutton.dev-drupal.com
echo cp /home/kirksten/workspace/$NewHost/all /var/www/vhosts/$NewHost/sites/

#4. Create a default folder inside sites folder and create a link of files folder from /var/files
echo mkdir /var/www/vhosts/$NewHost/sites/default
echo ln -s /var/files /var/www/vhosts/$NewHost/sites/default/files

#5. Generate a new configuration.php under sites/default/ I'm not sure about this part coz we need to edit the db information part inside the file to use the new database name.
#Note here we dump a standard config.php into sed which searchs/replaces the host name with the new name and writes to a file. This must be tested
echo "cat /somewhere/config.php | sed s/OldDBName/$1/g; > /config.php"


#6. Create a new database. Database name should be the branch name.
echo mysql create database $1;
echo mysql "use drupal_$1;  /home/kirksten/databases/drupal_database;"

#7. Edit the hosts file to add the dev server created.
echo echo $ServerIPAddress $NewHost $NewHost > /etc/hosts

#8. Restart the apache server
echo /etc/init.d/apache2 restart
```

At the moment the script doesn't actually do anything more than echo the commands it would execute. This should be enough for you to get the script up and running. If you have any questions just ask.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-07-12
Hi,

Was my script of any use to you?

Regards
Ian Dobson

---

