---
title: "Advice on upgrading vs. replacing a not-so-old computer"
date: 2012-06-23
forum: The Cafe
---

### Post by blackbird34 on 2012-06-23
Hi everyone

I've just benefited from the erratic (but very good) French education system by  gaining entrance to a french university where **I** will be paid to study (and the salary is a handsome windfall :guitar:).  So i thought i'd enquire about getting a better computer/making mine better with all the hardware specialists here :D

Currently I have [this ]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&destPage=document&docname=c02636271&lc=en&product=5032445&tmp_docname=c02636271")computer (specs in french but understandable) : a Compaq Presario CQ56 133SF, Intel Celeron 900 2.2GHz, 2GB RAM/250 GB HDD. It runs ok with Ubuntu (Unity) 12.04. _Several questions_:

--I'd like to max out the RAM to 8GB: which (DDR2) would you recommend (price, quality?...)
--Would this computer support an SSD drive? Also do you think there might be a way of keeping the HDD in there and putting an SSD in too?  
--Would a processor upgrade be possible/ any use? or would it require a graphics card upgrade too? 
--could i overclock that processor or would it be damaging/ not worth the effort/ insanely complicated ?
--Which of these options (or what other upgrade) would give the computer the biggest performance boost (1080p video is a little choppy at present, when it works....) ? 

This is all a bit theoretical at the moment, but curiosity is always a good thing :D Any ideas please?

---

### Post by Carborundum on 2012-06-23
> **blackbird34 said:**
> 
--I'd like to max out the RAM to 8GB: which (DDR2) would you recommend (price, quality?...)

The cheapest you can find. Quality tends not to be an issue with memory these days.

> 
--Would this computer support an SSD drive? Also do you think there might be a way of keeping the HDD in there and putting an SSD in too?
As far as the computer is concerned, there is no functional difference between an SSD and an HDD, so yes, it does support it. You might be able to keep the HDD if you can find an optical drive slot -> 2.5" adapter, but those tend to be difficult to come by.
> 
--Would a processor upgrade be possible/ any use? or would it require a graphics card upgrade too?
The CPU is usually soldered to the mainboard in laptops, so unless you are a wizard with the soldering iron, this is almost certainly not possible.

> 
--could i overclock that processor or would it be damaging/ not worth the effort/ insanely complicated ?
Overclocking on laptops is more difficult than on desktops, but not impossible. However, running a laptop overclocked 24/7 is not a good idea since they tend to have rather poor heat dissipation compared to desktops.
>  
--Which of these options (or what other upgrade) would give the computer the biggest performance boost (1080p video is a little choppy at present, when it works....) ? 
In terms of overall system responsiveness, the SSD without a doubt. However, it won't help with video playback at all. The only thing that will help you there is the processor, where your choices are somewhat limited, as per above.

---

### Post by blackbird34 on 2012-06-23
And can you use RAM from different brands together or not?

---

### Post by sudodus on 2012-06-23
> **blackbird34 said:**
> And can you use RAM from different brands together or not?
Yes, the specifications are more important the brand name. For example, if you mix different speed specs the slowest card will set the overall speed.

---

### Post by blackbird34 on 2012-06-23
Right. And can i just add one 4GB RAM stick to my existing 2GB then? Thus avoiding having to buy two RAM sticks and getting left with my own extra parts...

---

### Post by ExSuSEusr on 2012-06-23
I am thinking that for the price of an upgrade - so a little more money you might be able to pick up a much nicer system.

---

### Post by Paqman on 2012-06-24
> **blackbird34 said:**
> Right. And can i just add one 4GB RAM stick to my existing 2GB then? Thus avoiding having to buy two RAM sticks and getting left with my own extra parts...

It all depends on how many memory slots you have.

The memory controller in that machine will be dual-channel. To get the most out of it your memory should always be fitted as pairs of matching sticks.

So assuming you have two slots:
[LIST]
[*]If you have 2x 1GB already then you'll need to replace both sticks. You could fit 2x 2GB, or 2x 4GB if your motherboard supports that much.
[*]If you have 1x 2GB installed you could fit a second 2GB stick to give you 4GB in dual channel.
[/LIST]

