---
title: "Suspicious Network Activity"
date: 2011-07-12
forum: Security
---

### Post by dragonboss on 2011-07-12
I've recently noticed (via my conky) my computer has an average down speed of 120KB/s when idle, so i checked using nethogs the program what was utilizing the bandwidth and all i got was strings of numbers as the program using, not program names. Should I be concerned about this? Has my pc security been compromised? Also I installed and ran chkrootkit and it said everything was clean apart from nethogs(which was running at the time) and my open jdk being suspicious.

---

### Post by ~!geek!~ on 2011-07-12
Does average download rate is always 120 kBps. 
There may be a number of cases:
1 if u r using nethogs with browser on, it may be that the nethogs is showing ip addresses of the websites (the numbers you saw on nethogs) which u r accessing. This might not be a trouble for you. You may confirm it by checking the number shown after : in the string if its :80 written, this is probably the case. You may double check it by selecting the number string xxx.xxx.xxx.xxx:80 and middle click in browser address bar. See where it leads. If its website u r currently browsing you may be safe.
2 If u use torrent client a lot, It may be because of sharing of files using these torrent clients. I m unable to help much with it.
3. If u see that download for some time only it may be because of update manager which checks for the updates according to you preferences. 
See if it helps!!!

---

### Post by dragonboss on 2011-07-12
I closed all apps that use the internet to check whether any of those were causing the down speed to go up and they were not the cause. The number after the : is a 5 digit number like :XXXXX, and the whole line looks like:

```
PID      USER        PROGRAM                     DEV      SENT       RECIEVED
0        root       ..:XXXX-XX.XXX.XXX.XX:XXXX            0.000       XX.XXX KB/sec
```

---

### Post by ~!geek!~ on 2011-07-12
The number after : is the port number to which the application is trying to communicate with your system. port 80 is standard port for http protocol. The 5 digit port number is generally used by bittorrent protocols. Try to google something like: port xxxxx i.e port number that u see after : in the nethogs. If u find any standard app using this port by default, you may try to check if the application  found above is causing the problem. If its not standard port, I don't know any method to stop it except trying to set your ip to new one (if your internet connection has facility to set dynamic ip addresses, but as i said i m not of any help in this case) 
If you find any standard application using this port and you realize that you have one of these app installed. you may try to close that. 
I don't want u to panic but this huge  download rate of data without your knowledge is not healthy for the system. Set up some sort of firewall asap.

---

### Post by dragonboss on 2011-07-12
I have gufw set up already. I believe I've discovered the cause now. It was a boinc-client I left behind when uninstalling boinc. False Alarm!

---

### Post by karlson on 2011-07-12
> **dragonboss said:**
> I closed all apps that use the internet to check whether any of those were causing the down speed to go up and they were not the cause. The number after the : is a 5 digit number like :XXXXX, and the whole line looks like:

```
PID      USER        PROGRAM                     DEV      SENT       RECIEVED
0        root       ..:XXXX-XX.XXX.XXX.XX:XXXX            0.000       XX.XXX KB/sec
```

As a simple test have you tried looking at:

```
 sudo "netstat -apn | grep XXXX" 
```

where XXXX is the port number reported by nethogs?

---

### Post by ~!geek!~ on 2011-07-12
> **dragonboss said:**
> I have gufw set up already. I believe I've discovered the cause now. It was a boinc-client I left behind when uninstalling boinc. False Alarm!


Good to know that!!! 
Cheers!!!
:D

---

