---
title: "/etc/init.d Script"
date: 2010-04-27
forum: Server Platforms
---

### Post by arrrghhh on 2010-04-27
So I created a ghetto fantastic init script for WebKeePass.  It literally is just two lines, it changes the directory to where WebKeePass is started from, then starts it...

My problem is, if I run the script by hand doing "sudo /etc/init.d/keepass start" it works just fine.

Here's the catch - it's a java-based app, so the only way I can tell if it's running is if I do a "ps -A |grep java" and I see two, I can determine which one is my PS3MediaServer, and pretty much assume the other one is WebKeePass.  But I can't hit the webUI at all.  If I kill that "other" java, run keepass by hand it works great.

So what am I missing?  Why can't it run on startup?  I did the update-rc.d command, and I see the script in /etc/rc5.d/, is that correct?

I'm running Lucid 10.04 server, and here's the "code" for my init script.  If someone has a better script to start it, I'm all ears!!

```
cd /var/www/PassMan/
./startup.sh
```

Thanks!

---

### Post by Jive Turkey on 2010-04-27
I think it could have something to do with the user under which the init script is executing the program.  When you run it yourself it runs as you, your script runs it as, I dunno maybe root or something.  Here is a custom script that works for me to run rtorrent as me at startup.  You should be able to modify it to suit your needs.```
#!/bin/sh 
############# 
###### 
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
###### 
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
user="jt" 

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
logfile="/home/ck/rtorrent-init.log" 
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

### Post by arrrghhh on 2010-04-27
Hrm... I'm going to have to do some heavy modification to that script.  At least it appears so, I don't think I want this running in a screen session or anything like that.

Plus, I run the init script as root (I believe) - I use the "sudo /etc/init.d/keepass start" to kick the script off - isn't running it with sudo similar to running it as the root user?


Edit - I may just borrow the su -c line to see if that makes a difference.

---

### Post by drreed on 2010-04-28
Sorry if I stopped reading too soon, but when I hit " and pretty much assume the other one is WebKeePass.," it sounded like you were seeing your grep process. You always find at least two with grep, the one you're looking for and the ps with grep. But I guess you know that and are having some other problem, right?

---

### Post by arrrghhh on 2010-04-28
Well the problem is it just appears as "java" in ps, top, whatever.

I have another program PS3MediaServer that appears the same, just "java".  However, its init script I can do a "status" check on it and it tells me which PID the media server is, so I'm assuming the other java is WebKeePass... Unfortunately, I'm not sure how to tell (perhaps I should try and steal some ideas from that media server's init script...) if that other java is WebKeePass or not.  As I showed & stated, my init script that I made for WebKeePass is abysmally designed.

---

### Post by drreed on 2010-04-28
I downloaded WebKeePass to see what it was all about.

While reading the documentation, I ran across this:

6- Start the Tomcat server by running the startup.bat or startup.sh (based on your
   platform). These scripts are in the root of your install folder – NOT the ones in
   Tomcat’s /bin folder (You can use the /bin startup scripts if you set your
JAVA_HOME variable needed by Tomcat).

That and some other things I found made me wonder:

1. What about this JAVA_HOME, can you do an echo $JAVA_HOME to see what's in there?

Where is the trouble, Java or Tomcat? Is it Tomcat that isn't starting?
Does it try? are there any logs produced?

I have some other things to do today, but depending on how they go, I *might* just install this package and see what happens when I try to start it. I have 9.10 Server, 9.10 desktop, and a CentOS server,  anyone of which I could try it on. (My 9.10 server was just installed for testing purposes so it sin't like that's a problem or anything, it's really my time)

Double check your JAVA_HOME and which scripts your running. Also, they provide this listing:
```

# This is the init script for starting up the
# Jakarta Tomcat server
#
# chkconfig: 345 91 10
# description: Starts and stops the Tomcat daemon.
#
# Source function library.
. /etc/rc.d/init.d/functions
# Get config.
. /etc/sysconfig/network
# Check that networking is up.
[ "${NETWORKING}" = "no" ] && exit 0
tomcat=/usr/local/jakarta-tomcat
startup=$tomcat/bin/startup.sh
shutdown=$tomcat/bin/shutdown.sh
export JAVA_HOME=/usr/local/jdk
start(){
 echo -n $"Starting Tomcat service: "
 #daemon -c
 $startup
 RETVAL=$?
 echo
}
stop(){
 action $"Stopping Tomcat service: " $shutdown
 RETVAL=$?
 echo
}
restart(){
 stop
 start
}

# See how we were called.
case "$1" in
start)
 start
 ;;
stop)
 stop
 ;;
status)
# This doesn't work ;)
 status tomcat
 ;;
restart)
 restart
 ;;
 *)
echo $"Usage: $0 {start|stop|status|restart}"
exit 1
esac
exit 0
**************************************************
3 - Edit the lines that start with ‘tomcat’ and ‘export’ to match where you installed Tomcat and
your jdk.
4 - Save to /etc/init.d and chmod
Save the edited file above to /etc/init.d directory as "tomcat" (at least on most newer releases since
/etc/init.d is a standard now). Then you have to allow execute access to the script, so run:
chmod a+x tomcat
5 - Add to appropriate run level directories The easy way to do this is to just simply run:
chkconfig --add tomcat
6 - Start the Tomcat service, and you should be off to the races!


```

I guess you did all that right? Why are you trying to kill a java process in your init?

Sorry if these are all dumb questions, I didn't see anyone helping you and thought I'd give it a try. Sometimes it helps because I'm not frustrated by all the tangles, and can see the forest.

:P

---

### Post by arrrghhh on 2010-04-28
Yes, thank you for helping.  I'm not sure we're meeting eye-to-eye on my issue, but in your post I think I see some things I can change.

What I mean by not meeting eye-to-eye - my server boots.  All my services come up, but when I try to hit the webpage for WebKeePass, it fails.  Apache is up, I can hit my normal website, just not WebKeePass.  So I check to see what is running with ps -A.  If I |grep java, then I see two java's running.  That's when I kill it by hand, and run the script by hand and it works _just fine_.

So that's why I thought the issue was with my init script, it just baffled me that I could run it using "sudo /etc/init.d/keepass start" and it would startup no problem.

When I leave it to start on its own from bootup, it *appears* to be running, but when I try to hit the page it is not.  Does that make sense now?

Like I said, your post reminded me of some things to check.  I will check and get back, thanks!!

Update - alright, I think I got it working!!  I still need to do the update-rc.d dance and reboot to see for sure, but this script definitely looks more robust.  Had to change a few things, comment some stuff out, but it's starting WebKeePass manually!  Thanks!!

Looks good, rebooted and I can hit the page!  Sweet, thanks again!!

---

### Post by drreed on 2010-04-28
Excellent. Good luck with it   :guitar:

---

