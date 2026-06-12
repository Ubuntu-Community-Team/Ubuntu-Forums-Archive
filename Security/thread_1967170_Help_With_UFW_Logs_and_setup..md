---
title: "Help With UFW Logs and setup."
date: 2012-04-27
forum: Security
---

### Post by Bushflyr on 2012-04-27
I have a UFW question that I can't seem to find the answer to in my searching. 

My UFW rules are:
```
Status: active

     To                         Action      From
     --                         ------      ----

[13] 5353/udp                   ALLOW IN    192.168.1.0/24
[14] 5353/udp                   ALLOW OUT   192.168.1.0/24 (out)

```


In my UFW log file I have:

```
Apr 27 11:20:23 mars kernel: [   16.659653] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=398 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=358 

```

Why is it being blocked? Should it be blocked? And, how can I fix it so it's not throwing an error to the log file?

I do have Avahi set up. I use it for sharing files between my Mac and the server.

---

### Post by Ms. Daisy on 2012-04-28
Your log shows the traffic on IPv6 and your rule is for IPv4. Perhaps if you write a rule for IPv6 it will stop blocking it.

---

### Post by Bushflyr on 2012-04-29
OK, thanks. I'll give that a try. How would I go about translating that to an IPv6 rule?

---

### Post by Ms. Daisy on 2012-04-29
Well if you're not certain about IP addressing, then you can install GUFW. When you write a rule in GUFW it will create identical ones for IPv4 and for IPv6.

---

### Post by uRock on 2012-04-29
Moved to *Security Discussions*

---

### Post by Bushflyr on 2012-04-29
I'm don't follow. :confused:  I don't think I can use GUFW since I have no GUI. No mouse, screen, or keyboard, for that matter. :p

I created that rule initially in UFW so I can use Avahi to share folders only on my LAN.  Do I need to create an equivalent rule with IPv6? If so, why is my LAN using IPv6 and what is the v6 equivalent to 192.168.1.0/24?

Thanks for the help, I really appreciate it. And sorry for my n00bness. Use small words, please.

---

