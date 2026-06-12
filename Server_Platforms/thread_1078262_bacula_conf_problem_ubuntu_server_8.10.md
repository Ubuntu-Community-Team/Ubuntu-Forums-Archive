---
title: "bacula conf problem ubuntu server 8.10"
date: 2009-02-23
forum: Server Platforms
---

### Post by emmanuel de clercq on 2009-02-23
hi,

I recieve following message when i start Bacula backup via webmin.

"The Bacula console command /usr/bin/bconsole could not communicate with the Bacula director. Make sure the password in /etc/bacula/bconsole.conf is correct."


This are the config files:


#
# Default Bacula Director Configuration file
#
#  The only thing that MUST be changed is to add one or more
#   file or directory names in the Include directive of the
#   FileSet resource.
#
#  For Bacula release 2.4.2 (26 July 2008) -- debian lenny/sid
#
#  You might also want to change the default email address
#   from root to your address.  See the "mail" and "operator"
#   directives in the Messages resource.
#

Director {                            # define myself
  Name = ubuntu-dir
  DIRport = 9101
  QueryFile = "/etc/bacula/scripts/query.sql"
  WorkingDirectory = /var/lib/bacula
  PidDirectory = "/var/run/bacula"
  Maximum Concurrent Jobs = 1
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"         # Console password
  Messages = Daemon
  DirAddress = 192.168.0.5
}

and

#
# Bacula User Agent (or Console) Configuration File
#

Director {
  Name = ubuntu-dir
  DIRport = 9101
  Address = 192.168.0.5
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"
}


Any idea what could be the problem?

---

### Post by clanroot on 2009-04-14
I'm having the same issue as above. Does anyone have any thoughts on this matter?

---

### Post by clanroot on 2009-04-15
After hunting down a few suggestions on how to fix this that didn't work on their own, I decided to combine a few of them.

What ended up working was this --

In the director configuration file (for me /etc/bacula/bacula-dir.conf) I changed the following...

In the Directory declaration:
I set the PidDirectory to match the WorkingDirectory.
I removed/commented the DirAddress, because it's superfluous for simple setups.

In the Catalog declaration (toward the end of the file):
I set dbpassword to match my bacula dbuser password -- this attribute defaults to a null string, without this edit the Director would only be able to connect to the db if your bacula bduser happened to have no password. This is probably the main cause of initial problems.

```

---
Director {
  Name = servername-dir
  DIRport = 9101
  QueryFile = "/etc/bacula/scripts/query.sql"
  WorkingDirectory = "/var/lib/bacula"
  PidDirectory = "/var/lib/bacula"
  Maximum Concurrent Jobs = 1
  Password = "Cv70F6pf1t6pBopT4vQOnigDr0v3L" #Console password
  Messages = Daemon
  #DirAddress = 127.0.0.1
}

---
Catalog {
  Name = MyCatalog
  dbname = "bacula"; dbuser = "bacula"; dbpassword = "mypassword"
}

```


Hope this helps.

---

### Post by DeLaNooch on 2010-02-02
Old thread, but not many helpful Bacula resources out there for this specific issue. For reference sake...

I received similar error to emmanuel de clercq when attempting to connect bconsole on an Ubuntu 9.04 client to my Redhat 4.1.2 Bacula server. 

Based on clanroot's advice, I only modified the Catalog declaration in bacula-dir.conf, changing the null string to the password console string I used in both the bacula-dir.conf and bacula-sd.conf. 

Fixed problem instantly!

---

### Post by John Morris on 2011-02-24
Great info -- and gave me the clue to solve my own situation. I have been wanting to try Bacula for a mixed XP/Ubuntu LAN, and everything seems set up appropriately, including MySQL, Webmin, PHPmyAdmin, Bacula etc. etc. And I have been unable to run any version of the console (bconsole, BAT etc.). But then with Webmin and the information above (I had exactly the same message, delivered from Webmin), it crossed my mind that there might be a password issue on the catalogue file.
 
SYMPTOMS: The BAT console would not work -- after about 5 seconds, it would "fade to gray (or "grey"). The bacula-dir service would stop after trying the BAT. Then Webmin indicated the message. Bconsole would not work.
 
SETUP: Otherwise, this was a completely vanilla setup directly from Synaptic -- no makes or builds.
 
FIX: It was in fact a pw problem in the Catalogue entry of the bacula-dir.conf file -- but not a null password, but the pw for the dbuser. Somehow in multiple installs, I had lost track of the bacula pw for MySQL.
 
RESULT: Now Webmin can start and stop the Bacula services, and the BAT console works fine. And I can go ahead and start using Bacula at last.
 
ENVIRONMENT: Ubuntu 10.10
 
Thanks for the tips!

---

### Post by OldManRiver on 2011-03-29
> **clanroot said:**
> ```

---
Director {
Catalog {
  Name = MyCatalog
  dbname = "bacula"; dbuser = "bacula"; dbpassword = "mypassword"
}

```

