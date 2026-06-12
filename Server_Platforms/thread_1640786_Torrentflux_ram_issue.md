---
title: "Torrentflux ram issue"
date: 2010-12-08
forum: Server Platforms
---

### Post by Jonasu on 2010-12-08
Yesterday I threw together a new server with some old computerparts laying around in my room.. I installed 4gb of ram and thought that would be more than enough to run LAMP and a simple torrent program.
So I decided to install torrentflux because of the webinterface. But I found out soon that, after a while with downloading and refreshing the interface, it used almost 4gb of ram! I don't know if this is fixable, but I just like to know if someone else got the same problem and somehow managed to fix it.

But if this is an "unfixable" torrentflux bug, is there any similar 
programs I could use instead? 

Thanks!

---

### Post by arrrghhh on 2010-12-08
rtorrent is the only one I recommend.

Torrentflux spawns a separate process for _each_ torrent.  rtorrent is by FAR the best for footprint.

It doesn't come with a GUI of any sort unfortunately, by default it uses ncurses.  However, there are a TON of options out there - my favorite is '[rutorrent](http://code.google.com/p/rutorrent/)'.

Rtorrent is in the repo's, but as I recall I had to compile it to get xmlrpc working correctly with rutorrent.  [This post](http://forums.rutorrent.org/index.php?topic=115.msg1992#msg1992) is a good summary of how to compile rtorrent and get it ready for rutorrent.  The rest of that thread is not such a good read :p - I was struggling with a simple configuration issue with rtorrent, in relation to the 'watch' directory!

---

### Post by Jonasu on 2010-12-08
> **arrrghhh said:**
> rtorrent is the only one I recommend.

Torrentflux spawns a separate process for _each_ torrent.  rtorrent is by FAR the best for footprint. ......

Wow! Thanks. RuTorrent looks awesome, but should I go with a fresh ubuntu install before I install and compile rTorrent? I always seem to screw up something when I'm not following guides 100%.

Anyways, to bad torrentflux didn't work out as I had hoped, because it was so easy to install :P

---

### Post by arrrghhh on 2010-12-08
> **Jonasu said:**
> Wow! Thanks. RuTorrent looks awesome, but should I go with a fresh ubuntu install before I install and compile rTorrent? I always seem to screw up something when I'm not following guides 100%.

Anyways, to bad torrentflux didn't work out as I had hoped, because it was so easy to install :P

rtorrent from the repo's is dead-easy to install, I just recall it not working correctly with xmlrpc so no other client could connect to it... if you don't mind using the ncurses interface, then by all means, apt-get install rtorrent :D

---

### Post by Jonasu on 2010-12-09
> **arrrghhh said:**
> rtorrent from the repo's is dead-easy to install, I just recall it not working correctly with xmlrpc so no other client could connect to it... if you don't mind using the ncurses interface, then by all means, apt-get install rtorrent :D

Well, I actually do mind using the ncurses interface. I really want a webinterface, and that RuTorrent interface looked amazing. But then again, I always seem to screw up "long" guides like that without following it 100%, which is the case when I've already have installed a lot of stuff on the server. This time was no exception, i didn't get it to work. I don't think RuTorrent managed to link with rTorrent, there was a lot of buttons missing etc.. I'm going to try it again when I get the time to.

If someone know of a good "STEP BY STEP" tutorial for ubuntu server 10.10, that would be awesome!

---

### Post by arrrghhh on 2010-12-09
Well I wasn't able to find a complete step-by-step guide, but there's a lot more configuration than in that post... That post basically gets the packages installed.  You have to enable xmlrpc, etc... The rutorrent site should have all you need.

Indeed -

[Main site](http://code.google.com/p/rutorrent/wiki/Main) - look at the Setup and Configuration section.

---

### Post by windependence on 2010-12-09
Linux != Windows
 
Linux will use RAM if it is available, and will keep programs cached in RAM until that RAM is needed. It has a totally different memory management model than Windows, and I might add a much better one.
 
-Tim

---

### Post by Jonasu on 2010-12-09
> **arrrghhh said:**
> Well I wasn't able to find a complete step-by-step guide, but there's a lot more configuration than in that post... That post basically gets the packages installed.  You have to enable xmlrpc, etc... The rutorrent site should have all you need.

Indeed -

[Main site](http://code.google.com/p/rutorrent/wiki/Main) - look at the Setup and Configuration section.

Thanks, I'll try that. I also found some step-by-step rTorrent RuTorrent guides on google as well..

> **windependence said:**
> Linux != Windows
 
Linux will use RAM if it is available, and will keep programs cached in RAM until that RAM is needed. It has a totally different memory management model than Windows, and I might add a much better one.
 
-Tim

So what you try to say is that it's not "dangerous" to have a program using 95% of all the ram available? I have no swap so I got a bit worried that it might crash. But you're positive it won't?

Anyways, I'll think I stick with another solution (at least try)..

---

### Post by arrrghhh on 2010-12-09
> **windependence said:**
> Linux != Windows
 
Linux will use RAM if it is available, and will keep programs cached in RAM until that RAM is needed. It has a totally different memory management model than Windows, and I might add a much better one.
 
-Tim

Agreed, but I don't think that's the issue here.  I may be inserting some of my bias against Torrentflux here, but since it does spawn a separate process for each torrent, you must admit that rtorrent is MUCH better footprint-wise.  I ran into issues when I had too many torrents running in Torrentflux.  I've heard of people running 9,000+ torrents with rtorrent.  Now granted that's a bit ludicrous, but it's nice to know I can :D

> **Jonasu said:**
> So what you try to say is that it's not "dangerous" to have a program using 95% of all the ram available? I have no swap so I got a bit worried that it might crash. But you're positive it won't?

You need to have some swap space... It's not dangerous normally, no.  Linux tries to use all available RAM, and it's very efficient at managing it.  However, you should **always** have some swap space - I typically say 1.5x as much RAM as you have.  Obviously if you have a ton of RAM you'll probably never touch swap, and 1.5x gets kinda crazy... but you still should have some swap, just in case.

---

### Post by Jonasu on 2010-12-10
There! I finally got rTorrent+RuTorrent to work! Thanks for all the help!

Btw. I'm having a hard time trying to make rTorrent run on startup. Any suggestions on how to do this?

---

### Post by arrrghhh on 2010-12-10
> **Jonasu said:**
> There! I finally got rTorrent+RuTorrent to work! Thanks for all the help!

Btw. I'm having a hard time trying to make rTorrent run on startup. Any suggestions on how to do this?

I have an rtorrent init script... Not sure where I got it from, but you're more than welcome to use it.  All you should need to change is the user!

```
#!/bin/sh
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
user="youruser"

# the system group to run as, not implemented, see d_start for beginning implementation
# group=`id -ng "$user"`

# the full path to the filename where you store your rtorrent configuration
config="`su -c 'echo $HOME' $user`/.rtorrent.rc"

# set of options to run with
options=""

# default directory for screen, needs to be an absolute path
base="`su -c 'echo $HOME' $user`"

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
    fi
}

d_start() {
  [ -d "${base}" ] && cd "${base}"
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

---

