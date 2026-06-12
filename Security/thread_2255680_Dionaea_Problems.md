---
title: "Dionaea Problems"
date: 2014-12-06
forum: Security
---

### Post by Stephan_Crennell on 2014-12-06
Hey, 

I have Ubuntu set up with an instance of DionaeaFR for some school work. The thing that we are meant to be doing is attacking the honeypot virual machine with a series of different attacks, with me personally going for scanning attacks, SSH brute force attacks and DDoS attacks. The problem is though, Dionara doesn't seem to want to post results.

I have done all three attacks, but none of the results have shown up. 

While using Kali and nmapping the Dionaea VM, I got all of the open ports, but when looking at the sql webserver to see results, nothing. Same goes with DDoS attacks, I get the system to sagging in performance, but no results. The brute force was less than a success, the connect just kept dropping on me.

So I am asking, is there anything that I can do to sort out why results aren't being posted?

The only information I can give you that may relate, was that the attacking Kali machine is on eth0 while the Dionaea machine is on eth1, but I didn't think this would cause much of an issue, also that are both bridge-networks with the host machine, if you need any more information just ask.

Thanks,
Stephan.

---

### Post by bashiergui on 2014-12-06
Could be a million things. For all I know you're attacking 127.0.0.1 ;) Capture packets to make sure what you think is happening is actually happening. 

Maybe adjust the logging level of Dionaea. Read the docs [http://dionaea.carnivore.it](http://dionaea.carnivore.it)
There was an irc channel for dionaea, no idea if it's still exists #Nepenthes

As this is schoolwork I won't give you much more than that.

---

### Post by Stephan_Crennell on 2014-12-07
All sorted now.

I was attacking 192.168.56.101, but when i ran the server at 127.0.0.1 it was showing the logs, although not them all, only the closed ports that where being scanned. I suppose that should do as I am not completely sure whether it would be displaying open ports.

Thanks for the help though :)

---

