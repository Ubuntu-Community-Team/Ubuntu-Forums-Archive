---
title: "Anyone want to look at my server build (not your typical box)"
date: 2022-11-16
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2022-11-16
Here is the album link, descriptions are in the album

[https://imgur.com/a/bJsP80E](https://imgur.com/a/bJsP80E) (sorry for not attaching them, but that would lower the resoluition)

i have a mATX board (3 PCIe slots + 1 M.2 slot) in there and managed to use all 7 PCI slots on a mid tower case

Most of this hardware is used or repurposed

[LIST]
[*]SSDs: used
[*]HDDs: used
[*]drive case: used
[*]fans: onhand/reused
[*]case: onhand/reused
[*]card reader: onhand/reused
[*]network card: onhand/reused
[*]PSU: new
[*]cooler: onhand/reused
[*]MB: openbox/repurposed
[*]ram: used
[*]sound card: used (asus) audigy (repurposed)
[*]PICe -> PCI card: new
[*]modem: new (ISP provided)
[*]switch: repurposed
[*]M.2 SSD adapters: new
[*]CPU: used (overpriced cause it was OEM only sku)
[*]boost converter/ amplifier: new
[*]M.2 -> sata card: refurbished (seller probably just got them in a pallet and was sold it that way at ~1/2 price)
[/LIST]

---

### Post by lammert-nijhof on 2022-11-17
Nice system and photos! What about my $0 backup-server based mainly on the remains of a 2003 HP d530 SFF;
- Motherboard of the HP d530.
- Pentium 4 HT (1C2T; 3.0GHz);
- 1GB DDR (400MHz);
- 2 IDE HDDs 3.5" 250+320GB;
- 2 SATA-1 HDDs 2.5" 320+320GB;
- 500W xTech power supply repaired using a fan, SATA and IDE power cables from another defect power supply;
- Compaq Evo Tower with a Windows 98SE activation sticker;

Running 32-bits FreeBSD on OpenZFS 2.1.4 with 2 striped datapools (Raid-0); one for the IDE HDDs and one for the SATA HDDs. Two cables are connected; Ethernet and Power. The Ethernet transfers and the storage are lz4 compressed. The weekly incremental backup takes between 45 and 90 minutes dependent on the size of the changes in ~70 Virtual Machines (~900GB), of which half still receive updates.. 
The system runs at 200 Mbps of the 1Gbps due to a ~95% load on one CPU thread.

---

### Post by pqwoerituytrueiwoq on 2022-11-18
70VMs on 1GB ram with a single core cpu!? :shock:

---

### Post by DuckHook on 2022-11-18
@ pqwoerituytrueiwoq

I think it's a lovely build.

*sigh* I used to love doing stuff like this but haven't touched it for a couple of years now. Maybe it's time to revisit my old hobby.

One curiosity question though&#8230;

Have you measured how much juice it gulps? More and more, I'm finding that old components are not worth the long term electrical bill.

---

### Post by pqwoerituytrueiwoq on 2022-11-18
with 1 500GB WD Blue HDD it was ~ 60 watts at the breaker, the PCI card i measured pulls 30 watts... (2A on 5v and 2A on 12v) i really question if i am measuring that cards draw right... it just does not seem possible even though the wall power validates it

it is a AM4 system with a 2200GE (35Watt CPU with the iGPU only there so the system to post) the cpu uses like 5-7 watts idle i think it was like 25 watts running prime95

---

### Post by DuckHook on 2022-11-18
That's not bad at all. 60 watts is okay.

My refurbished tower will draw 100 watts for the GPU alone. CPU =  another 60 - 80 (depending on load) plus everything else and it can top out at +400 watts. If run 24/7, that's a nasty hit on the wallet, not to mention the environment.

OTOH, I replaced the OS on a WD MyBook Live a few years ago with OpenWRT, installed a 10TB HDD and run it constantly. 12 watts. Does everything I need it to and eats like a bird. After 2 years, it hasn't given me a day of trouble. Two of them mirroring each other gives me redundancy for a draw of 24 watts.

Due to such advantages, I found myself going in that direction rather than salvaging old towers, but I have to admit that I miss those old tinkering ways.

---

### Post by pqwoerituytrueiwoq on 2022-11-19
old system can be power sinks, i have been using a raspberry pi for a server for a long time now for that reason, this is not really a old system, the case is definitionally old, but the cpu is only from 2018
i was very picky when looking for the psu, had to down to a couple of options and i ram the number and while i did not get the most efficient unit it would need to last around 20 years (maybe more?) to match the sale price with the power savings

my hdds are 3-5 watts each, probably close to 70 watts now, i could pull my sound card and check the power draw at the wall, if that really uses 50% of the power usage i should look for a modern sound card, but that old card is neat

---

### Post by DuckHook on 2022-11-19
I would encourage you to assemble what feels good. It shouldn't always be about minimal this and efficiency that. Sometimes, it's about what is the most fun!

;)

---

### Post by pqwoerituytrueiwoq on 2022-11-19
i did do several things to try to keep power usage down when i built this beast,
the PSU in this powers my cable modem, a network switch, pair of creative T12s, the amp/boot converter. by using this instead of wall worts i have less AC-DC power loss and the load psuh the PSU higher up it's efficiency curve, if that card really pulls 30 watts it is really undermining what i have done, but it looks cool, gets the job done and fulls the empty slot in the front of my case as well as 3 PCI slots (adapter, card, gameport) but not like it burning 30 watts does any harm this time of year... ifit really pulls taht kind of power i want to know how it does and that is using that power, cause nothing on there should be able cool that 

