---
title: "CD cmd fails in rc.2/init.d script"
date: 2011-08-15
forum: Server Platforms
---

### Post by DCBSupafly on 2011-08-15
Below is the section of my boot.log where error occurs.  The minecraft server wrapper I have works great when I call it manually, but fails on boot.  **Problem seems to be with the cd cmd of all things.  **Do I need to refer to this path differently because I'm not logged in at this point?

boot.log
```
Starting craftbukkit-0.0.1-SNAPSHOT.jar...
/etc/rc2.d/S20minecraft: line 42: cd: /home/dcb/MCServ/server: No such file or directory
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
-su: line 0: cd: /home/dcb/MCServ/server: No such file or directory
 * Stopping CPU interrupts balancing daemon                                                                              [ OK ]
Error! Could not start craftbukkit-0.0.1-SNAPSHOT.jar!
 * Starting web server apache2                                                                                           [ OK ]
 * Stopping System V runlevel compatibility                                                                              [ OK ]
dcb@ubuntuSupa:/var/log$

```successful cd cmd to verify lack of typo!
```

dcb@ubuntuSupa:/etc/init.d$ cd /home/dcb/MCServ/server/
dcb@ubuntuSupa:~/MCServ/server$

```

---

### Post by maikel.b on 2011-08-15
Can you edit this script /etc/rc2.d/S20minecraft manual?

Otherwise i think that is have a solution for you??

If so let me know, i believe the script needs a other option...

Wait i will find it for you! 10 minutes!

---

### Post by maikel.b on 2011-08-15
Try to edit the /etc/rc2.d/S20minecraft

and change the cd in /bin/cd /home/dcb/MCServ/server

reboot the server and test again.

Good luck

---

### Post by maikel.b on 2011-08-15
If this won't work change the access to your folder with chmod -R 777 /home/dcb/MCServ/server/

i am not sure if this works, i hope this will work for you..

Did you have a update or something? 

Kind regards 

Maikel and good luck, if this didn't work?? Change the script and settings back to the default...

This for security reasons..!!!

---

### Post by DCBSupafly on 2011-08-15
Hey thanks for the help maikel.b.  I will post as soon as I can reboot, probably this afternoon.  btw I didn't see cd in the /bin folder, should I?

---

### Post by maikel.b on 2011-08-15
Nope your right!!

I think that my solution won't work!!

I installed fast a ubuntu 11.04 server, and checked the /bin folder.

And there is no cp script in these!! 

I can't help you with these one... sorry..

Maybe you can try the chmod -R 777 and the folder that needs access on the boot!

Hope this one works!!!

kind regards!

---

### Post by DCBSupafly on 2011-08-16
Thanks for the help, I did try chmod 777 on the folder but to no avail.  The error is the same.
Just to confirm that I have set the permissions correctly, all permissions are allowed below, right?

```
dcb@ubuntuSupa:~/MCServ$ ls -l
total 12
drwxr-xr-x 12 dcb dcb 4096 2011-08-16 03:30 backups
drwxrwxrwx  8 dcb dcb 4096 2011-08-16 12:22 server
drwxr-xr-x  3 dcb dcb 4096 2011-08-11 21:02 Tectonicus
dcb@ubuntuSupa:~/MCServ$

```

Is there a chance that referring to this path differently for the init.d/rc2.d scripts will help?  Is there ever a time to use $HOME vs ~/ vs /home/dcb/?

Is it possible that the partition is not mounted at this point or the user files are encrypted or otherwise made inaccessible because of the time at which the script is run?  Is there a later time to call something like this to test that idea?

---

### Post by DCBSupafly on 2011-08-16
BTW Below is the script I run, with my own variables set.  It has been very useful with the cronjob I have made for backups, but I'd really like it to run at boot!  You can see the original here: [http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

