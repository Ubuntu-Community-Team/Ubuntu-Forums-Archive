---
title: "[help] How To Avoid Getting Hacked."
date: 2015-05-29
forum: Security
---

### Post by randell3 on 2015-05-29
I would like to ask for answers especially from professionals regarding this matter.

Recently, when I am still not a ubuntu user, I was getting intrusion from other people thus I am forced to quit using unlicensed software then get freedom for personal use.

However, even if I am already living the clean way. I still get intrusions even if I understand that I am doing things the legal way.  

To take the (internet paranoid hacker jihad getting misplaced in my hand.. whatever you call it.) way, I would like to upload my system information and get assistance whoever can help me regarding this matter. 

Here is my IP table.

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ufw-track-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-forward (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         


```


I am afraid that I am a victim of a "Man In The Middle Attack". Also for additional info, I would like to ask how to avoid my traffic from being routed to the attackers computers.


Thanks in advance and I'll wait for response.

---

### Post by slickymaster on 2015-05-29
Hi randell3, welcome to the forums.

I'm moving your thread to the **Security** sub-forum, which is the suitable venue for it.

---

### Post by patrikmellq on 2015-05-29
I am not a expert - but if we use a router - then no one can make a direct hack on your computer - there has to be a weeknes among the software or system you use to get hacked - but that vanish if you keep you system with the latest updates.
I belive after reading different common Ubuntu security advice - that a router and UFW will do just fine.

If you are paranoid you can install Tripwire - then no one can hack your system without you knowing what and where the hack has been done.
And the hacker can not hack Tripwire - because the Tripwire databas will be on removable media.

With Tripwire (if there is one intrusion) you can make a investigation - because Tripwire will show all critical modified files that has been hacked - so you can backtrack how the intrusion had been made.
Here is a complete [SOLVED] Howto [http://ubuntuforums.org/showthread.p...light=TRIPWIRE]("http://ubuntuforums.org/showthread.php?t=2233278&highlight=TRIPWIRE")

---

### Post by Habitual on 2015-05-29
> **patrikmellq said:**
> I am not a expert - but if we use a router - then no one can make a direct hack on your computer - there has to be a weeknes among the software or system you use to get hacked - but that vanish if you keep you system with the latest updates.
I belive after reading different common Ubuntu security advice - that a router and UFW will do just fine.

If you are paranoid you can install Tripwire - then no one can hack your system without you knowing what and where the hack has been done.
And the hacker can not hack Tripwire - because the Tripwire databas will be on removable media.

With Tripwire (if there is one intrusion) you can make a investigation - because Tripwire will show all critical modified files that has been hacked - so you can backtrack how the intrusion had been made.
Here is a complete [SOLVED] Howto [http://ubuntuforums.org/showthread.p...light=TRIPWIRE]("http://ubuntuforums.org/showthread.php?t=2233278&highlight=TRIPWIRE")

and an Excellent recipe is [here]("http://ubuntuforums.org/showthread.php?t=2235300")...
Good Job.

---

### Post by randell3 on 2015-05-30
> **patrikmellq said:**
> I am not a expert - but if we use a router - then no one can make a direct hack on your computer - there has to be a weeknes among the software or system you use to get hacked - but that vanish if you keep you system with the latest updates. I belive after reading different common Ubuntu security advice - that a router and UFW will do just fine.  If you are paranoid you can install Tripwire - then no one can hack your system without you knowing what and where the hack has been done. And the hacker can not hack Tripwire - because the Tripwire databas will be on removable media.  With Tripwire (if there is one intrusion) you can make a investigation - because Tripwire will show all critical modified files that has been hacked - so you can backtrack how the intrusion had been made. Here is a complete [SOLVED] Howto [http://ubuntuforums.org/showthread.p...light=TRIPWIRE]("http://ubuntuforums.org/showthread.php?t=2233278&highlight=TRIPWIRE")  Thanks for the answer. I'll try to study that. Another thing, how do I be sure that I get the right update and not redirected sources?  I have read that you can view most of the codes inside ubuntu but doing so would be time consuming especially that I am new to the system and don't have sufficient knowledge in reviewing data.

---

### Post by patrikmellq on 2015-05-30
Hello - as i understand it - so does UFW block all incoming traffic - ports are closed.
UFW allow outgoing traffic from you internet software.

Assume you have a router and UFW - then it should not be any issue.
But if you feel that you want higher security - then install Tripwire - then no one can hack your system without you know it - if you follow my guide and install the Tripwire database on removable media.

Other ways can be to create a log server that check all traffic - in and out.
Then you need to install Tripwire on the log server.
But i assume is a time consuming task to read and check logs - but as combination with Tripwire you would have Fort Knox.

I don't belive you can be 100% safe from intrusion - because if some one want to get acces to your computer - then they will find a way.
So my suggestion is that Tripwire is the best solution - then you can stop being paronoid - because there can not be an intrusion with out you knowing.

So my opinion is that good security is to have a router, UFW and Tripwire if you are paranoid.

---

### Post by Lars Noodén on 2015-05-30
> **randell3 said:**
> Another thing, how do I be sure that I get the right update and not redirected sources?

If I understand correctly, one of the first things downloaded is a list of package file names with their MD5 checksums.  And to prevent falsification of that list, the list is signed with the Ubuntu repository's OpenPGP key.  That key is part of your system.  So if you got the right system when you first installed, you will keep getting the authentic updates from the real repository as you go.  The MD5 hash algorithm is considered too weak these days, however.  

[https://wiki.debian.org/RepositoryFormat](https://wiki.debian.org/RepositoryFormat)
[http://uk.archive.ubuntu.com/ubuntu/dists/trusty/](http://uk.archive.ubuntu.com/ubuntu/dists/trusty/)

Also it's been a while since I looked at Tripwire or similar IDS packages but you would need to update its database every time you update the software on your system.  Removable media is a good idea.  Some flash drives have physical switches that can be set read only.  The down side is that you need to be physically at the machine to update the IDS database.  It's not that hard to roll your own Tripwire variant, if you have some minor scripting skills.

---

