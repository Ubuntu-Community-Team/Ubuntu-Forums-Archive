---
title: "Aircrack help"
date: 2008-11-08
forum: Security
---

### Post by XxBJDxX on 2008-11-08
If this is in the wrong section, i apologize..

i have searched high and low for an awnser for this...

I am have a minor problem using aircrack, 
first let me give you a quick run-down...

I am using a D-link WUA-1340 Wireless G USB stick.

I am running this off the backtrack 3 live cd.

The wireless card works with no problems at all.

all configurations check out (iwconfig, ifconfig).

The only thing that fails to work is the step where you have to use fake assosiation with the AP

aireplay-ng -1 0 -e networkname -9 00:00:00:00:00 -h 00:00:00:00:00 rausb0

after i enter that i get 
"attack mode already specified"

any help would be nice, ive been pulling my hair out.

i might add that everything else in the process works fine...airodump, aircrack, airmon and the OTHER airodump all go fine, just this one step that has got me stumped.....

---

### Post by pytheas22 on 2008-11-08
It sounds like either a bug with aircrack, or possibly some oddity with your wireless driver.  I've never been able to get fake-authentication to work either (although for different reasons), even though all the other attacks work fine, using the same driver (rt2570).

If you just want to crack WEP, however, you don't really need to fake associate.  I know the 'simple WEP crack' instructions say you do, but in my experience it's never really been necessary.  For some of the advanced attacks, like cracking WEP with no other clients around, fake association is necessary, but obviously you can make sure that there are other clients around because you're only using aircrack against your own network, right? :)

---

### Post by XxBJDxX on 2008-11-08
ahhh of corse its my AP :P

well thank you for your reply.

I just need SOME method to caputre more IV's, because the, uh i mean my network traffic is slow and only coughs up about 100 IVs in a hour, and of course need 5000 or so to crack WEP. any ideas for other methods???

---

### Post by pytheas22 on 2008-11-08
You can still inject packets even if you're not fake-associated.  Try running a command like:
```

aireplay-ng -3 -b [target AP MAC] -h [MAC of a client legitimately connected to the AP] rausb0
```

When the connected client generates an ARP packet, your card should catch it.  Once it gets that packet, it can 'replay' it to inject arbitrary traffic on the network you're targeting.  You should be able to inject at up to 600 packets per second, so you can collect IVs very quickly this way.

If you wait a while, the connected client should send an ARP request on its own every so often, but if you want to be aggressive, you can use a command like this to kick the connected client off of the network.  When it reconnects, it will send an ARP request that you can use to launch the injection attack:
```

aireplay-ng --deauth 10 -a [target AP MAC] -c [MAC of client to kick off network] rausb0
```

Note that the connected client will lose its Internet connection for a few seconds here.

---

### Post by XxBJDxX on 2008-11-08
very interesting, i am off to go try what you have just suggested, thank you for your replys, ill let you know if i have success .

---

