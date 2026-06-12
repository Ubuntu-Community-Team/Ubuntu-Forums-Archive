---
title: "port 1024 open"
date: 2010-07-16
forum: Security
---

### Post by worksofcraft on 2010-07-16
Port Scan from "System>Administration>Network Tools" always showing port 1024 as open by "unknown" service on my computer. According to a security site it is associated with the "Latinus key logger virus" but that only runs on Windows I thought?

How can I find out what is listening on this port on Ubuntu 10.04 and what it's purpose is?

---

### Post by oomar on 2010-07-16
give us a little more information about your system and what you have installed.

id also like you to run "ss" in the command line. post its output. you can x out your IP address tho.

---

### Post by anomie on 2010-07-16
First: 

**$ sudo netstat -ltnp**

Check for clues about the program name, and make a note of the PID. Next: 

**$ sudo lsof -p <pid_here>**

That will show the files it has open, and should help you narrow down what it is.

---

### Post by worksofcraft on 2010-07-16
Thanks for those suggestions...

netstat -ltnp

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1145/samba      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1201/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1145/samba      
tcp        0      0 0.0.0.0:1024            0.0.0.0:*               LISTEN      1146/samba      
tcp        0      0 0.0.0.0:135             0.0.0.0:*               LISTEN      1146/samba      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1201/cupsd

so it looks like it's Samba... I did install but haven't managed to get it to show my shared folders on the windows network yet.

meanwhile I'm still looking through the output of ss because it has a lot of IP addresses in it and I wouldn't want to accidentally disclose things to potential hackers... thanks for that tip too :)

---

### Post by cariboo on 2010-07-16
If you are behind a router, your ip address is non-routable, so it doesn't matter if we see it or not.

If you are that concerned, just past the output of the **ss** command in gedit and use the search and replace function to change all instances of your ip address to **xxx.xxx.xxx.xxx**.

---

### Post by worksofcraft on 2010-07-16
Yes, thanks... there were pages and pages of output from ss and I suspect something was seriously wrong. In synaptic package manager I found I had experimental Samba-4 installed and so I removed it.

Now ss just gives:

State      Recv-Q Send-Q      Local Address:Port          Peer Address:Port   
ESTAB      0      0           192.168.1.100:52967         192.168.1.97:netbios-ssn 
ESTAB      0      0           192.168.1.100:52962         192.168.1.97:netbios-ssn 
ESTAB      0      0           192.168.1.100:50790         192.168.1.97:microsoft-ds 
ESTAB      0      0           192.168.1.100:52963         192.168.1.97:netbios-ssn 

and the mysterious port 1024 has disappeared too. I still have smbfs installed and I can still see shared folders on the network here... IDK perhaps I had an infected Samba-4 :shock:

---

### Post by oomar on 2010-07-16
once you have samba installed you still have to manually add the folders you want to share. 

now are you scanning from another computer or are you just doing a loopback scan because you will get differetn results. if i scan myself i always have random ports popping open but if i portscan from an outside source (ie my server) i find no ports open.

how it should be. lol

---

### Post by worksofcraft on 2010-07-17
Yes I had noticed those random ports too so I was using the port scan from a virtual machine running in Virtual box.

However  ss command I did run on my actual computer. It showed  literally hundreds of active IP addresses listed and I did a who is on many of them to find they were all over the world. Which I thought was strange since I only just switched on my computer and had hardly done anything yet. Sadly I overwrote that list with a new ss command after removing Samba 4... Would it be worth re-enable Samba4 in synaptic? just to see if it comes back?

---

### Post by oomar on 2010-07-17
i meant from an actualy physcial computer. im not sure what the differences would be from a virtual pc on your computer.

as for the ss results. it could very well just be internet connections. if you have a bunch of tabs open, that could be one reason for many connections. so close down EVERYTHING when you run ss to determine what is actually causing your open ports

---

### Post by cariboo on 2010-07-17
There is a bug in the gui network tools, that shows random ports open when you run a scan on localhost, I submitted it a couple of years ago, it was sent upstream, but I don't think it was ever fixed.

I personally prefer using nmap from the command line for port scanning, and always scan from another computer on my network.

---

### Post by oomar on 2010-07-17
i also use nmap for this purpose and it works great

---

