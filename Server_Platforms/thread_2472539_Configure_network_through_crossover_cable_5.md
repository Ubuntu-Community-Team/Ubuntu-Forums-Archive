---
title: "Configure network through crossover cable 5"
date: 2022-03-02
forum: Server Platforms
---

### Post by netw844f on 2022-03-02
Hello fellows,

I am trying connect Ubuntu Server 18.04 LTS with Window10 through crossover cable 5e. This is the output of my 50-cloud-init.yaml file, through command "sudo nano /etc/netplan/50-cloud-init.yaml":
[https://ibb.co/F49Yvr3](https://ibb.co/F49Yvr3)

On side on my windows10 I have this configurations:
[https://ibb.co/m9D6tnt](https://ibb.co/m9D6tnt)

I only get, on maximum velocity, 1.10 MB/s, when I tried transfer files to the ubuntu server through windows 10 with File Explorer - aka copy and paste:
[https://ibb.co/3CG2rVy](https://ibb.co/3CG2rVy)

How should I configure all systems (network card) to can connect this two pc through crossover cable?

Thanks

---

### Post by TheFu on 2022-03-03
I can't see those images. Sorry.
The trick is to put both systems on the same subnet with different IPs, then set the "gateway" to the other device's IP address.
Finally, use IP addresses to access each other.

If 1 of the computers uses GigE ethernet, you don't need a cross-over cable. The GigE standards automatically recognize the connection type and do the right thing. I've never seen that fail the last 15+ yrs.  If **both** computers are 10/100 base-tx connected, then you'll need a crossover cable.

Using any drag-n-drop to move files will always be slower. Use rsync.

---

### Post by The Cog on 2022-03-03
That speed is remarkably close to 10 Mbit/Sec. Are you sure they haven't settled on 10M as the link speed between them?

---

### Post by TheFu on 2022-03-03
> **The Cog said:**
> That speed is remarkably close to 10 Mbit/Sec. Are you sure they haven't settled on 10M as the link speed between them?

A bad NIC, bad cable, bad driver or improper routing can really slow things down.

Typically, it is a bad cable. Even a cable that worked yesterday could go bad just from unplugging it and moving it to another device today. I've seen this - seldom - but it is the most common. So is thinking that you have CAT5e vs CAT5 cables. People find an old cable and use it, but discover it isn't actually CAT5e. Quality CAT5 and higher cables will actually have the CAT5e written on the cable itself. There are also plugs that can drop a quality cable down to slower speeds if not built correctly. If you created the cable yourself, check that.  Monoprice makes good, cheap, cables, if you need to replace all the cables in your house.  Buying 10+ cables at a time makes it easy to trash the bad cables. Cables bought at big-box storage or in qty smaller than 10 are crazy expensive for what we get.

If routing is correct - the 2 gateway settings point to the opposite computer, then it could be either a NIC that is failing or had the wrong driver.  To research that, you'll need to see which NIC it is model and revision, then verify that's the correct driver. Realtek is famous for releasing different NICs using different chips, but having the exact same model. Most work fine. Some worry poorly.  Some don't work at all. That's where the NIC revision matters. **lshw -C network** will report on that, but you have a chicken-egg problem. Hard to load non-default software when there isn't an networking.  I was looking at lspci a few days ago and didn't see a clear "revision:" in the output.

---

### Post by MAFoElffen on 2022-03-05
I do this for ADHOC networking... Just as TheFu described with static address settings.

If all is set right (networking-wise), the bottleneck for me is in the machine's controllers and disks. You are not going to get 1GB speed of the NIC in your reads and writes, but is much faster than USB transfers. Just saying.

---

