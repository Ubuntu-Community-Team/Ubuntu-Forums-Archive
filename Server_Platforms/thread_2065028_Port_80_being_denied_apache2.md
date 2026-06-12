---
title: "Port 80 being denied apache2??"
date: 2012-09-30
forum: Server Platforms
---

### Post by 4mike on 2012-09-30
Hello, I am super new to Ubuntu (first time) and I hope that this is simple, and I believe that the issues is in apache. OK, I have setup 12.4 as a web server and can access all of the software correctly from the inside local...But cannot get access to the server from the internet (outside) I have setup a server name from afraid.org and use "gatekeeper.mooo.com" I have port forwarded port 80 on my linksys router to IP 192.168.xxx.xxx....When I look at the incoming log files I can see that there is a request from the internet to my WAN port 80.....
2012-09-30 20:25:14 TCP from <snip> to 192.168.xxx.xxx:80 

But I am not getting to my server page
Any help would be great ...Thanks

---

### Post by SeijiSensei on 2012-10-01
What do you see in /var/log/apache2/error.log and access.log?

---

### Post by 4mike on 2012-10-01
SeijiSensei, Thank you for replying.  If I did this correctly the access files should be attached. part 1 and part 2 due to size

---

### Post by hasan.akgoz on 2012-10-02
Where is error.log ? Can you see ?

---

### Post by Doug S on 2012-10-02
I think your apache web server is working fine.
I think either your port forwarding is not working properly or some other firewall rule is preventing proper operation.

---

### Post by The Cog on 2012-10-02
I think apache listens on the loopback address by default. Use the command ```
netstat -lnt
``` to check. You want it listening on either 0.0.0.0:80 or :::80 (either will do).

P.S. I think the config for this might be the bind address in httpd.conf.

---

### Post by Doug S on 2012-10-02
As far as I know by default Apache will listen to all interfaces, but yes do check it as The Cog mentions. Also, we can tell from the access.log file that it is listening to the NIC.
The file httpd.conf is now empty, and only there for history reasons, I think. The listening stuff is taken care of in /etc/apache2/sites-available/default and /etc/apache2/ports.conf
 
To observe if the packets are even arriving at the server computer you could run a packet sniffer:```
sudo tcpdump -n -tttt port 80
```

---

### Post by 4mike on 2012-10-02
OK,
Here is the errorlog..also as was suspect I have been told the cablevision blocks port 80 , I have tried several others with no change in results.

---

### Post by hasan.akgoz on 2012-10-02
I wrote web browser localhost see you default apache web page ? Can I see virtualhost file define ?

---

### Post by SeijiSensei on 2012-10-03
> **4mike said:**
> OK,
Here is the errorlog..also as was suspect I have been told the cablevision blocks port 80 , I have tried several others with no change in results.

First, if Cablevision is blocking port 80, it probably means the Terms of Service on your account forbid running servers.  This is a pretty common feature of the contracts from most residential providers in the US.  Technically, the [Forum Rules]("http://ubuntuforums.org/index.php?page=policy") forbid us from helping in this case.

Second, you say you tried other ports.  Did you try them on the router?  What happens if your forward, say, port 40000 back to the server's port 80?

---

### Post by 4mike on 2012-10-07
OK,  First thank you to everyone for your help this really is a great community.
 
I found out what the real issue is, if I allow the network interface to stay as the default DHCP and use another port then I can get it to work.  If I use the same IP and change it to static in the Network Config and reset /reboot then I no longer have access to the WAN.  
 
All I am doing is changing eth0 to static configuration assign 192.168.xxx.xxx  net mask to 255.255.255.0 and leave broadcast to automatic

---

