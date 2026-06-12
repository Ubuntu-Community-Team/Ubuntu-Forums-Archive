---
title: "will enabling 32-bit support in 64-bit Ubuntu still be a viable option in the future?"
date: 2018-07-18
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-07-18
[https://ubuntuforums.org/showthread.php?t=2395967&p=13784666#post13784666](https://ubuntuforums.org/showthread.php?t=2395967&p=13784666#post13784666)

I just managed to install my 32-bit Canon printer drivers in 64-bit Lubuntu by enabling 32-bit support in 64-bit, the drivers are in 32-bit and I don't think Canon will offer a 64-bit version of the drivers anytime in the future.

Will this option be available in the future though? Because I heard 32-bit support is being discontinued or does that only apply to just 32-bit ISOs?

Because I don't want to throw away a perfectly good printer.

Thanks.

---

### Post by TheFu on 2018-07-18
You can always have a tiny virtual machine with an old version of Ubuntu server with IPP support. Then any client can connect to that and print.  Be certain to lock down that VM from any other network traffic if it isn't under support anymore.

Or spend $50 to get a well-supported printer.  I've been using the same $50 Samsung laser printer over a decade, hassle-free. By switching to laser, I'm off the $50/yr ink habit.   Sell or give away the old printer.

A family member went through the same issues.

---

### Post by ardouronerous on 2018-07-18
So multiarch will vanish then?

The VM solution doesn't really work for me since I tend to print from the browser and I've been in a situation where I needed to print from the browser, like airport gate passes and government forms.

I've looked into Laser printers and they are kinda pricey.

---

### Post by TheFu on 2018-07-18
> **ardouronerous said:**
> So multiarch will vanish then?

The VM solution doesn't really work for me since I tend to print from the browser and I've been in a situation where I needed to print from the browser, like airport gate passes and government forms.

I've looked into Laser printers and they are kinda pricey.


You've lost me. Sorry.  Printing from a browser over IPP to a network print server sorta just works.  Throw a PS or PDF at it from anywhere on the network and it gets printed.  There are other network protocols too, but IPP is very standard and easy for all platforms.  The VM would run a print server that connects to the printer.  Your desktop/browser would print to the print server inside the VM.  I can try to explain it differently if that isn't clear.  It works for USB printers using USB passthru to the VM. It should work with networked printers too, provided they connect to the infrastructure and not some proprietary wireless protocol.  I think wifi enabled printers are a terrible idea, but I don't trust any wireless protocols to be secure on their own.

Laser printers come in all prices.   $50 - $500,000.  [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)  I found a $53 printer similar to mine. Toner never dries out and lasts for years, unlike ink.  I know that my old ML1740 printer shows up in the GUI list in 16.04 and didn't require any extra work to be installed. When I first bought it, I had to get Samsung-specific drivers.  Setting up printers isn't something I do very often, perhaps once every 4 yrs, so I don't remember any huge issues using either proprietary or F/LOSS drivers, once those became available.

Perhaps you have some different requirements for the printer?   

As 32-bit OSes become unsupported, fewer and fewer 32-bit compiled programs will work without extreme effort by you.   You can run a 10.04 32-bit Ubuntu minimal inside a VM forever, if you like. But for security reasons, you'll want to lock it down from all unneeded network access. Clearly, no patches for it or anything running on it will ever happen.

---

### Post by ardouronerous on 2018-07-18
> **TheFu said:**
> You've lost me.

My question wasn't if 32-bit OSes sre going away, rather if enabling support of 32-bit architecture will still be available in 64-bit Ubuntu, which is what multiarch is.

Thanks for the VM suggestion, I've never printed from a network before, how do I know if my printer is capable of this? My printer has WinXP drivers and I have WinXP on Virtualbox with Internnet disabled, can you provide any tutorials on how I can enable IPP printing, thanks.

---

### Post by monkeybrain20122 on 2018-07-18
> **ardouronerous said:**
> My question wasn't if 32-bit OSes sre going away, rather if enabling support of 32-bit architecture will still be available in 64-bit Ubuntu, which is what multiarch is.


I don't see why not. Multiarch exists exactly for that purpose.

---

### Post by ardouronerous on 2018-07-18
So 32-bit architecture isn't going away, only 32-bit ISOs?
Okay, thanks for clearing that up. :)

---

