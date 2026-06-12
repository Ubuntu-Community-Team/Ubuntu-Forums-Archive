---
title: "does this netstat info look OK?"
date: 2011-12-28
forum: Security
---

### Post by coverup1128 on 2011-12-28
Does this output from netstat look OK? I am wondering whether the last three lines are legitimate. They are not associated with any process, nor have a connection state. Should these connection be regarded as suspicious?  
```

~$ netstat -pantu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -               
tcp        1      0 192.168.0.13:49013      119.161.91.18:80        CLOSE_WAIT  1747/clock-applet
tcp        1      0 192.168.0.13:49014      119.161.91.18:80        CLOSE_WAIT  1747/clock-applet
tcp        1      0 192.168.0.13:49015      119.161.91.18:80        CLOSE_WAIT  1747/clock-applet
tcp        1      0 192.168.0.13:49016      119.161.91.18:80        CLOSE_WAIT  1747/clock-applet
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
tcp6       0      0 ::1:25                  :::*                    LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:51466           0.0.0.0:*                           -               

```

---

### Post by CharlesA on 2011-12-28
Looks fine.

If you want to see what process is listening on a certain port you can always run this:

```
sudo netstat -nlp
```

---

### Post by coverup1128 on 2011-12-28
Great, thanks. It turned out the last two lines correspond to the avahi-daemon process. Is there a GUI for Ubuntu which allows to inspect and start/stop daemons? For instance Mandriva provides this functionality through the Mandriva Control Center.

---

### Post by CharlesA on 2011-12-28
I don't think there is any way to configure which daemons are running via GUI.

You can use service to do it from a terminal tho.

```
sudo service ssh stop|start|restart
```

---

### Post by Soul-Sing on 2011-12-29
I do kill avahi and cups after a fresh install via /etc/init
: [http://ubuntuforums.org/showthread.php?t=1823683](http://ubuntuforums.org/showthread.php?t=1823683)
#9 postcount

---

### Post by CharlesA on 2011-12-29
Thought you can just uninstall avahi and cups if you aren't using them.

Would that break something?

---

### Post by Soul-Sing on 2011-12-29
> **CharlesA said:**
> Thought you can just uninstall avahi and cups if you aren't using them.

Would that break something?

I don't know. But be safer to disable something than to uninstall it completely.(?)

---

### Post by CharlesA on 2011-12-29
> **leoquant said:**
> I don't know. But be safer to disable something than to uninstall it completely.(?)
Probably a good idea then.

---

