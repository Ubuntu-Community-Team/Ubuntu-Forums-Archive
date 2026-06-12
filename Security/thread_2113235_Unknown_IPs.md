---
title: "Unknown IPs"
date: 2013-02-06
forum: Security
---

### Post by kosken on 2013-02-06
When I run the command: 

```
netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c|sort -nk 1
```

It shows these IPs: 

1 142.30.225.226 ("Province of British Columbia" No clue)
1 91.189.94.25 ("Canonical" I guess that's Ubuntu's servers)
1 99.147.138.28 ("SBC Internet Services" No Clue)
2
13 xx.xx.xx.xx (This ip I recognized as myself)
300 127.0.0.1


I honestly dont even know what the command does but read online that this is how you check if you are being attacked? Should I be worried?

---

### Post by CharlesA on 2013-02-06
Why are you running a command if you don't even know what it does?

It is listing all the connections you have to port 80 - http. Why do you think this is an attack?

It only tells you what servers you are connected to on port 80, which is regular web traffic. I do not know how this would detect an "attack."

```
netstat -plan|grep :80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1323/apache2
tcp        1      0 192.168.1.30:33590      91.189.89.144:80        CLOSE_WAIT  1955/ubuntu-geoip-p
tcp        1      0 192.168.1.30:53304      91.189.94.25:80         CLOSE_WAIT  2736/ubuntu-geoip-p

```

```

netstat -plan|grep :80|awk {'print $5'}
0.0.0.0:*
91.189.89.144:80
91.189.94.25:80

```

```
netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1
0.0.0.0
91.189.89.144
91.189.94.25

```

```
netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c
      1 0.0.0.0
      1 91.189.89.144
      1 91.189.94.25

```

```
netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c|sort -nk 1
      1 0.0.0.0
      1 91.189.89.144
      1 91.189.94.25

```

---

### Post by cariboo on 2013-02-06
The command only tells you what web sites you are connected to.

---

### Post by CharlesA on 2013-02-06
> **cariboo907 said:**
> The command only tells you what web sites you are connected to.

You said that better than I did. :)

---

### Post by kosken on 2013-02-06
Ok thanks for the reply, so the question is why am I connected to IP 1 and 3?

---

### Post by sandyd on 2013-02-06
> **kosken said:**
> Ok thanks for the reply, so the question is why am I connected to IP 1 and 3?

You are probably downloading something from those IP Addresses (I.e. visiting webpage, firefox addons, .etc .etc). There are an infinite amount of things that access port 80.

---

### Post by kosken on 2013-02-06
Understood, that actually makes sense. I can see how that long command can possibly show you if your server is being attacked by listing all the IP addresses connected to you trying to cause an overload. Thx for everyone's time

---

### Post by CharlesA on 2013-02-06
> **kosken said:**
> Understood, that actually makes sense. I can see how that long command can possibly show you if your server is being attacked by listing all the IP addresses connected to you trying to cause an overload. Thx for everyone's time

It does not show connections to your computer, it shows connections **from** your computer.

Port 80 is used whenever you visit a web page or download a file, so there is no way this command can tell if your computer is being attacked or not.

Where did you find the command originally?

I only found one page that lists a similar command and says it can detect potential security issues and it can be found here:
[http://vnluck.com/2011/03/system-security-with-netstat/](http://vnluck.com/2011/03/system-security-with-netstat/)

It sounds like they are trying to see which machines are connected to their machine via port 80. You are trying to use it to see what machines you are connecting to via port 80.

This is what one of the commands they listed returned on my web dev box:

```
netstat -ant | awk '{print $6}' | sort | uniq -c | sort -n
      1 CLOSE_WAIT
      1 established)
      1 ESTABLISHED
      1 Foreign
      7 LISTEN

```

---

### Post by cariboo on 2013-02-08
The address you show could be any of the hundreds of web sites that Province of BC hosts anything from tourism to road conditions to jobs.

SBC Internet does business as AT&T so again it could be almost any web site you were browsing at the time you ran the command.

---

