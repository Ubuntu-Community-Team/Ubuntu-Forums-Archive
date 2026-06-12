---
title: "[SOLVED] 'top' shows some processes running as root"
date: 2008-04-29
forum: The Cafe
---

### Post by bryncoles on 2008-04-29
firstly, apologies if this would be better off in another forum, or is a reoccuring discussion. ive just noticed though that typing 'top' into the terminal shows a lot of my processes as root. mostly, they are inactive - except xorg and init. what are these processes, why are they running as root (when im not) and should i be concerned?

---

### Post by SuperSon!c on 2008-04-29
you'll probably want to copy/paste what you're seeing.

---

### Post by bryncoles on 2008-04-29
good point.... i see this:

bryn@bryn-laptop:~$ top

top - 13:42:56 up  4:11,  2 users,  load average: 0.99, 0.43, 0.34
Tasks: 108 total,   1 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.3%us,  1.8%sy,  0.2%ni, 77.0%id,  8.6%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:    483092k total,   468608k used,    14484k free,     6264k buffers
Swap:  1413680k total,   203328k used,  1210352k free,   119028k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8087 bryn      20   0  265m 110m  22m S 47.3 23.5  12:36.17 firefox            
 7531 bryn      20   0 21780 6332 4732 S  3.9  1.3   0:55.25 compiz.real        
 7088 root      20   0  300m  68m 5816 S  2.0 14.5  13:50.69 Xorg               
    1 root      20   0  2844  532  480 S  0.0  0.1   0:01.48 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 kblockd/0          
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  117 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  148 root      20   0     0    0    0 S  0.0  0.0   0:00.12 pdflush            
  150 root      15  -5     0    0    0 S  0.0  0.0   0:01.34 kswapd0            
  191 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
bryn@bryn-laptop:~$

---

### Post by SuperSon!c on 2008-04-29
i see that firefox is chewing up CPU's.  do a search because this is a known bug for quite a few people on ubuntu.  this temp fix worked wonders for me (if this is your problem)

>  Originally Posted by philinux  View Post
Firefox 3 has a documented bug regarding its anti attack and forgery website detection. This bug causes 100% cpu and lots of disk activity.

The solution/workaround is to go into your mozilla profile folder in home and delete the following file.

/home/username/.mozilla/firefox/xxxxxx.default/urlclassifier3.sqlite

Close and restart firefox and this file will be recreated.

Initially this file was 30mg now it's 500kb.

---

### Post by picopir8 on 2008-04-29
I dont see anything out of the ordinary.

Your computer needs to boot up to a point that allows you to log in.  Everything that is launched up to that point is launched as root.  Also a number of cron jobs and maintenance tasks are also launched as root.

Most things tend to be very low CPU usage.  If you see anything that is running as root that takes up a lot of CPU, type the command into a search engine or read its manpage to learn more about it and see if it should be running.

Under normal usage though, there should be a number of root entries.

---

### Post by bryncoles on 2008-04-29
ah, thank you both! i was wondering if there was something here i should worry about, or if it all looked normal. 

ill look into toning down firefox... making it a little less 'enthusiastic' at least! 

good to know everything looks normal :-)

---

### Post by SuperSon!c on 2008-04-29
is that firefox cpu % when it's idling?  leave eveything alone and have one page open with firefox and let it sit for a min and take a look at the cpu usage then.

---

### Post by blithen on 2008-04-29
The computer obviously need processes running before you log in. You can only start running process on a non-root account when you log in. Thus all the main system process are going to be in root, and not your name.

---

### Post by bryncoles on 2008-04-29
with all applications closed (bar the terminal and firefox), the cpu idles at around 1% - except for xorg it would seem! i usually have about three tabs open in firefox, which pushes it up a little though ;-)

i followed your advice about deleting the file urlclassifier3.sqlite
from firefox, and that seems to have made a difference too. top now looks like this:

bryn@bryn-laptop:~$ top

top - 16:20:56 up 35 min,  2 users,  load average: 0.15, 0.45, 0.51
Tasks: 100 total,   2 running,  98 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3%us,  1.7%sy,  0.0%ni, 89.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    483092k total,   420420k used,    62672k free,     2576k buffers
Swap:  1413680k total,    74220k used,  1339460k free,    86420k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6086 root      20   0  271m  47m 6296 S  8.3 10.0   3:18.76 Xorg               
 7957 bryn      20   0  228m  87m  21m S  1.0 18.6   1:51.26 firefox            
 8206 bryn      20   0  2308 1104  856 R  0.7  0.2   0:00.46 top                
    1 root      20   0  2844 1568  500 S  0.0  0.3   0:01.46 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0          
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  117 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  148 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  149 root      20   0     0    0    0 S  0.0  0.0   0:00.04 pdflush            
  150 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 kswapd0            
bryn@bryn-laptop:~$ 

though xorg only started using 8% cause i started typing! it wasnt even showing when i started this reply.... :-D

*edit*

and xorg dropped back down to nice, low levels after i posted! it usually runs at around 2% so i dont worry too much that its at 8% in the above...

---

