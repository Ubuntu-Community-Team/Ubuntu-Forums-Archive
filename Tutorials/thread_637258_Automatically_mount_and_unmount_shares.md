---
title: "Automatically mount and unmount shares"
date: 2007-12-10
forum: Tutorials
---

### Post by tweedledee on 2007-12-10
Here is a script you can run in the background that will automatically detect your network shares as they dynamically come and go from the network, and respond accordingly (i.e., mounting them when the networked connection is available, and unmount it when it disappears).  I find this useful for my laptop (which travels) and my desktop (which doesn't, but connects to several other computers that may or may not be on/present at any moment).  This approach does not require editing /etc/fstab, so may be of interest to those who simply do not wish to mess with that file, even if the network connects are always active.  This method also addresses a bug in Ubuntu 7.04 and below, and sometimes 7.10, where active network shares create large delays in the shutdown process.  As this approach uses only tools available to most/all Linux distros (certainly any Debian-based distro), it does not really depend on any particular version of Ubuntu.

Updated 27 June 2008 (see bottom of post for history/changes).
Note to those who used versions prior to 27 June 2008: the /etc/automount.bash script is now /usr/local/bin/automount; remove the /etc/automount.bash file and replace with the new /usr/local/bin/automount and update /etc/init.d/automount.

Please post all requests for help to the forum rather than as a private message, as if you have the question, chances are others will as well.

This howto replaces a previous howto of a similar nature for most, but not all applications, so I've created this new thread instead of replacing the old one: [http://ubuntuforums.org/showpost.php?p=2243984](http://ubuntuforums.org/showpost.php?p=2243984)

I am not going to explain how to get operational mounts.  There are already several locations that do a good job of explaining the process, such as:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)
[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

Three pieces are necessary for your shares to connect dynamically, aside from working network connections and the like.  I will not explain how to generate a working mount command line, as there are already several guides in the forums and elsewhere (see above).  Assuming that you have a working mount command line and wish to automate the (un)mounting:

**1.** Copy the following code and create a file called /etc/automount.conf (using sudo and your favorite editor), then replace my sample configuration with your own, using the examples and comments for guidance:
```
# all lines that begin with comments (#) or are entirely blank are ignored
# the order of the options, share, and mount do not matter; autocreate cannot be first
# avoid excess white space at beginning or end of the options, share, and mount lines

# lines beginning with autocreate turn on autocreation (and auto removal) of the last mount directory
#   Note that autocreation may sometimes fail to remove the mount directory if unmounting
#   is not complete when it tries to delete it.  This will not cause any side effects.
# lines beginning with - are options lines
# lines beginning with // are share lines
# lines beginning with delay= set the delay between pings on the shares (in seconds)
#   This line can appear anywhere, and multiple times, but only the last value is saved
#   If the line is absent, the script defaults to a value of 60
# all other lines are assumed to be the mount location line

# Due to limitations in matching existing mounts, no mount location should be a match
#   for a substring of a second mount
#   e.g., don't mount /media/blah and /media/blah2 or /blah
#   e.g., /media/blah, /media/2blah, and /mount/blah are all fine concurrently

delay=60

# desktopwired
-t cifs -o credentials=/etc/.credentials2,user,rw,uid=1000 
//192.168.10.171/c
/media/deskwired

# laptop
-t cifs -o credentials=/etc/.credentials1,user,rw,uid=1000
//192.168.10.180/c
/media/laptop
autocreate

# laptop2
-t cifs -o credentials=/etc/.credentials0,user,rw,uid=1000 
//192.168.100.181/c
/media/laptop2
autocreate

```
The .credentials files are a more secure way of storing username and password; see links below for details.  In the example cases (which are all samba/cifs, but need not be), the first mount does not automtaically create and destroy the mount point, so the folder must exist.  The other two will automatically create and destroy the mount point as the connections come and go.  Note that although I use IP addresses in the examples above, if you are running a wins server, have a local dns server, run dnsmasq on your router, or have the necessary information in your /etc/hosts file, you can use relative names instead of IP addresses directly.  (If you use relative addresses using wins and/or dns, you may get "unknown host" errors when trying to ping computers that are not currently online, but this is not a problem.)

**2.** Copy the following code and (using sudo and your favorite editor), create a file called /usr/local/bin/automount:
```
#! /bin/bash

# This periodically reads mtab check the status of nework shares,
# and unmounts recently inactive shares.  All inactive shares are then issued a
# ping.  Responsive systems are then mounted.

if [ $1 == start ]
then
  Command=0 # start
else
  if [ $1 == stop ]
  then
    Command=1 # stop
  else
    echo "Usage: automount {start|stop} FILE [-v]"
    echo "  Recommend usage is via /etc/init.d/automount."
    echo "  FILE is requried and should be the location of the configuration file."
    echo "  -v enables verbose mode to monitor process."
    echo
    exit 1
  fi
fi

Delay=60 # default number of seconds between checks
ConfFile=$2

if [ "$3" == "-v" ]
then
  VerboseMode=1
else
  VerboseMode=0
fi

# Read configuration file to get shares
i=0 # tracks number of shares/mounts
j=0 # tracks information for each share/mount to ensure gathers enough
while read line
do
  if [ `echo ${line}|grep -c '^[[:blank:]]*#'` -eq 0 ] # not a comment
  then
    if [ `echo ${line}|grep -c '[[:alnum:]]'` -eq 1 ] # not a blank line (strictly, a line that contains letters or numbers)
    then
      if [ `echo ${line}|grep -c '^[[:blank:]]*autocreate'` -eq 1 ] # autocreate tag
      then
        ShareMountAuto[$i]=1 # set autocreate on
      else
        if [ `echo ${line}|grep -c '^delay='` -eq 1 ] # delay line
        then
          Delay=`echo ${line}|awk -F = '{print $2;}'`
        else
          if [ $j == 3 ] # last share has completed information, start a new share
          then
            (( i++ )) # increment shares
            j=1 # reset information counter
            ShareMountAuto[$i]=0 # default no autocreate
          else
            (( j++ )) # increment information counter
          fi
          if [ `echo ${line}|grep -c '^//'` -eq 1 ] # share line
          then
            ShareAddresses[$i]=`echo "${line}"|awk -F / '{print $3;}'`
            Shares[$i]=${line}
          else
            if [ `echo ${line}|grep -c '^-'` -eq 1 ] # mount options line
            then
              ShareMountOptions[$i]=${line}
            else
              ShareMounts[$i]=${line} # assume mount line
            fi
          fi      
        fi
      fi
    fi
  fi
done < $ConfFile

if [ $VerboseMode == 1 ]
then
  # output result of parsing configuration file
  echo "Parsing $ConfFile produced following mount commands:"
  for (( i = 0 ; i < ${#Shares[@]} ; i++ ))
  do
    if [ ${ShareMountAuto[$i]} == 1 ]
    then
      echo "  (Autocreate)" ${ShareMountOptions[$i]} "${Shares[$i]}" "${ShareMounts[$i]}"
    else
      echo " " ${ShareMountOptions[$i]} "${Shares[$i]}" "${ShareMounts[$i]}"
    fi
  done
fi

if [ $Command -eq 0 ] # start
  then
    # Check status of all shares, every Delay seconds
    while [ 1 ]
    do
      for (( i = 0 ; i < ${#Shares[@]} ; i++ ))
      do
        if [ $VerboseMode == 1 ]
        then
          echo
          echo "Checking ${Shares[$i]}"
        fi
        if [ `grep -c "${ShareMounts[$i]}" /etc/mtab` -ne 0 ] # share is mounted, make sure still live
        then
          if [ $VerboseMode == 1 ]
          then
            echo "  ${Shares[$i]} is mounted"
          fi
          if [ $VerboseMode == 1 ]
          then
            ping -c 1 "${ShareAddresses[$i]}"
          else
            ping -c 1 "${ShareAddresses[$i]}" > /dev/null
          fi
          if [ $? -ne 0 ] # ping failed
          then
            if [ $VerboseMode == 1 ]
            then
              echo "  ${ShareAddresses[$i]} ping failed, beginning unmount"
            fi
            if [ $VerboseMode == 1 ]
            then
              umount -l "${ShareMounts[$i]}" # unmount
            else
              umount -l "${ShareMounts[$i]}" > /dev/null # unmount
            fi
            if [ ${ShareMountAuto[$i]} == 1 ] # auto create directory
            then
              if [ $VerboseMode == 1 ]
              then
                echo "  removing ${ShareMounts[$i]}"
              fi
              if [ $VerboseMode == 1 ]
              then
                rmdir ${ShareMounts[$i]} # delete mount directory
              else
                rmdir ${ShareMounts[$i]} 2> /dev/null # delete mount directory
              fi
            fi
          else
            if [ $VerboseMode == 1 ]
            then
              echo "  ${ShareAddresses[$i]} ping succeeded, keeping mount"
            fi
          fi
        else # share is not mounted
          if [ $VerboseMode == 1 ]
          then
            echo "  ${Shares[$i]} is not mounted"
          fi
          if [ $VerboseMode == 1 ]
          then
            ping -c 1 "${ShareAddresses[$i]}"
          else
            ping -c 1 "${ShareAddresses[$i]}" > /dev/null
          fi
          if [ $? -eq 0 ] # ping succeeded
          then
            if [ $VerboseMode == 1 ]
            then
              echo "  ${ShareAddresses[$i]} ping succeeded, beginning mount"
            fi
            if [ ${ShareMountAuto[$i]} == 1 ] # auto create directory
            then
              if [ $VerboseMode == 1 ]
              then
                echo "  creating ${ShareMounts[$i]}"
              fi
              mkdir "${ShareMounts[$i]}" # create mount directory
            fi
            if [ $VerboseMode == 1 ]
            then
              echo "  mounting ${ShareAddresses[$i]}"
            fi
            mount ${ShareMountOptions[$i]} "${Shares[$i]}" "${ShareMounts[$i]}" # mount
          else
            if [ $VerboseMode == 1 ]
            then
              echo "  ${ShareAddresses[$i]} ping failed, not mounting"
            fi
          fi
        fi
      done
      if [ $VerboseMode == 1 ]
      then
        echo
        echo "Waiting $Delay seconds...."
      fi
      sleep $Delay # sleep until next round of pings
    done
else # stop
    # Unmount all shares, whether known to be mounted or not
    if [ $VerboseMode == 1 ]
    then
      echo
      echo "Unmounting all automount shares..."
    fi
    for (( i = 0 ; i < ${#ShareMounts[@]} ; i++ ))
    do
      umount -l "${ShareMounts[$i]}" 2> /dev/null # unmount
      if [ ${ShareMountAuto[$i]} == 1 ] # auto create directory
      then
        if [ $VerboseMode == 1 ]
        then
          rmdir "${ShareMounts[$i]}" # remove mount directory
        else
          rmdir "${ShareMounts[$i]}" 2> /dev/null # remove mount directory
        fi
      fi
    done
fi

exit 0

```
then:
```
sudo chmod 755 /usr/local/bin/automount
```to make it executable.

**3:** Copy the following and (using sudo and your favorite editor) paste it into a file called /etc/init.d/automount:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          N/A
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Automounts SAMBA shares
# Description:       Dynamically (un)mounts specific SAMBA shares.
### END INIT INFO

# Set info for messages
DESC="Automount shares"
NAME=automount
SCRIPTNAME=/etc/init.d/$NAME
DAEMON=/usr/local/bin/$NAME
PIDFILE=/var/run/$NAME.pid

# Exit if the daemon script is not installed
[ -x "$DAEMON" ] || exit 0

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

do_start()
{
  echo "Starting automount..."
  start-stop-daemon --start --quiet --background --make-pidfile --pidfile $PIDFILE --exec $DAEMON --test > /dev/null || return 1
  start-stop-daemon --start --quiet --background --make-pidfile --pidfile $PIDFILE --exec $DAEMON -- start $ConfFile || return 2
}

do_stop()
{
  echo "Stopping automount and unmounting..."
  start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
  RETVAL="$?"
  [ "$RETVAL" = 2 ] && return 2
  # Execute again w/ stop to unmount all
  $DAEMON stop $ConfFile
  rm -f $PIDFILE
  return "$RETVAL"
}

do_pause()
{
  echo "Stopping automount..."
  start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
  RETVAL="$?"
  [ "$RETVAL" = 2 ] && return 2
  rm -f $PIDFILE
  return "$RETVAL"
}

if [ "$2" = "" ] # no config file passed
then
  ConfFile=/etc/automount.conf # default configuration file
else
  ConfFile=$2
fi

case "$1" in
  start)
    [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
    do_start
    case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    exit "$?"
    ;;
  stop)
    [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
    do_stop
    case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    exit "$?"
    ;;
  force-reload|restart)
    [ "$VERBOSE" != no ] && log_daemon_msg "Restarting $DESC" "$NAME"
    do_stop
    case "$?" in
      0|1)
        do_start
        case "$?" in
          0) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
          1) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Old process is still running
          *) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Failed to start
        esac
        exit "$?"
        ;;
      *)
        # Failed to stop
        [ "$VERBOSE" != no ] && log_end_msg 1
        exit "$?"
        ;;
    esac
    ;;
  pause)
    [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
    do_pause
    case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    exit "$?"
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|pause} [FILE]"
    echo "  /etc/automount.conf will be used if FILE is not specified."
    exit 3
    ;;
