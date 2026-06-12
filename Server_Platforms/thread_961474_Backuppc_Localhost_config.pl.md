---
title: "Backuppc Localhost config.pl"
date: 2008-10-28
forum: Server Platforms
---

### Post by newsboy on 2008-10-28
I've been trying to get backuppc working in order to backup the localhost. I've tried following these [[COLOR="Blue"]directions[/COLOR]]("https://help.ubuntu.com/community/BackupPC") Which indicated to make several changes 

> Modify /etc/backuppc/config.pl

    * Run “sudo gedit /etc/backuppc/config.pl”
    *

      Add sudo to the TAR Client and ClientRestore commands
          o

            Change $Conf{TarClientCmd} and $Conf{TarClientRestoreCmd} to read 

$Conf{TarClientCmd} = ‘sudo $tarPath -c -v -f - -C $shareName’
. ‘ –totals’;

$Conf{TarClientRestoreCmd} = ‘sudo $tarPath -x -p –numeric-owner –same-owner’
. ‘ -v -f - -C $shareName’;

    *

      Also remove plus (+) from $incrDate in $Conf{TarIncrArgs}  so it won't be double escaped (need to escape only once when running sudo): 

$Conf{TarIncrArgs} = '--newer=$incrDate $fileList+';

    *

      Change $Conf{BackupFilesExclude} (these seem to all be temp files that you don’t really need to backup) to read 

$Conf{BackupFilesExclude} = [’/proc’, ‘/dev’, ‘/tmp’, ‘/mnt’, ‘/media’, ‘/sys’, ‘/lost+found’, ‘/usr/src’, ‘/var/lib’, ‘/var/tmp’, ‘/var/cache’, ‘/var/spool’, ‘/var/run’, ‘/var/lock’, ‘/var/games’, ‘/home/*/.Trash’, ‘/home/*/.mozilla/*/*/Cache’, ‘/home/*/.mozilla/*/*/Cache.Trash’];

However after doing this when I try to navigate to the web interface I get the error message "Software error: Unrecognized character \xE2 at /etc/backuppc/config.pl line 1060." And the line number corresponds to wherever I made the changes in the config.pl file

---

### Post by le0buntu on 2008-11-06
It could be a cut'n'paste issue, but i believe all the quotes used to should be single quotes (') and not acute accents (’) nor grave accents (`) (or whatever they're called).
e.g. 
['/proc','/dev', ...
not 
[’/proc’, ‘/dev’, ...

---

