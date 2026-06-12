---
title: "Help setting up new tape autoloader"
date: 2009-01-22
forum: Server Platforms
---

### Post by shizakapayou on 2009-01-22
I have a Quantum Superloader 3 LTO-4 SAS I'm trying to setup under Server 8.04.1 64-bit.  It's connected to the system with a Dell PERC5/e.  I'm having a hard time coming by anyone that's used an autoloader under Ubuntu.

I've installed mt-st and mtx.  Results of cat /proc/scsi/scsi:

```
Host: scsi0 Channel: 00 Id: 32 Lun: 00
  Vendor: DP       Model: BACKPLANE        Rev: 1.05
  Type:   Enclosure                        ANSI  SCSI revision: 05
Host: scsi0 Channel: 02 Id: 00 Lun: 00
  Vendor: DELL     Model: PERC 6/i         Rev: 1.11
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: TEAC     Model: CD-ROM CD-224E-N Rev: 3.AC
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 01 Lun: 01
  Vendor: ETIUSA   Model: E500             Rev: 2.2.
  Type:   Direct-Access                    ANSI  SCSI revision: 04
Host: scsi3 Channel: 00 Id: 02 Lun: 00
  Vendor: QUANTUM  Model: ULTRIUM 4        Rev: 2143
  Type:   Sequential-Access                ANSI  SCSI revision: 05

```

mtx -f /dev/sg5 inquiry.  I believe the last line means it does not see the autoloader part:
```
Product Type: Disk Drive
Vendor ID: 'ETIUSA  '
Product ID: 'E500            '
Revision: '2.2.'
Attached Changer API: No

```

I think my first goal should be making sure it recognizes the autoloader, not just the drive.  From there, I know I need to configure /etc/stinit.def, but I have no clue how to approach that.  Any help would be greatly appreciated.

---

### Post by Supercows on 2009-02-24
Hey,

We have a Quantum superloader 3 also and i would like to use it under Ubuntu 8.04 server. 

Do you got it working?

---

### Post by shizakapayou on 2009-02-24
Yes, I got it working.  The tape drive and the autoloader of the unit show up as two different devices - look in /dev for sg devices, in my case I had sg0-5.  As it turns out when I posted this, I had sg0-3 and sg5, but it had skipped 4.  A reboot brought it up and there it was.

I think all I had to install was mt-st and mtx.  With that you can manually write to tapes, move tapes around, etc.  I have my server running Bacula, automatically backing up on schedule, and it works great.  I can post some Bacula configs if you need them.

---

### Post by Supercows on 2009-03-11
Great! I would appreciate that! I am not getting Bacula to work great :'(

The Ultrium is indeed /dev/sg1 and /dev/nst0

Thx!

---

### Post by shizakapayou on 2009-03-11
Make sure in addition to the Ultrium, you can see the autochanger.  Here's a list of my devices:

```
administrator@mercury:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 32 Lun: 00
  Vendor: DP       Model: BACKPLANE        Rev: 1.05
  Type:   Enclosure                        ANSI  SCSI revision: 05
Host: scsi0 Channel: 02 Id: 00 Lun: 00
  Vendor: DELL     Model: PERC 6/i         Rev: 1.11
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: QUANTUM  Model: ULTRIUM 4        Rev: 2170
  Type:   Sequential-Access                ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 01
  Vendor: QUANTUM  Model: UHDL             Rev: 0061
  Type:   Medium Changer                   ANSI  SCSI revision: 02
Host: scsi1 Channel: 00 Id: 01 Lun: 01
  Vendor: ETIUSA   Model: E500             Rev: 2.2.
  Type:   Direct-Access                    ANSI  SCSI revision: 04
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: TEAC     Model: CD-ROM CD-224E-N Rev: 3.AC
  Type:   CD-ROM                           ANSI  SCSI revision: 05

```

Make sure both Quantum devices are there.