```
dcb@ubuntuSupa:~/MCServ$ cat /etc/init.d/minecraft
#!/bin/bash
# /etc/init.d/minecraft
# version 0.3.4 2011-06-12 (YYYY-MM-DD)

### BEGIN INIT INFO
# Provides:   minecraft
# Required-Start: $local_fs $remote_fs
# Required-Stop:  $local_fs $remote_fs
# Should-Start:   $network
# Should-Stop:    $network
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description:    Minecraft server
# Description:    Starts the minecraft server
### END INIT INFO

#Settings
SERVICE='craftbukkit-0.0.1-SNAPSHOT.jar'
OPTIONS='nogui'
USERNAME='dcb'
WORLD='SupaReset'
MCPATH='/home/dcb/MCServ/server/'
BACKUPPATH='/home/dcb/MCServ/backups/'
CPU_COUNT=1
INVOCATION="java -XX:+UseConcMarkSweepGC -XX:+CMSIncrementalPacing -XX:ParallelGCThreads=$CPU_COUNT -XX:+AggressiveOpts -jar $SERVICE $OPTIONS"

ME=`whoami`
as_user() {
  if [ $ME == $USERNAME ] ; then
    bash -c "$1"
  else
    su - $USERNAME -c "$1"
  fi
}

mc_start() {
  if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
  then
    echo "$SERVICE is already running!"
  else
    echo "Starting $SERVICE..."
    cd $MCPATH
    as_user "cd $MCPATH && screen -dmS minecraft $INVOCATION"
    sleep 7
    if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
    then
      echo "$SERVICE is now running."
    else
      echo "Error! Could not start $SERVICE!"
    fi
  fi
}

mc_saveoff() {
  if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
  then
    echo "$SERVICE is running... suspending saves"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"say SERVER BACKUP STARTING. Server going readonly...\"\015'"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"save-off\"\015'"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"save-all\"\015'"
    sync
    sleep 10
  else
    echo "$SERVICE is not running. Not suspending saves."
  fi
}

mc_saveon() {
  if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
  then
    echo "$SERVICE is running... re-enabling saves"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"save-on\"\015'"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"say SERVER BACKUP ENDED. Server going read-write...\"\015'"
  else
    echo "$SERVICE is not running. Not resuming saves."
  fi
}

mc_stop() {
  if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
  then
    echo "Stopping $SERVICE"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"say SERVER SHUTTING DOWN IN 10 SECONDS. Saving map...\"\015'"
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"save-all\"\015'"
    sleep 10
    as_user "screen -p 0 -S minecraft -X eval 'stuff \"stop\"\015'"
    sleep 7
  else
    echo "$SERVICE was not running."
  fi
  if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
  then
    echo "Error! $SERVICE could not be stopped."
  else
    echo "$SERVICE is stopped."
  fi
}

mc_update() {
  if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
  then
    echo "$SERVICE is running! Will not start update."
  else
    MC_SERVER_URL=http://www.minecraft.net/download/minecraft_server.jar?v=`date | sed "s/[^a-zA-Z0-9]/_/g"`
    as_user "cd $MCPATH && wget -q -O $MCPATH/minecraft_server.jar.update $MC_SERVER_URL"
    if [ -f $MCPATH/minecraft_server.jar.update ]
    then
      if `diff $MCPATH/$SERVICE $MCPATH/minecraft_server.jar.update >/dev/null`
      then
        echo "You are already running the latest version of $SERVICE."
      else
        as_user "mv $MCPATH/minecraft_server.jar.update $MCPATH/$SERVICE"
        echo "Minecraft successfully updated."
      fi
    else
      echo "Minecraft update could not be downloaded."
    fi
  fi
}

mc_backup() {
   echo "Backing up minecraft world..."
   if [ -d $BACKUPPATH/${WORLD}_`date "+%Y.%m.%d_%H.%M"` ]
   then
     for i in 1 2 3 4 5 6
     do
       if [ -d $BACKUPPATH/${WORLD}_`date "+%Y.%m.%d_%H.%M"`-$i ]
       then
         continue
       else
         as_user "cd $MCPATH && cp -r $WORLD $BACKUPPATH/${WORLD}_`date "+%Y.%m.%d_%H.%M"`-$i"
         break
       fi
     done
   else
     as_user "cd $MCPATH && cp -r $WORLD $BACKUPPATH/${WORLD}_`date "+%Y.%m.%d_%H.%M"`"
     echo "Backed up world"
   fi
   echo "Backing up $SERVICE"
   if [ -f "$BACKUPPATH/minecraft_server_`date "+%Y.%m.%d_%H.%M"`.jar" ]
   then
     for i in 1 2 3 4 5 6
     do
       if [ -f "$BACKUPPATH/minecraft_server_`date "+%Y.%m.%d_%H.%M"`-$i.jar" ]
       then
         continue
       else
         as_user "cd $MCPATH && cp $SERVICE \"$BACKUPPATH/minecraft_server_`date "+%Y.%m.%d_%H.%M"`-$i.jar\""
         break
       fi
     done
   else
     as_user "cd $MCPATH && cp $SERVICE \"$BACKUPPATH/minecraft_server_`date "+%Y.%m.%d_%H.%M"`.jar\""
   fi
   echo "Backup complete"
}

mc_command() {
  if [ "$1" ]
  then
    command="$1";
    if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
    then
      echo "$SERVICE is running... executing command"
      as_user "screen -p 0 -S minecraft -X eval 'stuff \"$command\"\015'"
    fi
    else
      echo "Must specify server command"
  fi
}

#Start-Stop here
case "$1" in
  start)
    mc_start
    ;;
  stop)
    mc_stop
    ;;
  restart)
    mc_stop
    mc_start
    ;;
  update)
    mc_stop
    mc_backup
    mc_update
    mc_start
    ;;
  backup)
    mc_saveoff
    mc_backup
    mc_saveon
    ;;
  status)
    if ps ax | grep -v grep | grep -v -i SCREEN | grep $SERVICE > /dev/null
    then
      echo "$SERVICE is running."
    else
      echo "$SERVICE is not running."
    fi
    ;;
  command)
    mc_command "$2"
    ;;

  *)
  echo "Usage: /etc/init.d/minecraft {start|stop|update|backup|status|restart|command \"server command\"}"
  exit 1
  ;;
esac

exit 0

```I wonder if the as_user part before the cd command could be a problem.  dcb is my only user on the server, and when i tried specifying another user, the script did not work at all. (I presume because the user needs to exist in the OS first.)  Still, the folder that is triggering the error is owned by dcb anyway...

