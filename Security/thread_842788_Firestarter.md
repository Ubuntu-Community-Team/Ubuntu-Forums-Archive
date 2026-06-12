---
title: "Firestarter"
date: 2008-06-27
forum: Security
---

### Post by pasha07 on 2008-06-27
Hey, I am really new to Linux so go easy on me. just switched over from windows to linux.  

I am using the latest version of ubuntu and i want to get firestarter to start automatically when i load up ubuntu. I have added it to start under "sessions" and have read all the files that i have to edit sudoers .. 

but when i do sudo visudo i get it opened in something.. that i can't seem to edit and even don't know how to close (Esc... ) nothing works.. 

how does a newbie like me can get firestarter to start when ubuntu starts?

thanks,
pasha

---

### Post by Shazaam on 2008-06-27
Firestarter is a gui for configuring iptables. Iptables is your "firewall". IMHO you don't need to have it start at boot because when you are done configuring iptables with Firestarter the rule changes stick. The ONLY reason I can think of to have it start at boot is if you want to watch any connections and there are many other apps that do the same thing such as iptraf (in the repos).
I get a full stealth report at grc.com and other sites and I don't have Firestarter load at boot.

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

---

### Post by mcduck on 2008-06-28
Having the Firestarter configuration GUI running always will only make your system less secure. Programs that are constantly running as root user are not the way to go if it can be avoided in any way. And, like already emntioned, you don't need it for anything else than configuring your firewall settings.

---

### Post by p_quarles on 2008-06-28
Moved to Security Discussions.

---

### Post by kevdog on 2008-06-28
Just a question for the original poster to confirm some information please.  I'm assuming you have used firestarter prior, and setup the appropriate filtering/forwarding that you desire.  If you have do this (sounds like you have), if you simply reboot, and do not start firestarter and startup, what is the results of:

sudo iptables -L

Basically firestarter creates a script file, and then passes its list of rules to iptables (the actual firewall) in a script at startup.  I don't know if the GUI needs to be active in order to accomplish this.  Its possible if the GUI needs to be active, that you could simple extract the ruleset when Firestarter is running, and then setup up a script or use the iptables-restore command within the rc.local file to restore the ruleset at boot time, without the need to run firestarter.

---

### Post by hyper_ch on 2008-06-28
are you actually sure you need firestarter or to configure iptables at all?

---

### Post by mcduck on 2008-06-28
> **kevdog said:**
> 
Basically firestarter creates a script file, and then passes its list of rules to iptables (the actual firewall) in a script at startup.  I don't know if the GUI needs to be active in order to accomplish this.  Its possible if the GUI needs to be active, that you could simple extract the ruleset when Firestarter is running, and then setup up a script or use the iptables-restore command within the rc.local file to restore the ruleset at boot time, without the need to run firestarter.

No, the GUI definitely doesn't need to run. Actually it's not absolutely true that Firestarter doesn't need to run for the firewall to work, the truth is that the *Firestarter GUI* doesn't need to be running.. Firestarter itself is, just like you said, divided into the configuration GUI and the actual Firestarter script (which manages iptables rules). The script is started automatically at boot.

---

### Post by brian_p on 2008-06-28
> **pasha07 said:**
> but when i do sudo visudo i get it opened in something.. that i can't seem to edit and even don't know how to close (Esc... ) nothing works.. 

From your description it seems the default editor has been changed. Does it say 'nano' at the top left of the page?

---

### Post by pasha07 on 2008-06-28
all right.. first off.. wow.. coming from windows it's amazing to see people actually helping each other out. and thanks for all the response. 

and its awesome that i don't need to run it, i stealth check my system and there wasn't any problem with firestarter not running. i love linux. 

anywho, i ran sudo iptables -L and here is the result.. not sure what it means. 

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dns.rnc.net.cable.rogers.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns.rnc.net.cable.rogers.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.103        dns.rnc.net.cable.g.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.103        dns.rnc.net.cable.g.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere   ****

