---
title: "Compatible server hardware."
date: 2009-10-04
forum: Server Platforms
---

### Post by ayenack on 2009-10-04
Hello all.

I'm setting up a server for a friend. He will be buying all the parts from China when he visits there within the next couple of weeks.

What I need is a compatibility list of components that work under Ubuntu Server 8.04. I'll give you a run down of what is needed and hopefully you'll be able to suggest decent parts that you've got knowledge of or used yourselves. I've tried to talk him into buying a pre-built system but he wants to build it himself for some reason.

Going to be running.
Quad Core Intel Xeon X5470, 3.33GHz, 2x6MB cache, 1333MHz FSB
24GB Memory, DDR2, 667MHz 6x4GB Dual Ranked DIMMs


Here's what I need advice on.

1, **Motherboard**. Must have good SATA/SAS raid controller and gigabit network controller with min 2 ports and bog standard graphics card and all other usual ports. I was thinking Tyan Tempest i5400PL (S5393) Intel 5100 Chipset.
2, **Chassis**. With Hotplug HD Bays, power supply.
3, **Hard Drives**. SATA/SAS Hard Drive. I was thinking along the lines of Near-Line SAS, 3.5-inch, 7.2K RPM HD.

Any advice on the above set-up or other good working components with Ubuntu Server appreciated.

Thanks for any help.

---

### Post by Lars Noodén on 2009-10-04
Since he is heading to China maybe he can get you the latest processors and leave the x86 behind in the 1990's

[http://www.linux.com/archive/feature/119890](http://www.linux.com/archive/feature/119890)
[https://launchpad.net/~ubuntu-mips](https://launchpad.net/~ubuntu-mips)

Just a thought.

---

### Post by ayenack on 2009-10-04
Would be an interesting choice but for know I think the Xeon is the way that I'll go. Thanks for the info though. I'll certainly keep an eye on the progress of both the chip and the ubuntu port.

---

### Post by houstonbofh on 2009-10-04
> **ayenack said:**
> 1, **Motherboard**. Must have good SATA/SAS raid controller and gigabit network controller with min 2 ports and bog standard graphics card and all other usual ports. I was thinking Tyan Tempest i5400PL (S5393) Intel 5100 Chipset.
Onboard raid is fake raid.  If you want hardware raid, you need a hardware raid card.  3ware has some nice ones with good support.

---

### Post by ayenack on 2009-10-04
Yeah. I was trying to keep the price down. Some on-board chips are OK though.

I'll have a look at some 3Ware boards. As it goes I've only ever heard good things about their raid cards. It would be a shame to have a bottle neck on the server so I think you're probably right about the raid board.

---

### Post by windependence on 2009-10-04
> **houstonbofh said:**
> Onboard raid is fake raid.  If you want hardware raid, you need a hardware raid card.  3ware has some nice ones with good support.

Not ALL onboard RAID is fake (software) RAID. The Tyan boards as a rule have good hardware RAID controllers. I have several in production here.

-Tim

---

### Post by ayenack on 2009-10-04
windependence do you run Ubuntu Server or Linux on your systems? If so can you give me a run down of the hardware you're using and any compatibility problems you've had?

I know the Tyan Tempest i5400PL (S5393) is Red Hat certified so there shouldn't be a problem under Ubuntu Server hopefully.

---

