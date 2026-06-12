---
title: "init.d scripts and deamons"
date: 2009-10-13
forum: Server Platforms
---

### Post by dannyor on 2009-10-13
Hi
I'm trying to implement an init.d script to run a certain Java application I've written. I have customized /etc/init.d/skeleton to create my own script (let us say it is called /etc/init.d/ddd). However when I call it it does not run as a background process (daemon). It is all there on the terminal where I called it from (that is my call to /etc/init.d/ddd does not return. It is blocked). When I stop it on the terminal (CTRL+C) it stops as well.
Well, I admit. I have completely failed to implement a daemon.
How do I do this?

Thanks in advance to all ye Linux savvies ...

p.s
When I look at /usr/sbin I see all kinds of binaries that are daemons. am I supposed to create something like that? can I generate one?

---

### Post by scorp123 on 2009-10-13
> **dannyor said:**
>  However when I call it it does not run as a background process (daemon).  And why not send it into the background?

If you execute any program like this:
```
/path/to/program
```
... it will sit there in the terminal and wait until someone terminates it. That's where you are now.

But if you execute any program like this:
```
/path/to/program &
```
... it will be run in the background. That's not yet really a daemon but it's close and only takes minimum effort.

To really have any program executed as a daemon you could use this program:
```
/sbin/start-stop-daemon
```

Please read the manual:
```
man start-stop-daemon
```

So if sending the program into the background as explained above is not enough then the idea here would be that you launch your program via **"start-stop-daemon"** 

Example script that uses "start-stop-daemon" to launch "Dropbox" as a daemon upon system boot:

**/etc/init.d/dropboxd**

```
# dropbox as service at boot time
#
# Found here:
# http://wiki.getdropbox.com/Regole/TextBasedLinuxInstall
# 
#
# To install as service at boot time:
#
# sudo chmod +x /etc/init.d/dropboxd
# sudo update-rc.d dropboxd defaults
#
DROPBOX_USERS="john willy angela suzie francie tom"
start() {
    echo "Starting dropbox..."
    for dbuser in $DROPBOX_USERS; do
        start-stop-daemon -b -o -c $dbuser -S -x /home/$dbuser/.dropbox-dist/dropboxd
    done
}

stop() {
    echo "Stopping dropbox..."
    for dbuser in $DROPBOX_USERS; do
        start-stop-daemon -o -c $dbuser -K -x /home/$dbuser/.dropbox-dist/dropboxd
    done
}

status() {
    for dbuser in $DROPBOX_USERS; do
        dbpid=`pgrep -u $dbuser dropboxd`
        if [ -z $dbpid ] ; then
            echo "dropboxd for USER $dbuser: not running."
        else
            echo "dropboxd for USER $dbuser: running."
        fi
    done
}


case "$1" in
  start)
    start
    ;;
  
  stop)
    stop
    ;;

  restart|reload|force-reload)
    stop
    start
    ;;

  status)
    status
    ;;

  *)
    echo "Usage: /etc/init.d/dropbox {start|stop|reload|force-reload|restart|status}"
    exit 1

esac

exit 0
```

---

### Post by dannyor on 2009-10-13
Thanks scorp.
As I said, I used the skeleton at /etc/init.d as a start point and it does use the start-stop-daemon you've mentioned, however it does not work but runs, well, NOT in the backgroud. I do know of adding the '&' in the end of the command, but that's not what I want since the process is still related in some way to the terminal and the process is killed when the terminal exits. I have a working example for a tomcat server I use but had no success with it yet.

---

### Post by scorp123 on 2009-10-13
> **dannyor said:**
> Thanks scorp.
As I said, I used the skeleton at /etc/init.d as a start point and it does use the start-stop-daemon you've mentioned, however it does not work but runs, well, NOT in the backgroud. I do know of adding the '&' in the end of the command, but that's not what I want since the process is still related in some way to the terminal and the process is killed when the terminal exits. I have a working example for a tomcat server I use but had no success with it yet. Yes, that's strange then. Could you try this: Use your script and instead of the program you wanted to run put another program in there ... Just to see if the script is at fault or if it's something regarding how the program is acting?

For example you could put something harmless in there, e.g. "ping" ("ping" packets should be small and should do no harm if you ping something on your own network) ... If it goes to the background as it should then this would mean that the script is OK and that your other application is in need of more debugging. If however it does not go into background then this would mean that the script is at fault ...  See what I mean?

I'd test that like this.

Or: You leave your existing script for a second and use e.g. my template above and re-write your script from scratch? Just to see if you get the same strange effect again ...?

---

### Post by dannyor on 2009-10-13
Thanks again scorp. 
I have compared your example with my script and found what the problem was.
I did not have the '-b' flag on the start-stop-daemon (thats how the /etc/init.d/skeledon is).

All the best

---

### Post by Sporkman on 2009-10-14
You need to have the daemon it spawns fork itself.

Here's a link:

[http://www-theorie.physik.unizh.ch/~dpotter/howto/daemonize](http://www-theorie.physik.unizh.ch/~dpotter/howto/daemonize)

---

