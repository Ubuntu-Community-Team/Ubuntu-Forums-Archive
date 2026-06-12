---
title: "netstat -ta and understanding the log.."
date: 2009-02-02
forum: Security
---

### Post by tednumber8 on 2009-02-02
I would like to understand the log from netsta -ta and why there are so mnay established connections on one IP address.

> Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:30992                 *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 192.168.0.3:49610       .bb.sky.com:www ESTABLISHED
tcp        0      0 192.168.0.3:49609       5.bb.sky.com:www ESTABLISHED
tcp        0      0 192.168.0.3:43386       65.55.11.240:www        ESTABLISHED
tcp        0      0 192.168.0.3:41427       ec2-75-101-162-204.:www TIME_WAIT  
tcp        0      0 192.168.0.3:49608       .bb.sky.com:www ESTABLISHED
tcp        0      0 192.168.0.3:49611       .bb.sky.com:www ESTABLISHED
tcp        0      0 192.168.0.3:49587       .bb.sky.com:www ESTABLISHED
tcp        0      0 192.168.0.3:49607       .bb.sky.com:www ESTABLISHED
tcp        0      0 192.168.0.3:41434       ec2-75-101-162-204.:www TIME_WAIT  
tcp        0      0 192.168.0.3:41430       ec2-75-101-162-204.:www TIME_WAIT 


Is there anything to worry about here and anyone know a good place to learn about this?

---

### Post by jerome1232 on 2009-02-02
Looks like they are all on port 80 do you have firefox open with a couple tabs to these sites?

If you add the -p flag and run netstat as root it'll tell you which program has the connection open

```
sudo netstat -tap
```

---

### Post by tednumber8 on 2009-02-02
Cheers buddy, have a better understanding already :popcorn:

---

