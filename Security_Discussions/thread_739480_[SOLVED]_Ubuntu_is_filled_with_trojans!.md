---
title: "[SOLVED] Ubuntu is filled with trojans!"
date: 2008-03-29
forum: Security Discussions
---

### Post by apokkalyps on 2008-03-29
I'm probably about to set up a bunch of server services.  I was thinking about security last night and did some googling and asked a few questions on IRC.  I found a webpage that suggested I install portsentry and tripwire.  I happened to nmap myself right before I did any of this and this was the result.


> 
barrett@barrett-desktop:~$ nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-29 09:13 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1687 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
2049/tcp open  nfs
3306/tcp open  mysql
6881/tcp open  bittorent-tracker

Nmap finished: 1 IP address (1 host up) scanned in 0.202 seconds



Then I was asking on IRC about security issues with sudo giving root access with a users password (maybe someone went after me from there).  The only other thing I did was uninstall FTP and install portsentry and tripwire in synaptic.  Immediatly after I do another NMAP to make sure my ftp is gone and this is what I get:


> 

barrett@barrett-desktop:~$ nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-29 09:56 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1666 closed ports
PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
22/tcp    open  ssh
25/tcp    open  smtp
79/tcp    open  finger
80/tcp    open  http
111/tcp   open  rpcbind
119/tcp   open  nntp
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
540/tcp   open  uucp
631/tcp   open  ipp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
2049/tcp  open  nfs
3306/tcp  open  mysql
6667/tcp  open  irc
6881/tcp  open  bittorent-tracker
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k



I recognize that stuff, NetBus, bo2k, trino_master and I think elite are all trojans, and theres a ton of other crap that I dont know why it has open connections to the internet all of a sudden.  

I ran chkrootkit and found nothing, did a nessus scan (possibly out of date) and it only found one netbus (but said the port was closed immediatly something about a possible tcp wrapper)

_____________________________________
EDIT:  not really trojans.....

[COLOR="Red"]I thought my ubuntu had been infected by a bunch of trojans, but I just figured out this is portsentry.  It dawned on me that nmap was probably just pulling the protocols on the ports it found open from a list and they may not actually be what its reporting them as.  Nessus was unable to open the ports so that corroborated it.  I uninstalled portsentry and it went back to the way the original nmap scan looked.  I have now reinstalled it and the ports are open again.  I think portsentry opens all these ports like a honeypot but the services arent there.  It waits for attacks on them, logs it, and possibly takes action.  [/COLOR]

I did a 
> sudo netstat -nlp

and sure enough, it lists all those open tcp ports under the process portsentry.

> 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:1               0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:20034           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:54850           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:32771           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:32772           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:40421           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:32773           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:32774           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:31337           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     5493/mysqld         
tcp        0      0 0.0.0.0:45226           0.0.0.0:*               LISTEN     4668/rpc.statd      
tcp        0      0 0.0.0.0:6667            0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:11              0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     6568/smbd           
tcp        0      0 0.0.0.0:5742            0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:49742           0.0.0.0:*               LISTEN     6491/rpc.mountd     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:79              0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:15              0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4649/portmap        
tcp        0      0 0.0.0.0:54320           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     7012/apache2        
tcp        0      0 0.0.0.0:27665           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:1524            0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5417/cupsd          
tcp        0      0 0.0.0.0:1080            0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:12345           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     6359/exim4          
tcp        0      0 0.0.0.0:12346           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:635             0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:49724           0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:540             0.0.0.0:*               LISTEN     8204/portsentry     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     6568/smbd           
tcp6       0      0 :::22                   :::*                    LISTEN     5340/sshd           
udp        0      0 0.0.0.0:640             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          4668/rpc.statd      
udp        0      0 0.0.0.0:641             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:513             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:1               0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          6491/rpc.mountd     
udp        0      0 0.0.0.0:32772           0.0.0.0:*                          6732/avahi-daemon:  
udp        0      0 0.0.0.0:32773           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:32774           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:7               0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:9               0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:161             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:162             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:54321           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:700             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:323             0.0.0.0:*                          6864/chronyd        
udp        0      0 0.0.0.0:37444           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:68              0.0.0.0:*                          8024/dhclient       
udp        0      0 0.0.0.0:69              0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:604             0.0.0.0:*                          4668/rpc.statd      
udp        0      0 0.0.0.0:31335           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:31337           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          6732/avahi-daemon:  
udp        0      0 0.0.0.0:111             0.0.0.0:*                          4649/portmap        
udp        0      0 0.0.0.0:34555           0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:635             0.0.0.0:*                          8208/portsentry     
udp        0      0 0.0.0.0:123             0.0.0.0:*                          6864/chronyd     


---

### Post by tgalati4 on 2008-03-29
Look in /var/log/auth.log for any strange activity.

---

### Post by InsektO on 2008-03-30
That list is weird, and I'm kind of a total noob here, but shoudn't you nmap yourself to your public (external) ip address, instead of 'localhost'?

---

### Post by kerry_s on 2008-03-30
hmm, i'm using custom debian etch/lenny.
pic->

---

### Post by mcduck on 2008-03-30
You shouldn't try running nmap on localhost. It's just normal that localhost ports are accessible from localhost.

To get any relevant information you need to run nmap from some other machine.

---

### Post by apokkalyps on 2008-03-30
Hmm I don't see why that should make a difference, but you're right, it does.  Which opens up a whole new can of worms.

I have opened a new thread to discuss my portsentry issues, (with a more relevant, less panicky title)

its here:
[http://ubuntuforums.org/showthread.php?p=4619284#post4619284](http://ubuntuforums.org/showthread.php?p=4619284#post4619284)

---

### Post by arvevans on 2008-03-30
It might be a good idea to show this thread as "CLOSED".  Hopefully, this thread will not be picked up by less knowledgeable persons and used to erroneously generate ideas that Linux is "full of Trojans".  You didn't really explain that the port mapper normally contains many pre-defined but inactive industry standard port assignments, or to explain that your application is what apparently added the unknown port responders.

Arv
_._

---

### Post by apokkalyps on 2008-03-30
yeah the title was a typo, it was supposed to say "**My** Ubuntu is filled with trojans", but its in stone now.

But you must not have read my whole post or you would have seen that I did put that explaination forward.
> [QUOTE]I thought my ubuntu had been infected by a bunch of trojans, but I just figured out this is portsentry. It dawned on me that nmap was probably just pulling the protocols on the ports it found open from a list and they may not actually be what its reporting them as. Nessus was unable to open the ports so that corroborated it. I uninstalled portsentry and it went back to the way the original nmap scan looked. I have now reinstalled it and the ports are open again. I think portsentry opens all these ports like a honeypot but the services arent there. It waits for attacks on them, logs it, and possibly takes action.[/QUOTE]

Also I didn't realize I had the power to close a thread, but I'll try to do that.

[COLOR="Red"]And If any newbies have any doubt, Ubuntu is not full of trojans!!![/COLOR]

---

### Post by arvevans on 2008-04-02
Re*:  Also I didn't realize I had the power to close a thread, but I'll try to do that.*

Under "Thread Tools" at the upper right of your initial post, the person who initiated the thread can change thread status.  Changing this to "SOLVED" allows searches to look for SOLVED or OPEN threads.  This helps find those still needing help.

Thanks,

Arv
_._

---

