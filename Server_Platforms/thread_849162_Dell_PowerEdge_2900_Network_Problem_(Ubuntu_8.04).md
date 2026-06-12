---
title: "Dell PowerEdge 2900 Network Problem (Ubuntu 8.04)"
date: 2008-07-04
forum: Server Platforms
---

### Post by fmonline on 2008-07-04
Hi,

I am very new to Ubuntu and have a new Dell PowerEdge 2900 with 4x300GB SATA drives and PERC 6/i raid controller.

I have installed 8.04 LTS Server (64bit).

The installation went fine with no issues.

The problem is that there is no connectivity - I can't ping out or in (from another computer).

I know the network card is working because I put in a Knoppix CD and it could use the card OK.

Is this maybe an issue with 8.04 and PE2900 cards, and if so is there a work around?


Mike

---

### Post by gtdaqua on 2008-07-04
Have you configured the IP address? Is it static or DHCP?

Post the output of:

```

cat /etc/network/interfaces

```

---

### Post by fmonline on 2008-07-04
Hi,

Thanks for your reply - yes I have configured a static IP address.

But, not long after I posted this question I resolved the problem, by a fair amount of extra time searching the web. 

The PowerEdge 2900 server has a dual NIC adapter (Broadcom NetXtreme) which Ubuntu seems to have configured the wrong way round.

Ubuntu thinks:

 NIC connection 1   is eth1
 NIC connection 2   is eth0

So by plugging my network cable into the 'wrong' connection (NIC  connection 2) I do get connectivity through eth0. 
This is not what I would have expected!

Apparently the ethXX number comes from the order the kernel probes the cards, and Ubuntu is somehow getting them reversed.

So I can now connect to my new server.

Thanks,
Mike

---

### Post by synntech on 2011-07-28
Hi, I know that this is a old post, but I have the same problem right now.  I'm using ubuntu server 10.04, and I already try to connect the ethernet cable to the phisical eth1, but it doesn´t work.

Do yo know, how to getting up those interfaces?

---

