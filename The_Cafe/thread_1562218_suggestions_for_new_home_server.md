---
title: "suggestions for new home server"
date: 2010-08-27
forum: The Cafe
---

### Post by Red Kelly on 2010-08-27
My old server packed it in so great excuse to get a new one. Only thing is I have been out of the loop as for new good hardware and was looking for suggestions. 
I would use it mainly for file sharing, streaming and myth tv. 
I'm thinking i5 prosessor, i don't know what motherboard tho.
motherboard needs atleast 2 pci slots and 1 pci e mini.
So any suggestions would be greatly appreciated.

---

### Post by Grenage on 2010-08-27
So you are basically after an HTPC?  Something low power, with HDMI?  You can get pre-built Atom ION machines, which are pretty good.  I usually opt for non-atom, because I like to use my HTPC as a video converter, too.

---

### Post by linux18 on 2010-08-27
If you can give up the pci slots, a laptop with HDMI and an i7 CPU makes a great low power server. My laptop has an i7 with 6 GB of RAM for under $1000. just remove the screen, attach a huge intercooler, and upgrade to 8GB of RAM. It's worth a look if the pci slots aren't absolutely necessary

---

### Post by Red Kelly on 2010-09-05
> **Grenage said:**
> So you are basically after an HTPC?  Something low power, with HDMI?  You can get pre-built Atom ION machines, which are pretty good.  I usually opt for non-atom, because I like to use my HTPC as a video converter, too.

No I have an htpc (asrock ion 330) i am after an upgrade in servers i have 2 1TB hdd and stream media to htpc, laptop, desktop, and phone. 

The server I have at the moment only has 2 sata conections for 3 hhd and a dvd player.

I would like to future proof as much as i could so 6 sata and a few PCI (for Tv tunercards).

but thanks for the sugestion.

---

### Post by Paqman on 2010-09-05
If it's just serving files you don't need an i5. My file server has a little ARM chip, and works great.

---

### Post by Red Kelly on 2010-09-05
Yer i gess your right i5 might be a bit of over kill how much prosseing power would streaming a tv card use? i3 good enough? 
could i ask what motherboard u use?

---

### Post by Austin25 on 2010-09-05
> **Red Kelly said:**
> Yer i gess your right i5 might be a bit of over kill how much prosseing power would streaming a tv card use? i3 good enough? 
could i ask what motherboard u use?
I would go with an AMD.

---

### Post by CharlesA on 2010-09-05
> **Austin25 said:**
> I would go with an AMD.

+1. Cheaper and all AMD CPUs support hardware virtualization.

---

### Post by Red Kelly on 2010-09-05
Thanks so AMD it is then.

still need to find a motherboard. any ideas?

---

### Post by BkkBonanza on 2010-09-05
+1 Low power.
Save the planet. Save money. 24/7.
My mini-itx C2D w/T5440 uses about 20W instead of 130W on the desktop.
With Atheros miniPCIe wifi for AP.
Boots from usb flash stick.
Dual LAN to use a router/firewall.

[http://www.logicsupply.com/products/nf93r_lf](http://www.logicsupply.com/products/nf93r_lf)

---

### Post by Red Kelly on 2010-09-05
@BkkBonaza thanks I like the look of it. will investigate further.

---

### Post by Red Kelly on 2010-09-05
MSI MS-96D7 looks good to. not as energy efficent but I can sleep a little easyer nowing that it will be mostly powered buy the solar panals on the roof during the day.
[http://www.msi.com/index.php?func=proddesc&maincat_no=133&prod_no=2085](http://www.msi.com/index.php?func=proddesc&maincat_no=133&prod_no=2085)

If i could just find a price.

---

### Post by toupeiro on 2010-09-05
I second the statements about the use case of your server.

General file serving doesn't require much horsepower at all.  If you were going to have a multi-tuner DVR, having an i7 to thread on with a lot of RAM would be beneficial.  

It's hard to argue with an i7 right now.  The price point is good, the performance scalability is huge.  Make sure you install your DIMM's in quantities of 3 to take advantage of the triple channel memory controller.

---

### Post by Red Kelly on 2010-09-05
@toupeiro So are u saying I need the power of an i7 to use DVR?
I didn't think it would take that much power.
If an i7 then what motherboard to go with it?

---

### Post by CharlesA on 2010-09-05
You'd only really need that much horsepower if you are transcoding video on the fly, or running a boatload of virtual machines.

---

### Post by Paqman on 2010-09-05
These days with stuff like VDPAU you can offload a fair bit of the processing for video to the GPU instead of the CPU. I'm not really up on MythTV, but [it looks like]("http://www.mythtv.org/wiki/VDPAU") you can get VDPAU working with it alright. I'm using it on XBMC and that was a doddle to set up.

---

### Post by Red Kelly on 2010-09-06
Zotac NM10-B-E-ION?

EDIT: forget that not enough pci slots

---

### Post by zdenal on 2010-09-06
I have running small green linux server for a year and I'm satisfied with power consumption and others.

Check this link:

[http://polach.cc/small-and-green-linux-home-server](http://polach.cc/small-and-green-linux-home-server)

Maybe it fit your needs.

---

### Post by Slug71 on 2010-09-06
Asus or Tyan Opteron board.

---

### Post by Red Kelly on 2010-09-07
ASUS P5BV-C/4L ?
[http://www.amazon.com/dp/B000ZLTO7E/ref=asc_df_B000ZLTO7E1241721?smid=A2JUPN4BTA3CZV&tag=dealtmp445894-20&linkCode=asn&creative=395105&creativeASIN=B000ZLTO7E](http://www.amazon.com/dp/B000ZLTO7E/ref=asc_df_B000ZLTO7E1241721?smid=A2JUPN4BTA3CZV&tag=dealtmp445894-20&linkCode=asn&creative=395105&creativeASIN=B000ZLTO7E)

---

### Post by CharlesA on 2010-09-07
> **Red Kelly said:**
> ASUS P5BV-C/4L ?
[http://www.amazon.com/dp/B000ZLTO7E/ref=asc_df_B000ZLTO7E1241721?smid=A2JUPN4BTA3CZV&tag=dealtmp445894-20&linkCode=asn&creative=395105&creativeASIN=B000ZLTO7E](http://www.amazon.com/dp/B000ZLTO7E/ref=asc_df_B000ZLTO7E1241721?smid=A2JUPN4BTA3CZV&tag=dealtmp445894-20&linkCode=asn&creative=395105&creativeASIN=B000ZLTO7E)

That would work, but It would probably be more cost effective to just use a regular desktop CPU instead of getting server-class equipment.

---

### Post by Delvien on 2010-09-07
> **linux18 said:**
> If you can give up the pci slots, a laptop with HDMI and an i7 CPU makes a great low power server. My laptop has an i7 with 6 GB of RAM for under $1000. just remove the screen, attach a huge intercooler, and upgrade to 8GB of RAM. It's worth a look if the pci slots aren't absolutely necessary

That would be a really expensive low power server.. The same can be accomplished for under half what a laptop can cost.

---

### Post by Red Kelly on 2010-09-08
@CharlesA yer your right looking at the cost I probably dont need to be that reliable.

Asus M3A?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131234](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131234)
reviews for this are a bit up and down.

Dam too many to choose from. This feals like it will never end. :) not complaning tho.

---

