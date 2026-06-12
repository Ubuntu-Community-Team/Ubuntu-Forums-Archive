---
title: "high open ports changing"
date: 2008-07-07
forum: Security
---

### Post by gagatz on 2008-07-07
Hi,
i have the following situation here, that i don't understand

when i'm doing the 'gnome-network-tools' open ports scan, it shows several open ports that i know about but also one or two or none high numbered
(35024 or so) open ports. Every time i repeat the search the results change. I'm not sitting behind a firewall and the computer happens to be a torserver also, but when i stop the torserver (or kill it) this open ports behaviour doesn't change.
how can i close these ports or know what applications are responsible for this?

thanx, gagatz

---

### Post by The Cog on 2008-07-07
sudo netstat -plnt
should give you the process IDs. Then use ps to find the details. Here is an example:
```
cog@Dingly:~$ sudo netstat -plnt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5096/cupsd
tcp6       0      0 :::22                   :::*                    LISTEN      5009/sshd
cog@Dingly:~$ ps -ef | grep 5009
root      5009     1  0 08:01 ?        00:00:00 /usr/sbin/sshd
cog      16416 16355  0 13:20 pts/4    00:00:00 grep 5009
cog@Dingly:~$ ps -ef | grep 5096
root      5096     1  0 08:01 ?        00:00:00 /usr/sbin/cupsd
cog      16428 16355  0 13:21 pts/4    00:00:00 grep 5096

```

---

### Post by brian_p on 2008-07-07
> **gagatz said:**
>  . . . . or know what applications are responsible for this?

One way:

```
sudo lsof -i :<port number>
```

(Without the angle brackets)

---

### Post by gagatz on 2008-07-07
thank you both, but this didn't provide any information:
i shut down the torserver to reduce the number of connections and now 

sudo netstat -plnt

yields 

PID/Program name   
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN     25219/privoxy       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5073/cupsd          
tcp6       0      0 :::80                   :::*                    LISTEN     6031/apache2        
tcp6       0      0 :::22                   :::*                    LISTEN     5003/sshd  

which is fine for me,
while doing the nettool search still shows these other open ports. The open ports change their number so rapidly that if i do two search really quick one after the other there are still different results...

the brian_p approach doesn't work either: 

lsof -i :

COMMAND     PID      USER   FD   TYPE  DEVICE SIZE NODE NAME
avahi-dae  5033     avahi   15u  IPv4   17441       UDP *:32770 
firefox-b 29020  username   42u  IPv4 8954739       TCP my.domainname.com:49040->a212-201-100-149.deploy.akamaitechnologies.com:www (ESTABLISHED)

but this is stable, the port numbers do not change.
My suspicion is, that the portnumbers change so quick, that these commands can't detect them?

do you have another idea?

---

### Post by brian_p on 2008-07-07
> **gagatz said:**
> 
lsof -i :

```
sudo lsof -i
```

---

### Post by gagatz on 2008-07-07
yes i've done this 
sudo lsof -i 
(otherwise it doesn't show anything)
also tried to pick randomly a port number and let it search for it very often:
sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293  ...
but didn't work :~|

---

### Post by brian_p on 2008-07-07
> **gagatz said:**
> yes i've done this 
sudo lsof -i 
(otherwise it doesn't show anything)
also tried to pick randomly a port number and let it search for it very often:
sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293 && sudo lsof -i:38293  ...
but didn't work :~|

netstat shows four listening processes but none of them show up in the lsof output, which is strange because that doesn't happen here.

---

### Post by gagatz on 2008-07-07
no its not too strange, since i entered the command

sudo lsof -i :20000-60000

so all the smaller ports are omitted

the purpose of the repeated command is to have lsof check very often for the same port, and since these seem to change all the time eventually this checked port will be open for a moment and since lsof is scanning for this one, output will be produced... didn't work grrrr

---

### Post by brian_p on 2008-07-07
> **gagatz said:**
> no its not too strange, since i entered the command

sudo lsof -i :20000-60000

so all the smaller ports are omitted

I don't have the GTK (the Gnome Telepathy Kit) service operative at present so port 999 on this machine is not open.

> the purpose of the repeated command is to have lsof check very often for the same port, and since these seem to change all the time eventually this checked port will be open for a moment and since lsof is scanning for this one, output will be produced... didn't work grrrr

I know how you feel.

---

### Post by Meson on 2008-07-07
> **gagatz said:**
> Every time i repeat the search the results change.

Try running the port scan without your web browser open.  You are probably seeing the ports that are temporarily opened for web pages.

---

