---
title: "How to Torque on ubuntu 10.04 on a single multicore machine"
date: 2010-06-17
forum: Server Platforms
---

### Post by jouke.postma on 2010-06-17
I updated this on jul 21 using comments below

Torque is a batch job queuing system that is used on clusters. But I find it handy to use it on my multi-core workstation as well. It allows jobs that need to be run to be schedule by multiple users. The scheduler will make sure that not too many jobs are run simultaneously which could cause high system loads or memory issues. 

I previously posted [how to install torque on ubuntu hardy]("http://ohioloco.ubuntuforums.org/showthread.php?t=1372508") from the torque source package. However, torque is now in the repositories of lucid and here are the steps that I had to take to get it to work on my workstation. 

For this setup I kept the server host name 'torqueserver' which is the default in the package. You can do the same or use a fully qualified domain name. In that case, you will have to adept the steps somewhat. 

My workstation has 8 cores, and I only want to give 6 of them to the que. Please adapt  your numbers accordingly. 


0) open root terminal
```
sudo -s
```

1) add torqueserver as an alias to /etc/hosts. 
```
gedit /etc/hosts
change 127.0.1.1	myHostName to 127.0.1.1	myHostName torqueserver
```
*) see post by drlemon. Alternatively use a resolvable host name (check with 'host $HOSTNAME') in the file: /var/lib/torque/server_name and whereever torqueserver is used below, use that host name


2) install torque from repositories 
```
apt-get install torque*
```

3) stop torque
```
qterm
```

4) check torque is not running (otherwise you can kill it)
```
ps aux | grep pbs
```

5) create missing directory 
```
mkdir /var/lib/torque/server_priv/arrays
```

6) add torqueserver as serverhost
```
echo "SERVERHOST localhost" >> /var/lib/torque/torque.cfg
```

7)setup nodes:
```
echo "torqueserver np=8" >> /var/lib/torque/server_priv/nodes
echo "pbs_server = 127.0.1.1" >> /var/lib/torque/mom_priv/config
```

8) setup database
```
pbs_server -t create
```

9) create que and set server settings in database
```
qmgr torqueserver
create queue batch
set queue batch queue_type = Execution
set queue batch max_running = 6
set queue batch resources_max.ncpus = 8
set queue batch resources_max.nodes = 1
set queue batch resources_default.ncpus = 1
set queue batch resources_default.neednodes = 1:ppn=1
set queue batch resources_default.walltime = 24:00:00
set queue batch max_user_run = 6
set queue batch enabled = True
set queue batch started = True
set server default_queue = batch
set server scheduling = True

exit
```

10) restart server and scheduler and node server
```
qterm
pbs_server
pbs_sched #this will give some warning about missing files
pbs_mom
```

11) check that the nodes are up
```
pbsnodes -a
```

12) exit the root terminal and as a normal user test the que
```
exit
qstat -q
echo "sleep 30" | qsub
qstat
```

13) see drlemon: do a gedit /etc/init.d/torque* and change in all three files the pidfile= line so that it points to /var/lib instead of /var/spool. Additionally remove the -t create from the server options in the torque-server file. 

This works for me but probably requires more configuration in a demanding computing environment. Check out the torque website for more queue configurations, user management etc.

---

### Post by drlemon on 2010-07-08
Thank you, jouke.postma !  In case someone else needs to repeat it, here is my experience with your instructions.

Messing with my /etc/hosts file somehow made me lose internet connection, but I was able to set up torque with the existing hostname. An extra issue that I found is that the file /var/lib/torque/server_name may need to be edited if you end up changing the name of the host.

The contents of my working mom_priv/config file are slightly different (per torque documentation):
```

drlemon@lynx-desktop:~$ cat /var/lib/torque/mom_priv/config 
$pbsserver lynx-desktop
$logevent 255

```

