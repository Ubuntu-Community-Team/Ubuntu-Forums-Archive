---
title: "[HOW-TO] FTP installation for example of GlFTPd"
date: 2005-11-08
forum: Tutorials
---

### Post by Sir_Yaro on 2005-11-08
It's my first how-to in english so please don't be to severe... :D
go to :
[http://glftpd.com/](http://glftpd.com/)

download and unpack package. 
```

cd /tmp
wget http://glftpd.com/files/glftpd-LNX_2.01.tgz
gunzip -c glftpd-LNX_2.01.tgz | tar -xvf -

```
change directory
```
$ cd glftpd-LNX_2.01
```
install required software:
```
sudo apt-get install xinetd zip unzip openssl tcpd
```
And run script as a root
```
# sudo sh installgl.sh
```

Thats is example how to answer the questions:
> Use tcpd? [Y]es [N]o: y
Use a jailed environment? [Y]es [N]o: y
Please enter the private directory to install glftpd inside [/jail]: /jail
Use a private group? [Y]es [No]: y
What would you like your private group to be called? [glftpd]: glftpd
Who should have access to glftpd? (separate with ,): YOUR_USER(S)_NAME
Please enter the directory inside /jail to install glftpd to [/glftpd]: /glftpd
Press <enter> for the default (glftpd)> glftpd
Enter a service name for glftpd. [...]
Press <enter> for the default (glftpd)> glftpd

modifying source (bin/sources/glconf.h) ... OK.
Compiling source files in /jail/glftpd/bin/sources to /jail/glftpd/bin:
   ansi2gl .. OK.
   dirlogclean .. OK.
   dirloglist .. OK.
   dirlogscanner .. OK.
   dirlogsearch .. OK.
   dupeadd .. OK.
   dupecheck .. OK.
   dupediradd .. OK.
   dupelist .. OK.
   dupescan .. OK.
   flysfv .. OK.
   ftpwho .. OK.
   glupdate .. FAILED!
   killghost .. OK.
   nukelogclean .. OK.
   nukelogscanner .. OK.
   olddirclean2 .. OK.
   undupe .. OK.
   userstat .. OK.
   weektop .. OK.
   Failed to compile: /jail/glftpd/bin/sources/glupdate.c


Copying required shared library files:
   libacl.so.1: OK
   libattr.so.1: OK
   libncurses.so.5: OK
   libc.so.6: OK
   libdl.so.2: OK
   libm.so.6: OK
   libpthread.so.0: OK
   librt.so.1: OK

Copying your system's run-time library linker(s):
(NOTE: Searches can take a couple of minutes, please be patient.)
   ld-linux.so.2: OK

Configuring the shared library cache . . . Done.


don't care about this error above (probably? :P )
> Enter the port you would like glftpd to listen on [21]: 21
Do you wish to use European weeks? European weeks starts with a Monday.
This is for glftpd's 'reset' binary (see docs for more info) [Y/N]: y

Please specify location, inside /jail/glftpd,
to install the cert (ftpd-dsa.pem) [/etc]: /etc           
Please specify a generic name for this certificate.
This can be any name but should say something about the ftp server
like the name for it perhaps (press enter for glftpd): SirYaroFTP

I've removed most of comunicates but all important remain.
Now server generate key, it've taken about 10 sec on my computer and about 2 minutes in old version of glftpd.

Probably You'll receive error like that:
```

Restarting inetd . . . Failed! You must restart inetd before using glftpd.
```
That's mean You need to install inetd superserver. Let's do it:
```
$ sudo apt-get install inetd
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Uwaga, wybieranie inetutils-inetd zamiast inetd
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  inetutils-inetd
0 aktualizowanych, 1 nowo instalowanych, 0 usuwanych i 85 nieaktualizowanych.
Konieczne pobranie 37,6kB archiwów.
Po rozpakowaniu zostanie dodatkowo u&#380;yte 139kB miejsca na dysku.
Pob: 1 http://archive.ubuntu.com breezy/universe inetutils-inetd 2:1.4.2+20040207-4 [37,6kB]
Pobrano 37,6kB w 15s (2397B/s)

Prekonfiguracja pakietów ...
Zaznaczenie poprzednio niezaznaczonego pakietu inetutils-inetd.
(Odczytywanie bazy danych ... 103934 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie inetutils-inetd (z .../inetutils-inetd_2%3a1.4.2+20040207-4_i386.deb) ...

Konfigurowanie inetutils-inetd (1.4.2+20040207-4) ...
Starting internet superserver: inetd.

$    
```

Server will start automatically, let check it:
```
# nmap localhost|grep 21
21/tcp  open  ftp
```



Now we need to edit config:
```
sudo mcedit /jail/glftpd.conf
```

> #shutdown 1
define if server is on or off
0 - yes
1 - only for admin
!* - off
# at the begining - server works for all

> sitename_long   MY[:space:]SITE[:space:]NAME
Long name of the server. Replace every space with [:space:] string.

> sitename_short  MSN
short name of the server

> email           root@127.0.0.1
admin email

> rootpath /jail/glftpd
where is server root path (do not change)

Following lines leave unchanged:
-----------------------------------------
> # Path relative to the ROOTPATH.
datapath        /ftp-data

welcome_msg     /ftp-data/misc/welcome.msg      *
goodbye_msg     /ftp-data/misc/goodbye.msg      *
newsfile        /ftp-data/misc/newsfile         *
banner          /ftp-data/misc/banner

# TLS enforcements.
userrejectsecure        !*
userrejectinsecure      !*
denydiruncrypted        !*
denydatauncrypted       !*
-----------------------------------------

> color_mode 0
Display colour listings?
Turn off - it makes only problems

put # before line:
> site_cmd LOCATE         EXEC    /bin/locate.sh

> free_space 20
How much free space is required to grant upload permision

> max_users 15 5
How many user may be logged in at the same time

> total_users 300
Maximum accounts amount on server

> # dupecheck     how many days?  ignore file case like Windows?
dupe_check      7               no
Files duplicate checking. If You have good, stable bandwidth use it. Otherwise put turn it off - it may cause a lot of problems.

ex:
> dupe_check      0               no
nodupecheck *

> dl_incomplete 0
To allow downloading unfinished files put 1 instead of 0

> min_homedir /site
Inside this directory root directory (accessible for ftp users) of server is located. 

Now couple examples of additional configuration:


> upload          /site/katalog/*        *
everybody can upload to "katalog" directory

> upload          /site/katalog/Encore/* -seem
only "seem" user can upload to "katalog/Encore" directory

> upload          *                               -yaro -admin
users admin and yaro can upload everywhere

> download        *                               *
everybody can download everywhere

> rename          *                              admin 1 =STAFF
only admin, STAFF group and users with flag "1" can rename files and directories on all server

> renameown       *                               *
everybody can rename own files and directories

> delete          *                               1
only users with flag "1" can delete on all server

> privpath /site/Upload/by.Blaster -yaro 1 -blaster
above-mentioned directory (Upload/by.Blaster) is visible only for user "yaro", "blaster" and users with flag "1"


I think that's all from additional options


Now we may log in (login glftpd, password glftpd). IN EXACTLY THE SAME WAY LIKE ME
```
# ftp 127.0.0.1
Connected to 127.0.0.1.
220 MY SITE NAME (glFTPd 2.00 Linux+TLS) ready.
Name (127.0.0.1:root): glftpd
331 Password required for glftpd.
Password:
230-                                _____
230- ______________________________|__   |____ ________________________________
230- \     _      /   _     /  _     /   |    |    _     /  _     /    _      /
230-  \    \     /    /    /   /____/.   |    |    /    /   /____/.    /_____/
230-   \________/____/    /______    |___|____|___/    /______    |____|
230- .-=----------- /____/ ---- |____| --------- /____/ ---- |____| -------=-.
230- `-=-------------------------------------------------------------------=-'
230-       `-----( Type 'site onel MESSAGE' to enter your message )-----'
230 User glftpd logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>                                                 
```

If You received an error like this:
```

Connected to 127.0.0.1.
421 Service not available, remote server has closed connection
ftp> quit

```
do (**UNSECURE!!!!!!** but always working):
```

echo 'IP *@*'>>/jail/glftpd/ftp-data/users/glftpd
```
or:
```

echo 'IP *@your.ip.addres.here'>>/jail/glftpd/ftp-data/users/glftpd
```
ex:
```

echo 'IP *@83.141.171.241'>>/jail/glftpd/ftp-data/users/glftpd
```
or (probably UNSECURE as well):
```
echo 'IP *@0.0.0.0'>>/jail/glftpd/ftp-data/users/glftpd
```

It's happen beacause of some strange reasons you're not identified as some concrete ident and ip address. Look here:
```
$ sudo cat /jail/glftpd/ftp-data/logs/login.log
Wed Nov 23 16:23:37 2005 [6585  ] *@0.0.0.0 (0.0.0.0): connection refused: ident@ip not added to any users.
Wed Nov 23 16:23:48 2005 [6639  ] *@0.0.0.0 (0.0.0.0): connection refused: ident@ip not added to any users.
Wed Nov 23 16:28:10 2005 [7679  ] *@0.0.0.0 (0.0.0.0): connection refused: ident@ip not added to any users.
```

After this actions you can notice change(s) on the end of user file:
```
# cat /jail/glftpd/ftp-data/users/glftpd |tail -n 4
NUKE 0 0 0
TIME 1 923341886 0 0
IP *@127.0.0.1
IP *@83.141.171.241
#  
```

Now try login again:
```
$ ftp 127.0.0.1
Connected to 127.0.0.1.
220 MY SITE NAME (glFTPd 2.00 Linux+TLS) ready.
Name (127.0.0.1:yaro):                            
```

Now let's back to the point:
receiving informations about glftpd user

```
ftp> site user glftpd
200- User Comment: glftpd
200- +=======================================================================+
200- | Username: glftpd                   Created: 0                         |
200- | Added by:                          Expires: Never                     |
200- | Time On Today: 00:00               Last seen: Thu Apr 21 14:44:15 2005|
200- | Flags: 1                           Idle time: Disabled                |
200- | Ratio: 1:3                         Credits:       4.9 MB              |
200- | Total Logins: 2                    Current Logins: 1                  |
200- | Max Logins: 2                      From same IP: Unlimited            |
200- | Max Sim Uploads: Unlimited         Max Sim Downloads: Unlimited       |
200- | Max Upload Speed:     0.0 K/s      Max Download Speed:     0.0 K/s    |
200- | Times Nuked: 0                     Bytes Nuked:      0 MB             |
200- | Weekly Allotment:     0 MB         Messages Waiting: N                |
200- | Time Limit:    0 minutes.          (0 = Unlimited)                    |
200- | Tagline: Glftpd default user                                          |
200- | Groups:                                                               |
200- | Priv Groups:                                                          |
200- +-----------------------------------------------------------------------+
200- | IP0: *@127.0.0.1                   IP1: *@0.0.0.0                     |
200- | IP2:                               IP3:                               |
200- | IP4:                               IP5:                               |
200- | IP6:                               IP7:                               |
200- | IP8:                               IP9:                               |
200- +=======================================================================+
200 Command Successful.
ftp>   
```                                  
On the very same end You can see from which IP's You can log in using this account.To allow every ip enter *@*

Additionally You can see flag "1" mentioned above.

Description of all flags:
>         Flagname        Flag    Description
        -------------------------------------------------------------
        SITEOP          1       User is siteop.
        GADMIN          2       User is Groupadmin of one of his/her groups
                                (doesn't work for private groups).
        GLOCK           3       User cannot change group.
        EXEMPT          4       Allows to log in when site is full. Also allows
                                user to do "site idle 0", which is the same as
                                having the idler flag. Also exempts the user
                                from the sim_xfers limit in config file.
        COLOR           5       Enable/Disable the use of color (toggle with "site color").
        DELETED         6       User is deleted.
        USEREDIT        7       "Co-Siteop"
        ANON            8       User is anonymous (per-session like login).



Let receive information about existing users:
```
ftp> site users
```

Now we may create new user "test" with password "test" allowed to log in from any IP address

```
ftp> site adduser
200-  .-------------------------------------------------------.
200- | USAGE: SITE ADDUSER <username> <password> <IP#1 - 5>    |
200- |                                                         |
200- | <username> The username to add.                         |
200- | <password> The password to set for this user.           |
200- | <IP#1 - 5> Optional: Up to 5 ips may be specified here. |
200- |                                                         |
200- | After you add a user, use "SITE ADDIP" to add IP's to   |
200- | the new account.                                        |
200-  `-------------------------------------------------------'
200 Command Successful.
ftp> site adduser test test *@*
200- User created, now adding IPs...
200- IP '*@*' successfully added to test.
200-
200 User (test) successfully added.
ftp>                                       
```

Let's change some settings (it can download any one thing at the same time and it is FTP operator)

```
ftp> site change
200- -----------------------------------------------------------
200-    SITE CHANGE <username> <field> <value>
200-    SITE CHANGE { <user1> <user2> } <field> <value>
200-    SITE CHANGE =<group> <field> <value>
200-    SITE CHANGE * <field> <value>
200- -----------------------------------------------------------
200-
200-    Fields:  ratio
200-             sratio
200-             wkly_allotment [#,]#
200-             max_dlspeed
200-             max_ulspeed
200-             max_sim_down
200-             max_sim_up
200-             timeframe # #
200-             credits
200-             flags
200-             homedir
200-             idle_time
200-             startup_dir
200-             num_logins # [#]
200-             time_limit
200-             tagline
200-             comment
200-             expires [yyyy-mm-dd]
200- -----------------------------------------------------------
200 Command Successful.
ftp> site change test max_sim_down 1
200 Command Successful.
ftp> site change test flags +1
200 Command Successful.
ftp>
```

display this informations:

```
ftp> site user test
200- User Comment: Added by glftpd
200- +=======================================================================+
200- | Username: test                     Created: 04-21-05                  |
200- | Added by: glftpd                   Expires: Never                     |
200- | Time On Today: 00:00               Last seen: Thu Apr 21 14:52:41 2005|
200- | Flags: 13                          Idle time: Disabled                |
200- | Ratio: 1:3                         Credits:      14.6 MB              |
200- | Total Logins: 0                    Current Logins: 0                  |
200- | Max Logins: 2                      From same IP: Unlimited            |
200- | Max Sim Uploads: Unlimited         Max Sim Downloads: 1            |
200- | Max Upload Speed:     0.0 K/s      Max Download Speed:     0.0 K/s    |
200- | Times Nuked: 0                     Bytes Nuked:      0 MB             |
200- | Weekly Allotment:     0 MB         Messages Waiting: N                |
200- | Time Limit:    0 minutes.          (0 = Unlimited)                    |
200- | Tagline: No Tagline Set                                               |
200- | Groups:                                                               |
200- | Priv Groups:                                                          |
200- +-----------------------------------------------------------------------+
200- | IP0: *@*                           IP1:                               |
200- | IP2:                               IP3:                               |
200- | IP4:                               IP5:                               |
200- | IP6:                               IP7:                               |
200- | IP8:                               IP9:                               |
200- +=======================================================================+
200 Command Successful.
ftp>   
```         

Now, You can see flags "1" and "3" as well as restriction in d/l field


Lot of information You can find in file
/jail/glftpd/docs/glftpd.docs

In practise You may (it's up to You) chmod everything in */jail/glftpd/site* to 777 because server control access rights by itself. Otherwise You need to take care of this rights for server (reading, writing etc access)

If You wan't to share some directory located outside */jail/glftpd/site* (Do You remember > min_homedir /site ??) directory You can do it only like that:

mount --bind /source/directory/ /jail/glftpd/site/target/directory/

and add this entry for example to /etc/rc.local



serwer ma wiecej mozliwosci niz bedziemy kiedykolwiek potrzebowac....
All accesible commands You may receive after invoking command: 

```
ftp> SITE HELP
```

Good luck!



please forgive me my poor english.... :)




