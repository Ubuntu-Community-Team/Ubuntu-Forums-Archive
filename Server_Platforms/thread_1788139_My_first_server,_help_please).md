---
title: "My first server, help please:)"
date: 2011-06-22
forum: Server Platforms
---

### Post by devilsrogue on 2011-06-22
So, I just got a dl380 g4 server with a pretty nice config if you ask me for the price.
it has 4 gb of ram 
and dual xeon 3.4ghz with ht, I am gonna upgrade it to the dual core modules so it has 2 cores each cpu and 2 threads each cpu making it a quad/8 threader system
I got it for 80 bucks on ebay without no hdds

Heres my question and I didnt know where else to ask:)

Since my model does not have sata, cant I put in a addon card for it? like one of those cheap pcie ones and put it in the non hot swap port? I dont have much $ so thats why. Those would only be used for storage as im buying 2 72 gb ones for the server os.
My server does have pcie, im just not sure if i can use the same pcie 1x cards in any of the slots that would normally go in a desktop. I really would like to because I can have a couple 2 tb drives REALLY cheap,If not Ill just go usb.

---

### Post by devilsrogue on 2011-06-22
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815287003](http://www.newegg.com/Product/Product.aspx?Item=N82E16815287003)

Something like that, It would seem that I would since the server supports pcie and its backwards compatable...hmmm

---

### Post by devilsrogue on 2011-06-22
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136765](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136765)

maybe the one with that will work

---

### Post by crispy_420 on 2011-06-22
If they don't need to be bootable I don't see why not. You are using them for storage anyway right? Just ensure they are a compatible chipset for Linux.

---

### Post by devilsrogue on 2011-06-22
Yea i just wasnt sure if theyd fry or something, i thought maybe the pcie in servers were different, i know that two of the slots have a lower clock or something

---

### Post by a2j on 2011-06-22
server has hot swap sas drive bays? or scsi? do you have room for your sata drives in there?

---

### Post by devilsrogue on 2011-06-22
Oh i can figure out where to mount the drives:) Ill most likely just get a few more of the caddies and modify them for sata

---

### Post by crispy_420 on 2011-06-22
PCI-e (express) or PCI-x (extended)? Then there is a difference.

---

### Post by Lloyd_mcse on 2011-06-22
> **crispy_420 said:**
> PCI-e (express) or PCI-x (extended)? Then there is a difference.

Yes there is a difference. PCI-X is rated up to 64bit 133mhz slots and is compatable with old style PCI card and PCI-E is a totally new standard not compatable with old PCI cards.
Please correct me if I'm wrong :)

---

### Post by devilsrogue on 2011-06-22
Duh, slaps self on head...i should of noticed that it said pci-x not pcie, well this should work then? [http://cgi.ebay.com/3Ware-9500S-4LP-AMCC-4-Port-PCI-X-SATA-RAID-CONTROLLER-/360349028090?pt=COMP_EN_Networking_Components&hash=item53e679cefa](http://cgi.ebay.com/3Ware-9500S-4LP-AMCC-4-Port-PCI-X-SATA-RAID-CONTROLLER-/360349028090?pt=COMP_EN_Networking_Components&hash=item53e679cefa)

---

### Post by crispy_420 on 2011-06-22
PDF says supported:

[http://www.3ware.com/products/pdf/9000_DS_012605.pdf](http://www.3ware.com/products/pdf/9000_DS_012605.pdf)

---

### Post by devilsrogue on 2011-06-22
Sweet:) thats what im going with:)  now ill just plop 2 cheap 1tb drives in for my file serving needs

when the server arrives tommorow im gonna be giving it a good cleaning and performing a ram test and all that good stuff and then its gonna get ubuntu server 11.04 64 bit:)

Its gonna serve
my website and my guild site for the upcoming star wars mmo
(this wont be much work for it at all:)
My email server(because public email to me sucks)
a teamspeak voice server
irc chat server
and of course the 2 1tb hdds, they are going to be more for backing up my main desktop system and backing up odds and ends and whatever i need on the server because media is gonna be hosted elsewhere:)
I might throw a team fortress 2 server on there as well, just because I can

---

### Post by crispy_420 on 2011-06-22
Why 11.04 and not the LTS version (10.04), it will be supported longer.

---

### Post by devilsrogue on 2011-06-22
I dont really mind upgrading stuff when a new version comes out, I like to have the latest of whatever I can:)

---

### Post by devilsrogue on 2011-06-22
Its practically painless on the server I got because it has Ilo, which lets me control the server from anywhere I want without software, its hardware based..I can totally install the os and all that without touching the server

---

### Post by tgalati4 on 2011-06-22
You will find that the major web frameworks are packaged for Ubuntu LTS releases.  If you are using it as a homeserver, then it doesn't really matter.

---

### Post by devilsrogue on 2011-06-22
Oh I know we have everything I need in there:) Im currently running it on my tablet pc as my testbed:) I cant wait to have that machine back tommorow, and have a proper server in place

---

