---
title: "Headless MaNGOS server running on LAMP X86 and X64"
date: 2012-04-24
forum: Server Platforms
---

### Post by AdmiralMorketh on 2012-04-24
[CENTER][CENTER]_[SIZE=4]Prerequisites:[/SIZE]_[/CENTER]
[/CENTER]
  1+ ubuntu 10.04 server[s] running SSH + LAMP
Git to download the MaNGOS sources so we can build them
SVN so we can download some stuff we need
unzip so we can unpack our files
cmake so we can configure the package
g++ to compile the project
python to run a few of our Database scripts
SSH to make it headless
    [CENTER][CENTER][SIZE=4]_Pre-install prep_[/SIZE][/CENTER]
[/CENTER]
Before we get started lets go ahead and install the LAMP if you haven't already done so I normally install the entire system as a LAMP from the CD in a later tutorial I will discuss how to set up a website that will interface with the MaNGOS server for easy account management and basic admin tools but in-case you haven't or your installing all of this on a ubuntu desktop (you may think that's odd however I have a friend that has a laptop running a ubuntu server and had to do this type of install) lets go ahead and run the LAMP installer
```
sudo apt-get install lamp-server^
```The ^ is NOT a typo if you leave that out it will not work. In the install it will ask you for a MySQL password for your root user after all of that is done were ready for the rest of it.
Now we install SSH so we can use putty on a windows machine or even ssh through the ubuntu shell we will also need this for a few other steps if you want to be able to log into the mangosd server with ssh if you are setting up mangosd and realmd ((world and log in server)) on same host then this is only needed for remote access from a windows / Linux machine and is optional
```
sudo apt-get install ssh
```in this tutorial I will be using a static IP address of 192.168.2.200 for the Realmd server and 192.168.2.201 for Mangosd
now that we have SSH installed we need to set up SVN and GIT to download the source code for MaNGOS
```
sudo apt-get install subversion
```now we can install GIT
```
sudo apt-get install git-core
```after this we need cmake
```
sudo apt-get install cmake
```now we also need a g++ compiler and all of the dependencies to make MaNGOS compile
```
sudo apt-get install build-essential automake autoconf  libmysqlclient-dev libtool libssl-dev  zlib1g-dev  pkg-config
```once that is done we need to get a few utilities that we will use later in the process
```
sudo apt-get install unzip
```now we can grab it all and do our compile

```

mkdir SOURCE && cd SOURCE
git clone git://github.com/mangos/mangos.git
cd mangos
git clone git://github.com/scriptdev2/scriptdev2.git src/bindings/ScriptDev2/
git am src/bindings/ScriptDev2/pathces/MaNGOS-*
mkdir build/
cd build/
```ok this block of code is a lot I know but it’s not that bad in here the first git we do grabs the source code for MaNGOS and sets it up in the local directory the first time I did this I ended up with mangos/mangos because I didn't realize it grabbed that for me I would suggest to use a directory named SOURCE and work inside of that
after we have everything downloaded and patched we need to now configure mangos for an install
```
sudo cmake ../ -DPREFIX=/opt/mangos -DPCH=1 -DACE_USE_EXTERNAL=0 -DDEBUG=0 -DTBB_USE_EXTERNAL=0
```this command looks a little scary at first but there's a few things you might want to know about this one
-DPREFIX=/opt/mangos is the install location I have mine set here you can install it where you want it however be careful that you use your new location in the rest of the tut or it will break 
-DPCH=1 we want to use the pre-compiled headers that came with the mangos distro so we set this option here
-DACE_USE_EXTERNAL=0 we set this option as a default most people don't have an external installation of ACE however if you have one feel free to use that instead of the prepackaged ACE sources
-DDEBUG=0 is pretty self explanatory this option tells the compiler we want DEBUG off if you feel you need this option turned on feel free to set it to 1
-DTBB_USE_EXTERNAL=0 I’m not exactly sure what this option is if anyone has information on this I will post it here

Now that we have all of that ready and configured we can now do the final pre-compile step:
```
sudo make -j3
```I’m using -j3 because I have a Core I3 dual-core system this number is represents the amount of PHYSICAL CPUs + 1 that you have installed (( in case you are using a VM this option is the number of CPUs on your config section + 1 ))
for a single core computer you may set this to 2 
for the computer to automatically find and set the number you may drop the -j option altogether
this step will take a long time depending on the speed of your system. it will print out a ton of information on what files are being generated and built everything in this step will be placed in the
```
SOURCE/mangos/build
```directory.
  [CENTER][CENTER][SIZE=4]_Compiling & Installing MaNGOS_[/SIZE][/CENTER]
[/CENTER]
  Once we have it all configured and setup for our system we can start the compile process using a few commands:
```
sudo make install
```will now compile link and install everything into the directory we set earlier using 
-DPREFIX=/opt/mangos
after we finished the installation there is more left before your ready to run the server we have to download the new Databases set those up and get your MySQL system ready for logins from everywhere as your mangosd server will need to connect to your DB Host. once we get MySQL configured we then set up your databases up until now both servers have the same software and setup instructions from this point forward I will be using realmd on server 192.168.2.200 and mangosd on server 192.168.2.201 if you are using both mangosd and realmd on the same system you may follow these instructions in order on the same computer.
  [CENTER][CENTER]_[SIZE=4]Installing Databases REALMD server[/SIZE]_[/CENTER]
[/CENTER]
  This is going to be the easy one .we need to create the mangos user name and the realmd database then we have to set that up for use and we have to configure the MySQL server to accept connections from everything. That being said let’s see how it’s done.
```
cd SOURCES/mangos
MySQL -u root -pPASSWORD < sql/create_mysql.sql
```this will create the user mangos with password mangos it will also create a few databases realmd mangos characters we are only interested in realmd on this server however if you are installing mangosd on the same server you need these here
now we have to add all the tables to the realmd database
```
MySQL -u mangos -pmangos realmd < sql/realmd.sql
```you must use mangos mangos in order to set this up the create_mysql.sql file has the username and password already set up in that file there will be a step later to change the password.
Now that we have the realm DB set up we can now go edit our MySQL conf file to allow remote connections
  [CENTER][CENTER]_[SIZE=4][COLOR=DarkRed]/!\ YOU ONLY NEED TO DO THIS IF YOU ARE SETTING MANGOSD UP ON REMOTE HOST /!\[/COLOR][/SIZE]_[/CENTER]
[/CENTER]
  
if you are setting up mangosd on the same server you can safely skip to the MaNGOS database install
```
sudo pico /etc/MySQL/my.cnf
```change this line:
```
bind-address           = 127.0.0.1
```and comment it out to match this line:
```
#bind-address           = 127.0.0.1
```press Ctrl+x then Y to save then hit RETURN to write it and close the file
once we have set MySQL up for remote connections we need to restart the MySQL server so that changes take effect
```
sudo /etc/init.d/mysql restart
```should do the trick however if you have made a mistake in your my.cnf file it will more than likely complain at this point in time if so go back and fix it then restart the MySQL server again. If all went well (you can stop holding your breath at this point ^_^) something similar to the flowing should appear 
```
MySQL start/running, process 3973
```Now that we have all the configuration settings done for the remote host to connect to the realm DB we can now finish installing the mangos server.
  [CENTER][CENTER]_[SIZE=4]Installing Databases MANGOS server[/SIZE]_[/CENTER]
[/CENTER]
  Now in your SOURCES dir we need to set up a few directories and then SVN the files we need for the databases if you have been following the tutorial to the letter you should be able to run the following command and be in the same directory were you started out from the SOURCES folder we set up earlier
```
cd .. 
mkdir udb && cd udb
```this will create a folder for all of our Unified Database files used for our creature tables and NPCs.
once inside the directory we can now svn our files
```
svn co https://unifieddb.svn.sourceforge.net/svnroot/unifieddb unifieddb
```once we have all of that done we need to grab the ACID (Artificial Creature Intelligence Database) files so we can set them up. Right now the directory structure of your SOURCE folder should have 3 folders in it:
udb
acid
mangos
```
cd ..
mkdir acid && cd acid
```once that is done from that folder we can run this command to grab the ACID files from the SVN repository
```
svn co https://sd2-acid.svn.sourceforge.net/svnroot/sd2-acid sd2-acid
```once we have all of the databases downloaded we have to unpack the UDB files
so once again working from your SOURCE directory we run this command to unzip everything we need
```
unzip udb/unifieddb/trunk/Full_DB/*.zip
``` Now that we have the database downloaded and unpacked we have to build the databases for the MaNGOS server. If you have the realmd server and mangos server on the same server you may safely skip this section because we already set this up in the realmd section of the tutorial. We did not however add the database files to the database so the following steps will be needed.
```
cd SOURCES/mangos
MySQL -u root -pPASSWORD < sql/create_mysql.sql
```this will create the user mangos with password mangos it will also create a few databases realmd, mangos, and characters we are only interested in mangos and characters on this server we will also be adding the scriptdev2 database for the NPC scripts.
```
MySQL -u root -pPASSWORD < src/bindings/ScriptDev2/sql/scriptdev2_create_database.sql
``` This will set up the scriptdev database we will now build the structure of the database and install the tables
```
MySQL -u root -pPASSWORD scriptdev2 < src/bindings/ScriptDev2/sql/scriptdev2_create_structure_mysql.sql
MySQL -u mangos -pmangos scriptdev2 < src/bindings/ScriptDev2/sql/scriptdev2_script_full.sql
``` Once scriptdev is ready to go we can then install the mangos database.
```
 MySQL -u mangos -pmangos mangos < sql/mangos.sql
MySQL -u mangos -pmangos mangos < udb/unifieddb/trunk/FullDB/UDB_0.12.2_mangos_11792_SD2_2279.sql
MySQL -u mangos -pmangos mangos < acid/sd2-acid/trunk/wotlk/<HIGHEST_VER>/<HIGHEST_VER>_acid.sql
MySQL -u mangos -pmangos mangos < src/bindings/ScriptDev2/sql/mangos_scriptname_full.sql 

```NOTE: on the UDB files we unpacked earlier you will use that same sql file in this step you will have to replace the version number with your version as well as the ACID files in order to make it work.
After we have the mangos ready we can wrap up the database install with the last database characters
```
MySQL -u mangos -pmangos characters < sql/characters.sql
```Now we have the updates to install to make it run. this script needs to be placed in the mangos/sql/updates directory
I prefer pico as it’s a fast way to edit things on the command line however everyone has their own favorite text editor
```
sudo pico updates.py
```and then paste all of this in to that file:
```
#!/usr/bin/env python
import glob, os
patches = glob.glob('*.sql')
patches = sorted(patches)

for x in patches:
  db = x.split("_")[2].replace('.sql', '')
  os.system("MySQL -u mangos -pmangos -v " + db + " < " + x)
```then you need to make it executable
```
chmod +x updates.py
```and now e are ready to run it and patch the database.
```
python updates.py
```this will go through every update in the folder and order them all by the number that’s in the name once it arranges them it calls MySQL and inserts the SQL files into the database if you don’t need updates it won’t install any it will just say that it can’t find the right file. If all went well at this point we now need to set up the config files in the /opt/mangos/etc folder to get the system ready to go. Pay close attention over the next few steps as this gets a bit tricky if you have a varied installation as I often do.
  [CENTER][CENTER][SIZE=4]_Configuration_[/SIZE][/CENTER]
[/CENTER]
  let’s change directory to our install folder I used /opt/mangos as mine on both of my servers take note that we will be changing the realmd.conf on the realm server located at 192.168.2.200 and that we will also be changing the mangosd.conf on the mangos server located at 192.168.2.201 again if you have them on the same server you can safely change both files on the local host at each configuration setting I will give you examples for both local install and remote install.
First off we need to change to our configuration location
```
cd /opt/mangos/etc
```once here there is a few files of interest```
ls
mangosd.conf.dist  realmd.conf.dist  scriptdev2.conf.dist
```you will have to copy all of these to the same location to a conf file like this
```
sudo cp mangosd.conf.dist mangosd.conf
```because I am working in the /opt/ directory and by default the owner is root we need to use sudo to run all of these commands latter on I will explain how to set all of this up for a user of mangos and group of mangos.
```
sudo cp scritdev2.conf.dist scriptdev2.conf
```On the realm server you need to set this one up the others are unnecessary unless there on the same server.
```
sudo cp realmd.conf.dist realmd.conf
```on the mangosd server we also need to copy over the ahbot.conf file to install the Auction House Bot this file is located in your distro that you downloaded with git
```
sudo cp SOURCE/mangos/src/game/AuctionHouseBot/ahbot.conf.dist.in ahbot.conf
```once we have all the files copied to the right files we need to edit a few settings to tell the server how we have it set up I am going to start with the realmd conf file
I will be starting off with the Auction House settings
```
sudo pico ahbot.conf
```in here there is a few settings we need to change in order to get the AH working properly
```
.....
AuctionHouseBot.Seller.Enabled = 0
.......
AuctionHouseBot.Buyer.Enabled = 0
``` first off we need to find these and set them to 1 to enable the AH buy and sell feature.
Now in our mangosd.conf file we need to set up our realm log in info
```
LoginDatabaseInfo     = "192.168.2.200;3306;mangos;mangos;realmd"
```this option can be set up for localhost if you have both on same server.
the other 3 lines we are interested in are these
```
RealmID = 1
DataDir = "."
LogsDir = ""
```the realm ID is going to be the ID number for the server if you have multiple installations this number will indicate which entry in the database it needs to use.
DataDir is going to be the directory in which we place the de-compiled maps from our WoW client
LogsDir is the location in which to place all of our logs from the server you can use the default or you can change this to be in any location you choose. I prefer mine to be located in the system standard /var/log this is so I can have the logs rotated on a regular basis. the DataDir I normally keep in /opt/mangos/data you must create this directory the server will not do it for you.
```
sudo mkdir /opt/mangos/data
```in the scriptdev2 conf file if you have MySQL and mangos on the same machine you don’t have to touch this file as long as you have renamed it to ```
scriptdev2.conf
```now that we have all of that ready to go we need to check the Realmd settings and make sure we have that ready for startup
so on the realm server lets run these commands
```
sudo cp realmd.conf.dist realmd.conf
```this will copy the file to its proper name while leaving the original untouched.
most of the time you don’t have to touch this file unless you changed the username and password for mangos
at this point the only server daemon you can start up is the realm daemon so let’s go ahead and do that.
```
cd /opt/mangos/bin
sudo ./realmd
```your install location might be different then mine depending on how you installed it earlier if you followed this guide exactly it should be located here.
something similar to this should come up if it’s been configured right and the databases were setup right.
```
admiral@RealmD:/opt/mangos/bin$ sudo ./realmd
MaNGOS/ (* * Revision 11967 - *) for Linux_x32 (little-endian) [realm-daemon]
<Ctrl-C> to stop.

Using configuration file /opt/mangos/etc/realmd.conf.
Login Database total connections: 2
MySQL client library: 5.1.61
MySQL server ver: 5.1.61-0ubuntu0.10.04.1
MySQL client library: 5.1.61
MySQL server ver: 5.1.61-0ubuntu0.10.04.1
Added realm "MaNGOS"
```  [CENTER][CENTER]_[SIZE=4]Post Install setup[/SIZE]_[/CENTER]
[/CENTER]
  Now that we have done that we can now begin extracting all of the maps and other data from the WoW client you MUST have client 3.3.5a (12340) release in order for this to work right.
I suggest a program like WinSCP in order to pull the files from your computer and to pull the extractor binaries from the source directory we set up earlier.
using WinSCP lets go to this directory
```
SOURCE/mangos/contrib/extractor_binary
```and pull all the files to our windows machine where we will be running the client software. Copy the content of this directory into your client directory.
  Once we have finished copying all the files into the client directory running ad.exe will give you 2 folders: dbc, maps
  Once ad.exe finishes running we can then run 
  ```
vmpaExtractor3.exe –l –d data 
```  This will extract all the vmaps from the data directory and make a folder called Buildings
  Next from our cmd line we need to run
  ```
mkdir vmaps 
  vmap_assembler.exe Buildings vmaps
```  This will be a long wait it took my system 6 hours with a Core I3 x64 system with 16Gb of ram. that being said it will toss everything you need into the right wow client folder in subfolders you will need the following folders in you /opt/mangos/data directory before you can start the server. Before we can add anything to that directory on the server we need to set the right permissions on the mangos/data directory we want them Read/Write for everyone.
```
cd /opt/mangos
sudo chmod a+rw data
```should allow you to drop the files into the server using WinSCP.
```
admiral@MangosD:/opt/mangos/data$ ls
Buildings  dbc  maps  vmaps

```Once we have all of that copied into the directory we can now finally start the MaNGOS World server.
if you get something similar to this:
```
Cannot connect to login database 192.168.2.200;3306;mangos;mangos;realmd
```then don’t worry as again if you were following this guide exactly we haven’t set the mangos user in the realm server to be able to log in from everywhere. because I am going to be using static addresses I will be setting my mangos user on the realm server to log in from localhost and 192.168.2.201
there is a few different ways we can set this up I prefer to use Heidisql as its flexible for multiple connections and we can do some pretty powerful SQL commands with it
once we get into Heidi we need to change the user permissions for the user mangos if you prefer to do it on the MySQL command line I will give you the SQL code snip-it here for you to set it up.
```
MySQL -u root -pPASSWORD
CREATE USER 'mangos'@'192.168.2.201' IDENTIFIED BY 'mangos';
GRANT SELECT, EXECUTE, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, LOCK TABLES  ON `realmd`.* TO 'mangos'@'192.168.2.201' WITH GRANT OPTION;
quit;

```should give you something like this```
Query OK, 0 rows affected (0.00 sec)
```now we can try starting it all back up. you should now be able to change your realmlist.wtf file in your wow client folder make sure you set that to
```
set realmlist 192.168.2.200 
```my realm server is located at 192.168.2.200 yours will most likely be different check your ip address and use that instead.
once we are able to get the client set up we need to set up a user account so you can get on the server.
lets go ahead and start the server so we can begin to run the commands we need in order to get you on the system.
MaNGOS:
```
cd /opt/mangos/bin
sudo ./mangosd
```Realm:
```
cd /opt/mangos/bin
sudo ./realmd
```lets INSERT an admin level account into our DB so in a fresh terminal/screen/konsole on the realmd system:
```
mysql -u mangos -pmangos realmd
```this will log into the local MySQL server using USER mangos PASSWORD mangos and switch to realmd Database now you should get a prompt like this:
```
mysql>
```and we need to unlock the ADMINISTRATOR account that comes with the server so we can use that to set up accounts on the in-game chatline
```
UPDATE `account` SET `locked`=0 WHERE  `id`=1 LIMIT 1;
```the defualt password is ADMINISTRATOR. you can now log into your MaNGOS server using your admin account and password. from the in-game chatwindow you can use a list of commands to manage your users and your server there is a complete listing of the commands in your MaNGOS database and here is a short PHP script you can place into your /var/www folder to give you a complete list of them:
```
<?php

$database = "mangos";
$host = "localhost";
$username = "mangos";
$password = "mangos";

// Insert a non-breaking space in place of an empty string, useful for tables.
function ins_nbsp($something)
{
        if ($something == "")
        {
                $something = "&nbsp;";
        }
        return($something);
}
?>

<html>

<head>
   <title>Mangos Commands</title>
</head>

<body bgcolor="black">
<font color="white">
<center><h1>Commands</h1></center>

<center>
<table bordercolor="black" border="1">
        <tr>
                <th><FONT COLOR=WHITE>Name</FONT></th>
                <th><FONT COLOR=WHITE>GM Level</FONT></th>
                <th><FONT COLOR=WHITE>Description</FONT></th>
        </tr>

<?php
$view = 60;
$db = mysql_connect($host, $username, $password) or die ("Unable to connect!");
mysql_select_db($database,$db) or die ("Unable to select database!");

$query =  "SELECT name, security, help FROM mangos.command";

$result = mysql_query($query);
while ($row = mysql_fetch_array($result))
{
        $name = $row["name"];
        $security = $row["security"];
        $help = $row["help"];
        echo "\t<tr>\n";

        echo "\t\t<td><FONT COLOR=WHITE>$name</FONT></td>\n";
        echo "\t\t<td><FONT COLOR=WHITE>$security</FONT></td>\n";
        echo "\t\t<td><FONT COLOR=WHITE>$help</FONT></td>\n";
        echo "\t</tr>\n";
}
?>

</table>
</center>
</font>
<br>


</body>
</html>

```Hopefully all of this information saves you weeks of head-to-desk interaction and a hole in your pocket from purchasing Advil.  The next tutorial im thinking about putting together is getting a Mini-Manager web site set up to do all of the mundane database stuff for you.

---

### Post by AdmiralMorketh on 2012-04-24
As a note to users of the MaNGOS server platform there are a few quests that are broken that i have found:
ID number            Quest Name
____________________________________
12680        Grand Theft Palomino
12687        Into the Realm of Shadows
12733        Death's Challenge
12698        The Gift That Keeps On Giving
12701        Massacre At Light's Point
8483          The Dwarven Spy
8896          The Dwarven Spy



this list will grow as i find more bugs or more bugs are reported to me by other users.

---

### Post by beboylips on 2012-04-26
Thank you very much for the guide. Worked perfectly.

Btw, if anyone is interested, I'm setting up a server on MaNGOS on my box with a very decent bandwidth and ram. I just got back into WoW servers after a 2 - 3 year break and I got the shivers again so I want to play the game a little.

If anyone is interested, PM me with a username/password you want and I'll send you back all the info. Feel free to invite friends, my box can handle a very handsome amount of people.

:)

