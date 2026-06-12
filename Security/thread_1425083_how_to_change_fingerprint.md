---
title: "how to change fingerprint?"
date: 2010-03-08
forum: Security
---

### Post by etusha on 2010-03-08
Hi all
im interested to know how to change fingerprint ?
Linux (Ubuntu) look like Windows
Linux kernel 2.6 look like Linux 2.4 

----
apache 2.2 look like apache 1.3
apache look like IIS 
apache look like "BLABLABLA"

---

### Post by Conu on 2010-03-08
I was playing with nmap the other day and thinking about this. I dont think its all that hard in theory. In practise it might take a bit coding :)
Each of the fingerprinters (nmap, nessus, etc) uses slightly different methods. So if we look at nmap ( [http://nmap.org/book/osdetect-methods.html](http://nmap.org/book/osdetect-methods.html) ) there are a series of six TCP probes. The response from each is evaluated, the resulting fingerprint is compared to a database.
If you had a firewall with stateful packet inspection then these probes could be trapped and a different response generated. Using the nmap OS db as the starting point it could be reverse engineered to provide the specific OS desired.
In practice this would mean a lot of sitting between 2 computers and using nmap and wireshark :) I'm sure there is a prog like this somewhere, prob half finished!
You would also have to clean up all your server stuff, I know samba likes to display to everyone that its samba vX.X.X running on Ubuntu vX.X blah blah. And then your web browser loves telling anyone who will listen about the intimate details of your system :(.
Well thats my 2 cents worth:)

---

### Post by emiller12345 on 2010-07-22
Is it possible to make rules in the NAT table or Mangle table of iptables to change Ubuntu's OS fingerprint to something else? I'm thinking the POSTROUTING would work to send out the packets.  Or might it be possible to use the linux kernel module ipt_queue to collect incoming packets, and libnet1 to send replies back out? Timing is also used in OS fingerprinting.

---

