---
title: "encryption defeated with compressed air"
date: 2008-03-26
forum: Security Discussions
---

### Post by anathema415 on 2008-03-26
[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")

Don't know if anyone's seen this yet. I'm not a techie so I'm not sure if the boot-time encryption on the Ubuntu install is vulnerable or not.

---

### Post by solitaire on 2008-03-26
All kinds of software encryption will be vulnerable to this attack..since it has to load the key into memory before decrypting the drive....

---

### Post by Oldsoldier2003 on 2008-03-26
> **anathema415 said:**
> [http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")

Don't know if anyone's seen this yet. I'm not a techie so I'm not sure if the boot-time encryption on the Ubuntu install is vulnerable or not.
No OS or computer is "safe" if someone has physical access to the machine.

---

### Post by wieman01 on 2008-03-27
> **Oldsoldier2003 said:**
> No OS or computer is "safe" if someone has physical access to the machine.
It will be safe as soon as it is turned off. Otherwise disk encryption would not make sense at all.

---

### Post by hyper_ch on 2008-03-27
> **wieman01 said:**
> It will be safe as soon as it is turned off. Otherwise disk encryption would not make sense at all.

Even turned off it's not safe as it still can be hacked by brute-force... even if it takes a little while...

---

### Post by wieman01 on 2008-03-27
> **hyper_ch said:**
> Even turned off it's not safe as it still can be hacked by brute-force... even if it takes a little while...
OK, that's always an option. There is no such thing as 'unbreakable'. Maybe Fort Know is but I seriously doubt it. But then the question is whether the assets you are trying to protect are worth it. If they aren't, an attacker won't bother because brute force can be expensive. You are protected by a trade-off an attacker will have to make.

[Quantum cryptography]("http://en.wikipedia.org/wiki/Quantum_cryptography") will be the solution one day, I am sure.

---

### Post by solitaire on 2008-03-27
Even if the machine is turned off the data is still held in ram for 5 mins (at room temp) and up to a few hours (if cooled buy liquid nitrogen before the original 5 mins are up).

Best thing to do is run mem check before shutting down the PC for the night (or before you go out)

---

### Post by hyper_ch on 2008-03-27
> **solitaire said:**
> Best thing to do is run mem check before shutting down the PC for the night (or before you go out)

Shutting down the computer... are you crazy ^^

Maybe not even run that manually but at an init scrit that does it upon shutting down..

---

### Post by mozetti on 2008-03-27
> **hyper_ch said:**
> 
Maybe not even run that manually but at an init scrit that does it upon shutting down..

I was wondering about that. In XP there was a setting you could turn on with one of the MS PowerToys that cleared RAM on shutdown. Is there such a setting in linux, other than running the memtest? Just curious.

---

### Post by hyper_ch on 2008-03-27
have a look at the runlevels in ubuntu (init.d)

---

### Post by Biochem on 2008-03-27
> **solitaire said:**
> Even if the machine is turned off the data is still held in ram for 5 mins (at room temp) and up to a few hours (if cooled buy liquid nitrogen before the original 5 mins are up).

Liquide Nitrogen make rubber band brittle as a 1 mm thick sheet of glass. I wonder how one would be able to manipulate it before it heats up and loose it's data?

---

### Post by solitaire on 2008-03-27
It only takes a few mins to dump the contents of a memory chip into a file.
so if it was deep frozen before the five min mark then you have ample time to stick it in another machine and pull the data.

---

### Post by CarrotRevelation on 2008-04-09
From the Article at [http://www.securityfocus.com/brief/712]("http://www.securityfocus.com/brief/712")
By Robert Lemos
-----------------------------------
"When we put this together and plugged it in, what did we find? Boatloads of passwords," he said.

On Linux, the Gnome Desktop Manager stores, not only the login password in memory, but other passwords as well, the researchers found. The researchers discovered passwords for the Thunderbird e-mail client and secure shell (SSH) program. On Windows, Outlook stored its passwords in ASCII, while other programs -- such as AOL Instant Messenger -- stored passwords in Unicode.
-----------------------------------

What I'm wondering is how will they treat the memory module like non-volatile memory. They should be able to plug in and provide power to keep the memory resident, but how will/do they prevent an OS kernel and related files from overwriting the forensic memory? Are they tethering the module as non-vol after the O.S. has loaded? I guess it's time to track down these researchers on the web.

Does Canonical have any initiatives regarding this issue? We already know that memory can be dumped remotely.

Edit: Never mind. I'm reading the [http://citp.princeton.edu/pub/coldboot.pdf]("http://citp.princeton.edu/pub/coldboot.pdf")        right now and it answers a lot of questions.

---

### Post by netlogic on 2008-04-11
> **hyper_ch said:**
> Even turned off it's not safe as it still can be hacked by brute-force... even if it takes a little while...

not exactly... you will need about 1000 servers to break AES within a year. if you have that much of sensitive information that the govt wants, i would say you must be a terrorist or spy.

> I was wondering about that. In XP there was a setting you could turn on with one of the MS PowerToys that cleared RAM on shutdown. Is there such a setting in linux, other than running the memtest? Just curious.

Not true. Those tools erase the XP cache. If it completely erase your memory, it will crash your computer right away.

If you are that paranoid, try this...
1. sudo swapoff -a
2. sudo swapon -a
3. boot to another linux distro (install DSL or something small)
4. in the terminal create one large file depends on the size of the ram...
dd if=/dev/zero of=file bs=1024 count=1000
5. remove the file

---

### Post by brian_p on 2008-04-11
> **netlogic said:**
> not exactly... you will need about 1000 servers to break AES within a year. if you have that much of sensitive information that the govt wants, i would say you must be a terrorist or spy.

A very rough calculation indicates the time to brute force a 128 bit AES to be longer.

There are 2^128, about 10^38, possibilities to be tried. A decent supercomputer does 1 petaflop. With 1,000 such machines 10^20 seconds is needed.

---

### Post by Rhubarb on 2008-04-11
> **solitaire said:**
> It only takes a few mins to dump the contents of a memory chip into a file.
so if it was deep frozen before the five min mark then you have ample time to stick it in another machine and pull the data.

Not true, the only purpose of freezing the RAM is to allow the RAM to retain it's memory for longer periods of time while no power is given to the RAM (ie while the PC is off / RAM is transferred to another PC).

This is how RAM works.  If you needed to cool RAM for it to remember it's contents, then everyone that uses a computer would need their RAM cooled while their computer is on.

---

### Post by netlogic on 2008-04-11
> **brian_p said:**
> A very rough calculation indicates the time to brute force a 128 bit AES to be longer.

There are 2^128, about 10^38, possibilities to be tried. A decent supercomputer does 1 petaflop. With 1,000 such machines 10^20 seconds is needed.

Agree. It will take a long time even with pre-computed tables. I have recently saw 16gig Rainbow tables floating around, but still it will take a really long time. I really don't understand how kids go around telling people, "I owned you by mad skills." Most of these hacks are social engineering and require very little programming skills.  The best bet to beat the crooks are always be paranoid and always question the technology and don't apply technology until you fully understand how they work.

---

### Post by mrsteveman1 on 2008-04-11
Rainbow tables are only useful to convert unsalted hashes into the corresponding plaintext. Truecrypt and LUKS specifically use a salted hash of the password in the volume header, so tables won't help you there. If you have access to the memory you already have the real encryption key in usable form, so the table won't help much there either. 

Most softwares encryption keys aren't dictionary words or common character strings anyway, they tend to be long strings of pseudorandom data encrypted with the salted hash of the users password. The only weak point is when the actual usable encryption key is stored in memory, brute forcing a 128bit AES cipher with a 256bit key would take much, much too long to be a useful method of attack.

With the memory thing, as long as the program you are using to recover the memory contents runs in real mode (and thus is very tiny), you aren't likely to overwrite anything important.

The real solution here is to either not trust your computer at all, or physically protect the chips (including any CMOS reset switches). For instance, the Ironkey usb stick encases its chips in resin to prevent someone from tapping the bus lines or otherwise tampering with the chips to circumvent normal security. It also destroys the encryption keys and the chip itself if it detects tampering.

Something similar would have to be done with a laptop to really protect against the memory attack.

---

### Post by netlogic on 2008-04-11
> **mrsteveman1 said:**
> Rainbow tables are only useful to convert unsalted hashes into the corresponding plaintext. Truecrypt and LUKS specifically use a salted hash of the password in the volume header, so tables won't help you there. If you have access to the memory you already have the real encryption key in usable form, so the table won't help much there either. 
.

RIGHT... We weren't talking about Truecrypt. I think we are talking about the nature of encryption. Truecrypt is one of many disk encryption tool out there.
Yea, truecrypt is becoming the choice for many people. However, salt just complicates the dictionary attack.

> Most softwares encryption keys aren't dictionary words or common character strings anyway, they tend to be long strings of pseudorandom data encrypted with the salted hash of the users password. The only weak point is when the actual usable encryption key is stored in memory, brute forcing a 128bit AES cipher with a 256bit key would take much, much too long to be a useful method of attack.

Right. 128bit and 256bit is a large bits of data. However, fictional people claim they are almost finishing up with Quantum attack. I doubt it.

> With the memory thing, as long as the program you are using to recover the memory contents runs in real mode (and thus is very tiny), you aren't likely to overwrite anything important.

I disagree. Can you explain further how you came up with this statement?

---

### Post by mrsteveman1 on 2008-04-11
Salts complicate the use of a rainbow table to convert a known password hash into the real password. With volume encryption, you don't have the real password OR the hash. Tables don't help

Real mode code has to load in under 1mb of memory because the address space is 20bits long, hence you would likely avoid overwriting the memory where the key is. The recent stories in the news discuss using a USB key or a netboot server to load code to extract the memory after a reboot. Running in real mode or otherwise controlling where your forensic tools load in to memory would help prevent the key from being overwritten.

---

### Post by netlogic on 2008-04-11
> **mrsteveman1 said:**
> 
The recent stories in the news discuss using a USB key or a netboot server to load code to extract the memory after a reboot. Running in real mode or otherwise controlling where your forensic tools load in to memory would help prevent the key from being overwritten.

I think we got each others information mixed up. Right, I knew about this. That is why I suggested about creating a 250 megs partition for DSL without a window manager to create a new device on the ram. I was assuming you knew a way to recover the overwritten data of the ram.

---

### Post by mrsteveman1 on 2008-04-11
yea :D

This is where it gets interesting, the research paper says the tools they used are tiny, the USB one is a modified syslinux, which they say is only 10KB in size. Syslinux, i believe, runs in real mode, which avoids overwriting a lot of the memory space. Plus its tiny anyway, so its not likely to overwrite much.

The PXE one they say is 9KB and does nothing but stream memory over the network as UDP packets. PXE code is also real mode by default (afaik).

The other thing they claim is that it doesn't really matter if the key gets corrupted, they even expect it. The memory decays over time and starts immediately, so you can expect some of the key to have been overwritten.  They say they have a method of determining the key quickly despite the decay.

The paper does discuss ways to overwrite memory, and suggests that programs overwrite the keys in memory after using them.

Something else i found interesting, they say they have written a small program to mount bitlocker drives under linux, they call it BitUnlocker :D

---

