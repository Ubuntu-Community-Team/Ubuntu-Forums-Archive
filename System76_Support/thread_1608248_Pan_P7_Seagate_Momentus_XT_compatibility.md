---
title: "Pan P7 Seagate Momentus XT compatibility"
date: 2010-10-28
forum: System76 Support
---

### Post by Mendel314 on 2010-10-28
I was just about to order a momentus xt to put in my pan p7, I just want to make sure that it will be compatible.  Has the xt been tested with the p7? should I expect any issues?

---

### Post by isantop on 2010-10-29
As long as it's a standard SATA device, you should be fine. That said, we haven't officially tested it in the PanP7, so we can't guarantee it will work. 

If you do decide to try it out, be sure to let us know how it goes.

---

### Post by zaphod777 on 2010-10-30
I would think that it would be fine since according to Seagate the OS see's it as a normal SATA HDD and everything is done on the back end by the drives controller.

---

### Post by Mendel314 on 2010-10-30
Awesome. I'll order it now then.

What would be the easiest way to clone the HD I have now? I really don't want to have to reconfigure my desktop etc. It took forever to get it the way I like it

---

### Post by zaphod777 on 2010-10-30
check out clonezilla [http://clonezilla.org/](http://clonezilla.org/) it is my favorite disk cloning software. You can do a backup image to a USB drive and then restore it to the new drive. Or if you buy one of those 10 or 20 dollar sata external enclosures you can do a HDD -> HDD clone. Then the new drive will be identical to the old one. Then you can use the enclosure with your old drive and have a spare external USB HDD.

Also once you install the new HDD you will need to use an Ubuntu LiveCD and use GPARTED to expand your partition to use the rest of your new 500 GB HDD.

---

