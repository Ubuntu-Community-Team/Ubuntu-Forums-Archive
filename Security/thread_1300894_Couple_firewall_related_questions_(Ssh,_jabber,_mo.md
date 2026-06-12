---
title: "Couple firewall related questions (Ssh, jabber, mounting)"
date: 2009-10-25
forum: Security
---

### Post by kartal on 2009-10-25
Hi
Yesterday I have installed Firestarter. it is a nice an easy application to use. However after installing FS Sshfs mounting, jabber client(kopete), samba mounting etc all stopped working. I believe I have enabled all the protocols for inbound and outbound traffic for lan ips ,like 

5222 for jabber
139 for samba
22 for Sshfs

For some reason opening these ports wont help me at all. Is there anything else I need to do to enable these services back ? Disabling the firewall gives me all those services back in place, so I am %100 sure that it is the FS causing the malfunction or non functioning.


thanks

---

### Post by sasho_zl on 2009-10-25
Try configuring the Netfilter with GUFW.

---

### Post by lovinglinux on 2009-10-25
Get rid of Firestarter and install [gufw](apt:gufw).

---

### Post by Lars Noodén on 2009-10-25
You can watch the connections with netstat or tcpdump:

```

# show all tcp connections, continuously
netstat -nt -c

# show all traffic on eth0
sudo tcpdump -i

# assuming ip# *xx.yy.zz.aa*:

# show all incoming traffic on eth0 
tcpdump -i eth0 ip dst *xx.yy.zz.aa*

# show all outgoing traffic on eth0
tcpdump -i eth0 ip src *xx.yy.zz.aa*

```

---

### Post by lovinglinux on 2009-10-25
> **Lars Noodén said:**
> You can watch the connections with netstat or tcpdump:

```

# show all tcp connections, continuously
netstat -nt -c

# show all traffic on eth0
sudo tcpdump -i

# assuming ip# *xx.yy.zz.aa*:

# show all incoming traffic on eth0 
tcpdump -i eth0 ip dst *xx.yy.zz.aa*

# show all outgoing traffic on eth0
tcpdump -i eth0 ip src *xx.yy.zz.aa*

```

I use [iptstate](apt:iptstate)

---

### Post by kartal on 2009-10-25
Hi

Thank you for the suggestions. I am going to try all now.

---

### Post by kartal on 2009-10-26
Hi
After uninstalling Firestarter and installing Gufw, Kopete stopped connecting even if there is no firewall gui running. So I ended up installing Firestarter again, I suppose Gufw is not enabling or disabling whatever FS had changed during its initial running. So I am stuck with FS and I need to manually start FS and disable firewall to connect jabber. I know does not make sense but this is the only solution I could come up with. Any suggestions to totally get rid  of FS?

thanks

---

### Post by lovinglinux on 2009-10-27
> **kartal said:**
> Hi
After uninstalling Firestarter and installing Gufw, Kopete stopped connecting even if there is no firewall gui running. So I ended up installing Firestarter again, I suppose Gufw is not enabling or disabling whatever FS had changed during its initial running. So I am stuck with FS and I need to manually start FS and disable firewall to connect jabber. I know does not make sense but this is the only solution I could come up with. Any suggestions to improve or gotally scraping FS and its settings?

thanks

I guess you need to purge Firestarter, instead of just removing it:

```
sudo apt-get purge Firestarter
```

Also, try to cleaning the iptables before starting gufw, to make sure there are no Firestarter left-overs:

```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

---

### Post by kartal on 2009-10-28
thanks, I think that resolved my problem here.

---

