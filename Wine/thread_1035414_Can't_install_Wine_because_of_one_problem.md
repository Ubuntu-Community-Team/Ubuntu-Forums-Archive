---
title: "Can't install Wine because of one problem"
date: 2009-01-09
forum: Wine
---

### Post by wolfyking2 on 2009-01-09
Ok, when I open up the .deb package, I click the install button.  It asks me for my password, I type it in.  Then it says I can't install it because some other program like synaptic or Add/Remove is running, but nothing like that is running besides the installer.  It does this for every thing I try to install.  It must be so simple, but I really need help :(:confused:

---

### Post by ajgreeny on 2009-01-09
Have a look at what is running with```
 top -n 1
``` in the terminal and post the output back here.

---

### Post by wolfyking2 on 2009-01-09
This is what I have: top - 16:17:01 up  9:58,  2 users,  load average: 0.48, 0.23, 0.20
Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.1%us,  2.6%sy,  2.8%ni, 86.0%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514048k total,   505480k used,     8568k free,     6064k buffers
Swap:   883532k total,    39404k used,   844128k free,   197968k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5046 root      20   0  237m  41m 7780 S  2.0  8.2  23:04.75 Xorg               
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:01.48 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  111 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  145 root      20   0     0    0    0 S  0.0  0.0   0:00.58 pdflush            
  146 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush            
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.36 kswapd0            
  188 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1436 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd I have no flippin' idea what all this means tho >.<

---

### Post by ajgreeny on 2009-01-09
Nothing of help in what you posted there, but there would be other processes that you could not see without scrolling the output to the bottom.  have another look, or look in the kde of system monitor (can't remember what it's called) and look for anything that could be using dpkg or apt in any way.  Post back again if you wish.

By the way, can you try installing it with synaptic or adept and see if you get the same problem.

---

### Post by wolfyking2 on 2009-01-09
WHAT? O.O I have no idea what you just said

---

### Post by hikaricore on 2009-01-09
Try rebooting then installing it.

Some program has the installer (dpkg) locked up on you will not be able to install a package until it is closed.

---

### Post by Meow27 on 2009-01-10
the updater is also considered to be a synaptic

---

