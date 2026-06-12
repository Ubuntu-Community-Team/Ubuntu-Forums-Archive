---
title: "Need advice on new system (file server/VM machine)"
date: 2010-06-30
forum: The Cafe
---

### Post by CharlesA on 2010-06-30
Hi there,

I'm seriously considering building a new machine to take over my file server/VM box duties, but I'm not quite sure what would work best.

My budget is 300-400 bucks for CPU/Mobo/RAM. I've got a case, PSU, HDD, DVD, etc I can use out of the old machine.

I was thinking about basing it around an AM3 Quad Core, but I don't know for sure.

So far I have got a list of parts:

Mobo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131366](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131366)
RAM: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820148150](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148150)
CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103656](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103656)

Any suggestions would be helpful. :)

Thanks.

---

### Post by cascade9 on 2010-06-30
1st off, you have DDR2 and that motherboard needs DD3. 

You might be better off with a 8XX chipset with a SB8XX southbridge for SATAIII support, and most of the boards with that chipset have USB 3.0 as well, which is nice ;)

---

### Post by cacycleworks on 2010-06-30
imho, I'd suggest going for something not-current technology. And definitely no need for video ANYthing. Try to get gigabit on the ethernet, lots of RAM slots, and if possible, actual hardware raid.

Our server at work has a few VMs and is running a hardware raid. It's not too much of a machine ... pretty good AMD quad core (Phenom 9550), 6G of RAM (all that was laying around), and a Rosewill PCIe RAID controller. The 4 250G drives in the RAID are actually externally mounted to an aluminum plate, as they were > 150 deg F inside the case. The aluminum plate has 2 fans blowing between pairs of drives. And lots of fans in the case. The main server itself has the 1G samba shared RAID and then one VM runs our internal webserver and another VM runs the postgres database for our accounting software.

```

top - 01:30:18 up 33 days, 13:44,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.2%sy,  0.0%ni, 99.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   5911108k total,  5690768k used,   220340k free,   306956k buffers
Swap:  2584568k total,   142052k used,  2442516k free,  3627804k cached

```

[CPU is $86]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103877&cm_re=phenom-_-19-103-877-_-Product") but then I'm all about being as cheap as possible with what meets my needs for the MoBoard and other components. Not sure what our motherboard is but it has nVidia MCP78S chipset. It runs a console on 15" monitor just fine when I carry the monitor to it... otherwise is headless. 

:) Chris

---

### Post by CharlesA on 2010-06-30
> **cascade9 said:**
> 1st off, you have DDR2 and that motherboard needs DD3. 

You might be better off with a 8XX chipset with a SB8XX southbridge for SATAIII support, and most of the boards with that chipset have USB 3.0 as well, which is nice ;)

Hrm, it says DDR3.. :lolflag:

@cacycleworks: Nice rig. The one I currently have has a 2.5Ghz Dual Core, but when I am running more than 2 or 3 VMs it bogs the hell out of everything, which is why I am thinking about upgrading.

---

### Post by cascade9 on 2010-06-30
> **CharlesA said:**
> Hrm, it says DDR3.. :lolflag:
Opps, sorry...thats what I get for having to many tabs open. 

Edit- ha, figured out how I made that silly mistake....DDR3 1066. Go for 1333 or better, most of the AM3 boards have the ability to run the RAM 'overclocked' at 1600 or even higher. The board you have picked with run with 1066, but its worth the few extta $$$ you might have to pay to get 1333+. I'm also a fan of heatsinked RAM . Not that DDR3 really needs heatsinks, but it does make it easier to work on (pretty much impossible to knock of a resistor, etc). 

Not that there is anything wrong with the Phenom X4 9950 cacycleworks posted, but its outclassed, in all ways, by the newer Phenom IIs. BTW, good point on the 'dont need video at all' and if you are happy with that, then a 770/870 chipset is the way to go IMO. 

BTW, with some of AM2+/AM3 motehrboards you can 'unlock' cores on some of teh AMD CPUs. A Semperon can be turned into a Athlon II X2, and Phenom II X2 can unlock to X3/X4. I've heard that some of teh newer X4s unlock to X6, but I havent seen that done in person yet. AFAIK, the athlon X2 and X4 chips dont have any 'extra' cores to unlock.  

The setup I just built for my housemate (gigabyte 770T-USB3 and phenom II X2 550)  unlocks to X4 fine. Seems to run well unlocked, but I havent stress tested it yet. Of course, with unlocking (like overclocking) your milage may vary, and there are no  guarantees that it will work.

---

### Post by cacycleworks on 2010-06-30
Thing is, with a VM / fileserver, you don't need "cool" specs. Lots a cores + lots a RAM. Speed is pretty much irrelevant. 1066, 1333, 1600? Will the ethernet controller notice any of that when it's feeding that 60+ Meg PDF file to your laptop? Nope. What are the VMs doing? Not gaming ... or you wouldn't be here. ;) Oh, I forgot, the OS is running from a 32GB sata2 SSD. The raid mounts on its own partition. I was kinda aiming to get something pretty reliable out of this without blowing stupid money on it.

Get the most cores+RAM for the least $ and the least effort. Want faster? Run a really light linux. 

Our server's OS is ubuntu server x86_64 9.04. Our uptime is only 33 days -- because I was freaking out that one of the VMs lost its mind and I said eff it and restarted the server because I couldn't find my notes for the VM quick enough. (Sorry, my cashier was yelling at me ... the webserver runs the orders desk) With 5 or 6 office users running off the RAID, 1 to 3 people on the webserver, and 1 to 4 people hitting the postgres server, we never notice anything less than full speed.

I'm not hating on the cool new toys, just adding some reality and playing devil's advocate.

