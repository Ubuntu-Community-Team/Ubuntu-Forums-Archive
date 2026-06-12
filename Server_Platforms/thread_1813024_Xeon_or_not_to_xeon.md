---
title: "Xeon or not to xeon?"
date: 2011-07-27
forum: Server Platforms
---

### Post by 007casper on 2011-07-27
Xeon or not to xeon?

What are the advantages of xeon?
3x the encryption, decryption; 
SMP - Symmetric multiprocessing; 
ECC ram 
IPMI - Intelligent Platform Management Interface (newer model)
sometimes a larger l3 cache.

What are the disadvantages of xeon?
cost; is it really necessary?

thank you.

---

### Post by jerrrys on 2011-07-27
i run older dual xeon setup and that is its main advantage:  [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing")

as far as L3 goes,  i could upgrade processors to have an L3, but the overall gain in doing this is questionable.  so i stick with just L2. 

some of the older xeon's are not capable of [KVM]("http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine"), if thats a concern to you. my processors, being older, do not have this capability so i use virtualbox.

---

### Post by 007casper on 2011-07-28
Thank you.  I am really trying to list all the cons vs pros through out.

I want to figure out how crucial it is to use xeon chips for a high traffic sites, and especially that gets extreme burst of traffics through out the day occasionally.  

I wonder if a server set up can be utilized with i7 2600k, or 990X EE; 980X etc. and can get better performance for half the price.

Instead of building one xeon server, you can build two server with i7 990x set up for the same price. 

Supposedly, i7 990x is about the same performance as a Xeon X5690 minus the ECC, and encryption, decryption speed.

and then there is the good old clustering, even with mobile chips with N570.

Any thoughts...

---

### Post by 007casper on 2011-07-30
I am trying to figure out how crucial it is to use xeon chips.  Who is using it?  In what environments?  Why?  After all, I know some servers are good in certain scenarios, and overkill in others.

- xeon: rendering fx, astronomy due to speed in calculation what else??? ecommerce?

I have several xeon servers.  At this point, I wonder if using commodity server set up through clusters would be a better scenario since i7 series are competing with xeon chips.  Also, computation is distributed on online set ups.  And now, supposedly mobile chip clusters seem to give better performance than xeon servers?  Is this possible?  or just hype?

Is it really necessary to use xeon chips for online application set ups?

I know cluster set up is abstract, and it is not a clear comparison.

any clarification, suggestion, constructive criticism welcome.  Thank you.

---

### Post by rubylaser on 2011-07-30
The other advantage you can get in Sandy Bridge processors is VT-D for PCI passthrough in Xen or ESXi (although the 2400 Sandy Bridge also supports VT-D, so you don't necessarily need to get a Xeon to have it).

ECC RAM is definitely a good thing if you have a lot of RAM in your system to prevent the occasional bit flip.  Personally, the E3-1230 Xeon on a Supermicro board, with 8GB of ECC RAM is around $500 all in, so it's not really that expensive, and you'll have IPMI, and real server hardware.

---

### Post by Entilza on 2011-07-30
> **rubylaser said:**
> Personally, the E3-1230 Xeon on a Supermicro board, with 8GB of ECC RAM is around $500 all in, so it's not really that expensive, and you'll have IPMI, and real server hardware.

This is the exact setup I just built and it's working out great.

The E3-1230 is basically an i7 but with Xeon features.  The E3-1230 also does not have integrated chip video so it runs cooler and draws less power since most server boards have onboard video.  The bonus is it's actually cheaper than the i7 2600 !

The supermicro board I am using is X9SCA-F  (The IPMI Feature is priceless and it's basically free)

---

### Post by 007casper on 2011-07-31
> the E3-1230 Xeon on a Supermicro board, with 8GB of ECC RAM is around $500 all in
interesting.  Thank you for the heads up.

it seems as it pumps 78 megabits/GHz
2 gigabit / (2 socket x 4 cores x 3.2GHz per core)= 78 megabits/GHz


other thoughts on the net
The current line of Xeons are based on the same architecture as the i7. The difference is usually that the Xeons are the cream of the crop. They run cooler and at lower voltages. Otherwise, performance is usually identical.

    Xeons are able to be used in multi-socket motherboards, where i7s are not. 
    Xeons are also usually the first to be updated. There are 8-core Xeons, but not i7s yet, though they are still based on the same architecture. 
    The additional reliability of the Xeons is very important in servers where the lower heat dissipation and power consumption are essential. And the server must be able to treat many administration processes, manage disks at the same time.

---

