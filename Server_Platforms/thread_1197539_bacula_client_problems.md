---
title: "bacula client problems"
date: 2009-06-26
forum: Server Platforms
---

### Post by dmm1983 on 2009-06-26
im currently having problems with bacula.
the server config i think is fine, its the 2nd client im having issues with at the moment.

it claims it cannot connect to the ex. example:xxxx

any body please help with links or anything

the story of the system:

ubuntu server 9.04
bacula 2.4.x

---

### Post by Dublee on 2009-06-26
Can you please post the configuration files?

---

### Post by dmm1983 on 2009-07-08
here is the bacula dir

#
# Default Bacula Director Configuration file
#
#  The only thing that MUST be changed is to add one or more
#   file or directory names in the Include directive of the
#   FileSet resource.
#
#  For Bacula release 2.4.4 (28 December 2008) -- debian 5.0
#
#  You might also want to change the default email address
#   from root to your address.  See the "mail" and "operator"
#   directives in the Messages resource.
#

Director {                            # define myself
  Name = tux-dir
  DIRport = 9101                # where we listen for UA connections
  QueryFile = "/etc/bacula/scripts/query.sql"
  WorkingDirectory = "/var/lib/bacula"
  PidDirectory = "/var/run/bacula"
  Maximum Concurrent Jobs = 1
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"         # Console password
  Messages = Daemon
  DirAddress = x.x.x.x
}

JobDefs {
  Name = "DefaultJob"
  Type = Backup
  Level = Incremental
  Client = tux-fd
  FileSet = "Full Set"
  Schedule = "WeeklyCycle"
  Storage = File
  Messages = Standard
  Pool = Default
  Priority = 10
}

JobDefs {
  Name = "DefaultJob1"
  Type = Backup
  Level = Incremental
  Client = newt2-fd
  FileSet = "Full Set"
  Schedule = "WeeklyCycle"
  Storage = File
  Messages = Standard
  Pool = Default
  Priority = 10
}
#
# Define the main nightly save backup job
#   By default, this job will back up to disk in /nonexistant/path/to/file/archive/dir
Job {
  Name = "tux"
  JobDefs = "DefaultJob"
  Write Bootstrap = "/var/lib/bacula/tux.bsr"
}

#Job {
#  Name = "Client2"
#  Client = newt2-fd
#  JobDefs = "DefaultJob"
#  Write Bootstrap = "/var/lib/bacula/Client2.bsr"
#}

Job {
  Name = "newt2"
  Type = Backup
  Client = newt2-fd
  FileSet = "Full Set"
  Schedule = "WeeklyCycle"
  Storage = File
  Messages = Standard
  Pool = Default
  Write Bootstrap = "/home/kern/bacula/working/newt2.bsr"
}


# Backup the catalog database (after the nightly save)
Job {
  Name = "BackupCatalog"
  JobDefs = "DefaultJob"
  Level = Full
  FileSet="Catalog"
  Schedule = "WeeklyCycleAfterBackup"
  # This creates an ASCII copy of the catalog
  #
  # WARNING!!! Passing the password via the command line is insecure.
  # see comments in make_catalog_backup for details.
  # Arguments to make_catalog_backup are:
  #  make_catalog_backup <database-name> <user-name> <password> <host>
  #
  # Ubuntu uses make_catalog_backup_awk script for
  # security reasons
  # Replace <CatalogName> with the real Catalog name
  #
  RunBeforeJob = "/usr/bin/awk -f /etc/bacula/scripts/make_catalog_backup_awk -v cat1=<CatalogName> /etc/bacula/bacula-dir.conf"
  # This deletes the copy of the catalog
  RunAfterJob  = "/etc/bacula/scripts/delete_catalog_backup"
  Write Bootstrap = "/var/lib/bacula/BackupCatalog.bsr"
  Priority = 11                   # run after main backup
}

#
# Standard Restore template, to be changed by Console program
#  Only one such job is needed for all Jobs/Clients/Storage ...
#
Job {
  Name = "RestoreFiles"
  Type = Restore
  Client=tux-fd
  FileSet="Full Set"
  Storage = File
  Pool = Default
  Messages = Standard
  Where = /backup/bacula
}


