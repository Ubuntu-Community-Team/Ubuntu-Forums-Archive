---
title: "High hard disk usage when the server isn't even being used."
date: 2008-11-15
forum: Server Platforms
---

### Post by linuxisevolution on 2008-11-15
I have a Pentium 3 550mhz 128mb ram server setup, that has been working well for quite a while, until now. The load average is very low:


> debian:~# uptime
 20:34:31 up 14 days, 20:18,  1 user,  load average: 0.00, 0.04, 0.01
debian:~# 

The server is running Debian 4, but I like this forum better :)

At about 10:30 at night, the hdd started to whirl up and grind away with the bright yellow light keeping me awake. I looked at my router and switch, but there was no network activity. It does this at around 10:30 at night, every night, and it drives me crazy not being able to figure this out. The server is hosting two sites.

[http://www.thelinuxhowto.co.nr]("http://www.thelinuxhowto.co.nr")

and

[http://www.winrid.co.nr]("http://www.winrid.co.nr")

Here is the filesystem usage according to munin:

[http://www.winrid.co.nr/munin]("http://www.winrid.co.nr/munin")

Could someone please explain this? Thanks!

---

### Post by linuxisevolution on 2008-11-15
Here is top:



> debian:~# top

top - 20:41:39 up 14 days, 20:25,  1 user,  load average: 0.04, 0.07, 0.02
Tasks:  77 total,   1 running,  76 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    127028k total,   116076k used,    10952k free,     8496k buffers
Swap:   176672k total,     3068k used,   173604k free,    68548k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      15   0  1940  644  552 S  0.0  0.5   0:03.09 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.09 ksoftirqd/0        
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.32 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   61 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   97 root      10  -5     0    0    0 S  0.0  0.0   0:07.90 kswapd0            
   98 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
  564 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khubd              
  871 root      10  -5     0    0    0 S  0.0  0.0   0:28.88 kjournald          
 1048 root      20  -4  2692  440  340 S  0.0  0.3   0:00.40 udevd              
 1329 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused          
 1528 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kmirrord           
 1759 daemon    15   0  1680  464  380 S  0.0  0.4   0:00.01 portmap            
debian:~# 



---

### Post by iponeverything on 2008-11-15
sounds like you have a cron job that is kicking off at the same time every night. 

take a peak in /var/log for clues.

---

### Post by linuxisevolution on 2008-11-15
> **iponeverything said:**
> sounds like you have a cron job that is kicking off at the same time every night. 

take a peak in /var/log for clues.

I never setup a cron job ( that name made me laugh... ), but for forms sake I hope a haxor didn't. I did nano /var/log and nothing was in the file. I did find /var/log , found all the log files, and found nothing "cron" related. What else could this be? Lets say it's not at the exact same time ( because it isn't, its AROUND the same time ), what would cause this?:confused:

---

### Post by Philio on 2008-11-16
It certainly sounds like it's something that's running regularly at that time. You can check your cron tasks with crontab -l.

It's likely that as you have low RAM in your machine that it is swapping a lot, this could cause heavy disk usage if something is running that eats up all available RAM.

If you have heavy swap usage you will likely see kswapd high up on the list in top.

---

### Post by linuxisevolution on 2008-11-16
> **Philio said:**
> It certainly sounds like it's something that's running regularly at that time. You can check your cron tasks with crontab -l.

It's likely that as you have low RAM in your machine that it is swapping a lot, this could cause heavy disk usage if something is running that eats up all available RAM.

If you have heavy swap usage you will likely see kswapd high up on the list in top.

Thanks. "No crontab for root." So thats not it. Top shows kswapd accessing the hard disk for 10+ minutes, so I'll buy a 128mb stick of ram off of newegg. Does apache2 really need that much memory? I have about 500 page views.

---

### Post by Thirtysixway on 2008-11-16
If apache is using too much ram, you could look at using an alternate http server such as lighttpd.

---

### Post by linuxisevolution on 2008-11-16
> **Thirtysixway said:**
> If apache is using too much ram, you could look at using an alternate http server such as lighttpd.

I already have apache2 setup... I'll just get more ram.

---

### Post by Philio on 2008-11-16
Well from what I remember I think the very basic Ubuntu server with just SSH running and the default stuff uses close to 100Mb RAM.

Apache by default spawns quite a few processes which will use a few Mb each, if your serving PHP pages these processes can increase to 15Mb+ in size, easily filling up what little remaining RAM there probably is anyway.

Have a look at the output of free and see how much RAM is free/how much swap is being used.

If your getting 500 hits you could prehaps change the Apache config to only use 2 or 3 child processes.

---

### Post by linuxisevolution on 2008-11-16
> **Philio said:**
> Well from what I remember I think the very basic Ubuntu server with just SSH running and the default stuff uses close to 100Mb RAM.

Apache by default spawns quite a few processes which will use a few Mb each, if your serving PHP pages these processes can increase to 15Mb+ in size, easily filling up what little remaining RAM there probably is anyway.

Have a look at the output of free and see how much RAM is free/how much swap is being used.

If your getting 500 hits you could prehaps change the Apache config to only use 2 or 3 child processes.

Will changing the child processes slow down the server? If I never changed that, how many processes is it using now?

---

### Post by djamu on 2008-11-16
Hi

**disk grinding at daily intervals:**

updatedb -used by locate & slocate- indexes your system -except your pruned paths and FS's- everyday 
> that is all files that changed, quite similar  to windoze & osx file indexing 

it's a default setting in debian ( and so also in ubuntu )
settings:
```
/etc/updatedb.conf
```

the cron job is in cron.daily > and so runs daily at a fixed time.
```
/etc/cron.daily/mlocate
```


**regarding apache:**

you most likely installed apache2 prefork

if it's serving dynamic pages ( php & the likes )
then each process ( depending on loaded apache modules ) is 15-32MB ( with me it's about 30MB on average )

if it's static pages then only a couple of MB are needed.


apache2 has a bad default setting ( big iron ) that spawns a couple of processes and keeps a couple in reserve.

**following is important**

the default **MaxClients=150** setting..  **when busy** it will keep spawning processes until this maximum is reached ... in other words if your serving dynamic pages and have a busy server > worst case scenario is that apache will use 150x32MB = 4.8GB....

you can test this by refreshing a page it serves very fast ( tap the F5 key very fast for a minute )... your server will almost certainly die/ lock up in front you ....

a good reasonable setting for the couple of hundred pages your serving daily is

```
sudo vim /etc/apache2/apache2.conf
```

and look for following

```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
```

a little lower you have the settings for the apache worker module .. just ignore those ( they're there for SMP machines with apache2 worker installed, full explanation of this is a little of topic )


I suggest changing previous into something like this... ( a save setting I use on low memory machines ).

```
<IfModule mpm_prefork_module>
    StartServers          2
    MinSpareServers       2
    MaxSpareServers      4
    MaxClients          6
    MaxRequestsPerChild   1000
</IfModule>
```

now apache will spawn maximum 6 processes > worst case 6*32MB= 192MB ... if you don't use MYSQL then 256MB ram will just do....

a little bit above that you have the KeepAliveTimeout parameter, change it to 

```
KeepAliveTimeout 2
```

with 
```
KeepAlive On
```


bye...
:popcorn:

---

### Post by linuxisevolution on 2008-11-16
The maxclients thing on my server must be okay, because I went to my site and refreshed it 100 times at once, no hiccups at all lol. Thanks.

---

### Post by djamu on 2008-11-16
well I do suggest or rather urge you to match the maxclients to the available ram ... just in case some idiot runs a script fetching lots of pages / spawning lots of instances .... pretty easy to do 
( most basic DOS attack you can imagine )....

just a good advice

---

### Post by linuxisevolution on 2008-11-16
> **djamu said:**
> well I do suggest or rather urge you to match the maxclients to the available ram ... just in case some idiot runs a script fetching lots of pages / spawning lots of instances .... pretty easy to do 
( most basic DOS attack you can imagine )....

just a good advice

Well I think my largest page is 1mb, so spawning lots of pages wont do much... Besides, I watch my network constantly, so I will notice and block the ip. 


BTW: DOS was awesome. :guitar:

---

