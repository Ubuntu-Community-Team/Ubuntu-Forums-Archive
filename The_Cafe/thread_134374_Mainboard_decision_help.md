---
title: "Mainboard decision help"
date: 2006-02-21
forum: The Cafe
---

### Post by ember on 2006-02-21
So as I wrote an hour ago, my barebone quit working today, so I have need for a new mainboard. What I need is:

- socket 754
- AGP
- usb 2.0
- firewire
- onboard network chip

I figured out that these demands are met by:

[MSI K8N Neo Platinum Edition 54G]("http://www.alternate.de/html/shop/productDetails.html?artno=GIEM06&")
and
[MSI K8T Neo-FIS2R (Sound, Gigabit-LAN, FW, IDE/SATA-RAID)]("http://www.alternate.de/html/shop/productDetails.html?artno=GIEM01&")

Does anyone have experience with running these products with Ubuntu. I will be running Breezy Badger (32 bit).

Best regards,
ember

---

### Post by mstlyevil on 2006-02-21
[QUOTE=ember]So as I wrote an hour ago, my barebone quit working today, so I have need for a new mainboard. What I need is:

- socket 754
- AGP
- usb 2.0
- firewire
- onboard network chip

I figured out that these demands are met by:

[MSI K8N Neo Platinum Edition 54G]("http://www.alternate.de/html/shop/productDetails.html?artno=GIEM06&")
and
[MSI K8T Neo-FIS2R (Sound, Gigabit-LAN, FW, IDE/SATA-RAID)]("http://www.alternate.de/html/shop/productDetails.html?artno=GIEM01&")

Does anyone have experience with running these products with Ubuntu. I will be running Breezy Badger (32 bit).

Best regards,
ember[/QUOTE]

If I can make a suggestion, I would go with Asus before MSI. Even a Gigabyte board would be better. You should consider a Nvidia NForce3 chipset because you want AGP and also because Nvidia chipsets are very compatible with Linux plus you could pick up those boards for a very competitive price because they are so common. Just my 2 cents.

---

### Post by RaptorRaider on 2006-02-21
I'm running an MSI K8N Neo Platinum (without the 54G, they added that later) and it's fine really.

---

### Post by ember on 2006-02-21
[QUOTE=mstlyevil]If I can make a suggestion, I would go with Asus before MSI. Even a Gigabyte board would be better. You should consider a Nvidia NForce3 chipset because you want AGP and also because Nvidia chipsets are very compatible with Linux plus you could pick up those boards for a very competitive price because they are so common. Just my 2 cents.[/QUOTE]

I saw no ASUS board with AGP and Firewire. Can you point out one? I'd be happy to consider it.

@Raptor:
Thanks.

---

### Post by mstlyevil on 2006-02-21
[QUOTE=ember]I saw no ASUS board with AGP and Firewire. Can you point out one? I'd be happy to consider it.

@Raptor:
Thanks.[/QUOTE]

I didn't find a ASUS board with firewire but I did find a DFI board with it and 2 SATA interface slots. DFI makes some of the highest quality boards for the market and this one is a good price. If you still use a PATA hard drive this board will support that also but will allow you to upgrade to SATA later.

[DFI Board on Newegg]("http://www.newegg.com/Product/Product.asp?Item=N82E16813136154")

---

### Post by RaptorRaider on 2006-02-21
Pretty much all socket 754 chipsets support both SATA and PATA. I can find lots with Firewire anyway.

Right now, you are linking to a VIA chipset by the way; I'd still advise you to go with the MSI K8N or any other nForce 3-based motherboard since they seem to run perfectly out of the box.

---

### Post by mstlyevil on 2006-02-21
[QUOTE=RaptorRaider]Pretty much all socket 754 chipsets support both SATA and PATA. I can find tons with Firewire anyway.

Right now, you are linking to a VIA chipset by the way; I'd still advise you to go with the MSI since it runs perfectly out of the box.[/QUOTE]

I found some that did not have SATA. And I told Neweggs search to look for Nforce 3. I blame their Windows servers. :-D

Edit: I found this one with a NForce 3 chipset

[Newegg.com DFI NForce3]("http://www.newegg.com/Product/Product.asp?Item=N82E16813136147")

