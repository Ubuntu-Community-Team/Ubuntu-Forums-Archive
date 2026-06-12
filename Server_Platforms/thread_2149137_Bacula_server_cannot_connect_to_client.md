---
title: "Bacula server cannot connect to client"
date: 2013-05-27
forum: Server Platforms
---

### Post by abdouboulegh on 2013-05-27
hello, I'm working on a tight schedule so i hope someone can help me

here's my problem, i configured my bacula server running on ubuntu 12.04, the backups and restaure are working from the same machine, now i'm trying to configure a distant machine running ubuntu server as a client, of course there's no connectivity problem between the two hosts,when i try to connect to the client via BAT i get this "Failed to connect to ubuntu_proxy_server", what am i missing ?  here are my configuration file : 

[HR][/HR]bacula-fd.conf : 
> 
Director {
 Name = ubuntu-dir
 password = [COLOR=#333333][FONT=lucida grande]"pzWhQ1tfdFA48JrTgrfd8ZOjbywK4siVBZfSqagMq/AV"[/FONT][/COLOR]
}

[COLOR=#333333][FONT=lucida grande]
[/FONT][/COLOR]
Director {
Name = ubuntu-mon
Password =[COLOR=#333333][FONT=lucida grande] "vqD_ixVhP6rkm6qziIUiG-_fgegBHnOAF"[/FONT][/COLOR]
Monitor = yes
}

FileDaemon {
Name = ubuntu_proxy_server
FDport = 9102
WorkingDirectory = /var/lib/bacula
Pid Directory = /run/bacula
Minimum Concurrent Jobs = 20
FDAddress = 127.0.0.1
}



[HR][/HR]> 
Director {
Name = ubuntu-dir
DIRport = 9101
address = localhost
password="pz"
}

[HR][/HR]and this is the server config for this client : 
> 
[COLOR=#333333][FONT=lucida grande]JobDefs {[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Name = "DefaultJob2"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Type = Backup[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Level = Incremental[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Client = ubuntu_proxy_server [/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  FileSet = "Full Set"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Schedule = "WeeklyCycle"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Storage = File[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Messages = Standard[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Pool = File[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Priority = 10[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande] Write Bootstrap = "/opt/SAUVEGARDE/bacula/Client2.bsr"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]   Full Backup Pool = Full-Pool[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Incremental Backup Pool = Inc-Pool[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Differential Backup Pool = Diff-Pool[/FONT][/COLOR]

[COLOR=#333333][FONT=lucida grande]}[/FONT][/COLOR]

[COLOR=#333333][FONT=lucida grande]Job {[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Name = "Backup_proxy_server"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  JobDefs = "DefaultJob2"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Write Bootstrap = "/opt/SAUVEGARDE/bacula/Client2.bsr"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]}[/FONT][/COLOR]




[COLOR=#333333][FONT=lucida grande]Job {[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Name = "BackupCatalog2"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  JobDefs = "DefaultJob2"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Level = Full[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  FileSet="Catalog"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Schedule = "WeeklyCycleAfterBackup"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  RunBeforeJob = "/etc/bacula/scripts/make_catalog_backup.pl MyCatalog"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  RunAfterJob  = "/etc/bacula/scripts/delete_catalog_backup"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Write Bootstrap = "/opt/SAUVEGARDE/bacula/BackupCatalog2.bsr"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Priority = 11                   # run after main backup[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]}[/FONT][/COLOR]


[COLOR=#333333][FONT=lucida grande]Job {[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Name = "RestoreFiles2"[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Type = Restore[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Client=ubuntu_proxy_server                 [/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  FileSet="Full Set"                  [/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Storage = File                      [/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Pool = Default[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Messages = Standard[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]   Where = /opt/SAUVEGARDE/bacula-restores2[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]}[/FONT][/COLOR]

[COLOR=#333333][FONT=lucida grande]Client {[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Name = ubuntu_proxy_server[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Address = [/FONT][/COLOR][10.0.3.13]("http://10.0.3.13/")
[COLOR=#333333][FONT=lucida grande]  FDPort = 9102[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Catalog = MyCatalog[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Password = "1EdTbjgKNOzKnGEbZOhSzITRAC8NK9q20"          # password for FileDaemon[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  File Retention = 30 days            # 30 days[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  Job Retention = 6 months            # six months[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]  AutoPrune = yes                     # Prune expired Jobs/Files[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]}[/FONT][/COLOR]


PS : sorry if the post is a little messy, it's my first time here =)

---

