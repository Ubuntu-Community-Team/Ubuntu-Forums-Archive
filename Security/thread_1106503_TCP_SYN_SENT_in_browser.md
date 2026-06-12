---
title: "TCP SYN_SENT in browser"
date: 2009-03-25
forum: Security
---

### Post by unf4b1x on 2009-03-25
I guess now I really need to put a stop to this and I really need your help coz I can't do it on my own, please. I can't work properly everytime an outbound connections such as these comes up. It makes surfing/browsing/logging in to legitimate sites so slow until it times out. I can't access to sites I usually accessed before. And people doesn't seem to believe that I am already being hacked or something coz they always say that a plugin/addon of firefox blah blah blah... When it doesn't always involve firefox. It involves ALL browsers who is using port 80. My wineserver is using port 80. Sorry but I need to obfuscate the source and destination to protect myself. Please, I just need a simple guide that a newbie like me could understand better. Is this what they call a TCP SYN_SENT flood attack?```
sudo netstat -plant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:0           0.0.0.0:*               LISTEN      6635/sendmail: MTA:
tcp        0      0 127.0.0.1:0           0.0.0.0:*               LISTEN      6297/cupsd      
tcp        0      0 127.0.0.1:0            0.0.0.0:*               LISTEN      6635/sendmail: MTA:
tcp        0      1 1.2.3.4:33957   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:49873   9.10.11.12:80         SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:48523   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:33958   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:33956   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:35594   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:35530   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:33920   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:33938   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:35616   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:35538   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:35615   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:35601   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:33939   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      0 1.2.3.4:41249   212.175.15.77:80        ESTABLISHED 16948/firefox   
tcp        0      1 1.2.3.4:35599   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:33941   5.6.7.8:80        SYN_SENT    16948/firefox   
tcp        0      1 1.2.3.4:49872   9.10.11.12:80         SYN_SENT    16948/firefox  
```

---

### Post by The Cog on 2009-03-25
According to that output, your IP address is 1.2.3.4. Firefxo is repeatedly trying to connect to 5.6.7.8 but 5.6.7.8 is not answering - not even rejecting the connection request. It's not a straight internet fault though, because it has succesfully connected to 212.175.15.77.

So I guess the question is, what is 5.6.7.8 and why is firefox so keen to connect to it? Could it be checking for plugin updates?

P.S.
It's not a SYN flood attack against you - it is your PC that is sending the SYN (connect request) packets.

---

### Post by cariboo on 2009-03-25
It really doesn't help when you obfuscate the ip address if you are behind a router you ip address is non-routeable. If you are running a server why hide the ip address. From the one ip address that you didin't change, it looks like you computer is sending data to Turkey. I would suggest unplugging the nework cable and running rkhunter or chkrootkit.

Jim

---

### Post by shad0w_crash on 2009-03-26
Could you dump the pakket and post it?

[http://packages.ubuntu.com/dapper/tcpdump](http://packages.ubuntu.com/dapper/tcpdump)

Do you use something like hamachi (VLAN)?

---

