---
title: "Default Bacula install not working"
date: 2011-09-10
forum: Server Platforms
---

### Post by fman23 on 2011-09-10
I've tried everything and cant figure this out.  Apparently the director can't connect to the mysql database, but the other daemons can.

The error is:

```
10-Sep 23:27 bacula-dir JobId 0: Fatal error: Could not open Catalog "MyCatalog", database "bacula;".
10-Sep 23:27 bacula-dir JobId 0: Fatal error: mysql.c:194 Unable to connect to MySQL server.
Database=bacula; User=bacula
MySQL connect failed either server not running or your authorization is incorrect.
10-Sep 23:27 bacula-dir ERROR TERMINATION
Please correct configuration file: /etc/bacula/bacula-dir.conf
```

and my bacula-dir.conf

```
#
# Default Bacula Director Configuration file
#
#  The only thing that MUST be changed is to add one or more
#   file or directory names in the Include directive of the
#   FileSet resource.
#
#  For Bacula release 5.0.3 (04 August 2010) -- ubuntu 11.04
#
#  You might also want to change the default email address
#   from root to your address.  See the "mail" and "operator"
#   directives in the Messages resource.
#

Director {                            # define myself
  Name = server.local-dir
  DIRport = 9101                # where we listen for UA connections
  QueryFile = "/etc/bacula/scripts/query.sql"
  WorkingDirectory = "/var/lib/bacula"
  PidDirectory = "/var/run/bacula"
  Maximum Concurrent Jobs = 1
  Password = "J0DxYLmx5vh3UBsfPFstsLeduse6gdL9hpVhUFHUq1eY"         # Console password
  Messages = Daemon
  DirAddress = 127.0.0.1
}

JobDefs {
  Name = "DefaultJob"
  Type = Backup
  Level = Incremental
  Client = server.local-fd 
  FileSet = "Full Set"
  Schedule = "WeeklyCycle"
  Storage = File
  Messages = Standard
  Pool = File
  Priority = 10
  Write Bootstrap = "/var/lib/bacula/%c.bsr"
}


#
# Define the main nightly save backup job
#   By default, this job will back up to disk in /nonexistant/path/to/file/archive/dir
Job {
  Name = "BackupClient1"
  JobDefs = "DefaultJob"
}

#Job {
#  Name = "BackupClient2"
#  Client = server.local2-fd
#  JobDefs = "DefaultJob"
#}

# Backup the catalog database (after the nightly save)
Job {
  Name = "BackupCatalog"
  JobDefs = "DefaultJob"
  Level = Full
  FileSet="Catalog"
  Schedule = "WeeklyCycleAfterBackup"
  # This creates an ASCII copy of the catalog
  # Arguments to make_catalog_backup.pl are:
  #  make_catalog_backup.pl <catalog-name>
  RunBeforeJob = "/etc/bacula/scripts/make_catalog_backup.pl MyCatalog"
  # This deletes the copy of the catalog
  RunAfterJob  = "/etc/bacula/scripts/delete_catalog_backup"
  Write Bootstrap = "/var/lib/bacula/%n.bsr"
  Priority = 11                   # run after main backup
}

#
# Standard Restore template, to be changed by Console program
#  Only one such job is needed for all Jobs/Clients/Storage ...
#
Job {
  Name = "RestoreFiles"
  Type = Restore
  Client=server.local-fd                 
  FileSet="Full Set"                  
  Storage = File                      
  Pool = Default
  Messages = Standard
  Where = /nonexistant/path/to/file/archive/dir/bacula-restores
}


# List of files to be backed up
FileSet {
  Name = "Full Set"
  Include {
    Options {
      signature = MD5
    }
#    
#  Put your list of files here, preceded by 'File =', one per line
#    or include an external list with:
#
#    File = <file-name
#
#  Note: / backs up everything on the root partition.
#    if you have other partitions such as /usr or /home
#    you will probably want to add them too.
#
#  By default this is defined to point to the Bacula binary
#    directory to give a reasonable FileSet to backup to
#    disk storage during initial testing.
#
    File = /usr/sbin
  }

#
# If you backup the root directory, the following two excluded
#   files can be useful
#
  Exclude {
    File = /var/lib/bacula
    File = /nonexistant/path/to/file/archive/dir
    File = /proc
    File = /tmp
    File = /.journal
    File = /.fsck
  }
}

#
# When to do the backups, full backup on first sunday of the month,
#  differential (i.e. incremental since full) every other sunday,
#  and incremental backups other days
Schedule {
  Name = "WeeklyCycle"
  Run = Full 1st sun at 23:05
  Run = Differential 2nd-5th sun at 23:05
  Run = Incremental mon-sat at 23:05
}

# This schedule does the catalog. It starts after the WeeklyCycle
Schedule {
  Name = "WeeklyCycleAfterBackup"
  Run = Full sun-sat at 23:10
}

# This is the backup of the catalog
FileSet {
  Name = "Catalog"
  Include {
    Options {
      signature = MD5
    }
    File = "/var/lib/bacula/bacula.sql"
  }
}

# Client (File Services) to backup
Client {
  Name = server.local-fd
  Address = localhost
  FDPort = 9102
  Catalog = MyCatalog
  Password = "iMzZJwS2aNUN32XdNlAcwYWRzbFM2s3So"          # password for FileDaemon
  File Retention = 30 days            # 30 days
  Job Retention = 6 months            # six months
  AutoPrune = yes                     # Prune expired Jobs/Files
}

#
# Second Client (File Services) to backup
#  You should change Name, Address, and Password before using
#
#Client {
#  Name = server.local2-fd                
#  Address = localhost2
#  FDPort = 9102
#  Catalog = MyCatalog
#  Password = "iMzZJwS2aNUN32XdNlAcwYWRzbFM2s3So2"         # password for FileDaemon 2
#  File Retention = 30 days            # 30 days
#  Job Retention = 6 months            # six months
#  AutoPrune = yes                     # Prune expired Jobs/Files
#}


# Definition of file storage device
Storage {
  Name = File
# Do not use "localhost" here    
  Address = localhost                # N.B. Use a fully qualified name here
  SDPort = 9103
  Password = "gNarjsvrZmp062IxYdDivjfGHcVVu1QWW"
  Device = FileStorage
  Media Type = File
}



# Definition of DDS tape storage device
#Storage {
#  Name = DDS-4    
#  Do not use "localhost" here
#  Address = localhost                # N.B. Use a fully qualified name here
#  SDPort = 9103
#  Password = "gNarjsvrZmp062IxYdDivjfGHcVVu1QWW"          # password for Storage daemon
#  Device = DDS-4                      # must be same as Device in Storage daemon
#  Media Type = DDS-4                  # must be same as MediaType in Storage daemon
#  Autochanger = yes                   # enable for autochanger device
#}

# Definition of 8mm tape storage device
#Storage {
#  Name = "8mmDrive"
#  Do not use "localhost" here
#  Address = localhost                # N.B. Use a fully qualified name here
#  SDPort = 9103
#  Password = "gNarjsvrZmp062IxYdDivjfGHcVVu1QWW"
#  Device = "Exabyte 8mm"
#  MediaType = "8mm"
#}

# Definition of DVD storage device
#Storage {
#  Name = "DVD"
#  Do not use "localhost" here
#  Address = localhost                # N.B. Use a fully qualified name here
#  SDPort = 9103
#  Password = "gNarjsvrZmp062IxYdDivjfGHcVVu1QWW"
#  Device = "DVD Writer"
#  MediaType = "DVD"
#}


# Generic catalog service
Catalog {
  Name = MyCatalog
# Uncomment the following line if you want the dbi driver
# dbdriver = "dbi:sqlite3"; dbaddress = 127.0.0.1; dbport = 
  dbname = "bacula;" DB Address = ""; dbuser = "bacula"; dbpassword = "m9VfzPEPZoYR"
}

# Reasonable message delivery -- send most everything to email address
#  and to the console
Messages {
  Name = Standard
#
# NOTE! If you send to two email or more email addresses, you will need
#  to replace the %r in the from field (-f part) with a single valid
#  email address in both the mailcommand and the operatorcommand.
#  What this does is, it sets the email address that emails would display
#  in the FROM field, which is by default the same email as they're being
#  sent to.  However, if you send email to more than one address, then
#  you'll have to set the FROM address manually, to a single address. 
#  for example, a 'no-reply@mydomain.com', is better since that tends to
#  tell (most) people that its coming from an automated source.

#
  mailcommand = "/usr/lib/bacula/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula: %t %e of %c %l\" %r"
  operatorcommand = "/usr/lib/bacula/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula: Intervention needed for %j\" %r"
  mail = root@localhost = all, !skipped            
  operator = root@localhost = mount
  console = all, !skipped, !saved
#
# WARNING! the following will create a file that you must cycle from
#          time to time as it will grow indefinitely. However, it will
#          also keep all your messages if they scroll off the console.
#
  append = "/var/lib/bacula/log" = all, !skipped
  catalog = all
}


#
# Message delivery for daemon messages (no job).
Messages {
  Name = Daemon
  mailcommand = "/usr/lib/bacula/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula daemon message\" %r"
  mail = root@localhost = all, !skipped            
  console = all, !skipped, !saved
  append = "/var/lib/bacula/log" = all, !skipped
}

# Default pool definition
Pool {
  Name = Default
  Pool Type = Backup
  Recycle = yes                       # Bacula can automatically recycle Volumes
  AutoPrune = yes                     # Prune expired volumes
  Volume Retention = 365 days         # one year
}

# File Pool definition
Pool {
  Name = File
  Pool Type = Backup
  Recycle = yes                       # Bacula can automatically recycle Volumes
  AutoPrune = yes                     # Prune expired volumes
  Volume Retention = 365 days         # one year
  Maximum Volume Bytes = 50G          # Limit Volume size to something reasonable
  Maximum Volumes = 100               # Limit number of Volumes in Pool
}


# Scratch pool definition
Pool {
  Name = Scratch
  Pool Type = Backup
}

#
# Restricted console used by tray-monitor to get the status of the director
#
Console {
  Name = server.local-mon
  Password = "PNAXtzqhWWMZRaWT3jLneE3sOyu-GUl_w"
  CommandACL = status, .status
}
```