i am planning to plug a pico into one of my usb ports for reading DHT22 sensors, reading some buttons/switches, LED, and a photocell

going to have 4 PICOs setup in the house and 2 will be sharing a power adapter that also powers a tiny audio amp, on that note that adapter is next to my 16 port switch. that switch has a internal 5v adapter i could tap and use that to power my stuff i guess that would make it more efficient, but it is such a tiny amount of power... once i get this setup i plan to sell a couple of my raspberry pis as they are in high demand

still need to make the boards to put my picos on, already got the wiring done (aside from the garage, should have that done next week)

---

### Post by DuckHook on 2022-11-19
You've taught me something: replacing wall warts with combo PSUs (when this can be done safely and effectively) is a viable strategy. I will remember that.

Nor did I know that RPis are in such demand. Your alert prompted me to see what they are selling for these days and all I can say is: ***sticker shock***. :shock:

Since when I had bought them, they've now doubled in price!

---

### Post by pqwoerituytrueiwoq on 2022-11-19
you may be wondering why not just buy a lower wattage psu so you can be higher up the efficiency curve... gl with that unless you are Dell
luckily 80+ now test 10% loads on all units and [publishes them]("https://www.clearesult.com/80plus/manufacturers/115V-Internal") (the cert itself ignores 10% loads unless titanium grade) and a low power system like this a never gonna eat much more than 10-20% of any reputable sub 600W psu you can buy

finding anything standard sub 450W is near impossible
the evga unit i got was 2ed best (ignoring the asus unit with a typo-ed 10% data, see the pdf on it)

was looking for low wattage, high efficiency, and long warranty (7-12 years) then comparing prices and power usage delta and factoring that into the unit cost

ATX PSUs has 3.3, 5 and 12v, and you can use boost or step down converters for other voltages, you can also get 8.7v, 7,  and 1.7v buy using 12, 5, and 3.3v and using one of them instead of ground (eg: 12v and 5v instead of ground)
that said you need to keep the current draw low when doing this so you do not raise a lower voltage out of spec ([interesting stuff in this thread on the topic]("https://www.badcaps.net/forum/showthread.php?t=85799"))

---

### Post by DuckHook on 2022-11-19
Now you've got me spooked. While I do play around with components, I lay off the voltage juggling act because I trust neither my knowledge nor my judgment. I had a minor catastrophe a while ago burning out all my drives from hooking the wrong cables to a new PSU, so I'm really shy about monkeying with the electrical side of things. But a 5 V lead from a PSU into an external appliance would not be beyond me, so that's more what I had in mind.

At any rate, thanks for the suggestions. It never occurred to me to lead from the PSU instead of a wall wart, so yours is a useful and informative tactic.

---

### Post by pqwoerituytrueiwoq on 2022-11-19
that last part is no different than than, voltage comes from differences so if you take 12v as red and 3.3v as black you get 8.7v ( 12 - 3.3 = 8.7)
by also having access to a stop up/down converter you can get any voltage you want, eg 12v into a boot converter can give you 24v out or maybe you need 1v you could use a step down converter on 3.3v

i have a boost converter on my audio amp card thing linked in my album cause the amp works better at 20-24v, i may not need the large resistor not that i have a better PSU, but i think that may have helped with audio crackling, but that also may have been resolved with the better PSU

you need to be careful when using PSU cables from another PSU, always check the pin outs

[LIST]
[*]paperclip test: [https://www.silverstonetek.com/upload/downloads/QA/PSU/PSU-Paper%20Clip-EN.pdf](https://www.silverstonetek.com/upload/downloads/QA/PSU/PSU-Paper%20Clip-EN.pdf) 
[*]volt meter at the end of your cable and make sure you have the correct voltage on the correct pin 
[*]be careful with cables with capacitors in them and make sure you do not reverse the voltage on those pins, usually only in the 24pin cables 
[/LIST]

---

### Post by mIk3_08 on 2022-11-20
> **lammert-nijhof said:**
> Nice system and photos! What about my $0 backup-server based mainly on the remains of a 2003 HP d530 SFF;
- Motherboard of the HP d530.
- Pentium 4 HT (1C2T; 3.0GHz);
- 1GB DDR (400MHz);
- 2 IDE HDDs 3.5" 250+320GB;
- 2 SATA-1 HDDs 2.5" 320+320GB;
- 500W xTech power supply repaired using a fan, SATA and IDE power cables from another defect power supply;
- Compaq Evo Tower with a Windows 98SE activation sticker;

Running 32-bits FreeBSD on OpenZFS 2.1.4 with 2 striped datapools (Raid-0); one for the IDE HDDs and one for the SATA HDDs. Two cables are connected; Ethernet and Power. The Ethernet transfers and the storage are lz4 compressed. The weekly incremental backup takes between 45 and 90 minutes dependent on the size of the changes in ~70 Virtual Machines (~900GB), of which half still receive updates.. 
The system runs at 200 Mbps of the 1Gbps due to a ~95% load on one CPU thread. Wow! this is cool. I might try this someday If I have any vacant unused system hardware. Regards and cheers.

---

### Post by lammert-nijhof on 2022-11-21
It is a Backup Server and it backups ~70VMs :)

---