Added on 29/06/2007:
> **ajillusion said:**
> [B]Thanks  Sir_Yaro for the great tutorial 
i need some more help
i have followed your tutorial and installed successfully 
now all i want to know is how to make usergroups and its permission  [/B]

There is simple example in glftpd.conf already:
```
##############################################################################
##################     THE RIGHTS SECTION BEGINS HERE     ####################
##############################################################################
# (you can use a ! in front of any group/user/flag to negate it)             #
# The default is no, you don't need to add "!*" at the end                   #
#                                                                            #
# Function       Path                   =GROUP or -username or X (flag)      #
##############################################################################

upload          *                               -yaro -mac
resume          *                               *
makedir         *                               *
download        *                               *
dirlog          *                               *
rename          *                               1 =STAFF
filemove        *                               1 =STAFF
renameown       *                               *
nuke            *                               *
delete          *                               1
deleteown       *                               *

##############################################################################
###################     THE RIGHTS SECTION ENDS HERE     #####################
##############################################################################

```
This one might be altered a bit by me. Im not sure.
As u can see there is group STAFF which has 2 extra rights. People in this group can *rename* and move (*filemove*) file no matter where they are (***). U can add specific rights to different groups in a same way. Also u can limit access to this right/option to spacific path.
For example:
```
makedir         /path/to/directory                               *
```
Allow everyone to create directories (*makedir*) only in /path/to/directory .

