---
title: "Server watchdog"
date: 2010-01-24
forum: Server Platforms
---

### Post by penetal on 2010-01-24
Hey I was wondering if someone knew how to make a server watchdog that sees if the server answers to an "ping" test.

I have a few Counter Strike Source servers running but they have a problem and tend to freeze up sometimes where the process is still running and the server heats up a bit until its killed and started over.

I think a script that checks if the server reply and if it don't reply after X numbers of attempts it kills the server and starts it over.

FYI:
I'm using ubuntu server edition 9.10

```
!/bin/sh

echo "Starting Cs:Source Server [HLDS-CSS]"
cd /home/fm/HLDS/CSS
sleep 1s
screen -A -m -d -S SRCDS-CSS ./srcds_run -game cstrike -tickrate 100 -port 27016 +map de_dust +maxplayers 20 -autoupdate
cd ..

echo "Starting Cs:Source Server [HLDS-GG]"
cd GG
sleep 1s
screen -A -m -d -S SRCDS-GG ./srcds_run -game cstrike -tickrate 100 -port 27017 +map gg_simpsons_arena +maxplayers 20 -autoupdate
cd ..

echo "Starting Cs:Source Server [HLDS-10X]"
cd 10X
sleep 1s
screen -A -m -d -S SRCDS-10X ./srcds_run -game cstrike -tickrate 100 -port 27015 +map surf_10x_reloaded +maxplayers 20 -autoupdate
cd ..

echo "Starting Cs:Source Server [HLDS-OFFICE]"
cd OFFICE
sleep 1s
screen -A -m -d -S SRCDS-OFFICE ./srcds_run -game cstrike -tickrate 100 -port 27018 +map cs_office +maxplayers 20 -autoupdate
cd ..

echo "*****************************"
echo "*****************************"
echo "Servers started In background"
echo "*****************************"
echo "*****************************"
screen -x
```

```
fm@FM-Server:~/HLDS$ screen -x
There are several suitable screens on:
        28580.SRCDS-10X (01/24/2010 05:38:01 PM)        (Detached)
        22086.SRCDS-CSS (01/21/2010 03:19:21 PM)        (Detached)
        14391.SRCDS-GG  (01/18/2010 03:11:47 AM)        (Detached)
        14288.SRCDS-OFFICE      (01/17/2010 04:19:04 AM)        (Detached)
Type "screen [-d] -r [pid.]tty.host" to resume one of them.

```

---

### Post by penetal on 2010-01-25
bump!

---

### Post by thor erik on 2010-01-27
The solution I came up for this issue(with this particular server) was:
4 sets of init.d scripts:
template:
```
#!/bin/bash
#replace <newuser> with the user you created above
SRCDS_USER="<newuser>"
#Do not change this path
PATH=/bin:/usr/bin:/sbin:/usr/sbin
#The path to the game you want to host. example = /home/newuser/dod
DIR=/home/<newuser>/HLDS/GG
DAEMON=$DIR/srcds_run
#Change all PARAMS to your needs.
# I have removed the -ip <xxx.xxx.xxx.xxx> portion from this command as the last update to L4D removed the need for it
# If you have issues with your game put the -ip string back into the PARAMS line below
PARAMS="-game cstrike -tickrate 100 -port 27017 +map gg_simpsons_arena +maxplayers 20 -autoupdate" #These options can vary a bit from game to game, google is your friend here.
NAME=SRCDS-GG #needs to be adjusted each time
DESC="Frag Mine Sungame"
case "$1" in
start)
 echo "Starting $DESC: $NAME"
 if [ -e $DIR ];
 then
  cd $DIR
su $SRCDS_USER -l -c "screen -d -m -S $NAME $DAEMON $PARAMS"
  screen -d -m -S $NAME $DAEMON $PARAMS
 else echo "No such directory: $DIR!"
 fi
 ;;
stop)
 if screen -ls |grep $NAME
 then
     echo -n "Stopping $DESC: $NAME"
     kill `screen -ls |grep $NAME |awk -F . '{print $1}'|awk '{print $1}'`
    echo " ... done."
else
    echo "Coulnd't find a running $DESC"
fi
;;
restart)
 if screen -ls |grep $NAME
 then
     echo -n "Stopping $DESC: $NAME"
     kill `screen -ls |grep $NAME |awk -F . '{print $1}'|awk '{print $1}'`
     echo " ... done."
 else
     echo "Couldn't find a running $DESC"
 fi
 echo -n "Starting $DESC: $NAME"
 cd $DIR
 screen -d -m -S $NAME $DAEMON $PARAMS
 echo " ... done."
 ;;
status)
 # Check whether there's a "srcds" process
 # if "checkproc" is installed, you can use this:
 # checkproc $DIR/srcds_run && echo "DODS-Server RUNNING" || echo "DODS-Server NOT RUNNING"
 # (thx to commander)
 ps aux | grep -v grep | grep $NAME > /dev/null
 CHECK=$?
 [ $CHECK -eq 0 ] && echo "SRCDS is UP" || echo "SRCDS is DOWN"
 ;;
*)
 echo "Usage: $0 {start|stop|status|restart}"
 exit 1
 ;;
esac
exit 0

```
and for making sure it was responding 4 php scripts:
```
<?php
function source_query($ip)
{
$cut = explode(":", $ip);
$HL2_address = $cut[0];
$HL2_port = $cut[1];
$HL2_command = "\377\377\377\377TSource Engine Query\0";
$HL2_socket = fsockopen("udp://".$HL2_address, $HL2_port, $errno, $errstr,3);
fwrite($HL2_socket, $HL2_command);
$JunkHead = fread($HL2_socket,4);
$CheckStatus = socket_get_status($HL2_socket);
return $CheckStatus['unread_bytes'];
}

$ip="127.0.0.1:27017";
$query = source_query($ip); // $ip MUST contain IP:PORT

if($query == 0 )
{
system("service gg restart");
//echo "server down \n";
}
else
{
//echo "server up\n";
}
?>

```
and corresponding cronjobs running each of the php scripts once a minute.
not ideal, but it works well enough.
Tried to make a watchdog in C(instead of the above php script) but had issues with sockets not working properly(still looking into that though, will post the code if it works)

---

