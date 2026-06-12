---
title: "Installing System76 Driver on a fresh install of UNR 9.10..."
date: 2010-02-10
forum: System76 Support
---

### Post by vttay03 on 2010-02-10
I finally decided to bite the bullet and wiped my Starling clean of UNR 9.04 and do a fresh install of UNR 9.10.  Everything went smoothly until I tried to get the System76 driver up and running.  I've followed the below instructions...

> 
If you've done a fresh install of Ubuntu 9.10...

First, run all System updates before running the System76 Driver.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.


Now, I did install the 2.4.5 version instead of the 2.4.4 thinking the driver had since been updated.  After installing the .deb package, I open the System76 Driver application and click 'Restore' as indicated.  Most of the time it tells me I have no active internet connection (although I'm connected via a wired connection).  I have gotten it to run once by removing the wired connection and plugging it back in.  When I finally did get it to run, it just ran forever and I finally had to exit out.  I've read some posts about possibly needing to install grub-pc.  Why would this affect it?  One other note is that I forced a downgrade on one package after the fresh install b/c of unnecessary terminal outputs.  This package is libglib2.0-0.  Any hints or suggestions are appreciated...

---

### Post by vttay03 on 2010-02-10
UPDATE : I was able to click 'Install' instead of 'Restore' and it seemed to install properly.  After I rebooted, wireless was functional (and quite a bit better than in 9.04 I might add).  What are the consequences of not allowing 'Restore' to run correctly?  I checked the software sources and it seems as if the System76 repository was correctly added.  What could have caused 'Restore' to hang like that?

---

### Post by thomasaaron on 2010-02-10
If you did a fresh install of 9.10, you should already have grub2 installed (which is the purpose of grub-pc).

Try running...

system76-driver

...from a terminal. Let's see if it gives us some output in the terminal that would indicate why it is hanging.

I'm not sure why you would want to force a downgrade on that package. That's *typically* not a good idea for the average user. But I don't *think* it has anything to do with the driver.

---

### Post by vttay03 on 2010-02-10
I think I posted a bit prematurely...like I said above after clicking 'Install' it appeared to run correctly.  So following your advice, I launched it from the terminal and ran 'Restore' again.  This time, nothing seemed to hang and everything went smoothly.  I have wireless again and UNR 9.10 seems to be quite a bit snappier than UNR 9.04.  Thanks for the driver fix!  One other question...why are one of the steps listed on the 'Restore' tab as Install the GNUCash Accouting Software?  What does this have to do with the System76 driver?

---

### Post by thomasaaron on 2010-02-11
We had stopped installing extra software sometime ago. But it looks like gnucash is back by popular demand!

If you don't want it, you can delete it via Applications > Ubuntu Software Center.

---

