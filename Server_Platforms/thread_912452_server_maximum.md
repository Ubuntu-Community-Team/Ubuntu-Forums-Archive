---
title: "server maximum"
date: 2008-09-06
forum: Server Platforms
---

### Post by herrbrand on 2008-09-06
hello

I was arguing with a friend about the max capesity of an ubuntu server. so my question is, how many avarage sites kan you run on a ubuntu server?

I understand that it depens on the server speed en memory but isn't there an guide line?

Robbert

---

### Post by Krupski on 2008-09-06
> **herrbrand said:**
> hello

I was arguing with a friend about the max capesity of an ubuntu server. so my question is, how many avarage sites kan you run on a ubuntu server?

I understand that it depens on the server speed en memory but isn't there an guide line?

Robbert

I run Ubuntu Server as a home file server. The first place it "maxes out" is hard drive access. With the hard drives saturated, the CPU usage barely gets high enough to trigger a jump in CPU clock speed.

Even with lots of ram (I have 8GB), the ram fills up and then the drives bog down... long before the CPU gets used up.

A "real" server would need a better performing hard drive array to put the rest of the hardware to good use.

---

### Post by schettj on 2008-09-06
> **Krupski said:**
> I run Ubuntu Server as a home file server. The first place it "maxes out" is hard drive access. With the hard drives saturated, the CPU usage barely gets high enough to trigger a jump in CPU clock speed.

Huh?
Even PATA drives should be able to read at 20-40MB/sec. I dunno about you, but my internet pipe isn't anywhere near that. About $400 will get you a 1-2TB sata-300 RAID that should be able to go 200-400MB/sec and even keep up with a gigabit link.

To the original poster... what do you mean, exactly? Serving web pages? Any wimpy x86 server will be able to handle T1-T3 speeds outbound. Ditto for email (even with virus and spam checking) for hundreds of users.

If you're talking simultaneous desktops, it's probably 1 per .5ghz per 686-class core, with .5gb real ram needed per desktop. More or less. 

But for serving bits on the internet? Your pipe is going to be the limiting factor there (DDOS aside)

---

### Post by Krupski on 2008-09-06
> **schettj said:**
> Huh?
Even PATA drives should be able to read at 20-40MB/sec. I dunno about you, but my internet pipe isn't anywhere near that. About $400 will get you a 1-2TB sata-300 RAID that should be able to go 200-400MB/sec and even keep up with a gigabit link.

To the original poster... what do you mean, exactly? Serving web pages? Any wimpy x86 server will be able to handle T1-T3 speeds outbound. Ditto for email (even with virus and spam checking) for hundreds of users.

If you're talking simultaneous desktops, it's probably 1 per .5ghz per 686-class core, with .5gb real ram needed per desktop. More or less. 

But for serving bits on the internet? Your pipe is going to be the limiting factor there (DDOS aside)

I've got four 1 TB SATA 300 (Western Digital) drives in my file server setup as RAID 0+1 (striping + mirroring). The network is copper gigabit.

Copying a file from, say, the file server to a Windows machine I get 50 to 60 megabytes per second. If I copy multiple files at once, the sum total of all the throughput is around 85 megabytes per second. It simply doesn't go faster than that.

But, when I do have the drives maxed out at 85 mb/sec, the CPU doesn't even come up off idle.

The CPU is an Intel Core II Duo E6700 running at 2.66 GHz (and using the acpi-cpufreq controller and the conservative governor), it runs at 1.536 GHz. unless it's usage goes above 80%, whereupon it clocks up in 5 steps to the max of 2.66 GHz.

With the hard drives saturated, the CPU cores loaf at 1.536 GHz which tells me that disk I/O is the bottleneck.

Even copying a large file WITHIN the server (i.e. not using the network) still tops out at 85 MB/Sec, so I know it's not the LAN that's the bottleneck.

I know that the CPU governor is working, because I can do something CPU intensive like multiple GZIP processes and the CPU will jump right up to 2.66 GHz. (then drop back down as soon as it's done).

I don't think SATA is all it's cracked up to be...

---

### Post by schettj on 2008-09-07
> **Krupski said:**
> I don't think SATA is all it's cracked up to be...Uh... the win drive is the limiter there. But we're talking server performance, right?

---

### Post by herrbrand on 2008-09-07
hallo

thanks for al the replays. I was curious if it is profitable to put my server in an server center for about 120 $ a month and put websites with domeins on it for 10 $ a moth. my server is and standard amd 64 bit 3200+ with 1 GB memory. I wil put more memory in it en 2 hhd's in raid 0.

if I can run alleast 10 websites i am out of costs. for each website more i make profit.

is this feasible?

Robbert

---