I know a lot of people that have had trouble with MSI including myself. I personaly do not recommend them.

---

### Post by RaptorRaider on 2006-02-21
I doubt he'll be very interested in Newegg anyway - he seems to live in Germany.

A quick and short list of nForce 3 motherboard with Firewire I found in 10 seconds (still selling in the Netherlands so they should be in Germany too):
> Asus K8N-E Deluxe
DFI Lanparty UT nF3 250Gb
GigaByte GA-K8NNXP
MSI K8N Neo Platinum
Shuttle AN51R

---

### Post by mstlyevil on 2006-02-21
[QUOTE=RaptorRaider]I doubt he'll be very interested in Newegg anyway - he seems to live in Germany.

A quick and short list of nForce 3 motherboard with Firewire I found in 10 seconds (still selling in the Netherlands so they should be in Germany too):[/QUOTE]

I Probally should ask where they live first. :-k

---

### Post by ember on 2006-02-21
Right, I do live in Germany, in Karlsruhe namely. I will have to look for a serious store selling the recommendations made by raptor. At Alternate and our local stores they only sell the MSI board.

---

### Post by ember on 2006-02-21
O.k. It looks like I will go for the MSI or the Asus board, depending on which is available locally. I'd like to be able to kick someone if it's broken ;)

Thanks for your help.

---

### Post by RaptorRaider on 2006-02-22
Oh crap, I forgot...

The latest BIOSes for my motherboard (the MSI K8N Neo Platinum), absolutely suck.
Seriously, I have no idea what those BIOS-engineers were thinking.

How many and what kind of RAM modules will you be running?

---

### Post by ember on 2006-02-22
That was something I read about, which Bios version are you using? I heard that 1.7 is relativly stable while 1.9 (and a 2.1 I did not find on the MSI page) were so buggy that they even prevented starting.

I have two DDR-333 Kingston Value RAM modules with 512 MB each, so no dual channel, just standard timing.

---

### Post by RaptorRaider on 2006-02-22
I'm not very sure about this, but thought that 1.0-1.6 were fine while 1.7-1.9 were terrible.
As a matter of fact, I remember posting a thread about it [here]("http://gathering.tweakers.net/forum/list_messages/1081897/") (Dutch). I changed to 1.9, everything crashed and lots of BSOD's.

I think the problem is that ever since 1.7 those stupi, errr, fantastic engineers removed the "Command Rate" option and defaulted it to 1T.
When using more than 1 memory module this will often lead to BSOD's a few seconds after booting.

---

### Post by bjweeks on 2006-02-22
Asus for the win!

---

### Post by ember on 2006-02-22
[QUOTE=RaptorRaider]I'm not very sure about this, but thought that 1.0-1.6 were fine while 1.7-1.9 were terrible.
As a matter of fact, I remember posting a thread about it [here]("http://gathering.tweakers.net/forum/list_messages/1081897/") (Dutch). I changed to 1.9, everything crashed and lots of BSOD's.

I think the problem is that ever since 1.7 those stupi, errr, fantastic engineers removed the "Command Rate" option and defaulted it to 1T.
When using more than 1 memory module this will often lead to BSOD's a few seconds after booting.[/QUOTE]

Hmm ... my dutch is very bad ;) ... anyway that sounds quite unpleasant. Have you solved these issues recently?

---

### Post by RaptorRaider on 2006-02-22
Flashed back to v1.4. :neutral: 

Are you sure you can't find any of the motherboards I listed earlier in good German "pricewatches"?
Unless you're not comfortable with shipping my guess is that it wouldn't be that hard to get 4 out of 5 of the motherboards I listed.

---

### Post by ember on 2006-02-22
Ah o.k. :-s

I found the Asus mainboard in on some stores, my "problem" is that I am highly cynical about online stores I do not know that good, same applies to ebay where I made some bad experience concerning hardware, but I guess I have to swallow the bitter pill and order the mainboard seperated from the rest. I saw Amazon has the Asus board. 

The others are out, because:
1) I will not buy something from Shuttle again
2) The DFI board has only a Nforce 150 chipset
3) The Gigabyte board has the worst availability of all

So I guess, I'll go for the Asus board. Again, many thanks for your help.

---

