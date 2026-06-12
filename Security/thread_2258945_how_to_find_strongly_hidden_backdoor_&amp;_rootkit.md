---
title: "how to find strongly hidden backdoor &amp; rootkit  &amp;  port"
date: 2014-12-31
forum: Security
---

### Post by mahmodifard on 2014-12-31
hello . how to find rootkit ? wich is better chkrootkit  or rkhunter ? whats the benefit of them ?  how to find hidden procesand port ? ho to use unhide for this purpose ?how to scan  system,s log to find ip and action,s of hacker ?

---

### Post by mahmodifard on 2015-01-01
im scan my system in this way :
scan with rkhunter :
```
   sudo apt-get install rkhunter     
  sudo rkhunter --versioncheck
sudo rkhunter --update
sudo rkhunter -c
sudo gedit /var/log/rkhunter.log
```

scan ports :
```
 sudo netstat -antu -p
```
list of proces :
```
 sudo   ps -e
```
list of hide proces :
```
sudo  apt-get  install   unhide 
sudo  unhide-posix proc
 sudo unhide-posix sys 

```
view log,s
```
 sudo gedit   /var/log/dpkg.log
sudo gedit  /var/log/daemon.log
 sudo gedit    /var/log/user.log


```
check  Repository
```
 grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

is that true ?  do you can scan easyer and better than this ?  its take long thime .

---

### Post by fugu2 on 2015-01-07
any action you take from a compromised machine can be subverted. If you think this backdoor is being remotely accessed, then I suggest using a 2nd "clean" computer to sniff data traveling to/from the infected computer. If the has a wifi card, then you'll need a wifi card on your clean computer with monitor mode access. If the infected computer has an ethernet port then you'll need a network tap device or a pair of ethernet cards on the clean computer. then dump pcap using software like wireshark or tcpdump. Look for data that is out of the ordinary.

---

### Post by Habitual on 2015-01-07
> **mahmodifard said:**
> how to find hidden procesand port ? ho to use unhide for this purpose ?how to scan  system,s log to find ip and action,s of hacker ?
[Fishing for Hackers: Analysis of a Linux Server Attack - Part I]("http://draios.com/fishing-for-hackers/")
[Fishing for Hackers: Analysis of a Linux Server Attack - Part II]("http://draios.com/fishing-for-hackers-part-2/")
[How to monitor and troubleshoot a Linux server using sysdig]("http://xmodulo.com/monitor-troubleshoot-linux-server-sysdig.html")

Good luck.

---

### Post by HermanAB on 2015-01-08
It depends on how paranoid you are.

If you are very worried about a machine, then you could set up an external firewall with strong rules that will only allow connections to specific IP addresses and ports and then look at the packets that are getting dropped.

---

