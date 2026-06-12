---
title: "too many queued packets"
date: 2006-07-07
forum: Server Platforms
---

### Post by coach-x on 2006-07-07
When using netstat I get the following info about current connections.  I am wondering if the number of send-q packets is anything to worry about.

```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 x.x.x.x:80       190.48.11.161:64249     ESTABLISHED
tcp        0  17290 x.x.x.x:80       201.230.96.212:41236    FIN_WAIT1
tcp        0      0 x.x.x.x:80       190.48.11.161:64399     TIME_WAIT
tcp        1  11998 x.x.x.x:80       82.150.161.110:3655     CLOSE_WAIT
tcp        0      0 x.x.x.x:80       152.130.15.16:8078      ESTABLISHED
tcp        0      0 x.x.x.x:80       152.130.15.16:8082      ESTABLISHED
tcp        0  10220 x.x.x.x:80       12.47.254.245:62676     ESTABLISHED
tcp        0      0 x.x.x.x:80       152.130.15.16:7925      TIME_WAIT
tcp        0      0 x.x.x.x:80       152.130.15.16:7964      TIME_WAIT
tcp        0      0 x.x.x.x:80       152.130.15.16:7960      TIME_WAIT
tcp        0      0 x.x.x.x:80       160.69.1.134:38047      FIN_WAIT2
tcp        0  35884 x.x.x.x:80       71.214.177.29:2026      ESTABLISHED
tcp        0  17290 x.x.x.x:80       201.230.96.212:41236    FIN_WAIT1
tcp        0  17290 x.x.x.x:80       201.230.96.212:41236    FIN_WAIT1
tcp        0      0 x.x.x.x:80       204.180.222.21:57172    FIN_WAIT2
tcp        0      0 x.x.x.x:80       56.0.84.23:23060        TIME_WAIT
tcp        0      0 x.x.x.x:80       216.77.130.75:19446     ESTABLISHED
tcp        0  12133 x.x.x.x:80       216.77.130.75:19441     ESTABLISHED
```

---

