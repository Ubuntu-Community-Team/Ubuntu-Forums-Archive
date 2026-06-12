---
title: "Star1 Wireless Card"
date: 2010-12-31
forum: System76 Support
---

### Post by macabrem on 2010-12-31
Is the Starling Star1 wireless card an rtl8187, or an 8187b, or something else?

Is there a terminal command to run to see what card is installed?

Has anybody successfully fixed the Star1 short range wireless issues with other OS's without installing a new card?  Particularly, I'm running the new Crunchbang based on Debian, so if anybody has successfully fixed the card on a Debian based distro, let me know.  

I wasn't sure if it is a matter of just downloading a driver from somewhere since this issue is fairly old now?  

Thanks for any help.

---

### Post by jml on 2011-01-02
Ordinarily, typing the command "lspci" (without the quotation marks,) would bring up the card.  But on my STAR1, it does not come up.  I used the search function on this sub-forum and found this link:

[http://ubuntuforums.org/showthread.php?t=1275262&highlight=wireless+chipset](http://ubuntuforums.org/showthread.php?t=1275262&highlight=wireless+chipset)

It confirms that the STAR1 uses the Realtec RTL8187B wireless card.  I have tried to run several other Linux distros on my Starling and results vary from the wireless card not being recognized to everything being recognized.  Debian Testing (Squeeze) recognizes the card, but it has the same poor performance issues it had with Ubuntu prior to the patches created by System 76.  The only way I have been able to get acceptable performance out of this card is to run Ubuntu (I use 10.04,) and then install the custom drivers from System 76.  They only work with Ubuntu and no other distro.

Prior to this fix, I actually bought an inexpensive USB wireless device manufactured by Belkin and used that until I was able to get the internal card working.

Joe

---

### Post by macabrem on 2011-01-03
> **jml said:**
> Ordinarily, typing the command "lspci" (without the quotation marks,) would bring up the card.  But on my STAR1, it does not come up.  I used the search function on this sub-forum and found this link:

[http://ubuntuforums.org/showthread.php?t=1275262&highlight=wireless+chipset](http://ubuntuforums.org/showthread.php?t=1275262&highlight=wireless+chipset)

It confirms that the STAR1 uses the Realtec RTL8187B wireless card.  I have tried to run several other Linux distros on my Starling and results vary from the wireless card not being recognized to everything being recognized.  Debian Testing (Squeeze) recognizes the card, but it has the same poor performance issues it had with Ubuntu prior to the patches created by System 76.  The only way I have been able to get acceptable performance out of this card is to run Ubuntu (I use 10.04,) and then install the custom drivers from System 76.  They only work with Ubuntu and no other distro.

Prior to this fix, I actually bought an inexpensive USB wireless device manufactured by Belkin and used that until I was able to get the internal card working.

Joe

Thanks for the reply.  I was having problems getting any command to recognize the card, so I'm glad it wasn't just me.

I was debating getting a USB wireless device.  I thought I would exhaust other options before spending the money.  I was hoping somebody tore apart the System 76 driver and rewrote it for Debian.  

Thanks again.

---

