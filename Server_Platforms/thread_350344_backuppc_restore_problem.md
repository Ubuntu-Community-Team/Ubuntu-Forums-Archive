---
title: "backuppc restore problem"
date: 2007-01-31
forum: Server Platforms
---

### Post by novascale on 2007-01-31
Hi

I've install and configure backuppc on my edgy, everything works except the restoring system

when i restore a file i've this error in the log :


2007-01-31 19:10:54 Running: /usr/share/backuppc/bin/BackupPC_tarCreate -h localhost -n 1 -s /home/nico/data -t /Document\ texte[/I]
2007-01-31 19:10:55 Restore failed (BackupPC_tarCreate failed)

and the file is not restored

precision : the folder is rwx for backuppc 

here an extract of the config.pl :

#########################################################
$Conf{TarShareName} = '/';
$Conf{XferMethod} = 'tar';
$Conf{TarClientCmd} = '$sshPath -q -x -n -l root $host'
                    . ' /usr/bin/env LC_ALL=C $tarPath -c -v -f - -C $shareName+'
                    . ' --totals';
$Conf{TarFullArgs} = '$fileList+';
$Conf{TarClientRestoreCmd} = '$sshPath -q -x -l root $host'
		   . ' /usr/bin/env LC_ALL=C $tarPath -x -p --numeric-owner --same-owner'
		   . ' -v -f - -C $shareName+';
$Conf{TarClientPath} = '/bin/tar';
#########################################################


and the content of localhost.pl

#########################################################
#
# Local server backup of /etc as user backuppc
#
$Conf{XferMethod} = 'tar';

$Conf{TarShareName} = ['/home/nico/data'];

$Conf{TarClientCmd} = '/usr/bin/env LC_ALL=C $tarPath -c -v -f - -C $shareName'
                        . ' --totals';

# remove extra shell escapes ($fileList+ etc.) that are
# needed for remote backups but may break local ones
$Conf{TarFullArgs} = '$fileList';
$Conf{TarIncrArgs} = '--newer=$incrDate $fileList';
#########################################################

Tanks for your help and exuse my poor english

---

### Post by brunux on 2007-12-01
I have the same problem. Have you solved it?

brunux

---

### Post by HermanAB on 2007-12-01
Hmm, you must have noticed that there are umpteen gazillion backup scripts for Linux.  Every newcomer tries his/her hand at one.

There are only two that are any good: Bacula and Amanda.  Bacula is good for small systems, while Amanda is good for enormous systems.

Everybody else with a bit more experience simply use a combination of tar and rsync over ssh, put one or two lines in a cron job and be done with it.

'Hope that clears things up a bit!

Cheers,

Herman

---