---

### Post by AdmiralMorketh on 2012-04-28
> **beboylips said:**
> Thank you very much for the guide. Worked perfectly.
...........
If anyone is interested, PM me with a username/password you want and I'll send you back all the info.

beboylips,
Im glad you found the guide helpful it took me almost 6 weeks to build my first server with the little documentation on the internet that i could find. Also to make your life easier as an admin i have run across an interesting php application that serves as a front end to the MaNGOS database ive played with it for a while and i know that if you have a MaNGOS realm server go offline or completely go down to the point MySQL is un-accessible the entire website is broken as of right now i dont know how to fix that and as such i did not post it before now. for the daily uses of Admin its a nice little toy instructions are pretty straight forward on it unzip the entire thing into the /www/var directory and then go to 
[http://YOUR.SERVER/install](http://YOUR.SERVER/install)
at which point the installer will walk you through the setup for your mangos site
[https://sites.google.com/site/mwenhanced/downloads](https://sites.google.com/site/mwenhanced/downloads)
the full release is normally ok for a fresh install incase in the future the link is broken you might try looking for MangosWeb Enhanced. i hope to at least fix a few things that i find annoying ive also found that MaNGOS has SOAP built in so theres a possibility of making an add-on to the admin panel for the console commands similar to WebMin for most server platforms which would be very nice to get mangos running in webmin ^_^

---

### Post by beboylips on 2012-05-03
Hey again,

I ran into an issue when setting un MaNGOS on my dedicated box. Both mangosd and realmd are running fine with updated databases but  I can't login into a realm. It just sends me back into the realm selection list. 

Any clues to what may be the causes?

Thanks

-Beboy

---

### Post by beboylips on 2012-05-08
Solved it. Had to change the IP of the realm in the realmd->realms table.

---

### Post by AdmiralMorketh on 2012-05-19
> **beboylips said:**
> Solved it. Had to change the IP of the realm in the realmd->realms table.
yup that would do it I apologize for the REALLY slow response time havent had the time latly to get on and check messages.

---

### Post by beboylips on 2012-05-20
Same here :)

---

