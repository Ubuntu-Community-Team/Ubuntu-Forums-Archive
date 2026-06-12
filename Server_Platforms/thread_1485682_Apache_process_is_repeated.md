---
title: "Apache process is repeated"
date: 2010-05-17
forum: Server Platforms
---

### Post by technocp on 2010-05-17
I am using ubuntu 8.10 server for running my sugar crm. because of some reason I can see multiple instances of apache2 running when I issue top command. can I further know about the problem that is occuring.

I know this is more of sugarcrm or php or apache problem but I would like to track the problem. your guidance for the same is required.

Thanks

---

### Post by iponeverything on 2010-05-17
The default configuration of apache is to start several processes in order to better service multiple client connections. This number can be changed in the apache config file.

---

### Post by technocp on 2010-05-17
so do you believe that this is not a problem and I should not be worried about it. for more information below is the result of top command issued
14472 www-data  20   0  208m  22m 3884 R   33  1.1   6:17.22 apache2        
14514 www-data  20   0  212m  26m 4040 R   25  1.3  10:19.85 apache2        
17497 www-data  20   0  209m  23m 3844 R   23  1.2   0:07.98 apache2        
13159 www-data  20   0  208m  22m 4036 R   21  1.1  20:09.96 apache2        
17231 www-data  20   0  208m  22m 3844 S   15  1.1   1:15.85 apache2        
13511 www-data  20   0  208m  22m 4028 S   14  1.1  22:44.85 apache2        
16447 www-data  20   0  213m  26m 3892 S   14  1.4   3:30.11 apache2        
17360 www-data  20   0  227m  40m 3892 S   14  2.0   0:29.18 apache2        
13174 www-data  20   0  223m  35m 3976 R   13  1.8   6:06.88 apache2        
17268 www-data  20   0  212m  25m 3756 R   12  1.3   0:57.08 apache2        
17262 www-data  20   0  208m  22m 3856 S   12  1.1   0:56.93 apache2        
17556 root      20   0  178m  33m 7516 S    2  1.7   0:00.83 php            
 2170 mysql     20   0  241m  61m 5996 S    1  3.1   8:40.40 mysqld         
17577 root      20   0 18984 1312  988 R    0  0.1   0:00.04 top            
    1 root      20   0  4104  924  632 S    0  0.0   0:01.01 init           
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd       
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.19 migration/0    

pls. suggest if this is a problem and any steps to be taken

---

### Post by iponeverything on 2010-05-17
It is not a problem.

---