# List of files to be backed up
FileSet {
  Name = "Full Set"
  Include {
    Options {
      signature = MD5
      compression = GZIP
    }
#
#  Put your list of files here, preceded by 'File =', one per line
#    or include an external list with:
#
#    File = <file-name
#
#  Note: / backs up everything on the root partition.
#    if you have other partitons such as /usr or /home
#    you will probably want to add them too.
#
#  By default this is defined to point to the Bacula build
#    directory to give a reasonable FileSet to backup to
#    disk storage during initial testing.
#
    File = /build/buildd/bacula-2.4.4/debian/tmp-build-sqlite
  }

#
# If you backup the root directory, the following two excluded
#   files can be useful
#
  Exclude {
    File = /proc
    File = /tmp
    File = /.journal
    File = /.fsck
  File = /backup
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
    File = /var/lib/bacula/bacula.sql
  }
}

# Client (File Services) to backup
Client {
  Name = tux-fd
  Address = tux
  FDPort = 9102
  Catalog = MyCatalog
  Password = "5eWjEdmCLXMjJT_wBUCAGRRByC-Nnoi8w"          # password for FileDaemon
  File Retention = 30 days            # 30 days
  Job Retention = 6 months            # six months
  AutoPrune = yes                     # Prune expired Jobs/Files
}

#
# Second Client (File Services) to backup
#  You should change Name, Address, and Password before using
#
#Client {
#  Name = newt2-fd
#  Address = x.x.x.x
#  FDPort = 9102
#  Catalog = MyCatalog
#  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cg"
         # password for FileDaemon 2
#  File Retention = 30 days            # 30 days
#  Job Retention = 6 months            # six months
#  AutoPrune = yes                     # Prune expired Jobs/Files
#}

# Client (File Services) to backup
Client {
  Name = newt2-fd
  Address = newt2
  FDPort = 9102
  Catalog = MyCatalog
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cg"              # password for
  File Retention = 30d                # 30 days
  Job Retention = 180d                # six months
  AutoPrune = yes                     # Prune expired Jobs/Files
}


# Definition of file storage device
Storage {
  Name = File
# Do not use "localhost" here
  Address = x.x.x.x               # N.B. Use a fully qualified name here
  SDPort = 9103
  Password = "SsiFjaqW6W-a_cPiZnTKzPFd4kpLt6hTX"
  Device = FileStorage
  Media Type = File
}



# Definition of DDS tape storage device
#Storage {
#  Name = DDS-4
#  Do not use "localhost" here
#  Address = tux                # N.B. Use a fully qualified name here
#  SDPort = 9103
#  Password = "SsiFjaqW6W-a_cPiZnTKzPFd4kpLt6hTX"          # password for Storage daemon
#  Device = DDS-4                      # must be same as Device in Storage daemon
#  Media Type = DDS-4                  # must be same as MediaType in Storage daemon
#  Autochanger = yes                   # enable for autochanger device
#}

# Definition of 8mm tape storage device
#Storage {
#  Name = "8mmDrive"
#  Do not use "localhost" here
#  Address = tux                # N.B. Use a fully qualified name here
#  SDPort = 9103
#  Password = "SsiFjaqW6W-a_cPiZnTKzPFd4kpLt6hTX"
#  Device = "Exabyte 8mm"
#}

# Definition of DVD storage device
#Storage {
#  Name = "DVD"
#  Do not use "localhost" here
#  Address = tux                # N.B. Use a fully qualified name here
#  SDPort = 9103
#  Password = "SsiFjaqW6W-a_cPiZnTKzPFd4kpLt6hTX"
#  Device = "DVD Writer"
#  MediaType = "DVD"
#}