This is probably something simple I overlooked, but this is driving me crazy.

Computer: Ubuntu Server 11.04
I also installed Webmin and Virtualmin

---

### Post by fman23 on 2011-09-13
bump?

---

### Post by Habitual on 2011-09-18
this doesn't look 'default'
Write Bootstrap = "/var/lib/bacula/%c.bsr"

I'm using Ubu 8.04 LTS and  bacula* Version: 2.2.8
and I don't see that in my config. 
I'm just saying.

---

### Post by fman23 on 2011-09-21
thank you for reply, ill comment out and retry

---

### Post by Habitual on 2011-09-21
I believe yours should be:
```
bacula-dir.conf:  Write Bootstrap = "/var/lib/bacula/Client.bsr"
```

This should match the "Client {" section entry of the same file.
[B]
Don't rem it out.[/B]

---

### Post by fman23 on 2011-09-21
nope still didnt work :(

im using 11.04 btw

---

### Post by Habitual on 2011-09-21
Did you restart the bacula services?

```
for i in `find /etc/init.d/ -iname "bacula*"` ; do $i restart; done
```

---

### Post by fman23 on 2011-09-21
of course, i use webmin and used the restart all daemons button.

---

### Post by Habitual on 2011-09-21
Here is a 'set' that someone helped me put together and this works for me, you ***will*** need to adjust a couple of things:
[COLOR="Red"]File = **/home/jj**[/COLOR] <-- edit this to the /path/to/backup
[COLOR="Red"]Address = **192.168.1.17**[/COLOR] and this.
[COLOR="Red"]Password = "**Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj**"[/COLOR]  # Same password as in /etc/bacula/bacula-sd.conf and this.


Add this to the **bottom** of /etc/bacula/bacula-dir.conf and restart bacula services. You can check this in ```
bconsole > status client
``` or ```
status storage
``` or ```
status all
```

```

### My Stuff

#JobDefs
JobDefs {
  Name = "MyJobDef"
  Type = Backup
  Level = Incremental
  FileSet = "MyFileSet"
  Schedule = "MySchedule"
  Storage = MyStorage 
  Messages = Standard
  Pool = MyPool
  Priority = 15
}

#Jobs
Job { 
  Name = "MyJob"
  Client = bacula-director-fd 
  JobDefs = "MyJobDef"
  Write Bootstrap = "/var/lib/bacula/mybackup.bsr"
}

#FileSets
FileSet {
  Name = "MyFileSet"
  Include {
    Options {
      signature = MD5
      compression = GZIP
    }
    File = /home/jj
  }
  Exclude {
  }
}

#Schedules
Schedule {
  Name = "MySchedule"
  Run = Full 1st mon at 09:00
  Run = Incremental mon-sun at 09:05
}

#Pools
Pool {
  Name = MyPool
  Pool Type = Backup
  Recycle = yes
  AutoPrune = yes
  Volume Retention = 8 days 
  Maximum Volume Jobs = 1 
  Label Format = MyPool- 
  Storage = MyStorage 
}

#Storage
Storage {
  Name = MyStorage
  Address = 192.168.1.17
  SDPort = 9103
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj"  # Can be copied from /etc/bacula/bacula-sd.conf
  Device = MyStorage # Must match name of "Device" section in bacula-sd.conf
  Media Type = File
  Maximum Concurrent Jobs = 5
}

```

I can't stress enough the importance of adding this to the bottom of /etc/bacula/bacula-dir.conf and restarting bacula services.

I don't use Webmin so using the terminal is my answer.

Good Luck.

---

### Post by fman23 on 2011-09-21
ok that didnt work.  The problem lies in the MyCatalog block where it is trying to connect to MySQL, but is failing, no matter what i do (i even tried to make it connect as root).  the funny thing is, all of the other daemons can connect to the MySQL server.  Im thinking about compiling on my own now.

---

### Post by fman23 on 2011-09-21
thank you for trying to help though. :)

