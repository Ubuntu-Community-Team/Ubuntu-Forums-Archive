---
title: "Outgoing ICMP shown in router log but not in netstat"
date: 2010-05-01
forum: Security
---

### Post by thing-fish on 2010-05-01
Recently my router logs have been showing outgoing ICMP packets from my ubuntu box to various IP addresses.  I've look a number of them up and they don't make any sense, though they are usually but not always foreign. 121.214.132.61, 198.107.129.106 and 89.185.186.202 are examples from today.

Again, these are OUTGOING packets that my router is stopping, but I very much want to know what process is doing these pings. I captured the results of sudo netstat -p -an -c but the IP addresses above do not appear in that log.

Is there a better way to monitor outbound traffic so I can figure out what process is doing this?

---

### Post by OpSecShellshock on 2010-05-01
Have you recently installed anything from a source outside of the repositories? Have you checked to see if these are "destination unreachable protocol unreachable" responses to incoming ping attempts?

Latter is doubtful since inbound ICMP traffic shouldn't even touch your computer behind the router, but you never know how these things are set up.

---

### Post by KillaB7 on 2010-05-01
EDIT: Nevermind. Just my machine responding to an old torrent connection.

---

### Post by thing-fish on 2010-05-03
> **OpSecShellshock said:**
> Have you recently installed anything from a source outside of the repositories?

Not that I can think of.  My configuration has been stable for many months.

> **OpSecShellshock said:**
> 
Have you checked to see if these are "destination unreachable protocol unreachable" responses to incoming ping attempts?

Latter is doubtful since inbound ICMP traffic shouldn't even touch your computer behind the router, but you never know how these things are set up.

Exactly: the router is set to ignore incoming pings and the log has many "Blocked incoming ICMP error message (ICMP type 3)...as there is no UDP session active between..."  I just can't figure out what is running that's trying to send outbound pings :(  Any help is appreciated.

---

### Post by dearingj on 2010-05-03
1) Is this a wireless router, and if so is it possible that somebody else might be using your internet connection?
2) If there are multiple computers connected to your router, do your router's logs identify which computer these appear to be coming from?

You might get more useful information by installing and running [Wireshark]("apt://wireshark") on whichever computer is sending these ICMP requests.

---

### Post by thing-fish on 2010-05-03
> **dearingj said:**
> 1) Is this a wireless router, and if so is it possible that somebody else might be using your internet connection?
2) If there are multiple computers connected to your router, do your router's logs identify which computer these appear to be coming from?

It is a combination wired/wireless router, but the log is showing outbound ICMP packets from my Xubuntu box, which is wired.  I've tried running Netstat to capture the outbound ping but have had no luck.  The router log shows that it blocked an outgoing ping from the Xubuntu box, netstat does not show any activity to the destination IP.

---

### Post by KillaB7 on 2010-05-03
What port are you seeing this activity on? and is UPnP running on your router?

There is a bug in Deluge/libtorrent that open's ports via UPnP but never closes them. Ubuntu then responds with an ICMP packet to any attempt at a connection on that port.

---

### Post by Kinstonian on 2010-05-03
> **thing-fish said:**
> Not that I can think of.  My configuration has been stable for many months.



Exactly: the router is set to ignore incoming pings and the log has many "Blocked incoming ICMP error message (ICMP type 3)...as there is no UDP session active between..."  I just can't figure out what is running that's trying to send outbound pings :(  Any help is appreciated.

Not all ICMP traffic are pings.  ICMP is used for error notification and control and uses types/codes instead of ports so you need to get the type and code then look it up [here](http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol) to figure out why you are sending ICMP traffic.

---

### Post by thing-fish on 2010-05-03
> **KillaB7 said:**
> What port are you seeing this activity on? and is UPnP running on your router?

There is a bug in Deluge/libtorrent that open's ports via UPnP but never closes them. Ubuntu then responds with an ICMP packet to any attempt at a connection on that port.

No, I do not have UPnP enabled on the router.  And I don't know the port, the only information in the router log are lines like this:

[INFO] Mon May 03 06:26:44 2010 Blocked outgoing ICMP packet (ICMP type 3) from 192.168.1.3 to 41.244.11.81

---

### Post by thing-fish on 2010-05-03
> **Kinstonian said:**
> Not all ICMP traffic are pings.  ICMP is used for error notification and control and uses types/codes instead of ports so you need to get the type and code then look it up [here](http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol) to figure out why you are sending ICMP traffic.

That is interesting, I didn't know that.  But why would these packets be going to random IP addresses located in Australia, Germany, South Africa, etc?

I don't understand why netstat shows no traffic to these addresses, and that's the only tool I know to use.  Is there another tool? Wipe and reinstall time? :confused:

---

### Post by KillaB7 on 2010-05-03
> **thing-fish said:**
> I don't know the port.

From your Xubuntu machine try:
sudo tcpdump icmp -v

---

### Post by OpSecShellshock on 2010-05-03
ICMP type 3 could be any one of several "destination unreachable" response messages. Since they're responses rather than any kind of initiated communication, this is probably not a huge deal. If you have a server of some kind running (any process that's listening for incoming connections) and also have a port forwarded on your router to enable the server to receive those connections, then from time to time you're going to have external hosts attempting to use those ports for something other than what they're intended for. In those cases, one of these ICMP packets might go out from your computer to that external host as a way of rejecting whatever it is they're trying to do. Since your router is preventing it from going out, they're just not going to get any response at all on their end.

Short version is that these types of ICMP messages represent your computer telling a remote computer that it failed to reach you for some reason. This would only be a problem if it was supposed to reach you.

---

### Post by thing-fish on 2010-05-04
Thank you for the tcpdump advice.  It showed that it was port 27877 in all cases.

And thanks for the information about ICMP type 3.  I do have a server running with a port forwarded, and what you describe sounds exactly like what's happening.

I'm relieved that tcpdump captured this activity but am bummed that netstat did not.  Now that I know the port, should the following command work to figure out which program is doing this?

```
sudo netstat -p -an -c | grep 27877
```

---

### Post by Kinstonian on 2010-05-05
> **thing-fish said:**
> Thank you for the tcpdump advice.  It showed that it was port 27877 in all cases.

And thanks for the information about ICMP type 3.  I do have a server running with a port forwarded, and what you describe sounds exactly like what's happening.

I'm relieved that tcpdump captured this activity but am bummed that netstat did not.  Now that I know the port, should the following command work to figure out which program is doing this?

```
sudo netstat -p -an -c | grep 27877
```

When you you say it was port 27877 in all cases, I'm assuming the ICMP traffic you're getting was Type 3 (destination unreachable)/Code 3 (port unreachable).  When someone makes a TCP connection request to a port on your computer that isn't listening, then your computer will respond with a packet with the RST and ACK flags set to tell the other computer that the port is closed.

The problem is UDP doesn't use flags, so it uses ICMP Type 3/Code 3 packets to tell the computer that sent the UDP traffic that the UDP port is closed.  That's what your computer is doing and there isn't a user process responsible for it.

---

