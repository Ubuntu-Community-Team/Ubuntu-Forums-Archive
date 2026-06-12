---
title: "SSH port changing not work"
date: 2011-04-25
forum: Server Platforms
---

### Post by Whitedragon150 on 2011-04-25
Hi i have change in /etc/ssh/ssh_config my port to 333 and when i reload my ssh the port not change? I don't know why it not change?

---

### Post by pricetech on 2011-04-25
If you're trying to change the port number of the server, you'll have to edit /etc/ssh/sshd_config.

You need to use a port above 49152 also.

---

### Post by CharlesA on 2011-04-25
You can use whatever port you want. I don't know of any restrictions.

EDIT: Just remember to restart ssh after changing the port:

```
sudo service ssh restart
```

---

### Post by Whitedragon150 on 2011-04-25
I have tried but that not help? maybe is that i do it all in SSH?

---

### Post by CharlesA on 2011-04-25
> **Whitedragon150 said:**
> I have tried but that not help? maybe is that i do it all in SSH?
Are you editing the /etc/ssh/[COLOR="Blue"]sshd_config[/COLOR] file?

---

### Post by arrrghhh on 2011-04-25
Well, technically all ports below 1024 are **reserved**, however if you know there are no services running on your network using that port, then by all means use it.

I'm not sure why port 49152 was singled out, that doesn't make any sense to me.  I'd mirror the other comments tho, make sure you're editing the correct file, and always restart SSH after a change.

---

### Post by CharlesA on 2011-04-25
> **arrrghhh said:**
> Well, technically all ports below 1024 are **reserved**, however if you know there are no services running on your network using that port, then by all means use it.

Right. I thought that only root could make connections on ports below 1024, but I can't recall where I saw that.

---

### Post by pricetech on 2011-04-26
> **arrrghhh said:**
> 
I'm not sure why port 49152 was singled out.

Not singled out.  49152 to 65535 are Dynamic / Private ports, according to IANA.

Just like certain IPs are for private use.

Not saying the "port police" would knock down your door and beat you senseless, but why not use a port in the above range ??

and yes, restart ssh when your done.  I did leave that out.  My bad.

---

### Post by arrrghhh on 2011-04-26
Ah, I didn't realize that pricetech.  I just knew the ports below 1024 being 'reserved' for certain well-known purposes.  Learn something new every day, thanks ;).

---

### Post by stlsaint on 2011-04-27
> **Whitedragon150 said:**
> Hi i have change in /etc/ssh/ssh_config my port to 333 and when i reload my ssh the port not change? I don't know why it not change?
Hey bud you are editing the wrong file. You need to edit the 
```
/etc/ssh/sshd_config
``` on the server as stated above. Then as restart ssh. Also just ensure (insane stuff can happen on a server) that you havent tried setting 333 to be used by some other app! :popcorn:

---

### Post by Usa_Tony_Cuba on 2011-04-27
> **CharlesA said:**
> Right. I thought that only root could make connections on ports below 1024, but I can't recall where I saw that.
Right.. any port numbers below 1024 (the so-called "ports low numbers ") can only be bound by the superuser.. ( *see bind (2), tcp (7) and udp (7).*) This is so that our customers connecting to low numbered ports can be confident that the service running on the port is the standard implementation and not cheat service run by a user of the machine. The well-known port numbers specified by the [IANA]("www.iana.org/") is located This unique space is usually root.

---

### Post by CharlesA on 2011-04-27
> **Usa_Tony_Cuba said:**
> Right.. any port numbers below 1024 (the so-called "ports low numbers ") can only be bound by the superuser.. ( *see bind (2), tcp (7) and udp (7).*) This is so that our customers connecting to low numbered ports can be confident that the service running on the port is the standard implementation and not cheat service run by a user of the machine. The well-known port numbers specified by the [IANA]("www.iana.org/") is located This unique space is usually root.
Thanks. :)

---