Now u can login to ftp and create new group. 
By default it can be done only by glftpd user because he's the only one who has admin flag (*1*) set up:
```
ftp> site user glftpd
200- User Comment: glftpd
200- +=======================================================================+
200- | Username: glftpd                   Created: 0                         |
200- | Added by:                          Expires: Never                     |
200- | Time On Today: 00:00               Last seen: Fri Jun 29 14:11:55 2007|
200- | Flags: 15                          Idle time: Disabled                |
200- | Ratio: 1:3                         Credits:       4.9 MB              |
200- | Total Logins: 10                   Current Logins: 1                  |
200- | Max Logins: 2                      From same IP: Unlimited            |
200- | Max Sim Uploads: Unlimited         Max Sim Downloads: Unlimited       |
200- | Max Upload Speed:     0.0 K/s      Max Download Speed:     0.0 K/s    |
200- | Times Nuked: 0                     Bytes Nuked:      0 MB             |
200- | Weekly Allotment:     0 MB         Messages Waiting: N                |
200- | Time Limit:    0 minutes.          (0 = Unlimited)                    |
200- | Tagline: Glftpd default user                                          |
200- | Groups:                                                               |
200- | Priv Groups:                                                          |
200- +-----------------------------------------------------------------------+
200- | IP0: *@127.0.0.1                   IP1: *@*                           |
200- | IP2:                               IP3:                               |
200- | IP4:                               IP5:                               |
200- | IP6:                               IP7:                               |
200- | IP8:                               IP9:                               |
200- +=======================================================================+
200 Command Successful.
ftp>      
```                                                                  
and with this:
```
-groupcomment    1
-grpadd          1
-grpchange       1
```
located approximately at the end of glftpd.conf we can see that only users with admin flag has access to this comand. We can add this flag to specified other users:
```
site change USER flags +1
```
or just allow user with other flags to use this command (VERY BAD idea):
```
-grpadd          148
```

```
Flagname Flag Description
-------------------------------------------------------------
SITEOP 1 User is siteop.
GADMIN 2 User is Groupadmin of one of his/her groups
(doesn't work for private groups).
GLOCK 3 User cannot change group.
EXEMPT 4 Allows to log in when site is full. Also allows
user to do "site idle 0", which is the same as
having the idler flag. Also exempts the user
from the sim_xfers limit in config file.
COLOR 5 Enable/Disable the use of color (toggle with "site color").
DELETED 6 User is deleted.
USEREDIT 7 "Co-Siteop"
ANON 8 User is anonymous (per-session like login).

```

So to create new group u need access to GRPADD command. U can check if u have it with *site help *command:

```
230 User glftpd logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> site help
200- --=--------------------- Available SITE commands ---------------------=--
200-    TAGLINE: Change Your Tagline
200-       WKUP: Show Weektop Uploaders
200-       WKDN: Show Weektop Downloaders
200-       ALUP: Show Alltime Uploaders
200-       ALDN: Show Alltime Downloaders
200-       GPWK: Show Weektop Groups
200-  GPMONTHUP: Show Month Top Groups
200-       GPAL: Show Alltime Top Groups
200-       GPWD: Show Weektop Group Downloaders
200-  GPMONTHDN: Show Month Top Group Downloaders
200-       GPAD: Show Alltime Top Group Downloaders
200-      DAYUP: Today's Top Uploaders
200-      DAYDN: Today's Top Downloaders
200-    MONTHUP: Show MonthTop Uploaders
200-    MONTHDN: Show MonthTop Downloaders
200-    TRAFFIC: Show Site Traffic
200-    REQUEST: Make a Request
200-  REQFILLED: Mark a Request as Filled
200-    WELCOME: Show Welcome Message
200-      RULES: Show Site Rules
200-       USER: Show Users On Site (Type username to see users stats)
200-      NUKES: Show Nukes
200-    UNNUKES: Show UnNukes
200-       DUPE: Search Dupe Database
200-       TIME: Show Local Time
200-        NEW: Show Recent Dirs
200-      GROUP: Join/Leave Groups
200-       ONEL: Add/View Onliners
200-        MSG: Send a Message
200-        WHO: See who's online
200-      COLOR: Toggle Color
200-       SEEN: See when a user was last on
200-     LASTON: Display stats of last users online
200-     SEARCH: Locate a DIR on the site.
200-     PASSWD: Change Password
200-       VERS: Show Daemon Version
200-       STAT: Show Statline
200-       IDLE: Show Minimum and Maximum Idle Timeout
200-      GINFO: Detailed nfo of Groups
200-      USERS: List Users on Site
200-      DELIP: SITE DELIP <yourownusername> # (delete your own IP's)
200-      ADDIP: Add IP To a User
200-      DELIP: Delete an IP From a User
200-    ADDUSER: Add User
200-    DELUSER: Delete User
200-      READD: Readd Deleted User
200-     CHANGE: Change Field For a User
200-   GADDUSER: Add User and put him in a group
200-    RENUSER: Rename User
200-     CHPASS: Change Another User's Password

200-     GRPADD: Add group

200-     GRPDEL: Delete group
200-     GRPNFO: Change Group nfo
200-     GRPREN: Rename group
200-        GRP: Show extended group info
200-      CHGRP: Change a user's group
200-  GRPCHANGE: Change group settings
200-   CHGADMIN: Change the gadmin(s) for a group
200-     LOGINS: Login Log
200-     SYSLOG: Syslog Log of User Changes
200-     UPDATE: Update DirLog Database
200-      PURGE: Purge Deleted Users
200 Use "SITE HELP <command>" for syntax help.
ftp>                                   

```

So to add group *test *execute:
```
ftp> site grpadd test
200 Group (test) successfully added.
```
to move existing user to this group:
```
ftp> site CHGRP mac test
200- 'mac' has been successfully added to 'test'
200 Command Successful.
```
to create new user and put him in an existing group:
```
ftp> site GADDUSER test newuser password *@127.0.0.1
200- User created, now adding IPs...
200- IP '*@127.0.0.1' successfully added to newuser.
200-
200 User (newuser) successfully added to group test.
ftp>   
```

Also u can create description for a groups and mark some paths as private for specific users, flags or groups:

