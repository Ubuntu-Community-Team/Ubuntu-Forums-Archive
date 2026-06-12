---
title: "ports all open"
date: 2009-07-11
forum: Security
---

### Post by 2j4ez on 2009-07-11
Hello I was downloading the other day and I noticed my firewall going nuts.

The blue circle on firestarter kept going red saying i was hit and it gave me a ip address

I done a nmap localhost it came up with all ports open. should I be worried about this? Can these be closed?

Please help thanks for your time

---

### Post by ajgreeny on 2009-07-11
Do you really need firestarter at all?  If you are running a desktop system, and have no servers running, you probably do not need to make any changes at all to the default ubuntu setup.

By default ubuntu has no ports open and listening, it's only when you start something that requires a port to be opened, eg firefox, that the system will open the right port, and when you close that application the port will be closed again.

Firestarter is not the firewall, that is iptables, and I assume you must have opened some ports for them to actually be open, as you suggest they are.

If you want to go back to the ubuntu default state run the following in terminal to stop firestarter, if it's running, flush iptables and then restart networking with the new settings.
```
sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo /etc/init.d/networking restart
```

---

### Post by 2j4ez on 2009-07-11
Seems i keep getting hit when I have transmission open is this normal?
I closed transmission and have not been hit for 1/2 hour now

---

### Post by sasho_zl on 2009-07-11
It is normal. Transmission is a bittorrent client and other torrent applications are trying to make a connection on ports in the range of 50000 - 60000.

---

### Post by lovinglinux on 2009-07-11
> **2j4ez said:**
> Seems i keep getting hit when I have transmission open is this normal?
I closed transmission and have not been hit for 1/2 hour now

Other peers sharing the same file as you are trying to connect to your machine. You should open the port in the firewall, to allow Transmission to accept connections, otherwise the number of peers you connect will be reduced and your speed probably won't be as good as it could be.

---

### Post by The Cog on 2009-07-12
Or, unless you are running other services and have a list of IP addresses you want to block/allow, remove the firewall again. It is already interfering with your torrent transfers, and causing needless worry.

Linux isn't windows. If you don't want people to connect to a service, then don't install it. Unlike windows, Ubuntu by default isn't listening for incoming connections on any port. It only listens if you choose to install a service. If you installed a firewall, it has nothing to do because there are no services to protect. But if you do install a service (or run a torrent client), you then have extra work to do in re-opening that port in the firewall too. You are making completely pointless extra work for yourself.

---

### Post by ajgreeny on 2009-07-12
> **The Cog said:**
> Or, unless you are running other services and have a list of IP addresses you want to block/allow, remove the firewall again. It is already interfering with your torrent transfers, and causing needless worry.

Linux isn't windows. If you don't want people to connect to a service, then don't install it. Unlike windows, Ubuntu by default isn't listening for incoming connections on any port. It only listens if you choose to install a service. If you installed a firewall, it has nothing to do because there are no services to protect. But if you do install a service (or run a torrent client), you then have extra work to do in re-opening that port in the firewall too. You are making completely pointless extra work for yourself.
+1
As I said, a firewall is not normally needed in a standard desktop setup.  Only if you run servers do you normally need to do what you appear to have done.

---

