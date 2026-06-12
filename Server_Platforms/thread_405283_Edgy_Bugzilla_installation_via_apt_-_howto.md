---
title: "Edgy Bugzilla installation via apt - howto"
date: 2007-04-09
forum: Server Platforms
---

### Post by locutus42 on 2007-04-09
It took awhile to figure out the little glitches and I've not tested email yet but FWIW, here are the steps I had to take to get Bugzilla v2.2 installed on the last Edgy beta using what's in the Ubuntu repositories. This is the script I used since I ran this over and over from a LiveCD setup in order to get it installed and somewhat working:

file: /usr/local/bin/bugzillaInstall

```

#!/bin/bash

# file: bugzillaInstall
# location: /usr/local/bin
#
# mount workstation partition for script access and wireless files
#mkdir mnt
#sudo mount /dev/hda3 mnt
sudo cp mnt/lib/firmware/bcm43xx_* /lib/firmware/
# Enable faster LiveCD access
sudo hdparm -c1 -d1 -u1 -m16 /dev/hdc
echo "*************************************************************"
echo "Add Universe and Multiverse repositories to apt package system."
echo "Uncomment 'universe' lines and add multiverse to the end of those lines."
echo "*************************************************************"
sleep 10;
sudo vi /etc/apt/sources.list
sudo apt-get update
sudo apt-get install apache apache-perl mysql-server
# note:
# apt-get said there were errors while processing apache. Fixing with -f
sudo apt-get -f install

echo "*************************************************************"
echo "setting root password in MySQL, and create the 'bugzilla' dbase"
echo "Hit 'Enter' when prompted for the default MySQL root password."
echo "*************************************************************"
sleep 5;
mysql -u root -p < mnt/usr/local/bin/bugzillaInstall.sql
echo "*************************************************************"
echo "During the Bugzilla package install, you will be prompted for:"
echo "Entering your bugzilla Admin email address."
echo "Entering the Bugzilla Admin password of 'secret'."
echo ""
echo "Choose to install using dbconfig-common."
echo "Use your MySQL Admin password of 'mysql'"
echo "Use your Bugzilla password of 'secret'"
echo ""
echo "Choose to use the Package Maintainers version of 'params' file."
#echo "Use mysql user=root and pasword=mysql"
#echo "Use bugzilla user=bugzilla and pasword=secret"
echo "*************************************************************"
sleep 5;
sudo apt-get install bugzilla
sudo /usr/share/bugzilla/lib/checksetup.pl
echo "*************************************************************"
echo "login with the email address entered during bugzilla install"
echo "Use the 'secret' password
echo "Login using the following URL:"
echo "   http://localhost/cgi-bin/bugzilla/index.cgi?GoAheadAndLogIn=1"
echo "*************************************************************"

# MySQL notes:
#mysql -u root -p
#set password for 'root'@'localhost' = password('your_password');
#grant all privileges on bugzilla.* to 'bugzilla'@'localhost' identified by 'secret';
```

file: /usr/local/bin/bugzillaInstall.sql
```

set password for 'root'@'localhost' = password('mysql');
create database bugzilla;
commit;

```


This whole setup will install apache, MySQL, an email system, perl, along with Bugzilla. 
Issues:
[LIST=1]
[*]I've not currently tested/debugged the email sysytem though it will be required for easily adding new users to the Bugzilla system.
[*]I tried setting up the use of SMTP for email in the "params"->"Email" section of the Bugzilla and that didn't work. My experiences with a new Debian install used Exim4 for SMTP and that's not installed in this example.
[*]The baseURL listed in 'params' is a problem and is why the login URL is not the standard on on the homepage of your Bugzilla install. That might be fixed by setting up a virtual host( /etc/apache/sites-available ) and updating the baseURL accordingly. 
[*]?
[/LIST]

Things to try:
[LIST=2]
[*]install Exim4 and see if SMTP will work
[*]setup the apache virtual host for the bugzilla home directory and update Bugzillas baseURL
[*]see how the Feisty Server LAMP installation handles adding bugzilla to the stack
[*]try updating Bugzilla to the 3.x version
[/LIST]

Comments/rants:
[LIST=3]
[*]installing Debian Sarge into a VMware VM using the DebianNet Install was much easier to get all this running and it didn't default to the big sendmail stack installation or the quirks I saw in the Ubuntu installation.
[*]having setup a Bugzilla system for a 'Windows' shop, I can say that they were none to happy with all the pieces and steps it took to build this. Though they are used to paying thousands of dollars for something only close to this, they really dwelled on how easy Windows software is to install. We need to see some improvements in this regard before there's wider scale usage of these kinds of tools/services. Since they don't keep their fingers on their Linux systems like they keep their hands on their Windows mice, they're not comfortable with all the non-GUI setup and configurations.
[*]Putting all these pieces together just for a ticket tracking system needs to be ALOT easier if Ubuntu is going to move much further into the server space.
[*]The tools many businesses need are there but not currently accessible at the moment. As a matter of fact, a few companies I know still use the spreadsheet for ticket tracking and one uses an online wiki for version control. 
[/LIST] 

Have fun. :-)

---

### Post by marko on 2007-04-12
Working on a similar issue, but currently on Dapper with an older Bugzilla install.  My question is:  Why is this so hard?  Is it because it involves so many components and everything has to work together?  I have been frustrated with how challenging it can be to setup a working Bugzilla server.

Although most of my install works, I do wish I could get it running with lsws (Litespeed Tech's web server).  Great as Apache is, LSWS is really impressive.  Hard enough finding documentation on Bugzilla install, it is near impossible to find the combination of Ubuntu, Bugzilla, and LSWS in one place.

Maybe someone has already made this combination of software work together.  If so, I would appreciate hearing about it.

---

### Post by Eriol_Ancalagon on 2007-05-14
Ya this is pretty annoying trying to set something up "relatively quickly" for testing purposes.  The main steps away from just "apt-get"ing the packages are:
Before installing bugzilla
[LIST][*]Set up a root mysql password
[*]Set up a "bugzilla" table inside mysql[/LIST]
After installing bugzilla
[LIST][*]Changing the root password inside the config file to what you entered in your config files[/LIST]
After that, run checksetup and you should be mostly there.

Damned annoying it doesn't "just work" though.  Heck it has prompts, and it STILL doesn't work?  /boggle  The main thing is that the installer prompts seem to be trying to connect to the SPECIFIC "bugzilla" db inside mysql before it even MAKES that DB.  I also think it's copying the "Default" install config files before even configuring them causes confusion.

Overall, the maintainer needs to try a 100% clean install of 7.04 server (perhaps also checking "lamp install" like many will), try "apt-get install bugzilla" directly after installing the system (NOTHING else), and work from there.

---

### Post by Techno.Scavenger on 2007-07-18
I got it working for Ubuntu 7.04 by editing /etc/apache/httpd.conf, adding the following lines.

    Alias /bugs/ /usr/lib/cgi-bin/bugzilla/

   <Directory /usr/lib/cgi-bin/bugzilla>
      AddHandler cgi-script .cgi
      Options +Indexes +ExecCGI
      DirectoryIndex index.cgi
      AllowOverride Limit
   </Directory>

Then restart apache, /etc/init.d/apache restart. Of course you still have to follow the instructions above especially the part on creating the database and changing the password.

Rgds,
TechnoS

---