```
############################################################################
# Private Groups:   privgroup GROUPNAME GROUPDESC                          #
############################################################################
privgroup       STAFF            My[:space:]Private[:space:]Group

############################################################################
# PRIVPATHS:  Directories should be uniquely named (no wildcards)          #
############################################################################
privpath /site/admins_only      1
privpath /site/privatedir      1 =STAFF
privpath /site/privatedir2      1 =TEST
privpath /site/privatedir3      1 =STAFF -yaro -mac
privpath /site/privatedir4      1 =STAFF -yaro -mac =TEST


```
> plus how will my user will acess the ftp to upload or download the files 
is there any clients or any other way 
[http://ubuntuforums.org/showthread.php?t=351841](http://ubuntuforums.org/showthread.php?t=351841)
[http://en.wikipedia.org/wiki/List_of_FTP_clients](http://en.wikipedia.org/wiki/List_of_FTP_clients)

---

### Post by kakashi on 2005-11-08
well i have not read all of the guide or done anything on it cuz i am currently trying to create a fully documented compile of wine but i appreciate the effort you put into this work. keep it up. this type of stuff is why linux/ubuntu will rule the world one day.

---

### Post by Sir_Yaro on 2005-11-08
Actually it's one of my old how-tos originally wrote for mandrake linux... :P

---

### Post by Dany on 2005-11-11
Nice guide :)
I have a problem and that is that I can not log in on localhost...
I get this message  " ftp: connect: Connection refused "  and I have tried the install with and without tcpd enabled. Another strange thing was that on step 7(last  step)of the install guide it only takes about 10-20 seconds to make the DSA parameters.

1024 semi-random bytes loaded
Generating DSA parameters, 1024 bit long prime
This could take some time
...........+............................+..............+.+............+....+..................................+++++++++++++++++++++++++++++++++++++++++++++++++++*
.....+......+......+.....................................+.................................+....................+..............+++++++++++++++++++++++++++++++++++++++++++++++++++*
1024 semi-random bytes loaded
Generating DH parameters, 1024 bit long safe prime, generator 2
This is going to take a long time
.....................+.........................................................+...........................................................................................................................+.................+.........+...........+....................+..............+.................+......+..................+...........................................+...............................+............................................................................................................................................+..........................................+.........+...............................................................+............................................................................................................................................................................+..................................+..........................+..............+........................................................+...................................+....................................................+................................................................................+.................................................................................................++*++*++*
Generating DSA key, 1024 bits
Moving ftpd-dsa.pem to /jail/glftpd//etc . . . Done


And on step 8 I get another error:

8. STARTING GLFTPD:
-------------------

Copying /etc/resolv.conf to /jail/glftpd/etc/resolv.conf . . . Done.
Testing entries in resolv.conf (can take time):
   Testing 195.54.122.200 . . . OK.
   Testing 195.54.122.204 . . . OK.
   Testing 195.54.122.199 . . . OK.
   Testing 81.26.226.3 . . . OK.
Configuring inetd for glftpd . . . Done.
Restarting inetd . . . Failed! You must restart inetd before using glftpd.

Adding crontab entry to tabulate site stats nightly . . . Done.


And when I try and do the   nmap localhost|grep 21  command nothing happens.

Any suggestions what can be wrong?

---

### Post by majikstreet on 2005-11-11
Sir Yaro, you have to replace yaro with username. Otherwise people will just type yaro instead of their username! Or just tell them to replace yaro with their own username.

-m

Dany - what I just outlined is probably your problem.

---

### Post by Dany on 2005-11-11
[QUOTE=majikstreet]Sir Yaro, you have to replace yaro with username. Otherwise people will just type yaro instead of their username! Or just tell them to replace yaro with their own username.

-m

Dany - what I just outlined is probably your problem.[/QUOTE]
 
I searched for inetd in synaptic and installed this package : netkit-inetd  after that reinstalled glftpd again and I got starting inetd...sucess instead of failed, but still login doesn work.Then I tried to add the port after localhost when logging in on ftp and it worked :)

# ftp
ftp>o 127.0.0.1 port

---

### Post by Sir_Yaro on 2005-11-23
I've fixed this how-to. So, now it include solution for above mentioned problems.
btw. I'm very curious why there're problems with ident and ip on ubuntu.
Does anyone know how to fix it ?

---

### Post by Bald0z on 2006-02-07
I have the same problem!! Or even: I can login locally to my ftp, with either 127.0.0.1 or my real ip, but! All users that access my FTP fail the login, and this is what I see in login.log:

Users that tried to login were Bald0z, dade, glftpd
All seen as 0.0.0.0 !

```

Tue Feb  7 15:44:51 2006 [10669 ] LOGIN: <UNKNOWN>@0.0.0.0 (0.0.0.0) NONE "Bald0z" "NoGroup" "No Tagline Set"
Tue Feb  7 15:46:54 2006 [10712 ] LOGIN: <UNKNOWN>@0.0.0.0 (0.0.0.0) NONE "dade" "" "No Tagline Set"
Tue Feb  7 15:49:02 2006 [10757 ] LOGIN: <UNKNOWN>@0.0.0.0 (0.0.0.0) NONE "dade" "" "No Tagline Set"
Tue Feb  7 15:50:04 2006 [10712 ] LOGOUT: *@0.0.0.0 (0.0.0.0) "dade" "" "No Tagline Set"
Tue Feb  7 15:51:10 2006 [10817 ] LOGIN: <UNKNOWN>@0.0.0.0 (0.0.0.0) NONE "dade" "" "No Tagline Set"
Tue Feb  7 15:52:12 2006 [10757 ] LOGOUT: *@0.0.0.0 (0.0.0.0) "dade" "" "No Tagline Set"
Tue Feb  7 15:54:21 2006 [10817 ] LOGOUT: *@0.0.0.0 (0.0.0.0) "dade" "" "No Tagline Set"
Tue Feb  7 16:54:18 2006 [13383 ] LOGIN: <UNKNOWN>@0.0.0.0 (0.0.0.0) NONE "Bald0z" "NoGroup" "No Tagline Set"
Tue Feb  7 16:54:39 2006 [13383 ] LOGOUT: *@0.0.0.0 (0.0.0.0) "Bald0z" "NoGroup" "No Tagline Set"
Tue Feb  7 16:54:46 2006 [13390 ] LOGIN: <UNKNOWN>@0.0.0.0 (0.0.0.0) NONE "glftpd" "" "Glftpd default user"
Tue Feb  7 16:56:11 2006 [13390 ] LOGOUT: *@0.0.0.0 (0.0.0.0) "glftpd" "" "Glftpd default user"
Tue Feb  7 16:57:25 2006 [13425 ] jointklat: *@0.0.0.0 (0.0.0.0): Bad user@host.
Tue Feb  7 17:07:13 2006 [13580 ] jointklat: *@0.0.0.0 (0.0.0.0): Bad user@host.

```


HELP!!!

(I tried installing an ident server, as Ubuntu doesn't ship with one natively, but that didn't seem to solve the problem).

Thank you

---

### Post by EjeCt on 2006-03-17
I have installed glftpd.. But i have installed xinedt instead of inetd.. I 've got no problems whatsoever with ident.

EjeCt

---

### Post by Mickey1 on 2006-05-06
ERROR: Can't determine if you are using inetd or xinetd!
Please fix this problem and re-run the installation script

How do i fix this
Am rather new to linux still but am determined to make it work as windows is just starting to aggrevate me more and more

Cheers in advance and thank you for posting this nice tutorial :)

EDIT: Fixed this by installing xinetd

---

### Post by Jaykie on 2006-05-20
@Bald0z

