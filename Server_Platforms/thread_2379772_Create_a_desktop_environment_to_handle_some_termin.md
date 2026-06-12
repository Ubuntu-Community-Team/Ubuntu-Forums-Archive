---
title: "Create a desktop environment to handle some terminal istances"
date: 2017-12-09
forum: Server Platforms
---

### Post by dam034 on 2017-12-09
Dear users,

I have a VPS with ubuntu server 16.04

I want to handle some terminal istances like ubuntu desktop to leave opened commands.

Now I have tasksel, where I can install a desktop environment.

I need a simple desktop environment to handle the terminal istances, and it will be available also in remote mode, via SSH or webmin.

What you advice?


Thanks

---

### Post by powersj on 2017-12-09
> **dam034 said:**
> 
I want to handle some terminal istances like ubuntu desktop to leave opened commands.


If you are looking for a way to keep a terminal instance open even after disconnecting from the server, then I highly recommend looking at byobu rather than installing an entire UI. This is my favorite intro to byobu:

[https://www.youtube.com/watch?v=NawuGmcvKus](https://www.youtube.com/watch?v=NawuGmcvKus)

---

### Post by dam034 on 2017-12-15
Since I don't understand good the english, I only briefly understood the video content.

I think this byobu is fine for what I need.

Starting from a ubuntu 16.04 server, how can I install and use this program?


Thanks

---

### Post by volkswagner on 2017-12-15
I highly recommend using [screen]("https://www.howtoforge.com/linux_screen") to create multiple
terminal sessions that can be detached and attached
for connecting after ssh session has been lost.

---

### Post by dam034 on 2017-12-15
I state that I'm willing to install the UI on ubuntu server, but not as ubuntu desktop, then without chromium, thinderbird, libreoffice, ecc... even if I don't know how to do it.

I want to know:
[LIST]
[*]with screen can I manage more terminal istances?
[*]can I resume a lost istance to execute other subcommands?
[*]can I connect from different clients and see the same istances?
[/LIST]


Thanks

---

### Post by volkswagner on 2017-12-15
Yes, yes and yes &#128513;

Each screen instance gets a name, you can even set the name. You'll be able to connect back to it from any machine at any time. It's actually called "attach" and "detach". No need for a GUI.

[https://youtu.be/PQMYfn9rlAo](https://youtu.be/PQMYfn9rlAo)

---

### Post by dam034 on 2017-12-16
I saw the video you linked, and I found screen very useful.

But there is a problem: I don't understand good the english, especially the spoken.

I can't understand in the video between 3:35 and 3:55 how he switches the terminal istances.

Another question: can I run screen on the server locally without connecting from a remote client?


Thanks

---

### Post by LHammonds on 2017-12-18
Yes, you can run "screen" locally or remotely.  You can list all screen instances and bring them to the main screen and send to the background as needed.

Another option to consider is this...if you just need to run a command (fire and forget) and let it continue to run even if you disconnect from the session, you can use "nohup" and send the command into the background with ampersand (&).

For example, if I wanted to start a script called "runme.sh" that will take hours to complete, I can issue the following command:

```
nohup /var/scripts/runme.sh &
```

LHammonds

---

### Post by Tadaen_Sylvermane on 2017-12-19
I use tmux when I need to keep a terminal running. Screen for my minecraft servers though.

---

### Post by dam034 on 2017-12-19
> **LHammonds said:**
> Another option to consider is this...if you just need to run a command (fire and forget) and let it continue to run even if you disconnect from the session, you can use "nohup" and send the command into the background with ampersand (&).
I already use nohup for long running commands.

> **Tadaen_Sylvermane said:**
> I use tmux when I need to keep a terminal running. Screen for my minecraft servers though.
It isn't only minecraft, I have to manage minecraft, mtasa, nodejs and mediatomb (at least now these come to mind).

I read this: [https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen) but I didn't understand:
[LIST]
[*]if I can detach the virtual terminal sessions from a remote client and re-attach from another client, leaving them running
[*]the key combination CTRL+A, how to create a new session is CTRL+C or CTRL+A+C
[/LIST]

Help!

---

### Post by LHammonds on 2017-12-20
> **dam034 said:**
> 
It isn't only minecraft, I have to manage minecraft, mtasa, nodejs and mediatomb (at least now these come to mind).

Ah ha!  Minecraft!

I run Minecraft servers and use Screen to manage them all.

I have a lot of custom scripts to manage them but I'll dig through them and see about just showing you the crux of the commands to make it all happen.

I'll edit this post and paste the code here.

EDIT:

For each Minecraft instance, I create a low-rights user account that matches my instance and folder name.  Example: hamcraft

Start Code:
```

RAM2Use=4096
ServerKey="hamcraft"
cd /opt/spigot/${ServerKey}
su ${ServerKey} --command "screen -d -m -S ${ServerKey} -t ${ServerKey} java -d64 -XX:MaxPermSize=256M -Xincgc -Xmx${RAM2Use} -jar /opt/spigot/${ServerKey}/server.jar --log-strip-color"

```

Function for sending in-game message:
```

function f_sendmsg()
{
  ## Purpose: Send messages to Minecraft players via the console.
  ## Parameter #1 is the server key/loginID/session.
  ## Parameter #2 is the message to send to the console.

  ## Make sure the required parameters are not empty.
  if [[ -z "${2}" ]]; then
    if [[ -z "${1}" ]]; then
      ## No server key specified.
      echo "`date +%Y-%m-%d_%H:%M:%S` [SEVERE] Both parameters to f_sendmsg() are missing." | tee -a ${LOGFILE}
    else
      echo "`date +%Y-%m-%d_%H:%M:%S` [SEVERE] 2nd parameter to f_sendmsg() is missing." | tee -a ${LOGFILE}
    fi
    return
  fi
  acct="${1}"
  msg="${2}"
  CurrentUser=`whoami`
  if [ "${CurrentUser}" != "${acct}" ]; then
    ## Need to switch to the owner account to run the screen command.
    su ${acct} --command "screen -S ${acct} -p ${acct} -X stuff \"${msg}\""
    ## Send carriage return.
    su ${acct} --command "screen -S ${acct} -p ${acct} -X eval \"stuff \015\""
  else
    ## This script is being run by the current account.
    screen -S ${acct} -p ${acct} -X stuff "${msg}"
    ## Send carriage return.
    screen -S ${acct} -p ${acct} -X eval "stuff \015"
  fi
}

```

Stop server instance:
```

ServerKey="hamcraft"
f_sendmsg ${ServerKey} "say &c[WARNING]&a Server shutting down for &bUPGRADE"
f_sendmsg ${ServerKey} "say &c[WARNING]&a Server shutdown in 3..."
sleep 1
f_sendmsg ${ServerKey} "say &c[WARNING]&a Server shutdown in 2..."
sleep 1
f_sendmsg ${ServerKey} "say &c[WARNING]&a Server shutdown in 1..."
sleep 1
f_sendmsg ${ServerKey} "save-all"
f_sendmsg ${ServerKey} "stop"

```

LHammonds

---

### Post by deadflowr on 2017-12-20
> the key combination CTRL+A, how to create a new session is CTRL+C or CTRL+A+C

Treat CTRL+A as one key,
so it would be press and hold CTRL+A then press C while CTRL+A is still held down.
same would apply to the other keybindings.

---

### Post by dam034 on 2017-12-22
Thanks for the replies.

I want to clarify about minecraft I still have to install the server, and it'll be after Christmas holidays.

About screen, I tried to move in the program and I find it very good. I discovered if I have open screen from a client, I can't open screen from another client until I close it on the first client (and maybe it's better).

Now I have a question about screen: how can I plan some virtual terminals start on boot?


Thanks

---

### Post by LHammonds on 2017-12-23
> **dam034 said:**
> Now I have a question about screen: how can I plan some virtual terminals start on boot?
I gave you the start code.  Just put it in a script and call that script from root's crontab.

Even though you initiate in the root account, Minecraft is started with the low-rights user account I mentioned.  Just make sure the files/folders for that instance are owned or able to be manipulated by the low-rights account.

I "never" issue screen commands manually nor do I interact manually with screen...so I don't even need to remember those pesky control keys to send to background and such.  I just start the server and when needed, I "push" commands to the screens console such as "say" or "stop"

LHammonds

---

### Post by dam034 on 2017-12-24
Unfortunately I don't understand your code, because I'm a beginner for "screen".

Can you give me an example to open at startup 2 virtual session with this commands?

The first:
```
root@vps1:~# mediatomb
```
The second:
```
root@vps1:~# cd /srv/mtasa
root@vps1:/srv/mtasa/# ./mta-server64
```
Hoping to understand something from your examples :KS


Thanks

---

### Post by LHammonds on 2017-12-25
> **dam034 said:**
> Unfortunately I don't understand your code, because I'm a beginner for "screen".
This can be fixed by typing the following at the command line:
```
man screen
```
or by visiting the following URL:
[Screen manual](http://manpages.ubuntu.com/manpages/xenial/man1/screen.1.html)

> **dam034 said:**
> Can you give me an example to open at startup 2 virtual session with this commands?

The first:
```
root@vps1:~# mediatomb
```
The second:
```
root@vps1:~# cd /srv/mtasa
root@vps1:/srv/mtasa/# ./mta-server64
```

I'm not at all familiar with "mediatomb" or "mta-server64" so I'll just go based on what you typed.  If you don't know the full path to "mediatomb" you can obtain it by typing the following:
```
which mediatomb
```

Assumption #1 - The associated low-rights user configured to run the app is called "mtauser"
Assumption #2 - The session name will be called "mta-server64" as noted by the "-S" option
Assumption #3 - The shell title will be called "mta-server64" as noted by the "-t" option
Assumption #4 - The full path to the executable program is /srv/mtasa/mta-server64

```

cd /srv/mtasa
su mtauser --command "screen -d -m -S mta-server64 -t mta-server64 /srv/mtasa/mta-server64"

```

-----------------------------

Assumption #1 - The associated low-rights user configured to run the app is called "mediauser"
Assumption #2 - The session name will be called "mediatomb" as noted by the "-S" option
Assumption #3 - The shell title will be called "mediatomb" as noted by the "-t" option
Assumption #4 - The full path to the executable program is /bin/mediatomb

```

su mediauser --command "screen -d -m -S mediatomb -t mediatomb /bin/mediatomb"

```

LHammonds

---

### Post by dam034 on 2017-12-28
I read and executed your examples and they work.

Then I had fun executing screen command with my own titles, session names and executables to open. Till now, I executed all command as root user for experiments. After I'll create some low-rights users to execute them.

Now I have some questions:
[LIST]
[*]how can I launch a command like "/srv/mtasa/mta-server -s "Hello world" -t 3600"?
[*]how can execute CTRL+C on all virtual sessions on shutdown command?
[*]how can I execute a command in a virtual session (e.g. "refresh" in mtasa session) without re-attach it?
[*]how to create more virtual sessions in only one socket, so I can switch with CTRL+A "?
[/LIST]

Thanks

---

### Post by Tadaen_Sylvermane on 2017-12-28
I don't use root to run my minecraft servers at all. All run under the non-privileged user. Ramdisk for the win!

/etc/fstab

```
[FONT=monospace][COLOR=#000000]# minecraft server ramdisk[/COLOR]
none /ramdisk tmpfs uid=1008,gid=1008,size=2048M 0 0
```
[/FONT]
```

NOW=$(date +%Y.%m.%d.%H.%M)
EMERGENCYEMAIL=myemail@hidden.com
MINECRAFTEXE=/snapraid/data/ssd/minecraftexe
BACKUPLOC=/data/backups/minecraft
NEWSERVER=$(curl -s https://minecraft.net/en-us/download/server | grep minecraft_server | awk -F\" '{print $2}')
NEWSERVERJAR=$(basename "$NEWSERVER")
CURRENTSERVERJAR=$(ls -t "$MINECRAFTEXE" | head -1)


mc_server_specific_variables() {
    TESTLOCK=/home/"$USER"/gameworlds/"$1"/test.lock
    RAMDISKLOCK=/home/"$USER"/gameworlds/"$1"/ramdisk
    INVOCATION="screen -dmS ${server} java -jar ${MINECRAFTEXE}/${CURRENTSERVERJAR} nogui"
}


backupfunction() { # general mc server backup control
    screen -p 0 -S "$1" -X eval 'stuff "save off"\015'
    screen -p 0 -S "$1" -X eval 'stuff "save-all"\015'
    sync
    sleep 10
    if [[ -e "$RAMDISKLOCK" ]] ; then
        rsync -auv --progress /ramdisk/"$1"/* /home/"$USER"/gameworlds/"$1"/
    fi
    case $(date +%I%M) in
        0600|1200)
            if [[ -e "$RAMDISKLOCK" ]] ; then
                tar -czf "$BACKUPLOC"/"$1"."$NOW".tar.gz /ramdisk/"$1"/*
            else
                tar -czf "$BACKUPLOC"/"$1"."$NOW".tar.gz /home/"$USER"/gameworlds/"$1"/*
            fi
            ;;
    esac    
    find "$BACKUPLOC"/ -type f -mtime +2 -exec rm -rf {} \;
    screen -p 0 -S "$1" -X eval 'stuff "save-on"\015'
}


mc_server_test() { # check if mc server running
    if ! screen -ls | grep "$2" ; then
        if [[ ! -e "$TESTLOCK" ]] ; then
            for try in 1 2 3 ; do
                "$1" start "$2"
                sleep 10
                if [[ "$try" == 3 ]] ; then
                    if ! screen -ls | grep "$2" ; then
                        echo "server ${2} crashed and cannot restart @ ${NOW}" | ssmtp "$EMERGENCYEMAIL"
                        touch "$TESTLOCK"
                        exit 0
                    fi
                fi
            done
        fi
    fi
}


mc_server_shutdown_timer() { # shutdown mc servers with ingame warnings
    # stop / restart minecraft servers
    for seconds in ${@:3} ; do
        screen -p 0 -S "$1" -X eval "stuff \"say server ${2} in ${seconds} seconds.\"\015"
        sleep $(expr "$3" - "$4")
    done
    screen -p 0 -S "$1" -X eval 'stuff "stop"\015'
}


mc_server_update() { # update minecraft exe jar
    if [[ ! -e "$MINECRAFTEXE" ]] ; then
        mkdir -p "$MINECRAFTEXE"
    fi
    if [[ ! -e "$MINECRAFTEXE"/"$CURRENTSERVERJAR" ]] ; then
        wget -O "$MINECRAFTEXE"/"$NEWSERVERJAR" "$NEWSERVER"
    fi
    if [[ "$NEWSERVERJAR" != "$CURRENTSERVERJAR" ]] ; then
        wget -O "$MINECRAFTEXE"/"$NEWSERVERJAR" "$NEWSERVER"
        for running in $(screen -ls | grep Detached | cut -d . -f 2 | awk '{print $1}') ; do
            "$1" restart "$running"
        done
    fi
}


for server in ${@:2} ; do        
        mc_server_specific_variables "$server"
        if screen -ls | grep -q "$server" ; then
            case "$1" in
                stop)
                    "$0" backup "$server"
                    mc_server_shutdown_timer "$server" "$1" 30 20 10 &
                    ;;
                restart)
                    "$0" stop "$server"
                    sleep 35
                    "$0" start "$server"
                    ;;
                backup)
                    backupfunction "$server" &
                    ;;
                update)
                    mc_server_update "$0"
                    ;;
                test)
                    mc_server_test "$0" "$server"
                    ;;
                *)
                    echo "${server} is running!"
                    ;;
            esac
        else
            case "$1" in
                start)
                    if [[ -e "$RAMDISKLOCK" ]] ; then
                        if mountpoint /ramdisk ; then
                            mkdir -p /ramdisk/"$server"/
                            rsync -auv --progress /home/"$USER"/gameworlds/"$server"/* /ramdisk/"$server"/
                            cd /ramdisk/"$server"/ && $INVOCATION
                        else
                            echo "ramdisk for ${server} not mounted!"
                        fi
                    else
                        cd /home/"$USER"/gameworlds/"$server"/ && $INVOCATION
                    fi
                    sleep 10
                    "$0" "$1" "$server"
                    ;;
                test)
                    mc_server_test "$0" "$server"
                    ;;
                update)
                    mc_server_update "$0"
                    ;;
                *)
                    echo "${server} is not running!"
                    ;;
            esac
        fi
    done
```

---

### Post by LHammonds on 2017-12-29
> **dam034 said:**
> 
how can I launch a command like "/srv/mtasa/mta-server -s "Hello world" -t 3600"?how can execute CTRL+C on all virtual sessions on shutdown command?

how can I execute a command in a virtual session (e.g. "refresh" in mtasa session) without re-attach it?



I would take complicated start/stop commands and simplify it.  For example:

```
mkdir -p /var/scripts
touch /var/scripts/mta-start.sh
touch /var/scripts/mta-stop.sh
touch /var/scripts/mta-refresh.sh
touch /var/scripts/reboot.sh
chown -R root:root /var/scripts
chmod 0755 /var/scripts/*.sh
```

/var/scripts/mta-start.sh
```
#!/bin/sh
cd /srv/mtasa
/bin/su mtauser --command "/usr/bin/screen -d -m -S mta-server64 -t mta-server64 /srv/mtasa/mta-server -s \"Hello world\" -t 3600"
```

/var/scripts/mta-stop.sh
```
#!/bin/sh
/bin/su mtauser --command "/usr/bin/screen -S mta-server64 -t mta-server64 stuff ^C"
```

/var/scripts/mta-refresh.sh
```
#!/bin/sh
## Send refresh command
/bin/su mtauser --command "/usr/bin/screen -S mta-server64 -t mta-server64 stuff \"refresh\""
## Send carriage return.
/bin/su mtauser --command "/usr/bin/screen -S mta-server64 -t mta-server64 -X eval \"stuff \015\""
```

/var/scripts/reboot.sh
```
#!/bin/sh
/var/scripts/mta-stop.sh
/bin/sleep 10
/bin/sync
/sbin/shutdown -r now
```

Your root crontab can then look like this:

```
## Start the mta server after each reboot
@reboot /var/scripts/mta-start.sh > /dev/null 2>&1
## Refresh mta server every 5 minutes
/5 * * * * /var/scripts/mta-refresh.sh > /dev/null 2>&1
## Reboot daily at 3am
0 3 * * * /var/scripts/reboot.sh > /dev/null 2>&1
```

> **dam034 said:**
> 
how to create more virtual sessions in only one socket, so I can switch with CTRL+A "?


I don't interact with screen sessions manually and I keep them all separate so I have no experience with this scenario.

LHammonds

---

### Post by dam034 on 2017-12-29
Maybe I badly explained myself.

I saw your batch commands and I understood them. But I'm thinking when I execute "reboot" or "halt -p" on the VPS (especially when I do the disk image), if with these two commands I create a damage to the opened screen sessions, closing them not correctly.

I want to know if when I have to power off or reboot the VPS I need to close the virtual sessions (with your code) or I can run reboot/halt without problems.

Furthermore, I need help on this question:
> **dam034 said:**
> how can I execute a command in a virtual session (e.g. "refresh" in mtasa session) without re-attach it?

Thanks

---

### Post by LHammonds on 2017-12-29
The examples I gave you are just that...examples.  They do not include any logging or error checks.

I have no idea about the mta or media services you are running so you'll have to do some digging.

In the "stop" script, I would include a way to ensure that the session I told to stop actually stopped.  You can do this many ways.  Such as checking to see if the screen session no longer exists (because it closes once the called program terminates) or by checking log files (requires more coding and text manipulation) or by checking the process(s) that are running.  If you have multiple mta processes (screens) running, you cannot simply do a "ps aux | grep mta-server" because you would get the other sessions that you have not issued the "stop" command to...unless you design your stop commands to stop all of them at the same time.

Once you have verified that the session(s) have actually closed, you can then exit out of the stop script.  If the reboot script is the one that called the stop script, it should be free to reboot the server "if you verify the exit code"

Let's say you issue the stop command, wait for the average amount of time it takes to stop the service, then find that it is still running.  Then you issue the stop command again.  If you then issue a kill command to the process and it still fails to stop the server, you could exit the stop script with an error code.  The calling "reboot" script can check the return code and either continue to reboot the server upon successful stop of the service(s) or abort the reboot and maybe even fire off a warning email that something went wrong and log the results.

As for the "refresh," I thought I answered it with the "mta-refresh.sh" script but see that it has a typo.  I'll edit it now.

EDIT:

Here is a code snippet for a function call I use to see if my Minecraft servers are still running.  It simply checks to see if a Java process is still running:

```

function f_isjavarunning()
{
  local isjavarunning=0
  Active=`pidof java`
  if [[ -z ${Active} ]]; then
    ## No Minecraft server is running.
    isjavarunning=0
  else
    ## At least 1 Minecraft server is still running.
    isjavarunning=1
  fi
  return ${isjavarunning}
}

```
Here is a code snippet for a function call to see if a screen session is still running:

```

function f_checkserver()
{
  ## Purpose: Check if server is online or offline via screen session.
  ## Parameter #1 = Server Key / UserID / Folder name / Session
  su ${1} --command "screen -ls" | grep "1 Socket" 1>/dev/null 2>&1
  result=$?
  if [ "${result}" == "0" ]; then
    echo -e "Online ${1}"
  else
    echo -e "Offline ${1}"
  fi
}  ## f_checkserver()

```

LHammonds

---

### Post by The Cog on 2017-12-29
When you are in screen, **Ctrl-A C** (Control-A followed by C) creates a new session, **Ctrl-A 0** selects the first session, **Ctrl-A 1** selects the second etc. **Ctrl-A ?** brings up a help screen.
**Ctrl-A D** disconnects from screen but leaves it running (over SSH, disconnecting the SSH connection will also leave screen running) and it can be reconnected with the command "screen -r". 

So to detach from screen and reattach from another computer, :
* SSH to the server from the first client
* start screen (and start something running within screen?)
* Detach from screen with Ctrl-A D
* SSH to the server from the second client
* use "screen -r" to reattach

---