---

### Post by maikel.b on 2011-08-16
Hello, sorry for my late reaction!!

This script needs to access your home folder.. 

I got a question, do you have a encrypted home folder?

When you boot the server, do you need to fill in a password to access your home folder?

There is a option to encrypt your folders in Ubuntu server, and maybe if you use this option?? The script can't access these folder due the encryption that not has been activated at the boot moment??

Kind regards Maikel.

---

### Post by DCBSupafly on 2011-08-16
I did use the option to encrypt my /home folder when I installed Ubuntu.  No particular reason other than it sounded like a good idea.  How do I deal with this if I want to have scripts in there that need to run on boot?  Should I not have my home folder encrypted?

---

### Post by maikel.b on 2011-08-16
Oke, I believe this is the problem!!!

I will try to find a solution for you to disable this option...

---

### Post by maikel.b on 2011-08-16
One time I installed a server with the encryption option on, but I didn't like this option..

I got 2 servers running here, and these server don't use a screen..

Every boot I had to put in the decryption code before I can use the server...

So I never had this problem that you are dealing with..

If this server is new..?? And there is not so many data on it?? 

Reinstall the machine, and don't encrypt your home space!!

Or this article can help you??

[http://askubuntu.com/questions/9922/how-do-i-disable-the-home-encryption-offered-during-install](http://askubuntu.com/questions/9922/how-do-i-disable-the-home-encryption-offered-during-install)

Please lookout and be careful with your data!!!

I hope this will help you.. I never used this article, but maybe it can help you!!!

Kind regards

Maikel

---

### Post by maikel.b on 2011-08-30
Hi,
 
Is the problem solved???
 
Kind regards 
 
Maikel

---

### Post by DCBSupafly on 2011-08-30
I was in the process of moving the installation to a new machine, so this time I did not encrypt, and it seems to work fine!  Thanks for helping me figure that out, I only wish there were a way to keep the home folder encrypted and still call the script at boot.  I guess the answer there is to move the script outside of my home folder.

Thanks!

---

