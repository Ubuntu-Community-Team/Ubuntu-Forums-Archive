---
title: "Eth0 transmitting a lot of data!"
date: 2010-01-11
forum: Security
---

### Post by TorchlightJay on 2010-01-11
Hello,
    So I am on wireless using wlan0. I also have a wmaster0, a pan0 (not sure what those two things are) and of course an eth0. From time to time, I use eth0 but I don't use it often (like right now I am not using it). I took a look at my firestarter and noticed that it says it's transmitted and received nearly 100TB of data! I don't even have that much data on my system. What is going on?

---

### Post by styxcoverbnd on 2010-01-11
Do you run torrents or any P2P software? Or do you have a server setup on this machine? 

Also close all open connections and open up a terminal and do a sudo netstat -tnlp and let us know the output of that command as it will show if there are any connections currently made and if there are any listening ports

---

### Post by TorchlightJay on 2010-02-26
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2022            0.0.0.0:*               LISTEN      2789/sshd       
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2890/mysqld     
tcp        0      0 0.0.0.0:9102            0.0.0.0:*               LISTEN      4184/bacula-fd  
tcp        0      0 0.0.0.0:9103            0.0.0.0:*               LISTEN      3558/bacula-sd  
tcp        0      0 0.0.0.0:8082            0.0.0.0:*               LISTEN      3037/mono       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3399/cupsd      
tcp6       0      0 :::2022                 :::*                    LISTEN      2789/sshd       
tcp6       0      0 :::80                   :::*                    LISTEN      4162/apache2    
tcp6       0      0 ::1:631                 :::*                    LISTEN      3399/cupsd  

Does any of that make sense?

---

### Post by Kinstonian on 2010-02-26
It looks like you're using Bacula for backups, which can obviously take up a lot of bandwidth.

---

