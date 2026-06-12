---
title: "Can I replace an HDD wih an SSD"
date: 2010-03-16
forum: The Cafe
---

### Post by Abu_Dayya on 2010-03-16
Not really ubuntu related, but I want to get the lenovo s10-3t netbook and it only comes with a 320GB HDD. I don't really need all that storage on a netbook. So, I'm thinking of replacing it with a 60GB SSD, Is that possible? Can I just buy an SDD and slide out the old HDD and put in the new faster SSD instead??

---

### Post by Psumi on 2010-03-16
Is the HDD SATA?

if it's PATA, IDE or something else, then it will probably not work. I believe SSDs only come in SATA.

---

### Post by Abu_Dayya on 2010-03-16
yes, I believe its SATA. So you're saying it works?

---

### Post by Grenage on 2010-03-16
The drive is likely SATA in a proprietary cradle?  It should be a simple swap.

---

### Post by Psumi on 2010-03-16
> **Abu_Dayya said:**
> yes, I believe its SATA. So you're saying it works?

I don't see why it shouldn't. Especially when the connectors should be the same.

Oh and, don't bother clonezilla'ing to the SSD, Clonezilla hates mapping to smaller drives apparently.

You might want to also check the [Disadvantages](http://en.wikipedia.org/wiki/Solid_State_Drive#Disadvantages) of using an SSD. ESPECIALLY the last point, if you plan to keep the battery in your laptop/netbook.

---

### Post by 3rdalbum on 2010-03-16
Even a 60 gigabyte SSD is going to be reasonably expensive.

If it's NOT expensive, then it's going to be much worse than your existing hard disk. Make sure you read benchmarked reviews of your chosen SSD, and make sure it has TRIM support.

---

### Post by Abu_Dayya on 2010-03-16
Thanks Psumi. Although I didn't know that SSDs consume more power than regular HDDs. Guess I'll have to check that the SSD I get is flash

Thanks again

---

### Post by Detonate on 2010-03-16
Prices are starting to come down.  Intel just announced a new 60GB SSD available  at a price of $125 each on orders of 1000 or more.

---

### Post by ikt on 2010-03-16
> **Psumi said:**
> 
You might want to also check the [Disadvantages](http://en.wikipedia.org/wiki/Solid_State_Drive#Disadvantages) of using an SSD. ESPECIALLY the last point, if you plan to keep the battery in your laptop/netbook.

I don't understand, nobody uses dram-ssd drives.. lol

---

### Post by Psumi on 2010-03-16
> **ikt said:**
> I don't understand, nobody uses dram-ssd drives.. lol

That's what I get for blindly reading Wikipedia.

---

### Post by Post Monkeh on 2010-03-16
> **Detonate said:**
> Prices are starting to come down.  Intel just announced a new 60GB SSD available  at a price of $125 each on orders of 1000 or more.

i'll take 2000

---

### Post by fjf on 2010-03-17
Do you have a link?.  All I could find are the 40 GB ones.

---

### Post by cascade9 on 2010-03-17
You shouldnt have any problems installing a SSD where they was a HDD before. You might well have some of the issues that are around with SSDs (wear leveling, etc) but it should work. If you get the 'rigth' SSD is should have a few advantages compared to the old mechanical HDD- 

[http://blog.laptopmag.com/lenovo-ideapad-s10-much-faster-with-ssd-upgrade](http://blog.laptopmag.com/lenovo-ideapad-s10-much-faster-with-ssd-upgrade)

> **Psumi said:**
> Is the HDD SATA?
 
 if it's PATA, IDE or something else, then it will probably not work. I believe SSDs only come in SATA.
 
 There are PATA SSDs- 
 
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150636+1421530855&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=636&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150636+1421530855&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=636&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

> **ikt said:**
> I don't understand, nobody uses dram-ssd drives.. lol

Not many people do, but they are out there, have been for a long time. Hyderdrive and Gigabyte iRAM are the only ones I've heard of.

[http://www.hyperossystems.co.uk/](http://www.hyperossystems.co.uk/)
[http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2179](http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2179)

They will blow flashed based SSDs away on speeds, they are very, very fast. 

> **Abu_Dayya said:**
> Thanks Psumi. Although I didn't know that SSDs consume more power than regular HDDs. Guess I'll have to check that the SSD I get is flash

Thanks again

DRAM based SSDs are rare, expensive and you've not going to find one in 2.5'' AFAIK. Flash based SSDs (typically) use less power than HDDs, though there are some situations/models where a flash based SSD will use more power.

---

### Post by Grenage on 2010-03-17
> make sure it has TRIM support

Does Linux actually have proper TRIM support these days?

---

### Post by cascade9 on 2010-03-17
> **Grenage said:**
> Does Linux actually have proper TRIM support these days?

TRIM support is in the 2.6.33 kernel, and its being backported to 2.6.32 IIRC. It migth well work with hacks on earlier versions as well. 

[http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-33-933312.html](http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-33-933312.html)

---

### Post by Grenage on 2010-03-17
Excellent; last time I checked, the support was flakey at best.  Good to see that isn't the case any more.

---

### Post by 3rdalbum on 2010-03-17
Yeah TRIM has been added to Linux.

---

### Post by anaconda on 2010-03-17
Yes, it can be done, but why would you want to do that?
I can figure 3 reasons, but not one of them is a very good reason:

is the hd too loud? Propably not..
is the current hd too hot? it could be..
does the hd consume too much power? With new netbooks battery life, which is normally >6h this is not a problem..

But if you do get a SSD-disk, get a good one. I have bad experiences from a cheap and really slow ssd-hd. It was (and is) really really slow. eg. starting nautlus (or almost any other program) can take >30s.
And when using the same machine (acer aspire one) from normal hd it is fast..

And I expected the SSD would be faster than normal hd...

---

