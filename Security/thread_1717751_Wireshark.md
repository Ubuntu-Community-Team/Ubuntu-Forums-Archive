---
title: "Wireshark"
date: 2011-03-30
forum: Security
---

### Post by conradin on 2011-03-30
Hi all,
I've been trying to use wireshark. I used to use it on old PCs when i was using hardy a few years back. Lately, though Ive been trying to use it and it just doesn't see any of my network card devices. I really need to do some capturing on my own computer, I need to know what file a server is asking my computer for so I can correct the version number when it fails. (srsly, I have 6 computers, none of them work with wireshark, its ridiculous!)

So, what can I do to get wire shark to recognize my NIC, Or, what other programs are out there for packet monitoring? Would a firewall be able to give me the info I seek?

---

### Post by uRock on 2011-03-30
Moved to security discussions.

---

### Post by 8668 on 2011-03-30
> **conradin said:**
> Hi all,
I've been trying to use wireshark. I used to use it on old PCs when i was using hardy a few years back. Lately, though Ive been trying to use it and it just doesn't see any of my network card devices. I really need to do some capturing on my own computer, I need to know what file a server is asking my computer for so I can correct the version number when it fails. (srsly, I have 6 computers, none of them work with wireshark, its ridiculous!)

So, what can I do to get wire shark to recognize my NIC, Or, what other programs are out there for packet monitoring? Would a firewall be able to give me the info I seek?

Have you tried running it as root? I had the same problem yesterday, ran as root and I'm golden

---

### Post by Rubi1200 on 2011-03-30
> **8668 said:**
> Have you tried running it as root? I had the same problem yesterday, ran as root and I'm golden
You should absolutely NOT be running Wireshark as root!!!

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

### Post by uRock on 2011-03-30
Running wireshark as root may cause an infected packet to compromise the system.

Also be aware that every packet is stored in RAM, so if you do not stop and dump Wireshark, then you will run out of RAM and the system will be using the swap and may slow or crash the system.

If you are using WIreshark just to monitor connections, then EtherApe may be a better choice as it does not fill the RAM nor analyze packets, but it will show all connections and you can click on an address to see what protocols are being used. (I have attached a screenshot of EtherApe in action.)

---

### Post by Soul-Sing on 2011-03-30
> **uRock said:**
> Running wireshark as root may cause an infected packet to compromise the system.

Also be aware that every packet is stored in RAM, so if you do not stop and dump Wireshark, then you will run out of RAM and the system will be using the swap and may slow or crash the system.

If you are using WIreshark just to monitor connections, then EtherApe may be a better choice as it does not fill the RAM nor analyze packets, but it will show all connections and you can click on an address to see what protocols are being used. (I have attached a screenshot of EtherApe in action.)


yeah or an apparmored tcpdump. less complex, less code.
```
tcpdump -n -i eth0 > tcpdump.txt
```
```
tcpdump -n -i eth0 > tcpdump.txt gzip tcpdump.txt
```

---

### Post by newbuntuxx on 2011-03-30
Correction to the tcpdump command:

```
sudo tcpdump -i interface_name -nX port 80 and src host sever_ip -w filename.cap
```

I assumed the file is being sent over port 80, and file name would be in the contents of the packet (hence the X switch)

Replce "server_ip" with the server's IP. If you want to use the hostname, then get rid of the "n" switch and then use the hostname.

---

### Post by uRock on 2011-03-30
I like putting Snort in packet sniffing mode, as well. I have a launcher to start Snort in this mode.```
sudo snort -vi eth0
```

---

### Post by Soul-Sing on 2011-03-31
> **newbuntuxx said:**
> Correction to the tcpdump command:

```
sudo tcpdump -i interface_name -nX port 80 and src host sever_ip -w filename.cap
```

I assumed the file is being sent over port 80, and file name would be in the contents of the packet (hence the X switch)

Replce "server_ip" with the server's IP. If you want to use the hostname, then get rid of the "n" switch and then use the hostname.

indeed! I didn't read the question of the op, and gave blindly an
alternative for wireshark, with an example to run it on a desktop situation, thx for the correction.

---

### Post by 8668 on 2011-03-31
> **Rubi1200 said:**
> You should absolutely NOT be running Wireshark as root!!!

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

That was incredibly informative. Thank you for the info

---

### Post by Rubi1200 on 2011-04-01
> **8668 said:**
> That was incredibly informative. Thank you for the info
You are more than welcome :-) 

It is quite easy, and safer, to capture packets using the method outlined in that article.

---

### Post by conradin on 2011-04-01
Ok, solved! Etherape, i tried, I didnt get it right away. runninng under root, I can understand, the cause for concern, but it works, and Im looking at just 5 seconds of pretty quiet traffic.  Thank you all so much
!!

---

