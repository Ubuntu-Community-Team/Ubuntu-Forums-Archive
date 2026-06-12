---
title: "This showed up in my netstat - Plz help the n00b"
date: 2011-10-31
forum: Security
---

### Post by vociferous666 on 2011-10-31
```
tcp        0      0 tan-serv.l:microsoft-ds hosted.by.pacificr:1721 ESTABLISHED
tcp6       0      0 192.168.1.10%32174:5900 192.168.1.5%164563:2799 ESTABLISHED

```


Second line is my local vnc connection from a laptop.
tan-serv is the host name of my ubuntu box.
I am hoping this is some kind of WINS or domain related stuff for SMB. 

Anyone know what this is?

---

### Post by Dangertux on 2011-10-31
Could you give more detailed output via the following command.

```

sudo netstat -ntpu

```

Thanks.

---

### Post by vociferous666 on 2011-10-31
```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.10:139        173.72.37.186:2470      ESTABLISHED 12278/smbd      
tcp        0     12 192.168.1.10:445        192.168.1.115:55710     ESTABLISHED 14815/smbd      
tcp        0      0 192.168.1.10:23         192.168.1.115:23        ESTABLISHED 15352/in.telnetd: c
tcp        0      0 192.168.1.10:445        216.45.50.151:1721      ESTABLISHED 887/smbd   
```

---

### Post by vociferous666 on 2011-10-31
Seems I set up my port forwards wrong and outside clients are connecting to my smb server eek!

Ill start looking into that.

---

### Post by Dangertux on 2011-10-31
In addition to the samba which is a concern, what's up with the telnet connection.

---

