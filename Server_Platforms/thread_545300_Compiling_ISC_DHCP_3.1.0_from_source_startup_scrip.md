---
title: "Compiling ISC DHCP 3.1.0 from source startup script problem"
date: 2007-09-07
forum: Server Platforms
---

### Post by CounterStrike on 2007-09-07
I am running Dapper server (2.6.15-29-server) and need to run ISC DHCP version 3.1.0 which I have been trying to compile from source. I have updated the system as to where apt-get advises there are no new updates, installed build-essential and linux-headers-2.6.15-29-server so I can compile the source form the tarball. after I configure, make and make install the source, everything appears fine and I can see that dhcpd is available from the command line and states it is ISC version 3.1.0 but the problem is that  it does not create a script (that I can find) in /etc/init.d
Does anyone know if this is by design? I have not had a whole lot of experience compiling from source, but the ones that I did did put scripts in /etc/init.d (like vmware server). Am I just missing something required to build the installation (another package)? I am trying to use the 3.1.0 version due to the improvements in failover for dhcp which is why I don't just use the dhcp3-server package available in the repositories.

  I would sincerely appreciate any feedback regarding this issue I am having.

Thanks,

CounterStrike   :confused:

---

### Post by CounterStrike on 2007-09-07
So I didn't see anything definitive saying that isc's dhcpd comes with or without a script for controlling the starting and stopping of dhcpd, but I did find the commands how to start /usr/sbin/dhcpd (and it starts!). If only I could have figured out how to stop it then I would have been ok with that method, but I couldn't find any command line options to gracefully stop the daemon once it started. I did figure out I could add that command to the rc.local script to start at boot up, but then again I couldn't stop it unless I killed the process. So further googling and digging (funny how easy it was to find the information under dhcpd stop, when searching for dhcpd start did not return the results with the scripts in it) I came across several good dhcp start stop and restart scripts to put into /etc/init.d/

Here is the one I ended up using

```
#! /bin/sh
#
# Start or stop dhcpd daemon
#

# Add all interfaces you want dhcpd to handle here

test -x /usr/sbin/dhcpd || exit 0

# Set run_dhcpd to 1 to start dhcpd at boot or 0 to disable it.
run_dhcpd=1

if [ $run_dhcpd = 0 ]; then
        cat <<EOF

Please edit the file /etc/dhcpd.conf according to your needs. The current
/etc/dhcpd.conf is just the sample file that is provided with the DHCP
package from the Internet Software Consortium, so it will not be useful
at all for you.

After you have edited /etc/dhcpd.conf you will have to edit
/etc/init.d/dhcp as well. There you will have to set the variable
run_dhcpd to 1, and then type "/etc/init.d/dhcp start" to start the
dhcpd daemon.

EOF
        exit 0
fi

DHCPDPID=/var/run/dhcpd.pid

case "$1" in
        start)
                start-stop-daemon --start --quiet --pidfile $DHCPDPID \
                        --exec /usr/sbin/dhcpd -- eth0
                ;;
        stop)
                start-stop-daemon --stop --quiet --pidfile $DHCPDPID
                ;;
        restart)
                start-stop-daemon --stop --quiet --pidfile $DHCPDPID
                sleep 2
                start-stop-daemon --start --quiet --pidfile $DHCPDPID \
                        --exec /usr/sbin/dhcpd -- eth0
                ;;
        *)
                echo "Usage: /etc/init.d/dhcp {start|stop|restart}"
                exit 1
esac

exit 0  

```

After getting that in it wouldn't run. It said permission denied. After some quick googling I came across a debian page on adding init.d scripts. I had to chmod 755 dhcp and then update-rc.d dhcp defaults to add links to the startup and shutdown scripts. [http://www.debian-administration.org/articles/28]("http://www.debian-administration.org/articles/28")
Now all is good. 

Did I mention i'm a noob?

Hope this helps someone else in the future.

Thanks,

CounterStrike

---

