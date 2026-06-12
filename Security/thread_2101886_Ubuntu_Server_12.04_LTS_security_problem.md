---
title: "Ubuntu Server 12.04 LTS security problem"
date: 2013-01-05
forum: Security
---

### Post by tdmtmanu on 2013-01-05
Hello,
I'm testing a virtual server with Ubuntu Server 12.04 LTS 64bit.
I want to use it as a web server.
I've set up a multiple sites with virtual hosts and all working perfectly.

But I have launched remotely, from another network, the simple command ApacheBench: ab-c 2000-n 100 [http://www.miosito.it/](http://www.miosito.it/)
and the command sent in complete crisis/crash the entire server, making inaccessible  all websites configured in it.
From the server console I can see CPU, RAM and swap to 100% and many many www-data process.
After 20 minutes the server return to normal utilization with few process.

I think it is a security setting that applies both to commands of this type, but also for other types of "attacks".

Someone can help me?
Thank you :)

---

### Post by samiux on 2013-01-06
> **tdmtmanu said:**
> Hello,
I'm testing a virtual server with Ubuntu Server 12.04 LTS 64bit.
I want to use it as a web server.
I've set up a multiple sites with virtual hosts and all working perfectly.

But I have launched remotely, from another network, the simple command ApacheBench: ab-c 2000-n 100 [http://www.miosito.it/](http://www.miosito.it/)
and the command sent in complete crisis/crash the entire server, making inaccessible  all websites configured in it.
From the server console I can see CPU, RAM and swap to 100% and many many www-data process.
After 20 minutes the server return to normal utilization with few process.

I think it is a security setting that applies both to commands of this type, but also for other types of "attacks".

Someone can help me?
Thank you :)

You do a stress test by ApacheBench for 2,000 concurrency with 100 requests connections each.  Your web server refused to response due to DoS.

To improve this situation, you need to increase the brandwidth and the amount of memory.  To further tune your web server, you need to do some changing on configuration files of PHP and MySQL, if any.

The ApacheBech can be used to perform DoS attack.  To avoid DoS, you can consider to install mod_evasive if you are using Apache.

To increase the security of your web server, you can consider to install ModSecurity (Web Application Firewall, WAF) which is designed for Apache, IIS7 and Nginx.

For the tutorial, you can refer to this [link](http://www.thefanclub.co.za/how-to/how-install-apache2-modsecurity-and-modevasive-ubuntu-1204-lts-server).

After installed those addons, the stress test cannot reveal the real ability of your web server.

Last word, be keep in mind that WAF cannot 100% protect your web server from being attacked.  The skilled attackers can bypass the WAF with ease.

Samiux

---

### Post by Doug S on 2013-01-06
The command as listed by the OP does not work for me:```
doug@s10:~/c$ ab -c 2000 -n 100 s15.smythies.com/
ab: Cannot use concurrency level greater than total number of requests
```so I am curious what actual command options were used.
 
In addition to the interesting stuff mentioned by samiux, you can also use iptables rules to limit connection rates. Example:```
sudo iptables -A INPUT -i eth0 -m state --state NEW -p tcp -m limit --limit 100/minute --limit-burst 20 --dport 80 -j ACCEPT
sudo iptables -A INPUT -i eth0 -m state --state NEW -p tcp --dport 80 -j DROP
``````
doug@s10:~/c$ ab -c 1000 -n 1000 s15.smythies.com/
This is ApacheBench, Version 2.3 <$Revision: 655654 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/
Benchmarking s15.smythies.com (be patient)
Completed 100 requests
apr_socket_recv: Connection timed out (110)
Total of 125 requests completed
doug@s10:~/c$

``````
doug@s15:~/c$ sudo iptables -v -x -n -L
Chain INPUT (policy ACCEPT 1335 packets, 83823 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     125     7500 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state NEW limit: avg 100/min burst 20 tcp dpt:80
    6079   364740 DROP       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state NEW tcp dpt:80
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy ACCEPT 1419 packets, 1292350 bytes)
    pkts      bytes target     prot opt in     out     source               destination

```

---

### Post by tdmtmanu on 2013-01-07
> **samiux said:**
> You do a stress test by ApacheBench for 2,000 concurrency with 100 requests connections each.  Your web server refused to response due to DoS.

To improve this situation, you need to increase the brandwidth and the amount of memory.  To further tune your web server, you need to do some changing on configuration files of PHP and MySQL, if any.

The ApacheBech can be used to perform DoS attack.  To avoid DoS, you can consider to install mod_evasive if you are using Apache.

To increase the security of your web server, you can consider to install ModSecurity (Web Application Firewall, WAF) which is designed for Apache, IIS7 and Nginx.

For the tutorial, you can refer to this [link](http://www.thefanclub.co.za/how-to/how-install-apache2-modsecurity-and-modevasive-ubuntu-1204-lts-server).

After installed those addons, the stress test cannot reveal the real ability of your web server.

Last word, be keep in mind that WAF cannot 100% protect your web server from being attacked.  The skilled attackers can bypass the WAF with ease.

Samiux

ModSecurity and mod_evasive is installed (configured and running), but not prevent this attack :\

---

### Post by tdmtmanu on 2013-01-07
> **Doug S said:**
> The command as listed by the OP does not work for me:```
doug@s10:~/c$ ab -c 2000 -n 100 s15.smythies.com/
ab: Cannot use concurrency level greater than total number of requests
```so I am curious what actual command options were used.

Sorry, the command is: ab -n 2000 -c 200 [http://www.miosito.it/](http://www.miosito.it/)

---

### Post by samiux on 2013-01-07
> **tdmtmanu said:**
> ModSecurity and mod_evasive is installed (configured and running), but not prevent this attack :\

Your box can or cannot defence of (D)DoS depend on many factors :

(1) the brandwidth of your connection;
(2) the amount of memory of the server;
(3) the ability of the web script code configuration setting, such as PHP.ini;
(4) the ability of the database configuration setting, such as MySQL.conf;
(5) the number of difference IP addresses that perform the attack;
(6) the number of requests per attacker's IP address (if HTTP based (D)DoS);
(7) the power of your CPU; 
(8) if the (D)DoS is performed via DNS: and 
(9) how the firewall/IDS/IPS/WAF handle the attacks

One more thing, you should keep in mind that if you perform the "ab" command to the victim from the attacker, you cannot examine the performance of the victim from the attacker as his IP address has been blocked/banned.  You should examine the performance of the victim with another IP address(es) or victim's localhost.

Samiux

---

