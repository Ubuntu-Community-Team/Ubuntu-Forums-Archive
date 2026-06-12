---
title: "Running WireShark as root?..."
date: 2010-10-11
forum: Security
---

### Post by VcDeveloper on 2010-10-11
, I'm running behind a 2wire NAT Router with only have smtp, www, pop3 open routing to my ubuntu VM server.  Network also includes three other ubuntu VM server's and a Desktop.  I'm the only one on the network so my question is, what security risk is there running WireShark as root?

Because running it under dumpcap is horrible after you quit.  It hogs up all the resource to remove the dump.

---

### Post by bodhi.zazen on 2010-10-11
[http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)

> Running Wireshark (or any other network capture/analyzer, for that  matter) on Linux needs root privileges. Therefore, you have to have root  privileges when starting Wireshark, else you can't capture data. Please  note that you don't have to login as root when starting your computer,  you can use su(1) or sudo(8) for that purpose. However, this remains  unsecure as the dissectors, the parts of Wireshark which parse the  captured data, run with root privileges as they did before. A much safer  solution would be to su(1) to root, then use the bundled **dumpcap**  to dump the data (for example, you can evoke dumpcap by using "dumpcap  -w ./dumpfile", which will dump the packets to the file "dumpfile" in  the current working directory. See "dumpcap -h" for details). You could  also use tcpdump for this purpose. The advantage of this solution is,  while dumpcap/tcpdump still run as root, you can run Wireshark as a  ordinary user and load the data you captured previously, so effectively  this is kinda "privilege separation by hand".

The above wiki page discusses the concerns in more detail.

Do with the information as you wish, but I am not sure how running as root helps your problem.

---

### Post by Rubi1200 on 2010-10-11
I would suggest you also take a look here:
[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

### Post by VcDeveloper on 2010-10-11
Uhmmm, well, I guess what I'm reading is, the packets are the ones that are dangerous to my system.  So, I have no choice but to run it in dumpcap.

.....So, I have another question then.  I'm running Wireshark from my ubuntu DMZ VM, and I will be using this to route port 80 to my live ubuntu VM Webserver.  How much memory and disk space should I allocate to my DMZ in order for not to degrade the performance of the other VM servers as well as the main ubuntu server?

Also keep in mind I'm running the Desktop Server Version.

---

### Post by bodhi.zazen on 2010-10-11
I do not know the answer to your question, but from what you posted I would suggest snort is probably a better option as I doubt you are ever going to review all those packets.

My impression is you are using Wireshark as a NIDS, and again, IMO, psad or snort are almost certainly better options.

---

### Post by VcDeveloper on 2010-10-11
Thanks for your help!  I'll give snort a try!

---

### Post by 98cwitr on 2010-10-12
I have to run WS as root or I can't see my interfaces. Snort's good too though :)

---

### Post by bodhi.zazen on 2010-10-12
> **98cwitr said:**
> I have to run WS as root or I can't see my interfaces. Snort's good too though :)

Not if you apply the changes in the various wikies.

One link was already given

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

