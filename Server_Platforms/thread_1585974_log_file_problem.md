---
title: "log file problem"
date: 2010-10-01
forum: Server Platforms
---

### Post by doomy1986 on 2010-10-01
Hello,


I got a odd problem with the log file for my backup script..

This is a part of the backup script:

```

echo "$(date '+%F %T') --------Starting Backup--------" | tee -a $logFile

        #We make the local copy
        echo "$(date '+%F %T') Local copy: Rsync en cours" | tee -a $logFile

        /usr/bin/rsync -e "ssh -l $user -p $port" --recursive --log-file=$logFile  --links --times --verbose --copy-links --super --delete --compress --stats --bwlimit=$speedlimit  --exclude-from=$exclude_file $user@$host:$remote_dir $local_dir"/last"

        echo "$(date '+%F %T') exit status = $?" | /usr/bin/tee -a $logFile

echo "$(date '+%F %T') Local Backup done" | tee -a $logFile


```It should output this:

```

2010-10-01 01:00:01 --------Starting Backup--------
2010-10-01 01:00:01 Local copy: Rsync en cours
2010/10/01 01:00:02 [13314] receiving file list
DATA
....
DATA
2010/10/01 01:00:04 [13323] Number of files: 25803
2010/10/01 01:00:04 [13323] Number of files transferred: 0
2010/10/01 01:00:04 [13323] Total file size: 11378530372 bytes
2010/10/01 01:00:04 [13323] Total transferred file size: 0 bytes
2010/10/01 01:00:04 [13323] Literal data: 0 bytes
2010/10/01 01:00:04 [13323] Matched data: 0 bytes
2010/10/01 01:00:04 [13323] File list size: 1004699
2010/10/01 01:00:04 [13323] File list generation time: 0.001 seconds
2010/10/01 01:00:04 [13323] File list transfer time: 0.000 seconds
2010/10/01 01:00:04 [13323] Total bytes sent: 4504
2010/10/01 01:00:04 [13323] Total bytes received: 1022614
2010/10/01 01:00:04 [13323] sent 4504 bytes  received 1022614 bytes  293462.29 bytes/sec
2010/10/01 01:00:04 [13323] total size is 11378530372  speedup is 11078.11
2010-10-01 01:00:04 exit status = 0
2010-10-01 01:00:07 Local Backup done

```
But what i get is that:

```

2010-10-01 01:00:01 --------Starting Backup--------
2010-10-01 01:00:01 Local copy: Rsync en cours
2010/10/01 01:00:02 [13314] receiving file list
DATA
....
DATA
2010/09/30 23:10:55 [6772] Number of files: 104065
2010/09/30 23:10:55 [6772] Number of files transferred: 87
2010/09/30 23:10:55 [6772] Total file size: 242374426141 bytes
2010/09/30 23:10:55 [6772] Total transferred file size: 133000876 bytes
2010/09/30 23:10:55 [6772] Literal data: 47116475 bytes
2010/09/30 23:10:55 [6772] Matched data: 85884401 bytes
2010/09/30 23:10:55 [6772] File list size: 2458249
2010/09/30 23:10:55 [6772] File list generation time: 0.001 seconds
2010/09/30 23:10:55 [6772] File list transfer time: 0.000 seconds
2010/09/30 23:10:55 [6772] Total bytes sent: 228996
2010/09/30 23:10:55 [6772] Total bytes received: 42989601
2010/09/30 23:10:55 [6772] sent 228996 bytes  received 42989601 bytes  66033.00 bytes/sec
2010/09/30 23:10:55 [6772] total size is 242374426141  speedup is 5608.10

```It seems that when rsync is finished nothing more gets written into the logfile..

Strangely it works when there are none or very few files transferred by rsync..

Is there some kind of log writing limit per task?

Thank you very much!

---

### Post by doomy1986 on 2010-10-06
Sorry that i push the Thread but havent anyone seen this Problem?

Is there something else i could try?

I'm really blocked with this, any help would be very much appreciated.

---

### Post by SeijiSensei on 2010-10-06
Rather than use tee, why not just write to the logfile directly like this:

```

echo "This is my log file" >> $logfile
echo "Here's another line" >> $logfile

```

Using >> redirects the output to the file referenced in $logfile and appends each new line to the file.

---

### Post by dtfinch on 2010-10-06
If you're passing "-e" to bash (I don't know if you are), that would cause it to abort the script if rsync returned a non-zero exit code, which it does if it encounters any non-fatal single-file errors.

---

### Post by doomy1986 on 2010-10-08
thank you very much for your answers!

@dtfinch
do you mean the following command?

```

/usr/bin/rsync -e "ssh -l $user -p $port"

```

How can i avoid this and get it to finish the script?


@SeijiSensei
I already tried this and it didnt change anything.

---

