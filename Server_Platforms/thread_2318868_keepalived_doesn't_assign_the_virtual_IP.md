---
title: "keepalived doesn't assign the virtual IP"
date: 2016-03-30
forum: Server Platforms
---

### Post by AJNouri on 2016-03-30
I am testing haproxy with keepalive to 3 servers.  
Haproxy server configurations work fine (USLTS4/USLTS5), but not keepalived. 


The process started on both haproxy's, but the VIP is not assigned to the master (USLTS4), so not reachable from clients.


Here are haproxy and keepalived configs:


**haproxy**
[ATTACH=CONFIG]268065[/ATTACH]


**keepalived**
[ATTACH=CONFIG]268066[/ATTACH]


Both haproxy's work fine separately and loadbalance traffic


```
USLTS4:~$ netstat -nlta | grep :80 tcp        0      0 0.0.0.0:80     
0.0.0.0:*               LISTEN

USLTS5:~$ netstat -nlta | grep 80 tcp        0      0 0.0.0.0:80      
0.0.0.0:*               LISTEN
```

No VIP assigned to the main haproxy
[ATTACH=CONFIG]268067[/ATTACH]


Tested with unicast and multicast (default) configurations.


    ```
unicast_peer { 
    192.168.20.254
    }

```

Looks like missing something fundamental.
Any hint?

---

### Post by ajgreeny on 2016-03-30
Please do not add large images inline as you did.  Not all users will wait for them to open if they have a slow connection so you may miss some useful answers.

Please add images as attachments by clicking on the paperclip in the toolbar (if you don't see a paperclip hit the Go Advanced button) then browse to the image on your hard disk and upload it.

---

