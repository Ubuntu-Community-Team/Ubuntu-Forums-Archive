---
title: "Ubuntu server terminating background process when last ssh closed"
date: 2015-03-05
forum: Server Platforms
---

### Post by jtkb on 2015-03-05
[LEFT][COLOR=#000000][FONT=Arial]I have an Ubuntu 14.04 server and I am trying to start [Apache Karaf]("http://karaf.apache.org/") from a ssh, exit the ssh and expect Karaf to remain executing. What I actually find is that as soon as the last ssh is closed/logged out, the Karaf process is terminated.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]

I start Karaf with the bin/start command as [described here (background mode)]("http://karaf.apache.org/manual/latest/users-guide/start-stop.html") and the docs state that this should put Karaf into the background mode, however my experience has shown this does not happen.

 As soon as I logout of ssh, the process dies.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I have tried using 'nohup' but again the karaf process is always killed once the last ssh is closed. I don't believe this is a problem with Karaf but some configuration of Ubuntu. I also see the same behaviour on Linux Mint.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]However, Karaf DOES run as a backgorund process if I run it on a RaspberryPi, which is running Raspbian.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Is there a configuration of sshd that forces all processes started in a ssh to terminated once ALL ssh connections are ended? Whatever I try I cannot make a background process remain once I have logged out

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Looking at the start script it uses exec :
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]exec "$KARAF_HOME"/bin/karaf server "$@" >> "$KARAF_REDIRECT" 2>&1 &[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

and thus another process is created. If I just do a bin/start file descriptors 0,1 and 2 are all directed toward `/dev/null'.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]If I do ```
nohup ./start 0<&- &>/dev/null &
``` followed by a disown, then fd 0,1,2 of the resultant process all go to /dev/null. I noted on the RaspberryPi that fd 0,1 and 2 all state /dev/pts/0 (deleted)

I have also tried using the `setsid` command in the following ways:

```
setsid nohup ./start &
setsid nohup ./karaf server &
setsid nohup ./start 0<&- &>/dev/null &
```

Still none of these work. I do notice however when I use 'setsid' that ```
ps -elf
``` reports the proccess doesn't have a controlling terminal and the PPID is 1, yet it is ALWAYS terminated when the last ssh is closed.

Can anyone help me resolve this issue?

Please note I don't wish to use screen or tmux. There must be a way to resolve this as it works on a RaspberryPi running Raspbian.
[/FONT][/COLOR]
[/LEFT]

---

### Post by ian-weisser on 2015-03-05
> **jtkb said:**
> [COLOR=#000000][FONT=Arial]I have an Ubuntu 14.04 server and I am trying to start [Apache Karaf]("http://karaf.apache.org/") from a ssh, exit the ssh and expect Karaf to remain executing. What I actually find is that as soon as the last ssh is closed/logged out, the Karaf process is terminated.[/FONT][/COLOR]

When you log in, all processes that you start become *children* of your login session. Regardless of whether they are background or foreground.
When you logout, as part of closing out your login process, the system automatically terminates all the children (otherwise, they would be orphaned).

The easy way to resolve your problem is to consult the 'system service' instructions in your Karaf documentation. System services are children of init (PID 1), not your login session, so they don't terminate when you logout. You can start/stop them manually...or programmatically based on any criteria you can detect or any rule you can conceive.

---

### Post by jtkb on 2015-03-06
> **ian-weisser said:**
> When you log in, all processes that you start become *children* of your login session. Regardless of whether they are background or foreground.
When you logout, as part of closing out your login process, the system automatically terminates all the children (otherwise, they would be orphaned).

The easy way to resolve your problem is to consult the 'system service' instructions in your Karaf documentation. System services are children of init (PID 1), not your login session, so they don't terminate when you logout. You can start/stop them manually...or programmatically based on any criteria you can detect or any rule you can conceive.

Hi Ian

I follow all that you're saying but the last thing I tried, using 'setsid' appeared to change the PPID of Karaf to one and with no controlling terminal (as confirmed with ps -elf). However when I close the ssh, Karaf is STILL terminated, even though I've changed the PPID and set no controlling terminal. There has to be a way to do this otherwise no daemons would ever run in Ubuntu. Also I can start Karaf on a Raspberry Pi (with Raspbian) by issuing the start command and it works, as I expect and as it should. It's almost as though Ubuntu is preventing me from from starting a daemon.

---

### Post by nerdtron on 2015-03-06
I guess you may want to use screen? [www.youtube.com/watch?v=y-cZpAlhpNU](www.youtube.com/watch?v=y-cZpAlhpNU)


Screen allows you have a "virtual terminal" then run any command you like inside that screen. Now don't exit the screen but rather "detach" to it. It will still run and keep any process you left inside running. You can even exit the ssh session and go back later to "reattach" to that screen.

---

### Post by jtkb on 2015-03-06
> **nerdtron said:**
> I guess you may want to use screen? [www.youtube.com/watch?v=y-cZpAlhpNU]("http://www.youtube.com/watch?v=y-cZpAlhpNU")


Screen allows you have a "virtual terminal" then run any command you like inside that screen. Now don't exit the screen but rather "detach" to it. It will still run and keep any process you left inside running. You can even exit the ssh session and go back later to "reattach" to that screen.

Screen isn't working either. Although SCREEN remains after I close ssh, the karaf process terminates.

---

### Post by ian-weisser on 2015-03-06
> **jtkb said:**
> I follow all that you're saying but the last thing I tried, using 'setsid' appeared to change the PPID of Karaf to one and with no controlling terminal (as confirmed with ps -elf). However when I close the ssh, Karaf is STILL terminated, even though I've changed the PPID and set no controlling terminal. There has to be a way to do this otherwise no daemons would ever run in Ubuntu. Also I can start Karaf on a Raspberry Pi (with Raspbian) by issuing the start command and it works, as I expect and as it should. It's almost as though Ubuntu is preventing me from from starting a daemon.

To me, that seems like a bug in Karaf. "Karaf doesn't work on Ubuntu"
Lots of daemons run in Ubuntu without special fiddling.

---

### Post by MAFoElffen on 2015-03-07
ian-weisser was spot-on with post #2... But he didn't go into specifics on how to handle that.

I just answered this in another thread, so instead of retyping it all again:
[http://ubuntuforums.org/showthread.php?t=2268207&p=13240949#post13240949](http://ubuntuforums.org/showthread.php?t=2268207&p=13240949#post13240949)

---

