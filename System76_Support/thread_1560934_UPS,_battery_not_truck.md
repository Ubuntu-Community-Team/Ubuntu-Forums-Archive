---
title: "UPS, battery not truck"
date: 2010-08-25
forum: System76 Support
---

### Post by BuggyFunBunny on 2010-08-25
I've a Ratel, and I'm using Intel SSD for some databases' datastores.  Just dev/test, but, well, you know.  The Intel parts don't have a supercap or other "safety" item, so a UPS makes sense.  

It's been ages since I bought one, and doing some research led to a question about the power provided:  square wave, quasi sine wave, etc.

The other issue is live power monitoring.  In the Olde Days, some UPS would have a RS-232 cable twixt itself and the computer, and would initiate a controlled shutdown if the line power was lost for a specifiable period.

I can't find that sort of information from the Usual Dealers.

Nor do I want to spend $500 on the thing; if that's the minimum, I'll just do more frequent backups.

So, does anyone know of a UPS that delivers "safe" power (I gather anything better than square wave is OK, but I'm not even sure of that), has a tether to the computer, and can be had for $500 or less?

thanks,
Robert

---

### Post by BobvanderPoel on 2010-08-25
Get an APC since they are supported by Linux. Others may be as well, but APC is good.

I just installed a ES 550 and it's handled 2 minor power fails without problem. On my pretty much standard desktop with monitor it promises about 1/2 of standby, more than enough for me.

Both web and stand-a-lone programs for monitoring are avail from the standard repositories.

---

### Post by jpv on 2010-08-25
Check out [http://www.refurbups.com/](http://www.refurbups.com/), I've been a happy customer for a few years now.

I can't really help with brands, but just about anything should be supposed using apcupsd, nut, powstatd, or upsd.  I think modern units use USB, but older ones may still have serial, often with funky pin-outs.  So watch out for that since you need a) a serial port and maybe b) a funky cable.

---

### Post by BuggyFunBunny on 2010-08-26
> **BobvanderPoel said:**
> Get an APC since they are supported by Linux. Others may be as well, but APC is good.


Thanks.  All the ads talk about windoze.

---

### Post by 7528620xs on 2010-08-26
I just installed a ES 550 and it's handled 2 minor power fails without  problem. On my pretty much standard desktop with monitor it promises  about 1/2 of standby, more than enough for me.





---------------------------------------------------------------------------------------
       [ed hardy shirts](http://www.edhardysalemall.com/)/[ed hardy shoes](http://www.edhardysalemall.com/)/[ed hardy](http://www.edhardysalemall.com/)

---

### Post by tgalati4 on 2010-08-26
Check craigslist for a used APC smartups or back-ups PRO--the ones with the metal cases.  Replace the batteries and run apcupsd.  You might have to solder a serial cable together, some models have strange pinouts, but it's not difficult to do.

The plastic case UPS's can catch fire when the MOSFETs flame out.

---

### Post by BulletTootg on 2010-08-30
> **BuggyFunBunny said:**
> I've a Ratel, and I'm using Intel SSD for some databases' datastores.  Just dev/test, but, well, you know.  The Intel parts don't have a supercap or other "safety" item, so a UPS makes sense.  

It's been ages since I bought one, and doing some research led to a question about the power provided:  square wave, quasi sine wave, etc.

The other issue is live power monitoring.  In the Olde Days, some UPS would have a RS-232 cable twixt itself and the computer, and would initiate a controlled shutdown if the line power was lost for a specifiable period.

I can't find that sort of information from the Usual Dealers.

Nor do I want to spend $500 on the thing; if that's the minimum, I'll just do more frequent backups.

So, does anyone know of a UPS that delivers "safe" power (I gather anything better than square wave is OK, but I'm not even sure of that), has a tether to the computer, and can be had for $500 or less?

thanks,
Robert


You don't need to spend $500 unless you're buying the newest and coolest toy. You need to get a line interactive UPS that offers power filtering, AVR boost/drop and outputs a sine wave. Also, you need to get one with a rs-232 port.


If you're looking to buy brand new and under $500.00 then you can go with a UPS like the [APC Smart-UPS 750VA]("http://excessups.com/smartups-750va-smt750-p-168.html") which offer 500W, outputs a sine wave and has all the proper power protection. This unit will prevent all the problems caused by power anomalies. 

If you're looking to get more value and spend less money you can either go with a [Smart-UPS 1500]("http://excessups.com/smartups-1500-sua1500-p-38.html") which has 950W, sine wave output and all the bells and whistles. If you don't care much for the fancy looks and want to get even more value, then go with a [Smart-UPS 1400]("http://excessups.com/smartups-1400-su1400net-beige-p-40.html") which is the same only doesn't have a USB port and is beige. It has the same capacity as the 1500, more capacity than the 750, and is the most value for the money. Data center protection.

Any of the Smart-UPS units will be ten times better than any XS, ES, or RS APC units. Those aren't designed to be very reliable and aren't meant for important work. You can also save some money by buying locally through Craigslist and replacing your own batteries. Look around and make sure you get a good deal. There's a lot of excellent equipment out there for good prices.

---

### Post by tonyyarusso on 2010-09-06
I have two of these:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16842101067](http://www.newegg.com/Product/Product.aspx?Item=N82E16842101067)

1500VA, 865W, choice of RS232 or USB connection, approximated sinewave.  Seems to do the trick pretty well for my home equipment.

---