What I found on my situation is that the special characters I use in "mypassword" for mysql were not saving in this section of the Director file.

Now I see no error in WebMin but have:

Process statuses: Bacula Director daemon - Up  |  Storage daemon - Down  |  File daemon - Up

So ran/etc/init.d/bacula-sd start to find errors and got none.  Rechecking status again.  Found I had to stop to get it working right.  Appears the start sequence was off.

So ran my job and got these job errors:
> Starting backup job Immediate ..

Automatically selected Catalog: MyCatalog
Using Catalog "MyCatalog"
A job name must be specified.
The defined Job resources are:
     1: Daily
     2: BackupCatalog
     3: RestoreFiles
     4: Immediate
Select Job resource (1-4): 4
Run Backup job
JobName:  Immediate
Level:    Incremental
Client:   ro-server-dfw-fd
FileSet:  Net Comps
Pool:     Default (From Job resource)
Storage:  File (From Job resource)
When:     2011-03-29 21:19:43
Priority: 10
OK to run? (yes/mod/no):

.. the backup job is now running. When complete, the results will be shown below ..

 yes
Job queued. JobId=2
You have messages.
messages
29-Mar 21:19 ro-server-dfw-dir JobId 2: No prior Full backup Job record found.
29-Mar 21:19 ro-server-dfw-dir JobId 2: No prior or suitable Full backup found in catalog. Doing FULL backup.
29-Mar 21:19 ro-server-dfw-dir JobId 2: Start Backup JobId 2, Job=Immediate.2011-03-29_21.19.43.13
29-Mar 21:19 ro-server-dfw-sd JobId 2: Error: dev.c:121 Unable to stat device /nonexistant/path/to/file/archive/dir: ERR=No such file or directory
29-Mar 21:19 ro-server-dfw-sd JobId 2: Warning: 
     Device "FileStorage" requested by DIR could not be opened or does not exist.
29-Mar 21:19 ro-server-dfw-sd JobId 2: Error: dev.c:121 Unable to stat device /nonexistant/path/to/file/archive/dir: ERR=No such file or directory
29-Mar 21:19 ro-server-dfw-sd JobId 2: Warning: 
     Device "FileStorage" requested by DIR could not be opened or does not exist.
29-Mar 21:19 ro-server-dfw-sd JobId 2: Error: dev.c:121 Unable to stat device /nonexistant/path/to/file/archive/dir: ERR=No such file or directory
29-Mar 21:19 ro-server-dfw-sd JobId 2: Warning: 
     Device "FileStorage" requested by DIR could not be opened or does not exist.
29-Mar 21:19 ro-server-dfw-sd JobId 2: Failed command: Jmsg Job=Immediate.2011-03-29_21.19.43.13 type=5 level=1301451585 ro-server-dfw-sd JobId 2: Warning: 
     Device "FileStorage" requested by DIR could not be opened or does not exist.

29-Mar 21:19 ro-server-dfw-sd JobId 2: Fatal error: 
     Device "FileStorage" with MediaType "File" requested by DIR not found in SD Device resources.
29-Mar 21:19 ro-server-dfw-dir JobId 2: Fatal error: 
     Storage daemon didn't accept Device "FileStorage" because:
     3924 Device "FileStorage" not in SD Device resources.
29-Mar 21:19 ro-server-dfw-dir JobId 2: Error: Bacula ro-server-dfw-dir 2.4.4 (28Dec08): 29-Mar-2011 21:19:45
  Build OS:               i486-pc-linux-gnu debian 5.0
  JobId:                  2
  Job:                    Immediate.2011-03-29_21.19.43.13
  Backup Level:           Full (upgraded from Incremental)
  Client:                 "ro-server-dfw-fd" 
  FileSet:                "Net Comps" 2011-03-29 21:17:53
  Pool:                   "Default" (From Job resource)
  Storage:                "File" (From Job resource)
  Scheduled time:         29-Mar-2011 21:19:43
  Start time:             29-Mar-2011 21:19:45
  End time:               29-Mar-2011 21:19:45
  Elapsed time:           0 secs
  Priority:               10
  FD Files Written:       0
  SD Files Written:       0
  FD Bytes Written:       0 (0 B)
  SD Bytes Written:       0 (0 B)
  Rate:                   0.0 KB/s
  Software Compression:   None
  VSS:                    no
  Storage Encryption:     no
  Volume name(s):         
  Volume Session Id:      2
  Volume Session Time:    1301451448
  Last Volume Bytes:      0 (0 B)
  Non-fatal FD errors:    0
  SD Errors:              0
  FD termination status:  
  SD termination status:  
  Termination:            *** Backup Error ***


.. the backup did not complete successfully. Check the error message above for details.