### Post by TheFu on 2018-07-18
At some point, 32-bit code will die.  That is certain, just like 16-bit code is all gone.  About 15 yrs from now, would be my guess. Does that matter to anyone today?  As it becomes less and less used, it will not be provided by default.

I had a job porting 32-bit code to 64-bit in the early 1990s.  At the time, we were struggling with 16-bit code on a few platforms and 32-bit seems to make life really easy in comparison.  The drivers are always the first to lose support. OTOH, if you stay with F/LOSS drivers on well-supported printers, it  will keep working longer and easier.

I don't know if WinXP has a built-in network print server or if it will translate whatever input into the require output for the printer. I doubt it, but this isn't a Windows support forum and I've barely used Windows for over a decade. That's the power of a Unix print server.

IMHO.

---

### Post by Skaperen on 2018-07-18
keep a copy of a 32-bit system with the working drivers for as long as you keep that printer.if you still use it in 15 years, or otherwise have a 64-bit-only system, run that old 32-bit system in a VM.  i have heard that 32-bit will be gone in the kernel, soon, so you might want to be planning.

---

### Post by ardouronerous on 2018-07-18
Really? I though the Linux kernel will retain 32-bit?
What about the distros that runs on older hardware like Pentium II? Distros like Damn Small Linux, Tiny Core and Puppy Linux? What happens to these distros when Linux kernel pulls the plug on 32-bit?

---

### Post by TheFu on 2018-07-18
> **ardouronerous said:**
> Really? I though the Linux kernel will retain 32-bit?
What about the distros that runs on older hardware like Pentium II? Distros like Damn Small Linux, Tiny Core and Puppy Linux? What happens to these distros when Linux kernel pulls the plug on 32-bit?

I think it is just a main desktop Linuxen thinking of dropping 32-bit releases. I didn't think the main kernel would for a very long time.  Though, they did recently remove support for a number of  VIA 32-bit CPUs from the kernel.  One of my first media center systems had a VIA x86 inside. That won't work anymore.   More popular 32-bit CPUs are too popular (embedded devices) to be removed.   The main Linux Foundation sponsors will prevent that for the next decade, at least.

---

### Post by monkeybrain20122 on 2018-07-18
> **TheFu said:**
> I think it is just a main desktop Linuxen thinking of dropping 32-bit releases. I didn't think the main kernel would for a very long time.  Though, they did recently remove support for a number of  VIA 32-bit CPUs from the kernel.  One of my first media center systems had a VIA x86 inside. That won't work anymore.   More popular 32-bit CPUs are too popular (embedded devices) to be removed.   The main Linux Foundation sponsors will prevent that for the next decade, at least.


I think OP is worried about i386 libs needed for running bit software (such as his printer driver or wine) rather than 32 bit iso for 32 bit cpu (hardware), I could be wrong but I think those are separate issues.

---

### Post by TheFu on 2018-07-19
> **monkeybrain20122 said:**
> I think OP is worried about i386 libs needed for running bit software (such as his printer driver or wine) rather than 32 bit iso for 32 bit cpu (hardware), I could be wrong but I think those are separate issues.

Yes. When 32-bit distros go away, the compatibility libs will follow a few yrs later.  I haven't seen any published plans about this, but it will happen out of necessity to concentrate resources on well-used versions of code, not on fringe areas. We're already seeing this as different projects drop 32-bit packages.   [https://www.cyberciti.biz/open-source/heads-up-google-to-drop-support-for-all-chrome-on-32-bit-linux-distributions/](https://www.cyberciti.biz/open-source/heads-up-google-to-drop-support-for-all-chrome-on-32-bit-linux-distributions/) happened in 2016.

---

### Post by ardouronerous on 2018-07-20
> **monkeybrain20122 said:**
> I think OP is worried about i386 libs needed for running bit software (such as his printer driver or wine) rather than 32 bit iso for 32 bit cpu (hardware), I could be wrong but I think those are separate issues.

You are correct, I'm worried about 32-bit libraries being removed from future LTS versions.

> **TheFu said:**
> Yes. When 32-bit distros go away, the  compatibility libs will follow a few yrs later.  I haven't seen any  published plans about this, but it will happen out of necessity to  concentrate resources on well-used versions of code, not on fringe  areas. We're already seeing this as different projects drop 32-bit  packages.   [https://www.cyberciti.biz/open-source/heads-up-google-to-drop-support-for-all-chrome-on-32-bit-linux-distributions/](https://www.cyberciti.biz/open-source/heads-up-google-to-drop-support-for-all-chrome-on-32-bit-linux-distributions/) happened in 2016.

You said it may take 15 years for 32-bit libraries to go away, well, 15 years is a long time lol :)

Question, why doesn't anyone add the Canon's drivers into the Linux kernel, Canon's drivers offer better functionality to the CUPS driver available in the kernel.

Canon offers the source file for this printer here: [https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=44DF8C84AD71428685924667E398AA79&ctype=dr](https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=44DF8C84AD71428685924667E398AA79&ctype=dr)

---

### Post by cariboo on 2018-07-20
> **ardouronerous said:**
> You are correct, I'm worried about 32-bit libraries being removed from future LTS versions.



You said it may take 15 years for 32-bit libraries to go away, well, 15 years is a long time lol :)