It's not because of the ident server you are getting that kinda log files.
You need to disable IPV6 since glftpd doesn't support it.
Check this thread how to do it:
[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

I had the same problem and this helped.

Jaykie

---

### Post by r00tn00b on 2007-02-22
Well i followed the guide but when i want to connect i get connection refused and because i'm quite new to LNX i have no idea where to look ;(

Any help from other users would help.

thx in advance

---

### Post by Sir_Yaro on 2007-02-22
please show output of your console

---

### Post by r00tn00b on 2007-02-22
> **Sir_Yaro said:**
> please show output of your console

Well i may have find the problem.

Instead of using 127.0.0.1 i used localhost with port# and that worked , finaly hehe
Now i have another problem and that is that this comp is behind a router i wanted to connect from winxp to lnx but for some reason i can't .

The otherway around works perfect, i can connect to winxp serv-u without problems.

i also had dmz on in router, disabling that doesn't help also.

any suggestions?

thx for the quick respons btw

---

### Post by Sir_Yaro on 2007-02-24
did u try to switch between passive and active mode ?

---

### Post by Hochler on 2007-05-04
I'm getting a permission denied for every user except "glftpd" when trying to access a dir mounted with the "mount --bind" command. Any ideas?

---

### Post by Sir_Yaro on 2007-05-04
assuming your site is in /jail/glftpd/site exec:
```
sudo chmod -R o+r /jail/glftpd/site
```

and of course check "*THE RIGHTS SECTION*" in glftpd.conf

Main difference between common linux ftpd and glftpd is rights access managment.
With glftpd u can even set chmod 777 on a whole directory tree because you control access via glftpd config anyway.
Of course it might be beter idea to do it bit more secure way. But it will do.

Please read:
```
yaro@mediacenter:/jail/glftpd/docs$ ls -l glftpd.docs
-rw-r--r-- 1 root root 113794 2007-04-09 12:55 glftpd.docs
yaro@mediacenter:/jail/glftpd/docs$ 
```

---

### Post by Hochler on 2007-05-04
I tried *"sudo chmod -R o+r /jail/glftpd/site"* and it's still only accessible via the "glftpd" user. I also tried setting chmod 777 on the dir.

When you say *"check 'THE RIGHTS SECTION' in glftpd.conf"* do you mean that I should change the defaults? If so, to what?

Here's my Rights Section:
```

##############################################################################
##################     THE RIGHTS SECTION BEGINS HERE     ####################
##############################################################################
# (you can use a ! in front of any group/user/flag to negate it)             #
# The default is no, you don't need to add "!*" at the end                   #
#                                                                            #
# Function       Path                   =GROUP or -username or X (flag)      #
##############################################################################

upload          *                       	*
resume		*				*
makedir		*				*
download	*				*
dirlog		*				*
rename		*				1 =STAFF
filemove	*				1 =STAFF
renameown	*				*
nuke	        *				*
delete		*				1
deleteown	*				*

##############################################################################
###################     THE RIGHTS SECTION ENDS HERE     #####################
##############################################################################

```

---

### Post by Sir_Yaro on 2007-05-05
config is ok. I was afraid it was altered somehow.
please show me output of: 
```
mount|grep bind
```and
```
cat /etc/fstab
```
And eventualy if u don't mount this directory in fstab add command that you use to do it.

---

### Post by Hochler on 2007-05-05
```

$ mount|grep bind
/media/hda3/Downloads/jl on /jail/glftpd/site/justice_league type none (rw,bind)

```

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=aa3ef881-6e56-45e5-ad74-94fcad7bb01b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=44B4-6315  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=F2A49386A4934BCB /media/hda3     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=6335DAEA758E23A6 /media/hda4     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=ECD4C2BCD4C28872 /media/hdb1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=a178a85e-d265-4c51-a1b8-875c82e7e568 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Sir_Yaro on 2007-05-06
It might have something to do with ntfs partition... I hope not cause I can't help u with ntfs...

or just simple permision problem. :)
please show me:
```
ls -ld /media/hda3/Downloads/jl
ls -ld /jail/glftpd/site/justice_league
```

---

### Post by Hochler on 2007-05-06
It dont think it's NTFS, I also tried it on my FAT32 external hard drive and got the same problem.

```

$ ls -ld /media/hda3/Downloads/jl
drwxrwx--- 1 root plugdev 0 2007-05-05 15:48 /media/hda3/Downloads/jl

```

```

$ sudo ls -ld /jail/glftpd/site/justice_league
Password:
drwxrwx--- 1 root plugdev 0 2007-05-05 15:48 /jail/glftpd/site/justice_league

```

---

### Post by Sir_Yaro on 2007-05-07
```
sudo chmod 777 /media/hda3/Downloads/jl
sudo chmod 777 /jail/glftpd/site/justice_league
```
:)
that will do (i hope)

---

### Post by Hochler on 2007-05-07
Did that a whole bunch of times, nothing.

```

$ sudo chmod 777 /media/hda3/Downloads/jl
Password:
$ sudo chmod 777 /jail/glftpd/site/justice_league
$ ls -ld /media/hda3/Downloads/jl
drwxrwx--- 1 root plugdev 0 2007-05-05 15:48 /media/hda3/Downloads/jl
$ sudo ls -ld /jail/glftpd/site/justice_league
drwxrwx--- 1 root plugdev 0 2007-05-05 15:48 /jail/glftpd/site/justice_league

```

---

### Post by Sir_Yaro on 2007-05-07
That is most baffling thing I've ever seen...
I miss something obvious or this can't happened...

try to change group:
```
sudo chown root.glftpd /media/hda3/Downloads/jl
sudo chown root.glftpd /jail/glftpd/site/justice_league
sudo ls -ld /media/hda3/Downloads/jl
sudo ls -ld /jail/glftpd/site/justice_league
```

---

### Post by Hochler on 2007-05-08
Hm, well that changed the permissions for /jail/glftpd/site/justice_league/, but /media/hda3/Downloads/jl still refuses to change.

```

$ sudo chown root.glftpd /media/hda3/Downloads/jl
$ sudo chown root.glftpd /jail/glftpd/site/justice_league
$ sudo ls -ld /media/hda3/Downloads/jl
drwxrwx--- 1 root plugdev 0 2007-05-05 15:48 /media/hda3/Downloads/jl
$ sudo ls -ld /jail/glftpd/site/justice_league
drwxr-xr-x 2 root glftpd 4096 2007-05-04 17:27 /jail/glftpd/site/justice_league
$ sudo chmod 777 /jail/glftpd/site/justice_league/
$ sudo ls -ld /jail/glftpd/site/justice_league/
drwxrwxrwx 2 root glftpd 4096 2007-05-08 21:00 /jail/glftpd/site/justice_league/
$ sudo chmod 777 /media/hda3/Downloads/jl/
$ sudo ls -ld /media/hda3/Downloads/jl
drwxrwx--- 1 root plugdev 0 2007-05-08 21:11 /media/hda3/Downloads/jl

```

---

### Post by Sir_Yaro on 2007-05-09
That is 100% ntfs related problem. I've realised myselt that ntfs can't have permisions set like a native linux file systems. It just doens't support them. afaik ntfs has only **arhs** attributes.

I have not ntfs and windows on my box since like 5 years so I just forgot it. :D
I'm not sure how ntfs support works but I think your problem MIGHT be (and probably is) here (fstab):
```
UUID=F2A49386A4934BCB /media/hda3     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
```
> umask=007,
means new dirs and files will be created with permision 770 what is same as drwxrwx--- 
> gid=46 0
means only groups 46 and 0 has above mentioned rights. On my computers 46 is plugdev and zero is always root. If you have same groups this confirm my theory... :)

So I'd say first try to change 
```
gid=46 0 
```
to 
```
gid=46 0 glftpd_gid
```

```
yaro@mediacenter:~$ sudo cat /etc/group|grep ftpd
Password:
glftpd:x:1001:yaro
```
So in my case:
```
gid=46 0 1001
```
U might need use other gid to make it work. *users* group gid  will do probably better. Look:
```
yaro@mediacenter:~/test$ ls -l
drwxrwxrwx 2 dhcp users 4096 2007-05-09 13:36 user_yaro
yaro@mediacenter:~/test$ ls -l
drwxrwxrwx 2 syslog users 4096 2007-05-09 13:39 This_is_created_by_user_test
drwxrwxrwx 2 dhcp   users 4096 2007-05-09 13:36 This_is_created_by_user_yaro
yaro@mediacenter:~/test$   
```
glftpd use system uid's from 101 as it own and *users* group. So I think if you change access permisions according to my advises this should work.

Second thing what u can try is to change
umask=007 to umask=000 what gives (?) full permision to read, write nad execute to everybody, no matter what. So I don't really recomended that.


Anyway if that will fix your problem please tell me know what did you exactly do.

---

### Post by cewan on 2007-06-06
Thanks for a great tutorial, Yaro!

---

### Post by Sir_Yaro on 2007-06-13
> **cewan said:**
> Thanks for a great tutorial, Yaro!

You are very welcome :D

---

### Post by ajillusion on 2007-06-29
[B]Thanks  Sir_Yaro for the great tutorial 
i need some more help
My server is CentOs form Fdcserver 
i have followed your tutorial and installed successfully 
now all i want to know is how to make usergroups and its permission 
plus how will my user will acess the ftp to upload or download the files 
is there any clients or any other way  [/B]

---

### Post by Sir_Yaro on 2007-06-29
> **ajillusion said:**
> [B]Thanks  Sir_Yaro for the great tutorial 
i need some more help
My server is CentOs form Fdcserver 
i have followed your tutorial and installed successfully 
now all i want to know is how to make usergroups and its permission  [/B]

