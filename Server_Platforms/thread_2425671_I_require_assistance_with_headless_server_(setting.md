---
title: "I require assistance with headless server (setting up fake/virtual monitor)"
date: 2019-08-28
forum: Server Platforms
---

### Post by 22knarf on 2019-08-28
I want to set up an old pc as a minecraft server. Since it's old and not that quick, i want to use ubuntu.
Unfortunately I got no clue how to set up a fake monitor and the ways that I found online (and understood somewhat) don't work for whatever reason:
[https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg](https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg) - Can't edit or safe the file.
[https://askubuntu.com/questions/453109/add-fake-display-when-no-monitor-is-plugged-in](https://askubuntu.com/questions/453109/add-fake-display-when-no-monitor-is-plugged-in) - missing dependent programs or something, even when installed.

Please help, linux is frustrating if you don't understand it XD

---

### Post by slickymaster on 2019-08-28
Thread moved to **Server Platforms** for a better fit

---

### Post by Tadaen_Sylvermane on 2019-08-28
You are taking a Windows approach to it. Any reason you can't just do this over ssh with the command line? GUI is always slower and usually a bad idea for server stuff as it doesn't have near the power and speed of use. A minecraft server can be set up on a headless server in about 5-10 minutes over ssh.

---

### Post by 22knarf on 2019-08-29
well, mostly because i have no experience at all with ssh, and i like a gui. Plus, apart from the virtual monitor, it works just fine.
I can try with ubuntu server tho, see how that goes.

---

### Post by TheFu on 2019-08-29
+1 for using ssh.

---

### Post by LHammonds on 2019-08-31
You can definitely run a Minecraft server on a headless server like  Ubuntu Server and only use SSH to manage it.  I used to run a hub with a  dozen connected servers using Craftbukkit + Bungee....all without any  having to touch the server.  Reboots and OS updates were automated.   Updates to Minecraft and the plugins I did manually since Minecraft  updates can break plugins and plugin updates can break themselves if you  are not careful checking what changes need to be made to config files  and permission nodes.

I never really documented how I setup my  servers from start to finish though.  If I ever get back into hosting  Minecraft/bukkit servers, I should really do that.

The trick is  to run the server in a "screen" session.  I figured out how to interact  with the screen session without actually having to go into it...thus  sending commands to the console was done via script such as sending  broadcast notices, save/shutdown commands, etc.

I can find my old  scripts I used to manage the server but it isn't for the faint of heart  and without a step-by-step guide, I doubt many could make much use of  my scripts as they are without knowing all the details of how everything  is related to each other...but I can give you some snippets of they  crucial bits that make it all work.

Let's assume you are using a  server file called "server.jar" and have it placed in  /opt/minecraft/server.jar with a user account "minecraftuser" in a group  called "minecraft"

The startup, shutdown and management of the  "server.jar" typically is the same even if you use Minecraft's vanilla  server.jar, Craftbukkits server.jar, Spigot's server.jar, etc.

Here  is how I would start the server in a screen session called "mcsession"  (keep in mind, this is from years ago so it might be slightly different  today):
```

cd /opt/minecraft
su minecraftuser --command  "/usr/bin/screen -d -m -S mcsession -t mcsession /usr/bin/java -d64  -XX:MaxPermSize=128M -Xincgc -Xmx4096M -jar /opt/minecraft/server.jar  --log-strip-color"

```

To send a broadcast message to this  server so all online players could see it, I would send the message  like this and follow it up with a carriage return:
```

su minecraftuser --command "screen -S mcsession -p mcsession -X stuff \"say Hello World\""
su minecraftuser --command "screen -S mcsession -p mcsession -X eval \"stuff \015\""

```

To shutdown the server, I would save the world and initiate the shutdown like this:
```

su minecraftuser --command "screen -S mcsession -p mcsession -X stuff \"save-all\""
su minecraftuser --command "screen -S mcsession -p mcsession -X eval \"stuff \015\""
su minecraftuser --command "screen -S mcsession -p mcsession -X stuff \"stop\""
su minecraftuser --command "screen -S mcsession -p mcsession -X eval \"stuff \015\""

```

I  could run multiple screen sessions, each with a unique user account,  session name, folder path and game port.  So one port could be the  vanilla Minecraft server, another port could be a Spigot server with a  bunch of plugins.

**EDIT:** When I first started running Minecraft servers, the initially started on my Windows PC.  I eventually started running them on a headless Ubuntu server but my initial configuration and testing was always done first on my Windows PC...then I copied the end-result to the server to run.  Once I got more familiar with Linux, I ended up building, updating and maintaining the server there.

LHammonds

---

### Post by Tadaen_Sylvermane on 2019-08-31
This is the script I use to run my servers. It is converted from an old sysv script I found online long time ago. Runs in a for loop for as many servers specified. This runs as an unprivileged user via @reboot in the crontab of that user. Some variables are sourced from another file. The only thing these don't do is install screen and the openjdk-8-headless, create the user and make the proper directories. This works for ramdisk as well, which I highly recommend if you have the ram to spare.

They are sloppy as all hell, but they work wonderfully.

```
#!/bin/bash# tadaen sylvermane | jason gibson
# server minecraft controller


# source #


. /usr/local/bin/mainsource


# variables #


BACKUPLOC="$POOLLOC"/backups/minecraft
MINECRAFTEXE=/snapraid/data/data1/minecraftexe
CURRENTSERVERJAR=$(basename $(find "$MINECRAFTEXE"/ -type f))
WORLDDIR=/home/"$MCSERVERUSR"/gameworlds
RSYNCOPT=-auv


# functions #


mc_backups() {
    screen -p 0 -S "$1" -X eval 'stuff "save off"\015'
    screen -p 0 -S "$1" -X eval 'stuff "save-all"\015'
    sync
    sleep 10
    if [[ -e "$RAMDISKLOCK" ]] ; then
        rsync "$RSYNCOPT" --progress "$RAMDISKDIR"/"$1"/* "$WORLDDIR"/"$1"/
    fi
    case $(date +%I%M) in
        0600|1200)
            if [[ -e "$RAMDISKLOCK" ]] ; then
                tar -czf "$BACKUPLOC"/"$1"."$NOW".tar.gz "$RAMDISKDIR"/"$1"/*
            else
                tar -czf "$BACKUPLOC"/"$1"."$NOW".tar.gz "$WORLDDIR"/"$1"/*
            fi
            ;;
    esac
    find "$BACKUPLOC"/ -type f -mtime +1 -exec rm -rf {} \;
    screen -p 0 -S "$1" -X eval 'stuff "save-on"\015'
    find "$RAMDISKDIR"/"$1"/logs/ -type f -mtime +30 -exec rm {} \;
    find "$WORLDDIR"/"$1"/logs/ -type f -mtime +30 -exec rm {} \;
}


# begin script #


if [[ "$USER" == root ]] ; then
    bin_link_controller
    case "$SCRIPTCALL" in
        mcramdiskcreate) #MAINCOMMAND#
            minecraft_ramdisk_creation
            ;;
    esac
elif [[ "$USER" == "$MCSERVERUSR" ]] ; then
    for server in "$@" ; do
        RAMDISKLOCK="$WORLDDIR"/"$server"/ramdisk
        INVOCATION="screen -dmS ${server} java -jar \
        ${MINECRAFTEXE}/${CURRENTSERVERJAR} nogui"
        if screen -ls | grep -q "$server" ; then
            case "$SCRIPTCALL" in
                mcstop|mcrestart) #MAINCOMMAND#
                    for log in hs_err*log *.log.gz ; do
                        if [[ -e "$RAMDISKLOCK" ]] ; then
                            find "$RAMDISKDIR"/"$server"/ -name "$log" -mtime +10 -exec \
                            rm {} \;
                        else
                            find "$WORLDDIR"/"$server"/ -mtime +10 -exec rm {} \;
                        fi
                    done
                    mc_backups "$server"
                    for seconds in 30 20 10 ; do
                        screen -p 0 -S "$server" -X eval \
                        "stuff \"say server ${SCRIPTCALL} in ${seconds} seconds.\"\015"
                        sleep 10
                    done
                    screen -p 0 -S "$server" -X eval 'stuff "stop"\015'
                    if [[ "$SCRIPTCALL" == mcrestart ]] ; then
                        sleep 5 && mcstart "$server"
                    fi
                    ;;
                mcbackup) #MAINCOMMAND#
                    mc_backups "$server"
                    ;;
                *)
                    echo "${server} is running!"
                    ;;
            esac
        else
            case "$SCRIPTCALL" in
                mcstart) #MAINCOMMAND#
                    if [[ -e "$RAMDISKLOCK" ]] ; then
                        if mountpoint -q "$RAMDISKDIR" ; then
                            mkdir -p "$RAMDISKDIR"/"$server"/
                            rsync -auv --progress "$WORLDDIR"/"$server"/* \
                            "$RAMDISKDIR"/"$server"/
                            cd "$RAMDISKDIR"/"$server"/ && $INVOCATION
                        else
                            echo "ramdisk for ${server} not mounted!"
                        fi
                    else
                        cd "$WORLDDIR"/"$server"/ && $INVOCATION
                    fi
                    sleep 10
                    "$SCRIPTCALL" "$server"
                    ;;
                *)
                    echo "${server} is not running!"
                    ;;
            esac
        fi
    done
fi


# end script #
```

Sourced parts

```
POOLLOC=/snapraid/pool
MCSERVERUSR=mcserver
RAMDISKDIR=/ramdisk
RAMDISKGROUP=$(basename "$RAMDISKDIR")
RAMDISKGID=2000

bin_link_controller() {
    SCRIPTEXELINKS=/usr/local/bin
    bin_link_create() {
        if [[ ! -L "$SCRIPTEXELINKS"/"$1" ]] ; then
            if [[ ! -d "$SCRIPTEXELINKS" ]] ; then
                mkdir -p "$SCRIPTEXELINKS"
            fi
            if dir | grep $(basename "$0") > /dev/null ; then
                ln -s $(pwd)/$(basename "$0") "$SCRIPTEXELINKS"/"$1"
            else
                ln -s "$0" "$SCRIPTEXELINKS"/"$1"
            fi
        fi
    }
    if grep -q '#MAINCOMMAND#' "$0" ; then
        for line in $(grep ") #MAINCOMMAND#" "$0" | grep -v command | \
        sed 's/#MAINCOMMAND#//g') ; do
            if echo "$line" | grep "|" > /dev/null ; then
                for command in $(echo "$line" | awk -F\| \
                '{OFS="\n"; print $1, $2, $3, $4, $5, $6, $7, $8}' | \
                cut -d\) -f 1) ; do
                    bin_link_create "$command"
                done
            else
                for command in $(echo "$line" | cut -d\) -f 1) ; do
                    bin_link_create "$command"
                done
            fi
        done
    elif [[ "$@" ]] ; then
        for link in "$@" ; do
            bin_link_create "$link"
        done
    else
        bin_link_create $(basename "$0")
    fi
}

minecraft_ramdisk_creation() {
    if ! grep "$RAMDISKGROUP" /etc/fstab ; then
        echo "none ${RAMDISKDIR} tmpfs defaults,size=2048M,gid=${RAMDISKGID} 0 0" \
        >> /etc/fstab
        mkdir -p "$RAMDISKDIR"
    fi
    if ! grep "$RAMDISKGROUP" /etc/group ; then
        groupadd --gid "$RAMDISKGID" "$RAMDISKGROUP"
        if [[ "$HOSTNAME" == "$SERVERHOSTNAME" ]] ; then
            package_installer openjdk-8-jre-headless screen
            adduser --uid 1200 "$MCSERVERUSR"
            usermod -aG "$RAMDISKGROUP" "$MCSERVERUSR"
        else
            for user in /home/* ; do
                usermod -aG "$RAMDISKGROUP" $(basename "$user")
            done
        fi
    fi
    if ! mountpoint -q "$RAMDISKDIR" ; then
        mount "$RAMDISKDIR"
    fi
}
```

---

### Post by LHammonds on 2019-08-31
> **Tadaen_Sylvermane said:**
> This is the script I use to run my servers.
That script utilizes a ramdisk.  Minecraft used to benefit from a ramdisk in the early days but I don't think there is any performance benefit since version 1.2.5

LHammonds

---

### Post by Tadaen_Sylvermane on 2019-09-01
Damn. Well, good to know I guess. I won't take it out of the script though. Took a bunch of trial and error to get it right. Scripting is not my strong point. Thankfully the script works for both depending on a lock file existing.

Maybe I'll put my servers back on the ssd instead of the ramdisk. Not hurting for ram though, dunno what to do. Maybe I should shut them down altogether now anyway. I never play on them, and the wife doesn't use the computer much these days since an accident at work left her with bad headaches when on a screen for to long.

---

