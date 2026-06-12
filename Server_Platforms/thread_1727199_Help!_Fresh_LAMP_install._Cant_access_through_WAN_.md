---
title: "Help! Fresh LAMP install. Cant access through WAN ip."
date: 2011-04-12
forum: Server Platforms
---

### Post by Sirkyuubi on 2011-04-12
This is my first post here. I hope I'm posting in the right area.

Anyways I just installed lamp stack on my my Ubuntu 10.10 Desktop (wanted to practice web hosting)

Everything installed ok. My main issue is that I cant get access to my test page, or any page for that matter, through my wan IP. When I type my LAN ip it works great.

since I know you guys need info heres what I got and what I've done.

Hardware
Router: Belkin - Model F5D8236-4 V2
8 port switch
Computer: Old Dell Workstation 3.6ghz p4 socket 775 wired eithernet connection
OS: Ubuntu Desktop 10.10 with AMP installed
Modem/ISP: Comcast High Speed Internet with phone service.


What I've done so far
I have setup the dell workstation on it's own IP and added it to DMZ to (hopefully) lower complications of dealing with NAT.
With apache2 /etc/apache2/sites-ava*/coolness is used as default and default is my backup.
Apache2 listen and vhost are set on port 9000 (I heard some isp's block ports so I used a random one)
The only files I have changed for apache2 are sites-available/coolness (default file) and ports.conf
/home/coolness/public_html/index.html has been added and works on lan. Everything in this folder is permission level 755.
I have ssh'd into another system outside my network and tried to links my wan ip. Still no go.

I honestly can't figure out why my WAN ip isn't working but my lan ip is.

---

### Post by BkkBonanza on 2011-04-12
Assuming the DMZ allows all ports thru to your server the next steps would be:

1. Make sure the server is listening as expected. Using 

sudo netstat -lntp

make sure that apache is indeed listening on the correct port.

2. On the same machine, make sure no firewall is blocking access,

sudo iptables -vnL

to see what rules may be in place.

3. Check whether the dest port is open from your remote machine. SSH to the machine, 

sudo apt-get install nmap
nmap -PN -p 9000 <wan-ip>

and see what it reports for port status. Should be "Open". If not then your router is not allowing it thru and you'll have to check the router for correct settings to allow that port and ensure it is forwarded into your DMZ.

Report back output if anything is not making sense.

---

### Post by volkswagner on 2011-04-12
Make sure your ISP is not blocking port 80.  If it is you may need to run apache2 on an alternate port.  You can change this in /etc/apache2/ports.conf

You would then need to access your server via [http://your.ext.ip.add:8080](http://your.ext.ip.add:8080) replacing your ipaddress and port number respectively.

From a computer in your LAN go to [canyouseeme.org ]("http://canyouseeme.org")and check for port 80 or any alternate you may want to run.  With your sever in a DMZ, I'd imagine any port you check should be true as for the site to function your firewall needs to be open also.

---

### Post by Sirkyuubi on 2011-04-12
coolness@ubuntu-workstation:/etc/network$ sudo netstat -lntp
[sudo] password for coolness: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp           0        0  0.0.0.0:80                0.0.0.0:*                  LISTEN         
4455/apache2    
tcp           0         0  127.0.0.1:631              0.0.0.0:*                  LISTEN
924/cupsd       
tcp           0         0  0.0.0.0:9000               0.0.0.0:*                  LISTEN
4455/apache2    
tcp          0         0  127.0.0.1:3306             0.0.0.0:*                  LISTEN
1001/mysqld     
tcp6          0         0  ::1:631                    :::*                       LISTEN
924/cupsd       


coolness@ubuntu-workstation:/etc/network$ sudo iptables -vnL
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts  bytes  target         prot opt in         out         source                      destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts  bytes  target          prot opt in        out         source                        destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts  bytes  target          prot opt in         out          source                       destination         


This is the first time I have used these so I don't know what they mean.
As far as using sudo on the ssh'd box, its never gonna happen. Apparently it does have nmap, but permission is denied.

---

### Post by BkkBonanza on 2011-04-12
Ok. Those both look correct. netstat shows that apache is listening on port 9000, and iptables shows that no blocking is occurring.

For the last step you can use any online port scanner instead of nmap. They will only scan your originating address so you have to do it from within the same network that your router is on. There are many out there but as suggested above you can try [canyouseeme.org]("http://canyouseeme.org") but test port 9000. It should indicate the port is open. If it's closed or stealth then that means you have to figure out the correct router settings to get port 9000 open for your DMZ.

Normally a DMZ wouldn't block ports but there must be some mis-configuration if the port isn't open and forwarded to your server.

---

### Post by Sirkyuubi on 2011-04-12
Ok I added port 9000 to my DMZ IP and it works. Any idea why I would need to port forward to a DMZ? I thought that DMZ was outside the network and exposed to everything.

---

### Post by BkkBonanza on 2011-04-12
I would have expected that too but I guess it's dependent on router implementation. If it doesn't expose ports then I'm not sure what purpose it serves.

---

