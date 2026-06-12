---
title: "squid on 8.04"
date: 2008-06-24
forum: Server Platforms
---

### Post by emada on 2008-06-24
I cant get squid to work on ubuntu 8.04. i got squid via apt-get and when i tryed to start it i got a fail message telling me to set "visible_hostname" so i did. and that made the init.d script work fine but i cant find the pid file in /var/run and it never opens the ports for squid

entering squid in the cl gave me an error saying it couldnt read from the squid.conf file due to permission issue so i chmod 777 /etc/squid/squid.conf and still no joy, any ideas?

---

### Post by windependence on 2008-06-24
> **emada said:**
> I cant get squid to work on ubuntu 8.04. i got squid via apt-get and when i tryed to start it i got a fail message telling me to set "visible_hostname" so i did. and that made the init.d script work fine but i cant find the pid file in /var/run and it never opens the ports for squid

entering squid in the cl gave me an error saying it couldnt read from the squid.conf file due to permission issue so i chmod 777 /etc/squid/squid.conf and still no joy, any ideas?

After you start squid, do this:

```
ps aux | grep squid
```

You should see two lines, one is you searching for the squid process and the other is the actual process itself. The process ID should be in that output. If you don't see it, it isn't starting.

On reading the squid.conf file did you try a:

```
cat /etc/squid/squid.conf
```

If you want to edit the file do this:

```
sudo nano /etc/squid/squid.conf
```

After making changes do a ctl+o (that's the letter o) and hit enter to save the file. It's a good idea to make a copy before you start editing. Good luck!

Oh, and it would be a good idea to change the permissions on the squid.conf file back to what they were after you finish editing. Leaving them world writable is not a good idea.

-Tim

---

### Post by emada on 2008-06-24
yes i had to edit squid.conf to set visible_hostname

---

### Post by emada on 2008-06-24
thanx windependence your tip worked

i can see it is running but still no pid and no open ports.

---

### Post by windependence on 2008-06-25
You should get a PID # when you do the ps command. can you post the ouput of:

ps aux | grep vsftpd

-Tim

---

