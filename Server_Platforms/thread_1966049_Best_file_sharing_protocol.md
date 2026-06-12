---
title: "Best file sharing protocol?"
date: 2012-04-26
forum: Server Platforms
---

### Post by JD32 on 2012-04-26
I know this has probably been asked before but im trying to setup a media server to stream my video. Now i have a headless server running ubuntu server and SSH with a DNS to log in from anywhere. Configure it and everything isn't the problem. I'm looking for the fastest protocol to stream my videos. The best i can get now is about 120-140kbs. Not enough for VLC to stream HD video without stopping to buffer every 30 seconds. It streams fine on my local network but is there anything i can do to configure it to transfer faster over the internet?

Is my ISP limiting it? i'm supposed to have 1mbs upload speed

Is it the SSH protocall? should i be using FTP, HTTP, NFS or something else?

Is my server hardware limiting my speed? its a pretty old system, only like a ~2.0ghz single core processor (cant recall exatcly what processors, pretty sure its some intel pentium)  and 512mb or ram. and an old IDE drive

I'm leaning towards my outdated hardware being the problem.

But anyway if anyone has an opinions or thoughts let me know.

Thanks!

---

### Post by arrrghhh on 2012-04-26
> **JD32 said:**
> Is my ISP limiting it? i'm supposed to have 1mbs upload speed

It's your ISP.  Remember, they always, ALWAYS report bandwidth in bits, not bytes.  So 1mbps ~= 128KBps.  So 120-140KB/s is about all you can expect from your ISP, unless you upgrade.

Streaming over the 'net is never easy... Most seem to use a dedicated box like a SlingBox.  I don't stream over the WAN, so I can't really help advise much there...

---

### Post by JD32 on 2012-04-26
so there's no way around this to stream videos unless i upgrade my ISP service?

---

### Post by papibe on 2012-04-26
Hi JD32.

If you can stream OK in your network, it means it isn't your server.

I would start by testing your upload speed. Take several of them so you can have a better estimate. Note that it is very difficult to get that max speed as a constant rate. Your goal is probably in the range of 85-90%.

Now, let's see. An upload of:
```
1mbs
```
means 'One mega **bits** per second', not bytes.

Then your max speed is:
```
128 KB/s
```
(128 Kilo **bytes** per second).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by JD32 on 2012-04-26
yeah im sure my ISP is my limiting factor... How would i run a speed test through the terminal?

---

### Post by arrrghhh on 2012-04-26
> **JD32 said:**
> yeah im sure my ISP is my limiting factor... How would i run a speed test through the terminal?

Hands down the best way is iperf... but you need to have a machine on the far-end to do a proper test.

If you know your ISP caps you at 1mbps, then you know that won't be enough to stream.  What do you need to speed test it for?  On that same note, if you have any other machines on the network with a UI, you can just speed test on them.

Edit - see this page for the topic of speed testing from CLI.  Download seems really easy to test, upload is where it gets tough...
[http://stackoverflow.com/questions/426272/how-to-test-internet-connection-speed-from-command-line](http://stackoverflow.com/questions/426272/how-to-test-internet-connection-speed-from-command-line)

---

### Post by SeijiSensei on 2012-04-26
If you have another machine on the network with a browser, just visit [http://speedtest.net/](http://speedtest.net/).

In general NFS has probably the lowest overheads since it's a UDP service.  On the other hand, unless the clients are running some *nix OS, they won't have a native NFS client available by default.

---

### Post by JD32 on 2012-04-26
yup, upload max of 1.03mbps... cost me double just to get 2mbps upload... So guess ill never be able to stream like i want to :(

---

### Post by Jonathan L on 2012-04-27
> 128 Kilo **bytes** per second

... just because it took me so long to find this out: bit rates are expressed in decimal powers (because they are measured on oscilloscopes): 1 Mbit/sec is 1,000,000 bits in a second.

When we're thinking about file transfer times, we normally are taking about the time to copy a file, say of 1 Mbyte, by which we'd normally mean binary powers, so 1 * 2^20 bytes, or 1,048,576 bytes or 8,388,608 bits.  Disk drive manufacturers normally use powers of 10 because it makes it sound bigger; RAM manufacturers always use proper binary powers because that's how RAM is made.

To exactly work out the theoretical minimium time a certain amount of payload data takes if you know the transport rate can be a bit tricky (various kinds of framing, including IP and TCP or UDP headers), but for example it might be 28 bytes per packet of 1000 bytes, or approximately 3%.

... apologies if slightly off topic.

Kind regards,
Jonathan.

---

### Post by JD32 on 2012-04-27
Yeah, and technically its a kibibit which is 2^10. They use Kilobytes 10^2 for exactly what you said, to make them sound bigger/cleaner numbers. Because we all know binary is in base 2 not 10 lol

---