esac

exit

```
then:
```
sudo chmod 755 /etc/init.d/automount
```to make it executable.
then:
```
sudo update-rc.d automount defaults 99 01
```
to automatically start and stop the (un)mounting script upon boot and shutdown.

**Uninstallation**:
Delete the three files you created, then:
```
sudo update-rc.d automount remove
```

**---Additional notes---**
This approach assumes that either the computer is used by a single user, or that all users will share the shares.  Unfortunately, due to the fact that mount requires root access, there is not a simple way to implement this in user space.  I am working on a revised script that will deal with this problem, but it may take a while.  In the meantime, you can either use the old version linked above, or a similar approach using these files.  First, create your automount.conf in a local directory.  Skip step 3; instead, use:
```
automount start FILE
```
to invoke the script upon logging in, where FILE is the path to your automount.conf file.  (For logging out, replace "start" with "stop" in your logout script file, or just ignore it and let the shares be taken of by normal procedures upon shutdown.)  You will then also need to chmod +s the appropriate mount commands as described in [http://ubuntuforums.org/showpost.php?p=2243984](http://ubuntuforums.org/showpost.php?p=2243984).

You could also make use of the ability to pass a config file to automount, so that intead of the above, you can use the full setup only without creating the /etc/automount.conf file, so that /etc/init.d/automount simply fails to start upon boot, then invoke /etc/init.d/automount start FILE upon each user login, where FILE is their personal config file, the problem being that /etc/init.d/automount must be started with root priveleges, so users need to enter the root password - it may be possible to set up a system using keyring logins, etc. to avoid the need for manual entry here, but I'm going to leave that purely as an exercise for anyone wanting to try it.

See [http://ubuntuforums.org/showpost.php?p=2589255&postcount=14](http://ubuntuforums.org/showpost.php?p=2589255&postcount=14) for an example of how to start/stop the script only when connected to the network, so you aren't pinging endlessly for no reason.  The example uses the old version of this script, but you can use /etc/init.d/automount start and /etc/init.d/automount stop to start and stop the scripts instead of the commands given.

automount can be invoked directly with detailed monitoring of processes using
```
sudo /usr/local/bin/automount start /etc/automount.conf -v
``` or (assuming /usr/local/bin is in your path, which it should be)
```
sudo automount start /etc/automount.conf -v
```
to troubleshoot mounts that don't appear to be working.

**---History---**
2007-12-10: Original post
2008-01-21: Fixed issue with paths containing spaces in automount.bash
2008-01-25: Added verbose mode to automount.bash, made passing of config file to automount.bash mandatory, and added ability to pass config file to automount
2008-05-11: Minor updates to text, no changes to scripts.
2008-06-27: Revised /etc/init.d script to conform to Debian standards.  Relocated main script to /usr/local/bin/automount instead of /etc/automount.bash, and modified output to silence most errors/standard out messages unless -v passed to script.

---

### Post by fiatguy85 on 2008-01-20
Thank you very useful!  I am having one problem though.  A disk I want to mount contains a space in the path and it cannot be changed.  This command will work:

```
sudo mount -t cifs -o credentials=/root/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777 //storagebob/Disk\ 2 /media/Net2
```

But the config lines below will not:

```
# Net 2
-t cifs -o credentials=/root/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777
//storagebob/Disk\ 2
/media/Net2
```

mount will not accept the \040 for a space as it will in the fstab file.  Supposedly mount will accept the path if it is surrounded with single or double quotes, but then you script will not determine that to be the pathline and it also fails.  Other than this it works wonderfully!  Thanks!

---

### Post by tweedledee on 2008-01-21
Should be fixed.  Update your automount.bash with the revised code above, nothing else should need to be changed.

---

### Post by fiatguy85 on 2008-01-21
Thanks for the quick fix!  Works perfectly!  Also fixed my hang on shutdown from not unmounting the drives.

---

### Post by jesrani on 2008-01-25
Hello. I have setup Ubuntu 7.10 desktop in a network of ten Win98 and two Xp computers. Each computer has one folder "Documents" shared through password. I can see all the computers from Places --> Network and can access if I provide the user name and password. I have made a folder /network (under /root folder) and then sub-folders like /network/coating, /network/maintainance etc for each computer. I want to mount each computer's shared "Documents" folder under these subfolders and then backup these folders (using rsync?) to another hdd.I was able to do this by editing fstab but it took a long time to boot. Also all computers were not always online and that meant an empty folder under /network. So I assume that rsync would also make the destination empty, which is not what I want. I want it to be like "Mapping drivs in XP", if the network is not connected, the source itself is not present so the backup software (I use SyncBack on XP) returns an error but the destination is not deleted.
Reading your HOW To, I created the 3 files. I made changes in the automount.conf file only as under :

# Coating (Win98)
-t smbfs -o username=user,password=pass,user,rw,uid=1000 
//coating/documents
/network/coating
autocreate

# Maintainance (XP)
-t cifs -o username=user,password=pass,user,rw,uid=1000
//maintainance/documents
/network/maintainance
autocreate

I also followed other instructions, but nothing is happening. the sub-folders under /network are all empty. nothing is getting mounted. Please advice. I have added wins at the end of the hosts: line in nsswitch.conf and winbind is also installed.

My fstab is as under (I ahve put # on some lines to remove the mounts on boot)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d3899dc6-d2c3-442d-a679-b026cdb1ba60 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda5 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /BackupDisk ext3 defaults 0 0
# 20/01/08 : hbj : mount Win98 computers through smbfs and xp through cifs
#//coating/documents /network/coating smbfs username=user,password=pass,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#//maintainance/documents /network/maintainance cifs username=user,password=pass,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

### Post by tweedledee on 2008-01-25
> **jesrani said:**
> Reading your HOW To, I created the 3 files.

Everything appears to be correct, so I'm not sure where the problem is arising yet.  I have updated both automount and automount.bash in the original post, please replace your existing ones with those, after running
```
sudo /etc/init.d/automount stop
```to stop the existing script.  Once you have the scripts updated, execute
```
sudo /etc/automount.bash start /etc/automount.conf -v
``` (or wherever your automount.conf file is) and post the output of one round (everything from when you first start to the "waiting" message), pressing "Ctrl+C" to kill the script at that point.

You may be able to resolve the problem yourself from the new verbose output, if it's made obvious, in which case just update your .conf file accordingly and you're all set after restarting /etc/init.d/automount (and you don't need to post the output, just that you fixed it).

---

### Post by jesrani on 2008-01-27
thanks a lot for the update. when i ran the command 
Code: sudo /etc/init.d/automount stop,
I got the error command not found.
i updated the 2 files and ran the other command anyhow and now the mounts are getting mounted.
now i have another requirement. one of the mounts is through an admin password but i want to make the mounts readonly, is it possible?
what do you think of using rsync for backing up? in xp i use SyncBack for Synchronizing and Cobian Backup for backups. I could not find anything like Cobian for Ubuntu. However from another thread I had opened, it seems that rsync will be ok for sync. i want the mount to be readonly so that i cant delete anything in the other computer by mistake.

---

### Post by tweedledee on 2008-01-27
> **jesrani said:**
> now i have another requirement. one of the mounts is through an admin password but i want to make the mounts readonly, is it possible?
Replace the "rw" in the mount options with just "r" and you'll remove write access.
> **jesrani said:**
> what do you think of using rsync for backing up? in xp i use SyncBack for Synchronizing and Cobian Backup for backups. I could not find anything like Cobian for Ubuntu. However from another thread I had opened, it seems that rsync will be ok for sync. i want the mount to be readonly so that i cant delete anything in the other computer by mistake.
I've not actually used rsync.  I suspect it will work fine for what you want to do.  My understanding of how it works is that it is actually unidirectional anyway; i.e., to truly "sync" as SyncBack uses the term, you'd have to run rsync twice, once in each direction.  There are also some GUIs for rsync, one or two of which I have tried but found horribly slow.  I actually use a custom program for my own backups, that I'm hoping to get in a publishable state sometime in the next few months, but that obviously doesn't help your immediate problem.  Certainly rsync is extremely popular around these forums.  There are at least a couple of threads with decent discussions of backup/sync software if you search for them.

---

### Post by jesrani on 2008-01-28
The shares are not getting mounted when i start the computer. but when i ran the command
sudo /etc/automount.bash start /etc/automount.conf -v
it mounted the shares. somehow the folders for the shares were still present and it mounted in these folders. but there was write access in the share with admin password. then i used the same command above with "stop" instead of "start" and it unmounted and removed the shares. then i again ran with "start" and it created the folders and mounted. but i still had write access even though i had changed "rw" to "r".
Then I ran the command again and it reported both shares as mounted so did not mount again. I let it run for the 60 secs and it reported the same thing again. so it works but not on startup.
please advice.

---

### Post by tweedledee on 2008-01-28
> **jesrani said:**
> The shares are not getting mounted when i start the computer. but when i ran the command
sudo /etc/automount.bash start /etc/automount.conf -v
it mounted the shares. somehow the folders for the shares were still present and it mounted in these folders. but there was write access in the share with admin password. then i used the same command above with "stop" instead of "start" and it unmounted and removed the shares. then i again ran with "start" and it created the folders and mounted. but i still had write access even though i had changed "rw" to "r".
Then I ran the command again and it reported both shares as mounted so did not mount again. I let it run for the 60 secs and it reported the same thing again. so it works but not on startup.
please advice.

Regarding the mounting on startup, did you run the "update-rc.d" command in the orignal post?  Try executing it again; if it complains that links already exist (as opposed to saying it has created several), then try removing the /etc/init.d/automount, running the 2nd "update-rc.d" command to remove the links, re-create /etc/init.d/automount, and running "update-rc.d" again.

On your read/write problem, I'm not sure what the issue is.  I'd suggest a search through the forums for postings by someone more knowledgeable than me about such details.

---

### Post by jesrani on 2008-01-28
I had run the command initially, I think. Anyway I solved the problem. I checked the "automount" file under /etc/init.d and it did not have permission to run as an executable.  checked that option and now it is ok. as for the read / write thing, I will try to find on the forum. thanks a lot for your help.

---

### Post by MunkyJunky on 2008-05-25
This looks very handy for me, but I'm having a few problems. It will mount files when I type a terminal command to do something with automount.conf, the only problem is it wont mount shares at boot. I feel this is a problem to do with my /etc/init.d/automount file, as a **Sudo /etc/init.d/automount stop** generates the error '*sudo: /etc/init.d/automount: command not found*.

I copied the file exactly as in the original post (in fact, the only change I have made was the network shares in automount.conf to mount my own network share. 

Any ideas on how to remedy this? I presume I've just made a simple mistake which is breaking it all.

---

### Post by tweedledee on 2008-05-25
> **MunkyJunky said:**
> Any ideas on how to remedy this? I presume I've just made a simple mistake which is breaking it all.

Chmod 755 the /etc/init.d/automount - it's probably not executable.  It appears I forgot that step in the original post and have just updated it.

---

### Post by MunkyJunky on 2008-05-25
Thanks, that seems to have fixed it. I haven't tried a reboot yet, but I can stop/start it through terminal, which I couldn't before.

---

### Post by Harry Muscle on 2008-06-27
Wondering if someone could give me a hand ... I've followed all the steps in the first post, making sure to make all the required files executable, however, when I try to run:

sudo /etc/automount.bash start /etc/automount.conf -v

I get the following error:

sudo: unable to execute /etc/automount.bash: No such file or directory

I've double check and tripple checked to make sure that it's set as an executable file, and it is, for the owner, group, and others.

Any idea what might be up?

Thanks,
Harry

P.S.  I'm running Ubuntu Hardy.

P.P.S.  When I try to run the above command without sudo, I get this error:

bash: /etc/automount.conf: /bin/bash^M: bad interpreter: No such file or directory

Not sure if it gives anyone any clues as to what might be wrong.  Thanks again.

---

### Post by tweedledee on 2008-06-27
Could be an apparmor and/or SELinux problem, if you are running either or both (apparmor is default).  I've just posted an update to the setup that I've had ready for a few weeks and hadn't gotten around to updating that conforms better to Linux standards.  Update your /etc/init.d/automount with the new version I have posted, delete /etc/automount.bash, and create /usr/local/bin/automount from the revised original post.  Hopefully that will address the problem, as well as providing a slightly improved setup.

---

### Post by untoldone on 2008-08-13
So I'm not entirely sure whats going on ... but about 1 in 4 of my shares fail to be unmounted when the host goes down using this script.  I have a hunch its not a problem with the script itself but rather a problem with cifs.  I think its a similar issue to that of the problem some are having with umounts hanging at shutdown (umount times out because network manager shuts down before the share unmounts, then the umount command hangs).  According to the man pages for mount.cifs, the soft option (default) specifies that actions should not hang but this option does actually seem to work all that well.  I found a posting on the samba list at [http://lists.samba.org/archive/linux-cifs-client/2006-March/001215.html](http://lists.samba.org/archive/linux-cifs-client/2006-March/001215.html) but there was no follow up which makes me believe soft is not actually implemented well and I could not find more recent discussion of the soft option.  Anyways -- did you ever have issues with umounts hanging while using your script, if so, did you ever find a resolution?

---

### Post by tweedledee on 2008-08-13
> **untoldone said:**
> Anyways -- did you ever have issues with umounts hanging while using your script, if so, did you ever find a resolution?

Your evaluation is fairly accurate.  The short answer to your question is "yes I do, and no I haven't," but I may be able to address the problem.  I see two types of umount hangs while running this script, both ultimately caused by the long-standing bug in CIFS.

The first hang is when computer 1 has an active share with computer 2, but computer 2 drops the connection (e.g., when it is turned off), and I shutdown or hibernate computer 1 before the script has had time to call umount; in this case, shutdown leads to the standard hanging umount that takes a minute or two to quit, while hibernate fails (and eventually returns to the desktop), but will be successful once the script makes the umount call.  As far as I can tell, the only way to deal with this would be to use a shorter delay (maybe 10 seconds instead of 60) between pings to increase the probability that computer 1 disconnects before you request shutdown; I just live with it, since I don't see it frequently.

The second case, which I've not extensively examined, may be due to having many shares (> 3-4) active when calling shutdown.  I've not spent time sorting this out, because I rarely shutdown (usually I hibernate, where this isn't an issue), and I only occasionally have more than 2 live connections.  If you reproducibly see that having 4 shares causes 1 to not disconnect in time, but having 3 works fine, I may be able to tune the script to either umount faster during shutdown or cause it delay the shutdown process until all umounts are complete.

The real solution, of course, is for the CIFS bug to get fixed, and then I wouldn't need to worry about the shutdown issue at all.  However, it doesn't seem likely to be resolved soon.

---

### Post by untoldone on 2008-08-16
Thank for the reply.  I'll try to keep track of how often my shares fail to umount over the next month and play around with the number of shares that are checked by the script.  This behavior I listed above was actually just what I observed when disconnecting a line between two switches to test the setup (neither computer lost a network connection -- the two computers just lost the ability to communicate with each other).  But I will see how this works in everyday use.

---

### Post by log on 2009-07-01
Awesome. This solves so many problems!

I have a mythbox with a video directory that has SMB mounts to all of the computers in the house. The problem is that those computers aren't always on.

I wish smbmount would just recognise that the host is down and auto-unmount :(

However, this fixes it :)

Cool :guitar:

---

### Post by mollydoggy1971 on 2010-04-14
This appears to be a wonderful solution (I think) for me.  I need to mount networked drives so that they are accessible in other programs in Ubuntu, such as a music player.  All my audio files are on an external drive attached to my Windows 7 machine.  I can access the drive through the file manager, but not in my programs.  
My real problem is this - I am a noob when it comes to Linux, and do not understand what it is that I'm being asked to do in the first post of this thread.  Is there anyone out there who could explain it to me in more simple steps?  For example, it says something about using sudo and your favorite editor.  I don't know what sudo nor an editor are.  This may help to explain the level of expertise I have.  Please, explain it to me in VERY basic terms.  I take notes on everything I do, so that I can learn from my procedures.  
I thank you in advance for your help.

---

### Post by tweedledee on 2010-04-15
> **mollydoggy1971 said:**
> Is there anyone out there who could explain it to me in more simple steps?  For example, it says something about using sudo and your favorite editor.  I don't know what sudo nor an editor are.  This may help to explain the level of expertise I have.  Please, explain it to me in VERY basic terms.  I take notes on everything I do, so that I can learn from my procedures.  
I thank you in advance for your help.

All the commands below need to be entered into a terminal (command prompt) window.  I'm assuming you have "normal" Ubuntu installed.  If you are running Xubuntu, replace all "gedit" below with "mousepad".  If Kubuntu, replace all "gedit" with "kate".  All of those are just default graphical text editors.  After each of the commands below, paste in the text provided in the first post.  You'll need to customize the text for step 1 to match your system, referring to one of the links provided.  "sudo" is just a way of saying "execut the following command as root" so that you can access areas of your system normally not writeable by users.  You will be prompted for your password after the first use of sudo, and then again if more than 15 minutes (by default) has passed since your last use of it.
```