There is simple example in glftpd.conf already:
```
##############################################################################
##################     THE RIGHTS SECTION BEGINS HERE     ####################
##############################################################################
# (you can use a ! in front of any group/user/flag to negate it)             #
# The default is no, you don't need to add "!*" at the end                   #
#                                                                            #
# Function       Path                   =GROUP or -username or X (flag)      #
##############################################################################

upload          *                               -yaro -mac
resume          *                               *
makedir         *                               *
download        *                               *
dirlog          *                               *
rename          *                               1 =STAFF
filemove        *                               1 =STAFF
renameown       *                               *
nuke            *                               *
delete          *                               1
deleteown       *                               *

##############################################################################
###################     THE RIGHTS SECTION ENDS HERE     #####################
##############################################################################

```
This one might be altered a bit by me. Im not sure.
As u can see there is group STAFF which has 2 extra rights. People in this group can *rename* and move (*filemove*) file no matter where they are (***). U can add specific rights to different groups in a same way. Also u can limit access to this right/option to spacific path.
For example:
```
makedir         /path/to/directory                               *
```
Allow everyone to create directories (*makedir*) only in /path/to/directory .

Now u can login to ftp and create new group. 
By default it can be done only by glftpd user because he's the only one who has admin flag (*1*) set up:
```
ftp> site user glftpd
200- User Comment: glftpd
200- +=======================================================================+
200- | Username: glftpd                   Created: 0                         |
200- | Added by:                          Expires: Never                     |
200- | Time On Today: 00:00               Last seen: Fri Jun 29 14:11:55 2007|
200- | Flags: 15                          Idle time: Disabled                |
200- | Ratio: 1:3                         Credits:       4.9 MB              |
200- | Total Logins: 10                   Current Logins: 1                  |
200- | Max Logins: 2                      From same IP: Unlimited            |
200- | Max Sim Uploads: Unlimited         Max Sim Downloads: Unlimited       |
200- | Max Upload Speed:     0.0 K/s      Max Download Speed:     0.0 K/s    |
200- | Times Nuked: 0                     Bytes Nuked:      0 MB             |
200- | Weekly Allotment:     0 MB         Messages Waiting: N                |
200- | Time Limit:    0 minutes.          (0 = Unlimited)                    |
200- | Tagline: Glftpd default user                                          |
200- | Groups:                                                               |
200- | Priv Groups:                                                          |
200- +-----------------------------------------------------------------------+
200- | IP0: *@127.0.0.1                   IP1: *@*                           |
200- | IP2:                               IP3:                               |
200- | IP4:                               IP5:                               |
200- | IP6:                               IP7:                               |
200- | IP8:                               IP9:                               |
200- +=======================================================================+
200 Command Successful.
ftp>      
```                                                                  
and with this:
```
-groupcomment    1
-grpadd          1
-grpchange       1
```
located approximately at the end of glftpd.conf we can see that only users with admin flag has access to this comand. We can add this flag to specified other users:
```
site change USER flags +1
```
or just allow user with other flags to use this command (VERY BAD idea):
```
-grpadd          148
```

```
Flagname Flag Description
-------------------------------------------------------------
SITEOP 1 User is siteop.
GADMIN 2 User is Groupadmin of one of his/her groups
(doesn't work for private groups).
GLOCK 3 User cannot change group.
EXEMPT 4 Allows to log in when site is full. Also allows
user to do "site idle 0", which is the same as
having the idler flag. Also exempts the user
from the sim_xfers limit in config file.
COLOR 5 Enable/Disable the use of color (toggle with "site color").
DELETED 6 User is deleted.
USEREDIT 7 "Co-Siteop"
ANON 8 User is anonymous (per-session like login).

```

So to create new group u need access to GRPADD command. U can check if u have it with *site help *command:

```
230 User glftpd logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> site help
200- --=--------------------- Available SITE commands ---------------------=--
200-    TAGLINE: Change Your Tagline
200-       WKUP: Show Weektop Uploaders
200-       WKDN: Show Weektop Downloaders
200-       ALUP: Show Alltime Uploaders
200-       ALDN: Show Alltime Downloaders
200-       GPWK: Show Weektop Groups
200-  GPMONTHUP: Show Month Top Groups
200-       GPAL: Show Alltime Top Groups
200-       GPWD: Show Weektop Group Downloaders
200-  GPMONTHDN: Show Month Top Group Downloaders
200-       GPAD: Show Alltime Top Group Downloaders
200-      DAYUP: Today's Top Uploaders
200-      DAYDN: Today's Top Downloaders
200-    MONTHUP: Show MonthTop Uploaders
200-    MONTHDN: Show MonthTop Downloaders
200-    TRAFFIC: Show Site Traffic
200-    REQUEST: Make a Request
200-  REQFILLED: Mark a Request as Filled
200-    WELCOME: Show Welcome Message
200-      RULES: Show Site Rules
200-       USER: Show Users On Site (Type username to see users stats)
200-      NUKES: Show Nukes
200-    UNNUKES: Show UnNukes
200-       DUPE: Search Dupe Database
200-       TIME: Show Local Time
200-        NEW: Show Recent Dirs
200-      GROUP: Join/Leave Groups
200-       ONEL: Add/View Onliners
200-        MSG: Send a Message
200-        WHO: See who's online
200-      COLOR: Toggle Color
200-       SEEN: See when a user was last on
200-     LASTON: Display stats of last users online
200-     SEARCH: Locate a DIR on the site.
200-     PASSWD: Change Password
200-       VERS: Show Daemon Version
200-       STAT: Show Statline
200-       IDLE: Show Minimum and Maximum Idle Timeout
200-      GINFO: Detailed nfo of Groups
200-      USERS: List Users on Site
200-      DELIP: SITE DELIP <yourownusername> # (delete your own IP's)
200-      ADDIP: Add IP To a User
200-      DELIP: Delete an IP From a User
200-    ADDUSER: Add User
200-    DELUSER: Delete User
200-      READD: Readd Deleted User
200-     CHANGE: Change Field For a User
200-   GADDUSER: Add User and put him in a group
200-    RENUSER: Rename User
200-     CHPASS: Change Another User's Password

200-     GRPADD: Add group

200-     GRPDEL: Delete group
200-     GRPNFO: Change Group nfo
200-     GRPREN: Rename group
200-        GRP: Show extended group info
200-      CHGRP: Change a user's group
200-  GRPCHANGE: Change group settings
200-   CHGADMIN: Change the gadmin(s) for a group
200-     LOGINS: Login Log
200-     SYSLOG: Syslog Log of User Changes
200-     UPDATE: Update DirLog Database
200-      PURGE: Purge Deleted Users
200 Use "SITE HELP <command>" for syntax help.
ftp>                                   

```

So to add group *test *execute:
```
ftp> site grpadd test
200 Group (test) successfully added.
```
to move existing user to this group:
```
ftp> site CHGRP mac test
200- 'mac' has been successfully added to 'test'
200 Command Successful.
```
to create new user and put him in an existing group:
```
ftp> site GADDUSER test newuser password *@127.0.0.1
200- User created, now adding IPs...
200- IP '*@127.0.0.1' successfully added to newuser.
200-
200 User (newuser) successfully added to group test.
ftp>   
```

Also u can create description for a groups and mark some paths as private for specific users, flags or groups:

