---
title: "tigervnc server setup"
date: 2011-11-23
forum: Tutorials
---

### Post by andrewdev on 2011-11-23
Hello everyone,

I had some problems setting up tigervnc on Ubuntu. I ended up copying the way centos does the tigervnc configuration and writing my own init script. 

1. First download the tigervnc .deb for your architecture from [http://winswitch.org/dists/](http://winswitch.org/dists/)

2. Next create /etc/vncservers  (The configuration file for tigervnc) You will add a display number/username for each user you want to be able to connect. I added multiple for the same user so that I could connect with different screen geometries. 

```

# The VNCSERVERS variable is a list of display:user pairs.
#
# Uncomment the lines below to start a VNC server on display :2
# as my 'myusername' (adjust this to your own).  You will also
# need to set a VNC password; run 'man vncpasswd' to see how
# to do that.  
#
# DO NOT RUN THIS SERVICE if your local area network is
# untrusted!  For a secure way of using VNC, you should
# limit connections to the local host and then tunnel from
# the machine you want to view VNC on (host A) to the machine
# whose VNC output you want to view (host B)
#
# [user@hostA ~]$ ssh -v -C -L 590N:localhost:590M hostB
#
# this will open a connection on port 590N of your hostA to hostB's port 590M
# (in fact, it ssh-connects to hostB and then connects to localhost (on hostB).
# See the ssh man page for details on port forwarding)
#
# You can then point a VNC client on hostA at vncdisplay N of localhost and with
# the help of ssh, you end up seeing what hostB makes available on port 590M

# Use "-nolisten tcp" to prevent X connections to your VNC server via TCP.
#

# Use "-localhost" to prevent remote VNC clients connecting except when
# doing so through a secure tunnel.  See the "-via" option in the
# `man vncviewer' manual page.

VNCSERVERS="1:user1 2:user1 3:user2"
VNCSERVERARGS[1]="-geometry 800x600"
VNCSERVERARGS[2]="-geometry 1366x768"
VNCSERVERARGS[3]="-geometry 1366x768"

```

3. Create the init script /etc/init.d/vncservers (I am open to suggestions to make this better).

```

#!/bin/bash
### BEGIN INIT INFO
# Provides:
# Required-Start:
# Required-Stop:
# Default-Start:5
# Default-Stop:0 1 2 3 4 6
# Short-Description: runs vnc servers
### END INIT INFO 
PATH=/sbin:/bin:/usr/bin

. /lib/lsb/init-functions

. /etc/vncservers

start_vnc_servers() 
{
        echo "Starting ..."

        for server in $VNCSERVERS
        do
                set -- `echo $server | /usr/bin/tr ':' ' '`
                display=$1
                usern=$2

                echo "vncserver $server"
                echo "$usern \"vncserver :$display ${VNCSERVERARGS[$display]}\""
                su $usern -c "vncserver :$display ${VNCSERVERARGS[$display]}"
        done
}

stop_vnc_servers()
{
        echo "killing ..."

        for server in $VNCSERVERS
        do
                set -- `echo $server | /usr/bin/tr ':' ' '`
                display=$1
                usern=$2

                export HOME=/home/$2

                echo "vncserver $server"
                echo "vncserver -kill $display"
                vncserver -kill :$display
        done
}

case "$1" in
  start)
        start_vnc_servers
        exit 0
        ;;
  restart)
        stop_vnc_servers
        start_vnc_servers
        exit 0
        ;;
  stop)
        stop_vnc_servers
        exit 0
        ;;
  *)
        echo "Usage: $0 start|stop" >&2
        exit 1
        ;;
esac

```

3.Finally run:
```

update-rc.d vncservers enable
service vncservers start

```

Hope it works for you too.

---

### Post by sergey3 on 2013-08-24
in the step 3 you missed 2 commads


```

chmod +x /etc/init.d/vncservers
update-rc.d -f vncservers defaults
update-rc.d vncservers enable
service vncservers start

```

first one makes your script executable
second creates all links otherwise I was getting errors 

```

root@NAS# update-rc.d vncservers enable
update-rc.d: warning: vncservers start runlevel arguments (none) do not match LSB Default-Start values (5)
update-rc.d: warning: vncservers stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 2 3 4 6)
 System start/stop links for /etc/init.d/vncservers do not exist.

```

after doing this I&#7743; still getting warnings. How to fix them?

```

root@NAS# update-rc.d vncservers enable
update-rc.d: warning: vncservers start runlevel arguments (none) do not match LSB Default-Start values (5)
update-rc.d: warning: vncservers stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 2 3 4 6)
 Enabling system startup links for /etc/init.d/vncservers ...
 Removing any system startup links for /etc/init.d/vncservers ...
   /etc/rc0.d/K20vncservers
   /etc/rc1.d/K20vncservers
   /etc/rc2.d/S20vncservers
   /etc/rc3.d/S20vncservers
   /etc/rc4.d/S20vncservers
   /etc/rc5.d/S20vncservers
   /etc/rc6.d/K20vncservers
 Adding system startup for /etc/init.d/vncservers ...
   /etc/rc0.d/K20vncservers -> ../init.d/vncservers
   /etc/rc1.d/K20vncservers -> ../init.d/vncservers
   /etc/rc6.d/K20vncservers -> ../init.d/vncservers
   /etc/rc2.d/S20vncservers -> ../init.d/vncservers
   /etc/rc3.d/S20vncservers -> ../init.d/vncservers
   /etc/rc4.d/S20vncservers -> ../init.d/vncservers
   /etc/rc5.d/S20vncservers -> ../init.d/vncservers

```

---

