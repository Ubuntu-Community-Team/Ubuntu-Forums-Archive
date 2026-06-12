---
title: "&quot;Screen&quot; Blues - A Minecraft Setup Story"
date: 2017-06-11
forum: Server Platforms
---

### Post by nightraver on 2017-06-11
Hello Ubuntu Community!

Relatively new Ubuntu user here hoping to get some assistance on a long-standing issue I've been trying to solve through screen.

So, long story short: I've been trying to get my Minecraft server to run through a screen instance to allow access in the event of some unforseen lockout from the client software. I have been trying to accomplish this through the use of a simple screen script placed in a larger script given to me via the mod group I have been using (FTB).

The code in question is as follows:

```
start_server() {   
sudo screen -SL minecraft "$JAVACMD" -server -Xms${MIN_RAM} -Xmx${MAX_RAM} -XX:PermSize=${PERMGEN_SIZE} ${JAVA_PARAMETERS} -jar ${FORGEJAR} nogui
echo "Minecraft - FTB Infinity Beyond has initiated in screen instance 'minecraft'"
}

```

My only real contribution to the code is the screen part of it is: "sudo screen -SL minecraft" and the echo section below the rest of the code. I have only added the logging tag due to the plethora of issues I've been coming up against. In theory, I'd want to remove that eventually...

So now fortunately, the server boots up... This is good. However, upon either detaching from the screen instance through pressing the keys "[ctrl] A + D" or through closing out the SSH instance, the Minecraft server is put into a "limbo state" and the screen instance disappears. Upon typing in "screen -ls" I get the wonderful prompt of "no socket found" and upon typing in "screen -r" I get the prompt of "no screen instance to reattach to."

Upon listing my processes, however, I find that there are both a screen instance with the very same command above, as well as a server instance.

So what is going on here? Why is my screen suddenly disappearing, but leaving ghost processes on my server?

---

### Post by LHammonds on 2017-06-14
My Minecraft server is configured to be fully self-automated.  It starts up by itself, it reboots daily by itself and notifies in-game users about the pending reboot, etc.

I too use screen and run each instance with its own low-rights user account.

I'll create a user account that matches the instance such as "hamcraft" and then run the following command in the root crontab:

```
su hamcraft --command "screen -d -m -S hamcraft -t hamcraft java -d64 -XX:MaxPermSize=256M -Xincgc -Xmx$2048 -jar /opt/hamcraft/server.jar --log-strip-color"
```

I never open screen directly at the console.  Instead, I run various bash scripts to push the commands I want to send to the console....for example, I have a "start.sh" script that will start a specified instance, "stop.sh" will stop a specified instance with in-game notices, "sendcmd.sh" will send whatever console command I want to issue on a specified instance and "rsync.sh" which will make a backup of a Minecraft instance and notify in-game users that a backup started, then issue the save-on/save-off and again notify users of backup completion and status.

Here is an example of commands I issue to stop an instance:

Save the world to disk:
```
su hamcraft --command "screen -S hamcraft -p hamcraft -X stuff \"save-all\""
```
Send a carriage return:
```
su hamcraft --command "screen -S hamcraft -p hamcraft -X eval \"stuff \015\""
```
Stop the server:
```
su hamcraft --command "screen -S hamcraft -p hamcraft -X stuff \"stop\""
```
Send a carriage return:
```
su hamcraft --command "screen -S hamcraft -p hamcraft -X eval \"stuff \015\""
```

My scripts are far more complicated than the above but those are the crux of the commands to manipulate the server.

LHammonds

---

### Post by Tadaen_Sylvermane on 2017-06-16
I'm curious why you both run this from root. Seems to defeat the security model of linux for no real gain. I'd suggest modifying to run under an unprivileged user. This is the script I use for my 4 lxd container minecraft servers. They all run unprivileged, the server starts with @reboot in the crontab. The test runs every 5 minutes and emails me if the server stops running. Works great, and I don't have to mess with su or root at all.

*EDIT* The Invocation should be $SERVICE with {}. It's formatting it with ***** for some reason.


