---
title: "Think Linux is safe?"
date: 2006-08-26
forum: The Cafe
---

### Post by Anduu on 2006-08-26
Of course it is.

However someone always seems to find a way around just about every secure system....

[http://www.computing.co.uk/vnunet/news/2163054/virus-attacks-amd-processors](http://www.computing.co.uk/vnunet/news/2163054/virus-attacks-amd-processors)

I am sure if this were to ever become a high level threat some sort of defense would be developed.

---

### Post by Tomosaur on 2006-08-26
While the security hole is at a hardware level, and thus unrelated to the OS, the fact remains that actually becoming infected by this virus is about a billion times more unlikely on linux than it is on windows.

---

### Post by peabody on 2006-08-27
If this is supposed to be cross operating system, why's it prefixed with w32 nd w64?  Anyway, you'd still need two version, the core of the code would be the same, but windows and linux binary formats aren't the same, so you'd need different code to get it loaded.  Although, now that you mention it, wine might actually end up running it...hmmm... that's interesting...

---

### Post by prizrak on 2006-08-27
> **Tomosaur said:**
> While the security hole is at a hardware level, and thus unrelated to the OS, the fact remains that actually becoming infected by this virus is about a billion times more unlikely on linux than it is on windows.

How so? It makes no difference what you run it bypasses the OS completely. 

> If this is supposed to be cross operating system, why's it prefixed with w32 nd w64? Anyway, you'd still need two version, the core of the code would be the same, but windows and linux binary formats aren't the same, so you'd need different code to get it loaded. Although, now that you mention it, wine might actually end up running it...hmmm... that's interesting...
Because there is a 32bit version that runs on 32bit AMD CPU's and a 64bit version that runs on 64bit AMD CPU's. The amount of "bits" on the CPU is completely unrelated to the OS, for instance DOS was 8 and 16bit but will run quite happily on a 32bit CPU. 

A binary is run by an OS this virus is basically an OS in itself. I'm not sure what venue it uses for getting on the machine but would probably be run at boot or get loaded straight into memory over the network through DMA.

---

### Post by daou on 2006-08-27
> The w32.bounds and w64.bounds viruses infect systems by tying themselves to Windows executable files, which disqualifies them as so-called chip level threats. They do however employ elements of such attacks by showing an ability to executive chip level assembly code.

I wouldn't consider it a problem unless you like to run random exe files through wine or dual boot with the same mindset.

---

### Post by peabody on 2006-08-27
> **prizrak said:**
> 
Because there is a 32bit version that runs on 32bit AMD CPU's and a 64bit version that runs on 64bit AMD CPU's. The amount of "bits" on the CPU is completely unrelated to the OS, for instance DOS was 8 and 16bit but will run quite happily on a 32bit CPU. 


I understand that, I'm talking about the "w" prefix.  I that was a naming convention for windows virus'.

---

### Post by Mathiasdm on 2006-08-27
> **prizrak said:**
> How so? It makes no difference what you run it bypasses the OS completely. 


Because there is a 32bit version that runs on 32bit AMD CPU's and a 64bit version that runs on 64bit AMD CPU's. The amount of "bits" on the CPU is completely unrelated to the OS, for instance DOS was 8 and 16bit but will run quite happily on a 32bit CPU. 

A binary is run by an OS this virus is basically an OS in itself. I'm not sure what venue it uses for getting on the machine but would probably be run at boot or get loaded straight into memory over the network through DMA.
Bweh, it can't bypass the OS completely. You need a user that's 'smart' enough to execute the required file.

---

### Post by Cynical on 2006-08-27
> **prizrak said:**
> The amount of "bits" on the CPU is completely unrelated to the OS, for instance DOS was 8 and 16bit but will run quite happily on a 32bit CPU. 

What are you talking about? There are no "bits" on a cpu. When you are speaking in terms of 64-bit you are talking about a computer architecture with registers that are 64-bits wide. And no its not completely unrelated to the OS. Obviously an OS that requires smaller chunks of data to go through registers that support larger chunks will work. But one that requires data chunks that are larger than what the registers support won't.

> **prizrak said:**
> 
A binary is run by an OS this virus is basically an OS in itself. I'm not sure what venue it uses for getting on the machine but would probably be run at boot or get loaded straight into memory over the network through DMA.

I'm not quite sure what the Danish Medical Association has to do with networking...

---

### Post by daou on 2006-08-27
> I'm not quite sure what the Danish Medical Association has to do with networking...

I always thought it was the Dutch Mill Association :rolleyes: .

---

### Post by OffHand on 2006-08-27
It is still a Proof of concept. It's not out there in the wild atm as far as I know.

---

### Post by Tomosaur on 2006-08-27
> **prizrak said:**
> How so? It makes no difference what you run it bypasses the OS completely. 


So it's a magic virus that spreads through the power supply? :P

The point is - you need to get the virus onto your system first, before it has any chance of affecting you. Unless you're an idiot, you don't open and run every single randomly named file you get sent by people you don't know. It has little chance of infecting you through other means, since linux is more secure than windows anyway.

---

### Post by Ramses de Norre on 2006-08-27
Would such a virus require root privileges to run?

---

### Post by Cynical on 2006-08-27
Not to run, but to do anything devasting to your computer yes it would require root privileges. I like the way linus referred to this virus.

[http://www.infoworld.com/article/06/04/19/77568_HNlinuxpatch_1.html](http://www.infoworld.com/article/06/04/19/77568_HNlinuxpatch_1.html)

---

### Post by Anduu on 2006-08-27
> **Cynical said:**
> Not to run, but to do anything devasting to your computer yes it would require root privileges. I like the way linus referred to this virus.

[http://www.infoworld.com/article/06/04/19/77568_HNlinuxpatch_1.html](http://www.infoworld.com/article/06/04/19/77568_HNlinuxpatch_1.html)

Wrong virus...

---

### Post by peabody on 2006-08-27
> **Ramses de Norre said:**
> Would such a virus require root privileges to run?

Supposedly no because it manages to bypass the OS in assembly.

---

### Post by kenweill on 2006-08-27
> 
he w32.bounds and w64.bounds viruses infect systems by tying themselves to Windows executable files, which disqualifies them as so-called chip level threats. They do however employ elements of such attacks by showing an ability to executive chip level assembly code.


Windows executable files. Right.
I guess it wont affect Linux.
But what if it is tied in a Windows executable files installed in WINE?

---