And there was yet another surprise: the init daemons /etc/init.d/torque-* were all pointing to resources in /var/spool/torque (the default installation directory in the torque tar ball) instead of /var/lib/torque (which is where the package in Lucid installed it), and I had to go in and manually edit the paths to make them work. This bug has already been reported [https://bugs.launchpad.net/ubuntu/+source/torque/+bug/360827]("https://bugs.launchpad.net/ubuntu/+source/torque/+bug/360827") , and the developers said it should be fixed in the next Ubuntu (Meerkat), which will have torque 2.4.

---

### Post by PaulPrice on 2010-10-21
Thank you for this very helpful guide to getting started!
However, following the queue setup exactly in the 'qmgr' stage, I could only ever run a single job at a time on my multi-core machine.  A simpler setup allowed multiple jobs to run at once:

```

$ qmgr
Max open servers: 4
Qmgr: list queue batch
Queue batch
    queue_type = Execution
    total_jobs = 0
    state_count = Transit:0 Queued:0 Held:0 Waiting:0 Running:0 Exiting:0 
    max_running = 6
    resources_max.ncpus = 8
    resources_default.ncpus = 1
    mtime = Thu Oct 21 18:35:37 2010
    resources_assigned.ncpus = 0
    resources_assigned.nodect = 0
    enabled = True
    started = True

```I therefore advise executing a few of the above 'set queue batch <blah>' commands in the qmgr, choosing them carefully.  resources_default.ncpus=1 seems to be important.

---

### Post by Tchova on 2011-06-17
Dear all
I have a brand new installation of torque 2.4.8, I am  currently testing torque and maui for my main cluster. My boss did not  let me test it on the actual cluster, so I used a simple linux box, and  installated talk server and talk client on both, I have installed the  latest snapshot version of maui. maui and torque can talk perfectly, as i  can see maui can identify the resources when i do showq 
ACTIVE JOBS--------------------
JOBNAME            USERNAME      STATE  PROC   REMAINING            STARTTIME


     0 Active Jobs       0 of    2 Processors Active (0.00%)
                         0 of    1 Nodes Active      (0.00%)

IDLE JOBS----------------------
JOBNAME            USERNAME      STATE  PROC     WCLIMIT            QUEUETIME


0 Idle Jobs

BLOCKED JOBS----------------
JOBNAME            USERNAME      STATE  PROC     WCLIMIT            QUEUETIME


But all jobs that I submit i do not get the output and error files, and when i do a tracejob I get the following
:
06/16/2011 19:13:45  S    enqueuing into batch, state 1 hop 1
06/16/2011 19:13:45  S    Job Queued at request of milton@milton-desktop, owner = milton@milton-desktop, job name =
                          ExampleJob, queue = batch
06/16/2011 19:13:45  S    Job Modified at request of Scheduler@milton-desktop
06/16/2011 19:13:45  S    Email 'b' to [EMAIL="milton@cs.wits.ac.za"]milton@cs.wits.ac.za[/EMAIL]  failed: Child process '/usr/sbin/sendmail -f
                          [EMAIL="milton@cs.wits.ac.za"]milton@cs.wits.ac.za[/EMAIL] [EMAIL="milton@cs.wits.ac.za"]milton@cs.wits.ac.za[/EMAIL] ' returned 127 (errno 10:No child processes)
06/16/2011 19:13:45  L    Job Run
06/16/2011 19:13:45  S    Job Run at request of Scheduler@milton-desktop
06/16/2011 19:13:45  S    Reject reply code=15001(Unknown Job Id), aux=0, type=JobObituary, from pbs_mom@milton-desktop
06/16/2011 19:13:45  M    job was terminated
06/16/2011 19:13:45  M    obit sent to server
06/16/2011 19:13:45  A    queue=batch
06/16/2011 19:13:45  M    scan_for_terminated: job 52.milton-desktop task 1 terminated, sid=29831
06/16/2011 19:13:45  M    server rejected job obit - 15001
06/16/2011 19:13:45  A    user=milton group=milton jobname=ExampleJob queue=batch ctime=1308244425 qtime=1308244425
                          etime=1308244425 start=1308244425 owner=milton@milton-desktop exec_host=torqueserver/0
                          Resource_List.ncpus=1 Resource_List.neednodes=1 Resource_List.nodect=1 Resource_List.nodes=1
                          Resource_List.walltime=00:01:00
06/16/2011 19:14:22  A    06/16/2011 19:14:22  S    dequeuing from batch, state EXITING
06/16/2011 19:14:22  S    Email 'a' to [EMAIL="milton@cs.wits.ac.za"]milton@cs.wits.ac.za[/EMAIL]  failed: Child process '/usr/sbin/sendmail -f
                          [EMAIL="milton@cs.wits.ac.za"]milton@cs.wits.ac.za[/EMAIL] [EMAIL="milton@cs.wits.ac.za"]milton@cs.wits.ac.za[/EMAIL] ' returned 127 (errno 10:No child processes)


I googled everything about the error and could not find a  solution. That happen to everyjob I submit, I really appreciate if any  of you could help me with that.
Thank you very much
Milton Lauxande

---

### Post by RMKrug on 2012-02-15
Nice post - but I don't manage to get it to work under Oneiric. Is there anything which is missing ion your post here? It sems that the config in /var/lib/torque/ is not picked up by torque:

pbsnodes -a
pbsnodes: Server has no node list MSG=node list is empty - check 'server_priv/nodes' file

after going thropugh yout howto.

Rainer

---

### Post by GenericPlayer on 2012-03-04
I can't get it to work on 11.10 either. qterm returns the error "qterm: Unauthorized request". In addition the package is installed to /var/spool/torque instead of /var/lib but its not like I got far along enough for that to be an issue.

---

### Post by braingram on 2012-03-27
I added a reply to this post that might be useful in sorting out the "Unauthorized request" issue:

[http://ubuntuforums.org/showthread.php?p=11797874#post11797874](http://ubuntuforums.org/showthread.php?p=11797874#post11797874)

In short, make sure /etc/torque/server_name is the same as /etc/hostname

---

### Post by yapatel on 2012-05-10
I'm not sure if that's completely true;

The [resources_default.ncpus=1] command is setting the default resources for any job submitted to the queue.

The [max_running = 6] command sets the number of jobs allowed to run simultaneously in the queue.

If you want a user to be able to run multiple simultaneous jobs, you need to set the previous command and have [max_user_run = #] set.

This should let you run submit and simultaneously run multiple jobs.

> **PaulPrice said:**
> Thank you for this very helpful guide to getting started!
However, following the queue setup exactly in the 'qmgr' stage, I could only ever run a single job at a time on my multi-core machine.  A simpler setup allowed multiple jobs to run at once:

```

$ qmgr
Max open servers: 4
Qmgr: list queue batch
Queue batch
    queue_type = Execution
    total_jobs = 0
    state_count = Transit:0 Queued:0 Held:0 Waiting:0 Running:0 Exiting:0 
    max_running = 6
    resources_max.ncpus = 8
    resources_default.ncpus = 1
    mtime = Thu Oct 21 18:35:37 2010
    resources_assigned.ncpus = 0
    resources_assigned.nodect = 0
    enabled = True
    started = True

```I therefore advise executing a few of the above 'set queue batch <blah>' commands in the qmgr, choosing them carefully.  resources_default.ncpus=1 seems to be important.

---

### Post by yapatel on 2012-05-13
Your tutorial is great - really helped get things going.

Can I configure an up-and-running installation of torque/pbs to send email notifications or do I have to uninstall it all (via aptitude) and install it from their tar ball?

---

