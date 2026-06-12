---
title: "bacula backup"
date: 2011-01-03
forum: Server Platforms
---

### Post by mido1812 on 2011-01-03
hi i am new with bacula open source sofwatre for backup files .  i start a job with bacula using wbemin the job work fine i need to know where i find the file that backup and thanks

and this the the bacula-dir 


Director {
      Name = bacula-dir
      DIRport = 9101
          QueryFile = "/etc/bacula/query.sql"
      WorkingDirectory = "/var/bacula/working"
      PidDirectory = "/var/run"
      Maximum Concurrent Jobs = 1
      Password = "MMvI9Xt3tAPrxX5muC94P6gVPFjhmv+ubeWnUdLuLxYN"
      Messages = Daemon
           DirAddress = 192.168.23.94
          
    }
     
# Definition des parametres pour les Jobs ###
     
    JobDefs {
      Name = "DefaultJob"
     Type = Backup
      Level = Incremental
      Client = ahmed-fd
      FileSet = "File Centres"
      Schedule = "WeeklyCycle"
      Storage = DDCENTRES
      Messages = Standard
      Pool = DDSMB
      Priority = 10
    }
     
    JobDefs {
      Name = "DefaultJob2"
      Type = Backup
      Level = Incremental
      Client = centres-fd
      FileSet = "File Centres"
      Schedule = "WeeklyCycle"
      Storage = DDCENTRES
      Messages = Standard
      Pool = DDSMB
      Priority = 10
    }
     
    Job {
  Name = ahmed-fd
  JobDefs = DefaultJob
      Write Bootstrap = "/var/bacula/working/hotline.bsr"
    }
     
    Job {
        Name = "centres-fd"
      JobDefs = "DefaultJob2"
      Write Bootstrap = "/var/bacula/working/centres.bsr"
    }
     
    # Definition des jobs de restaurations
    Job {
      Name = "RestoreHotline"
     Type = Restore
      Client= ahmed-fd
      FileSet="File Centres"
      Storage = DDCENTRES
      Pool = DDSMB
          Messages = Standard
      Where = /backup
    }
     
    Job {
      Name = "RestoreCentres"
      Type = Restore
      Client= centres-fd
      FileSet="File Centres"
      Storage = DDCENTRES
      Pool = DDSMB
          Messages = Standard
      Where = /backup
    }
     
    # Definition des fichiers a sauvegarder et des exclusions
    FileSet {
  Name = "File Centres"
      Include {
        Options {
      signature = MD5
        }
    File = c://test
     }
      Exclude {     # Permet d'exclure des fichiers de la sauvegarde
    #    wild = *.obj
    #    exclude = yes
      }
    }
     
    FileSet {
      Name = "Full Set"
      Include {
        Options {
          signature = MD5 # MD5 activé pour chaque fichiers
        }
        File = /backup/sql #Sauvegarde des bases sql
      }
      Exclude {       # Permet d'exclure des fichiers de la sauvegarde
        File = /proc
        File = /tmp
        File = /.journal
        File = /.fsck
      }
    }
     
    # Definition du cycle de sauvegarde
    Schedule {
      Name = "WeeklyCycle"
      Run = Full 1st sun at 23:05
      Run = Differential 2nd-5th sun at 23:05
      Run = Incremental mon-sat at 23:05
    }
     
    # Definitions des clients a sauvegarder
    Client {
      Name = ahmed-fd
      Address = 192.168.23.98
      FDPort = 9102
      Catalog = MyCatalog
      Password = "hmwTHg9jbZ5NaTCdB+xPGe663qDPE9wg0giH1kmC5eaH"
      File Retention = 30 days           # Retention fichiers 30 jours
      Job Retention = 6 months         # Retention du job 6 mois
      AutoPrune = yes
    }
     
    Client {
      Name = centres-fd
      Address = 192.168.23.98
      FDPort = 9102
      Catalog = MyCatalog
      Password = "hmwTHg9jbZ5NaTCdB+xPGe663qDPE9wg0giH1kmC5eaH"
      File Retention = 30 days        # Retention fichiers 30 jours
      Job Retention = 6 months       # Retention du job 6 mois
      AutoPrune = yes
    }
     
    # Definition de l'enregistreur de données
    Storage {
      Name = HOTLINE
    # ne pas utiliser "localhost"
      Address = 192.168.23.94
      SDPort = 9103
  Password = "Wg6C8PB2-qIKDN-Zdf1IXzZdyw7oCx5u8"
      Device = HOTLINEStorage
      Media Type = FichiersHOTLINE
    }
     
    Storage {
      Name = DDCENTRES
    # ne pas utiliser "localhost" ici
      Address = 192.168.23.94
      SDPort = 9103
      Password = "Wg6C8PB2-qIKDN-Zdf1IXzZdyw7oCx5u8"
      Device = DDCENTREStorage
      Media Type = FichiersCENTRES
    }
     
    # Definition de l'authentification à la base de donnée
        # Attention si vous avez compiler bacula comme je l'ai
    # fait la base ne possede pas de mot de passe par defaut
    Catalog {
      Name = MyCatalog
      dbname = "bacula"; dbuser = "root"; dbpassword = "ccit"
    }
     
    # Definition des mails a envoyer en cas de probleme ou a la fin d'un job
    Messages {
      Name = Standard
      mailcommand = "/sbin/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula: %t %e of %c %l\" %r"
      operatorcommand = "/sbin/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula: Intervention needed for %j\" %r"
      mail = [EMAIL="befa@rtfm.fr"]befa@rtfm.fr[/EMAIL] = all, !skipped
      operator = [EMAIL="fpizard@emmaus.asso.fr"]fpizard@emmaus.asso.fr[/EMAIL] = mount
      console = all, !skipped, !saved
      append = "/var/bacula/log" = all, !skipped
    }
     
    Messages {
      Name = Daemon
      mailcommand = "/sbin/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula daemon message\" %r"
      mail = [EMAIL="befa@rtfm.fr"]befa@rtfm.fr[/EMAIL] = all, !skipped
      console = all, !skipped, !saved
      append = "/var/bacula/working/log" = all, !skipped
    }
     
    # Definition des pools contenant les volumes
    Pool {
      Name = LOCAL
      Pool Type = Backup
      Recycle = yes
      AutoPrune = yes
      Volume Retention = 365 days         # Retention du pool 1 année
    }
     
    Pool {
      Name = DDSMB
      Pool Type = Backup
      Recycle = yes
      AutoPrune = yes
      Volume Retention = 365 days         # Retention du pool 1 année
    }

---