```
############################################################################
# Private Groups:   privgroup GROUPNAME GROUPDESC                          #
############################################################################
privgroup       STAFF            My[:space:]Private[:space:]Group

############################################################################
# PRIVPATHS:  Directories should be uniquely named (no wildcards)          #
############################################################################
privpath /site/admins_only      1
privpath /site/privatedir      1 =STAFF
privpath /site/privatedir2      1 =TEST
privpath /site/privatedir3      1 =STAFF -yaro -mac
privpath /site/privatedir4      1 =STAFF -yaro -mac =TEST


```
> plus how will my user will acess the ftp to upload or download the files 
is there any clients or any other way 
[http://ubuntuforums.org/showthread.php?t=351841](http://ubuntuforums.org/showthread.php?t=351841)
[http://en.wikipedia.org/wiki/List_of_FTP_clients](http://en.wikipedia.org/wiki/List_of_FTP_clients)

---

### Post by ajillusion on 2007-06-29
Thanks For the Quick Reply Sir_ Yaro Bro 
I have never used Linux but i tryed till my last breath i would like some live help 
if possible ! 

wanna change the root path 

My Ip is on 127.0.0.1 but wanted to change it my server ip 
plus i wanna make Four  Groups Admin Mods 

Usergroups 
Admin  - Upload / Download / Edit/ Move/ Delete
Mods - Upload / Download / Edit / Move 
User 1 -  Download Max 3Gb Per day Per user  / No upload / No edit / No Move / No delete 
User 2 -  Download Max 6Gb Per day Per user  / No upload / No edit / No Move / No delete
User 2 -  Download Max 10Gb Per day Per user  / No upload / No edit / No Move / No delete  

--------------------------- 
I Would be happy if you give me live help

---

### Post by Sir_Yaro on 2007-06-29
> **ajillusion said:**
> Thanks For the Quick Reply Sir_ Yaro Bro 
I have never used Linux but i tryed till my last breath i would like some live help 
if possible ! 

wanna change the root path 

My Ip is on 127.0.0.1 but wanted to change it my server ip 
plus i wanna make Four  Groups Admin Mods 

Usergroups 
Admin  - Upload / Download / Edit/ Move/ Delete
Mods - Upload / Download / Edit / Move 
User 1 -  Download Max 3Gb Per day Per user  / No upload / No edit / No Move / No delete 
User 2 -  Download Max 6Gb Per day Per user  / No upload / No edit / No Move / No delete
User 2 -  Download Max 10Gb Per day Per user  / No upload / No edit / No Move / No delete  

--------------------------- 
I Would be happy if you give me live help

I dont really know what do u mean.
IP is something what u get from your provider and usually u can't change it. Beside that 127.0.0.1 is so called loop address which always point at yourself and generally is useless for user.
U can check ur network card ip address with:
```
 ifconfig |grep Bcas
```
and ur public ip address at:
[http://whatismyip.com/](http://whatismyip.com/)


And I dont really undestand second part about groups. What do u mean exactly? **And what did u do already?**

---

### Post by dn* on 2007-07-28
> **Sir_Yaro said:**
> That is 100% ntfs related problem. I've realised myselt that ntfs can't have permisions set like a native linux file systems. It just doens't support them. afaik ntfs has only **arhs** attributes.

I have not ntfs and windows on my box since like 5 years so I just forgot it. :D
I'm not sure how ntfs support works but I think your problem MIGHT be (and probably is) here (fstab):
```
UUID=F2A49386A4934BCB /media/hda3     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
```

means new dirs and files will be created with permision 770 what is same as drwxrwx--- 

means only groups 46 and 0 has above mentioned rights. On my computers 46 is plugdev and zero is always root. If you have same groups this confirm my theory... :)

So I'd say first try to change 
```
gid=46 0 
```
to 
```
gid=46 0 glftpd_gid
```

```
yaro@mediacenter:~$ sudo cat /etc/group|grep ftpd
Password:
glftpd:x:1001:yaro
```
So in my case:
```
gid=46 0 1001
```
U might need use other gid to make it work. *users* group gid  will do probably better. Look:
```
yaro@mediacenter:~/test$ ls -l
drwxrwxrwx 2 dhcp users 4096 2007-05-09 13:36 user_yaro
yaro@mediacenter:~/test$ ls -l
drwxrwxrwx 2 syslog users 4096 2007-05-09 13:39 This_is_created_by_user_test
drwxrwxrwx 2 dhcp   users 4096 2007-05-09 13:36 This_is_created_by_user_yaro
yaro@mediacenter:~/test$   
```
glftpd use system uid's from 101 as it own and *users* group. So I think if you change access permisions according to my advises this should work.

Second thing what u can try is to change
umask=007 to umask=000 what gives (?) full permision to read, write nad execute to everybody, no matter what. So I don't really recomended that.


Anyway if that will fix your problem please tell me know what did you exactly do.

Hey, are you aware if this issue was ever resolved? I'm pretty certain that I was able to mount my ntfs drive on my old installation of ubuntu, but I'm having exactly the same issue as mentioned here now. Before I tried your mount --bind idea, I was fiddling about with symlinks.. is that a possible solution? Thanks

---

### Post by Sir_Yaro on 2007-07-28
I'll check that for you tomorrow. But I'm quite sure it will works without problems. :)

---

### Post by dn* on 2007-07-28
> **Sir_Yaro said:**
> I'll check that for you tomorrow. But I'm quite sure it will works without problems. :)

changing the umask entry of my ntfs drive to 022 appears to be the solution (coupled with some chmod and chown'ing)

---

### Post by Sir_Yaro on 2007-07-28
> **dn* said:**
> changing the umask entry of my ntfs drive to 022 appears to be the solution (coupled with some chmod and chown'ing)

great!! That's mean I'm off tomorrow! :D :lolflag:

---

### Post by Jenga201 on 2007-08-06
First of all, great guide.  It's giving me a nice introduction to linux in general.

I'm running ubuntu 6.06 server in windows with vmware.

I've been able to follow your guide up until i have to login to the ftp server for the first time.

I have flashfxp set to connect via Auth TLS, and i have secure filie listing and secure file transfers enabled, but i still get this error:

[R] USER glftpd
[R] 530-You must connect to this server using SSL/TLS.
[R] 530-
[R] 530-FlashFXP Directions: goto the SSL tab in Site Manager
[R] 530-and select AUTH TLS and then make sure the Secure File
[R] 530-Listings and Secure File Transfers boxes are checked.
[R] 530 Login failed: Your user class requires you to use secure connections.
[R] Connection failed

I've tried resetting the certificate , but nothing i seem to do works for me.

Also one other problem i had...
With this step:
nmap localhost|grep 555
555/tcp  open  ftp

(my ftp is actually listening on port 555)

I get:
555/tcp open dsf

Any help with this would be appreciated

---

### Post by Sir_Yaro on 2007-08-07
Check if marked "Auth TLS" along with "secure file listing" and "sec. file transfer" on SSL tab.

And if that's a first/initial login you MUST login from the very same host where glftpd is running (in other words from a localhost to localhost). I guess you try to login from windows host to linux on VM - it won't work. Unless u edit */jail/glftpd/ftp-data/users/glftpd* file and add *IP *@** on the very end. BUT I DON'T RECOMMEND IT. is much better to create new user account or add only one ip address.

---

### Post by Jenga201 on 2007-08-07
yeah, the whole problem was that i was trying to use flashfxp in windows...i just used ftp 127.0.0.1 555  and it worked fine.

Thanks for your help

---

### Post by Jenga201 on 2007-08-07
I know this is off topic, but i'm wondering if you could suggest a good torrent client as well as a proxy server that works well with ubuntu 6.06 server.

I see lots of stuff about torrent clients but it all seems to be on the desktop edition, and i only see something about psybnc which is apparently old.

Thanks ^^

EDIT: Answered my own questions, thanks ^^

rtorrent works very well.

---

### Post by Jenga201 on 2007-08-14
i have one more quesiton...how do you get the zipscript to work?

---

### Post by Sir_Yaro on 2007-08-15
> **Jenga201 said:**
> i have one more quesiton...how do you get the zipscript to work?

take a look at this three lines in ***glftpd.conf*** :
```
#pre_dir_check  /bin/dirscript
#pre_check      /bin/dupescript
#post_check     /bin/zipscript
```
first u have to uncomment appropriate line then configure script (if it's configurable). But I advice u to use other zipscript than original one.

These is a good explanation of this lines in ***/jail/glftpd/docs/glftpd.docs***

---

### Post by rabban on 2007-08-15
I have installed glftpd following your guide and the glftpd doc. Great guide, made it a lot easier. I do a few questions though:

1) to secure the /jail/glftpd files, what read/write/execute settings should I use? root is owner of all files accept /site.

2) I struggle with file and directory acess control of /site. How do I give glftpd control over who has access to what? Currently I have a user as owner of files and direcotry with 755 control accept /site/upload (777). Admin user in glftpd cannot write to any catalog beside /site/upload even though I specify that admin can write to all /site catalogs in glftpd.conf

3)I have a problem with uploading files containing none ascii letter. You what settings I need to change for glftpd to accept filename with lettes such as: æ, ø , å?

---

### Post by Sir_Yaro on 2007-08-15
> **rabban said:**
> I have installed glftpd following your guide and the glftpd doc. Great guide, made it a lot easier. I do a few questions though:

