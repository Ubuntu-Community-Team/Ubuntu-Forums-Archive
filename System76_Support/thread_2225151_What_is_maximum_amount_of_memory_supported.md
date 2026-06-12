---
title: "What is maximum amount of memory supported?"
date: 2014-05-20
forum: System76 Support
---

### Post by jcllings on 2014-05-20
3rd Generation Intel Core i7-3610QM Processor ( 2.30GHz 6MB L3 Cache - 4 Cores plus Hyperthreading )						
16 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 8 GB						

This is my awesome System76 laptop. When I got it, I couldn't afford much for memory, was only able to get 16 Gb but now I've got some more cash and would like to max it out.  Why? I've noticed that when you reach the point where your box is getting slow and you want a memory upgrade, there isn't any by that time remaining in the market for your machine. ...so I like to get this out of the way before I need it since i will eventually regardless. 

Question: How can I figure out how much memory these two DDR3 slots can handle? It's not explicitly mentioned in the BIOS. Is there a way to do this without cracking open the case to get the motherboard model number for reference?

---

### Post by grahammechanical on 2014-05-20
Why do you not go on the System76 web site and look up your machine? Then you might see something like this

> [COLOR=#000000][FONT=Ubuntu]Up to 16 GB 204 pin Dual Channel DDR3 @ 1600 MHz[/FONT][/COLOR]

Regards.

---

### Post by slickymaster on 2014-05-20
Moved to the **System76 Support** sub-forum.

---

### Post by MoebusNet on 2014-05-20
In Terminal, type:

```
sudo dmidecode
```

That should tell you the maximum RAM supported for your motherboard. From: [http://ubuntuforums.org/showthread.php?t=1224006](http://ubuntuforums.org/showthread.php?t=1224006)

---

### Post by jcllings on 2014-05-20
> **grahammechanical said:**
> Why do you not go on the System76 web site and look up your machine? Then you might see something like this

Regards.

Well, The information I had posted regarding the hardware actually is a cut 'n paste from their site.  I suppose I could bug System76 Support but IDK how long that support contract actually runs. 
You would think they would see this as a marketing opportunity to sell me some memory but it doesn't appear that they sell much in the way of individual parts.

---

### Post by jcllings on 2014-05-20
It's already maxed out at 16 Gb according to System76 support.

---

### Post by untrustytahr on 2014-05-20
```
sudo dmidecode -t 16
```

Will display max capacity

---

### Post by matt_symes on 2014-05-20
Hi

You can get all the information with

sudo dmidecode -t memory

For total allowed memory, look on the memory controller.

sudo dmidecode -t 5 | grep -i memory

Kind regards

---

### Post by jcllings on 2014-05-20
> **untrustytahr said:**
> ```
sudo dmidecode -t 16
```

Will display max capacity
...
> **matt_symes said:**
> Hi

You can get all the information with

sudo dmidecode -t memory

For total allowed memory, look on the memory controller.

sudo dmidecode -t 5 | grep -i memory

Kind regards

Wow, those commands are awesome and definitely going into my alias collection! :-) :-)

...and look what I found out despite what System76 was telling me:

johndoa@machine:~$ sudo dmidecode -t 16
[sudo] password for johndoa: 
# dmidecode 2.12
# SMBIOS entry point at 0x000f04c0
SMBIOS 2.7 present.

Handle 0x0049, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Hmmm... what is meant above by 4 devices? Not memory slots, I hope because I only saw 2 when I had the case opened earlier. ...or could there be two more tucked away somewhere?

---

### Post by jcllings on 2014-05-20
One question always leads to another. :-/

OK so now what I am hearing is that only 8Gb per channel are supported and there are only 2 memory slots I've been able to find.

Since the board only has 2 slots, it only supports 16Gb max but IMHO if the CPU supports 32 Gb, it seems illogical that the mobo would only support 16Gb max. I've seen plenty less logical hardware idiosyncrasies before though. 

How can I check what the maximum amount of memory per slot is?

---

### Post by QIII on 2014-05-20
Hello!

What your CPU can handle and what your motherboard can supply are two unrelated matters.

The electronics on your motherboard are designed to handle a maximum of 16GB if that is specified by System76.

An anology:  If you have a "walking" water sprinkler that will handle 32 gallons per minute and a pump that will only supply 16 gpm, the best you can hope for is a throughput of 16 gallons per minute -- unless you buy a 32 gpm pump.

The mobo, in this case, is your pump.  It can only handle 16GB of RAM.  It doesn't matter that your CPU, or sprinkler, can manage 32GB of RAM.

Your motherboard is the limiting factor.  If System76's literature indicates that the maximum RAM is 16GB, then it is reasonable to assume that each of the slots will have a maximum of 8GB, unless a 16GB module will work in ONE slot.  It wouldn't do any good to put 16GB in each slot, since it just wouldn't get used -- or worse.  I'd go with what System76 gives as the maximum.

Hope that made sense!

Cheers!

---

### Post by jcllings on 2014-05-20
> **QIII said:**
> Hello!
What your CPU can handle and what your motherboard can supply are two unrelated matters.
The electronics on your motherboard are designed to handle a maximum of 16GB if that is specified by System76.
An anology:  If you have a "walking" water sprinkler that will handle 32 gallons per minute and a pump that will only supply 16 gpm, the best you can hope for is a throughput of 16 gallons per minute -- unless you buy a 32 gpm pump.
The mobo, in this case, is your pump.  It can only handle 16GB of RAM.  It doesn't matter that your CPU, or sprinkler, can manage 32GB of RAM.
Your motherboard is the limiting factor.  If System76's literature indicates that the maximum RAM is 16GB, then it is reasonable to assume that each of the slots will have a maximum of 8GB, unless a 16GB module will work in ONE slot.  It wouldn't do any good to put 16GB in each slot, since it just wouldn't get used -- or worse.  I'd go with what System76 gives as the maximum.
Hope that made sense!
Cheers!

It makes sense but the lack of clarity is pretty annoying.  Especially since it says nothing about this in the literature. What we've got here is the following:

1. There's a bug in dmidecode if it reports the wrong maximum memory. Where do I report this?
2. The System76 documentation at [http://bit.ly/1k3t3y2](http://bit.ly/1k3t3y2) isn't at all clear about what the system does or doesn't have for memory capabilities. Please fix / report / tell me where I can report  this.

---

### Post by MoebusNet on 2014-05-20
> **jcllings said:**
> It makes sense but the lack of clarity is pretty annoying.  Especially since it says nothing about this in the literature. What we've got here is the following:

1. There's a bug in dmidecode if it reports the wrong maximum memory. Where do I report this?
2. The System76 documentation at [http://bit.ly/1k3t3y2](http://bit.ly/1k3t3y2) isn't at all clear about what the system does or doesn't have for memory capabilities. Please fix / report / tell me where I can report  this.

From [https://launchpad.net/ubuntu/precise/+package/dmidecode](https://launchpad.net/ubuntu/precise/+package/dmidecode)
>  Beware that DMI data have proven to be too unreliable to be blindly trusted. Dmidecode does not scan the hardware, it only reports what the BIOS told it to.

In my case, dmidecode claims that my antique Dell D800 can only use 1 Gb RAM, even though Dell's specs claim max capacity 2Gb, which I am currently running. :)

I know this doesn't solve your question, but it's the best I can come up with for now.

---

