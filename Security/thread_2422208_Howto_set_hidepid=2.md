---
title: "Howto set hidepid=2"
date: 2019-07-03
forum: Security
---

### Post by mauzaritta3 on 2019-07-03
Hello,

I use ubuntu 18.04 LTS Server.

For security reasons I would like to set the option for proc to hidepid=2 in order to hide unnecessary information to a user. 
Unfortunately the /etc/fstab in Ubuntu 18.04 does not contains proc line. However added the following line to our system /etc/fstab.

```
proc            /proc           proc    defaults,hidepid=2   0    0
```

Unfortunately if I check /proc as normal user I am still able to see all entries from root.

Does anyone has a hint for me ?

BR Marc

---

### Post by #&amp;thj^% on 2019-07-03
See this: [https://www.cyberciti.biz/faq/linux-hide-processes-from-other-users/](https://www.cyberciti.biz/faq/linux-hide-processes-from-other-users/)
Only root can see all process and user only see their own process.

---

### Post by mauzaritta3 on 2019-07-03
Hello 1fallen,

thank you for your reply. 

This is exactly the website where I saw the entry I used to check the hidepid option.

Maybe I misinterpreted something but should a user see the entries from root in /proc like the following when the hidepid=2 is used ?
```
dr-xr-xr-x  60 root     root                   0 Jul  3 19:41 irq/
-r--r--r--   1 root     root                   0 Jul  3 20:15 kallsyms
-r--------   1 root     root     140737477885952 Jul  3 20:15 kcore
-r--r--r--   1 root     root                   0 Jul  3 20:15 keys
-r--r--r--   1 root     root                   0 Jul  3 20:15 key-users
-r--------   1 root     root                   0 Jul  3 19:42 kmsg

```

Furthermore even I don't use the option in /etc/fstab I am not able to see the processes when the user use the "top" command.

BR Marc

---

### Post by #&amp;thj^% on 2019-07-03
To restrict access to /proc, you use the hidepid option while mounting /proc. Add to your fstab (or edit if there's already an entry):

```
proc /proc proc defaults,hidepid=2 0 0
```
Mine:
```
cat /etc/fstab
# /dev/sda4 UUID=3056cf16-05cf-48ca-9876-78b5c416e6e5
/dev/sda4           	/         	ext4      	rw,relatime	0 1

# /dev/sda2 UUID=faf4782c-d15f-4d72-9625-9464bbd80bd2
/dev/sda2           	/boot     	ext4      	rw,relatime	0 2

# /dev/sda3 UUID=2e7f2ba4-5182-42ac-87d6-700a86bd3e2f
/dev/sda3           	none      	swap      	defaults,pri=-2	0 0
proc    /proc    proc    defaults,hidepid=2     0     0

```
[B]EDIT:The root user will still see all processes though, for debugging purposes.
[/B]
It is worth noting that with the secure values set ("1", or "2") all processes remain visible to the root user.

Not sure I fully understand your comment:"even I don't use the option in /etc/fstab"

You can use the gid option to enable access for a particular group. See [http://www.debian-administration.org/article/702/Hiding_processes_from_other_users](http://www.debian-administration.org/article/702/Hiding_processes_from_other_users) for more details.

---

### Post by mauzaritta3 on 2019-07-04
Hello 1fallen,

> Not sure I fully understand your comment:"even I don't use the option in /etc/fstab"
My fault, I meant "even I use the option in /etc/fstab I am able to see the root entries in /proc"


This is my /etc/fstab configuration:
```
user1@snxc:/proc$ cat /etc/fstab 
UUID=<my_id> / ext4 defaults 0 0
UUID=<my_id> /boot ext4 defaults 0 0
proc    /proc    proc    defaults,hidepid=2     0     0

```

But I am still able to see the following:

```
user1@snxc:/proc$ ll
total 4
dr-xr-xr-x 211 root     root                   0 Jul  4 11:34 ./
drwxr-xr-x  23 root     root                4096 Jul  3 09:45 ../
dr-xr-xr-x   9 user1   user1                 0 Jul  4 11:39 1835/
dr-xr-xr-x   9 user1   user1                 0 Jul  4 11:39 1987/
dr-xr-xr-x   9 user1   user1                 0 Jul  4 11:39 2002/
dr-xr-xr-x   2 root     root                   0 Jul  4 11:34 acpi/
-r--r--r--   1 root     root                   0 Jul  4 11:39 buddyinfo
dr-xr-xr-x   4 root     root                   0 Jul  4 11:34 bus/
-r--r--r--   1 root     root                   0 Jul  4 11:39 cgroups
-r--r--r--   1 root     root                   0 Jul  4 11:39 cmdline
-r--r--r--   1 root     root                   0 Jul  4 11:39 consoles
-r--r--r--   1 root     root                   0 Jul  4 11:39 cpuinfo
-r--r--r--   1 root     root                   0 Jul  4 11:39 crypto
-r--r--r--   1 root     root                   0 Jul  4 11:39 devices
-r--r--r--   1 root     root                   0 Jul  4 11:39 diskstats
```

So, do you really see only entries for your user and not entries for root in /proc.

BR Marc

---

### Post by #&amp;thj^% on 2019-07-04
Yes of course as seen below, **_I did remove the names off to right._**

Before:
```
ps -ef 
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 06:14 ?        
root         2     0  0 06:14 ?        
root         3     2  0 06:14 ?        
root         4     2  0 06:14 ?        
root         8     2  0 06:14 ?        
root         9     2  0 06:14 ?        
root        10     2  0 06:14 ?        
root        11     2  0 06:14 ?       
root        12     2  0 06:14 ?        
root        13     2  0 06:14 ?        
root        14     2  0 06:14 ?        
root        16     2  0 06:14 ?        
root        17     2  0 06:14 ?        
root        18     2  0 06:14 ?        
root        19     2  0 06:14 ?        
root        20     2  0 06:14 ?        
root        21     2  0 06:14 ?        
root        24     2  0 06:14 ?        
root        25     2  0 06:14 ?        
root        26     2  0 06:14 ?        
root        27     2  0 06:14 ?        
root        28     2  0 06:14 ?        
root        30     2  0 06:14 ?        
root        31     2  0 06:14 ?        
root        32     2  0 06:14 ?        
root        33     2  0 06:14 ?        
root        34     2  0 06:14 ?        
root        35     2  0 06:14 ?       
root        37     2  0 06:14 ?        
root        38     2  0 06:14 ?        
root        39     2  0 06:14 ?        
root        40     2  0 06:14 ?        
root        41     2  0 06:14 ?        
root        44     2  0 06:14 ?        
root        45     2  0 06:14 ?        
root        46     2  0 06:14 ?        
root        47     2  0 06:14 ?       
root        48     2  0 06:14 ?        
root        49     2  0 06:14 ?        
root        50     2  0 06:14 ?        
root        51     2  0 06:14 ?        
root        52     2  0 06:14 ?        
root        53     2  0 06:14 ?        
root        54     2  0 06:14 ?        
root        55     2  0 06:14 ?        
root        57     2  0 06:14 ?        
root       148     2  0 06:14 ?        
root       149     2  0 06:14 ?        
root       150     2  0 06:14 ?        
root       151     2  0 06:14 ?        
root       152     2  0 06:14 ?        
root       153     2  0 06:14 ?        
root       169     2  0 06:14 ?        
root       219     2  0 06:14 ?        
root       222     2  0 06:14 ?        
root       223     2  0 06:14 ?        
root       224     2  0 06:14 ?        
root       225     2  0 06:14 ?        
root       226     2  0 06:14 ?        
root       227     2  0 06:14 ?        
root       228     2  0 06:14 ?        
root       229     2  0 06:14 ?        
root       230     2  0 06:14 ?        
root       231     2  0 06:14 ?        
root       232     2  0 06:14 ?        
root       233     2  0 06:14 ?        
root       234     2  0 06:14 ?        
root       246     2  0 06:14 ?        
root       261     2  0 06:14 ?        
root       262     2  0 06:14 ?        
root       267     2  0 06:14 ?        
root       269     2  0 06:14 ?        
root       289     1  0 06:14 ?       
root       303     1  0 06:14 ?       
root       304     2  0 06:14 ?        
root       310     2  0 06:14 ?        
root       316     1  0 06:14 ?        
root       439     2  0 06:14 ?        
root       452     2  0 06:14 ?        
root       453     2  0 06:14 ?        
root       490     2  0 06:14 ?        
root       523     2  0 06:14 ?        
root       524     2  0 06:14 ?        
root       527     1  0 08:57 ?        
root       537     2  0 06:14 ?        
haveged    543     1  0 06:14 ?        
root       717     2  0 06:14 ?        
root       719     2  0 06:14 ?        
root       720     2  0 06:14 ?        
systemd+   721     1  0 06:14 ?        
root       722     2  0 06:14 ?        
root       724     2  0 06:14 ?       
root       725     2  0 06:14 ?        
root       796     2  0 08:10 ?        
root       970     1  0 06:14 ?        
dbus       971     1  0 06:14 ?        
root       974     1  0 06:14 ?        
root       984     1  0 06:14 ?        
privoxy    988     1  0 06:14 ?        
root       991     1  0 06:14 ?        
root       993     1  0 06:14 ?        
ntp        996     1  0 06:14 ?        
root      1120     1  0 06:14 ?        
root      1124   993  2 06:14 tty7     
root      1126     1  0 06:14 ?        
polkitd   1145     1  0 06:14 ?        
root      1186     2  0 06:14 ?        
root      1371     1  0 06:14 ?        
root      1597   993  0 06:14 ?        
me        1608     1  0 06:14 ?        
me        1609  1608  0 06:14 ?        
me        1617     1  0 06:14 ?        
me        1620  1597  0 06:14 ?        
me        1624  1608  0 06:14 ?        
me        1627  1608  0 06:14 ?        
me        1632  1608  0 06:14 ?        
me        1639  1608  0 06:14 ?        
me        1645  1639  0 06:14 ?        
me        1647  1608  0 06:14 ?        
me        1650  1608  0 06:14 ?        
me        1659  1620  0 06:14 ?        
me        1663  1620  0 06:14 ?        
me        1667  1608  0 06:14 ?        
rtkit     1675     1  0 06:14 ?        
me        1681  1620  0 06:14 ?        
root      1687     1  0 06:14 ?        
me        1688  1667  0 06:14 ?        
me        1698     1  0 06:14 ?        
me        1701  1620  0 06:14 ?        
me        1702  1620  0 06:14 ?        
me        1703  1608  0 06:14 ?        
me        1704  1620  0 06:14 ?        
me        1709  1620  0 06:14 ?        
root      1711     1  0 06:14 ?        
me        1715  1620  0 06:14 ?        
me        1720  1620  0 06:14 ?        
me        1724  1620  0 06:14 ?        
me        1727  1620  1 06:14 ?        
me        1729  1620  0 06:14 ?        
me        1734  1620  0 06:14 ?        
me        1745  1620  0 06:14 ?        
me        1759  1608  0 06:14 ?        
me        1765  1608  0 06:14 ?        
root      1768     1  0 06:14 ?        
me        1773  1608  0 06:14 ?        
me        1830  1608  0 06:14 ?        
me        1831  1727  0 06:14 ?        
root      2050     1  0 06:14 ?        
me        2056  1608  0 06:14 ?        
me        2058  1608  0 06:14 ?        
me        2060  1608  0 06:14 ?        
me        2062  1608  0 06:14 ?        
me        2064  1608  0 06:14 ?        
root      2065     1  0 06:14 ?        
me        2253     1  0 06:15 ?        
me        2344     1  0 06:15 ?        
me        2345     1  7 06:15 ?        
me        2346     1  1 06:15 ?        
root      2480     2  0 07:48 ?        
root      4814     2  0 09:00 ?        
me        4959  1627  0 06:40 ?        
root      9548     2  0 07:31 ?        
root      9562   991  6 07:31 ?        
root     10164     2  0 11:29 ?        
root     10264     2  0 07:54 ?        
root     11803     2  0 12:19 ?        
me       13484  1608  0 06:23 ?        
me       13527  1608  0 06:23 ?        
root     16675     2  0 11:58 ?        
root     17931     2  0 10:47 ?        
root     18684     2  0 12:24 ?        
root     20280     2  0 08:01 ?        
root     25033     2  0 09:15 ?        
me       25156  1663  1 12:29 ?        
me       25164 25156  0 12:29 pts/0    
root     25515     2  0 12:29 ?        
me       25890 25164  0 12:29 pts/0    00:00:00 ps -ef
root     27432     2  0 07:43 ?        
root     28427     2  0 10:30 ?        
me       29450  1627  0 06:58 ?        
me       29458  1627  0 06:58 ?        
root     30269     2  0 11:20 ?        
root     32526     2  0 08:34 ? 
```
I'm not sure your looking at this correctly, if you are the Admin of this server you will be able to see what you want to see, but the/other users will only see their processes and ID's.  
After:
```
ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
me        1505     
me        1512  1497  
me        1516  1505  
me        1519  1505  
me        1524  1505  
me        1531  1505  
me        1537  1531  
me        1539  1505  
me        1544  1505  
me        1548  1512  
me        1557  1512  0 08:14 ?       
me        1561  1505  1 08:14 ?        
me        1599  1561  0 08:14 ?        
me        1601  1512  0 08:14 ?        
me        1602  1505  0 08:14 ?        
me        1616  1512  0 08:14 ?        
me        1618  1512  0 08:14 ?        
me        1621  1512  0 08:14 ?        
me        1625  1512  0 08:14 ?        
me        1626  1512  0 08:14 ?        
me        1627  1512  0 08:14 ?        
me        1645  1512  0 08:14 ?        
me        1652     1  0 08:14 ?        
me        1653  1512  0 08:14 ?        
me        1656  1512  0 08:14 ?        
me        1658  1512  0 08:14 ?        
me        1667  1512  0 08:14 ?        
me        1676  1512  1 08:14 ?        
me        1680  1512  0 08:14 ?        
me        1696  1519  0 08:14 ?        
me        1702  1505  0 08:14 ?        
me        1751  1505  0 08:14 ?        
me        1753  1505  0 08:14 ?        
me        1755  1505  0 08:14 ?        
me        1766  1652  0 08:14 ?        
me        1768  1505  0 08:14 ?        
me        1769  1766  0 08:14 ?        
me        1787     1  0 08:14 ?        
me        1823  1505  0 08:14 ?        
me        2153     1  0 08:14 ?        
me        2154     1  0 08:14 ?        
me        2155     1  1 08:14 ?        
me        2292  1505  0 08:14 ?        
me        2514     1  0 08:15 ?        
me        5097  1557  0 08:20 ?        
me        5105  5097  0 08:20 pts/0    
me        6494  5105  0 08:23 pts/0    00:00:00 ps -ef
```
     

Just to be clear you can change /proc on the fly without an entry in /etc/fstab, VIA:
```
sudo mount -o remount,rw,hidepid=2 /proc
```

---

### Post by mauzaritta3 on 2019-07-04
Hello 1fallen,

thank you for your reply.

Could you please type in "cd /proc && ls -alh" and check if a normal user is able to see entries for root ?

BR Marc

---

### Post by #&amp;thj^% on 2019-07-04
Yes it shows Root, again I think you are getting tripped up over what you see and what others may see.
The key here is that you need access to the system in the first place. If you are a user on a system, there's no reason to hide other processes from you, since security through obscurity never works. 
I know the man pages can be a bit hard to understand at times, but to be clear:
Setting it to "2"
```
2   As for mode 1, but in addition the /proc/[pid] [B][U]directories
              belonging to other users become invisible.  This means
              that /proc/[pid] entries can no longer be used to discover
              the PIDs on the system.  [/U][/B]This doesn't hide the fact that a
              process with a specific PID value exists (it can be
              learned by other means, for example, by "kill -0 $PID"),
              but it hides a process's UID and GID, which could
              otherwise be learned by employing stat(2) on a /proc/[pid]
              directory.  This greatly complicates an attacker's task of
              gathering information about running processes (e.g.,
              discovering whether some daemon is running with elevated
              privileges, whether another user is running some sensitive
              program, whether other users are running any program at
              all, and so on).
```

---

### Post by deadflowr on 2019-07-04
Your output in post #5 is right.
You only list pid entries for user1
```
dr-xr-xr-x   9 user1   user1                 0 Jul  4 11:39 1835/
dr-xr-xr-x   9 user1   user1                 0 Jul  4 11:39 1987/
dr-xr-xr-x   9 user1   user1                 0 Jul  4 11:39 2002/
```
the rest aren't pids per se.
pids are numerical.

Run the command shown in the linked howto you posted earlier (or 1fallen posted):
```
ls -ld /proc/[0-9]*
```

---

