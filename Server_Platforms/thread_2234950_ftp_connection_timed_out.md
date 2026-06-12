---
title: "ftp connection timed out"
date: 2014-07-17
forum: Server Platforms
---

### Post by delanov on 2014-07-17
I'm attempting to ftp to another computer within my home. From MINT 11 >> vsftpd will ftp to UBUNTU 14.04. However, UBUNTU 14.04 >> vsftp does not ftp to MINT 11.

I run the following four codes on UBUNTU. I need help deciphering the results, and would appreciate all input.  I cannot see any reference to port 20 0r 21 ???


(1) root@ddval-p6653w:~# nmap -Pn 192.168.x.xxx

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2014-07-17 19:01 PDT
Nmap scan report for 192.168.x.xxx
Host is up (0.0035s latency).
Not shown: 999 filtered ports
PORT STATE SERVICE
22/tcp open ssh[sudo] password for ddval:
Nmap done: 1 IP address (1 host up) scanned in 5.55 seconds

(2) ddval@ddval-p6653w:~$ sudo iptables -L -n

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination


(3) ddval@ddval-p6653w:~$ netstat -tlpn

root@ddval-p6653w:~# netstat -tlpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 127.0.1.1:53 0.0.0.0:* LISTEN 1125/dnsmasq
tcp 0 0 0.0.0.0:21 0.0.0.0:* LISTEN 876/vsftpd
tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN 873/sshd
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 1668/cupsd
tcp 0 0 0.0.0.0:445 0.0.0.0:* LISTEN 574/smbd
tcp 0 0 0.0.0.0:139 0.0.0.0:* LISTEN 574/smbd
tcp6 0 0 :::22 :::* LISTEN 873/sshd
tcp6 0 0 ::1:631 :::* LISTEN 1668/cupsd
tcp6 0 0 :::445 :::* LISTEN 574/smbd
tcp6 0 0 :::139 :::* LISTEN 574/smbd


(4) root@ddval-p6653w:~# ps -aux | grep -i ftp

root 876 0.0 0.0 4780 952 ? Ss 18:19 0:00 /usr/sbin/vsftpd
root 2687 0.0 0.0 4684 808 pts/0 R+ 18:45 0:00 grep --color=auto -i ftp

---

### Post by nerdtron on 2014-07-17
You're using iptables on Ubuntu?
Isn't it just easier to use UFW?

sudo ufw allow 21
sudo ufw allow 22
sudo ufw enable

---

### Post by delanov on 2014-07-17
> **nerdtron said:**
> You're using iptables on Ubuntu?
Isn't it just easier to use UFW?

sudo ufw allow 21
sudo ufw allow 22
sudo ufw enable

I've been on the fringe of Linux for a few years and still remain little more than a noob :-)  Just the other day I thought I would give the power of the computer a go and FTP fell victim.  Frankly, I could not tell you which is easer, but I surly appreciate your help and direction :-)

---

### Post by nerdtron on 2014-07-17
Even better, just for the sake of experimentation or if the computer is just on your home network, you can just disable the firewall entirely. If you do this and you have the correct settings on you vsftp configuration, then it should work.

---

### Post by TheFu on 2014-07-18
> **delanov said:**
> I've been on the fringe of Linux for a few years and still remain little more than a noob :-)  Just the other day I thought I would give the power of the computer a go and FTP fell victim.  Frankly, I could not tell you which is easer, but I surly appreciate your help and direction :-)

All Linux-based firewalls are iptables. The others are just a different front-end.

I'm more concerned about anyone using **FTP**.  That protocol **should have died 15 yrs ago** for a number of reasons. It is like telnet.  You have ssh running already, so just use an sftp client.  There are lots of nice clients for every platform, it will be secure since passwords aren't transmitted as plain text.  If you use Windows - WinSCP is a nice client. There are others.  The commands map 1-for-1 to old-school FTP (by design), so there isn't anything new to learn.  Plus the 3 main FTP servers have each had back doors inserted in their source code over the years - I think it happened to 1 of them twice.  Just for clarification, nobody has announced any back doors in the current FTP servers that I know.  Also - about the only organizations that should still be using FTP are those that want so share all files on the system with the entire world and don't care who grabs the files.  FTP doesn't usually play nice with firewalls either.

On my home network when NFS isn't available between the systems, I usually use scp or rsync with ssh-key-based authentication.  It is very convenient - much more than FTP or sftp.  OTOH, I've been called "odd", so I can completely understand folks using sftp between their Windows and unix-like systems.  If you need lots of easy access from Windows, then CIFS (samba) which has next to ZERO security is what most organization use.  Just to be fair, NFS can be configured with low security and no encryption too.  Neither NFS nor CIFS should be used over the internet (at least without a good VPN).

If you just want to share files with the entire world, use http.  If authenticated logins are needed, then scp/sftp are what you want.  FTP should have been killed off years ago.

---

### Post by delanov on 2014-07-18
> **TheFu said:**
> All Linux-based firewalls are iptables. The others are just a different front-end.

I'm more concerned about anyone using **FTP**.  That protocol **should have died 15 yrs ago** for a number of reasons. It is like telnet.  You have ssh running already, so just use an sftp client.  There are lots of nice clients for every platform, it will be secure since passwords aren't transmitted as plain text.  If you use Windows - WinSCP is a nice client. There are others.  The commands map 1-for-1 to old-school FTP (by design), so there isn't anything new to learn.  Plus the 3 main FTP servers have each had back doors inserted in their source code over the years - I think it happened to 1 of them twice.  

If you just want to share files with the entire world, use http.  If authenticated logins are needed, then scp/sftp are what you want.  FTP should have been killed off years ago.

Thank you.  I'll turn my attention to ssh.

---

### Post by delanov on 2014-07-18
> **nerdtron said:**
> Even better, just for the sake of experimentation or if the computer is just on your home network, you can just disable the firewall entirely. If you do this and you have the correct settings on you vsftp configuration, then it should work.

Thank you. TheFoo has recommended using SSH.  Filezilla is on the Ubuntu machine and supports the SSH protocol.  I need to put an SSH client on the mint machine -- provided it doesn’t already have one ??.  The system I am looking for is:  Move files between two house computers.  For the sake of curiosity I'll turn off the firewall to check the current settings as you suggest.  I've checked both machines vsftpd.conf files and they show the same settings.  It seems strange that the mint machine will connect to the ubuntu machine but the ubuntu machine will time-out when trying to connect to the mint machine.

---

### Post by delanov on 2014-07-18
> **nerdtron said:**
> Even better, just for the sake of experimentation or if the computer is just on your home network, you can just disable the firewall entirely. If you do this and you have the correct settings on you vsftp configuration, then it should work.

):PYES

Turning off ufw at both machines did the trick\\:D/

Thank you again, and I'll probably be back asking for more advice;)

---

