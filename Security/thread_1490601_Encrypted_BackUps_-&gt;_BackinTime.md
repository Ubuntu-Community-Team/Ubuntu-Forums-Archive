---
title: "Encrypted BackUps -&gt; BackinTime?"
date: 2010-05-22
forum: Security
---

### Post by frogotronic on 2010-05-22
Hello,

  If I'm using Karmic and have an encrypted home folder, when I use BackinTime (or another program) to make backups on an external drive, is/are that backup-ed files also encrypted?

Thanks,
CH

---

### Post by Frogs Hair on 2010-05-22
I attempted to ask that question on the Back in Time website , but I got a sever not found message.

---

### Post by frogotronic on 2010-05-22
okay, thanks...maybe someone from the community can answwer this query...


:popcorn:

---

### Post by FuturePilot on 2010-05-22
It depends. If you're backing up your /home/$USER then no, they are not encrypted. You would have to back up /home/.ecryptfs/$USER if you wanted the encrypted content. The problem with that right now is that because of the encrypted file names, if you ever needed to restore a file it would be almost impossible to figure out which one it was.

---

### Post by samuraiii on 2010-05-23
Maybe the best way will be encrypt backup separately through encfs... 
like its suggested here [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)
but mount encrypted folder directly in backup  (encfs <backup/device>/encrypted /home/$user/backup)
and then sync ~/backup with the files you want....
and if you want strong password this would help you not to need it enter it everytime 
[http://bitbucket.org/obensonne/gnome-encfs/src]("http://ubuntuforums.org/d%20if%20you%20want%20strong%20password%20this%20would%20help%20you%20not%20to%20need%20it%20enter%20it%20everytime%20http://bitbucket.org/obensonne/gnome-encfs/src")

---

### Post by abuster on 2011-04-11
Since this is top rated at google for "backintime encrypted backup", I will bump and share my solution here.

                     Install encfs and zenity:
```
 apt-get install encfs zenity 
```Create encrypted directory. If you would like support for hard links(backintime incremental backups), choose the standard mode, not paranoia mode.
 ```

cd /whole/path/to
mkdir .backintime_encfs
mkdir backintime
encfs /whole/path/to/.backintime_encfs /whole/path/to/backintime

```Script to mount and run backup:
```

#!/bin/bash
# Script to mount encrypted directory and run backup.
enc_path=/whole/path/to
directory=backintime
enc_directory=.backintime_encfs
extpass="zenity --title 'Encrypted backup' --entry \
--text 'Please type password for encrypted backup storage' --hide-text"

#set display for password prompt
export DISPLAY=:0.0
#check if directories exists
if [ -d $enc_path/$enc_directory ] && [ -d $enc_path/$directory ]
then
  # check if encrypted directory already is mounted
  mountpoint $enc_path/$directory > /dev/null
  if [ "$?" != "0" ]; then
    encfs --extpass="$extpass" $enc_path/$enc_directory $enc_path/$directory
  fi
  # check if mount was successful
  mountpoint $enc_path/$directory > /dev/null
  if [ "$?" = "0" ]; then
    echo "Running backup..."
    nice -n 19 /usr/bin/backintime --backup-job >/dev/null 2>&1
    # optional umount of encrypted storage:
    # fusermount -u $enc_path/$directory
    exit 0
  else
    echo "Unable to mount encrypted directory"
    exit 1
  fi
else
  echo "Encrypted directory not found"
  exit 1
fi

``` Disable schedule in Back In Time, and add script to crontab:

```

crontab -e
# add this line and save
@hourly /usr/local/bin/encrypted_backup_script

```If "fusermount -u $enc_path/$directory" is uncommented, the password prompt will show every time the backup runs. If it's commented, the encrypted storage will stay mounted as long as the machine runs.

Reference: [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

---

### Post by irw on 2011-04-28
I have an encrypted partition on my external HD; hence once mounted, it can be used as any other external drive, and any type of backup program can be used.
Once unmounted, it is encrypted and secure.


I have been using BackInTime, but was shocked to discover today that it ***_does not backup hidden files or folders_*** ](*,) - eg. ".thunderbird" which includes all my email and is one of my more important folders to backup!

(Fortunately I am paranoid and have other backup systems in place, and have not lost anything yet)

---

### Post by frogotronic on 2011-04-28
I have actually switched to DejaDup for exactly this reason.

- CH

---

### Post by serenicom on 2011-05-01
> **irw said:**
> 

I have been using BackInTime, but was shocked to discover today that it ***_does not backup hidden files or folders_*** ](*,) - eg. ".thunderbird" which includes all my email and is one of my more important folders to backup!

(Fortunately I am paranoid and have other backup systems in place, and have not lost anything yet)

By default BackInTime excludes hidden files, I tripped over that one too. Go into Settings>Exclude and remove .* from the list.

Phil S.

---

### Post by irw on 2011-05-02
I have just discovered this 10 minutes ago when i had a look at my wife's PC ... :oops:

---

