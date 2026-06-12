---
title: "This sounds kinda unpleasant if it appears in the wild"
date: 2012-08-03
forum: Security
---

### Post by kurt18947 on 2012-08-03
[SIZE=3]http://www.pcworld.com/article/260015/researcher_creates_proofofconcept_malware_that_infects_bios_network_cards.html[/SIZE]


Researcher Creates Proof-of-concept Malware That Infects BIOS, Network Cards

                                                         By [Lucian Constantin]("http://www.pcworld.com/author/Lucian-Constantin"), IDG-News-Service:Romania-Bureau                             Jul 29, 2012 4:00 pm         
                                                                                                                        Security researcher Jonathan Brossard created a proof-of-concept  hardware backdoor called Rakshasa that replaces a computer's BIOS (Basic  Input Output System) and can compromise the operating system at boot  time without leaving traces on the hard drive.

More at the above link.

---

### Post by Hungry Man on 2012-08-04
It is very very unlikely that this will appear in the wild. This has actually been discussed on this forum before a few times. I'll break it down.

1) Infection is BIOS model specific, generic infection won't work most of the time.

2) Infection can even be BIOS version specific.

3) Infection needs Admin rights.

It's an unreliable way to attack a system and if you've got root there are easier ways to stay hidden.

---

### Post by kurt18947 on 2012-08-04
Thanks.  I actually had a thought (scary thought, that)after I read this.  I'm guessing few 'normal users' ever update BIOSs.  If they're having trouble they take the machine to someone.  Would it be worthwhile for manufacturers to include a jumper or DIP switch that is required to be moved in order to enable/disable writing to BIOS?  Or is the risk of such an attack so low that it wouldn't be worth the manufacturer's effort?

---

### Post by Hungry Man on 2012-08-04
It would interfere with legitimate BIOS updates so users would get pissy about it.

Some manufacturers include dual BIOS and if one were to get infected you could simply boot to the other.

---

