---
title: "Port knocking not working"
date: 2012-04-16
forum: Security
---

### Post by slowtrain on 2012-04-16
So, I tried to implement a basic port knocking scheme on an office desktop that is getting a lot of break-in attempts.  But, simple though the scheme is, I can't seem to make it work.  Maybe there's something basic I'm missing or maybe someone could suggest an alternative?  Have heard of FWKNOP, but that seems even more complicated and I have to wonder if that will work if the simple program 'knock' won't.

I'm using the ubuntu instructions for the program 'knock':

[https://help.ubuntu.com/community/PortKnocking](https://help.ubuntu.com/community/PortKnocking)

I've also tried variations of the configuration file based on the man pages for knockd.  I then shut all ports, including port 22, with firestarter, which I understand is just a frontend for iptables.  And next I try knocking to get ssh access, but ssh is blocked and simply times out.

From what I can see in my syslog, a single knock (on 3 ports) from my laptop to my desktop results in the desktop's knock daemon running the iptable command that should give my ssh port 22 access not once but 3 times.  That is, the log shows this entry (and some other stuff) 3 times:

knockd: openSSH: running command: /sbin/iptables -A INPUT -s myLaptopIPaddress -p tcp --dport 22 -j ACCEPT

I'm wondering how my ssh attempt could fail after the above command is run?  Anyone interested in seeing my iptables -L here?

---

### Post by slowtrain on 2012-04-18
Hi folks:  So, to partially answer my own question (and raise some new issues below), the problem is that the default iptable rule change that is suggested by knock documentation is not correct for the current Ubuntu.

The command knock uses is:

/sbin/iptables -A INPUT -s %IP% -p tcp --dport 22 -j ACCEPT

The one it should use is:

/sbin/iptables -I INBOUND 1 -s %IP% -p tcp --dport 22 -j ACCEPT

That is, the rule to add port 22 should go into the INBOUND chain, not INPUT.  Also, it can't go to the end of the chain because there's an LSI rule that moves TCP connections to the LSI chain where they are dropped.  

I didn't know where better to put the new rule, so I chose the first line.  Hope I'm not creating some other kind of problem here.  

My INBOUND chain, after execution of the knock looks like the one below.  Yup, I've seen my iptable rule repeated anywhere from 1 to 2 to 3 times--why I'm not sure.  Am using knock with 3 ports to open up port 22.  This doesn't make me confident that when I try to close the port, it will always erase every one of redundant the rules (say 3 go in and 2 come out).  Any idea why this is and how to correct it?

sudo iptables -nvL INBOUND
Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    6   960 ACCEPT     tcp  --  *      *       myLaptopIP      0.0.0.0/0           tcp dpt:22 

    2    80 ACCEPT     tcp  --  *      *       myLaptopIP      0.0.0.0/0           tcp dpt:22 

    9  1557 ACCEPT     tcp  --  *      *       myLaptopIP      0.0.0.0/0           tcp dpt:22 

 2952 2775K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

   93  5726 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0

---

### Post by Doug S on 2012-04-19
> the problem is that the default iptable rule change that is suggested by knock documentation is not correct for the current Ubuntu.
That is incorrect. In my opinion, the problem is that you are using firestarter. It is firestarter that creates and uses the INBOUND chain. I think it is also firestarter that saves the iptables configuration such that it re-loads upon re-boot, such that any rules you add, via startup script or whatever, get added again leading to the multiple ocurrences.
I see no end of postings about grief with firestarter and the junk it leaves behind when ones tries to stop using it. Firestarter is no longer being developed. My suggestion is that you get rid of it.

---

