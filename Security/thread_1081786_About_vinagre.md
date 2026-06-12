---
title: "About vinagre"
date: 2009-02-26
forum: Security
---

### Post by zaikunzhang on 2009-02-26
I want to prohibit the IP XXX.XXX.X.XX from controlling my desktop through vinagre. How to achieve this? 

I have added 'vncserver:XXX.XXX.X.XX' in /etc/hosts.deny, but it does not work.

Your help is appreciated.  :p

---

### Post by bodhi.zazen on 2009-02-27
Do you wish to black list the ip entirely , or just from vinagre ?

blacklist : ```
sudo iptables -I INPUT 1 -s XXX.XXX.XX.XXX -j DROP
```If just from vinagre

```
sudo iptables -I INPUT 1 -s XXX.XXX.XX.XXX -p tcp --dport 5900:5910 -j DROP
```You can use iptables (as in the examples above), ufw, or if you wish a gui tool gufw or guarddog.

If you use iptables, you need to save and restore your changes.

```
sudo -c bash "iptables-save > /etc/iptables-save
```Now edit /etc/rc.local

```
gksu gedit /etc/rc.local
```Add this one line :

```
iptables-restore < /etc/iptables-save
```

---

### Post by The Cog on 2009-02-28
Just a correction to typos. If just from vinagre:
```
sudo iptables -I INPUT 1 -s XXX.XXX.XX.XXX -p tcp --dport 5900:5910 -j DROP
```

---

### Post by bodhi.zazen on 2009-02-28
Thanks The Cog, I edited my post as well.

---

### Post by zaikunzhnag on 2009-03-02
Thank you, bodhi.zazen and The Cog. Your help is highly appreciated. :P

If I want to black list all ip except ip1 and ip2, just from vinagre, how should I do? :confused:

Thanks.

---

### Post by bodhi.zazen on 2009-03-02
```
sudo iptables -I INPUT 1 -s good_ip_1[FONT=monospace] [/FONT]-p tcp --dport 5900:5910-j ACCEPT[FONT=monospace]
[/FONT]sudo iptables -I INPUT 2 -s good_ip_2[FONT=monospace] [/FONT]-p tcp --dport 5900:5910 -j ACCEPT[FONT=monospace]
[/FONT]sudo iptables -I INPUT 3 [FONT=monospace][/FONT]-p tcp --dport 5900:5910 -j DROP
```

Change "good_ip_1" and "good_ip_2" to the ip addresses you wish to allow.

---

### Post by zaikunzhang on 2009-03-05
> **bodhi.zazen said:**
> ```
sudo iptables -I INPUT 1 -s good_ip_1[FONT=monospace] [/FONT]-p tcp --dport 5900:5910-j ACCEPT[FONT=monospace]
[/FONT]sudo iptables -I INPUT 2 -s good_ip_2[FONT=monospace] [/FONT]-p tcp --dport 5900:5910 -j ACCEPT[FONT=monospace]
[/FONT]sudo iptables -I INPUT 3 [FONT=monospace][/FONT]-p tcp --dport 5900:5910 -j DROP
```

Change "good_ip_1" and "good_ip_2" to the ip addresses you wish to allow.

Thank you very much.

---

