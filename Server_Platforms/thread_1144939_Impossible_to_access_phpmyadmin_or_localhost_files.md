---
title: "Impossible to access phpmyadmin or localhost files offline!"
date: 2009-05-01
forum: Server Platforms
---

### Post by Aeren on 2009-05-01
Hello everyone.

Yesterday, I've installed my lamp server on my laptop. Everything went fine, and I got to fool around for a while with some php programming, accessing phpmyadmin and localhost folders without trouble.
However, now that my laptop isn't connected to internet, it seems that I'm not allowed to access phpmyadmin. It simply tells me that i'm in offline mode and can't access the page. The same happens with my localhost folders (except the one I used yesterday, which I can access through 127.0.0.1 but not through localhost - the other folders I can't acces either way).
Another thing I noticed is that if I change the folder I still can manage to access (adding a new file for example), it doesn't update through 127.0.0.1.

Does anyone have an explanation for this?

PS : I run on Ubuntu 8.04

---

### Post by nandemonai on 2009-05-01
Hmm, shouldn't need to be online to access localhost...

What's your /etc/hosts file look like?

---

### Post by Aeren on 2009-05-02
Here it is.

127.0.0.1	localhost
127.0.1.1	aromanch-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by daboroe on 2009-05-02
did you go going to: [http://aromanch-laptop](http://aromanch-laptop) ? That might work. Like I said **MIGHT **work.

---

### Post by Aeren on 2009-05-02
Doesn't work either :(

---

### Post by nandemonai on 2009-05-02
Very odd..

What about..

```
ping 127.0.0.1 -c 10
```

```
ping localhost -c 10
```

```
ping aromanch-laptop -c 10
```

---

### Post by Aeren on 2009-05-02
This is what I get.

127.0.0.1 :
10 packets transmitted, 10 received, 0% loss, time 8997ms
rtt min/avg/max/mdev = 0.038/0.040/0.044/0.007 ms

localhost :
10 packets transmitted, 10 received, 0% loss, time 8996ms
rtt min/avg/max/mdev = 0.038/0.041/0.044/0.007 ms

aromanch-laptop :
10 packets transmitted, 10 received, 0% loss, time 8995ms
rtt min/avg/max/mdev = 0.038/0.042/0.045/0.004 ms

---

### Post by nandemonai on 2009-05-02
That's not good.

Ok, how's about your /etc/network/interfaces file?

Should look something like this if you have no configured network card:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Make sure the loopback interface is in there as above. If not, add it and save.

```
sudo nano /etc/network/interfaces
```

Then restart networking.

```
sudo /etc/init.d/networking restart
```

---

### Post by Aeren on 2009-05-02
The file looks exactly the same, nothing more, nothing less :-?

---

### Post by Peasantoid on 2009-05-02
If you're using Firefox, I know what your problem is. Is File > Work Offline checked? If so, you can disable it permanently by going to about:config and setting toolkit.networkmanager.disable to true.

---

### Post by Aeren on 2009-05-02
Yay, it works! File > Work Offline was indeed checked. Thanks a lot :D

---

### Post by Peasantoid on 2009-05-02
No problem. :)

To this day I still don't know the purpose of "Offline Mode"...

---

### Post by nandemonai on 2009-05-02
Ok I should have thought of that. :P

Why then can't they ping the loopback device? A firewall shouldn't block that even...

---

