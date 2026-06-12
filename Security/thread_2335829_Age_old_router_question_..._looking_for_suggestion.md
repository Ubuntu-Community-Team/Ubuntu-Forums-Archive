---
title: "Age old router question ... looking for suggestions"
date: 2016-09-01
forum: Security
---

### Post by cackles on 2016-09-01
I built a mini-itx Celeron on-board Asus N3150i-C, 8GB RAM, 60GB SSD, 1 x 4-port PCI-E LAN and a mini PCI-E Intel 7260ac wi-fi card.

Initially all I was going to do was install IPCop but then after research I found more powerful firewalls/gateways/etc.

Then I read many flame wars about the best to use.

Now I'm just like ... ummmm ... so many options.

I am going to agree with one post I read and that is that it is going to be better to setup Ubuntu with all the best stuff.

So if you can, I'd like some suggestions about what to use on top of Ubuntu, please.

I'm looking for everything you would find in the best routers with a web interface. DHCP and DNS are straight forward, sort of, I would like to be able to manipulate everything through a control panel. DDoS etc. prevention, website/IP blacklist for external traffic (preferably auto updating). Web caching with a malware scanner or similar. Also being able to easily kick/ban someone from the network/parental controls is something I really need.

I don't need a mail server or anything else because that's running off another machine.

I am just looking for the names of what to install into a headless Ubuntu machine, basically.

Extra advice is welcome, I've been at this on and off for a couple of months now.

---

### Post by 1clue on 2016-09-01
Is your lan card Intel or something else?  It makes a difference, especially on low power setups. Off-brand cards seem to have the same specs but often cause more interrupts on the CPU, making the whole system slower. When you get above gigabit nics things change a bit.  Be sure to look for special hardware on your board and get the right drivers for it, that matters for router setups.

Are you running a VM in there? Will the router be bare metal or a VM?  In looks like you have enough RAM to run without virtual memory, I'd recommend that.

I'm using one of these: [http://www.supermicro.com/products/motherboard/atom/x10/a1srm-ln7f-2758.cfm](http://www.supermicro.com/products/motherboard/atom/x10/a1srm-ln7f-2758.cfm) running gentoo. I'm not doing bare metal though, it's a vm host which has a router on it.  The router is extremely faster than my internet connection (65mbps) but that's not hard. I can write an encrypted, compressed pipe at about 2.5gbps across the LAN on bare metal, that may actually be a limit on my other hardware though. My i7 box is actually slower when doing localhost-only routing/encryption/compression tests than my c2758 box.

Your setup looks like it could be pretty good for normal router work, not sure about encryption.  You have new aes instructions which are a bit different from my quick-assist.  You should be pretty quick if you can live inside the instruction set they give you.

As for what to use for ids/ips I'm still looking on that. I was thinking of making VMs with different configurations so I can try what works best.

I'd be interested to follow your progress here.

---

### Post by 1clue on 2016-09-01
Just as a comment, my i7 has a realtek nic in it as well, same series.  I have a 4x realtek card in it as well, and it's worthless. It works and I can get wire speed, but cpu load follows network load. I bought this stuff before I knew anything about the nics.

If you intend to JUST use your box for a router then you may be OK. If you intend heavy CPU loads then you may want to forget that your on-board nic exists at all, or hook it up to a low-speed low-traffic network.

---

### Post by cackles on 2016-09-01
> **1clue said:**
> Just as a comment, my i7 has a realtek nic in it as well, same series.  I have a 4x realtek card in it as well, and it's worthless. It works and I can get wire speed, but cpu load follows network load. I bought this stuff before I knew anything about the nics.

If you intend to JUST use your box for a router then you may be OK. If you intend heavy CPU loads then you may want to forget that your on-board nic exists at all, or hook it up to a low-speed low-traffic network.

It's going to be a dedicated router/wireless-access/firewall.

Everything else is on my server, 64GB DDR4, Intel 5820k-e with a Samsung Evo 950 512GB master and 12TB HDD's - 6TB mirrored. Win 10 host, but my Ubuntu machines run under it.
It has on-board NIC + a 2 port HP NIC. The 2 port NIC aggregated to 2 ports on the 'router' with the on-board NIC going to my IP cameras PoE network setup or something similar is the plan, I haven't made my mind up. But that's something else totally different.