Any suggestion on what to do now?  This I have no clue on.

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-30
All,

Figured out the "/nonexistant/path/to/file/archive/dir" needed to be an actual dir, so created a backup dir, edited the .conf files accordingly and then looked in WebMin, which still had this value, so put in the right value and now the processing on the backup is running, but still monitoring to see that it goes right.

Cheers!

OMR

---

### Post by brenti on 2011-11-11
I am receiving the aforementioned error.

After looking at the log files for bacula, I've discovered that my problem lies with the MySQL server (I think).  Because I am new at this I ask first for patience, and second for help.

Here is the error:

[B][I][INDENT]11-Nov 10:20 bacula-dir JobId 0: Fatal error: Could not open Catalog "MyCatalog", database "bacula;".
11-Nov 10:20 bacula-dir JobId 0: Fatal error: mysql.c:194 Unable to connect to MySQL server.
Database=bacula; User=bacula
MySQL connect failed either server not running or your authorization is incorrect.
11-Nov 10:20 bacula-dir ERROR TERMINATION
Please correct configuration file: /etc/bacula/bacula-dir.conf[/INDENT][/I][/B]

Can anyone let me know how to create the database properly, and also create the catalog? Any help is appreciated.  Also, I have verified that the MySQL server is running.

Thanks!
Brent

*EDIT*
I am using Webmin with modules for MySQL and for Bacula. Just FYI.

---

### Post by Habitual on 2011-11-11
bacula-dir.conf credentials for db privs...

Terminal > 
```

grep dbname /etc/bacula/bacula-dir.conf -n 

```
-n is the line number
then ```
vi +n /etc/bacula/bacula-dir.conf
```

and adjust to match the bacula db|user|host|password access credentials.

HTH.
Subscribed with interest.

---

### Post by brenti on 2011-11-15
> **Habitual said:**
> bacula-dir.conf credentials for db privs...

Terminal > 
```

grep dbname /etc/bacula/bacula-dir.conf -n 

```
-n is the line number
then ```
vi +n /etc/bacula/bacula-dir.conf
```

and adjust to match the bacula db|user|host|password access credentials.

HTH.
Subscribed with interest.

Not sure how this will help.  I have already verified that the credentials are correct.

Thanks for the response.

Brent

---

### Post by Habitual on 2011-11-15
can you post (sanitize the password) the output of 

terminal > 
```
grep dbname /etc/bacula/bacula-dir.conf -n
```?

---

### Post by brenti on 2011-11-15
Here's is the output of the command:

**[INDENT]236:  dbname = "bacula;" DB Address = "localhost"; dbuser = "bacula"; dbpassword = "mypassword"[/INDENT]**

Thanks
Brent

---

### Post by Habitual on 2011-11-15
and mine for comparison from my bacula host:
```
dbname = bacula; DB Address = "localhost"; user = bacula; password = "mypassword"
``` so my advice is lose the quotes around dbname = "bacula;" and restart the service/daemon.

HTH
Subscribed with interest...

---

### Post by brenti on 2011-11-15
tried that and got a different error in the log:

[B][INDENT]15-Nov 11:27 bacula-dir JobId 0: Fatal error: Query failed: SELECT VersionId FROM Version: ERR=Table 'bacula.Version' doesn't exist
15-Nov 11:27 bacula-dir JobId 0: Fatal error: Could not open Catalog "MyCatalog", database "bacula".
15-Nov 11:27 bacula-dir JobId 0: Fatal error: Query failed: SELECT VersionId FROM Version: ERR=Table 'bacula.Version' doesn't exist
15-Nov 11:27 bacula-dir ERROR TERMINATION
Please correct configuration file: /etc/bacula/bacula-dir.conf[/INDENT][/B]

Even with this, I seem to be making progress.  Now, I just need to figure out how to build the bacula tables inside of MySQL.  Here's something curious:  I noticed the following message while installing bacula:

**[INDENT]debconf: Unknown template field '_description', in stanza #9 of /var/lib/dpkg/info/bacula-director-mysql.templates[/INDENT]**

Perhaps this could be an issue?

EDIT**Also, I noticed the problem was not with the quotes themselves, but the placement of the end-quote in relation to the semicolon.**

Thanks,
Brent

---

### Post by Habitual on 2011-11-15
> **brenti said:**
> ...I seem to be making progress.  Now, I just need to figure out how to build the bacula tables inside of MySQL.

It's a lot of little configuration changes.
```
sudo dpkg-reconfigure bacula-director-mysql
```

should re-make the bacula mysql tables for you.

---

### Post by brenti on 2011-11-15
oh man!  I thought this was a lost cause.

Thanks so much for your help.  worked perfectly!

I don't think I'll have any more issues, but I'll let you know if I do.

Thanks again!

Brent

---

### Post by Habitual on 2011-11-15
Brent:

Glad it worked out.

---

