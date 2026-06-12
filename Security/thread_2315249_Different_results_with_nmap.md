---
title: "Different results with nmap"
date: 2016-02-27
forum: Security
---

### Post by cogset on 2016-02-27
I know that nmap should be used to scan your system from the outside,  however I sometimes run a system scan on my own computer and there's  something I don't understand: the command ```
sudo nmap -A -vv --reason   --version-intensity 9  -T normal  -p 1-65535
``` returns all ports closed as  I would expect, since I have no servers installed or services listening  on my desktop.

But  instead the ```
sudo nmap -sT -vv --reason   --version-intensity 9  -T normal  -p 1-65535
``` command is often returning  some random high-numbered TCP port in open state like say *57526/tcp  open  unknown syn-ack* , all other things being equal -meaning I run the  two scans one after the other, with the computer in the same state.

Is that somehow normal, and why is this happening?

---

### Post by SeijiSensei on 2016-02-27
Can you connect to that port with "telnet localhost 57536"?

The port may be open for a brief moment if some other application is connecting to the Internet so it can receive [ACK packets in response to a SYN request]("https://en.wikipedia.org/wiki/Transmission_Control_Protocol").

---

### Post by cogset on 2016-02-28
Of course not : telnet is one the first things I get rid of...
But if I try to investigate right after the scan results with **fuser -v   57536/tcp**  I get nothing, as if that particular port had been closed already.

There are two things that puzzle me here: one being that the first scan option (nmap -A) ** always** returns all port closed whilst the second one (nmap -sT) more often than not finds some random TCP port open for a brief moment, the other being that with no services listening *and *a default ufw policy to deny incoming connections, why should a port be randomly opened, if only for a moment?

I'm not running such nmap scans whilst using any application, just the OS running and a network connection established.

---

### Post by CharlesA on 2016-02-28
> **cogset said:**
> Of course not : telnet is one the first things I get rid of...

Erm, the telnet client not the telnet server. There should be no services listening on the external interface by default, so you wouldn't have to worry about removing it if it was installed already.

Now, I use telnet for a lot of network testing, but if fuser works for you, then use what works for you.

> I'm not running such nmap scans whilst using any application, just the OS running and a network connection established.

They are temporary ports that are opened to receive data. This is why you should be scanning your system from another system on the same network/different network and compare the results rather than trying to an nmap scan on localhost.

---

### Post by HermanAB on 2016-03-01
Hmm, telnet is a very useful test utility, which should not be lightly discarded.  However, you can do everything that telnet does with netcat.

---

### Post by fugu2 on 2016-03-02
my first thought: because nmap is being run on itself, it's not scanning the ip like 192.168.1.100:1,192.168.1.100:2,192.168.1.100:3,... but instead is scanning on the loopback adapter 127.0.0.1:1,127.0.0.1:2,127.0.0.1:3,.. where other internal services run all the time, might be opening and closing ports briefly that we don't see. My recommendation is to capture packets with wireshark/tcpdump and then nmap scan. when you find an open port again, you can analyse why nmap is viewing it as an open port

---

### Post by cogset on 2016-03-04
Great tip about investigating with wireshark, I really should have thought about that.

However, I should have also specified that I'm using a command like ```
sudo nmap -A -vv --reason   --version-intensity 9  -T normal  -p 1-65535 <my computer IP> 
```
which I believe should point nmap to the actual IP address to scan and not the loopback interface, is that correct?

---

### Post by CharlesA on 2016-03-05
If you are scanning from the same machine, but it should only seen services running on that IP address.

It is a better idea to scan from an external host due to firewall rules, etc.

---

### Post by cogset on 2016-03-07
[FONT=system]I've been keeping  an eye on this, so far every time nmap has found a TCP port open with the -sT option, there was no trace of that in the wireshark capture.

 It almost looks like nmap* itself *is briefly opening such ports - could it be some weird side effect of scanning the computer "from the inside"?
 
 
 How should I proceed to scan from an external host?

Is it enough to use another computer on the same LAN and run nmap from there pointing it to the ip address of the computer I want to scan?
[/FONT]

---

