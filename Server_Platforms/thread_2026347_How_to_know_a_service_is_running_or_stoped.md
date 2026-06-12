---
title: "How to know a service is running or stoped"
date: 2012-07-14
forum: Server Platforms
---

### Post by Howtouse on 2012-07-14
Hi all, 

How to know a service is running or stoped by command line

ex: 
```

doing some thing to get a avalue of service, return ?
if (? -eq 0 )
echo "service is running"
else 
echo "service is stoped"
fi

```Many thanks for your help !

---

### Post by sandyd on 2012-07-14
> **Howtouse said:**
> Hi all, 

How to know a service is running or stoped by command line

ex: 
```

doing some thing to get a avalue of service, return ?
if (? -eq 0 )
echo "service is running"
else 
echo "service is stoped"
fi

```Many thanks for your help !
Something like
```

sudo service nginx status
 * nginx is running

```

---

### Post by Howtouse on 2012-07-15
> **sandyd said:**
> Something like
```

sudo service nginx status
 * nginx is running

```
Thanks !
but that's not my mean

```

sudo service nginx status --> how to return a value. from this value. we will know this service is running or stoped

```

---

### Post by BkkBonanza on 2012-07-15
Do you actually mean a service or just any process? Do you need to check a specific one running or any instance running with a given name of command/service?

Typically what is often done is when the service or process is started it's pid is put in a known location such as /var/run/mypid

Then that file (mypid) can be used to check if the process is still running using the ps command. If you need to locate it by name and not pid then pgrep can be used in a comparison expression.

if [ "`pgrep myappname`" == "" ]; then
 echo "not running"
else
 echo "still running"
fi

Also the $? variable can check exit status of last command and could be useful for seeing if pgrep found any process.

Also, pgrep has a lot of searching power so you can give it more specific criteria than just the name.

---

### Post by Howtouse on 2012-07-15
Many thanks [[COLOR=#DD4814]**BkkBonanza**[/COLOR]]("http://ubuntuforums.org/member.php?u=550406")
I did like you guide but the result didn't ok

to view status of all services i can use command: service --status-all
```

nh@ubuntu:~$ service --status-all
 [ + ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ - ]  grub-common
 [ - ]  kerneloops
 [ + ]  pulseaudio
 [ - ]  rsync
 [ ? ]  rsyslog
 [ + ]  ssh
 [ + ]  saned
 [ - ]  stop-bootlogd
 [ - ]  stop-bootlogd-single
 [ ? ]  sudo
 [ - ]  urandom
and more...

```
```
status mean
"+" started
 "-" stopped
 "?"  unknown
```

tested with bluetooth service
```
if [ "`pgrep bluetooth`" == "" ]; then
echo "not running"
else
echo "still running"
fi
```
output: still running

tested with ssh service
```
if [ "`pgrep ssh`" == "" ]; then
echo "not running"
else
echo "still running"
fi
```
output: still running

tested with saned service
```
if [ "`pgrep saned`" == "" ]; then
 echo "not running"
 else
 echo "still running"
 fi
```
 output: not running

Why status of services: bluetooch, ssh, saned are "+" but output different

---

### Post by Howtouse on 2012-07-15
Could you give me some example:
Write a script on ubuntu to check a service is running or stoped

---

### Post by koenn on 2012-07-15
you don't *need* a script to do that, there are standard commands to tell you that : 
```

:~$ status dbus
dbus start/running, process 1134

:~$ service dbus status
dbus start/running, process 1134

```

but if you absolutely want to reinvent that wheel, you could do something like
```

if ps -e |grep xxxxxxx > /dev/null; 
then echo running; 
else echo "not running"; 
fi

not running



if ps -e |grep cupsd > /dev/null; 
then echo running; 
else echo "not running";
fi

running


```

---

### Post by BkkBonanza on 2012-07-15
The pgrep command will search for a running process. You have to give it the name of the process. eg. for ssh service the process is named sshd not ssh. It's likely the same for others as linux devs typically name a daemon (service) with a d on the end. To get the name of the process just use the "ps afx" to see everything running and make note of the actual name you need.

(note above that ssh is a common process and that pgrep will detect ssh running when it's sshd you want that may not be running - ssh is the client and sshd the server (daemon/service))

As noted by koenn above if the status command will give you what you want then you may be better off using that and testing it's output. The approach I gave you is more general and will work for any process - not just one managed by Upstart. Also, I find the status command gives misleading results and often reports "unknown job" in cases where a service exists.

eg.

if [ "`status ssh | grep -c running`" == "1" ]; then
  echo "Running"
fi

---