```
#!/bin/bash
#tadaen sylvermane | jason gibson
#user control script


##### variables #####


NOW=$(/bin/date +%Y.%m.%d.%H.%M) # time when script is run
SERVICE=$(/bin/ls "/home/minecraftexe" | grep minecraft_server)
GAMEDAYS=3 # days to keep gameserver backups 
INVOCATION="/usr/bin/java -jar /home/minecraftexe/${*********nogui"
SERVER=failbox.mylan.home
SERVERPATH=/data/backups/minecraft
TESTLOCK=/home/"$USER"/testlock


##### begin script #####


mc_saveoff() { # changes server to read only to save world properly
    if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
        /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "say saving map. going read-only"\015'
        /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "save-off"\015'
        /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "save-all"\015'
        sync
        sleep 10
    fi
}


mc_saveon() { # changes server to read / write
    if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
        /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "say backed up! going read-write"\015'
        /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "save-on"\015'
    fi
}


case "$1" in
    start)    
        if [[ -e "$TESTLOCK" ]] ; then
            /bin/rm "$TESTLOCK"
        fi
        if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
            /bin/echo "$SERVICE is already running..."
        else
            /bin/echo "starting $SERVICE"
            cd /home/"$USER" && /usr/bin/screen -dmS "$USER" $INVOCATION
            sleep 7
            if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
                /bin/echo "$SERVICE is running"
            else
                /bin/echo "error! couldn't start $SERVICE"
            fi
        fi
        ;;
    stop)
        if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
            /bin/echo "stopping $SERVICE"
            /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "say server shutdown in 10 seconds..."\015'
            mc_saveoff
            /usr/bin/screen -p 0 -S "$USER" -X eval 'stuff "stop"\015'
            sleep 7
        else
            /bin/echo "$SERVICE wasn't running..."
        fi
        if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
            /bin/echo "error! couldn't stop $SERVICE"
        else
            /bin/echo "$SERVICE stopped..."
        fi
        ;;
    backup)
        if /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
            mc_saveoff
            /bin/tar -czf /home/"$USER"/"$3"."$NOW".tar.gz /home/"$USER"/"$3"
            mc_saveon
            /usr/bin/rsync -auv /home/"$USER"/"$3"."$NOW".tar.gz "$2"@"$SERVER":"$SERVERPATH"
            /bin/rm -rf /home/"$USER"/"$3"."$NOW".tar.gz
            /usr/bin/ssh "$2"@"$SERVER" "/usr/bin/find ${SERVERPATH}/ -type f -mtime +${GAMEDAYS} -exec rm -rf {} \;"
        fi
        ;;
    test)
        if ! /usr/bin/pgrep -u "$USER" -f "$SERVICE" > /dev/null ; then
            if [[ ! -e "$TESTLOCK" ]] ; then
                echo "${HOSTNAME} minecraft server has stopped! at ${NOW}" | ssmtp "$2"
                touch "$TESTLOCK"
                exit 0
            fi
        fi
        ;;
    *)
        /bin/echo "usage ${0} {start | stop | backup}"
        exit 0
        ;;
esac




##### end script #####

```

---

### Post by nightraver on 2017-07-01
Well I took kind of a middlegrounds between the two options chosen above and decided to go with a process of utilizing a startup script on its own. I am still coming up to the issue of not being able to reattach my detached script after restarting the server, or after reconnecting through ssh. Yet again, in the ps -ef listings, it shows the MC instance, an instance of screen and a java string. I really, really don't understand how these processes can be running, yet not visible or accessible?

```

#Variables
SUDO="sudo -u minecraft"
SCREEN="minecraft"
DIR="[retracted]/ServerStart.sh"


case "$1" in  start)
    screen -dmS $SCREEN -t $SCREEN $DIR
    echo "Server started on screen $SCREEN"
    ;;
  stop)
    screen -X -S $SCREEN kill
    echo "Server shutting down"
    ;;
  *)
    echo "Usage: /etc/init.d/beyond-start {start|stop}"
    exit 1



```

---

### Post by CatKiller on 2017-07-03
Why are you running screen or minecraft as root? That is a Bad Plan, and is probably why you can't re-attach to screen.

If you look closely, LHammonds runs it as a specific unprivileged user, which is fine if complicated.

Just run it as your normal user.

---

### Post by nightraver on 2017-07-24
I did try and run it without sudo privileges, but came across access permission errors within the loader script. This was with the entire Minecraft server directory set to chmod 777 for the desired daemon character. Is there something more I would have to do to have this work properly?

---

### Post by CatKiller on 2017-07-24
What's the loader script? What are the error messages?

Running things as root is using an Intercontinental Ballistic Missile to crack a nut. chmod 777 is not generally ideal, either.

---

### Post by nightraver on 2017-08-04
Ok, so I transferred my server back into my daemon's home directory, gave all the files within 755 permissions with recursive changes (down from 777 before), and changed ownership of all containing files to my mc daemon. I tried initializing the script with my daemon account  without the detach options, only to receive this error from screen:

/var/run/screen/S-minecraft/1795.pts-1.beyond: No such file or directory

Any help to get around this?

---

