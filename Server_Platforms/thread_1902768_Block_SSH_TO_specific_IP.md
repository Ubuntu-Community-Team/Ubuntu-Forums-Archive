---
title: "Block SSH TO specific IP"
date: 2011-12-31
forum: Server Platforms
---

### Post by nathansoz on 2011-12-31
Ok, so I have a server that has three dedicated IP addresses. Two of these IP addresses are associated with a domain names (using apache), while the third IP is what I have some of the maintenance utilities on (eg. phpmyadmin). The setup looks like this:

xx.xx.xx.01-Domain1.com
xx.xx.xx.02-Domain2.com
xx.xx.xx.03-no public facing domain

I would like to only allow SSH connections to xx.xx.xx.03, while blocking any attempted connections to Domain1.com and Domain2.com

Is this possible?

---

### Post by Lars Noodén on 2011-12-31
It's unclear whether you mean IP number or host name in the example you provide.  If it is IP number then you can look at the directive [ListenAddress](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) in [font=Courier New]/etc/ssh/sshd_config[/font]  It works only with addresses not names.

---

### Post by rsvancara on 2012-01-01
In the file /etc/ssh/sshd_config, look for the line:

#ListenAddress 0.0.0.0

Uncomment this line and change it to the IP Address you want to bind too.  But be careful, you could lock yourself out of your system.  This basically says, what ip address do you want to bind the ssh daemon too.  

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by SeijiSensei on 2012-01-02
> **nathansoz said:**
> I would like to only allow SSH connections to xx.xx.xx.03, while blocking any attempted connections to Domain1.com and Domain2.com

You can do this with a pair of iptables rules:

```

iptables -A INPUT -p tcp -d xx.xx.xx.3 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j REJECT
```

---

### Post by fluca1978 on 2012-01-02
A simple boot script can help:

```

#!/bin/sh
ADDRESS_PREFIX="xx.xx.xx"
SSHPORT=22
IPTABLES_CMD=`which iptables`

for address in 01 02 03
do
    $IPTABLES_CMD -A INPUT -p tcp -d ${ADDRESS_PREFIX}.${address} --dport ${SSHPORT} -j ACCEPT
    $IPTABLES_CMD -A INPUT -p tcp --dport ${SSHPORT} -j DROP
done

```

---

