---
title: "CUPS and port 631"
date: 2011-09-23
forum: Security
---

### Post by Monery on 2011-09-23
Grettings all
I just moved my home printer over to my Ubuntu server and I am sharing it to my Windows PC's via CUPS.

Now my server also serves as my router so I used Steve Gibson's excellent Shields Up! site and I noticed that port 631 is open and listening to both the public and private sides of the machine. Is there a way to make CUPS only talk on one of the network adapters so I don't have to worry about someone on the net taking advantage of port 631 being open?

---

### Post by Dangertux on 2011-09-23
You can edit /etc/cupsd.conf

When you do this check your listen entries they should look like this

```

Listen 127.0.0.1:631
Listen 192.168.1.5:631

```Change them as appropriate and remove any you don't want cups listening on. Then restart cups

```

sudo /etc/init.d/cups restart

```

---

### Post by SeijiSensei on 2011-09-23
Is that the only open port that was found?  If there are more, you should be running an iptables firewall to block inbound access to services you want to limit to the internal network.

---

### Post by Monery on 2011-09-24
> **Dangertux said:**
> You can edit /etc/cupsd.conf

When you do this check your listen entries they should look like this

```

Listen 127.0.0.1:631
Listen 192.168.1.5:631

```Change them as appropriate and remove any you don't want cups listening on. Then restart cups

The file when opened with nano was blank

```

sudo /etc/init.d/cupsd restart

```

Running the following command then gave me
```
bash: /etc/init.d/cupsd: No such file or directory
```

---

### Post by emiller12345 on 2011-09-24
I think they ment ...```
$ sudo /etc/init.d/cups restart
```

---

### Post by debd on 2011-09-25
on localhost:631, goto the admin tab and click on Edit Configuration File

there's some options to set which hosts you want to listen to.

---

### Post by Monery on 2011-09-25
[SOLVED]
 
> **debd said:**
> on localhost:631, goto the admin tab and click on Edit Configuration File
 
there's some options to set which hosts you want to listen to.
 
 
I verifed that printing from the Internet was not checked and restarted CUPS. I still see the port open when running the shields up test on it. I hope unchecking the option for inet printing will be good enough

---

### Post by Dangertux on 2011-09-25
Yes I did mean cups , I will edit the initial post for clarity sake and anyone else who may read this in the future. Good catch.

```

sudo /etc/init.d/cups restart

```Also important to know, if you have a line that just say this in your cupsd.conf file it is the equivalent of Listen 0.0.0.0:631 (IE: Listen on all available interfaces) so you might want to check for that as well.

```

Listen 631

```If it still shows as accessible you can just block it from external access via iptables as SeijiSensei pointed out.

UFW 
```

sudo ufw deny from any to 192.168.1.5 port 631 proto tcp
sudo ufw allow from 192.168.1.0/24 to 192.168.1.5 port 631 proto tcp

```

OR

iptables
```

sudo iptables -A INPUT -s 192.168.1.0/24 -p tcp --dport 631 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 631 -j DROP

```Hope that helps a little bit.

---

