---
title: "Ubuntu and SSD"
date: 2013-09-19
forum: The Cafe
---

### Post by Quarkrad on 2013-09-19
It seems to me that the main benfit of SSD drives is boot time - my understanding (I could be wrong here) is that once booted the PC runs in RAM anyway.  I can see in Windows world this could be huge attraction but as Ubuntu boots within 60 secs is there any great advantage in going SSD?   I guess there could be times when an app need to write the HD and I'm guessing RAM to a SSD is faster than RAM to HD but if you have 2MB or 4MB of RAM is this a big issue for 90% of users?  I can put up with booting within 60secs so what is the point of going SSD in Ubuntu world?

---

### Post by sudodus on 2013-09-19
Live sessions run in RAM, but normal installed systems do not. They use the root partition for a lot of read/write operations.

You can make it use RAM, for example with a boot option or acoording to this thread[URL="http://ubuntuforums.org/showthread.php?t=1594694"]

Making Ubuntu Fast using RAM (updated and simplified)[/URL]

---

### Post by Nytram on 2013-09-19
The first time you start an app it will be read from the HD so an SSD would speed this up too.

---

### Post by eriktheblu on 2013-09-19
I use mine for screencasting and video editing.

---

### Post by King Dude on 2013-09-19
Running off of an SSD makes your system run faster (typically a few seconds faster load times, depending on the program). But make sure your SSD runs from a PCI Express 2.x port to eliminate SATA bottleneck. Also, best format with Btrfs than Ext4, as Btrfs is a little more optimized for SSDs.

---

### Post by ventrical on 2013-09-19
> **King Dude said:**
> Running off of an SSD makes your system run faster (typically a few seconds faster load times, depending on the program). But make sure your SSD runs from a PCI Express 2.x port to eliminate SATA bottleneck. Also, best format with Btrfs than Ext4, as Btrfs is a little more optimized for SSDs.

On my new MSi-B75MA-P45 mobo I get 6Gb/s  transfer with my OCZ-AgilityY3. 3 seconds to boot up. Less than 1 second to load Libre Office (@ first jump).. etc... and I am running the development branch- saucy. The drive and the mo-board are SATA 3 compatible .

   I am experimenting with O'clocking and am going to try that drive on a 1.5Gb/s SATA connect.

---

### Post by ventrical on 2013-09-20
12 second boot time with SATA 3 on a 1.5Gb/s SATA with a P4 overclocked to 3.939GHz.

```


ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.54 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.14 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +44.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +30.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +15.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, crit = +105.0°C)

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 3939 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ikt on 2013-09-20
> **Quarkrad said:**
> It seems to me that the main benfit of SSD drives is boot time

Main benefit is that everything starts much faster. Particularly things not in RAM like Games etc

---

### Post by Cyril380 on 2013-09-20
Best investment that one can do.
I add a 128 GB, use only a fraction of that (all data stay on the HDD). Everything is faster including system backup.
Beside I don't mess with the Windows 8 on the HDD. 
They say that the larger (256G, 512G) SSDs are faster but they cost a bundle.

---

### Post by Bandit on 2013-09-21
I got a Samsung 256GB SSD in my Gaming box and can load Win7 from a cold boot in about 10 seconds. Real benefit can be if your running low on RAM and the OS has to cache some information back to the SSD. But more RAM you have less this can be helpful. That said like everyones pointed out, loading other applications in shorter times is a real plus. Speaking of which I installed World of Warcraft on one of my regular drives the last time and I really need to move it over to the SSD.. Loading heavy game data quicker to get into an instance run really makes game play less stressful. I am on my Mac so I cant remember the exact speeds mine gets but its faster then the advertised speed by a small amount.

---

### Post by Werne on 2013-09-21
> **ventrical said:**
> ```
CPU FAN Speed:     4115 RPM
```
It spins faster than my car engine. :shock:

I honestly don't recommend overvolting a P4 unless you want to get rid of it, Northwood's performance degrades once overvolted even slightly and the CPU tends to die after some time, fried five P4s that way. But I must say, they are excellent overclockers, 3GHz Pentium 4 Northwood can reach 4.5GHz with good cooling and a decent mobo, dies after about two years at that frequency though.



As for SSDs, read/write, seek time and storage transfers are hell of a lot faster when compared to HDDs (700/550MB read speed on an SSD, compared to 180/120MB on a HDD), they also make no mechanical noise at all which is something I very much like. Aaand that's about all that's good about them, they are about equally reliable as HDDs. Also about 4-5x more expensive than HDDs when it comes to price-per-GB. It's all about weighing what suits you best - speed or storage size, how much money you have, etc.

I'd personally go for an SSD (I don't need more than 250GB storage, an SSD would fit me nicely) but since I can't afford one, HDDs are good too. ;)

---

### Post by vicsar on 2013-09-22
I develop software and edit videos, there is nothing like an SSD. Now I only use mechanical hard drive as storage devices. 

Also, I should mention that there are hybrid drives like the Seagate Momentus XT which can help in case one's budget is limited. That's how I got started on this transition.

---

### Post by Copper Bezel on 2013-09-22
Still haven't upgraded my Asus Vivobook to an SSD. I used to refuse to use anything that had a magnetic drive, but I don't notice a substantial performance lag on this machine. I really ought to put that on the Amazon wish list.

Realistically, this one will die some time next week, because it's a magnetic drive in a portable, and then I'll buy the SSD.

---

### Post by ventrical on 2013-09-23
> **vicsar said:**
> I develop software and edit videos, there is nothing like an SSD. Now I only use mechanical hard drive as storage devices. 

Also, I should mention that there are hybrid drives like the Seagate Momentus XT which can help in case one's budget is limited. That's how I got started on this transition.

The SSD I have is backward compatible and runs very fast on older SATA versions (1.5Gb/s etc...) There is virtually no down time. So I can test older machines without a lot of hassle. It doesn't seem to get in the way of overclocking either.

---

