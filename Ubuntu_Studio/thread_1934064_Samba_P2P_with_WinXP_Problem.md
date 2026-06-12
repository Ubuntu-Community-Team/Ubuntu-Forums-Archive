---
title: "Samba P2P with WinXP Problem"
date: 2012-03-01
forum: Ubuntu Studio
---

### Post by hbnmgr on 2012-03-01
I had this setup following the wonderful advice at;
[http://ubuntuforums.org/showthread.php?t=202605&highlight=XFCE+access+network+computer](http://ubuntuforums.org/showthread.php?t=202605&highlight=XFCE+access+network+computer)

But after a few updates, it now doesn't work.  Did not find it under etc/init.d 

This is what am running into ...

> 
sudo /etc/init.d/samba start
[sudo] password for ------: 
sudo: /etc/init.d/samba: command not found

sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-14 linux-headers-3.0.0-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Any suggestions?  It acts like it is down but reports it is installed ? ? ?

Thanks!

---

### Post by Morbius1 on 2012-03-01
The "samba" service no longer exists and the new one is no longer in init.d. The way you do this today is:

If samba is not running:
```
sudo service smbd start
```If samba needs to be restarted:
```
sudo service smbd restart
```

---

### Post by hbnmgr on 2012-03-01
Thanks but, does that mean I need to start all over again, or just transfer the smb.conf file?

Also, after RESTARTING as you suggested, it seems to be running but - in WinXP attempting to Map the drive gives me an error "The drive could not be mapped because no network was found".  Odd , WinXP shows my network. But perhaps my ZoneAlarm is blocking it. What Windows Service is used when mapping so I can allow it to access the trusted zone?

Thanks!

---

### Post by Morbius1 on 2012-03-01
> Thanks but, does that mean I need to start all over again, or just transfer the smb.conf file?Not sure what that means. smbd is a service. It must be running for samba to function. 
> Also, after RESTARTING as you suggested, it seems to be running but - in  WinXP attempting to Map the drive gives me an error "The drive could  not be mapped because no network was found".  Odd , WinXP shows my  network. But perhaps my ZoneAlarm is blocking it. What Windows Service  is used when mapping so I can allow it to access the trusted zone?I know nothing of Zone Alarm but you need the following ports open on both Ubuntu and WinXP in order for samba and smb to communicate:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgmYou can use Ubuntu to check to see if these ports are open on both machines by installing a package:
```
sudo apt-get install nmap
```And running the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it twice:

* Once with the ip address of the WinXP machine
* And again with the ip address of the Ubuntu machine.

[U]If you have any further problems:
[/U] 
** You need to tell folks how closely you are following that HowTo. It's primary goal is to have the Ubuntu machine set up as a WINS server. There's nothing wrong with that as long as you follow the rules and make the appropriate changes to the WinXP machine. 

** It would also be a good idea to post the output of the following commands so everyone can see how you are set up:
```
testparm -s
``````
smbtree
```

---

### Post by hbnmgr on 2012-03-01
> **Morbius1 said:**
> 
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it twice:

* Once with the ip address of the WinXP machine
* And again with the ip address of the Ubuntu machine.


OUTPUT:
```

Starting Nmap 5.21 ( http://nmap.org ) at 2012-03-01 16:31 EST
Nmap scan report for 192.168.2.51
Host is up (0.00017s latency).
All 2000 scanned ports on 192.168.2.51 are filtered (1000) or open|filtered (1000)
MAC Address: 00:E0:4C:B2:1F:11 (Realtek Semiconductor)

Nmap done: 1 IP address (1 host up) scanned in 48.05 seconds
stephen:~$ sudo nmap -sS -sU -T4 192.168.2.52

Starting Nmap 5.21 ( http://nmap.org ) at 2012-03-01 16:36 EST
Nmap scan report for 192.168.2.52
Host is up (0.0071s latency).
Not shown: 1994 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
68/udp   open|filtered dhcpc
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 7.19 seconds

```[U]> If you have any further problems:
[/U]>  
** You need to tell folks how closely you are following that HowTo. It's primary goal is to have the Ubuntu machine set up as a WINS server. There's nothing wrong with that as long as you follow the rules and make the appropriate changes to the WinXP machine. 

** It would also be a good idea to post the output of the following commands so everyone can see how you are set up:```
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = HBNET
    netbios name = MAINSYS
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No

[MyFiles]
    path = /home/samba/
    force user = stephen
    force group = stephen
    read only = No
    create mask = 0644


``````
smbtree
HBNET
    \\MAINSYS                
cli_start_connection: failed to connect to MAINSYS<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL


```Connection Failed but don't know why??  

Also, I followed the instructions fully (no WINS) via the Link first noticed above. So - Why do they keep changing the software in ubuntu so much as to render it null and void and waste so much time and expense. Mine and Yours!!!

---

### Post by hbnmgr on 2012-03-01
Apparently I forgot to change the IP in my Trusted Zone to allow traffic to my #2 Linux System. I had previously changed it to my Laptop. Simply added both IPs in my Trusted Zone. That is why no Traffic showed up in NMAP and SMBTREE.

Thanks Guys!

THREAD = Solved

---

