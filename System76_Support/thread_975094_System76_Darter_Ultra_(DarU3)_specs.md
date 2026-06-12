---
title: "System76 Darter Ultra (DarU3) specs?"
date: 2008-11-08
forum: System76 Support
---

### Post by amosbatto on 2008-11-08
I was looking at the current [Darter Ultra (DarU3)]("http://system76.com/product_info.php?cPath=28&products_id=76") and noticed several discrepancies. First of all, the summary at the top of the page says Bluetooth is included, but lower on the page it shows that Bluetooth is not included by default and you have to buy it as an extra option. 

Secondly it lists the default processor as a "Core 2 Duo T5800 2.0 GHz 800 MHz FSB 2 MB L2 (35 Watt)", but according to  [Intel's website]("http://processorfinder.intel.com/") the T5800 model does not exist. The closest model which I could find was the [T5750]("http://processorfinder.intel.com/details.aspx?sSpec=SLA4D"). 

At any rate, I would like to know exactly what hardware the DarU3 has before I decide to buy one. Could someone who owns a DarU3 please post the output of the following commands:

lspci
lspci -n
dmesg


Thanks in advance,
Amos Batto


Another minor nitpick:
The summary at the top of the page should also inform the reader that a CD/DVD burner is included in the Darter Ultra.

---

### Post by amosbatto on 2008-11-08
I did some more digging on the DarU3. [according to one person]("http://ubuntuforums.org/showthread.php?t=927919&highlight=DarU3"), the DarU3 is based on the Clevo M722T, which is also used by the [Sager NP7220]("http://www.xoticpc.com/sager-np7220-biult-clevo-m722t-p-2414.html"). 

Unfortunately, the Clevo web site doesn't list the M722T. It shows the [M72T series]("http://www.clevo.com.tw/en/products/prodinfo.asp?productid=137") as only containing the M725T and the M728T models. 

Here is the interesting part, the [specs]("http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=137") on the M72T series only show it as supporting the following processors:

Intel®  Core™ 2 Duo processor T9400/T9600 
(2.53/2.8GHz, 45nm, FSB1066, 6MB L2 cache, 478uFC-PGA, Socket P)
	Intel®  Core™ 2 Duo processor P9500 
(2.53GHz, 45nm, FSB1066, 6MB L2 cache, 478uFC-PGA, Socket P)
	Intel®  Core™ 2 Duo processor P8400/P8600 
(2.26/2.40GHz, 45nm, FSB1066, 3MB L2 cache, 478uFC-PGA, Socket P) 

There is no mention on the Clevo website of the elusive "T5800" processor which has a slower 2.0GHz processor speed and a smaller 2MB L2 cache. 

Presumably the Clevo M722T is a special unlisted model which was designed to take a lower-end, unlisted CPU. But I can't be sure of that because [Ava Direct also sells the Clevo M722T barebones]("http://www.avadirect.com/product_details_configurator.asp?PRID=11426") and it makes no mention of the T5800 processor which runs at 2.0MHz with a 2MB L2 cache. Likewise, [PowerNotebooks sells the Sager NP7220]("http://www.powernotebooks.com/specs/Sager/7220specsxrp.php") and it also makes no mention of the T5800 CPU. Here we have a conflict between the specs on the Sager website and a reseller of Sager. 

The [Hypersonic Avenger AG2]("http://www.hypersonic-pc.com/customize-notebooks/avenger-ag2.html?step=2&prods=1854:5136&quant=&specials=0:414,1:415,2:416,3:417,4:418") is also based upon the Clevo M722T and also doesn't offer the T5800 CPU. 

If anyone has one of these machines, could you please post your /proc/cpuinfo.

---

### Post by thomasaaron on 2008-11-10
> the summary at the top of the page says Bluetooth is included, but lower on the page it shows that Bluetooth is not included by default and you have to buy it as an extra option

Thanks. Passed this on to the webmaster. It's fixed.

```

The summary at the top of the page should also inform the reader that a CD/DVD burner is included in the Darter Ultra
```

It's the same for all of the laptops. They list this in the configurator. I'll pass it on to the webmaster, though.

> but according to Intel's website the T5800 model does not exist

It not being listed on Intel's website does not mean it doesn't exist. See... 
[http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#.22Merom.22_.28standard-voltage.2C_65_nm.29](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#.22Merom.22_.28standard-voltage.2C_65_nm.29)
[http://www.google.com/search?q=T5800&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=T5800&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

It may be because Intel makes some products available to oems that it does not make available to the general public. Or it could just be that they've not updated their website with this product yet. I'm not really sure what's up with that.

---

### Post by amosbatto on 2008-11-10
Glad to see that the T5800 exists on Wikipedia--it gives me more faith that it is a real part. 

Well, it was fun investigating the DarU3, but ultimately I decided not to buy the DarU3. It is a great little machine for the price, but I have too many doubts about the keyboard. Most of the keys appear to be 18mm wide, which is an acceptable size. I am currently typing on a keyboard with keys which are 20mm wide without any problems. But the . , / (period, comma, slash) keys are only 14mm wide and I am afraid that those tiny keys will cause too many typos. 

I scaled up an image of the keyboard to its actual size and tried to type on the image. I could type OK on all the 18mm keys, but I found that my fat fingers would hit two keys at the same time on those tiny 14mm keys. 4mm doesn't seem like much of a difference, but I found that it was. I have checked a number of other 12" laptops and none of the other laptops which I am considering reduce the size of the . and , keys. 

Maybe I could learn to type on the DarU3 keyboard, but I have my doubts. It is sad because the DarU3 has exactly the specs that I want at the price that I want to pay.

---

### Post by calibre97 on 2008-11-12
I am looking at a Dell D630 to replace my older and heavier HP dv5035nr. The pluses on the Dell are small size and weight, takes a secondary battery that fits inside the bay (don't always need an optical drive), and has a high resolution of 1440x900 with a discrete NVIDIA graphics option. For about the same price (eBay, or refurbed at the dell site). The minuses include no SDHC slot built-in (my HP has it and it's a nice convenience), and a pokey PC Card slot requiring an adapter to get ExpressCard (though for what I'm at a loss).

Comparing the Darter with the Dell is an exercise in frustration. I'd love, LOVE to support you guys, but the graphics are built-in only (though that may not be as much a problem as I might think), and the resolution is stuck at 1280x800 which, granted, is what I've got now on the HP but still, I'm looking to move UP.

Any chance you guys would support WXGA+ in the near future? Like within 6 months or so? THAT would seal the deal for me.

---

### Post by thomasaaron on 2008-11-12
Is the Dell a 12" laptop? 1400x900 graphics seems like a lot for such a small notebook.

At any rate, R&D is always looking for the new latest-greatest thing. Not sure if they are looking at a higher-resolution for the Darter, though.

---

### Post by calibre97 on 2008-11-12
OK, fine. It's a 14.1" screen, but still small and light (4.3lbs). I keep thinking a 4 lb 12" laptop would be good enough, as it'd be 2lbs or so lighter than my HP with the same resolution, but then I use my D620 at work with the 1440x900 resolution and I get greedy again. The Pangolin is nice, but very heavy for a machine I want to take on the go (couch, Paneras, Peet's, etc) all the time...at least more than I do now with my HP beast.

Looks like I'm stuck with a dilemma then. Or I'll have to go with the Dell which isn't HORRIBLE as they are at least supporting Ubuntu now and stood up for XP. I like your machines but I'm greedy and want something riiiiight in the middle. Damn frustrating, it is. Not a reflection on you, by the way, just acknowledging I want it all.

---

