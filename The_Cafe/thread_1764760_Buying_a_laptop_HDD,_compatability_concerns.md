---
title: "Buying a laptop HDD, compatability concerns"
date: 2011-05-22
forum: The Cafe
---

### Post by Brendan_ST on 2011-05-22
Hello I'm interested in buy a new 12.5mm thick 2.5" hard drive for my  laptop (HP Pavilion DV5 1054TX) so I can get 1TB capacity but my laptop  only fits 9.5mm drives. I am willing to have the drive poking out the  bottom a bit held in with Gaffa tape because I'm hard core and my laptop  is usually stationary.
My first question is then: Do 12.5mm thick  drives require extra power or something that will make it not work in my  laptop? - I know 3.5" drives do but am not sure about thicker 2.5"  drives.

Secondly, will 2.5" enterprise drives work just the same  (be 'compatible' with my laptop) - are they worth spending the extra for  the performance gain? My laptop only supports 3 Gb/s Sata but the  seagate drive is a 6Gb/s drive but has other advantages over the WD  drive? (latency, spin rate...)?

Drives I've found:
Western Digital WD10TPVT
Seagate ST91000640NS (enterprise)

Thanks for your time.

---

### Post by PhillyPhil on 2011-05-22
> **Brendan_ST said:**
>  I am willing to have the drive poking out the  bottom a bit held in with Gaffa tape because I'm hard core and my laptop  is usually stationary.


:D Is there some reason you don't have a desktop instead?

I can't imagine all 1TB of data will be speed-sensitive, so you might want to consider an SSD for speed, coupled with an external HDD for capacity.

---

### Post by cayphed on 2011-05-22
Usually the new SATAIII (6Gb/s) drive are backwards compatible with SATAII (3Gb/s) and typically SATA 2.5" drives "chew" the same amont of power with the exception of SSD's using less, same princaple for 3.5" drives and even 5.25"... 
I'd also imagine if you insulated the drive with tape were needed you could almost get away with just cliping the chassis (metal fram inside) in laptop to get it to fit without so much of the "bulge" underneath, but I honestly **DON'T** recommend doing that....
Best thing todo if power supply still presents an issue, google the current and new drive and see what you get, the manufactures usually post the spec's.

---

### Post by Brendan_ST on 2011-05-22
> **PhillyPhil said:**
> :D Is there some reason you don't have a desktop instead?
Money is the main problem, buying a whole new computer would put me into negative dollars :P and I do like the portability of the laptop, even with a hard drive hanging out, a broken keyboard and no battery compared to moving a box+ screen + keyboard/mouse... I am considering it though If I can gather some cash...

> I can't imagine all 1TB of data will be speed-sensitive, so you might  want to consider an SSD for speed, coupled with an external HDD for  capacity.

Hmm yeah I read something about how drives are their fastest towards the outside?? of the disk or something... Also my craptop only has one drive bay so I can't have multiple drives... I might have to shift all my personal data onto external drives then so I could keep my current 320gb internal for OS's... pitty both my external drives are behaving very strangely at the moment but I have no idea how to diagnose them ;/

@cayphed, I've already had a look under the drive and there is no room to spare at all - the wireless card is crammed under it. I tried plugging one of my 3.5" drives into the laptop just to see what would happen and it didn't even power on, so I guess the power pack on my external drive enclosures is because of the extra power requirement.

---

### Post by Brendan_ST on 2011-05-22
The Seagate enterprise drive spec says
12V start max current     0.85A
5V start max current     0.51A
Average idle power     2.95W
Average operating power     5.43W

The WD drive spec says
5 VDC
Read/Write    500 mA
Idle    400 mA
Standby    50 mA
Sleep    20 mA
Power Dissipation
Read/Write    2.50 Watts
Idle    0.85 Watts
Standby    0.25 Watts
Sleep    0.10 Watts

and for comparison the seagate 750GB laptop drive spec says

5V start max current                 1.0A
Average idle power                 0.96W
Average seek power                 2.5W

I'm not really sure what to make of it all but it appears the enterprise drive requires an extra 12v current?

---

### Post by cayphed on 2011-05-22
If the external is a 3.5" then yes, they must have that extra omph... 
They wedged the wi-fi under the HDD???? O.o
Does the wi-fi link up with a cable? Or hard pluged in, you may be able to move it if so, like to a spot where a HDD spin doesn't interfere with the signal....
If you have Windows on daul-boot you could test the external like discribed on this page if it helps,
[http://www.ehow.com/how_6890830_test-external-hard-drive.html](http://www.ehow.com/how_6890830_test-external-hard-drive.html)

---

### Post by cayphed on 2011-05-22
they're still within the reccomended 3Ampere range, so I don't see any issues except for the gaffa tape buldge....
I can sympathy with you on costs to build a new one, my lappy is a whole year old and is starting to feel the age worry's, I'm building my new system week by week, part by part, just got to save the big dollars for the gaphics card, then I'm done. :)

---

### Post by Brendan_ST on 2011-05-22
I will have a go at that filesystem check soon but I suspect its something physical - executing ls, mkdir test, touch test, cd <folder>, all have random delays of 1 to 30 seconds and copying files can sometimes get 30 MiB/s fine then other times it will sit on a few MiB/s or few hundred KiB/s so I really don't understand the problem with it. As for my other drive I'm experiencing magically disappearing & reappearing files & folders so I really need another drive just to make sure I don't lose important data.

Ooh cool What kind of graphics card are you going for? I've read that you can't get any with open source drivers or that the only open source ones are community efforts :S. the nvidia drivers work great for me but I wish they were open ;/
maybe building my own computer could be my solution to avoiding Microsoft as the only company I've found that sells decent computers without windows is system76 but they don't sell in Australia unfortunately

---

### Post by cayphed on 2011-05-22
I'm saving the dollars for a GV-R697OC-2GD  [http://www.gigabyte.com/products/product-page.aspx?pid=3784#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3784#ov) as I'm an AMD/ATI fan, I've already got my 6-core am3 waiting for the over clock pain.... ^_^

---

### Post by Brendan_ST on 2011-05-22
If you go to the Downloads section their and view the drivers it only has windows ones listed.. what are you planning to use the computer for?

---

### Post by cayphed on 2011-05-22
The ati ubuntu driver I will wait for... Wont be too much longer now anyway.
I hope.
I also use windows, for mostly games at LAN party's, the "old-faithfull" laptop is most likely going to die
a painfull death if I don't build a gaming machine soon.... :'(

---

