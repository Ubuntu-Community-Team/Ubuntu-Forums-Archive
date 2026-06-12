---
title: "Anti Trust aganist HP"
date: 2008-09-16
forum: The Cafe
---

### Post by GOVATENT on 2008-09-16
Hello guys. Want to get a few views on my plan against HP. If you know, HP has a white list on their bios of what internal WLAN cards will work in the mini pci port inside their laptops. I learned this the hard way. I was trying to install my friends old Atheros to replace the HP provided broadcom card. I got a bios error that would not let me boot the machine till I removed the card. The white list is a small amount of cards that hp thinks are suitable for their model. They clam the FCC says it approved the card / antenna wires together. I say its BS because other machines (my Toshiba for example) work with any card I put in them. The bios checks the vendor ID and the model ID. I tried to add the Atheros card to the list with a hex editor. I did not know it would checksum at boot. That was the last I saw of the HP laptop. I believe that they are monopolizing this. They also refuse to give me the right phoenix crisis disk. So, do you think I have the ability to file an Anti Trust law suit. I am trying to find a lawyer to help me. What do you, the ubuntu community think? Please let me know. If you know of any lawyers that could help, please give me contact info. I live in South Florida.

---

### Post by tom66 on 2008-09-16
You didn't back it up before you flashed it? (also, can it not be reflashed?)

---

### Post by GOVATENT on 2008-09-16
yea i have a back up, but it still won't boot it and goes back to recovery mode. it dont matter anymore. I just bought a new laptop. I don't want anything to do with HP. I think i need a special bios file.

---

### Post by Sef on 2008-09-16
> So, do you think I have the ability to file an Anti Trust law suit. I am trying to find a lawyer to help me. What do you, the ubuntu community think?

That is not an anti-trust issue.  If they had 90% of the market then it would possibly be an anti-trust issue.  They have a right to determine what parts work with their computers.

---

### Post by Polygon on 2008-09-16
wait, im confused, why are you replacing the wireless card inside a laptop? arnt those built in?

or why did you buy a laptop WITHOUT a wireless card?

either way, HP has excellent linux support both with their printers and their computers....so....yeah

---

### Post by GOVATENT on 2008-09-16
I give up. I found some fine print that allows them to say it. I will contact the fcc cause I want to hear it form them tho. I think this scenario is like buying a desktop motherboard from asus and being told you could only use Nvidia based GPU. I don't know much about law, but i know this is wrong. I know, just boycott hp, which is what i will do.

---

### Post by Polygon on 2008-09-16
you still didn't answer my question on why your taking out / putting in a wireless card into a laptop, or why you even bought a laptop without a wireless card in the first place.

and again, like i said hp generally has very good linux support.

---

### Post by GOVATENT on 2008-09-16
oh, sorry, i wanted to swith out the broadcom from my brother hp and use my old toshibas atheros card in ubuntu. i think the fcc story is crap cause his broadcom worked just fine in the toshiba. i think its hp wanted to sell me parts i dont want or need.

---

### Post by Trail on 2008-09-17
Screenshot or it didn't happen?

Sorry, nothing personal but I cannot trust that easily any member with only 5 posts on such a matter.

---

### Post by mips on 2008-09-17
> **GOVATENT said:**
> I did not know it would checksum at boot. That was the last I saw of the HP laptop.

You should be able to fix it without to much stress.

Thing is HP laptop will ONLY work with HP branded cards.
You can try a genuine Intel 2200BG for example and it will not work, however a HP branded 2200BG will however work. Guesse which one costs way more? Correct, the HP one.


The practice is a bit questionable. I don't live in a FCC regulated country and the same happens over here. Why is it that only a few companies implement this practice and others dont assuming we are talikg about the FCC regulated USA?

---

### Post by beniwtv on 2008-09-17
Yeah, I agree with you GOVATENT. 

The only thing I hate from my HP laptop is that Broadcom WiFi card *sigh*. Don't get me started on Ndiswrapper + Nvidia propietary driver...

Luckily for me, since Hardy it works with the open source driver (yes it comes back after suspend :)). 

Cheers,

---

### Post by blueturtl on 2008-09-17
Oh yeah. We have one of these notorious HP notebooks in the house (nx6125). I know I won't be buying any computers from HP in the future.

They are of course free to do what ever they want with their products, but we are free not to buy those products. An afterthought maybe, since who would have thought they'd deliberately make their product less functional. Still something I know now to watch out for.

In our case the notebook will only accept one wireless card and that is the Broadcom model it shipped with. It was a big disappointment to find out that I had to use an external USB dongle if I wanted working wireless in Ubuntu. :(

---

### Post by SunnyRabbiera on 2008-09-17
Well truth be told Dell has the same deal with their laptops (getting dell certified parts and such) as does most other Laptop companies.
The only one I know doesnt do too much personal brand bundling is Toshiba, except the hard drive.
Both HP and Dell have similar schemes (though I would still buy Dell or HP products as both of them support linux)

---

### Post by worx101 on 2008-09-17
HP has excellent support for linux...


And urm.... I work for HP and they gave me the two laptops I currently use... So urm.. .yeh

---

### Post by GOVATENT on 2008-09-17
The two toshiba laptops i own are pretty customizable. I have a new chip set in the machine I bought yesterday from AMD. The only down side with toshiba is their ACPI management. But to my understanding there is a flag in the kernal that fixes it. I don't have any screenshots but I plan on using my friend's HP to do so. I am thinking it will just be easier to give up, boycott HP and live on. I don't have the money or time to bother with these rich evil people. As for my 5 posts, I never had much to say in the past, so sorry. I did not know it mattered how many posts one had to be considered a member of the community. Again, i started the thread just to get some views on my problem. And I thank you all for responding. On a side note, i was able to find were they state that their laptops only accept HP branded cards because of an FCC regulation. It's in page 129 of 165 in the Hardware Guide service manual. Even if i tried to sue, I am sure they would say its stated. Even though who the hells reads the service manual when buying a machine. I look at specs. I quote from the manual "WARNING: The FCC does not allow unauthorized Mini PCI devices to
be used in this notebook. Installing a PCI device can prevent your
notebook from operating properly and might result in a warning
message. To resume proper notebook operation, remove the
unauthorized device. Contact your HP Customer Care Center if a
warning message about your Mini PCI device displays in error." Which is what someone on the ubuntu irc chat said. I still don't think the FCC has anything to do with this because why is it only HP and a few IBM laptops that do this. Does the FCC just not like their laptops. I emailed the FCC and I am waiting to see what they say.

---

### Post by castrojo on 2008-09-17
My old Thinkpad X40 was like this, I had to buy an IBM-branded Intel card for decent wireless ... I got around the markup by finding one on Ebay for around US $20.

These days when I buy it I just make sure it comes with intel wireless/video so I don't have to deal with it. (This time around I bought an hp 2510p with all intel and it works great)

---

### Post by Canis familiaris on 2008-09-17
> **Polygon said:**
> you still didn't answer my question on why your taking out / putting in a wireless card into a laptop, or why you even bought a laptop without a wireless card in the first place.

and again, like i said hp generally has very good linux support.

(1) Supporting Linux does not make them an "honest" company.
(2) It is rude to "DEMAND" such as "Why did you put that thingy..",etc.

---

### Post by GOVATENT on 2008-09-17
They way I see it, they are forcing me to buy their upgrades. They eliminate wireless card competition. Its like buying a desktop motherboard with an AGP slot and being told you have to use only ATI agp cards. You would avoid such a board. But if there was no warning, you would buy it only later to find out the bios won't boot the system if there was an Nvidia card in it.

---

