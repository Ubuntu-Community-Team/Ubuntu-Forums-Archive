---
title: "Apache2 running but can't view"
date: 2010-03-14
forum: Server Platforms
---

### Post by grapeape25 on 2010-03-14
I have had a LAMP setup on my computer for a while without any trouble but I have suddenly become unable to access it through either localhost or my IP address. I have tried removing and reinstalling the packages but it still doesn't work and the /var/log/apache2/error.log does not give me any errors. 

Here is my apache2.conf

[http://pastebin.com/mP77Kf6c](http://pastebin.com/mP77Kf6c)

Any help is appreciated.

---

### Post by Samatva on 2010-03-15
Check /etc/apache2/ports.conf - make certain Apache is listening.

Also, how do you know Apache is running (? ps -A ?)

---

### Post by grapeape25 on 2010-03-15
I have it listening on 80.

I know it is running because

> scott@scott-desktop:/$ sudo apache2ctl start
httpd (pid 31216) already running


---

### Post by Ryan Dwyer on 2010-03-15
You might have a firewall blocking the traffic so you can't even connect to it yourself. Or maybe your lo interface isn't functioning.

Try running these commands:
ping localhost
telnet 127.0.0.1 80

---

### Post by cdenley on 2010-03-15
```

sudo /etc/init.d/apache2 restart
sudo netstat -tlnp
sudo iptables -n -L INPUT
nc -z -v -w 5 127.0.0.1 80
echo -e "HEAD / HTTP/1.0\n"|nc 127.0.0.1 80

```

---

### Post by grapeape25 on 2010-03-15
Thanks everyone for the input. I was unable to ping my localhost but I flushed iptables and it works now:

iptables -F

Is this just a temporary fix or a permanent fix?

---

