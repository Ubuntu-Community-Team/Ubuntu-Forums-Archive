---
title: "Ubuntu and Samsung  How well they play together?"
date: 2011-03-31
forum: The Cafe
---

### Post by dh04000 on 2011-03-31
Does anyone here know how well Samsung laptops and ubuntu play together?

I got my eye on one with a nvidia 330m without optimus.

---

### Post by beew on 2011-03-31
My main labtop is a Samsung R469 (Nvidia G105M) Bought it around jan 2010 for $700.

 Works beautifully with Ubuntu 10.10. Everything (well almost) works out of the box (need to install Nvidia driver of course) The only thing that doesn't work is the brightness applet. Funny thing is that the Samsung people told me the machine was built for Winodws (came with Windows7 home premium) and wouldn't work with Linux at all. Not knowing better at the time I took these people seriously and I didn't install Ubuntu until late 2010. :)

---

### Post by beew on 2011-03-31
BTW, are you sure your machine is Optimus free? 

This asus laptop uses a GT335M but is Optimus enabled (I posted it on your other thread to warn you since you said the Nvidia 2XX and 3XX cards are safe)
[URL="http://www.asus.com/product.aspx?P_ID=Z8eiRpmQaN8XIgxW"]http://www.asus.com/product.aspx?P_ID=Z8eiRpmQaN8XIgxW

[/URL]

---

### Post by dh04000 on 2011-03-31
> **beew said:**
> BTW, are you sure your machine is Optimus free? 

This asus laptop uses a GT335M but is Optimus enabled (I posted it on your other thread to warn you since you said the Nvidia 2XX and 3XX cards are safe)
[URL="http://www.asus.com/product.aspx?P_ID=Z8eiRpmQaN8XIgxW"]http://www.asus.com/product.aspx?P_ID=Z8eiRpmQaN8XIgxW

[/URL]

I triple checked. No optimus to be found!  :)

---

### Post by Quadunit404 on 2011-03-31
Ubuntu performs pretty flawlessly on mine, just needed to do a bit of hacking to get the function keys working right and then compile a custom kernel to get it to suspend properly. Samsung NP-RF510 btw.

---

### Post by dh04000 on 2011-03-31
> **Quadunit404 said:**
> Ubuntu performs pretty flawlessly on mine, just needed to do a bit of hacking to get the function keys working right and then compile a custom kernel to get it to suspend properly. Samsung NP-RF510 btw.


That's the one I want!

You'll have to post how to fix that stuff on here too. I'd be thankful if you did.

Function keys, like screen brightness, and sound? Or the wireless one and off key, which I'd be screwed without working?


How is the gaming on it!?! Can you run wine/steam/tf2/l4d2?

How about amnesia, oilrush and other native linux games????

OMG OMG OMG (bouncing in chair like little girl)

I'M SO EXCITED!

EDIT: OMG!

---

### Post by Quadunit404 on 2011-03-31
I forgot which files to edit, I'll have to check Linux on my Samsung for that, and compiling a kernel so suspend will work can be done through KernelCheck. Shouldn't take more than two hours, depending on how many CPU jobs you give to the compilation.

For Wireless and Bluetooth, there's the Samsung netbook PPA from VoRia, which has this utility called Samsung Tools that allows for you to control wireless and Bluetooth. Even though it doesn't officially support the NP-RF510 I have tried it and it works with the wireless/Bluetooth cards.

Haven't tried out Oil Rush yet, will next month, but World of Goo runs perfectly. You should be able to run Steam/TF2/whatever on it through Wine (I already did on my old laptop, but at rather low settings due to the sucky graphics card) but I haven't confirmed that yet as I do almost all my gaming on Windows nowadays.

Oh, and if you're getting it BEFORE Natty comes out, you'll need to install Nautilus Elementary or the menus will randomly stop working right. Natty AFAIK doesn't require this.

---

### Post by beew on 2011-03-31
There is a launchpad ppa for all kinds of fixes for Samsung netbooks (I am sure some work for things other than netbooks as well)
[https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa")

There is also a supporting forum for the ppa. You can find the link on the lp page linked above.

---

### Post by gnomeuser on 2011-03-31
The Samsung Fn stuff should work in kernel 2.6.39, I believe it was just merged. So fear not Ocelot will like you out of the box at least.

---

### Post by leclerc65 on 2011-03-31
Just bought a NF210-A03. Backlight problem (very dim screen when on battery) solved thanks to that web site.
I still have problem with the keyboard if typing rather fast.

---

