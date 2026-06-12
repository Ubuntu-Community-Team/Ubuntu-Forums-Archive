---
title: "[SOLVED] Vista OEM won't let me register?!?"
date: 2008-01-18
forum: Virtualisation
---

### Post by rune0077 on 2008-01-18
I'm sure this has come up before, but nothing showed up in the search. I have a full Vista dvd purchased as OEM software. I removed it completely from my hard disk and merged the freed-up space with my Ubuntu partition. The idea was then to run Vista on VirtualBox. 

This was not the best of ideas, because now I can't register Vista, which means it'll stop functioning in twenty-something days. Installation went fine, it's just the registering that causes issues (it basically says that my version is already registered to another machine). It's the same god damn machine, though, and as far as I can tell I haven't broken any license, right?

So my two questions is: is it either 1) possible to work around this issue with registering, or 2) possible to make my host-Vista actually recognize my real motherboard rather than the virtual one?

I need Vista for a few basic things (most specifically my banking), but I'm sure as hell not paying for a new license, and Microsoft refuses to offer support for OEM versions.

---

### Post by Nem1976 on 2008-01-18
Honestly this is has been an issue with MS since XP Activation.  I have a legal copy of XP but reload every 6 months or so.  You should have an option to contact MS regarding the activation if they ask you if you have activated before tell them yes but you and  reinstall the OS because your HDD died or something.  I have done this countless times and its still legal and your not going to have to hack your Vista to get the activation issue fixed.

---

### Post by Joeb454 on 2008-01-18
Phone Microsoft and explain that it won't allow you to register.

I did that because it refused to register my key, and they told me to put in a code and then all was fine :)

It's a free phone number too (or at least it is in the UK)

---

### Post by rune0077 on 2008-01-18
Yeah okay, I guess I have to call them. It's a really annoying issue, though.

---

### Post by dcstar on 2008-01-18
> **rune0077 said:**
> I'm sure this has come up before, but nothing showed up in the search. I have a full Vista dvd purchased as OEM software. I removed it completely from my hard disk and merged the freed-up space with my Ubuntu partition. The idea was then to run Vista on VirtualBox. 

This was not the best of ideas, because now I can't register Vista, which means it'll stop functioning in twenty-something days. Installation went fine, it's just the registering that causes issues (it basically says that my version is already registered to another machine). It's the same god damn machine, though, and as far as I can tell I haven't broken any license, right?
..........

There is a thread in these forums that specifically states that some Vista licences forbid use in a Virtual environment:

[http://ubuntuforums.org/showpost.php?p=3956634&postcount=10](http://ubuntuforums.org/showpost.php?p=3956634&postcount=10)

---

### Post by Nem1976 on 2008-01-18
Wow Interesting I didn't know that about vista.  Just another reason not to use it I guess.

---

### Post by David Ostrom on 2008-01-18
What is Vista? Is this a new OS, is it any good? I don't get out much.

---

### Post by SidewinderPro2 on 2008-01-18
It doesn't even compare to the stability and reliability of XP in any way, shape, or form. Its extremely buggy and prone to crashing and blue screening. The only real benefit that I have found is DirectX10. Otherwise it is a pig on resources and an overall nuisance. Itunes or something just owned my Vista drive, so I may have to reinstall it. When I do I plan on removing everything that I don't need and just installing my PC games. Ubuntu is now going to be my primary operating system for everyday things. Vista will be my gaming platform of course.



Just give Microsoft a call and make sure you don't mention anything about virtualization unless you really need to. Make those nuts in Redmond work :lolflag:


Anyone else remember the good old days of Windows 98 Second Edition? DOS games ran well and the system ran fast. No DRM and no invasive MS stuff to interfere with programs and computing. I guess Linux is bringing the peace of mind back to me...

---

### Post by rune0077 on 2008-01-18
> **SidewinderPro2 said:**
> It doesn't even compare to the stability and reliability of XP in any way, shape, or form. Its extremely buggy and prone to crashing and blue screening. The only real benefit that I have found is DirectX10. Otherwise it is a pig on resources and an overall nuisance. Itunes or something just owned my Vista drive, so I may have to reinstall it. When I do I plan on removing everything that I don't need and just installing my PC games. Ubuntu is now going to be my primary operating system for everyday things. Vista will be my gaming platform of course.


When I ran it on a seperate partition, it actually ran surprising well. There were some hardware issues in the beginning, but those where quickly fixed. It remained 100% stable and I have yet to see a single blue screen. And it looked great. That being said, I practically never used for anything other than accessing my netbank (which has to be done through a Windows or Mac machines, no Linux support), and I found the dual-booting very annoying.

But problem has solved it self. When I tried to activate it again, Vista popped up a phone number I could call to activate the product over the phone. This included typing in a lot of numbers, then receiving a code that also consisted of a lot of numbers and entering them in those ever popular windows-boxes. The nice machine-voice at the other end of the line refused to give me the code unless I "pressed 1" to confirm that I had accidentally deleted my OS and didn't actually have it installed on another system already. I did, got the code, typed it in, and Vista is now activated in VirtualBox. Good to see MS isn't entirely unreasonable.

---

### Post by David Ostrom on 2008-01-18
Make those nuts in Redmond work.:lolflag:
Thanks I liked that

---

### Post by jetole on 2011-12-05
I know this is listed as solved but technically this is a license violation. I'm not saying I agree with it but re-installing the OS in a virtual machine is considered a different instance then the machine you initially installed it on.

You're solutions are to either mimic the bios tables which are being checked (usually parts of the DMI table as well as the SLIC table in ACPI if it exists) or to get Microsoft to give you a new code. Both options are allowing you to cheat your way around the EULA you agreed to and no I'm not supporting MS or the EULA but just explaining it from how their lawyers would view it.

I don't use VirtualBox but from what I have heard, it has a option to mimic the hosts DMI, RSDT and SLIC table just so you can run a OEM edition of Windows in the VM. They mean the OEM shipped, SLP (System Prelocked Edition) editions and not the OEM type that you bought. An example would be, if you bought a Dell, the SLP edition that came with the system would run on any Dell it was installed on based on the Motherboard data alone where the none SLP editions (OEM you bought or retail editions) rely on more details about the host computers hardware i.e. SLIC, CPU ID, NIC MAC addresses, HDD identifiers, etc and if more then a couple of the details of all the hardware they check has changed then it considers it a different computer that you are trying to illegally copy it to and then it asks you to register it again.

UPDATE: Actually, now that I think about it, mimicking the BIOS tables wouldn't count since this is a non SLP OEM edition and it checks more then just the BIOS tables so you really do just have to get MS to give you a new code to activate it.

---

### Post by CharlesA on 2011-12-06
It would be a breach of the license agreement and this thread is over 3 years old.

---

