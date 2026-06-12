---
title: "[psad-status] firewall setup warning ......How to fix this ?"
date: 2014-06-08
forum: Security
---

### Post by linuxyogi on 2014-06-08
Hi,

I have done the following and restarted the psad service.

```
		 		
[LIST=1]sudo ufw logging on
sudo iptables -A INPUT -j LOG
sudo iptables -A FORWARD -j LOG
sudo ip6tables -A INPUT -j LOG
sudo ip6tables -A FORWARD -j LOG
[/LIST]

 		

``` 

But I am getting the following email repeatedly.

> 		 		
[LIST=1][-] You may just need to add a default logging rule to the /sbin/iptables
    'filter' 'INPUT' chain on 1.rambo.com.  For more information,
    see the file "FW_HELP" in the psad sources directory or visit:
 
    [http://www.cipherdyne.org/psad/docs/fwconfig.html](http://www.cipherdyne.org/psad/docs/fwconfig.html)
 
[-] You may just need to add a default logging rule to the /sbin/ip6tables
    'filter' 'INPUT' chain on 1.rambo.com.  For more information,
    see the file "FW_HELP" in the psad sources directory or visit:
 
    [http://www.cipherdyne.org/psad/docs/fwconfig.html](http://www.cipherdyne.org/psad/docs/fwconfig.html)
[/LIST]

 		



How to fix this ?

---

### Post by linuxyogi on 2014-06-12
_**Solution**_


[LIST=1]
[*]Open /etc/ufw/before.rules and type before the COMMIT directive:
*-A INPUT -j LOG*
*-A FORWARD -j LOG*
[*]Open /etc/ufw/before6.rules and type before the COMMIT directive:
*-A INPUT -j LOG*
*-A FORWARD -j LOG*
[*]Restart ufw by typing as root:
*ufw disable*
*ufw enable*
[/LIST]

---

### Post by cogset on 2014-07-02
Since I'm always getting that annoying warning in my mail,I've tried the above fix,so the last section of my /etc/ufw/before.rules now looks like that:
```
# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT


#added to fix psad warning 
-A INPUT -j LOG
-A FORWARD -j LOG

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT
```

and the same lines I've added to /etc/ufw/before6.rules as well.

The thing is,I keep getting the same warning message:
```
To: root@localhost
Subject: [psad-status] firewall setup warning on ubuntu-desktop!
From: root <root@ubuntu-desktop>

[-] You may just need to add a default logging rule to the INPUT chain on
    ubuntu-desktop.  For more information, see the file "FW_HELP" in
    the psad sources directory or visit:

    http://www.cipherdyne.org/psad/docs/fwconfig.html
```

Did I do this right? Is there something else I'm missing here?

---

### Post by linuxyogi on 2014-07-02
Try these if you already havent

sudo ufw logging on
sudo iptables -A INPUT -j LOG
sudo iptables -A FORWARD -j LOG
sudo ip6tables -A INPUT -j LOG
sudo ip6tables -A FORWARD -j LOG

---

### Post by cogset on 2014-07-03
Thanks,since I'm admittedly not familiar at all with iptables,is there a way to add this rules using ufw or editing /etc/ufw/before.rules again?

---

### Post by linuxyogi on 2014-07-03
> **cogset said:**
> Thanks,since I'm admittedly not familiar at all with iptables,is there a way to add this rules using ufw or editing /etc/ufw/before.rules again?

Just copy and paste those line one by one. I have never modified iptables directly either.

One more thing, if you are behind a router's firewall it is very unlikely that you will get a port scan notification. 

I used it for like 3 months but didn't get a single alert.

---

### Post by cogset on 2014-07-07
Thanks,I take you do mean copy/paste these lines in  /etc/ufw/before.rules again?

As for the observation about the router,I think you may be right:I don't have a proper router firewall (say iptables),yet so far the only devices scanning my computer have been the ones on the same network,like printers or tablets,in other word stuff downstream the router itself.

---

### Post by bashiergui on 2014-07-08
> Thanks,I take you do mean copy/paste these lines in /etc/ufw/before.rules again?No. Paste them one line at a time into a terminal.

---

