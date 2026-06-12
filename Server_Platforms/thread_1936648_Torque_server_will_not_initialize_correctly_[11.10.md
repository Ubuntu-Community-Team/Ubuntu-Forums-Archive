---
title: "Torque server will not initialize correctly [11.10]"
date: 2012-03-06
forum: Server Platforms
---

### Post by GenericPlayer on 2012-03-06
Hello,

I have been trying for 3 days now to get Torque server working on my installation of Ubuntu 11.10.

At first I went for the ease of the Ubuntu Software Center. Once installation is complete, it starts the server process on its own without adding root as a server manager. If I try to terminate the server using qterm or add root as a manager using qmgr I always get an "Unauthorized Request" error. 

I removed the installation and then tried again using "apt-get install torque-server" in a root csh shell. The same problem appears again. My reading of the Admin guide on the Adaptive Computing website states that after installation the server is started using the torque.setup command in which the server manager is specified. It seems in my situation that torque.setup  is put away in /usr/share/doc/torque/ and cannot be executed because the server is running right after installation. I tried killing the server process but that did not help either. I checked the serverdb file in /var/spool/torque/server_priv and it was empty.

Is there something I can do to make torque usable from a software center or apt-get installation, or will I have to download the source files and compile them? I have the desktop version of Ubuntu installed instead of the server version because I had to use the alternate install CD. Is that what is causing my problem?

---

### Post by braingram on 2012-03-27
I've also been working on this. The problem I was running into was I was trying to set /etc/torque/server_name to something other than /etc/hostname

Maybe try these steps (for a single machine setup):
1) install torque:
sudo apt-get install torque-server torque-scheduler torque-client torque-mom

2) stop/kill torque:
sudo /etc/init.d/torque-scheduler stop
sudo /etc/init.d/torque-mom stop
sudo /etc/init.d/torque-server stop

3) double check that things stopped (the scheduler might have an invalid pid file):
sudo killall pbs_sched

4) fix the scheduler pid file. change line 20 of /etc/init.d/torque-scheduler to:
PIDFILE=/var/spool/torque/sched_priv/sched.lock

5) set /etc/torque/server_name to whatever is returned by hostname:
cat /etc/hostname | sudo tee /etc/torque/server_name

6) configure the server for your user:
sudo sh /usr/share/doc/torque-common/torque.setup $USER

7) kill the newly configured server:
sudo qterm

8) add your node to the server:
echo "$HOSTNAME np=`cat /proc/cpuinfo | grep processor | wc -l`" | sudo tee /var/spool/torque/server_priv/nodes

9) configure the node/mom:
echo "\$pbsserver $HOSTNAME" | sudo tee /var/spool/torque/mom_priv/config

10) start everything up:
sudo /etc/init.d/torque-server start
sudo /etc/init.d/torque-mom start
sudo /etc/init.d/torque-scheduler start

11) see if nodes are available:
qnodes -a

-----

If you run into issues, make sure your hosts file is correct. Check "gethostip $HOSTNAME" returns something sensible.

---

### Post by lorubenet on 2012-04-16
Hi guys, 

thanks for the help!!

I tried what's described below but I still got the "Unauthorized Request" error. 
Searching through many posts I got finally to the right spot:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=629596](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=629596)

Bottom line: set your /etc/hosts such that your hostname (i.e. what comes out of /etc/hostname) has 127.0.0.1 ip and not the Ubuntu's default 127.0.1.1. 
That made the whole thing work nicely (well I still have to try to submit a job... ). 

Another thing I did along the way was to allow paswordless ssh to the localhost. I'm not sure if that is needed or not.

---

### Post by Agilar on 2012-08-20
I've managed to start pbs_server and pbs_mom but starting scheduler gives:

/etc/init.d/torque-scheduler start
 * Starting Torque scheduler:                                                                                                            pbs_sched: LOG_ERROR::Cannot assign requested address (99) in main, bind

google reveals that that the problem lies in the incorrect interface:'

netstat -rn

but it says nothing on how to solve it.

---

### Post by drmookie on 2012-09-29
I've been wrestling with this for the last few days, but seem to have nailed it now. Perhaps it is a bit of a fudge, but I have set my IP address statically, then altered my /etc/hosts accordingly so that it now reads:

127.0.0.1   localhost
<ip address>   <hostname>   torqueserver

Depending on where you are setting up, I know fixed IP addresses may not be an option, but if it is, this has done the trick for me. Otherwise, I just followed

[B][http://ubuntuforums.org/showthread.php?t=1512061](http://ubuntuforums.org/showthread.php?t=1512061)

[/B]Hope this helps and perhaps restores some sanity (although in my case I think it is too late...)!

---

