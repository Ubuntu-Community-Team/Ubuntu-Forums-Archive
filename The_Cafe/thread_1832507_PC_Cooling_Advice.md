---
title: "PC Cooling Advice"
date: 2011-08-24
forum: The Cafe
---

### Post by BrokenKingpin on 2011-08-24
I just picked up an Antec Three Hundred case for a home media server. I came with two fans installed, one top mounted 140mm fan, and one back mounted 120mm. You can see pictures here:
[http://www.canadacomputers.com/product_info.php?cPath=6_112&item_id=040477](http://www.canadacomputers.com/product_info.php?cPath=6_112&item_id=040477)

Normally I would think this is enough cooling, as it isn't a super high end PC. The only concern I have is that I will be installing 4-5 hard drives, and I was wondering if I should put a front mounted case fan in for cooling the drives? The disks are all 500GB Seagate drives. I am not sure if having that many drives in there would require extra cooling.

---

### Post by coffee412 on 2011-08-24
Im running 5 seagate drives. 4 are 320 giggers and one is 80 gigs for the OS. I have them in a full tower case of course with a front fan running to draw in cool air across the drives. 

I think the most important thing is to keep atleast half an inch of room between all the drives. This helps alot in the cooling. I have never had a problem with the drives heating up.

coffee

---

### Post by LowSky on 2011-08-24
I always recommend a front fan. Heck my current box has two.
Otherwise the case will only pull hot air.

And if you think I have a huge tower think again:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811112299](http://www.newegg.com/Product/Product.aspx?Item=N82E16811112299)
All I did was switch the blue fans out for a few Noctua's for silent computing.

---

### Post by BrokenKingpin on 2011-08-24
The only reason I hesitate to add the third fan is noise. With the current fans it should get great air flow over the mobo, just not through the drives.

---

### Post by LowSky on 2011-08-24
> **BrokenKingpin said:**
> The only reason I hesitate to add the third fan is noise. With the current fans it should get great air flow over the mobo, just not through the drives.

My computer makes a very low amount of noise. It has a total of 8 fans. Right now I'm sitting equal distance form my PC and my open window. What I hear is crickets and a slight wind noise from my PC. My PS3 (fat model) makes more noise than my PC, if that helps makes any sense of the level of noise. Bear in mind I using 5 drives, one SSD and 4 Hard drives ranging from 750GB to 2TB. Heat isn't an issue but I like things cool.

Now you may be wondering why I have 8 fans, so here is what I got

1 x 140mm top fan
3 x 120mm fans, one in rear, two in front
1 x 120mm CPU fan
The Power Supply built in fan
The Graphics Card's built in two fans (Nvidia GTX 460)

The Nvidia card barely ever runs loud even while gaming. Right now my typing and the crickets outside seem louder.

My suggestion is buy a fan that has a speed controller built in. for instance Antec makes a few, or buy a model that claims low noise, Noctua seems to be one of the more popular (and in my case proven) low noise fans.

---

### Post by christopher.wortman on 2011-08-24
[http://www.google.com/products/catalog?q=hard+drive+fans&hl=en&client=ubuntu&hs=rX6&channel=fs&prmd=ivns&bav=on.2,or.r_gc.r_pw.&biw=1600&bih=749&um=1&ie=UTF-8&tbm=shop&cid=7358255247547628319&sa=X&ei=uLtVTtO3AdLpgAeIrME7&ved=0CJsBEPMCMAQ](http://www.google.com/products/catalog?q=hard+drive+fans&hl=en&client=ubuntu&hs=rX6&channel=fs&prmd=ivns&bav=on.2,or.r_gc.r_pw.&biw=1600&bih=749&um=1&ie=UTF-8&tbm=shop&cid=7358255247547628319&sa=X&ei=uLtVTtO3AdLpgAeIrME7&ved=0CJsBEPMCMAQ)

These are super nifty and they work wonderfully. They just attach to the bottom of your hard disks... Not to mention they are compatible with Windows 98  and ME man!

---

### Post by cariboo on 2011-08-25
My server has 7 hard drives installed the temps range from 34°C to 41°C, before adding a couple of 80cm fans to the front of the case, the drives in the middle of the stack were running at 50°-55°C. There is an 8th drive in a usb enclosure, but it has been RMA'd twice, so I'm not sure if I should put it back in the case.

My feeling is that a server shouldn't be see or heard, so mine is located in my garage, I have a media center PC connected to my tv that only has a power supply fan, that is quiet enough that it can barely be heard when the house is totally silent.

**Edit** The media center pc is going to be replaced by a networked Blu-Ray dvd player or an LG smart hub. A decent home theater case costs more than either of those devices, and now that an easy to setup dlna server is available in the repositories, why not?

---

### Post by Aquix on 2011-08-25
It's not just about putting in a bunch of fans. You have to think about the airflow. If you put in a fan to blow air onto the harddrives then that warm air will go into the cabinet and you need to make sure that another fan blows that air out somewhere. And if the out fan is close to the cpu or gpu, then it might not be worth it if they become warmer because of warm air from cooling the hard drives. Just keep and eye on your lm-sensors temps

---

### Post by 3rdalbum on 2011-08-25
Replace the two existing fans with Noctua ones, if your budget can afford it.

Buy another Noctua fan for the front. Definitely. You will want to cool the drives, sure; but you also want to equalize the air pressure in the case.

With the fans only pushing air outside the case, you'll get a lot of suction into the case. Any spare hole or crevice will be sucking in air, and more importantly: Dust.

With a front fan as well, pushing air into the case through the dust filter at the front, the air pressure inside is more equal to what it is outside the case; hence, less suction through the holes in the case, and also less dust intake. Of course, the front fan sucks air in - but it does so through the dust filter that should be at the front of your case.

Dust really is the enemy of a computer because it's a good heat insulator.

That's the main reason why you should get another fan - to minimise dust.

---

### Post by BrokenKingpin on 2011-08-25
Thanks for the info guys. I will check out the temperatures with lm-sensors and go from there.

---

### Post by christopher.wortman on 2011-08-25
> **cariboo907 said:**
> My server has 7 hard drives installed the temps range from 34°C to 41°C, before adding a couple of 80cm fans to the front of the case, the drives in the middle of the stack were running at 50°-55°C. There is an 8th drive in a usb enclosure, but it has been RMA'd twice, so I'm not sure if I should put it back in the case.

My feeling is that a server shouldn't be see or heard, so mine is located in my garage, I have a media center PC connected to my tv that only has a power supply fan, that is quiet enough that it can barely be heard when the house is totally silent.

**Edit** The media center pc is going to be replaced by a networked Blu-Ray dvd player or an LG smart hub. A decent home theater case costs more than either of those devices, and now that an easy to setup dlna server is available in the repositories, why not?

You have 2x 31 inch fans? 0.o I would love to see the size of your case...

---

### Post by BrokenKingpin on 2011-10-24
I forgot to report back on this. I got the new case setup, and with the two stock fans everything is actually running cooler than they were in the old case with more fans. I ended up switching from 5 drives to 2 larger drives, which also probably helped keep the heat down.

Thanks for all the input guys.

---

