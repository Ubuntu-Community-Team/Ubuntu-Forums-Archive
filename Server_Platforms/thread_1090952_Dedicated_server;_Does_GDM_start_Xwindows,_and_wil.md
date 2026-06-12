---
title: "Dedicated server; Does GDM start Xwindows, and will uninstalling GDM solve it?"
date: 2009-03-08
forum: Server Platforms
---

### Post by Arkaniad on 2009-03-08
I have a dedicated server that i want to tunnel Xwindows to my laptop (os x) I think restarting SSHD might solve but not sure because i edited the config. Anyways, does GDM start Xwindows and if i remove GDM will it not start X on system start up? because i get Cannot start display when i try to start a tunneled X app. 

Ubuntu server 8.10 with Gdm and ubuntu-desktop installed.

---

### Post by hictio on 2009-03-08
> **Arkaniad said:**
> I have a dedicated server that i want to tunnel Xwindows to my laptop (os x) I think restarting SSHD might solve but not sure because i edited the config. Anyways, does GDM start Xwindows and if i remove GDM will it not start X on system start up? because i get Cannot start display when i try to start a tunneled X app. 

Ubuntu server 8.10 with Gdm and ubuntu-desktop installed.

You get the "Cannot start display" because it seems, you are not exporting the DISPLAY from the Ubuntu box to the Os X one.

Do you have the X11 app installed on the Os X box?
You have to start it (/Applications/Utilities/X11.app), it will open a Terminal.app like called xterm. If you don't have it installed, you''ll need to install it from the Os X install DVD/ CDs.

From that xterm you have to connect via SSH (using the -X flag so SSH handles the X Window session settings automagically) to the Ubuntu box.
Like this, on the Os xterm, type:

```

ssh -X ubuntu.server ENTER

```

Once connected, type, for instance, 'xclock' (or 'xtop', etc) which is a lightweight app that will be perfect to test if the DISPLAY has been correctly set, and all the X Window tunneling its working A Ok.

If I might ask, what is the app that you have on the Ubuntu Server that needs to be executed with a graphical GUI?


The other question, if you don't want to start the graphical environment on your Ubuntu Server, you can simply stop the service from running.
If its already running, type this on the Ubuntu Server:

```

sudo update-rc.d -f gdm remove ENTER

```

If, by chance, you want to enable it again, type:

```

sudo update-rc.d -f gdm defaults ENTER

```

---

### Post by Arkaniad on 2009-03-09
Thanks, but now it seems like the least of my worries. I dont suppose you have any Source dedicated server expirience?
Anyways... i need a script to run
```

./srcds_run -game garrysmod -secure +maxplayers 14 +map sb_forlorn_sb3_r2l +sv_gamemode Spacebuild3 +sv_gamemode Spacebuild3
```So i got this script...
```

#!/bin/sh
# Source Dedicated Server Init Script

# Server options
TITLE='Source Dedicated Server' # Script initialization title
LONGNAME='Garry's Mod'        # Full title of game type
NAME='garrysmod'                          # Server handle for the screen session
DAEMON='srcds_run'                # The server daemon
STEAM='/home/srcds/orangebox'        # STEAM to Steam installation
USER='tf2'

# Game options
IP='72.24.136.150'                # IP of the server
PORT='27015'                    # Port number to
MAP='sb_forlorn_sb3_r2l'                    # Initial map to start
GAME='Spacebuild3'                        # Game type (tf|cstrike|valve|hl2mp)
SIZE='14'                        # Maximum number of players

# Server options string
OPTS="-game $GAME +hostname \"$CLIENT\" +map $MAP +ip $IP -port $PORT \
    -autoupdate +maxplayers $SIZE -pidfile $STEAM/$GAME/$NAME.pid"

# Screen command
INTERFACE="/usr/bin/screen -A -m -d -S $NAME"

service_start() {
    # Check if the pid files currently exist
    if [ ! -f $STEAM/$GAME/$NAME.pid ] && [ ! -f $STEAM/$GAME/$NAME-screen.pid ]; then
        if [ -x $STEAM/$DAEMON ]; then
            echo "Starting $TITLE - $LONGNAME"
            echo "Server IP: $IP"
            echo "Server port: $PORT"
            echo "Server size: $SIZE players"
            cd $STEAM
            $INTERFACE $STEAM/$DAEMON $OPTS
            # Prevent race condition on SMP kernels
             sleep 1
            # Find and write current process id of the screen process
            ps -ef | grep SCREEN | grep "$NAME" | grep -v grep | awk '{ print $2}' > $STEAM/$GAME/$NAME-screen.pid
            echo "$TITLE screen process ID written to $STEAM/$GAME/$NAME-screen.pid"
            echo "$TITLE server process ID written to $STEAM/$GAME/$NAME.pid"
            
            echo "$TITLE started."
        fi
    else
        echo -e "Cannot start $TITLE.  Server is already running."
        #exit 1
    fi
}

service_stop() {
    if [ -f $STEAM/$GAME/$NAME.pid ] && [ -f $STEAM/$GAME/$NAME-screen.pid ]; then
        echo "Stopping $TITLE - $LONGNAME."
        # Get the process ID from the pid file we created earlier
        for id in `cat $STEAM/$GAME/$NAME-screen.pid`
            do kill -9 $id
            echo "Killing process ID $id"
            echo "Removing $TITLE screen pid file"
            rm -rf $STEAM/$GAME/$NAME-screen.pid
            break
        done
        # Remove server pid file
        echo "Removing $TITLE pid file"
        rm -rf $STEAM/$GAME/$NAME.pid
        # Wipe all old screen sessions
        screen -wipe 1> /dev/null 2> /dev/null
        echo "$TITLE stopped."
    else
        echo -e "Cannot stop $TITLE.  Server is not running."
        #exit 1
    fi    
}    


case "$1" in
    'start')
        service_start
        ;;
    'stop')
        service_stop
        ;;
    'restart')
        service_stop
        sleep 1
        service_start
        ;;
    *)
        echo "Usage $0 start|stop|restart"
esac

```It should work fine, but it doesnt.... Script gives me an error. Either i learn bash scripting or someone fixes that script :D

---

