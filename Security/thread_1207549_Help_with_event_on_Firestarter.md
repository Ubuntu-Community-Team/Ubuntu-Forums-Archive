---
title: "Help with event on Firestarter"
date: 2009-07-08
forum: Security
---

### Post by Riddermark on 2009-07-08
Hi,
     I am new to Ubuntu, have been running it for about 1 month.  I have set up Firestarter to configure iptables and run it at all times.  Last night I had an event occur and would like some help in understanding what it means.

[B]Time:Jul  7 23:59:31 Direction: Unknown In:eth1 Out: Port:80 Source:97.107.130.239 Destination:192.168.1.2 Length:68 TOS:0x00 Protocol:ICMP Service:HTTP
[/B]
Firestartere is set up with defalts, except that ICMP filtering is enabled and no packets are allowed.

Thanks in advance for advice.

Kevin

---

### Post by lovinglinux on 2009-07-08
In:eth1  - incoming on [ethernet](http://en.wikipedia.org/wiki/Ethernet) 1
Out: - nothing here
Port:80 - incoming port used, usually related to http web traffic
Source: [97.107.130.239](https://ws.arin.net/whois/?queryinput=97.107.130.239) - is the IP of the computer requesting the connection
Destination:192.168.1.2 - is the IP of the computer receiving the connection, in this case yours
Length:68 - length of the packet being transmitted
TOS:0x00 - don't have a clue
Protocol:ICMP - protocol of the connection, in this case a "ping"
Service:HTTP - the type of service usually associated with the port used, in this case a web service

Are you running a web server? Is this the only connection?

I recommend reading the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial. The best way to protect your machine, is to understand how security works.

BTW, you shouldn't be running Firestarter all the time, due to security issues. Just configure the settings and close it. The iptables will still work on the background.

---

### Post by Riddermark on 2009-07-08
Thanks for the reply.  No, I am not running a web server.  I only have one connection running.  

I have been running firestarter all the time.  I have heard conflicting information about firestarter.  Are the iptables reset to default at shutdown?  If so do I need to run firestarter each time I boot?  Also, does the event log for firestarter work if it is not running?  Please excuse my ignorence about these issues, I am still trying to learn about linux.  I will also check out the tutoural you mentioned.  

Thanks

K

---

### Post by cariboo on 2009-07-08
You should only use Firestarter to set your firewall rules, once the program is closed the firewall still works. To check you rules after firestarter has closed, open a terminal and type:

```
iptables -L
```

the above command will print a listing on screen of your firewall rules.

---

### Post by lovinglinux on 2009-07-08
> **Riddermark said:**
> Thanks for the reply.  No, I am not running a web server.  I only have one connection running.  

Your connection log is showing someone checking if your port 80 responds to icmp requests. Since you don't have a web server, then there is nothing to worry about, even if your firewall was disabled.


> **Riddermark said:**
> Are the iptables reset to default at shutdown? 

You shouldn't need to start Firestarter each boot. I guess when you setup the iptables with Firestarer it does not reset iptables after reboot. Anyways, you can use the the command provided by cariboo to check the iptables. 

If you see just this:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    
```

Then it was reset. But if you see a bunch of other stuff, then you are still protected.

> **Riddermark said:**
> Also, does the event log for firestarter work if it is not running? 

Firestarter is not the firewall. It's just an graphical interface that allows you to easily create iptables (the real firewall) rules. It is also not responsible for logging connections. Everything is configured in the iptables, so if you close Firestarter everything will still work. Firestarter just loads the system logs when it starts and show them to you.

You can check your logs in the "System >>Administration >> Log File Viewer" or simply using a command like this:

```
tail -f /var/log/kern.log | grep [COLOR="Red"]**eth0**[/COLOR]
```

Where [COLOR="Red"]**eth0**[/COLOR] is your network card. This command will show you the contents of the kern.log file in real time, but will display only those lines containing the word [COLOR="Red"]**eth0**[/COLOR].

---

### Post by Riddermark on 2009-07-08
Thanks for the help.  I tried the command from cariboo907 and got the reply


[B]iptables v1.4.1.1: can't initialize iptables table `filter': Permission denied (you must be root)Perhaps iptables or your kernel needs to be upgraded.

[/B]Should I run the command as:

[FONT=monospace]
sudo iptables -L



[/FONT]

---

### Post by lovinglinux on 2009-07-08
> **Riddermark said:**
> 
[/B]Should I run the command as:

[FONT=monospace]
sudo iptables -L
[/FONT]

Yes, I missed that.

---

