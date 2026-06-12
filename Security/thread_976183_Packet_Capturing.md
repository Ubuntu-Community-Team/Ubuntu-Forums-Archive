---
title: "Packet Capturing"
date: 2008-11-09
forum: Security
---

### Post by Dave_Connor on 2008-11-09
Nothing illegal. I am only messing with this type of software on my own systems. But I have a question when I capture the data. How do I read what has been captured ? I mean when I have Tcpdump write to file and then read the file. It shows the ip, ports, etc but where can I see what was transfered ?

---

### Post by IshikawaNakano on 2008-11-09
Open the output file with wireshark.

Select the packet that is part of the stream you want.

Click Analyze > Follow Stream

[http://www.wireshark.org/docs/wsug_html_chunked/ChAdvFollowTCPSection.html#ChAdvFollowStream](http://www.wireshark.org/docs/wsug_html_chunked/ChAdvFollowTCPSection.html#ChAdvFollowStream)

---

### Post by Kinstonian on 2008-11-09
If you're just starting out, I'd highly recommend WireShark.  Trust me, it's a lot easier.  However, to answer your question, when using tcpdump, you can use the -X option to see the contents of packets (first 68 bytes).  By default tcpdump only captures the first 68 bytes so to capture it all you need to add -s 1514.

---

### Post by kevdog on 2008-11-09
I'm no expert on packet monitoring but I second the recommendation for using wireshark.  Its extremely easy to use.

---

### Post by randy78 on 2008-11-09
The DSniff package is great if you want to see what some of these tools are capable of sniffing off of your network.

Just keep it legal ;)

---

### Post by Dr Small on 2008-11-09
> **kevdog said:**
> I'm no expert on packet monitoring but I second the recommendation for using wireshark.  Its extremely easy to use.
I also recommend Wireshark.

---

### Post by qwexer on 2008-11-10
I am in a class for networking that showed me tcpdump.  When I run tcpdump, I must be in sudo, which I assume is right, but when I run tcpdump, I get nothing on the screen.  If I set a -c it will finish out or I can just press ctr-c.  I can only read the output if I write it to a file and then read it.  What can I do to get it to output to the screen?  Anyone else have this problem?

---

### Post by Dr Small on 2008-11-10
> **qwexer said:**
> I am in a class for networking that showed me tcpdump.  When I run tcpdump, I must be in sudo, which I assume is right, but when I run tcpdump, I get nothing on the screen.  If I set a -c it will finish out or I can just press ctr-c.  I can only read the output if I write it to a file and then read it.  What can I do to get it to output to the screen?  Anyone else have this problem?
This isn't necessarily a fix for tcpdump (since I don't know much about it), but you can start screen, have tcpdump output to a file, start a new screen session, then run `tail -f filename` and you will be continuously updated from tcpdump. Then you can either stop tail, or switch back to the tcpdump screen and kill it.

---

### Post by persistentstubborn on 2008-11-10
> **qwexer said:**
>  What can I do to get it to output to the screen?  

```
sudo tcpdump -n -e -ttt -i NAMEOFTHELOGGINGPSEUDODEVICE
```

---

