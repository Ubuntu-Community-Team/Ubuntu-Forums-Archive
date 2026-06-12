---
title: "Howto : Install Torque/PBS (job scheduler/manager) for a workstation"
date: 2006-10-31
forum: Tutorials
---

### Post by avelldiroll on 2006-10-31
Disclaimer :
* This is more some quick'n dirty notes than a real Howto, so feel free to dislike the presentation.
* This was done on dapper, it should work mostly on edgy but as I didn't play with it much yet I don't know if upstart (the new init system) is still configured that way (update-rc.d)
* I tend to consider people interested in job scheduling to be CLI friendly and able to know when to be root ... as I might forget to be that precise, please bear with me and feel free to comment on where it bothers you.

Background :
I am working on different clusters on a daily basis some of them I am in charge with. To configure those I am not using Ubuntu or any Debian based distro, I am mostly using Rocks cluster [http://www.rocksclusters.org](http://www.rocksclusters.org) for its quick installation process.
Recently I put my hand on a 4-cores machine (2*dualcore), that I wanted to share with other people for small calculations (so no cluster here). I installed Ubuntu (my distro of choice for desktop - the machine being also used for visualisation of data) and I didn't find any job management system in the repositories (appart from cron (too basic) and drqueue (dedicated to 3D rendering)). I then searched for some Ubuntu howto and didn't find any, hence this post. Finally I searched for some linux job management tools for workstations (on master only) and didn't find any ... if anybody has heard of one I would be happy to know about it.
So I went back and used the beast I knew, I set up Torque/PBS with the upsetting feeling that I was hammering a nail with a sledgehammer.

Howto:

Installing Torque PBS on a workstation

( This is mostly following the quickstart guide : [http://www.clusterresources.com/wiki/doku.php?id=torque:appendix:l_torque_quickstart_guide](http://www.clusterresources.com/wiki/doku.php?id=torque:appendix:l_torque_quickstart_guide))

* Get the latest torque tarball from [http://www.clusterresources.com/downloads/torque/](http://www.clusterresources.com/downloads/torque/)

* Compile and install it somewhere it won't bothers you 

```
tar -xzvf torque.tar.gz
cd torque
./configure --prefix=/opt/local
make
make install
```

* Launch the setup tool (in the torque folder from the tarball) indicating an existing user name (Admin_User here)

```
torque.setup Admin_USER

```
(This launch pbs_server at the end)
  
* Quick'n dirty configuration for a 4 cpus workstation

(the torque executables should be in your path, if you used the same installation directory as I did you sould have hat the following line to your ~/.bashrc :
export PATH=$PATH:/opt/local/bin:/opt/local/sbin
) 
(By default $(TORQUECFG)=/var/spool/torque )

```
cd $(TORQUECFG)

```
Edit server_priv/nodes with your favourite editor :
```
vi server_priv/nodes
```
and add the following line :
```
myworkstation  np=4
```
(myworkstation : the name you gave to the machine
 4 : the number of cpus)

Set the client server :
```
vi mom_priv/config
```
and add the following line :
```
$pbs_server = 127.0.0.1
```

Start the client daemon :
```
pbs_mom
```

Restart the pbs server daemon :
```
qterm
pbs_server
```

Launch the scheduler daemon :

```
pbs_sched
```

You can see the current Torque/PBS config :
```
qmgr -c "list server"
qmgr -c "list queue batch"
```

And set some options (here for a 4-core worstation) :
```
qmgr -c "set server query_other_jobs = True"
qmgr -c "set queue batch resources_max.ncpus=4
```"

Finally you may want the 3 servers to be launched at boot time :

For that purpose, you need to create those 3 files (based on /etc/init.d/skeleton) :
/etc/init.d/pbs_server
/etc/init.d/pbs_mom
/etc/init.d/pbs_sched

###/etc/init.d/pbs_mom###

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO
#
# Author:       Miquel van Smoorenburg <miquels@cistron.nl>.
#               Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
#               Please remove the "Author" lines above and replace them
#               with your own name if you copy and modify this script.
#
# Version:      @(#)skeleton  2.85-23  28-Jul-2004  miquels@cistron.nl
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/opt/local/bin:/opt/local/sbin
DESC="PBS MOM Client Daemon"
NAME=pbs_mom
DAEMON=/opt/local/sbin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

# Read config file if it is present.
#if [ -r /etc/default/$NAME ]
#then
#       . /etc/default/$NAME
#fi

#
#       Function that starts the daemon/service.
#
d_start() {
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON \
                || echo -n " already running"
}

#
#       Function that stops the daemon/service.
#
d_stop() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME \
                || echo -n " not running"
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME --signal 1
}

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
  #reload)
        #
        #       If the daemon can reload its configuration without
        #       restarting (for example, when it is sent a SIGHUP),
        #       then implement that here.
        #
        #       If the daemon responds to changes in its config file
        #       directly anyway, make this an "exit 0".
        #
        # echo -n "Reloading $DESC configuration..."
        # d_reload
        # echo "done."
  #;;
  restart|force-reload)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: $NAME"
        d_stop
        # One second might not be time enough for a daemon to stop,
        # if this happens, d_start will fail (and dpkg will break if
        # the package is being upgraded). Change the timeout if needed
        # be, or change d_stop to have start-stop-daemon use --retry.
        # Notice that using --retry slows down the shutdown process somewhat.
        sleep 1
        d_start
        echo "."
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

exit 0
```


###/etc/init.d/pbs_sched###

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO
#
# Author:       Miquel van Smoorenburg <miquels@cistron.nl>.
#               Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
#               Please remove the "Author" lines above and replace them
#               with your own name if you copy and modify this script.
#
# Version:      @(#)skeleton  2.85-23  28-Jul-2004  miquels@cistron.nl
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/opt/local/bin:/opt/local/sbin
DESC="PBS Scheduler Daemon"
NAME=pbs_sched
DAEMON=/opt/local/sbin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

# Read config file if it is present.
#if [ -r /etc/default/$NAME ]
#then
#       . /etc/default/$NAME
#fi

#
#       Function that starts the daemon/service.
#
d_start() {
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON \
                || echo -n " already running"
}

#
#       Function that stops the daemon/service.
#
d_stop() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME \
                || echo -n " not running"
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME --signal 1
}

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
  #reload)
        #
        #       If the daemon can reload its configuration without
        #       restarting (for example, when it is sent a SIGHUP),
        #       then implement that here.
        #
        #       If the daemon responds to changes in its config file
        #       directly anyway, make this an "exit 0".
        #
        # echo -n "Reloading $DESC configuration..."
        # d_reload
        # echo "done."
  #;;
  restart|force-reload)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: $NAME"
        d_stop
        # One second might not be time enough for a daemon to stop,
        # if this happens, d_start will fail (and dpkg will break if
        # the package is being upgraded). Change the timeout if needed
        # be, or change d_stop to have start-stop-daemon use --retry.
        # Notice that using --retry slows down the shutdown process somewhat.
        sleep 1
        d_start
        echo "."
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

exit 0
```


###/etc/init.d/pbs_server###

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO
#
# Author:       Miquel van Smoorenburg <miquels@cistron.nl>.
#               Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
#               Please remove the "Author" lines above and replace them
#               with your own name if you copy and modify this script.
#
# Version:      @(#)skeleton  2.85-23  28-Jul-2004  miquels@cistron.nl
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/opt/local/bin:/opt/local/sbin
DESC="PBS Server"
NAME=pbs_server
DAEMON=/opt/local/sbin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

# Read config file if it is present.
#if [ -r /etc/default/$NAME ]
#then
#       . /etc/default/$NAME
#fi

#
#       Function that starts the daemon/service.
#
d_start() {
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON \
                || echo -n " already running"
}

#
#       Function that stops the daemon/service.
#
d_stop() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME \
                || echo -n " not running"
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME --signal 1
}

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
  #reload)
        #
        #       If the daemon can reload its configuration without
        #       restarting (for example, when it is sent a SIGHUP),
        #       then implement that here.
        #
        #       If the daemon responds to changes in its config file
        #       directly anyway, make this an "exit 0".
        #
        # echo -n "Reloading $DESC configuration..."
        # d_reload
        # echo "done."
  #;;
  restart|force-reload)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: $NAME"
        d_stop
        # One second might not be time enough for a daemon to stop,
        # if this happens, d_start will fail (and dpkg will break if
        # the package is being upgraded). Change the timeout if needed
        # be, or change d_stop to have start-stop-daemon use --retry.
        # Notice that using --retry slows down the shutdown process somewhat.
        sleep 1
        d_start
        echo "."
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

