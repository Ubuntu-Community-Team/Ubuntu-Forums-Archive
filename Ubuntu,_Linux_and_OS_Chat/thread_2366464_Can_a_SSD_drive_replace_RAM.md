---
title: "Can a SSD drive replace RAM?"
date: 2017-07-18
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-07-18
I have an old 9-year-old Gateway Desktop and the RAM is DDR2, which is becoming rarer to find nowadays, and if the RAM fails for whatever reason, is it possible to replace the RAM with a SSD drive?

---

### Post by montag dp on 2017-07-18
You need to have at least some RAM for the computer to operate. In theory, you could use just enough RAM to boot and then configure a partition of your SSD as swap to handle the rest, but that would not be a good idea. You'd be much better off just stocking up on some extra DDR2 RAM while you can still find it, if you want to keep that computer running long-term.

---

### Post by Michael_McKenney on 2017-07-18
Putting a swap on SSD drive can kill it faster.   It is cheaper to add ram.   Use the SSD for your OS but install a SATA drive and move your paging and temp files to it.   Ubuntu is very happy with my 6GB of RAM and 12 GB swap partition.   I don't really hit the swap partition.    My Windows 7 box is 16GB of RAM with a 32GB paging file.  I am planning on upgrading it to 32-64GB of RAM sooner than later.  My apps eat ram and paging.

---

### Post by mastablasta on 2017-07-18
for the price of DDR2 you will get a descent newish used PC. think about it.

i am in similar situation (13 years old desktop). it will last while it lasts, then i will switch the whole thing. as long as the data is safe...

---

### Post by Michael_McKenney on 2017-07-18
I just picked up 4GB of DDR2 for $60 at Microcenter on sale.   Newegg has sales on it all the time.

---

### Post by QIII on 2017-07-18
Are you aware that RAM access, even DDR2, is faster than even SSD access by orders of magnitude?

Swap was a costly speed compromise that was necessary when RAM was even more astronomically expensive than astronomically expensive storage.

Could you run on swap?  Sure, if you had just enough RAM to get by.  Do you want to live in the 1970s?  Probably not.  We used to do a lot of doodling and napping waiting for things to happen.

---

### Post by ardouronerous on 2017-07-18
> **Michael_McKenney said:**
> I just picked up 4GB of DDR2 for $60 at Microcenter on sale.   Newegg has sales on it all the time.

I'm not really a supporter of using credit cards and online shopping, I know I'm limiting myself, but I just don't trust online shopping, I'd rather go physically to a computer store and hold, feel and test the component, that's what I did when I purchased an SSD for my old laptop.

I wish someone would create an RAM adapter for old PCs, like DDR4 or 3 to DDR2 adapter, anyone heard if there's something like that?

---

### Post by 1clue on 2017-07-18
Aside of the many good points being made here already, particularly the ones about interface speed and early failures, I need to add something.

Virtual memory is a good thing to have, but a bad thing to actually use. VM was designed as an emergency fallback to prevent system failure for when system RAM was insanely expensive and they literally couldn't get enough of it on a mainframe, and rotating magnetic media was much cheaper.

The idea was that the system had enough RAM for normal processing but occasionally, in unusual circumstances the system could swap out to disk to prevent application failures or even system crashes. It was never intended to be used frequently.

The box I'm typing on started out with 6g with 12g swap, and when I detected that swap had been used I doubled it (both RAM and SWAP), and then again for the same reason doubled it again. I'm at 24g RAM right now, with 48 swap. I use tmpfs for lots of things, mostly as scratch spaces when I build applications but also as caches which need not survive reboot. As such I still maintain swap space and will continue to do so. Even though mine is not on an SSD I could safely put it there, because nothing ever gets written to disk, unless there's an exceptional situation which requires that it be done.

There are plenty of warnings about using an SSD as swap, mostly for early drive failure. An SSD would make excellent swap in the sense that it has random access speeds much greater than a spinning rust drive, but you need to accept the likeliness of early drive failure if you actually plan on using that swap significantly.

---

### Post by 1clue on 2017-07-18
Another thing:

I recommend against buying RAM for a machine you can't put it in right away, at least for personal use and especially when it's already old hardware. You have no idea when or why that box will fail. It may be a lightning strike or a flood or a tornado, for all you know.

I recommend that you max out your current RAM and then run the box until it dies or until you no longer can justify keeping it.