1) to secure the /jail/glftpd files, what read/write/execute settings should I use? root is owner of all files accept /site.There are a two ways that i know about. 
[LIST]
[*]chmod -R 777 on whole /site tree and let glftpd fully manage directory access. That is default way, I think. But if security is ur concern u have to well thought out how to limit access to the /site directory. It seems to be very easy task to do (700 on /jail/glftpd and change name of /site directory).
[*]or play with groups and give full access only to some specific group related to glftpd.
[/LIST]

> 
2) I struggle with file and directory acess control of /site. How do I give glftpd control over who has access to what? Currently I have a user as owner of files and direcotry with 755 control accept /site/upload (777). Admin user in glftpd cannot write to any catalog beside /site/upload even though I specify that admin can write to all /site catalogs in glftpd.conf
Access control works on two levels.  First is glftpd. It may allowed you to write or read something, or not. It depend on ***glftpd.conf*** entries in rights section (*THE RIGHTS SECTION BEGINS HERE*). Second level is system access control. And here is a tricky part. Every ftp user has it's own UID and those id's has same value like some system id's.
Compare */etc/passwd* and */jail/glftpd/etc/passwd*.
/etc/passwd:
> dhcp: x:**100**:101::/nonexistent:/bin/false
syslog: x:**101**:102::/home/syslog:/bin/false
klog: x:**102**:103::/home/klog:/bin/false

/jail/glftpd/etc/passwd:
> glftpd: xxxxxxx:0:0:0:/site:/bin/false
yaro: xxxxxx:**100**:100:04-09-07:/site:/bin/false
test: xxxxx:**101**:100:05-09-07:/site:/bin/false
gosc: xxxxx:**102**:100:05-25-07:/site:/bin/false

So is easy to draw a conclusion. If for example system account ***syslog*** has right to do (or not) something same right apply to glftpd user ***test***.

That's why using 777 on whole /site tree is not so bad on a very beging. It will limit right problem to minimum.
I'm not sure if I answer for your question... :P

> 3)I have a problem with uploading files containing none ascii letter. You what settings I need to change for glftpd to accept filename with lettes such as: æ, ø , å?
Oh. So u belong to those "lucky devils" with non-latin letters... Same as me... But i never had any issues with polish letters (&#281;ó&#261;&#347;&#322;&#380;&#378;&#263;&#324;)... 
I've copy/paste above mentioned letters as name of new file and transfer failed. :confused: I can only guess that it has something to do with locales. Does both sides (client and server) use the same code page ?
(few minutes later)
I've changed ftp client from FlashFXP to Gftp and i've trensfered file without problems. Try it... :)

---

### Post by rabban on 2007-08-15
Thank you for a quick answer

I'll have to play around with some settings on each of my of my 3 qestions and see what works. The FTP client I used, was the WindowsCommander (Toal Commander) buildin one. I'll give a more comprehensive client a try.

Rabban

---

### Post by trashmirror on 2007-09-16
thanks for your nice how to

but i have a problem with glftpd resolving ident and ip adresses from any user who want's to connect:
530 "*@0.0.0.0" is not valid for the account specified.

so i cant add any ip range etc. i have to set IP *@* that the user is able to connect ... it seems so that glftpd cant get the ident and ip adresses from users... 

would be nice if you could help me


thanks in advancd

---

### Post by Sir_Yaro on 2007-09-17
First thing first.
Connect to ftp from the VERY SAME pc that runs glftpd. Then input new ip or create account (or do it manually in /jail/glftpd/ftp-data/users/ ). At the very begining only 127.0.0.1 is allowed to connect.

---

### Post by trashmirror on 2007-09-17
i think i solved the problem.... IPV6 was enabled :(

but cant test it right now... having kernel problems...


thanks so far...

---

### Post by ricadelic on 2007-10-02
Thx for the great guide and the superb support!

i also had to set the mask for the NTFS disk to 022 to get it working.

---

### Post by dnathe4th on 2008-01-17
Sorry if this is digging up an old post, but I'm still having trouble.
I'm still trying to connect from 127.0.0.1 but I'm getting Connection Refused, whether I specify the port I have it set to or not.  From what I understand this doesn't mean there's a problem with the install, so where should I look to to try and straighten this out?
Thanks

---

### Post by Sir_Yaro on 2008-02-13
check my first post. section about /jail/glftpd/ftp-data/users/glftpd file

---

### Post by lible on 2008-03-05
Always seem to get error

Restarting inetd . . . Failed! You must restart inetd before using glftpd.

i tried with xnetd and rlinetd installed both give me the same errors.

Also the sudo apt-get install inetd no longer works... 

Also tried /etc/init.d/xinetd restart

Update:
got the /etc/init.d/xinetd restart to finally work

any help in resolving this problem would greatly be appreciated

im currently at 

:/tmp/glftpd-LNX_2.01$  nmap localhost|grep 21
21/tcp  open  ftp

without problems but cannot access 

sudo mcedit /jail/glftpd.conf
sudo: mcedit: command not found?????

Update 2: installed midnight commander mc under synapse and now and able to edit .conf

Sorry i guess i should have searched more before posting. Anyhow maybe someone can learn from my mistakes. :)

---

### Post by Lama on 2008-10-20
Spend a few hours figuring this out...
glftpd is a i386 precompiled binary. If you want to run it on AMD64 ubuntu, be sure to do a
```
apt-get install ia32-libs
```
or xinetd will not be able to run the binary, and you will get 421 errors!

---

### Post by cwfs on 2009-01-04
i have glftpd running but i would like to know how i can lock my users to a directory for an example  user1 home directory should be ftp/1  and user2 should be ftp/2   i have set this up in each users userfile but what happends is the user can go back directories to the sites home directory and i don't want this how can i prevent this issue ?

---

### Post by denethon4414 on 2009-01-04
~~nvm~~solved

---

### Post by cwfs on 2009-01-06
i am wanting to remove glftpd since i made the mistake of installing it into jail (how do i do this), i will reinstall into a non jail setup because jail has serious issues with scripts.

---

### Post by Xaitra on 2009-02-11
Have big problems with NTFS and glftpd. 
Tried every advice i could found here and alot of googling but cant get it to work. 

The problem is that users can upload to glftpd as i want and it goes directly into the NTFS drive, but glftpd is the owner of every file that is uploaded to the ftp. 

If we say a user called  hult and is in group iND upload a file to the ftp i want hult to be the owner and group iND. 
Right now glftpd is owner / group to all uploaded files. 

fstab line: 
```
/dev/sdd1 /media/hd-ntfs ntfs-3g defaults,nls=utf8,umask=022,gid=46 0 1001
```
I have tried umask=000 but no difference.

rc.local line: 
```
mount -t ntfs-3g /dev/sdc1 /media/hd-ntfs
``` 

```
sudo cat /etc/group | grep glftpd
glftpd:x:1001:robhol
```

46 = plugdev 
0 = root 

permissions:
```
root@robin-laptop:/media# ls -l
total 20
lrwxrwxrwx 1 root root    6 2009-02-09 01:48 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-02-09 01:48 cdrom0 
drwxrwxrwx 1 root root 8192 2009-02-12 00:13 EXTERNAL
drwxrwxrwx 1 root root 8192 2009-02-12 00:13 hd-ntfs

root@robin-laptop:/jail/glftpd# ls -l
drwsrwxrwx  9 root root   4096 2009-02-12 00:29 site

root@robin-laptop:/jail/glftpd/site# ls -l
drwxrwxrwx 1 root root 4096 2009-02-12 02:59 test

root@robin-laptop:/jail/glftpd/site/Xbox360# ls -l
-rwxrwxrwx 1 root root 100000000 2009-02-12 02:59 testfile.r04

```

Same owner and group in hd-ntfs as in /jail/glftpd/site

testfile.r04 I uploaded with user hult.  
In FTP program glftpd is the owner of testfile.r04 so hult cant delete the file he just uploaded when he isn't the owner.

right now I'm lost and tierd have tried to fix this 3 nights in a row now but cant get it to work.  If hult upload a file to /jail/glftpd/site  he is the owner to the file he upload and therefor delete as i want but not at the ntfs drive.

---

### Post by ushere on 2012-05-25
hi guys, nice guide!
I want to hide any owner of folders and files to groups and flags, is it possible? many thanks, bye

---

