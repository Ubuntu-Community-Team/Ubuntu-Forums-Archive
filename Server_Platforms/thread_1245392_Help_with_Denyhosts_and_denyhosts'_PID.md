---
title: "Help with Denyhosts and denyhosts' PID"
date: 2009-08-20
forum: Server Platforms
---

### Post by jonny.milano on 2009-08-20
Hello! I am trying to setup denyhosts on my server. I had thought that I had it all configured correctly yet when I go to check on it I get:
```

herb@herb:/var/run$ sudo /etc/init.d/denyhosts status
Denyhosts is not running

```
OK, it&#8217;s not running so I&#8217;ll do:
```

sudo /etc/init.d/denyhosts start   

```
and get:
```

starting DenyHosts:    /usr/bin/env python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg

DenyHosts could not obtain lock (pid: 10911) [Errno 17] File exists: '/var/run/denyhosts.pid'

```
Uh... didn&#8217;t the shell just say that it wasn&#8217;t running? I am confused. So I go and I delete the .pid file and try to restart denyhosts. Denyhosts didn&#8217;t like that. I recreate the .pid file with the same PID in it, got the same error. Then I change the PID in the .pid file, still no dice. Then I try and killall the process and get:
```

10911: no process killed

```

Bummer. Can someone help me out with this?? &#61514;

---

### Post by jonny.milano on 2009-08-27
can anyone please help??? pretty please...?

---

### Post by tribaldata on 2009-08-27
Jonny, did you remove the pid file using sudo or your user ?

Also if you do a : ps aux | grep deny
Do you get any denyhost daemon ?

---

### Post by jocampo on 2009-08-27
Check the process and confirm if such process is dead for sure

```

ps -fe | grep -i [d]eny

```

did you get something? if you do, kill it...

```

sudo kill -9 PID

```

where PID is the deny_host process

---

### Post by tribaldata on 2009-08-27
My guess is that your system crashed or denyhosts was otherwise terminated abnormally, this will result in a leftover pid file which will effectively stop denyhosts from starting.

To check this you would do something like:

```
cat /var/run/denyhosts.pid
```

This will tell you whether there is a value in that field. If there is a value there then do:

```
ps aux | grep deny
```

Does anything show up besides 'grep deny'?

If no, then do:

```
sudo rm /var/run/denyhosts.pid
```

Then start the daemon
```
sudo /etc/init.d/denyhosts start

```

If all work normally that should start your daemon.

Hope this help.:)

---

### Post by jonny.milano on 2009-08-28
Hey Tribaldata,

Thanks so much for your help! I followed your instructions like this:
```

herb@herb:~$ sudo cat /var/run/denyhosts.pid
[sudo] password for herb: 
12972
herb@herb:~$ sudo ps aux | grep deny
herb     10731  0.0  0.0   3004   760 pts/0    S+   08:03   0:00 grep deny
root     12972  0.0  0.4   8160  4764 ?        S    Aug24   0:03 python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
herb@herb:~$

```

..but I'm not sure where to go from here. Do you think that you could help me out? I promise to give back to the ubuntu forums once I actually know what I am doing! 

Thanks,
Jonny

---

### Post by jonny.milano on 2009-08-28
Hey jocampo,

I tried following your instructions but here is what I get:
```

herb@herb:~$ ps -fe | grep -i [d]eny
root     12972     1  0 Aug24 ?        00:00:03 python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
herb@herb:~$ sudo kill -9 12972
herb@herb:~$ sudo /etc/init.d/denyhosts status
Denyhosts is not running
herb@herb:~$ sudo /etc/init.d/denyhosts start
starting DenyHosts:    /usr/bin/env python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
DenyHosts could not obtain lock (pid: 12972)
[Errno 17] File exists: '/var/run/denyhosts.pid'
herb@herb:~$

```
??? What gives?? I thought that I just killed the denyhosts process???! Very strange. Does this make sense to you?

Thanks for the help!
Jonny

---

### Post by tribaldata on 2009-08-28
Hi Jonny, 

Sorry if i was unclear in my previous message.

The cat command will give you the pid of the process of DenyHosts, now you need to kill this pid and then restart it

So here what you do, 

Take the ```
sudo cat /var/run/denyhosts.pid
```
Then that will give you a number example : 2447
Use that number on this command 
```
sudo kill 2447
``` Replace the number for the one the cat command gave you.

Then try starting it again with this command
```
sudo /etc/init.d/denyhosts start
```

If it's telling you that there is a lock file do this command
```
sudo rm /var/run/denyhosts.pid
```

Then retry your start command
```
sudo /etc/init.d/denyhosts start
```

Hope this help.

---

