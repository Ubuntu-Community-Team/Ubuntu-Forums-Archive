---
title: "iptables help"
date: 2010-05-12
forum: Server Platforms
---

### Post by LGX on 2010-05-12
serv: 10.4   x64
 
 
Hi all,
 
I been trying to figure this out but my iptables does not save after a reboot.  Is there an another way to do this or use a simple command line or even a firewall.
 
I was trying to follow this but it does not save after a reboot.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
 
 
Any help would be great.
 
Thank you

---

### Post by benderisgreat on 2010-05-12
you could make it independent from the network scripts by starting up the script independently like so:

have file at /etc/init.d/iptables that contains atleast:
```
#!/bin/sh
iptables-restore < /etc/iptables.rules
```
make it executable:
```
sudo chmod +x /etc/init.d/iptables
```
and then make a startup link:
```
sudo ln -s ../init.d/iptables /etc/rcS.d/S39iptables
```

# edit
this will load the rules you saved in /etc/iptables.rules.
if you change the rules run ```
sudo sh -c "iptables-save > /etc/iptables.rules"
``` or the changes won't be saved.

---

