---
title: "how crucial is ECC RAM for my server"
date: 2016-01-23
forum: Server Platforms
---

### Post by milkboy007 on 2016-01-23
TL: DR- im planing deploying a low load (less than 10 active local networked user, low. no of outside visitors. ) single server, running print server, file server, and LAMP.[INDENT]On top of LAMP ill be running, Owncloud and dolibarr ERP sofware. it only stay on during work hours.
Is ECC RAM crucial on my setup?
[/INDENT]


Long story. i have been running these services for a while now (except for dolibarr which is hosted online) on _several_ old destkop grade PCs, NON-ECC memory with little trouble.
to reduce cost and simplify maintainace, im thinking of making a simpler setup and consolidating them all on one device (planning to get a new HW)
Stuff i read on forums is giving me conflicting views, some says ECC RAM is a must, while other says it is optional, as long as it is not extremely high load, availability & sensitive, like banking(where a single mistake could cost a fortune).:sad:
To add more to the confusion, [some vendors]("http://www.asrockrack.com/general/products.asp#Server") are marketing obvious desktop grade setup as server solutions.[-(

so i need a clarification, if not, at least a consensus. Is ECC RAM mobo crucial for my setup? how severe & frequent is the corruption if i use NON-ECC RAM?
i do have a disaster management plan (run automated databse backup, twice a day, to 2-3 online storage as redundant backup.)
lastly, could you give me some setup examples where ECC RAM is needed? so that i can get a better understanding.

thx.

---

### Post by MAFoElffen on 2016-01-23
It boils down to speed versus reliability. It depends what you are doing and what your goals and the limits of your scope.

I "was" a hardcore old-school server admin, in that about 9 years ago, in regard to servers up to that point: Raid, Cards, SCSI > SATA, ... ECC Registered Memory. ...and I was chasing the newest and most reliable hardware, which is a moving target.

Out of 14 servers here, they have all evolved. A lot of my RAID (most) when to software RAID, or went away completely for other solutions.   All but one is running ECC-R RAM. Basically, EEC-R systems have a less likely change of crashing. It still happens, but the odds are with you.

I went back to school, then other things evolved. I left Win in, because they gave me licenses, and I needed then to support my coursework. (so now not "all" Linux Servers: One Solaris and one Win Server Host.) On that one, I went for a new system with the option to go either ECC Registered, or normal memory. I went with Gsaming memory for less that 1/4 the cost of ECC Registered. (128G RAM max unbuffered) ECC Registered is slower but much more reliable. Because of it being more reliable, that same system is configured to go 1T with EEC-R. Besides, 64G sticks of DDR3 EEC-R are like an Gold... but you don't get the down the resalable investment back. So you need to figure out if the results of the trip along the way is paying you back.

In your scope, unbuffered would work and be cost efficient. The reliability factor of memory concerns detection, and correction of memory errors. When we look at applications were those are most important, we think of scientific, financial, and ***file servers***. So what you need to weight when looking at "Should I do this to save money?" is weighed against the question, "How important is the accuracy,  integrity, and the security of my data being there worth it to me?" At some point, is spending the money protecting your investment or a stumbling block in getting there.

Now a days, if the scope may change, I look for a server solution that is scalable. As memory goes, with systems that takes both, you could always install with non-ECC, then later upgrade to EEC-R. That is what I did with my last server ... and has done fine for me so far.

---

### Post by milkboy007 on 2016-01-23
yeah, i thought so too.
the plan was, if after research shows that ECC is not required, start with non-ECC, upgrade only if needed, since non-ECC dont lose much of its resale value and ECC memory cost more initially.
that way if i dont need it i can save some, and if i do need it, i would only pay a little bit more in total cost of the system, since non-ecc ram can be easily re sold.
if research shown otherwise, might as well save the trouble and go ECC.

but research has shown me conflicting views. i'm hoping that this forum would provide clearer insight

---

### Post by MAFoElffen on 2016-01-24
That new server of mine... I play and test with. I test virtuals and play games on. I push it very hard... and with non-ECC gaming memory it screams and have no memory errors. I could still go with ECC-R but...

8GB DDR3 non-ECC = $40 x 12 = 96GB, $480
32GB DDR3 ECC-R = $500 x 4 (becuase mine you have to go by groups of 4) = 128GB, $1000.

---

### Post by mastablasta on 2016-01-25
ECC if data loss is an issue. You can't "upgrade if needed". you Will find out when you need it that data is corrupt :)

anyway for your server normal RAM is good enough, just get a quality one. and also make good backups (since you have some ERP on it)

---

### Post by milkboy007 on 2016-01-25
> **mastablasta said:**
> ECC if data loss is an issue. You can't "upgrade if needed". you Will find out when you need it that data is corrupt :)

anyway for your server normal RAM is good enough, just get a quality one. and also make good backups (since you have some ERP on it)

i think you misunderstood when i say upgrade if needed. i meant, if data loss is frequent, like >6x/per yr, then i would change to ecc ram (im buying a ecc capable mobo).
im planing on doing twice a day, daily minor backup (data only), stored for a week, then 1 major monthly backup, stored for 6 month, on 2 off site storage. 
im also doing a weekly hdd image backup on an external non-raid hdd
i forgot to mention, im leaving the ERP database on the current online hosted server.
so overall in the event of system failure, outage should theoretically short

@MAFoElffen
thats y  i have reservation on buying ecc ram immediately. it is so expensive.
i will only buy if the cost is justified.

---

### Post by darkod on 2016-01-25
I might be wrong, but I have always considered ECC as a device to help you avoid corruption in the RAM, not for more stability or to avoid crashes... A memory that offers you Error Correction helps you protect against data corruption.

Imagine the following situation. The data goes through the non-ECC RAM and part of it (few bytes) get corrupted. There is no mechanism to detect that. It is rare, but it does happen. After the RAM when the data is written to the disk it is already too late. The data has already been corrupted compared to the original, and is written to disk as corrupted (changed). No raid or backup can help you there, because you are backing up already corrupted data.

That is what mastablasta said, you will find that out only at the moment when you need that particular data... You will see that you can't read it.

Having said all that, I do think manufacturers/vendors charge too much for ECC memory. And taking into account how rarely errors happen on non-ECC it is really difficult to decide whether it's worth the extra money.

Also to comment the ECC-R that MAFoElffen mentioned. I believe he wanted to say ECC Registered. Actually there is also Unregistered (Unbuffered) ECC memory, often called ECC UDIMM. Non-ECC can only be unbuffered but ECC can be unbuffered (UDIMM) or registered (RDIMM).

The ECC RDIMM is the most expensive, then comes the ECC UDIMM which should cost about double of non-ECC UDIMM. And it still offers error correction. Whether it is worth that money only you can decide...

---

### Post by MAFoElffen on 2016-01-25
> **darkod said:**
> Also to comment the ECC-R that MAFoElffen mentioned. I believe he wanted to say ECC Registered. Actually there is also Unregistered (Unbuffered) ECC memory, often called ECC UDIMM. Non-ECC can only be unbuffered but ECC can be unbuffered (UDIMM) or registered (RDIMM). It really didn't catch on... and I think it fell out from the too many choices kinds of affair (at least around here.)

The ECC RDIMM is the most expensive, then comes the ECC UDIMM which should cost about double of non-ECC UDIMM. And it still offers error correction. Whether it is worth that money only you can decide...
Yes. As Darko said, I was referring to ECC Regisitered... You can usually get used UDIMMS for about half the price of RDIMM, but there is a reason for that, a lot of people reselling UDIMM's bought them by mistake... There is not a lot of motherboards today, that can use UDIMMS. And usually if it uses one type, it doesn't used both types. Certainly, out of all the servers I have here, none of them can use UDIMM memory.

Only in the past 3-4 years have they started making boards that have memory controllers that can sense and use both Unbuffer non-ECC -OR- ECC Registered memory.

Another note on memory: Some server board "makes" are touchy about memory. IBM and Some HP's are two that seem to be "sensitive", enough that they recommend using their own "certified" (to work in their servers) memory, while under their warranty and service contracts. That is in the IBM's Virtualized Active Memory Sharing Pools and HP's Advanced ECC modes. Dell, Tyan, ASUS and Supermicro... don't really care that much and seem more tolerant.

---

### Post by mastablasta on 2016-01-26
if it's for a company use ECC. private server non ECC should be fine. they know companies Will use ECC so they have a higher price.

companies can afford it. it's an investment. it's also a cost (tax deduction, tax breaks?!).

yes it's really like insurance companies... for example chances of hail that Will be big enough to ruin the roof is actually pretty low, but many people would still insure it for that event. you never knwo when it might happen and when it does it Will be cheaper than to pay for the whole roof.

similar here - you won't see the issue unit it is too late.

---

### Post by 1clue on 2016-01-26
Keep in mind that all older hardware and most newer hardware uses either ecc or non-ecc, there is not much out there that you can choose.  Also the CPU either supports it or doesn't, you need to check both parts.

[http://www.servethehome.com/unbuffered-registered-ecc-memory-difference-ecc-udimms-rdimms/](http://www.servethehome.com/unbuffered-registered-ecc-memory-difference-ecc-udimms-rdimms/)

ECC lets you correct some data errors in RAM, and detect others.  Note that this usually only happens on systems which are always on and go long times between reboots.  It also happens more when hardware gets older.  If the register has 1 data error it can be corrected, if it has 2 then it can be detected.  In the 1-bit scenario you gain something in that an error is transparently fixed.  In the second scenario you gain in that your bad data is not written to the disk or used in a critical transaction.

Registered memory is important if there are a lot of memory modules on your system.  Electronically speaking it takes power from the CPU to read memory. To get around this they put a register (similar to a CPU register, or similar to one full-width unit of RAM) in between the normal stick and the bus, it's built into the memory stick.  That register will read the value coming back from the module and latch it under its own power, making it easier for the CPU to read/write.

So filter that through your original requirements:

Speaking FOR ECC memory, you mentioned an ERP app. In my opinion if you're doing business finances on a computer that means hands-down you want as much error correction/detection in the hardware as you can get.  Also IMO that means you have a computer which handles your ERP and nothing else.  My accountant says she builds her computers from the official sources (Microsoft, etc) and then disconnects the computer completely.  No software updates, no Internet, no wifi, no flash drives, no CDROMs, no electronic anything which did not originate in her office.  She does backups which will never be attached to a network-connected device, one goes to an on-site fire safe and another goes to an off-site safe deposit box.  I think that's a little extreme but she correctly says this is the only way to ensure no malware or security breach happens.

Speaking AGAINST ECC memory, you mentioned that you turn the computer off frequently.  That matters.

In the over-all price of your computer, the difference between ECC and non-ECC is small.  If you're getting new hardware for a business then I personally think registered ECC is the only way to go.  Used memory was mentioned above, it might be feasible for a workstation or a personal setup, but there's no way I'd put it in a business server that actually mattered.

---

### Post by lukeiamyourfather on 2016-01-28
If you value your data then use ECC memory. I'm on board with what James Hamilton has said, basically everything should have ECC memory including client systems.

[http://perspectives.mvdirona.com/2009/10/you-really-do-need-ecc-memory/](http://perspectives.mvdirona.com/2009/10/you-really-do-need-ecc-memory/)

---

### Post by milkboy007 on 2016-01-30
thx for all the info.guys
now im leaning towards getting ECC ram modules.

@ mastablasta 
yes the company can afford it. it is more a decision making about if it is unnecessary or a justified spending (value)
as my orginal post indicated, all the info from internet searches are conflicting and further investigation is needed before purchase.
i can see now that the consensus agree that ecc would be best for data integrity. 
i have excepted anything can happen, even with ecc data loss can still happen. that why based from simulated testing (risk management standpoint). a week worth of data loss has minimal impact.
month worth = minor disruption. backups strategies all based on that.
funny you should say insurance. i view it like choosing a health care insurance. some provide unnecessary coverage (i.e alternative medicine, which i view most as a placebo at best) for an extra cost, which i will never use.
one of the reason i want to get a better understanding to justify the cost. hahahaha........

@lukeiamyourfather & 1clue
i dont think its cost effective for all client to use ECC ram. as current client have no data corruption problem without ecc
i have yet to suffer tru a data corruption that disrupt business to a halt, or cause financial loss. over the past 5 years i can only recall it happening once or twice in the office.
its more about value rather than cost. i mean **if** there is no impact in getting a non-ecc instead of ecc ram, therefore ecc ram has little value in my setup.
internet searches doesnt present a clear picture. like any decision, a good information is crucial.

---

