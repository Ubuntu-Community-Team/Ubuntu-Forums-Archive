---
title: "Can't close port 80"
date: 2014-01-26
forum: Security
---

### Post by SuperFreak on 2014-01-26
I noticed that I have Port 80 open and I am not sure what is using it. I tried to close it using the command ```
sudo ufw deny  80
``` and also through the graphical firewall interface (shows port denied but it is greyed out). How do I close this Port and How do I find out why it is open

Thanks

This may be a clue but I am not sure what it means```
david@MainSqueeze:~$ netstat -tulpn | grep :80
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp6       0      0 :::80                   :::*                    LISTEN      -               
david@MainSqueeze:~$ 

```

---

### Post by Old_Grey_Wolf on 2014-01-26
Port 80 is used for HTTP. You browser uses it for one thing.

---

### Post by SuperFreak on 2014-01-26
> **Old_Grey_Wolf said:**
> Port 80 is used for HTTP. You browser uses it for one thing.

Some time ago I tested my ports usig [Shield's Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") and all ports were in Stealth mode. Now Port 80 shows as open.  I am not sure I understand what has changed. Is HTTP and the use of port 80 needed for browsing the internet or can Port 80 be closed or at least put in stealth mode?

According to Bohdi.zazen Port 80 is used to run Apache. I will have to investigate further but I think there is a reason I need Apache to run

---

### Post by Doug S on 2014-01-26
If you inquire with root level, you can see what process is listening on port 80. Example:```
doug@doug-64:~$ [COLOR=#ff0000]netstat -tulpn | grep :80[/COLOR]
(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      [COLOR=#ff0000]-[/COLOR]
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat -tulpn | grep :80[/COLOR]
[sudo] password for doug:
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      [COLOR=#ff0000]1525/apache2[/COLOR]
```

---

### Post by SuperFreak on 2014-01-26
Right you are...Thanks
```
david@MainSqueeze:~$ sudo netstat -tulpn | grep :80
[sudo] password for david: 
tcp6       0      0 :::80                   :::*                    LISTEN      2456/apache2    
david@MainSqueeze:~$ 



```

Now I just have to determine whether I need Apache2

edit: Disabling and removing Apache2 did not seem to close port```
sudo apt-get remove apache2
```

---

### Post by bab1 on 2014-01-26
> **SuperFreak said:**
> Right you are...Thanks
```
david@MainSqueeze:~$ sudo netstat -tulpn | grep :80
[sudo] password for david: 
tcp6       0      0 :::80                   :::*                    LISTEN      2456/apache2    
david@MainSqueeze:~$ 



```

Now I just have to determine whether I need Apache2

edit: Disabling and removing Apache2 did not seem to close port```
sudo apt-get remove apache2
```
Are you sure Apache2 has been removed?  What do you get with this command```
dpkg -l apache2
```

Are you aware that the IP address you are listing is for IPv6?

---

### Post by Lars Noodén on 2014-01-26
Also, make sure to run any scans from a second machine.  Doing the scan from the same machine won't give meaningful results as different rules apply for the localhost.

---

### Post by SuperFreak on 2014-01-26
> **bab1 said:**
> Are you sure Apache2 has been removed?  What do you get with this command```
dpkg -l apache2
```

Are you aware that the IP address you are listing is for IPv6?

I think I wrecked the uninstall/purge of Apache2. This is what I get from the dpkg command
```
david@MainSqueeze:~$ dpkg -l apache2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache2        <none>         (no description available)
david@MainSqueeze:~$ 


```

I was'nt aware it was IPv6 and I am not sure what that might mean


@Lars Noodén Thanks. I don't think it is possible to use Shield's Up in that way but I am beginning to get the impression it is not of much value anyway. How would I scan for open Ports from a second computer?

---

### Post by bab1 on 2014-01-26
> **SuperFreak said:**
> I think I wrecked the uninstall/purge of Apache2. This is what I get from the dpkg command
```
david@MainSqueeze:~$ dpkg -l apache2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache2        <none>         (no description available)
david@MainSqueeze:~$ 


```

I was'nt aware it was IPv6 and I am not sure what that might mean


@Lars Noodén Thanks. I don't think it is possible to use Shield's Up in that way but I am beginning to get the impression it is not of much value anyway. How would I scan for open Ports from a second computer?

Apache2 is still installed.  If you want to get rid of apache2 you need to purge it.  Use this command and recheck```
sudo apt-get purge apache2
```

What @Lars Noodén is saying is you need 2 computers on the network to correctly test.  I'm not sure that it's really true, but that is what he is saying.

Here is what I get with netstat the localhost (the only machine on at this time)```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:58122           0.0.0.0:*               LISTEN      1146/rpc.mountd 
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      857/smbd      [COLOR="#FF0000"]<--Samba[/COLOR]  
tcp        0      0 0.0.0.0:49837           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      658/rpcbind    [COLOR="#FF0000"]<-- For NFS [/COLOR]    
tcp        0      0 0.0.0.0:38482           0.0.0.0:*               LISTEN      1146/rpc.mountd 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      884/sshd        [COLOR="#FF0000"]<-- SSH[/COLOR]        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1012/cupsd      
tcp        0      0 0.0.0.0:42971           0.0.0.0:*               LISTEN      1146/rpc.mountd [COLOR="#FF0000"]<-- For NFS [/COLOR] 
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      857/smbd         [COLOR="#FF0000"]<--Samba[/COLOR]  
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:51908           0.0.0.0:*               LISTEN      904/rpc.statd     [COLOR="#FF0000"]<-- For NFS [/COLOR]   

```

---

### Post by SuperFreak on 2014-01-26
Thanks Bab1. This is the result of another purge
```
david@MainSqueeze:~$ sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@MainSqueeze:~$ 


```

and then```
david@MainSqueeze:~$ dpkg -l apache2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache2        <none>         (no description available)
david@MainSqueeze:~$ 

```


Does "un apache2" indicate it is not known whether it is installed or not?

---

### Post by bab1 on 2014-01-26
> **SuperFreak said:**
> Thanks Bab1. This is the result of another purge
```
david@MainSqueeze:~$ sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@MainSqueeze:~$ 


```

and then```
david@MainSqueeze:~$ dpkg -l apache2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache2        <none>         (no description available)
david@MainSqueeze:~$ 

```


Does "un apache2" indicate it is not known whether it is installed or not?

I'm not sure, but I believe that the un = un-installed.   You can clear the apt cache but it is not really relevant to your "open ports" problem.  What do you get with ```
sudo netstat -tulpn |g 80
```  
We can also check to see if apache2 is running with this```
pgrep -l apache2
```

---

### Post by SuperFreak on 2014-01-26
```
david@MainSqueeze:~$ sudo netstat -tulpn |g 80
[sudo] password for david: g: command not found


```

perhaps it should be this?
```
david@MainSqueeze:~$ sudo netstat -tulpn | grep :80
[sudo] password for david: 
david@MainSqueeze:~$ 


```

and
```
david@MainSqueeze:~$ pgrep -l apache2
david@MainSqueeze:~$ 

```

appears appache2 is not there. Shield's Up still reports Port 80 Open but perhaps that is the wrong way to check. If I knew how to check from my other computer, as Lars suggested, I would

---

### Post by bab1 on 2014-01-26
> **SuperFreak said:**
> ```
david@MainSqueeze:~$ sudo netstat -tulpn |g 80
[sudo] password for david: g: command not found



```

perhaps it should be this?
```
david@MainSqueeze:~$ sudo netstat -tulpn | grep :80
[sudo] password for david: 
david@MainSqueeze:~$ 


```


Yes.  Sorry about that.  I aliased the grep command to g because I was using it a lot. 
> 

and
```
david@MainSqueeze:~$ pgrep -l apache2
david@MainSqueeze:~$ 

```

appears appache2 is not there. Shield's Up still reports Port 80 Open but perhaps that is the wrong way to check. If I knew how to check from my other computer, as Lars suggested, I would

That's because Your router is what Shield's Up is testing.  Your computer has no port 80 open.

---

### Post by SuperFreak on 2014-01-26
That's good. I wonder what changed in the router, firewall is on. Anyway Thanks for your help

edit: Unbeknowst to me port forwarding on the router had allowed taffic through Port 80. Disabled UPNP

---

### Post by Lars Noodén on 2014-01-27
> **SuperFreak said:**
> 
@Lars Noodén Thanks. I don't think it is possible to use Shield's Up in that way but I am beginning to get the impression it is not of much value anyway. How would I scan for open Ports from a second computer?

The usual tool would be [nmap](http://manpages.ubuntu.com/manpages/saucy/en/man1/nmap.1.html) or its graphical front-end, zenmap.  Basic nmap is easy to use, but if you look at the options in the manual page, you can see that you can take it quite far.

[http://www.linux.com/learn/tutorials/290879-beginners-guide-to-nmap](http://www.linux.com/learn/tutorials/290879-beginners-guide-to-nmap)
 
It will tell you which ports are open and a bit more.  If you have publicly facing services on the machine then you might consider OpenVAS, which will look for known weaknesses.

---