I would go for 4GB myself. Any apps that require more than that (eg: big CAD suites) probably aren't going to run well on that machine anyway. Definitely get an SSD though, the OCZ Vertex ones have really dropped in price and are decent drives. Besides speed, fitting an SSD to a laptop makes it much more durable and slightly increases battery life.

---

### Post by HeroOfCanton on 2012-06-24
If you need to upgrade the RAM, CPU, video card, and storage drive you're probably better off buying a new machine. ;)

---

### Post by blackbird34 on 2012-06-24
Not a "need" yet, just thinking about it...

Thanks everyone... although getting a new computer just because i can seems a bit of a waste, this poor box initiated me to Ubuntu and Linux, it has sentimental value :D

---

### Post by mips on 2012-06-24
> **blackbird34 said:**
> Hi everyone

I've just benefited from the erratic (but very good) French education system by  gaining entrance to a french university where **I** will be paid to study (and the salary is a handsome windfall :guitar:).  So i thought i'd enquire about getting a better computer/making mine better with all the hardware specialists here :D

Currently I have [this ]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&destPage=document&docname=c02636271&lc=en&product=5032445&tmp_docname=c02636271")computer (specs in french but understandable) : a Compaq Presario CQ56 133SF, Intel Celeron 900 2.2GHz, 2GB RAM/250 GB HDD. It runs ok with Ubuntu (Unity) 12.04. _Several questions_:

--I'd like to max out the RAM to 8GB: which (DDR2) would you recommend (price, quality?...)
--Would this computer support an SSD drive? Also do you think there might be a way of keeping the HDD in there and putting an SSD in too?  
--Would a processor upgrade be possible/ any use? or would it require a graphics card upgrade too? 
--could i overclock that processor or would it be damaging/ not worth the effort/ insanely complicated ?
--Which of these options (or what other upgrade) would give the computer the biggest performance boost (1080p video is a little choppy at present, when it works....) ? 

This is all a bit theoretical at the moment, but curiosity is always a good thing :D Any ideas please?

> **blackbird34 said:**
> Not a "need" yet, just thinking about it...

Thanks everyone... although getting a new computer just because i can seems a bit of a waste, this poor box initiated me to Ubuntu and Linux, it has sentimental value :D

If you really want to go down this road then download the service manual for the laptop.

The CPU 'might' be replaceable if it is socketed, if it's soldered then no. Also keep in mind that mobile CPUs are usually more expensive and harder to come by. There might be a way to OC your existing CPU but you would have to do some googling.

SSD will work in just about any machine as long as the interface (PATA/SATA) is correct.

RAM is easy to do.

GPU is usually not upgradeable.

Don't be to emotional about your old laptop. The money you intend on spending could quite easily buy you a new one with a new warranty while spending big $$$ on old hardware does not make sense seeing if it dies that money is kinda wasted.

I will try and find a service manual for your laptop and be a bit more specific in my answers if you are willing to wait a bit.

EDIT: Here is the service manual- [http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=4247498&targetPage=http%3A%2F%2Fbizsupport2.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc02657369%2Fc02657369.pdf](http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=4247498&targetPage=http%3A%2F%2Fbizsupport2.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc02657369%2Fc02657369.pdf)

---

### Post by mr-woof on 2012-06-24
First question, on such an old laptop why do you need 8gb of ram? 

With 32 bit operating systems, you can only see a maximum of 3.5gb, I assume this is the same with Ubuntu, must admit I'm not sure.

Why not get a better laptop and use both, one for home and take the older laptop to the classes?

---

### Post by Carborundum on 2012-06-24
> **mr-woof said:**
> 
With 32 bit operating systems, you can only see a maximum of 3.5gb, I assume this is the same with Ubuntu, must admit I'm not sure.
It's not. 32-bit Ubuntu uses something called physical address extension to allow the kernel to make use of more than 4 GB of RAM.

---

### Post by mr-woof on 2012-06-24
Interesting, didn't know you could do this, thanks for the headsup :)

