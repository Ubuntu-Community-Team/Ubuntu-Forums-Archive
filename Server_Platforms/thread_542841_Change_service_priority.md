---
title: "Change service priority"
date: 2007-09-04
forum: Server Platforms
---

### Post by huggy77 on 2007-09-04
I am loading a couple of services on boot - namely Glassfish, APACHE2 and Qmail.  Is there a way to tell linux that these 3 services are extremely important and should be treated as such...

currently my TOP looks like:
```

10950 root      15   0  2320 1144  884 R  0.3  0.2   0:00.02 top                                                                                                
12647 root      18   0     0    0    0 Z  0.3  0.0   0:00.01 [tcpserver] <defunct>                                                                              
    1 root      18   0  2908 1848  524 S  0.0  0.4   0:01.10 /sbin/init                                                                                         
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [migration/0]                                                                                      
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 [ksoftirqd/0]                                                                                      
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [watchdog/0]                                                                                       
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 [events/0]                                                                                         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 [khelper]                                                                                          
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 [kthread]                                                                                          
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [kblockd/0]                                                                                        
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 [kacpid]                                                                                           
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 [kacpi_notify]                                                                                     
  115 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [kseriod]                                                                                          
  139 root      20   0     0    0    0 S  0.0  0.0   0:00.00 [pdflush]                                                                                          
  140 root      15   0     0    0    0 S  0.0  0.0   0:00.01 [pdflush]                                                                                          
  141 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [kswapd0]                                                                                          
  142 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [aio/0]                                                                                            
 1811 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [ksuspend_usbd]                                                                                    
 1812 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [khubd]                                                                                            
 1937 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [ata/0]                                                                                            
 1938 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 [ata_aux]                                                                                          
 1961 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 [scsi_eh_0]                                                                                        
 2361 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [scsi_eh_1]                                                                                        
 2362 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [scsi_eh_2]                                                                                        
 2609 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 [kjournald]                                                                                        
 2740 root      21  -4  2296  628  376 S  0.0  0.1   0:00.40 /sbin/udevd --daemon                                                                               
 3621 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 [kpsmoused]                                                                                        
 4311 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 /sbin/getty 38400 tty4                                                                             
 4312 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 /sbin/getty 38400 tty5                                                                             
 4314 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 /sbin/getty 38400 tty2                                                                             
 4315 root      18   0  1652  508  440 S  0.0  0.1   0:00.00 /sbin/getty 38400 tty3  

```

Are there any services here you think i should disable?

---

### Post by HermanAB on 2007-09-04
You can try 'renice' to change the priority, but you'll likely find that it won't make the slightest difference.  The Linux scheduler is very good and unless the server is extremely loaded, increasing the priority of a task won't have a noticeable effect, since everything will always run to completion anyway.

Cheers,

H.

---

### Post by Mr. C. on 2007-09-06
The system and various services are well tuned and capable of handling significant loads.  Changing a processes nice value is not the right approach.

It is not useful to attempt to make changes to things you don't really understand.  If you experience a problem, attempt to analyze that problem through observation and measurement.  Only then should you attempt to make modifications.

MrC

---

