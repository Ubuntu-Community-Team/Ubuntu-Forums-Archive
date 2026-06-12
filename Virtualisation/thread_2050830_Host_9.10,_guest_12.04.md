---
title: "Host 9.10, guest 12.04?"
date: 2012-08-31
forum: Virtualisation
---

### Post by 2122wolf on 2012-08-31
This is just a quick question about an idea that struck me not so long ago. I am running a laptop with an ATI X1200 graphics card - one of the series that AMD no longer supports for open source. As a result, I have gone from having a graphics card that does everything I want it to do, to something that can't even run the simple 'Bejeweled' type games I was running in windows.

Its actually making me consider giving up on Linux altogether until I can afford a machine with newer, supported hardware. Its sad that the only problem here is support.

Now my quetion is, how well would things go if I setup Ubuntu 9.10 with all of the support for my hardware and from there setup a virtual machine (or two) with later versions? I am not interested in rebooting everytime I need to perform a different task so I don't want to go the dual boot route. Its this or I return to windows - for now.

What do you think?

---

### Post by mbarland on 2012-09-01
It'll work, but obviously you won't get the security or software updates for your host os.

---

### Post by 2122wolf on 2012-09-01
Does that really matter if I am just using it for the basis of my virtual machine and nothing else? In other words I will keep it stripped down and do everything from the virtual machine.

I am not running an organisation or the fbi. All I want is a machine to run my old games and fulfill whatever my data editing needs are.

Thanks for the answer bro. I do believe that makes this a solution.

---

### Post by mbarland on 2012-09-02
It could potentially matter, but there are a lot of people on these forums happily running outdated and unsupported versions of Ubuntu. The concern is that your host is the lowest level contact to the outside world. So even though most of your day to day work will be effectively sandboxed in the virtual machine, the core os may have security holes. Everything run on any of the guest vms is routed through the host. Real world this will most liekly not become an issue, but it is something to consider. 

I'm in a similar boat, my ATI 4850 (only about 4 years old) recently landed on the unsupported list. I've been pricing a replacement out and will probably just be replacing the card once I need to update the os.

---

### Post by Dedoimedo on 2012-09-04
The only thing I can think of is performance optimization and maybe some kernel functionality in later releases that offer better and smoother guest experience, but it should work fine.
You might also be missing certain instruction sets in the cpu, but for most people this won't matter at all.
Dedoimedo

---