Before you invest in any hardware, always check the prices of the hardware you intend to the price of replacement computers. I firmly believe in reduce-reuse-recycle but you need to keep your feet on the ground. I've bought brand new hardware to replace existing old hardware simply because the cost difference in the electricity used would pay for the new box in under 2 years.

---

### Post by unityforever on 2017-07-24
ddr3 RAM of my old laptop has 21600MB/S write speed and 45ns latency.
my ssd has 460MB/S write speed and 2ms(2000000ns) latency

data speak louder than words.:D

i can't image if someone forced to use ssd as ram, how much time his computer will cost to boot up, may be ten minutes? he may feels opening the menu is rather difficult too. don't mentioned his ssd will be broken in a month.

---

### Post by verymadpip on 2017-07-25
Hi there.
If I recall correctly I got 2 x 2Gb DDR2 for £7 a stick (£14 total) in a second hand game/tech shop named CeX in the UK.  It's a chain & they have all kinds of things, games, phones, cameras, laptops & what have you.  Maybe you have something similar where you are.
They came with a 12 month guarantee, which was pretty cool.

---

### Post by 1clue on 2017-07-25
Long story short, if your computer has room for more RAM and you need more RAM then get more RAM. There is a very real performance advantage and a very real reliability advantage.

Don't keep spare RAM around, or at least don't spend money for it. You can still buy any RAM of any system that might still be in use. That almost certainly won't stop. The exception for keeping spare RAM is if you have a high-availability commercial server and you lose hundreds or thousands of dollars per hour of downtime.

If you have a task and that task can be done in the normal memory 99.99% of the time, then you might consider relying on virtual memory, but consider the amount of wear on your drives and the speed penalty.

If you have a task that often needs more memory than your system can hold then go buy another system.

I have used a system which was almost constantly hitting virtual memory. It was slow but it lasted for years. The thing is, if you depend on that system you never know exactly when that hard drive will give it up. Finally mine did give up, and it gave up right when I needed it to work.

---

### Post by lammert-nijhof on 2017-07-31
I just bought 2 x 1GB of DDR RAM for DOP 250 in China that equals to $6. Here in the Dominican Republic I bought 4 x 2GB DDR2 RAM for DOP 3000 say $72 and the prices are higher here then in the USA or Europe, because of transport costs and import tariffs. Collect or save some money and buy additional memory. 

You can't use an SSD frequently as virtual memory, it will slowdown your system considerably and it will wear out your SSD very fast.

---

### Post by Tadaen_Sylvermane on 2017-08-01
> **ardouronerous said:**
> I'm not really a supporter of using credit cards and online shopping, I know I'm limiting myself, but I just don't trust online shopping, I'd rather go physically to a computer store and hold, feel and test the component, that's what I did when I purchased an SSD for my old laptop.

I wish someone would create an RAM adapter for old PCs, like DDR4 or 3 to DDR2 adapter, anyone heard if there's something like that?

Won't be long before you can't even physically buy groceries in the store. Might want to move up to this century. The days of touching merchandise are nearly gone. Especially old stuff that no one uses, no one will keep it in stock anyway. It's special order stuff.

---

### Post by 1clue on 2017-08-01
> **ardouronerous said:**
> I wish someone would create an RAM adapter for old PCs, like DDR4 or 3 to DDR2 adapter, anyone heard if there's something like that?

If anything were to exist then it would certainly be a low-production device and therefore would be relatively expensive.

The problem is, most boards hold as much RAM as the chip they're running can address. You would need an extra software layer, and I'm not sure PAE would work. Not sure what the mechanics of PAE are, or whether they extend beyond the motherboard's wiring somehow.

I think you should seriously price out a new computer with the same specs as your existing one. Use NewEgg or CDW or whatever to find what sort of thing you want, and then search more specifically on amazon or ebay. You might get a new computer for much cheaper than you're thinking.

---

### Post by ClickXT on 2017-08-02
If you're sticking with that PC - I'd stock up on the RAM.

---

### Post by kansasnoob on 2017-12-30
> **Michael_McKenney said:**
> I just picked up 4GB of DDR2 for $60 at Microcenter on sale.   Newegg has sales on it all the time.

I've been upgrading a bunch of computers using mostly Intel socket LGA775 (and a few AMD AM2+) mobos and used DDR2 is dirt cheap. One example of 2GB sticks that I've found highly compatible is Kingston KVR800D2N6/2G PC2-6400 800MHz **Low Profile** RAM. Of course it's up to you to determine compatibility. 