[https://help.ubuntu.com/community/EnablingPAE/](https://help.ubuntu.com/community/EnablingPAE/)

---

### Post by mips on 2012-06-24
Ok I looked at the manual and will comment further.

1. Your CPU is socketed which means it's easy (depending on your skill level with a screw driver) to swap out. See page 75 of the manual.

Your laptop uses [mobile Penryn]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_Dual-Core_microprocessors#.22Penryn.22.2C_.22Penryn-3M.22_.2845_nm.29") based CPUs and the service guide says the [T4500]("http://ark.intel.com/products/42925") is compatible with your laptop. So if you can find a new or used working one at a decent price look into it.

Remember to clean all the thermal paste off of the heatsink and to replace it with new stuff, something good like Arctic Silver 5 etc.

2. To max out the RAM to 8GB you would have to remove the existing 2GB SODIMM(s) and replace them with 2x 4GB 800MHz **DDR2** SODIMM modules. RAM from the likes of Hynix, Kingston, Transcend etc will be fine.

3. You can replace your existing SATA HDD with any SATA SSD as long as it's not thicker than 9.5mm. You don't have to buy the fastest SSD (SATA3 etc) as you're laptop probably only supports SATA2. You should be able to get more info from your system based on the chipset used. If you know the chipset you can go look up whether it's sata1 2 or 3. If a newer SATA3 SSD costs less than a older SATA2 SSD you might as well buy it seeing it will work just fine on the older SATA ports. You can move your existing HDD to a external USB enclosure.

Do some costing based on the above information and see how much upgrading all this stuff will cost you in comparison to a new laptop and then make your final decision.

---

### Post by mips on 2012-06-24
> **mr-woof said:**
> 
With 32 bit operating systems, you can only see a maximum of 3.5gb, I assume this is the same with Ubuntu, must admit I'm not sure.


Ubuntu 12.04 ships with the PAE kernel on the 32-bit version so it's not a issue any more.

---

### Post by blackbird34 on 2012-06-24
That last link doesn't work... could you attach the pdf file or give a direct link to it please?

---

### Post by mips on 2012-06-25
> **blackbird34 said:**
> That last link doesn't work... could you attach the pdf file or give a direct link to it please?

Very strange, I tested it after posting it yesterday and it was working fine (It was a direct link btw.). When I tried it now it would not work.

I uploaded the file here [http://filegooi.co.za/get2/8712ab3c5c65daa69368290ef7435b80/c02657369.pdf](http://filegooi.co.za/get2/8712ab3c5c65daa69368290ef7435b80/c02657369.pdf) for you as an alternative source.

I just tried accessing the HP page I got that link from again and the site is giving me problems but I eventually got to the main page.

See Service and maintenance information section
[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=us&docIndexId=64179&taskId=135&prodTypeId=321957&prodSeriesId=4247498](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=us&docIndexId=64179&taskId=135&prodTypeId=321957&prodSeriesId=4247498)

or
[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=us&docIndexId=64179&taskId=135&prodTypeId=321957&prodSeriesId=4247498#2](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=us&docIndexId=64179&taskId=135&prodTypeId=321957&prodSeriesId=4247498#2)

direct link again,
[http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=4247498&targetPage=http%3A%2F%2Fbizsupport2.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc02657369%2Fc02657369.pdf](http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=4247498&targetPage=http%3A%2F%2Fbizsupport2.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc02657369%2Fc02657369.pdf)

EDIT: I just tested those links again. The direct link to the PDF immediately opened a save/download window. The first two links however took a bit of time to open but they eventually did.

If you have a problem again I suggest you just keep trying. The site seems dodgy.

---

### Post by Warpnow on 2012-06-25
I would not invest much into upgrading a Celeron 900 system given it will be the bottleneck of virtually ever endeavour.

---

### Post by mips on 2012-06-25
> **Warpnow said:**
> I would not invest much into upgrading a Celeron 900 system given it will be the bottleneck of virtually ever endeavour.

Depending on the price if he upgrades to a Penryn Pentium Dual-Core T4500 CPU it might just be worth while.

Edit: I see you can buy a T4500 CPU on eBay for about US$15-25, well worth it imho.

---