For Bacula, skip the stuff in the repositories.  Follow this guide to install from source: [http://wiki.bacula.org/doku.php?id=howto_compile_and_install_bacula_on_debian_4.0_etch](http://wiki.bacula.org/doku.php?id=howto_compile_and_install_bacula_on_debian_4.0_etch)  I used version 2.4.4, which I think is still current.  Make sure you get Mysql working.

There's four important config files for Bacula, all located in /etc/bacula - bacula-dir.conf, bacula-fd.conf, bacula-sd.conf, and bconsole.conf.  I found that Bacula has done a great job of documenting their software, while keeping it easy to read and understand, and not treating you like an idiot.  Read this, and look at the links at the bottom for information on each file: [http://www.bacula.org/en/dev-manual/Customizin_Configurat_Files.html](http://www.bacula.org/en/dev-manual/Customizin_Configurat_Files.html)

Here's my bacula-sd.conf, which is what defines the tape drive and autochanger:
```
# Default Bacula Storage Daemon Configuration file
#
#  For Bacula release 2.4.4 (28 December 2008) -- debian lenny/sid
#
# You may need to change the name of your tape drive
#   on the "Archive Device" directive in the Device
#   resource.  If you change the Name and/or the
#   "Media Type" in the Device resource, please ensure
#   that dird.conf has corresponding changes.
#

Storage {                             # definition of myself
  Name = mercury-sd
  SDPort = 9103                  # Director's port
  WorkingDirectory = "/var/bacula/working"
  Pid Directory = "/var/run"
  Maximum Concurrent Jobs = 20
}

Director {
  Name = administrator
  Password = "password"
}

Autochanger {
  Name = "Autochanger"
  Device = Superloader
  Changer Device = /dev/sg3
  Changer Command = "/etc/bacula/mtx-changer %c %o %S %a %d"
}

Device {
  Name = Superloader
  Archive Device = /dev/nst0
  Device Type = Tape
  Media Type = LTO-4
  Autochanger = Yes
  Autoselect = yes
  Maximum Changer Wait = 300
  LabelMedia = yes                  # lets Bacula label unlabeled media
  Random Access = no
  AutomaticMount = no               # when device opened, read it
  RemovableMedia = yes
  AlwaysOpen = no
}

Messages {
  Name = Standard
  director = mercury-dir = all
}

```

Those definitions should get Bacula working with the autochanger.  You can also look here for more: [http://www.bacula.org/en/dev-manual/Autochanger_Resource1.html](http://www.bacula.org/en/dev-manual/Autochanger_Resource1.html)  I recommend trying the mtx commands they have listed there, as it uses the script Bacula will use.  If that works, you're well on your way.

---

### Post by Supercows on 2009-03-12
Thanks! I am gone try this!

I had a config, but that was a storage device including the changer. Not seperated :)

---

### Post by Supercows on 2009-03-12
How do I set the Pool and Volumes? Can you tell me that?

Does this say anything to you?

Job queued. JobId=38
*
12-Mar 13:43 bbikol-bck01-dir JobId 38: Start Backup JobId 38, Job=bbikol-nfs01-fd_CloneZilla.2009-03-12_13.43.05
12-Mar 13:43 bbikol-bck01-dir JobId 38: Using Device "Superloader"
12-Mar 13:43 bbikol-bck01-sd JobId 38: Invalid slot=0 defined in catalog for Volume "Vmware_machines0015" on "Superloader" (/dev/nst0). Manual load may be required.
12-Mar 13:43 bbikol-bck01-sd JobId 38: 3301 Issuing autochanger "loaded? drive 0" command.
12-Mar 13:43 bbikol-bck01-sd JobId 38: 3991 Bad autochanger "loaded? drive 0" command: ERR=No such file or directory.
Results=
12-Mar 13:43 bbikol-bck01-sd JobId 38: 3301 Issuing autochanger "loaded? drive 0" command.
12-Mar 13:43 bbikol-bck01-sd JobId 38: 3991 Bad autochanger "loaded? drive 0" command: ERR=No such file or directory.
Results=
12-Mar 13:43 bbikol-bck01-sd JobId 38: Invalid slot=0 defined in catalog for Volume "Vmware_machines0015" on "Superloader" (/dev/nst0). Manual load may be required.
12-Mar 13:43 bbikol-bck01-sd JobId 38: Please mount Volume "Vmware_machines0015" or label a new one for:
    Job:          bbikol-nfs01-fd_CloneZilla.2009-03-12_13.43.05
    Storage:      "Superloader" (/dev/nst0)
    Pool:         Vmware_bck
    Media type:   LTO-3

---

### Post by shizakapayou on 2009-03-12
Here's the pool I used.  The pool basically just tells the job which storage to use, and what to do with it.

```
Pool {
  Name = Default
  Pool Type = Backup
  Storage = Superloader
  Recycle = yes                       # Bacula can automatically recycle Volumes
  AutoPrune = yes                     # Prune expired volumes
  Volume Retention = 1 days           # how long to keep a volume (tape)
}

```

Before you get too far ahead of yourself, try the mtx-changer commands in the link I posted.  You want to make sure Bacula can control the tape drive before trying to run a job.  Make sure to label the tapes as well, it makes things nice and easy.

---

### Post by Supercows on 2009-03-13
Thanks, i run btape. Everything was oké :)