1. sudo gedit /etc/automount.conf
2. sudo gedit /usr/local/bin/automount
2b. sudo chmod 755 /usr/local/bin/automount
3. sudo gedit /etc/init.d/automount
3b. sudo chmod 755 /etc/init.d/automount
3c. sudo update-rc.d automount defaults 99 01
3d. sudo /etc/init.d/automount start

```
If you wish to create a .credentials file for the logins in automount.conf (examples of that are provided in one or more of the links on setting up mounts), you can just use "sudo gedit /root/.credentials" to open that file for editing, then paste in the appropriate information.

Note that Ubuntu has changed to "Upstart" as their boot service since I wrote these scripts.  In theory, the startup script piece should still work, but if you get an error with step 3c or 3d, you may be out of luck without adapting this (beyond what I can help with, as I run pure Debian, don't use Upstart, and actually don't use window-mounts any more either so use a somewhat modified version of what's posted here).

If you try this and run into specific problems, I may be able to help you further.

---

### Post by mollydoggy1971 on 2010-04-16
Thanks for the explanation.  I'll give it a shot on my next day off and let you know how it goes!

---

### Post by jesrani on 2010-05-27
Hello,

I am using Ubuntu in an small network of XP computer for backup and this method works perfectly for me since more than 1 year. But there is a small problem that I want to overcome.
When the computer starts the shares are mounted automatically. But if there is a power failure and the computer is rebooted, the folder created automatically is still available and shows 0 items under it. If the particular share is online it is again mounted to the folder but in case that particular computer is down the folder remains with 0 items. In this scenario, if an automated backup is run by Cron the backed up folder also have everything under it deleted.
Hence I need to run the commands "sudo /etc/init.d/automount stop" and then "sudo /etc/init.d/automount start" when the computer starts. Is this possible?
Or can anything be changed in the automount file to give the stop command before running?

---

### Post by tweedledee on 2010-05-27
> **jesrani said:**
> Hence I need to run the commands "sudo /etc/init.d/automount stop" and then "sudo /etc/init.d/automount start" when the computer starts. Is this possible?
Or can anything be changed in the automount file to give the stop command before running?

The simplest solution would be to edit the /etc/init.d/automount script to include the line "do_stop" immediately before "do_start" under the "start)" portion of the case statement.  That essentially makes start equivalent to restart and will trigger the cleanup steps.  More elegant (and complicated) solutions are possible, but for the situation you describe and assuming it otherwise works automatically, that should take care of it.

---

### Post by thebighere on 2010-06-14
thank you so much for this script - it is working beautifully after much trouble trying to find another solution

however, i am on open suse, and i am getting this complaint when i try to automate:

/etc/init.d/automount: line 23: /lib/init/vars.sh: No such file or directory

I can't seem to find the equivalent in opensuse - any ideas?

thanks again

---

### Post by tweedledee on 2010-06-14
> **thebighere said:**
> thank you so much for this script - it is working beautifully after much trouble trying to find another solution

however, i am on open suse, and i am getting this complaint when i try to automate:

/etc/init.d/automount: line 23: /lib/init/vars.sh: No such file or directory

I can't seem to find the equivalent in opensuse - any ideas?

thanks again
That comes in with the "initscripts" package that is default in Debian; there may an equivalent in openSUSE, but there's a simpler change you can make.  Just delete that line and add```
VERBOSE=no
``` (or yes, depending on your logging preference) to the other variable definitions above the line.  You shouldn't need anything else that line triggers for the script to work, and should also be able to delete the lsb script call below it if that is a problem.

Actually, I'm not sure openSUSE will interpret any of the huge comment block above either, but that's at least not going to cause the script to crash (it only regulates boot order).

---

### Post by guimenez on 2010-10-07
Please, i'm using pam_mount.conf.xml to mount my shares and it works well.
But when i make logoff my Ubuntu 10.04 LTS always crash and i just see the mouse cursor.

Please can you help me?

many thanks

---

### Post by tweedledee on 2010-10-08
> **guimenez said:**
> Please, i'm using pam_mount.conf.xml to mount my shares and it works well.
But when i make logoff my Ubuntu 10.04 LTS always crash and i just see the mouse cursor.

Please can you help me?

many thanks

Sorry, I have almost no experience with using pam directly, and what I have tried never worked.  I'd suggest starting a new thread and hope someone with more experience volunteers something.

---

### Post by jesrani on 2012-02-27
I am suddenly having a problem in this script after using successfully since past number of years. I have created a new thread in the general forum, [http://ubuntuforums.org/showthread.php?t=1932185](http://ubuntuforums.org/showthread.php?t=1932185).
I hope someone can assist me on this.

---

### Post by midenok on 2012-05-19
How about [SMBNetFS]("http://sourceforge.net/projects/smbnetfs/")? Even with AutoFS (to start/stop smbnetfs)...

---