exit 0

```



Now update the rc's :

```
update-rc.d pbs_server defaults 95
update-rc.d pbs_mom defaults 96
update-rc.d pbs_sched defaults 97

```

And you are done.

A sample script for qsub using lam/mpi would be :

```
#!/bin/bash
#PBS -l ncpus=4

echo $PBS_JOBID
echo "Start time :"
date
lamboot

mpirun -np 4 your_mpi_command

echo "End Time :"
date
lamclean
lamhalt

```

HIH

---

### Post by motin on 2007-02-25
Great that you explain how to configure autostart of the services! Looking all over for this to no avail. 

However, when ran the setup-script after installing, I got a lot of complaints about libtorque.so.0 not being found. 

I had to copy the libs manually:
```
cp ./src/lib/Libpbs/.libs/libtorque.so.0 /usr/lib/libtorque.so.0
cp ./src/lib/Libpbs/.libs/libtorque.so.0.0.0 /usr/lib/libtorque.so.0.0.0
```

In case someone has the same problem...

---

### Post by widedangel on 2009-09-16
when I execute
```
torque.setup  ADMIN_NAME 
```it gives me the following error
```
./torque.setup: 31: pbs_server: not found
./torque.setup: 33: qmgr: not found
ERROR: cannot set TORQUE admins
./torque.setup: 39: qterm: not found
```can someone help me?

---

### Post by oligoelemento on 2010-04-13
You must execute torque.setup as root user and previously you have to redefine the path of torque binaries and libs (root user doesn't use the path variable of normal users), in this way the script can find the pbs_server executable:
```
sudo su
export PATH="$PATH:/opt/torque-2.4.7/bin:/opt/torque-2.4.7/sbin"
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/opt/torque-2.4.7/lib" 
./torque.setup root localhost
```

---

### Post by vennyg on 2010-05-18
This was exactly what i was looking for! thanks a lot to the author for this post and also to the above commenter for clearing the air regarding insrtalling ./torque.setup as root.

---

### Post by marstonstudio on 2010-06-17
here's a helpful item: [http://www.clusterresources.com/pipermail/torqueusers/2008-July/007737.html](http://www.clusterresources.com/pipermail/torqueusers/2008-July/007737.html)

I'm trying to install torque to an Ubuntu 8.04 linux distribution, and would
rather install from source than use the available deb package.

I first wgot torque-2.3.1.tar.gz, and extracted it.
Then I ran the following sequence, per the quickstart guide:
./configure --disable-gcc-warnings
sudo make
sudo make install

All went well up to this point. Then I tried to run:
sudo ./torque.setup myuser

and got this:
initializing TORQUE (admin: myuser at localhost)
pbs_server: error while loading shared libraries: libtorque.so.2: cannot
open shared object file: No such file or directory
qmgr: error while loading shared libraries: libtorque.so.2: cannot open
shared object file: No such file or directory
ERROR: cannot set TORQUE admins
qterm: error while loading shared libraries: libtorque.so.2: cannot open
shared object file: No such file or directory


============
answer:


By default Ubuntu doesn't include /usr/local/lib in the list of
directories to search for dynamic-linked libraries.  So, the best
approach is to add that path to the end of /etc/ld.so.conf, and run
"ldconfig" to update.  Then try your "torque.setup" again.


============

my /etc/ld.so.conf file wound up being:


include /etc/ld.so.conf.d/*.conf
include /usr/local/lib

---

### Post by moritzhoefert on 2010-06-25
Hello,

I installed torque on my 'mini cluster' consisting of two machines: sambstor.che.wisc.edu with 2 processors and gordon.che.wisc.edu with one processor. Gordon is mom and server and sambstor is just mom. I can submit jobs to the queue but they always remain in the state Q and  never run. Did anyone have similar problems? Is my configuration wrong?
I always start pbs/torque with 
```

