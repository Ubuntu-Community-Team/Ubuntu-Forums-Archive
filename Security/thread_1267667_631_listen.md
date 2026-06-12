---
title: "631 listen"
date: 2009-09-16
forum: Security
---

### Post by sopadeajo on 2009-09-16
doing a netstat i get: 
631 listen and udp ports 68, 49868 and 5353 without status.
I am a standalone computer not connected to any network.
Is 631 listening normal ?

---

### Post by slakkie on 2009-09-16
631 is cups iirc. 

```

grep 631 /etc/services
ipp             631/tcp                         # Internet Printing Protocol
ipp             631/udp

```

Yes, you have cupsd running? If so, yes, that is normal. But if you do an nmap from localhost you will see open ports, since cups might be listening only on 127.0.0.1 and not on your public interface.

---

### Post by rookcifer on 2009-09-16
> **sopadeajo said:**
> doing a netstat i get: 
631 listen and udp ports 68, 49868 and 5353 without status.
I am a standalone computer not connected to any network.
Is 631 listening normal ?

Yes, it is the CUPS daemon (for your printer).  It will only be listening locally, so no need for worry.

---

### Post by sopadeajo on 2009-09-16
> **rookcifer said:**
> Yes, it is the CUPS daemon (for your printer).  It will only be listening locally, so no need for worry.

Thank you, rookcifer, though i still think: why to listen if there is no local network at all?

---

### Post by i.r.id10t on 2009-09-16
Lots of things are network based, even if it is just localhost communication.  CUPS is one of 'em.

---

### Post by The Cog on 2009-09-16
> **i.r.id10t said:**
> Lots of things are network based, even if it is just localhost communication.  CUPS is one of 'em.

Yup. Printing from your PC to a locally connected USB printer still involves making a local connection from the printing application to the CUPS print server. It's a proper client/server connection, just within the one machine. Blocking it with firewall rules leaves you unable to print at all.

---

### Post by sopadeajo on 2009-09-16
> **The Cog said:**
> Yup. Printing from your PC to a locally connected USB printer still involves making a local connection from the printing application to the CUPS print server. It's a proper client/server connection, just within the one machine. Blocking it with firewall rules leaves you unable to print at all.

Thanks, The Cog.

I was worried because i have an old Lexmark 1100 which works fine , but It is not even connected to the computer. No printer connected to my computer. So, Ubuntu dedicates a port (631) to listen to your printer even though the printer is not connected. I must say that the printer has never been connected to this computer and no printer has ever been connected to .
But OK, i understand that most printers have a microprocessor inside to calculate printing tasks ans so it is not so odd that a printer might be considered as a kind of a slave computer.

---

### Post by cariboo on 2009-09-16
If you never plan to print from your Ubuntu computer, you can turn the cups server of by issuing the following command:

```
sudo update-rc.d -f cups remove
```

when you want to re-enable the cups server:

```
sudo update-rc.d cups defaults
```

then start the server:

```
sudo /etc/init.d/cups start
```

---

### Post by The Cog on 2009-09-17
Also, if you use the command **netstat -lnt** you will find that CUPS is listening on 127.0.0.1:631 and maybe ::1:631. These are the computers loopback addresses, and cannot be connected to from the outside world. You can of course configure CUPS to accept connections from other computers, but the default is not to so that the CUPS print server is private to that computer.

---

### Post by slakkie on 2009-09-17
> **cariboo907 said:**
> If you never plan to print from your Ubuntu computer, you can turn the cups server of by issuing the following command:

```
sudo update-rc.d -f cups remove
```

when you want to re-enable the cups server:

```
sudo update-rc.d cups defaults
```

then start the server:

```
sudo /etc/init.d/cups start
```If you never run it, you need to remove it.

---

