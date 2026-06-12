---
title: "Question about connections"
date: 2009-07-04
forum: Security
---

### Post by Cyked on 2009-07-04
So recently I've noticed more connections on my system than normal (i.e. connections other than what I expect).  At first I was just playing around with some things, rebooted with the network cable disconnected.  After logging back in I made sure that Apache was not running, reconnected the network cable, and was seeing new www connections.  Why is that?  Also, why would I see some as https?



Also wondering about iptables logging.  I see lots of denied connections from IPs that I'm not even blocking.  I setup a new file for the iptables log, following some howtos.  Where else might these be showing up from?  The all say "iptables denied".

This is the line I'm using for iptables logging from the Ubuntu Howto page/

```
sudo iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
```

---

### Post by gombadi on 2009-07-04
> 
This is the line I'm using for iptables logging from the Ubuntu Howto page/

Code:

sudo iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7



Do you have a link to the page this Howto came from?

That rule is silly :-(

It says to insert a firewall rule into the INPUT table at position 5 that will log, at log level 7, at the maximum rate of 5 per minute, every packet that the system receives, and label them with "iptables denied".

Who ever put that Howto up needs to fix it.


```

dig -x 170.135.216.181
whois 170.135.216.181

```

The above show this ip address is some sort of bank. Have you made any connections to from your system to the bank?

---

### Post by Cyked on 2009-07-05
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


Yes, that would be my bank.  I tried to do a whois on google, and didn't get much.  That is my bank, so yes....

Is there a way to show connections as which out outgoing vs. inbound. Or maybe by which app (my "outgoing" connections via firefox? vs. what is connecting to my server.)

> every packet that the system receives

Well that explains a lot... :-?

---

### Post by withjigs on 2009-07-05
may be use 
```
netstat -nlp
```

where "p" is for process who has started the connection.
Thanks

---

### Post by Cyked on 2009-07-14
Thanks for the Info.  I got it working now and am doing some logging and then dropping traffic.  Thanks!

---

