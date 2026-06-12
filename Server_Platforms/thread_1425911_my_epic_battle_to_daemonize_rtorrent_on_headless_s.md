---
title: "my epic battle to daemonize rtorrent on headless server"
date: 2010-03-09
forum: Server Platforms
---

### Post by Jive Turkey on 2010-03-09
I spent most of the day yesterday trying to make this work and haven't gotten really anywhere with it.  Building from source quietly failed although it built without error and I got checkinstall to pack it up it didn't actually work.  So I rolled back to the repository version of rtorrent.  As I understand it, the things I need to do are (I am thwarted at every step):

[LIST=1]
[*]create user with --disabled-password option
[INDENT]creating the user is no problem except they seem to have no shell, and running any command while su'd as that user throws an error like```
Cannot open your terminal '/dev/pts/1' - please check.
``` I found somewhere that changing the permissions on /dev/pts/N solves this problem however N can change after a reboot, or probably following other events so that's likely not the right fix.[/INDENT]
[*]create init script to run rtorrent as user in previous step
[INDENT]I found an example that seems like it works but I wont know for sure until I get the prior step worked out fully.  Here it is:```
#!/bin/bash
#############
###<Notes>###
#############
# This script depends on screen.
# For the stop function to work, you must set an
# explicit session directory using ABSOLUTE paths (no, ~ is not absolute) in your rtorrent.rc.
# If you typically just start rtorrent with just "rtorrent" on the
# command line, all you need to change is the "user" option.
# Attach to the screen session as your user with 
# "screen -dr rtorrent". Change "rtorrent" with srnname option.
# Licensed under the GPLv2 by lostnihilist: lostnihilist _at_ gmail _dot_ com
##############
###</Notes>###
##############

#######################
##Start Configuration##
#######################
# You can specify your configuration in a different file 
# (so that it is saved with upgrades, saved in your home directory,
# or whateve reason you want to)
# by commenting out/deleting the configuration lines and placing them
# in a text file (say /home/user/.rtorrent.init.conf) exactly as you would
# have written them here (you can leave the comments if you desire
# and then uncommenting the following line correcting the path/filename 
# for the one you used. note the space after the ".".
# . /etc/rtorrent.init.conf

#Do not put a space on either side of the equal signs e.g.
# user = user 
# will not work
# system user to run as
user="dummy"

# the system group to run as, not implemented, see d_start for beginning implementation
# group=`id -ng "$user"`

# the full path to the filename where you store your rtorrent configuration
config="/etc/rtorrent/rtorrent.rc"

# set of options to run with
options=""

# default directory for screen, needs to be an absolute path
base="/home/dummy/scrn"

# name of screen session
srnname="rtorrent"

# file to log to (makes for easier debugging if something goes wrong)
logfile="/var/log/rtorrentInit.log"
#######################
###END CONFIGURATION###
#######################
PATH=/usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
DESC="rtorrent"
NAME=rtorrent
DAEMON=$NAME
SCRIPTNAME=/etc/init.d/$NAME

checkcnfg() {
    exists=0
    for i in `echo "$PATH" | tr ':' '\n'` ; do
        if [ -f $i/$NAME ] ; then
            exists=1
            break
        fi
    done
    if [ $exists -eq 0 ] ; then
        echo "cannot find rtorrent binary in PATH $PATH" | tee -a "$logfile" >&2
        exit 3
    fi
    if ! [ -r "${config}" ] ; then 
        echo "cannot find readable config ${config}. check that it is there and permissions are appropriate" | tee -a "$logfile" >&2
        exit 3 
    fi 
    session=`getsession "$config"` 
    if ! [ -d "${session}" ] ; then
        echo "cannot find readable session directory ${session} from config ${config}. check permissions" | tee -a "$logfile" >&2
        exit 3
  stty stop undef && stty start undef
  su -c "screen -ls | grep -sq "\.${srnname}[[:space:]]" " ${user} || su -c "screen -dm -S ${srnname} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
  # this works for the screen command, but starting rtorrent below adopts screen session gid
  # even if it is not the screen session we started (e.g. running under an undesirable gid
  #su -c "screen -ls | grep -sq "\.${srnname}[[:space:]]" " ${user} || su -c "sg \"$group\" -c \"screen -fn -dm -S ${srnname} 2>&1 1>/dev/null\"" ${user} | tee -a "$logfile" >&2
  su -c "screen -S "${srnname}" -X screen rtorrent ${options} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
}

d_stop() {
    session=`getsession "$config"`
    if ! [ -s ${session}/rtorrent.lock ] ; then
        return
    fi
    pid=`cat ${session}/rtorrent.lock | awk -F: '{print($2)}' | sed "s/[^0-9]//g"`
    if ps -A | grep -sq ${pid}.*rtorrent ; then # make sure the pid doesn't belong to another process
        kill -s INT ${pid}
    fi
}

