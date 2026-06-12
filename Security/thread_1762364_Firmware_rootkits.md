---
title: "Firmware rootkits"
date: 2011-05-19
forum: Security
---

### Post by Noob2.0 on 2011-05-19
I've been doing some extensive research on rootkits and found some articles about how they inffect firmware. Can anyone tell if they are rootkits out in the wild infecting people's firmware or is it primarily still in the hypothetical phase? I know Microsoft has been infected with MBRs before but has linux? Could Linux be infected with an MBR? 

I know Linux has a very low infect rate when it comes to viruses. Does anyone know the infect rate when it comes to malware/rootkits?

---

### Post by inobe on 2011-05-19
bios security hardening measures are practical.

for example, some motherboards come equipped with bios security chips, routers and such can also be hardened, but usually resetting a router then reconfiguring will remove what it's infected with.

securing hardware should be the first line of defense, searching google will offer lots of information.

---

### Post by Soul-Sing on 2011-05-19
> I've been doing some extensive research on rootkits and found some articles about how they inffect firmware. Can anyone tell if they are rootkits out in the wild infecting people's firmware

i did some research as well on rootkits, found no cases of rootkits
infecting systems here on this forum.

---

### Post by lmn. on 2011-05-19
I've thought about whether it'd be possible for a virus to change your hd  firmware so it could scratch it up or something. But I doubt the  hardware allows something like this to happen by default.

---

### Post by doas777 on 2011-05-19
please be very specific about your terminology. a virus and a rootkit are mutually exclusive things. 

to infect firmware, a trojan would have to be tailored for that exact eprom and current software version, and have access to the tools to access it. i don;t believe that that can be done from userland.

usually the way you get a rootkit, is by being hacked interactively, via an application like ssh or php or whatever, compromising a low level account. then a escalation attack is used to get root, and a rootkit is installed to ensure that the attacker can keep root, even if the system administrator has noticed the original account was compromised, and fixed the input vector. a rootkit by definition must be installed with root privileges. a firmware rootkit all the more so. 

when it comes to firmware rootkits, your main worry is that you will get them from the maunfacture that way. there is big concern regarding this when it comes to international espionage. the US NSA for instance is worried about networking equipment (routers/switches/etc) manufactured in china, fearing that the asics and firmware may contain undetectable surveillance malware.

also, I wouldn't really class a mbr hijack as a firmware thing or a rootkit, but I may not be entirely correct on that.

---

### Post by Soul-Sing on 2011-05-20
rather acadmic discussion this.
this is a Ubuntu support forum, what could "we" do against possible firmware/hardware rootkits? (whatever that may be...) give recommendations where to buy (y)our hardware? Give you a blacklist of countries? (because the NSA told us to be very alert!)
Join the EFF.

---

### Post by rookcifer on 2011-05-20
> **doas777 said:**
> there is big concern regarding this when it comes to international espionage. the US NSA for instance is worried about networking equipment (routers/switches/etc) manufactured in china, fearing that the asics and firmware may contain undetectable surveillance malware.

Which is why NSA has built its own chip manufacturing plant.  Unfortunately most of us don't have access to that so we have to trust the COTS hardware we have.

As far as getting a firmware rootkit, I wouldn't worry about it.  As you said, if such a thing has affected the OP, it has probably happened at the factory and there's not much that can be done on our end.

---

### Post by doas777 on 2011-05-20
> **leoquant said:**
> 
Join the EFF.

Hear, Hear!

---

### Post by Noob2.0 on 2011-05-22
> **doas777 said:**
> please be very specific about your terminology. a virus and a rootkit are mutually exclusive things. 

to infect firmware, a trojan would have to be tailored for that exact eprom and current software version, and have access to the tools to access it. i don;t believe that that can be done from userland.

 also, I wouldn't really class a mbr hijack as a firmware thing or a rootkit, but I may not be entirely correct on that.

Thank you so much for the comment. I found it very interesting and informative. It is in agreement with the articles I have read. 

For the most part, firmware rootkits are placed on the hardware while at the manufactureres, or in route to its destination from the manufacturers. [I]John Heasman wrote an interesting thesis about firmware rootkits. He wrote that it is possible to infect hardware with rootkits from the internet but it would require the things you said in your comment above. 

As for the MBR rootkits, microsoft has been infected with them as early as 2008.  

"[/I]News broke out earlier this year of a new breed of rootkit using techniques never before seen in modern malware. The most notable of them is the fact that the rootkit **replaces the infected system's Master Boot Record** (MBR).

The MBR is the first physical sector of the hard drive and contains the first code loaded and executed from the drive during the boot process.

In the competition between rootkits and rootkit detectors, the first to execute has the upper hand. And you can't execute earlier than from the MBR. Of course, MBR viruses used to be very common in the DOS days, 15 years ago or so. But this is 2008.

This new Windows MBR rootkit launches itself very early during the Windows startup process without requiring any registry or file modifications. In fact, it is quite surprising that it's possible to write to the MBR from within Windows to begin with."

I was wondering if Linux is as vulnerable to MBR hijacking as Microsoft Operating systems are. The reason I'm so curious is because I think I might be infected with one.

---

### Post by Noob2.0 on 2011-05-22
> **leoquant said:**
> rather acadmic discussion this.
this is a Ubuntu support forum, what could "we" do against possible firmware/hardware rootkits? (whatever that may be...) give recommendations where to buy (y)our hardware? Give you a blacklist of countries? (because the NSA told us to be very alert!)
Join the EFF.


I was just inquiring on people's opinion about the possibility of firmware rootkits out in the wild. As my name suggests, I am rather rudimentary when it comes to everything linux, so I thought to ask more seasoned veterans of the technology. Whether my question was out of the scope of some here doesn't make it any less potentially prevalent. We should all stay ahead  of the curve when it comes to cyber security and firmware rootkits are the next gen threat. 

ANyway, thank you for recommending the EFF. I will take you up on that .

---

### Post by Soul-Sing on 2011-05-22
> We should all stay ahead of the curve when it comes to cyber security and firmware rootkits are the next gen threat.

indeed, and understood. this not only a support subforum, but also a [COLOR="Red"]security discussion[/COLOR] subforum.

---

### Post by inobe on 2011-05-22
> **Noob2.0 said:**
> 
This new Windows MBR rootkit launches itself very early during the Windows startup process without requiring any registry or file modifications. In fact, it is quite surprising that it's possible to write to the MBR from within Windows to begin with."

BAH sony, a well known entertainment entity responsible for rootkits, they even infringed OS code.

i think you should be more concerned about the software and hardware manufactures, third world countries, microsoft etc...

---

