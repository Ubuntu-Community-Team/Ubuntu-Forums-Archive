---
title: "Buildin New Server - Any Caveats"
date: 2012-07-10
forum: Server Platforms
---

### Post by Colin R on 2012-07-10
Hi All,

Have to order the bits to build a new server for a client.
500Gb Disk, 16Gb RAM, Intel i5 CPU
Motherboard is going to be an Asus 90-MIBF10-GOEAYOOZ.
Liquid Cooling

Just wondering if anyone has any comments (or recommendations)

What about an i7 instead of i5 and, is Liquid Cooling 'safe' enough for 24/7 operation?

TIA

---

### Post by thnewguy on 2012-07-10
I don't think there are any problems with what you have there. However, if you want to be extra careful, check out the hardware certified by Canonical to work with Ubuntu Server edition.
[http://www.ubuntu.com/certification/server/](http://www.ubuntu.com/certification/server/)

---

### Post by Cheesemill on 2012-07-11
If you are going to build a server then use server hardware, not desktop hardware.

Server motherboards and other hardware have been specifically designed to run 24x7 whereas desktop hardware hasn't.

Also I'd go nowhere near water cooling for a server. If you need more powerful hardware then either buy more powerful hardware or more than one server.

---

### Post by darkod on 2012-07-11
If I may suggest, and depending on your location, look into HP servers, some of the entry level models (tower or rack, depending what you want).

When I was planning my small, home storage server, I was reading a lot on components, planning which mini ITX board with embedded Atom to use, PSU, case, etc. And then I saw an offer for a HP Proliant Microserver which fitted into my plans perfectly, and costed maybe 50-70% of what hand picked components would have costed me one by one. Note that I wasn't selecting cheap garbage components.

For example in Spain they have the (tower) Proliant ML110 G7 with Xeon E3-1220 for 459&#8364; inc VAT. Of course, it has only 2GB memory and 250GB disk but you can build upon that.

I doubt I can come close to that price if I assemble it myself, and as Cheesemil said, you get server hardware for that price.

I always start thinking about building my own too, but sometimes it's worth shopping around.

---

### Post by Cheesemill on 2012-07-11
> **darkod said:**
> If I may suggest, and depending on your location, look into HP servers, some of the entry level models (tower or rack, depending what you want).

When I was planning my small, home storage server, I was reading a lot on components, planning which mini ITX board with embedded Atom to use, PSU, case, etc. And then I saw an offer for a HP Proliant Microserver which fitted into my plans perfectly, and costed maybe 50-70% of what hand picked components would have costed me one by one. Note that I wasn't selecting cheap garbage components.

For example in Spain they have the (tower) Proliant ML110 G7 with Xeon E3-1220 for 459€ inc VAT. Of course, it has only 2GB memory and 250GB disk but you can build upon that.

I doubt I can come close to that price if I assemble it myself, and as Cheesemil said, you get server hardware for that price.

I always start thinking about building my own too, but sometimes it's worth shopping around.
 A big +1 for HP servers, I've been using nothing else for years.

I can get that same Proliant ML110 G7 server in the UK for £385. Just add RAM and HD and your sorted.
I would *always* go for server hardware for a server, there's no two ways about it.

---

### Post by rubylaser on 2012-07-11
> **Cheesemill said:**
> A big +1 for HP servers, I've been using nothing else for years.

I can get that same Proliant ML110 G7 server in the UK for £385. Just add RAM and HD and your sorted.
I would *always* go for server hardware for a server, there's no two ways about it.

That looks like a nice, inexpensive server.  It's [$479 at Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859107006&nm_mc=OTC-FroogleNEW&cm_mmc=OTC-FroogleNEW-_-Server+-+Systems-_-Hewlett-Packard-_-59107006").

You could try tp build one with similar specs if you wanted to as well.  I would follow the recommendations above and build with server grade hardware (just an example and would include IPMI KVM).

[CPU] [Xeon E3-1230 v2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117286")
[MOBO] [SUPERMICRO MBD-X9SCM-F-O]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182253")
[RAM] [Kingston 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1333 ECC Unbuffered]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139262")
[CASE] [Antec 300]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811129042")
[PSU] [Antec BP550 Plus 550W Continuous Power ATX12V V2.2 80 PLUS Certified Modular]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371016")
[DISK] [Western Digital RE4 WD1003FBYX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136798")

That would be around $793 with 8GB of RAM and a 1TB WD Enterprise Hard Drive or $613 base price.  This shows the value in the HP server mentioned above.

---

### Post by Cheesemill on 2012-07-11
> **rubylaser said:**
> That looks like a nice, inexpensive server.  It's [$479 at Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859107006&nm_mc=OTC-FroogleNEW&cm_mmc=OTC-FroogleNEW-_-Server+-+Systems-_-Hewlett-Packard-_-59107006")..
That's about the same price then.
$479 = £308 but mine comes with a 250GB HD from [www.serversdirect.co.uk]("http://www.serversdirect.co.uk/Hewlett_Packard_HP_ML110G7_E3-1220_SATA_TV_UK_SVR_639260-035/version.asp").

+1 for the Antec 300 case, it's what I've got for my desktop.


Edit - Damn, just noticed that the £150 cash-back deal from HP has just run out. For £235 I'd have picked up as many as possible :)

---

### Post by CharlesA on 2012-07-11
If it's a for a client, go with server grade gear, not desktop grade gear.

If it was for a normal home server, you would be fine with desktop grade gear.

Also, huge +1 to HP servers (Dells get an honorable mention too).

---

### Post by Colin R on 2012-07-22
Sorry for the long delay but, finally managed to persuade the client to buy a server.

They bought a Fujitsu box and I have installed 12.04 on it.  No problems..

---