qterm
pbs_server
pbs_sched

```

The computers 'talk' to each other successfully:
```

root@gordon:/var/spool/torque/server_priv# pbsnodes
gordon.che.wisc.edu
     state = free
     np = 1
     ntype = cluster
     status = opsys=linux,uname=Linux gordon 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686,sessions=1382 1386 1387 1430 1448 27586 28676 28776 28858,nsessions=9,nusers=3,idletime=95,totmem=2719692kb,availmem=2619952kb,physmem=1024876kb,ncpus=1,loadave=0.02,netload=3201318378,state=free,jobs=,varattr=,rectime=1277484721

sambstor.che.wisc.edu
     state = free
     np = 2
     ntype = cluster
     status = opsys=linux,uname=Linux sambstor.che.wisc.edu 2.6.24-27-generic #1 SMP Fri Mar 12 01:10:31 UTC 2010 i686,sessions=5097 13098 28536 5611 14652 14734 14739 14743 14768 14779 14803 14806 15085 15071 16022 16109,nsessions=16,nusers=4,idletime=67974,totmem=4061992kb,availmem=3720692kb,physmem=1033780kb,ncpus=2,loadave=5.07,netload=2823186465,state=free,jobs=,varattr=,rectime=1277484764

```Here are some of my configurations:
```

