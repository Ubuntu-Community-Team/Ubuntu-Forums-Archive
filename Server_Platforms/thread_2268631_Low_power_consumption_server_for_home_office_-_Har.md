---
title: "Low power consumption server for home office - Hardware choices?"
date: 2015-03-10
forum: Server Platforms
---

### Post by joker535 on 2015-03-10
After 6 years of 24/7 service my MSI wind nettop with an Atom 230 finally died (caps popped on the motherboard) so its time for a new server. This machine was serving 4 websites (2 wordpress and 2 static sites one of which is a business site), serving NAS duty for storage and backups, serving music and videos to our other devices, and acting as an SSH tunnel. The old system had a pair of enterprise class sata drives in it but still managed to pull under 35W at full load. I want to be able to run a hypervisor with a couple of VMs on the new one but I want to keep the power use under 50W total. This means I need either an 8 core Atom C2750 (8 cores no HT and 20W) or a low power E3-1230Lv3 (4 cores with HT and 25W). Both are passively cooled, have similar ram power consumption, and will use the same drives so its down to MB/CPU decision time. The small price difference is not a concern. 

If you had a choice between this combo:

Intel Xeon E3-1230Lv3 -  Link removed

Supermicro X10SLM+_F-O - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813182823](http://www.newegg.com/Product/Product.aspx?Item=N82E16813182823)

Or this one:

Supermicro C2750 Atom board - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813182851](http://www.newegg.com/Product/Product.aspx?Item=N82E16813182851)

Which one would you choose and why?

Do you think the 4 core hyperthreaded Xeon will be faster/more powerful/more capable than the 8 core Atom in a hypervisor environment?

I am going to buy one of these 2 options and I am not interested at looking at anything else. 

What hypervisor do you think would run best on either of these setups?

Thanks in advance

Bob

---

### Post by tgalati4 on 2015-03-10
The Xeon probably has better internal data paths and better cache management for vms.   I have always liked Xen for vms, but Google has recently open-sourced their vm solution:  [http://kubernetes.io/](http://kubernetes.io/)  It offers some advantages over traditional vm approaches.

---

### Post by joker535 on 2015-03-11
I suspect I will end up with the Xeon. I have been searching for days for info on pros and cons of the Xeon vs Atom but so far there is little real world info. 

I have been leaning heavily toward Xen but I have been looking at other options. I expect to be running nothing but linux guests but I want to have the option to host a Windows VM should the need arise. I had considered the free Hyper-V core as I am familiar with the licensed version it but it might be hard to manage since I have no Windows machines here to manage it with.

---

### Post by tgalati4 on 2015-03-11
Was your motherboard not repairable?  Replacing capacitors is not difficult.

---

### Post by joker535 on 2015-03-11
It is technically repairable. Replacing a dozen caps is not too big of a deal but I suspect I have gotten all the life there is to get out of that machine. I could repair it adnt hen something else may fail. I would rather spend $1000 for something fresh and stable.

---

### Post by tgalati4 on 2015-03-12
That would be a good machine to donate to a local linux user's group.  Somebody should at least attempt to repair it.

---

### Post by joker535 on 2015-03-12
Unfortunately there is no local group. The closest is over an hour away and never responded when I attempted to join. There is not a lot of tech savvy folks here at the beach. 

I have removed the link to the vendor with the Xeon. Since posting it, others followed it and bought all of the ones in stock. Now I have to wait for one. Should have thought that out better.

---

### Post by tgalati4 on 2015-03-12
That is the beauty of open source.  You do the heavy lifting for others.  Post a listing on Craigslist.  Somebody will want it.  [Southeast linux fest]("http://www.southeastlinuxfest.org/") is happening in your area in a few months.  

Let us know how your new server works out.

---

### Post by gordintoronto on 2015-03-12
The only problem with the Xeon is availability in the retail channel. There are other models which have integrated graphics and use more power, which might be an OK tradeoff.

---

### Post by joker535 on 2015-03-13
Since this is a headless server tucked away in my wiring closet the integrated graphics are just wasted power being turned into heat. I have found a retailer that can get me the E3-1230Lv3 (or E3-1240Lv3).

---

### Post by joker535 on 2015-03-30
> **gordintoronto said:**
> The only problem with the Xeon is availability in the retail channel. There are other models which have integrated graphics and use more power, which might be an OK tradeoff.

I actually had no problem getting the Xeon E3-1230Lv3. Its special order everywhere (its an OEM chip) but I had it in less than a week for $260.85 shipped ground.

[http://www.wiredzone.com/intel-components-cpu-processors-server-cm8064601467601-10023639](http://www.wiredzone.com/intel-components-cpu-processors-server-cm8064601467601-10023639)

---

### Post by joker535 on 2015-03-30
I ended up with the Xeon setup. I am glad I did and the extra cost was worth it. If you are reading this and considering the same thing, the E3-1230Lv3 or E3-1240Lv3 are an excellent choice. 

The Xeon, MB, and passive heat sink cost me $475.61 shipped.

The 8 core C2750 atom board is $358.99 shipped.

For $116.60 extra I can have 4 VMs running all at the same time and it does not even sweat. I may add another 16G of ram and run some more.

---

