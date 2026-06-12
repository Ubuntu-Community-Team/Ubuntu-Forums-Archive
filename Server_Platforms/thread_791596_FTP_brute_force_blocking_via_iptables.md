---
title: "FTP brute force blocking via iptables"
date: 2008-05-12
forum: Server Platforms
---

### Post by dacool25 on 2008-05-12
I'm just trying to block other protocols besides ssh as directed in this [post]("http://ubuntuforums.org/showthread.php?t=791556"), and was wondering if this command would work for ftp:

```
sudo iptables -A INPUT -i eth0 -p tcp --dport 21 -m state --state NEW -m recent --set --name FTP
sudo iptables -A INPUT -i eth0 -p tcp --dport 21 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name FTP -j DROP
```

And also, do I just do the command again only with port 20, or can i specify that in the command?

---

### Post by SpaceTeddy on 2008-05-12
> **dacool25 said:**
> 
```
sudo iptables -A INPUT -i eth0 -p tcp **-m multiport --dports 20,21** -m state --state NEW -m recent --set --name FTP
sudo iptables -A INPUT -i eth0 -p tcp **-m multiport --dports 20,21** -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name FTP -j DROP
```


multiport should do the trick - please not that is is --dports not, not --dport.  This is just a guess tho - i've never blocked anything. i do know that multiport works tho :)

---

