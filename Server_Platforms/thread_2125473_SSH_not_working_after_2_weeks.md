---
title: "SSH not working after 2 weeks"
date: 2013-03-14
forum: Server Platforms
---

### Post by carp3di3m on 2013-03-14
Ubuntu server fresh install 3 weeks old.

After 2 weeks ssh stopped working.

When i reboot ssh is listening but has to restarted every time. then it work

No iptables and lucky i have shellinabox installed which works fine

netstat -tln                                                                
Active Internet connections (only servers)                                                                                    
Proto Recv-Q Send-Q Local Address           Foreign Address         State                                                     
tcp        0      0 0.0.0.0:4200            0.0.0.0:*               LISTEN                                                    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN                                                    
tcp        0      0 0.0.0.0:50923           0.0.0.0:*               LISTEN                                                    
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN                                                    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN                                                                                                       
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN                                               
tcp        0      0 0.0.0.0:46502           0.0.0.0:*               LISTEN                                                    
tcp6       0      0 :::111                  :::*                    LISTEN                                                    
tcp6       0      0 :::59536                :::*                    LISTEN                                                    
tcp6       0      0 :::22                   :::*                    LISTEN                                                    
tcp6       0      0 :::12865                :::*                    LISTEN                                                    
tcp6       0      0 :::45185                :::*                    LISTEN

---