:)

---

### Post by cascade9 on 2010-06-30
> **cacycleworks said:**
> Thing is, with a VM / fileserver, you don't need "cool" specs. Lots a cores + lots a RAM. Speed is pretty much irrelevant. 1066, 1333, 1600? Will the ethernet controller notice any of that when it's feeding that 60+ Meg PDF file to your laptop? Nope. What are the VMs doing? Not gaming ... or you wouldn't be here. ;) Oh, I forgot, the OS is running from a 32GB sata2 SSD. The raid mounts on its own partition. I was kinda aiming to get something pretty reliable out of this without blowing stupid money on it.

Get the most cores+RAM for the least $ and the least effort. Want faster? Run a really light linux. 

Our server's OS is ubuntu server x86_64 9.04. Our uptime is only 33 days -- because I was freaking out that one of the VMs lost its mind and I said eff it and restarted the server because I couldn't find my notes for the VM quick enough. (Sorry, my cashier was yelling at me ... the webserver runs the orders desk) With 5 or 6 office users running off the RAID, 1 to 3 people on the webserver, and 1 to 4 people hitting the postgres server, we never notice anything less than full speed.

Well, untill VMware benchmarks become a lot more common, its hard to make comparisons (and even then there will be issues)

> Every drop of performance you wring out of your servers translates into potentially higher consolidation ratios (more VMs per physical machine) or better response time per VM.> Has smaller caches; the more VMs, the more pressure there will be on the caches.> These kinds of performance losses are relatively easy to minimize. You could buy CPUs with larger caches, and assign (set affinity) certain cache/CPU hungry applications some of the physical cores.Whole article here- 

[http://www.anandtech.com/show/2770](http://www.anandtech.com/show/2770)

Well worth a read, because I admit 100% to taking those quotes out of context. 

Phenom IIs outclass the Phenoms everywhere, not just for gaming. 4MB cache on the phemon X4 vs 8MB for the phenom II X4, I know which I would rather have for virtualisation. 

As for the DDR3 1066- well, you can get DDR3 1333 cheaper than the crucial CharlesA linked to. Maybe he (she? I doubt it but you never know) likes crucial for various reasons, but then you are getting into manufacture preference, and thats almost impossible to debate in a sane manner. 

Exit- BTW, I do agree basicly on 'get as many cores and as much RAM as possible', and if you want faster run a lighter linux. If CharlesA was really running light on the cash, then its probably worth risking getting a Phenom II X2 and unlocking it to X4. Not that big a risk, as all the Phenom II are either a X4 base chip, or X6. But still, its a risk, its always possible that one, of both the 'locked' cores are broked in some way. Getting an X4 and hoping that it would unlock to X6 isnt crazy either. 

[http://en.ocworkbench.com/tech/amd-phenom-ii-x4-960t-hidden-cores-can-be-unlocked-turning-it-into-a-phenom-ii-x6/](http://en.ocworkbench.com/tech/amd-phenom-ii-x4-960t-hidden-cores-can-be-unlocked-turning-it-into-a-phenom-ii-x6/)
  
> **cacycleworks said:**
> 
I'm not hating on the cool new toys, just adding some reality and playing devil's advocate.

:)

Ditto ;)

---

### Post by cacycleworks on 2010-06-30
> **cascade9 said:**
> As for the DDR3 1066- well, you can get DDR3 1333 cheaper than the crucial CharlesA linked to. Maybe he (she? I doubt it but you never know) likes crucial for various reasons, but then you are getting into manufacture preference, and thats almost impossible to debate in a sane manner.

Oh cool, then we agree. :rolleyes:

---

### Post by CharlesA on 2010-06-30
Heh I just searched for the cheapest RAM, and that was what I found.

As for x4 vs x6, don't both CPUs have hypertreading so that the machine thinks it's got 8/12 cores?

Erm, don't mind me, I got Hyperthreading confused with Hypertransport. :|

I guess hyperthreading is an intel thing.

---

### Post by cascade9 on 2010-07-01
Yep, hyperthreading is intel only. 

As for the RAM, newegg searches can throw out odd results. There is much cheaper 2x2GB DDR3 kits around- 

[URL="http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007611+600006050+600006066&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=147&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc="]http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007611%20600006050%20600006066&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=20
[/URL]

---

### Post by CharlesA on 2010-07-01
Thanks. :-)

I wonder if there's a huge difference between a quad core AMD vs a  quad core Intel.  I can't find anything recent, but I doubt there is much of a difference between the two.

---

### Post by cascade9 on 2010-07-02
Dividing things up into 'quad core AMD' and 'quad core Intel' has major issues.  

Intel has made a lot of quad core CPUs (core 2 quad Q6XXX, Q8XXX, Q9XXX, core 2 extreme QX6XXX, QX9XXX, i5 7XX and i7). Every one of those CPUs has different MHz, FSBs, cache levels, etc. 

Same with AMDs offereings, lots of different versions with different MHz/FSBs/cache, etc.

---

### Post by CharlesA on 2010-07-03
Indeed. It's a bit difficult to directly compare intel and AMD CPUs. :(

---

### Post by cascade9 on 2010-07-04
You can do it, but there is a lot of sodding around. Made a lot more difficult by the legion of variants on the basic theme (eg, all the different sized caches intel put into the Core 2 seires......some things like more cache, some like more mHz) 

Probably the best site for general intel vs AMD is tomshardware, just check the 'charts'.

---

### Post by CharlesA on 2010-07-04
Thanks. :)

As a sidenote: I suppose I should find out why my current machine doesn't display the CPU temp when it runs landscape-sysinfo. Most sites point to a buggy BIOS but I don't know. =/

---