# Generic catalog service
Catalog {
  Name = MyCatalog
  dbname = "bacula"; dbuser = "bacula"; dbpassword = "hello1"
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

# Scratch pool definition
Pool {
  Name = Scratch
  Pool Type = Backup
}

#
# Restricted console used by tray-monitor to get the status of the director
#
Console {
  Name = tux-mon
  Password = "b-zmGk84LG0RwpRdkQ8cgd2Gv_HNWO7Ay"
  CommandACL = status, .status

---

### Post by dmm1983 on 2009-07-08
bacula sd file

# Default Bacula Storage Daemon Configuration file
#
#  For Bacula release 2.4.4 (28 December 2008) -- debian 5.0
#
# You may need to change the name of your tape drive
#   on the "Archive Device" directive in the Device
#   resource.  If you change the Name and/or the
#   "Media Type" in the Device resource, please ensure
#   that dird.conf has corresponding changes.
#

Storage {                             # definition of myself
  Name = tux-sd
  SDPort = 9103                  # Director's port
  WorkingDirectory = "/var/lib/bacula"
  Pid Directory = "/var/run/bacula"
  Maximum Concurrent Jobs = 20
}

#
# List Directors who are permitted to contact Storage daemon
#
Director {
  Name = tux-dir
  Password = "SsiFjaqW6W-a_cPiZnTKzPFd4kpLt6hTX"
}

#
# Restricted Director, used by tray-monitor to get the
#   status of the storage daemon
#
Director {
  Name = tux-mon
  Password = "6WVrM4jqQN2-m1JPhgOhSTSOvBxqE3T62"
  Monitor = yes
}

#
# Devices supported by this Storage daemon
# To connect, the Director's bacula-dir.conf must have the
#  same Name and MediaType.
#

Device {
  Name = FileStorage
  Media Type = File
  Archive Device = /backup/bacula
  LabelMedia = yes;                   # lets Bacula label unlabeled media
  Random Access = Yes;
  AutomaticMount = yes;               # when device opened, read it
  RemovableMedia = no;
  AlwaysOpen = yes;
}

#
# An autochanger device with two drives
#
#Autochanger {
#  Name = Autochanger
#  Device = Drive-1
#  Device = Drive-2
#  Changer Command = "/etc/bacula/scripts/mtx-changer %c %o %S %a %d"
#  Changer Device = /dev/sg0
#}

#Device {
#  Name = Drive-1                      #
#  Drive Index = 0
#  Media Type = DLT-8000
#  Archive Device = /dev/nst0
#  AutomaticMount = yes;               # when device opened, read it
#  AlwaysOpen = yes;
#  RemovableMedia = yes;
#  RandomAccess = no;
#  AutoChanger = yes
#  #
#  # Enable the Alert command only if you have the mtx package loaded
#  # Note, apparently on some systems, tapeinfo resets the SCSI controller
#  #  thus if you turn this on, make sure it does not reset your SCSI
#  #  controller.  I have never had any problems, and smartctl does
#  #  not seem to cause such problems.
#  #
#  Alert Command = "sh -c 'tapeinfo -f %c |grep TapeAlert|cat'"
#  If you have smartctl, enable this, it has more info than tapeinfo
#  Alert Command = "sh -c 'smartctl -H -l error %c'"
#}

#Device {
#  Name = Drive-2                      #
#  Drive Index = 1
#  Media Type = DLT-8000
#  Archive Device = /dev/nst1
#  AutomaticMount = yes;               # when device opened, read it
#  AlwaysOpen = yes;
#  RemovableMedia = yes;
#  RandomAccess = no;
#  AutoChanger = yes
#  # Enable the Alert command only if you have the mtx package loaded
#  Alert Command = "sh -c 'tapeinfo -f %c |grep TapeAlert|cat'"
#  If you have smartctl, enable this, it has more info than tapeinfo
#  Alert Command = "sh -c 'smartctl -H -l error %c'"
#}
#
# A Linux or Solaris tape drive
#
#Device {
#  Name = DDS-4                        #
#  Media Type = DDS-4
#  Archive Device = /dev/nrst0
#  AutomaticMount = yes;               # when device opened, read it
#  AlwaysOpen = yes;
#  RemovableMedia = yes;
#  RandomAccess = no;
## Changer Command = "/etc/bacula/scripts/mtx-changer %c %o %S %a %d"
## Changer Device = /dev/sg0
## AutoChanger = yes
#  # Enable the Alert command only if you have the mtx package loaded
## Alert Command = "sh -c 'tapeinfo -f %c |grep TapeAlert|cat'"
## If you have smartctl, enable this, it has more info than tapeinfo
## Alert Command = "sh -c 'smartctl -H -l error %c'"
#}

#
# A FreeBSD tape drive
#
#Device {
#  Name = DDS-4
#  Description = "DDS-4 for FreeBSD"
#  Media Type = DDS-4
#  Archive Device = /dev/nsa1
#  AutomaticMount = yes;               # when device opened, read it
#  AlwaysOpen = yes
#  Offline On Unmount = no
#  Hardware End of Medium = no
#  BSF at EOM = yes
#  Backward Space Record = no
#  Fast Forward Space File = no
#  TWO EOF = yes
#  If you have smartctl, enable this, it has more info than tapeinfo
#  Alert Command = "sh -c 'smartctl -H -l error %c'"
#}

#
# A OnStream tape drive.
# You need the kernel osst driver 0.9.14 or later, and
#   do "mt -f /dev/nosst0 defblksize 32768" once as root.
#
#Device {
#  Name = OnStream
#  Description = "OnStream drive on Linux"
#  Media Type = OnStream
#  Archive Device = /dev/nrst0
#  AutomaticMount = yes;               # when device opened, read it
#  AlwaysOpen = yes
#  Offline On Unmount = no
## The min/max blocksizes of 32768 are *required*
#  Minimum Block Size = 32768
#  Maximum Block Size = 32768
#  If you have smartctl, enable this, it has more info than tapeinfo
#  Alert Command = "sh -c 'smartctl -H -l error %c'"
#}

#
# A DVD device
#
#Device {
#  Name = "DVD Writer"
#  Media Type = DVD
#  Device Type = DVD
#  Archive Device = /dev/hdc
#  LabelMedia = yes;                   # lets Bacula label unlabeled media
#  Random Access = Yes;
#  AutomaticMount = yes;               # when device opened, read it
#  RemovableMedia = yes;
#  AlwaysOpen = no;
#  MaximumPartSize = 800M;
#  RequiresMount = yes;
#  MountPoint = /mnt/cdrom;
#  MountCommand = "/bin/mount -t iso9660 -o ro %a %m";
#  UnmountCommand = "/bin/umount %m";
#  SpoolDirectory = /tmp/backup;
#  WritePartCommand = "/etc/bacula/dvd-handler %a write %e %v"
#  FreeSpaceCommand = "/etc/bacula/dvd-handler %a free"
#}

#
# For OpenBSD OS >= 3.6
#
#Device {
#  Name = DDS-3
#  Media Type = DDS-3
#  Archive Device = /dev/nrst0
#  Use MTIOCGET= no
#  BSF at EOM = yes
#  TWO EOF = no
#  AutomaticMount = yes;
#  AlwaysOpen = yes;
#  RemovableMedia = yes;
#  RandomAccess = no;
#  If you have smartctl, enable this, it has more info than tapeinfo
#  Alert Command = "sh -c 'smartctl -H -l error %c'"
#}

#
# A very old Exabyte with no end of media detection
#
#Device {
#  Name = "Exabyte 8mm"
#  Media Type = "8mm"
#  Archive Device = /dev/nrst0
#  Hardware end of medium = No;
#  AutomaticMount = yes;               # when device opened, read it
#  AlwaysOpen = Yes;
#  RemovableMedia = yes;
#  RandomAccess = no;
#  If you have smartctl, enable this, it has more info than tapeinfo
#  Alert Command = "sh -c 'smartctl -H -l error %c'"
#}

#
# Send all messages to the Director,
# mount messages also are sent to the email address
#
Messages {
  Name = Standard
  director = tux-dir = all
}

---

### Post by dmm1983 on 2009-07-08
client bacula

#
# Default  Bacula File Daemon Configuration file
#
#  For Bacula release 2.4.2 (26 July 2008) -- debian lenny/sid
#
# There is not much to change here except perhaps the
# File daemon Name to
#

#
# List Directors who are permitted to contact this File daemon
#
Director {
  Name = tux-dir
  Password =  "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"
}

#
# Restricted Director, used by tray-monitor to get the
#   status of the file daemon
##
# Default  Bacula File Daemon Configuration file
#
#  For Bacula release 2.4.2 (26 July 2008) -- debian lenny/sid
#
# There is not much to change here except perhaps the
# File daemon Name to
#

#
# List Directors who are permitted to contact this File daemon
#
Director {
  Name = tux-dir
  Password =  "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"
}

#
# Restricted Director, used by tray-monitor to get the
#   status of the file daemon
#
Director {
  Name = tux-mon

Director {
  Name = tux-mon
  Password =   "b-zmGk84LG0RwpRdkQ8cgd2Gv_HNWO7Ay"
  Monitor = yes
}

#
# "Global" File daemon configuration specifications
#
FileDaemon {                          # this is me
  Name = newt2-fd
  FDAddress = tux
  FDport = 9102                  # where we listen for the director
  WorkingDirectory = /var/lib/bacula
  Pid Directory = /var/run/bacula
  Maximum Concurrent Jobs = 20
#  FDAddress = tux
}

# Send all messages except skipped files back to Director
Messages {
  Name = Standard
  director = tux-dir = all, !skipped, !restored
}

---

### Post by dmm1983 on 2009-07-14
I'm still stuck any body this is the error I receive:

tux-dir JobId 0: Fatal error: bsock.c:129 Unable to connect to Client: newt2-fd on newt2:9102. ERR=Connection refused

Whats it mean and how do i fix it???

---

### Post by druhboruch on 2009-07-14
I used to have similar problems.
I solved it by inserting ip and hostname of a client in /etc/hosts on the server.

---

### Post by dmm1983 on 2009-07-14
i still receive this message

 15-Jul 10:19 tux-dir JobId 45: Start Backup JobId 45, Job=newt2.2009-07-15_09.53.49.07
15-Jul 10:19 tux-dir JobId 45: Using Device "FileStorage"
15-Jul 10:19 tux-dir JobId 45: Warning: bsock.c:123 Could not connect to Client: newt2-fd on newt2:9102. ERR=Connection refused
Retrying ...
15-Jul 10:24 tux-dir JobId 45: Warning: bsock.c:123 Could not connect to Client: newt2-fd on newt2:9102. ERR=Connection refused
Retrying ...
15-Jul 10:29 tux-dir JobId 45: Warning: bsock.c:123 Could not connect to Client: newt2-fd on newt2:9102. ERR=Connection refused
Retrying ...
15-Jul 10:36 tux-dir JobId 45: Warning: bsock.c:123 Could not connect to Client: newt2-fd on newt2:9102. ERR=No route to host
Retrying ...
15-Jul 10:43 tux-dir JobId 45: Warning: bsock.c:123 Could not connect to Client: newt2-fd on newt2:9102. ERR=No route to host
Retrying ...
15-Jul 10:49 tux-dir JobId 45: Fatal error: bsock.c:129 Unable to connect to Client: newt2-fd on newt2:9102. ERR=No route to host

but there is a route to host.

---

### Post by druhboruch on 2009-07-15
> **dmm1983 said:**
> i still receive this message

 15-Jul 10:19 tux-dir JobId 45: Start Backup JobId 45, Job=newt2.2009-07-15_09.53.49.07
15-Jul 10:19 tux-dir JobId 45: Using Device "FileStorage"
15-Jul 10:19 tux-dir JobId 45: Warning: bsock.c:123 Could not connect to Client: newt2-fd on newt2:9102. ERR=Connection refused

but there is a route to host.

It may also be a firewall problem.

It connects to tux-fd, but doesn't like new2-fd, right?

Try to put in the "Address =" line fully qualified name of your client

---

### Post by dmm1983 on 2009-07-15
i couldnt connect on telnet to the port on the client atm 
but i will try ur suggestion next week and any others people suggest.
i dont have a firewall running atm either

It connects to tux-fd, but doesn't like new2-fd, right?
yes it connects fine to tux-fd just not newt2-fd


Try to put in the "Address =" line fully qualified name of your client 
i have tried this too...

---