What speeds do you get to and from your tape?

---

### Post by shizakapayou on 2009-03-13
That's one thing I keep meaning to call Quantum about.  The unit is connected to my PowerEdge 2950 III by a Dell SAS 5/e card, PCI Express x8.  The card also has a 8 x 1TB RAID 6 array attached, in an EnhanceTech R8.  Here's the report I'm getting from Bacula:

> Elapsed time:           5 hours 32 mins 30 secs
  Priority:               10
  FD Files Written:       315,106
  SD Files Written:       315,106
  FD Bytes Written:       696,704,696,179 (696.7 GB)
  SD Bytes Written:       696,766,388,140 (696.7 GB)
  Rate:                   34922.5 KB/s

This job was from the internal storage on the server, not the Enhance box.  It seems a bit slow to me, but I don't really know.  It's actually usually a bit higher, around 42000 KB/s.

Overall though, it's a great setup.  Tape drive's easily the best I've used (LTO-4 is great) and Bacula, well, it's infinitely better than Backup Exec ever was.

---

### Post by Supercows on 2009-03-13
We are testing on a ML350 (yeah still lives :D) dual xeon, with 2 GB ram and HP 5300 controller. With 4 x 74 GB SCSI and 3 x 300GB scsi and 3 x 18,2 GB SCSI :P

The idea is that that is the "storage server". The storage server pulls the data over the ethernet (1000G port) from our SAN (2 x QUAD XEON, 8 GB ram and 8 x 500 GB SATA disks) to a directory on the server. Later the "backup" directory must backup to tape. (other run)

I have made the first run's manualy to disk and get this:
  FD Files Written:       38,942
  SD Files Written:       38,942
  FD Bytes Written:       33,366,637,087 (33.36 GB)
  SD Bytes Written:       33,371,470,249 (33.37 GB)
  Rate:                   26672.0 KB/s
Also very slow :'(

Later on I make the backup to tape. I'll keep you posted :)
Thx for your help!!

---

### Post by jbcola on 2009-06-30
Hi,

Here is a quick and dirty script to backup the whole system on tape, and change the media as soon as the tape is full and create a full backup once every week.
It work with a quantum SuperLoader series:
(backup.sh)
#!/bin/bash
exec > /var/log/backup.$(date "+%Y%m%d").log 2>&1
echo Backup start : $(date)
MAILTO=root@mysys
TAPE="/dev/tape/by-id/scsi-1QUANTUM_ULTRIUM_3_JN0746AME50228-nst"

renice 10 $$

# Full backup every Sunday
if [ "$(date +%a)" = "Sun" ]
then
        rm -f /var/log/usr.snar
fi

set -x
tar -cMvpf $TAPE --exclude=/proc --exclude=/lost+found --exclude=/var/spool/squid --exclude=/mnt --exclude=/dev --exclude=/sys / /boot/ --multi-volume --new-volume-script=/usr/local/bin/changetape --label "Daily backup for $(date +%Y-%m-%d)" --listed-incremental=/var/log/usr.snar
echo Tar RC: $?
set +x
echo backup finished: $(date)

and the tape change script (changetape):
#!/bin/bash
set -x
exec >> /var/log/changetape.$(date "+%Y%m").log 2>&1
MAILTO=root@mysys
echo Tape full, changing tape
TAPEDEV="/dev/tape/by-id/scsi-1QUANTUM_ULTRIUM_3_JN0746AME50228-nst"
CHANGER="/dev/tape/by-id/scsi-3500e09efff0e1607"
/usr/sbin/mtx -f $CHANGER status | grep "Storage Element 16:Empty"
if [ $? -eq 0 ]
then
        echo loading fist tape
        /usr/sbin/mtx -f $CHANGER unload
        /usr/sbin/mtx -f $CHANGER load 1
else
        echo loading next tape
        /usr/sbin/mtx -f $CHANGER next
fi
sleep 60
mt -f $TAPEDEV rewind
set +x



Quite simple, but works like a charm...

Best regards,
Jean-Luc

---

