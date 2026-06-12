---
title: "Please recommend me a 1 GB video card"
date: 2010-04-03
forum: The Cafe
---

### Post by lightningfox on 2010-04-03
Hi
I'm planning to upgrade my PC.

My PC's  current setup is:
Pentium 4
1 GB RAM
ATI Radeon 9200 Pro video card


My new setup will have an Intel i7 processor and 4 GB Ram.

I'm planning on getting a 1 GB video card, but I'm not sure which video card to get.

Please recommend me a good 1 GB video card which is compatible with Linux.
The video card should preferrably have a good open source driver, otherwise if it doesn't have a good open source driver it should be easy to install a proprietary driver for it.

---

### Post by EarthMind on 2010-04-03
If you're an opensource fanatic: ATI HD 4890.
If you prefer quality and support over anything: Nvidia GTX 260 or higher

---

### Post by Psumi on 2010-04-03
> **EarthMind said:**
> If you're an opensource fanatic: ATI HD 4890.
If you prefer quality and support over anything: Nvidia GTX 260 or higher

Sorry to hijack a thread like this, but, do you know of any opensource cards on laptops with 512 MB or more?

---

### Post by lightningfox on 2010-04-08
Earthmind thanks for your reply.

I think I'll get a Ati hd 4890.


Can someone please tell me a good but not too expensive motherboard for Intel core i7.

Also, please tell me a good DDR3 2 GB RAM brand compatible with Intel core i7.

---

### Post by blueshiftoverwatch on 2010-04-08
> **EarthMind said:**
> If you're an opensource fanatic: ATI HD 4890.
If you prefer quality and support over anything: Nvidia GTX 260 or higher
My GTX 260 has 896MB of RAM, which is pretty close to 1GB. There are 1GB models though. When I was looking at GPU's in November while building my computer and comparing benchmarks. I've found that as far as Nvidia cards go. The GTX 260 is as high end as you can get before the price to performance ratio gets too crazy.

---

### Post by Psumi on 2010-04-08
> **blueshiftoverwatch said:**
> my gtx 260 has 896mb of ram, which is pretty close to 1gb. There are 1gb models though. When i was looking at gpu's in november while building my computer and comparing benchmarks. I've found that as far as nvidia cards go. The gtx 260 is as high end as you can get before the price to performance ratio gets too crazy.

gts 250.

---

### Post by WinterRain on 2010-04-08
Personally, I would stick with nvidia. I've never had a problem with nvidia and linux.

---

### Post by steveneddy on 2010-04-08
[http://www.nvidia.com/object/product_geforce_9800_gx2_us.html](http://www.nvidia.com/object/product_geforce_9800_gx2_us.html)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4644390&sku=B52-9826](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4644390&sku=B52-9826)

---

### Post by Warpnow on 2010-04-08
Your current setup likely has an AGP video port, whereas i7/i5 motherboards have a PCI-e port. Its very likely that any card you buy now for your current build would be incompatible. Also, AGP cards are really expensive nowadays.

---

### Post by lightningfox on 2010-05-02
Thank you for your answers.

---

### Post by swoll1980 on 2010-05-02
Nvidia GT250

---

### Post by earthpigg on 2010-05-02
```
[chris: ~]$ sudo lshw | grep 250
                product: G92 [GeForce GTS 250]
```

playing urban terror at >90fps on max settings, on GNU/Linux.

---

### Post by WinterRain on 2010-05-02
> **EarthMind said:**
> 
If you prefer quality and support over anything: Nvidia GTX 260 or higher

Won't work. The OP's computer is AGP. Those cards don't come in AGP. He needs to stay a couple generations back as far as video card. One of [these]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639%201305520548%201068310557&name=512MB") cards is the best he's going to do, unless he can find a 8400 AGP. But I would stay with nvidia. You've been warned.

---

### Post by WinterRain on 2010-05-02
> **swoll1980 said:**
> Nvidia GT250

The OP needs AGP, not PCI Express. The ATI 9250 he currently has is definitely AGP, as I just sold one.

---

### Post by 3rdalbum on 2010-05-02
He talks abouut his 'new setup' with an i7 processor, so a PCI-E card is appropriate. Do not buy an ATI, they are junk on Linux.

---

### Post by EarthMind on 2010-05-02
I strongly agree that you'll just be wasting your money if you'll buy an ATI HD 4890 just to use on Linux. However, if you dual boot with Windows for gaming then an HD 4890 is a good choice.

The peformance in Gnome is Ok-ish but it sucks big time in KDE, as it doesn't seem compatibe with kwin/KDE 4.4. The open source driver is better for GUI performance on both environments and the catalyst driver is much better for games.

In short:
Using linux only: Nvidia!
Dual booting: ATI/Nvidia

---

### Post by MooPi on 2010-05-02
If your stuck with AGP slot then I'd suggest Nvidia 6200 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814133312](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133312)
Looks like a good representative of the class. The extra ram for the card is only good for the mega huge displays. I run 512 mb of integrated graphics (Nvidia 7025)for my 22 inch monitor well.

---

### Post by lightningfox on 2010-05-09
Hi

I bought a new laptop (Samsung r580) instead of upgrading my desktop computer.

---