One thing I've learned over the years is to **avoid "one-sided" RAM**, where the modules only populate one side of the stick. Frequently those "one-sided" sticks will only be read at 1/2 their size. I've encountered that with both Intel and AMD motherboards. Kingston was bad about using the same part # for both two-sided and one-sided modules, but I'm pretty sure their low profile sticks all have RAM modules on both sides of the stick.

Crucial is very good at saying whether or not a specific part # will work in specific hardware - in other words a "reverse lookup". I've had at least a 90% success rate depending on their tool. A sure bet is to use the part # from the RAM being replaced if you're just replacing bad RAM, but I'm usually upgrading rather than just replacing. I can always find 2GB sticks of compatible DDR2 for under $10 each on Ebay.

For that matter does RAM ever actually go bad unless it's been overclocked? I've found that 9 times out of 10 just cleaning contacts and reseating the RAM corrects errors. I've actually only seen RAM "die" twice out of hundreds of sticks, and in both of those cases the RAM was fairly new.

---

### Post by mikewhatever on 2017-12-30
> **ardouronerous said:**
> I'm not really a supporter of using credit cards and online shopping, I know I'm limiting myself, but I just don't trust online shopping, I'd rather go physically to a computer store and hold, feel and test the component, that's what I did when I purchased an SSD for my old laptop.

I wish someone would create an RAM adapter for old PCs, like DDR4 or 3 to DDR2 adapter, anyone heard if there's something like that?

Where I live, they won't let you test things like RAM or SSDs before buying, and holding and feeling electronic equipment seems rather pointless. DDR2 RAM is dirt cheap these days, many people get rid of old machines. I am sure you can get some second hand sticks in good condition just for the cost of shipping.

---

### Post by kansasnoob on 2017-12-30
> **ardouronerous said:**
> I'm not really a supporter of using credit cards and online shopping, I know I'm limiting myself, but I just don't trust online shopping, I'd rather go physically to a computer store and hold, feel and test the component, that's what I did when I purchased an SSD for my old laptop.

I wish someone would create an RAM adapter for old PCs, like DDR4 or 3 to DDR2 adapter, anyone heard if there's something like that?

Ebay uses PayPal. That's safer than scanning a card at the grocery store or an ATM (or worse, one of those outdoor scanners on a gas pump). Newegg and Best Buy also accept PayPal. I recently bought a power supply from Best Buy on-line and picked it up in the store. While I was there I browsed for a few things and noticed the same exact power supply was priced more than double on the shelf! Why pay twice as much for the same identical thing?

As far as testing components - I've never had any brick-n-mortar just say, "hey, go ahead and open it up. Give it a whirl and if you don't like it just shove it back in the box". It's not like you're going to carry your computer into the store and test a new component yourself. You can of course pay someone to do things for you but paying someone to repair a 9 year old computer seems penny wise and pound foolish.

I've seldom gotten anything DOA from Newegg or Ebay but the few times that I have the RMA process was fairly painless. You may of course have to pay return shipping, but that's just like having to pay for the gas to make an extra trip to the store. Amazon is great at even paying return shipping if you buy a faulty item direct from them, but they're often a bit pricier than Newegg or Ebay.

You really have to take your DIY skills into account when dealing with computers. I recently had a friend bring me his computer after he broke the whole darn motherboard trying to upgrade the RAM! Some mobos don't have enough back-support towards the edge just beyond the RAM slots. I've also seen numerous broken RAM slots, as well as mangled CPU sockets. 

By far the biggest DIY error people make is not following proper anti-static procedures. I once saw a guy build a NEW computer on a shag carpet! Yes, sitting on the floor scooting all of the new components around on top of a shag carpet! Then he wondered why it didn't work! I tried to warn him but he ignored me. I've seen components on Ebay pictured resting on top of carpet! Needless to say that's a bad idea.

---

### Post by kansasnoob on 2017-12-30
> **mikewhatever said:**
> Where I live, they won't let you test things like RAM or SSDs before buying, and holding and feeling electronic equipment seems rather pointless. DDR2 RAM is dirt cheap these days, many people get rid of old machines. I am sure you can get some second hand sticks in good condition just for the cost of shipping.

I have a matched pair of one-sided Kingston DDR2 533mhz 2GB sticks I'd gladly give away. It's a 4GB kit but they only read 1/2 size on all the hardware I've tried them in! I have one 1GB stick with the same problem. It's not an AMD vs Intel thing because I've encountered the same problem with both. I think these sticks were pulled from old Everex desktop PC's, I do know they were once read as "good" RAM or I would have tossed them in the recycle bucket.

---

