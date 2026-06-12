---
title: "Indestructible botnet"
date: 2011-07-03
forum: The Cafe
---

### Post by srisharan on 2011-07-03
Kaspersky claims of a new indestructible botnet for windows.

[http://news.cnet.com/8301-13506_3-20075725-17/tdl-4-the-indestructible-botnet/]("http://news.cnet.com/8301-13506_3-20075725-17/tdl-4-the-indestructible-botnet/")

---

### Post by Eiji Takanaka on 2011-07-03
yeah tdl4 or something ent it?

You'd think an underground internet was starting to form or something geez. 

*Does crazy eyes and looks at a marble.....an internet inside the internet.

---

### Post by grahammechanical on 2011-07-03
Did you notice the bit about it residing in the MBR? A bit scary if you dual boot. May be? Would it mess up Grub? Or would a Grub install overwrite it? Who knows. Yet.

Regards.

---

### Post by nerdy_kid on 2011-07-03
now here's a scary thought:  wouldn't a virus written in assembly and somehow attached to the MBR be able to infect Ubuntu as well?  I don't entirely know what I'm talking about so maybe not...

---

### Post by Dustin2128 on 2011-07-03
@nerdy_kid
I believe it would not be able to run in linux unless it's written in java or something, and even then it'd probably need some tweaks. If it's written in assembly as you said, I highly doubt it, running on linux is sooooooooo much different than running on windows.
Oh well [insert mildly insulting remark to windows users].

---

### Post by Madspyman on 2011-07-03
I thought the master boot record was on the hard drive. Couldn't you put a separate hard drive in there and make that the boot drive instead?

---

### Post by Dustin2128 on 2011-07-03
> **Madspyman said:**
> I thought the master boot record was on the hard drive. Couldn't you put a separate hard drive in there and make that the boot drive instead?
I thought that too, but I'm not certain enough in my knowledge of hard drives. If so, and if you were a dual booter using grub, it'd be a cakewalk to remove the virus. Simply wipe your boot partition after booting to ubuntu, reformat it for good measure, then install grub again. If that really is how it works though, then it would be in ext2 format, which I highly, Highly doubt the virus would be able to read/write in the first place.

---

### Post by doas777 on 2011-07-03
> **nerdy_kid said:**
> now here's a scary thought:  wouldn't a virus written in assembly and somehow attached to the MBR be able to infect Ubuntu as well?  I don't entirely know what I'm talking about so maybe not...
no, but I understand how you got there. an os provides execution channels by which binary code is run. without the ability to tell a sample of malcode to run, you cannot execute it in a given environment, and environments are os-family specific. 

that said, the assembly payload (if it operates on sheer Interrupt handler calls) would produce the same results on both platforms. a VXer could package the program to self execute via one vulnerability in windows, or another vulnerability in linux depending on its environment. it dramatically increases the difficult, but is conceivable.

the problem is (well, from the VXers perspective), they can't do anything useful at the assembly level. the hacker is interested in your bank account number, not your pc's ability to divide two numbers and store teh value in a register.

when you deploy a piece of very low level code, it targets a very very specific task, that has a predictable (and exploitable) impact in OS or Application code. rootkits for instance, target a number of very specific peices of the kernel memory that enumerate things that are running. they simply keep specific bits of activity from being enumerated to the kernel.
the key takeaway here is that the assembly code to create a rootkit for the windows kernel will not work the same way for the unix/linux kernels. 

this means that yes, assembly could execute on any processor for which its instructions are native, but no, that one piece of assembly code could not easily impact multiple kernel architectures.

---

### Post by psusi on 2011-07-03
What the heck does it even mean to call it "indestructible"?  Sensationalist nonsense.

---

### Post by prodigy_ on 2011-07-03
There's nothing new about malware that infects boot sectors. And it's neither undetectable nor indestructible.

---

### Post by inobe on 2011-07-04
write the drive to zeros, kiss the mbr and whatever else is on it goodbye. 

reset the bios, all settings and whatever it was flashed with, buh bye.

reset router firmware, audios.........

---

### Post by doas777 on 2011-07-04
> **prodigy_ said:**
> There's nothing new about malware that infects boot sectors. And it's neither undetectable nor indestructible.
Kasperskys comments refer to the botnet, not the malware.
This one is significant because it has a mechanism for upgrading its encryption systems on the fly, and is thus able to continually disguise its communication between peers or c&c systems, and can implement dynamic-polymorphism to defeat signature based scanning, and modifies its behavior to prevent heuristic or behavioral detection. It also provides it special mechanisms to prevent take-over by individuals attempting to steal bots to propogate a change-of-ownership as it were, making it much harder for MS or Google or Lawenforcement to take control of, as has happened to many older botnets. 
many pieces of malware have used unique special advantages, but this one seems to put many of them together.

---

### Post by Dangertux on 2011-07-04
> **doas777 said:**
> Kasperskys comments refer to the botnet, not the malware.
This one is significant because it has a mechanism for upgrading its encryption systems on the fly, and is thus able to continually disguise its communication between peers or c&c systems, and can implement dynamic-polymorphism to defeat signature based scanning, and modifies its behavior to prevent heuristic or behavioral detection. It also provides it special mechanisms to prevent take-over by individuals attempting to steal bots to propogate a change-of-ownership as it were, making it much harder for MS or Google or Lawenforcement to take control of, as has happened to many older botnets. 
many pieces of malware have used unique special advantages, but this one seems to put many of them together.

I  am not really sure this makes it any more undetectable. It will just change the way it is detected. See DNS sinkhole.

---

### Post by nerdy_kid on 2011-07-04
> **doas777 said:**
> no, but I understand how you got there. an os provides execution channels by which binary code is run. without the ability to tell a sample of malcode to run, you cannot execute it in a given environment, and environments are os-family specific. 

that said, the assembly payload (if it operates on sheer Interrupt handler calls) would produce the same results on both platforms. a VXer could package the program to self execute via one vulnerability in windows, or another vulnerability in linux depending on its environment. it dramatically increases the difficult, but is conceivable.

the problem is (well, from the VXers perspective), they can't do anything useful at the assembly level. the hacker is interested in your bank account number, not your pc's ability to divide two numbers and store teh value in a register.

when you deploy a piece of very low level code, it targets a very very specific task, that has a predictable (and exploitable) impact in OS or Application code. rootkits for instance, target a number of very specific peices of the kernel memory that enumerate things that are running. they simply keep specific bits of activity from being enumerated to the kernel.
the key takeaway here is that the assembly code to create a rootkit for the windows kernel will not work the same way for the unix/linux kernels. 

this means that yes, assembly could execute on any processor for which its instructions are native, but no, that one piece of assembly code could not easily impact multiple kernel architectures.

Thanks for a great explanation! :)

---