Question, why doesn't anyone add the Canon's drivers into the Linux kernel, Canon's drivers offer better functionality to the CUPS driver available in the kernel.

Canon offers the source file for this printer here: [https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=44DF8C84AD71428685924667E398AA79&ctype=dr](https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=44DF8C84AD71428685924667E398AA79&ctype=dr)

I take it you didn't read the disclaimer on the site you linked to.

---

### Post by TheFu on 2018-07-20
> **ardouronerous said:**
> 
You said it may take 15 years for 32-bit libraries to go away, well, 15 years is a long time lol :)


That's a matter of perspective.  As you get older, 15 yrs doesn't seem so long.

> **ardouronerous said:**
> 
Question, why doesn't anyone add the Canon's drivers into the Linux kernel, Canon's drivers offer better functionality to the CUPS driver available in the kernel.
 

Software license.  The kernel is released under the GPLv2 license.  They can't just take code from anywhere and use it.

---

### Post by ardouronerous on 2018-07-20
> **TheFu said:**
> Software license.  The kernel is released under the GPLv2 license.  They can't just take code from anywhere and use it.

I found another Canon site with the source file: [http://support-sg.canon-asia.com/contents/SG/EN/0100272402.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272402.html)

According to the site, the source file is under GPLv2.

---

### Post by TheFu on 2018-07-21
> **ardouronerous said:**
> I found another Canon site with the source file: [http://support-sg.canon-asia.com/contents/SG/EN/0100272402.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272402.html)

According to the site, the source file is under GPLv2.

When I look at both sites, they don't say that.  They show the GPLv2 because "components" of the solution use GPL code, but the Canon-specific parts are under a proprietary license which prevent re-distribution.  That means the kernel guys can't use it.   

If you want it handled, complain to Canon.  Printer drivers are one of those things that makes good sense to turn over to F/LOSS teams.  It isn't like people didn't actually purchase the hardware, so Canon got their money.  And there is a never-ending hassle in maintained all software as each set of OS patches is released and all the different flavors might have slightly different underlying libraries.  For end-user programs flatpacks and snaps should make that better, but I don't think that works with drivers.

---

### Post by kurt18947 on 2018-07-21
> **TheFu said:**
> 
................................................
Or spend $50 to get a well-supported printer.  I've been using the same $50 Samsung laser printer over a decade, hassle-free. By switching to laser, I'm off the $50/yr ink habit.   Sell or give away the old printer.

A family member went through the same issues.

One big issue is color. If you need color, it's difficult to find a color laser for less than $175.00 or thereabout and most are more than that. Consumables favor lasers though so I'm not sure at what point color lasers become cheaper to own than inkjets. If you don't need color, monochrome lasers can be found very reasonably and they're less of a maintenance headache than inkjets. I make linux support a major consideration of any new hardware I buy. In fact, I've been known to write a letter to a senior person at a manufacturer and tell him or her in effect "I really liked your machine but your competitor offers linux support, you do not so your competitor's machine is sitting on my desk". I don't know if it makes a difference or not but it makes me feel better :).

---

### Post by dre2fresh on 2018-07-24
it depends are you using it for terminal (console) for ppa:repositories to install additional like wine through terminal if so then i'm pretty sure you can use the same command 
(sudo dpkg --add-architecture i386) try using that to see if it works for another time installing a application through ubuntu and are you using bionic beaver or artful aardvark

---

### Post by dre2fresh on 2018-07-24
[INDENT]yes dependswhat your using it for what are you using artful aardvark or bionic beaver are you trying to install more 32 applications through then use thus code the next time to see if it works 
(sudo dpkg --add-architecture i386):) [/INDENT]

---

