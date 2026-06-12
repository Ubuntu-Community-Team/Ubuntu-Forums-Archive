---
title: "Question about UFW &amp; open ports"
date: 2018-01-28
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2018-01-28
Hi,

I have configured ufw to deny any incoming.

```
$ sudo ufw default deny
[sudo] password for xubuntu: 
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)

```

But still when I open torrent clients like transmission I see 


```
$ nmap 192.168.0.100 -p51413

Starting Nmap 7.60 ( https://nmap.org ) at 2018-01-28 19:15 IST
Nmap scan report for xubuntu (192.168.0.100)
Host is up (0.000056s latency).

PORT      STATE SERVICE
[COLOR=#ff0000]51413/tcp open  unknown
[/COLOR]
Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```

Isn't ufw suppose to close port 51413 unless I create a rule to allow it ?

---

### Post by howefield on 2018-01-28
Is this regarding Ubuntu 18.04 ?

---

### Post by linuxyogi on 2018-01-28
> **howefield said:**
> Is this regarding Ubuntu 18.04 ?

Extremely sorry, I completely forgot . Yes it is, please move it.

---

### Post by linuxyogi on 2018-01-29
Bump

---

### Post by dino99 on 2018-01-29
Have you glanced at: [https://ubuntuforums.org/showthread.php?t=823741](https://ubuntuforums.org/showthread.php?t=823741) ? or [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) ?

---

### Post by linuxyogi on 2018-01-29
> **dino99 said:**
> Have you glanced at: [https://ubuntuforums.org/showthread.php?t=823741](https://ubuntuforums.org/showthread.php?t=823741) ? or [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) ?


I have done  ```
$ sudo ufw deny  51413
```


```
 sudo ufw reload 
```



But with transmission open I am still getting

```
$ nmap 192.168.0.100 -p51413

Starting Nmap 7.60 ( https://nmap.org ) at 2018-01-29 17:38 IST
Nmap scan report for xubuntu (192.168.0.100)
Host is up (0.000082s latency).

PORT      STATE SERVICE
51413/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds


```

---

### Post by zika on 2018-01-29
> **linuxyogi said:**
> But I am getting this

```
$ sudo ufw deny port 51413
[sudo] password for xubuntu:
ERROR: Need 'to' or 'from' clause 
```
Word &#8222;port&#8220; is a placeholder where to put 51413...
Do think of choosing protocol to link to 51413 to deny...
Isn't bump a no-no here, especially in such a short time?

---

### Post by linuxyogi on 2018-01-29
@[**[COLOR=#000000]zika[/COLOR]**]("https://ubuntuforums.org/member.php?u=690937")      

Please see my edit.

---

### Post by SeijiSensei on 2018-01-29
Is it open if you scan it from other machines?

---

### Post by linuxyogi on 2018-01-29
> **SeijiSensei said:**
> Is it open if you scan it from other machines?

Unfortunately I have only 1 machine.

---

### Post by zika on 2018-01-29
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by linuxyogi on 2018-01-29
> **zika said:**
> [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Thanks but the fact is my ISP closes all ports. None of its customers can play online games. 

But the thing is they (my ISP) provides internet using ethernet cable (RJ45) so if a port is open

on my machine it is accessible from the local subnet.

---