I know there might be an issue with my 4 x NIC and should get an Intel, but I am going to see how well the one I have does, it is here:
[https://www.startech.com/uk/Networking-IO/Adapter-Cards/4-Port-PCI-Express-Gigabit-Ethernet-NIC-Network-Adapter-Card~ST1000SPEX42](https://www.startech.com/uk/Networking-IO/Adapter-Cards/4-Port-PCI-Express-Gigabit-Ethernet-NIC-Network-Adapter-Card~ST1000SPEX42)

---

### Post by 1clue on 2016-09-02
That's almost exactly the card I have on my i7. The Asus P6T motheboard in there has the same nic, so it's 5x Realtek cards.

Like you, I'd just bought my 4x Realtek nic when a guy I really respect on Gentoo forums pointed out the shortcomings. I'm not made of money, so I still haven't replaced the Realtek with Intel.

BTW if you know what cards you want, you can probably do much better on amazon or ebay. Or if you're outside the usa some other equivalent site. I got my card for just over $100 USD. I do my research by browsing something like newegg or cdw, and read the manucaturer's propaganda, and benchmark articles, and oddly enough the pfSense forum has a whole lot of people dedicated to checking relative speeds of chips, motherboards, nics, and all that.  But pfSense is based on freebsd so their drivers aren't the same as ours. But when I get a short list of what I want, I look on ebay or amazon for cheaper prices.

It's probably going to be fine for you, my i7 can get wire speed out of the cards but the CPU is just running a bit heavier is all. If you're not running near the limits then you're going to be fine. I'm running near the limits and it hurts, but not enough yet to have made me replace with an Intel nic.

I haven't seen benchmarks for your chip or your motherboard, but if you're running bare metal router on it then you'll probably have more cpu and networking than your setup requires.

My i7 still reigns supreme over the c2758 for compiling, more than 2x faster, but all the localhost networking/compression/encryption tests I've done the c2758 gets maybe 20% better than the i7.  Considering the 2758 is an atom processor I think that's pretty outrageous.

---

### Post by cackles on 2016-09-03
> **1clue said:**
> That's almost exactly the card I have on my i7. The Asus P6T motheboard in there has the same nic, so it's 5x Realtek cards.

Like you, I'd just bought my 4x Realtek nic when a guy I really respect on Gentoo forums pointed out the shortcomings. I'm not made of money, so I still haven't replaced the Realtek with Intel.

BTW if you know what cards you want, you can probably do much better on amazon or ebay. Or if you're outside the usa some other equivalent site. I got my card for just over $100 USD. I do my research by browsing something like newegg or cdw, and read the manucaturer's propaganda, and benchmark articles, and oddly enough the pfSense forum has a whole lot of people dedicated to checking relative speeds of chips, motherboards, nics, and all that.  But pfSense is based on freebsd so their drivers aren't the same as ours. But when I get a short list of what I want, I look on ebay or amazon for cheaper prices.

It's probably going to be fine for you, my i7 can get wire speed out of the cards but the CPU is just running a bit heavier is all. If you're not running near the limits then you're going to be fine. I'm running near the limits and it hurts, but not enough yet to have made me replace with an Intel nic.

I haven't seen benchmarks for your chip or your motherboard, but if you're running bare metal router on it then you'll probably have more cpu and networking than your setup requires.

My i7 still reigns supreme over the c2758 for compiling, more than 2x faster, but all the localhost networking/compression/encryption tests I've done the c2758 gets maybe 20% better than the i7.  Considering the 2758 is an atom processor I think that's pretty outrageous.

An i7 being beat by an atom? :O

As for the NIC, yea, I thought I was on to a winner. Now I can an Intel 4 port for £50GBP/$65USD ... and after being told what you found out too I'm like, nooooooooooooo! Especially since I hinted the parts down for the machine and saved a whole lot on that, had to be patient mind you.

Looks like I will need to hunt down what modules to use though, like rip off cPanel's setup somewhat.

My main problem just now is concentration though, between illness and the meds for them. I am pretty sure I will get there though.

Thanks for the input and good luck with yours.

---

### Post by 1clue on 2016-09-03
A first-gen i7 being beaten at router duties by a chip which is designed to beat higher-performance older hardware, and motherboard made specifically for router duties, built in encryption/compression acceleration and a no-nonsense board design.

So it wasn't all that big a surprise that it could beat the old i7. 600w vs 20w.

Another thing, the i7 board (Asus P6T) is maxed out at 24g and the supermicro can handle 64g.

---

