---
title: "[SOLVED] Is there a need for Anti Hacking Software to protect Ubuntu?"
date: 2008-05-15
forum: Security
---

### Post by Rytron on 2008-05-15
Hi,
Is there a need for Anti Hacking Software to protect Ubuntu?
Also if there is a need, is there any freeware Anti Hacking Software available for Ubuntu?
Thanks.

---

### Post by brian_p on 2008-05-15
> **Rytron said:**
> Hi,
Is there a need for Anti Hacking Software to protect Ubuntu?
Also if there is a need, is there any freeware Anti Hacking Software available for Ubuntu?
Thanks.

The likelihood of your receiving some useful responses would be increased if you would specify what it is you want to protect

---

### Post by Rytron on 2008-05-15
> **brian_p said:**
> The likelihood of your receiving some useful responses would be increased if you would specify what it is you want to protect

Well you see, I was listening to a radio program recently about personal computers being vulnerable to hackers. I refer to protecting all files on my pc.

---

### Post by Dr Small on 2008-05-15
Hackers are the good guys, crackers are the bad guys.
Anti-hacker software on Ubuntu? That is like saying, you want to buy the book without the pages..

---

### Post by hyper_ch on 2008-05-16
> **Rytron said:**
> Well you see, I was listening to a radio program recently about personal computers being vulnerable to hackers. I refer to protecting all files on my pc.

(1) As long as you are connected to an external network you are always vulnerable for being hacked... when you can access the internet, the internet can also access you

(2) What do you mean by "protecting all files on my pc"?

---

### Post by Rytron on 2008-05-16
> **hyper_ch said:**
> (1) As long as you are connected to an external network you are always vulnerable for being hacked... when you can access the internet, the internet can also access you

(2) What do you mean by "protecting all files on my pc"?

So I presume Ubuntu is much less prone to hackers than Windows or Mac. I mean by 'all files' - you know any files I create myself such as spreadsheets, text files, etc.

---

### Post by brian_p on 2008-05-16
> **Rytron said:**
> So I presume Ubuntu is much less prone to hackers than Windows or Mac. I mean by 'all files' - you know any files I create myself such as spreadsheets, text files, etc.

If you stick with packages from official Ubuntu sources 'much less prone' would become 'not prone'.

Executing

```
nmap -sT -p 20-65535
```

will give you some idea about which ports are open on the machine. You could even post the output here if you wish.

---

### Post by Rytron on 2008-05-16
> **brian_p said:**
> If you stick with packages from official Ubuntu sources 'much less prone' would become 'not prone'.

Executing

```
nmap -sT -p 20-65535
```

will give you some idea about which ports are open on the machine. You could even post the output here if you wish.


As requested:
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-16 15:04 IST
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.124 seconds
```

---

### Post by Monicker on 2008-05-16
If you are running from the machine you want to scan
```

nmap -sT -p 20-65535 localhost
```


From another machine

```
nmap -sT -p 20-65535 192.168.1.100
```


Obviously you should change the ip address in the second example to match the actual address of your machine.

I would also recommend a scan from outside your network, directed at the public ip address of the gateway.

---

### Post by brian_p on 2008-05-16
> **Rytron said:**
> As requested:
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-16 15:04 IST
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.124 seconds
```

Apologies, I forgot bthe target. That should be

```
nmap -sT -p 20-65535 localhost
```

---

### Post by Monicker on 2008-05-16
> **Jiraya said:**
> Does anybody knows what exactly nmap do? I mean, how it works?

Its a feature rich port scanner.  Check the description in Synaptic, or run "apt-cache show nmap" from a terminal.

---

### Post by Rytron on 2008-05-16
> **brian_p said:**
> Apologies, I forgot bthe target. That should be

```
nmap -sT -p 20-65535 localhost
```

Heres my output:

```
:~$ nmap -sT -p 20-65535 localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-16 15:56 IST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.067 seconds
```

---

### Post by brian_p on 2008-05-17
> **Rytron said:**
> Heres my output:

```
:~$ nmap -sT -p 20-65535 localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-16 15:56 IST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.067 seconds
```

Not really the output I'd expect but I still think you can be confident your files are safe.

---

