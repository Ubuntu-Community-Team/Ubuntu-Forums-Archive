---
title: "Cron job for ifconfig"
date: 2008-08-25
forum: Server Platforms
---

### Post by dlichterman on 2008-08-25
Hey everyone-

Ive got a server here on campus running ubuntu, and a few times I believe the school network went down, and with everything plugged in the server basically never showed back up on the network, but was still running and everything.  I was thinking of maybe doing a nightly cron job that will "reset" the internet connection.  Should I just have it call a bash script with:
```

ifconfig eth0 down
ifconfig eth0 up

```
Or similar?  Is there a better command like restarting networking? Would that be:
```

/etc/init.d/networking restart

```

Thanks for the help everyone

-Daniel

---

### Post by kamui0523 on 2008-08-25
```
/etc/init.d/networking restart
```
This is better.
Do you know what`s the problem with your server?cable?NIC? or router?

---

### Post by Benismyhorse on 2008-08-25
Yea I think that the Command
```
/etc/init.d/networking restart
```
I think it would be better:)

---