---

### Post by Habitual on 2011-09-22
in terminal > 
```
sudo dpkg-reconfigure bacula-director-mysql
```

Answers you should use based on your supplied conf files are:
```

Database Server Name: localhost
Database administrator username: root
Database administrator password: <only you know this>
DBA password confirmation:  <only you know this the 2nd time>
Database owner username: bacula
Database user password: m9VfzPEPZoYR
Database user password Confirmation: m9VfzPEPZoYR
```

Restart services and your MyCatalog block where it is trying to connect to MySQL should be ok.

Please lemme know...

---

### Post by fman23 on 2011-09-25
Found the problem :D.  > dbname = "bacula;" 

fixed to dbname = "bacula";

Funny that should be in default package? Ill post a bug report.

---

### Post by soeze on 2011-10-23
Thank you very much fman!

> **fman23 said:**
> Found the problem :D.  

fixed to dbname = "bacula";

Funny that should be in default package? Ill post a bug report.

I had the same problem after apt-get install bacula on Ubunbtu server 11.04. Fixing the above in /etc/bacula/bacula-dir.conf under Catalog solved it.

---

### Post by slez-e on 2012-04-23
> **fman23 said:**
> Found the problem :D.  

fixed to dbname = "bacula";

Funny that should be in default package? Ill post a bug report.
This was my issues as well. Thank you for taking the time to look through the bacula-dir.conf file with a fine toothed comb as I would have never found this error.

---