root@gordon:/var/spool/torque/server_priv# cat nodes 
gordon.che.wisc.edu np=1
sambstor.che.wisc.edu np=2
torque/server_priv# qmgr
Max open servers: 4
Qmgr: p s
#
# Create queues and set their attributes.
#
#
# Create and define queue standard
#
create queue standard
#
# Create and define queue medium
#
create queue medium
set queue medium queue_type = Execution
set queue medium Priority = 1000
set queue medium max_running = 10
set queue medium resources_max.walltime = 50:00:00
set queue medium resources_default.walltime = 00:30:00
set queue medium enabled = True
set queue medium started = True
#
# Set server attributes.
#
set server acl_hosts = gordon
set server log_events = 511
set server mail_from = adm
set server scheduler_iteration = 600
set server node_check_rate = 150
set server tcp_timeout = 6
set server submit_hosts = gordon.che.wisc.edu
set server next_job_number = 24
root@gordon:/var/spool/torque# cat mom_priv/
config    jobs/     mom.lock  
root@gordon:/var/spool/torque# cat mom_priv/config 
$pbsserver      gordon.che.wisc.edu    
$clienthost     gordon.che.wisc.edu
$logevent       255 
$cputmult       1.0
$wallmult       1.0
$max_load       1.0
$ideal_load     1.0
$restricted     *.che.wisc.edu
root@gordon:/var/spool/torque# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    gordon
.... more stuff ....

menduser@sambstor:~$ sudo cat /var/spool/torque/mom_priv/config
[sudo] password for menduser: 
$pbsserver      gordon.che.wisc.edu
$logevent       255 


```

---

### Post by kbiswas on 2011-11-21
Did anybody have the problem and figure out hot to solve the issue of job stuck in queue? I have installed torqueue 2.5.5 with mostly default settings. I am using pbs_sched. The pbs_server seems to run OK and sees the nodes and assigns them as free. After submitting a job, it stays in queue and does not run. The server_logs file says the job has been submitted by user. But the sched_logs does not say anything about any job! I guess somehow there is no communication between the scheduler and the server. And I cannot figure out how to solve this! qstat -f, pbsserverdb, qmgr -c "p s" commands does not show anything unusual. 
Thanks!

---

### Post by kbiswas on 2011-11-21
OK, using Torque 2.5.5, problem with job stuck in queue when everything else seemed to be working OK - in my case turned out to be that the pbs_server was set to Idle. Check qmgr -c "list server". Once the server status is turned to true, that is scheduling, then it starts interacting with the pbs scheduler and the jobs in queue start running. I don't know whether I inadvertantly set the server to Idle status or that is the default after installation.

---

