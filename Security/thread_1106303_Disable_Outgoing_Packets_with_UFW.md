---
title: "Disable Outgoing Packets with UFW"
date: 2009-03-25
forum: Security
---

### Post by Hochler on 2009-03-25
I've read many tutorials and threads on UFW, but all they talk about are blocking incoming packets. Is there anyway to block outgoing packets with UFW, specifically port 80? If not, is there any other way to do it? I've used firestarter, but I need a quick CLI way to disable/enable outgoing packets on port 80.

---

### Post by bodhi.zazen on 2009-03-25
Not with ufw.

You can do it with iptables.

The nice thing about ufw, the rules for ufw are very similar for iptables.

See : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by lovinglinux on 2009-03-25
I guess there is an workaround that requires editing ufw config file, but then is not practical if you need to block/accept outgoing packets regularly.

These might be helpful 

[http://www.google.com.br/search?en-US:&q=ufw+block+outgoing+site%3Aubuntuforums.org](http://www.google.com.br/search?en-US:&q=ufw+block+outgoing+site%3Aubuntuforums.org)

[http://www.google.com.br/search?en-US:&q=ufw+block+outbound+site%3Aubuntuforums.org](http://www.google.com.br/search?en-US:&q=ufw+block+outbound+site%3Aubuntuforums.org)

---

### Post by xoros on 2010-05-11
Edit: nevermind, ufw does not seem to be able to do it.

I assume something like this would work:
```
sudo iptables -A OUTPUT -p tcp -m multiport --dports 80,8080,8081,443 -j DROP
```

And this to remove it when done:
```
sudo iptables -D OUTPUT -p tcp -m multiport --dports 80,8080,8081,443 -j DROP
```

---

### Post by bodhi.zazen on 2010-05-12
This is an old thread.

UFW will do this now :

```
sudo ufw deny out 80
```

see man ufw

```
sudo ufw delete deny out 80
```

To multiport use 

```
sudo ufw deny out 80,8080,8081,443/tcp
```

Your iptables rules will do this as well.

---