getsession() { 
    session=`cat "$1" | grep "^[[:space:]]*session[[:space:]]*=" | sed "s/^[[:space:]]*session[[:space:]]*=[[:space:]]*//" `
    echo $session
}

checkcnfg

case "$1" in
  start)
    echo -n "Starting $DESC: $NAME"
    d_start
    echo "."
    ;;
  stop)
    echo -n "Stopping $DESC: $NAME"
    d_stop
    echo "."
    ;;
  restart|force-reload)
    echo -n "Restarting $DESC: $NAME"
    d_stop
    sleep 1
    d_start
    echo "."
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0
```
Ideally I want to execute screen in a way that it would be shared with other system users so I wouldn't have to su to dummy account first, I found on the screen docs an "acladd *username*" command, but its not clear how to make it the default, either for the user or the init script.  Any ideas?
[/INDENT]
[*]create .rtorrent.rc in user's $HOME
[INDENT]This part does work how I like but I'm including the config in case anyone has any tips to improve it.```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.
 
# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 512
max_memory_usage = 805306368
 
# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 1
max_peers_seed = 10
 
# Maximum number of simultanious uploads per torrent.
max_uploads = 10
 
# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 22

send_buffer_size = 1M
receive_buffer_size = 25K

directory = /home/dummy/rtorrent/incomplete/
 
session = /home/dummy/rtorrent/session/
 
#save session
session_save = yes
 
# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/dummy/rtorrent/src/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=100M

# Move completed downloads to complete directory
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/dummy/rtorrent/ ;d.set_directory=/home/dummy/rtorent/"
 
# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,200"
 
# The ip address reported to the tracker.
ip = 127.0.0.1
 
# The ip address the listening socket and outgoing connections is
# bound to.
bind = 10.0.0.100
 
# Port range to use for listening.
port_range = 50666-51000
 
check_hash = no
 
# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = no
 
# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa
 
# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,enable_retry,prefer_plaintext
 
# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
 dht = auto
 
# UDP port to use for DHT.
#
 dht_port = 6881
 
# Enable peer exchange (for torrents not marked private)
#
 peer_exchange = yes
 
#
# Do not modify the following parameters unless you know what you're doing.
#
 
# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10
 
# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100
 
# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10
 
encoding_list = UTF-8
```
[/INDENT]
[*]reboot and enjoy the magic
[/LIST][INDENT]No love :([/INDENT]

---

### Post by samosamo on 2010-03-10
This is how I did it. I'll write it out the basic steps and if you need any more help just ask.  rtorrent is not a daemon type program so you'll have to think outside the box.

[LIST]
[*]Install rtorrent, apache2, and rutorrent.
[*]Create user to run rtorrent from
[*]Put rutorrent in ~/public_html/rutorrent
[*]Have users access your box via web [http://dyniphost.com/~user/rutorrent](http://dyniphost.com/~user/rutorrent)
[*]You should enable basic auth with .htaccess
[*]Take my crontab script to run rtorrent on startup/restart after crashes
```
$ cat rtorrentcheck.sh  
#!/bin/bash

whoami=`whoami`
running=`ps -u $whoami | grep rtorrent$ | wc -l`

if [ $running -eq 0 ]; then
	/usr/bin/screen -dmS rtorrent rtorrent
fi

```
[/LIST]

---

### Post by samosamo on 2010-03-10
Uhhh coincidence?  As I posted this, it seems the rutorrent team was releasing version 3.0 at the same time.  Documentation doesn't seem to be uploaded yet but looking through these files it looks like it has user support??

---

### Post by apokkalyps on 2010-10-11
> **samosamo said:**
> This is how I did it. I'll write it out the basic steps and if you need any more help just ask.  rtorrent is not a daemon type program so you'll have to think outside the box.

[LIST]
[*]Install rtorrent, apache2, and rutorrent.
[*]Create user to run rtorrent from
[*]Put rutorrent in ~/public_html/rutorrent
[*]Have users access your box via web [http://dyniphost.com/~user/rutorrent](http://dyniphost.com/~user/rutorrent)
[*]You should enable basic auth with .htaccess
[*]Take my crontab script to run rtorrent on startup/restart after crashes
```
$ cat rtorrentcheck.sh  
#!/bin/bash

whoami=`whoami`
running=`ps -u $whoami | grep rtorrent$ | wc -l`

if [ $running -eq 0 ]; then
	/usr/bin/screen -dmS rtorrent rtorrent
fi

```
[/LIST]

Sorry to be dense, but can you tell me what to do with this script once I have it?

---

### Post by msandoy on 2010-10-11
I may be wrong, but would it not be easier just to log in to the server, run screen rtorrent, and use screen -r to change into that session every time you want to check on it? At least that is what I do with my server. Just remember to go ctrl+a, ctrl+d before you exit the ssh session.
I have rtorrent automatically pick up torrents from a specific folder, and automatically stop seeding at a certain share ratio. Torrents are fed to the server via a bash script using rsync. Works like a charm. :-)

---

