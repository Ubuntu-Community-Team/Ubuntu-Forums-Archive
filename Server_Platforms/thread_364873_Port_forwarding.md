---
title: "Port forwarding"
date: 2007-02-18
forum: Server Platforms
---

### Post by colyn on 2007-02-18
I have my website up and running but was wondering if port forwarding in my router/firewall is really needed.

What does it do??

---

### Post by kidders on 2007-02-18
Hi there,

Imagine you are running a web server on a home network at 10.0.1.5. Obviously, that IP isn't publicly accessible, so nobody on the internet can address it directly. Let's assume (for the sake of simplicity) that you only have one router (internal IP 10.0.1.1), and it has a direct internet connection ... so your network's public IP = your router's public IP. All outgoing packets appear to originate at your public IP address, and all incoming ones are addressed to it.

So, think about things from your router/firewall's perspective: Someone tries to access your web server, so they try to initiate a connection with your network, using its public IP. Packets addressed to your router start arriving, but it has no use for them, and no way of knowing what it's supposed to be doing with them. Under such circumstances, packets are usually dropped or rejected.

The way to sort things out is to explicitly instruct your router/firewall to forward applicable packets to your internal web server at 10.0.1.5. These packets can be easily identified using their port number ... so you call it "port forwarding". When you get a firewall to forward a port, all incoming packets on that port are redirected to the specified internal address behind the firewall, so it appears to all concerned that the connection is direct, even though it isn't.

If what I'm describing applies to you, then port forwarding *is* necessary.

What you wind up with is a bit like this...

**10.0.1.5** <--> **10.0.1.1** | **12.34.56.78**  <--> **87.65.43.21**

[LIST]
[*]10.0.1.5 can address 87.65.43.21 directly.
[*]87.65.43.21 *cannot* address 10.0.1.5 directly.
[*]Incoming data from 87.65.43.21 is addressed to your public IP (12.34.56.78), but forwarded 10.0.1.5 by the router, because it's been told to do that.
[*]Effectively, it appears as though the data is simply passing straight through the firewall.
[/LIST]

What confuses some people about port forwarding is, assuming you accept everything I've just written, why 10.0.1.5 can access the internet (eg with a web browser) without having to worry about where the data coming back again gets sent to. If you think about it, it doesn't make much sense ... When you ask for http://www.google.com, how can the router/firewall know what to do with the packets it sends back?

The short answer is that your firewall is monitoring outgoing packets, sees the TCP connection being set up with Google, and gathers enough information to guess the right thing to do with incoming data. Port forwarding only becomes necessary when the connection is being initiated from the outside world, so your firewall has nothing to go on.

I hope that answers your question (or have I just confused you?!).

---

### Post by colyn on 2007-02-19
Sounds simple enough..so it's a good idea to have port forwarding enabled to the internal webserver in order for others to access it..

---

### Post by kidders on 2007-02-19
Yep. :-)

The important word is **internal** though. If your web server had a direct internet connection, port forwarding would be meaningless.

---

### Post by colyn on 2007-02-19
> **kidders said:**
> Yep. :-)

The important word is **internal** though. If your web server had a direct internet connection, port forwarding would be meaningless.

I always wondered.. Even when I was running my server on a Win 2k machine I had port forwarding enabled to the http port on the internal machine.
Thanks

---

