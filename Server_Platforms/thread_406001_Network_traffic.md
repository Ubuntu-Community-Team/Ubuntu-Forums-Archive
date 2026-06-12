---
title: "Network traffic"
date: 2007-04-10
forum: Server Platforms
---

### Post by tutone on 2007-04-10
I think my Ubuntu 6.10 server has been hacked. My router is showing traffic to port 21 and 22 that should not be there. I have webmin installed and ssh server, both still working. How can I see which files are being accessed? I am trying to use the stat command but I keep getting syntax errors. Any help would be appreciated!

---

### Post by zarg@henrikke on 2007-04-10
> **tutone said:**
> I think my Ubuntu 6.10 server has been hacked. My router is showing traffic to port 21 and 22 that should not be there. I have webmin installed and ssh server, both still working. How can I see which files are being accessed? I am trying to use the stat command but I keep getting syntax errors. Any help would be appreciated!

Block port 21 and 22 on your server:

iptables -I INPUT 1 -p tcp --dport 21 -j DROP
iptables -I INPUT 1 -p tcp --dport 22 -j DROP

---

### Post by tutone on 2007-04-10
Thanks for the post. I am really more interested in what they are doing then that they are in the machine. Is there a command to list just the files that have been accessed over the past 7 days? I will reset this machine once I know what they have been up to. The source IP are coming back from China, Korea and Japan.

---

### Post by bait on 2007-04-10
Try typing in netstat -p to see which program is using ports 21 /20.

---

### Post by NeoGreen on 2007-04-10
You might want to try to block those IP Address if they have not changes.  You can do this by typing the following:
 ```
iptables -A INPUT -s a.b.c.d -j DROP
```

replace the a.b.c.d with the intruders IP address.

---

### Post by rgeddes on 2007-04-11
To log all activity on a port you can do the following:

```
sudo tcpdump -w tcpdump.log.1 dst port 22
```

      This will capture and log all events on port 22 to a file called "tcpdump.log.1"
      To stop the logging - Control-C
      To capture all packets/datagrams omit the "dst port 22" part
      Be mindful of the log file size - depends on how many packets/datagrams are recorded
      You can watch the file size grow with 

```
watch ls -l tcpdump.log.1
```

When you are done collecting data

Open the file "tcpdump.log.1" in the ethereal (wireshark) program 

    To isolate a tcp session that contains an ip address of interest, 
      select the entry with the ip address, click-right and select "Follow TCP Stream"

Ethereal (wireshark) has many more features... this can get you started if you are interested in knowing what your uninvited guests are doing... the packet/datagram data can look a little daunting, but with a little effort and patience you can start to make some sense of it...

cheers
Rich

---

### Post by rgeddes on 2007-04-11
Forgot to mention lsof

lsof -p PID

will list all the files being used that are associated with the process id number PID

If you can manage to get the PID number of an intruder process, you can send it to lsof and it will tell you all the files are associated with that process id number.

So if an intruder process is 666, let's say, and the intruder is accessing the "sensitive.data" file

```
lsof -p 666
```

should list the connections associated with the intruder as well as the "sensitive.data" file.

---

### Post by colinireland on 2007-04-12
Hello

I am having some trouble running ethereal under Dapper.
When I run ethereal I can't seem to pick up the TCP traffic of other laptops on my wireless network. I am using ipw2200 and checked the box saying to use promiscuous mode. I used the ifconfig command to enable promiscuous mode. Ethereal can pick up all data to and from my computer. I can only see NBNS, DHCP, IGMP, SSDP, DNS and browser protocols from other computers on my network. 

Is there something I am doing wrong? Is it a driver problem? 

Any help would be very much appricated.

Colin
PS does anyone know of a good ethereal tutorial etc they could direct me to?

---

