---
title: "Apache &quot;Unable to fork new process&quot;"
date: 2010-06-09
forum: Server Platforms
---

### Post by cdenley on 2010-06-09
I had apache stop working for me this morning. After restarting apache, it began working again. I think I had the same problem a couple weeks ago. Apache's error log was filled with:
```

[Wed Jun 09 06:27:02 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process
[Wed Jun 09 06:27:13 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process
[Wed Jun 09 06:28:45 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process
[Wed Jun 09 06:28:56 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process
[Wed Jun 09 06:29:07 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process
[Wed Jun 09 06:29:18 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process

```

I think it may be related to apache being reloaded frequently. I created a log analyzer which parses an apache log and stores the data in a database. I rotated the log every time it was parsed to ensure apache wasn't writing to it while my script parsed it. I had this script run every 6 minutes. Could reloading apache 10 times an hour cause these problems? It seems to have started after I created my log parsing script. How often can I rotate apache's logs safely?

---

### Post by stlsaint on 2010-06-09
This is a memory related error. I dont know the setup of your server so it could be any number of processes taking up memory, if your running drupal you could change your settings.php file to a lower memory level, look for any mysql errors in logs, etc etc. Could you explain the setup of your server for better help!?

---

### Post by cdenley on 2010-06-09
It is mostly for two websites using PHP and mysql. A lot of different php scripts. Nothing like drupal. Mysql was running fine. Apache was listening for connections, but wouldn't respond once a connection was made. I didn't check the memory usage before I restarted apache, since I was in a hurry to get it back online. Are you sure that reloading apache frequently couldn't have somehow caused apache to exceed some kind of limit for open files or processes or something? The only text/html responses that apache took longer than 0.25 seconds to serve this morning was for someone using their wireless 3G network. The only text/html responses that took longer than 0.1 seconds this morning besides that 3G user were a few external connections which were for php scripts which are typical which I wouldn't suspect can consume a lot of memory. The server doesn't generate a lot of traffic, and 1GB of memory should be more than enough.

Apache was unavailable for almost an hour, yet all other services continued to run fine. I doubt the problem was from no more memory being available. The server's terminal appeared to respond fine, too.

---

### Post by cdenley on 2010-06-11
I was able to reproduce the problem in a virtual machine. I installed ubuntu 8.04 in vmware player with 256MB of memory, installed:
[LIST]
[*]libapache2-mod-php5
[*]libapache2-mod-python
[*]openssh-server
[/LIST]

I created an SSL vhost with a password-protected key, enabled the mod_ssl, and restarted apache. Then I created and ran a script which reloaded apache every 20 seconds. After about 86 minutes or 258 reloads, it ran out of memory. Unfortunately, the virtual machine was unusable and vmware eventually crashed, so I couldn't find out more about how the memory was being used. There was no content being hosted except for the "it works" page. There were absolutely no requests to the server except a few for "/server-status" from me.

I think this is pretty definitive that the problem is with reloading apache too frequently, as I had suspected. I still have to figure out how to fix the problem, though.

---

### Post by cdenley on 2010-06-11
I created a script to keep reloading apache until apache logs an error.
[PHP]
<?php
$logpath='/var/log/apache2/error.log';
$pos=0;
if(is_file($logpath))
        $pos=filesize($logpath);
$count=0;
$start=time();
while(true) {
        system('/etc/init.d/apache2 reload');
        $count++;
        $fh=fopen($logpath,'r');
        fseek($fh,$pos);
        while(!feof($fh)) {
                $line=fgets($fh);
                if(strpos($line,'[error]')!==false) {
                        print $line;
                        print $count." reloads\n";
                        print (time()-$start)." seconds\n";
                        fclose($fh);
                        exit(0);
                }
        }
        $pos=ftell($fh);
        fclose($fh);
}
?>
[/PHP]

This reliably reproduces the problem for me within a few minutes without making my system unusable so I can actually investigate. I seem to have memory available, but I still get that error.
```

Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.3%us, 18.1%sy,  0.0%ni, 70.9%id,  0.5%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:    255676k total,   164328k used,    91348k free,     1236k buffers
Swap:   265032k total,   162932k used,   102100k free,    16740k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
24991 root      20   0  241m 120m 4948 S  0.0 48.2   1:17.44 apache2

```

I disabled mod_php, mod_python, mod_ssl, and the ssl vhost and the problem seems to go away. I enable mod_python, and the problem comes back. I suspect the problem is with mod_python. I will keep testing to verify the problem can be reproduced with mod_python, and can't without it.

---

### Post by cdenley on 2010-06-11
I ran my script for 15 minutes and couldn't produce the problem without mod_python. With mod_python, I can produce the problem within 5 minutes. I'm confident that the problem only happens with mod_python enabled. I would like to be able to determine the underlying cause of this, though.
```

[Fri Jun 11 09:21:49 2010] [error] (12)Cannot allocate memory: fork: Unable to fork new process

```

I have free memory. There is only one apache process owned by root, since apache can't fork any more. The process only has 74 files opened. How can I determine if any of the other limits have been reached?
```

cdenley@ubuntu:~$ sudo lsof -n -p 15227|wc -l
74
cdenley@ubuntu:~$ sudo cat /proc/15227/limits
Limit                     Soft Limit           Hard Limit           Units     
Max cpu time              unlimited            unlimited            ms        
Max file size             unlimited            unlimited            bytes     
Max data size             unlimited            unlimited            bytes     
Max stack size            8388608              unlimited            bytes     
Max core file size        0                    unlimited            bytes     
Max resident set          unlimited            unlimited            bytes     
Max processes             2048                 2048                 processes 
Max open files            1024                 1024                 files     
Max locked memory         32768                32768                bytes     
Max address space         unlimited            unlimited            bytes     
Max file locks            unlimited            unlimited            locks     
Max pending signals       2048                 2048                 signals   
Max msgqueue size         819200               819200               bytes     
Max nice priority         0                    0                    
Max realtime priority     0                    0                    

```

---

### Post by cdenley on 2010-06-11
I just reproduced it in lucid as well with apache prefork.

---

### Post by cdenley on 2010-06-11
Reproduced it in maverick as well.

---

### Post by cdenley on 2010-06-11
I filed a bug report.
[https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python/+bug/592789](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python/+bug/592789)

I'm going to mark this as solved, since I don't need mod_python anyway. I would still like to know how frequently I could reload apache if there is such a thing as too frequently, and how I could determine why a process such as this fails to allocate memory (that could be useful in the future). In a couple hours, though, I won't have access to the server or any vmware images I used for testing since I will be on vacation until June 21. At least I know without mod_python enabled and without frequent log rotations, apache should allocate memory fine while I am gone.

---

