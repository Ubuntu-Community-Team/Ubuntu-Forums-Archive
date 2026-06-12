---
title: "Bacula backup, no default config files?"
date: 2008-08-14
forum: Server Platforms
---

### Post by rosv on 2008-08-14
Hi,
I just installed bacula using apt-get install bacula.
My problem is that there doesn't seem to be a default config file in /etc/bacula/bacula-dir.conf

I have the other two config files ( bacula-sd.conf and bacula-fd.conf)

Isn't bacula-dir.conf included in the default installation?

I tried creating my own bacula-dir.conf :

Job {
  Name = "BackupServer"
  JobDefs = "DefaultJob"
  Write Bootstrap = "/var/lib/bacula/Client1.bsr"
}

# Definition of "Tape Drive" storage device
Storage {
  Name = HP
  # Do not use "localhost" here    
  Address = backupserver               # N.B. Use a fully qualified name here
  SDPort = 9103
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj"
  Device = HP
  Media Type = tape
}

# LocalhostBacup FileSet.
FileSet {
  Name = "LocalhostFiles"
  Include {
    Options {
      signature = MD5
      compression=GZIP
    }
    File = /etc
    File = /home
  }
}

# LocalhostBackup Schedule -- Daily.
Schedule {
  Name = "LocalhostDaily"
  Run = Full daily at 00:01
}

# Localhost backup.
Job {
  Name = "LocalhostBackup"
  JobDefs = "DefaultJob"
  Enabled = yes
  Level = Full
  FileSet = "LocalhostFiles"
  Schedule = "LocalhostDaily"
  Storage = HP
  Write Bootstrap = "/var/lib/bacula/LocalhostBackup.bsr"
}  




But when I try to bring up the deamon I get:

 * Starting Bacula Director:                                                                             14-Aug 11:46 bacula-dir: ERROR TERMINATION at parse_conf.c:483
Config error: Could not find config Resource DefaultJob referenced on line 3 :   JobDefs = "DefaultJob"
: line 3, col 24 of file /etc/bacula/bacula-dir.conf
  JobDefs = "DefaultJob"                                                                                               [fail]

The other two deamons are working fine and I can successfully read and wirte test data from my HP storageworks DAT

---

### Post by StickyStyle on 2008-08-15
Yeah, best I remember there was a boiler plate .conf for director each time I installed bacula.
What does ```
$dpkg -l | grep bacula
``` show?

If you just installed it, I would just try and reinstall everything (remember to do a --purge when you remove) because who knows if this is just the first of your problems.  Or if you already have some time invested in it, there are some sample configs in /usr/share/doc/bacula-common/examples/conf


Oh, and the error is telling you that your job "BackupServer" being told to reference a template job JobDefs = "DefaultJob" but you have not defined one (at least in the config you have here).
[http://www.bacula.org/en/rel-manual/Configuring_Director.html#SECTION001440000000000000000](http://www.bacula.org/en/rel-manual/Configuring_Director.html#SECTION001440000000000000000)

---

### Post by adam.carroll on 2008-08-19
I recently experienced this exact problem and it was because I tried to install bacula before having mysql installed. 

I resolved this by completely removing all bacula components, installing mysql-server, then installing bacula once again.

---