---

### Post by kevdog on 2008-06-28
I'm not sure if the Firestarter GUI was running or not when you ran the iptables -L command, however the firewall is definitely active with that output.   A lot of different chains.

Iptables does both packet filtering (what everybody thinks of when they hear the term firewall), but also does nat routing.  Nat routing is necessary if you do any internet connection sharing (which means you are routing).  Bridging is the only other alternative to internet connection sharing and this doesnt require an active iptables or firewall configuration, however this approach does greatly improve the traffic on the network.

Sorry for the off topic discussion.

To exit the vim editor -- Hold down the Shift key and then ZZ (push Z key twice).

---

### Post by TWO on 2008-06-28
Apart from using the > sudo iptables -L command to see if the firewall is active, does anyone know of any other way to check whether the Firestarter script file is started from boot? Is there anything that indicates that it has been started?

Thanks 

TWO

---

### Post by Pjotr123 on 2008-06-28
Better use ufw for configuring your firewall:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by kevdog on 2008-06-28
In order to totally bypass Firestarter on a routine basis, here is one method

1. Use firestarter to setup your firewall however you want it.

2. Save the iptables configuration to a file:
sudo iptables-save > /etc/firewall.ruleset

3. Ok now you dont need any part of firestarter unless you need to modify the ruleset.

4. Load the ruleset at boot into iptables within /etc/rc.local

gksu gedit /etc/rc.local

Add the following command prior to the exit 0 line at the bottom:

cat /etc/firewall.ruleset | iptables-restore

I don't really know of any other way to verify the active ruleset of iptables of than iptables -L.  If you want to test the iptables functionality, then you could perform some logging commands within iptables, and then examine the /var/log/kern.log file to see if certain packets were dropped or filtered depending on how you set up the logging instructions.

---

### Post by mcduck on 2008-06-28
> **TWO said:**
> Apart from using the  command to see if the firewall is active, does anyone know of any other way to check whether the Firestarter script file is started from boot? Is there anything that indicates that it has been started?

Thanks 

TWO
You can execute this command to check if the script is running:
```
sudo /etc/init.d/firestarter status
```

The script can be started and stopped in the same way:
```
sudo /etc/init.d/firestarter start
sudo /etc/init.d/firestarter stop
sudo /etc/init.d/firestarter restart
```

I suppose there could also be some log file somewhere, but I can't check that since I've moved to using UFW instead of Firestarter.


edit: I really doubt that copying iptables rules from the Firestarter script to another file and adding that to start at boot instead of the original script would bring any benefits. You'd just go through extra work just to end up with what you started with in the first place.. ;)

---

### Post by kevdog on 2008-06-28
It would save you a running process :)

---

### Post by TWO on 2008-06-28
> Better use ufw for configuring your firewall:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

Pjotr123, thanks for the link. It was an interesting read.


> **mcduck said:**
> 

edit: I really doubt that copying iptables rules from the Firestarter script to another file and adding that to start at boot instead of the original script would bring any benefits. You'd just go through extra work just to end up with what you started with in the first place.. ;)

Mcduck, thanks for those commands. At least I can now confirm that the script is running in the background. I just reset my computer after leaving it to finish package downloads during the night and found that the script still ran after reboot. 

I guess the whole wanting some type of tray icon to indicate that a firewall is running is a bad habit from years of 3rd party firewalls/ anti-virus programs under Windows! Nice to just know that something is running without the need for a GUI hogging resources! 

I'm quite happy for the Firestarter script to be running automatically at boot, so I guess I'll stick with that rather than UFW. Besides, I think it'll be a tad bit easier to configure as well. 


Kevdog, cheers for your suggestion as well.

Thanks very much

TWO

---

### Post by kevdog on 2008-06-28
Glad you got it figured out to your liking :)-

---

### Post by kevdog on 2008-06-28
Glad you got it figured out to your liking :P

---

