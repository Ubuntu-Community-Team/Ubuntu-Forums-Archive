---
title: "Digital Restrictions Management (DRM), unusable hardware, and license restrictions"
date: 2006-10-04
forum: System76 Support
---

### Post by DRM_free on 2006-10-04
I’m looking to buy a laptop whose hardware is DRM-free and supported by FOSS drivers. Have you considered selling such laptops?

Currently, all laptop and desktop computers being sold by System76 have a number of issues:

***** The embedded Intel 802.11 abg wireless card (which is automatically included in all your laptops) uses a closed-source binary blob that for all you know could be streaming the contents of your home directory to Intel corporate headquarters. 

***** Their Intel processors are crippled by DRM and TPM, whose sole purpose is to handcuff users and limit what they can do with their computers. Anyone who buys from Intel is subsidizing DRM development.

*****  The embedded Intel 802.11 abg wireless card forces users to download the firmware from the Intel website and to agree to a EULA. The license explicitly forbids distros from packaging the firmware, leading to a chicken-and-egg problem for users:  the only way to get the firmware is by downloading it, but if you only have a wireless connection you can’t download it because the wireless connection doesn’t work without the firmware.

***** The modems embedded in the laptops can’t be used in Linux because they are winmodems.

I’m literally willing to pay twice as much for a laptop (or desktop) that is made with open source-friendly hardware, such as:

***** A processor that is DRM-free -- this currently includes all AMD, Sun UltraSparc, and VIA processors.

***** An embedded 802.11 abg wireless card that is fully supported by FOSS drivers and that doesn’t need binary blobs. The Free Software Foundation says Ralink/RT wireless chipsets meet this criteria:

[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

***** An embedded modem that works with FOSS drivers in Linux.

***** A graphics card that can run Compiz or Beryl and that is supported by open source drivers. ATI Radeon 9600 through X850 cards (using the r300 open source driver) have been reported to run Compiz / AIGLX out of the box on Fedora 6. The Open Graphics project is also getting ready to release a 3D and OpenGL-capable card with completely open specifications and an internal design licensed under the GPL:

[http://OpenGraphics.org](http://OpenGraphics.org)

These are just some ideas for what you might want to include in your next-generation laptops and desktops. Selling computers that are truly FOSS-friendly will definitely help you stand out from all the other OEMs.

I realize that building a desktop with FOSS-friendly components is easier than building a laptop, and I’m sure such a desktop would also be very popular among Linux enthusiasts if it were marketed to showcase the fact that it is made up entirely of FOSS-friendly hardware.

---

### Post by skymt on 2006-10-04
I'd buy that. I'm in the market for a laptop, and I'd love to have the forward compatibility inherent in such an free/open design.

---

### Post by zachtib on 2006-10-05
> **DRM_free said:**
> I’m looking to buy a laptop whose hardware is DRM-free and supported by FOSS drivers. Have you considered selling such laptops?

Currently, all laptop and desktop computers being sold by System76 have a number of issues:

***** The embedded Intel 802.11 abg wireless card (which is automatically included in all your laptops) uses a closed-source binary blob that for all you know could be streaming the contents of your home directory to Intel corporate headquarters. 

***** Their Intel processors are crippled by DRM and TPM, whose sole purpose is to handcuff users and limit what they can do with their computers. Anyone who buys from Intel is subsidizing DRM development.

*****  The embedded Intel 802.11 abg wireless card forces users to download the firmware from the Intel website and to agree to a EULA. The license explicitly forbids distros from packaging the firmware,

***** The modems embedded in the laptops can’t be used in Linux because they are winmodems.


you sure about all of these?

DRM really requires software report to do anything, no?  I'm also pretty sure you can disable TPM in the BIOS.  Plus, I hate to break it to you, but AMD (i love them too, don't flame)  officially joined the "Trusted Computing" group a while ago. 

also, the ipw3945 driver is open source and provides linux support for the wifi card

and like it or not, Intel video cards provide the pest open source linux support, as intel recently open sourced their video card drivers

good luck finding any laptop with a modem that will work OOTB on linux, most modems are winmodems

---

### Post by DRM_free on 2006-10-05
> you can disable TPM in the BIOS.

For now, but it doesn't change that fact that you are paying for it and thus funding its development.

> AMD officially joined the "Trusted Computing" group a while ago.

But **all** of AMD's processors are DRM-free, so I have no objection to buying them.

> the ipw3945 driver is open source

The ipw3945 driver is useless without the binary userland blob, which prevents you from using your laptop in another country. Also, a userland daemon is in some ways more dangerous to privacy than an in-kernel binary driver because the userland blob has access to all the computer's resources (ie. filesystem). Not to mention that the artificial separation makes it slow and bloated.

> Intel video cards provide the best open source linux support 

If Intel sold stand-alone video cards with the same level of open source support, I'd be the first one to recommend them. However, the Intel graphics only work with Intel's DRM-crippled CPUs and binary blob wireless chipsets. What Intel is doing is selling sugar-coated poison (the sugar being the graphics and the poison being the DRM).

Theo de Raadt recently called Intel an **Open Source Fraud** for this very reason:
[http://bsd.slashdot.org/article.pl?sid=06/10/03/032259](http://bsd.slashdot.org/article.pl?sid=06/10/03/032259)

> good luck finding any laptop with a modem that will work OOTB on linux, most modems are winmodems

IBM released a completely GPL’ed driver (called mwave) for the 56K softmodem in Thinkpad 600E:
[http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/index.html](http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/index.html)
[http://sourceforge.net/projects/acpmodem/](http://sourceforge.net/projects/acpmodem/)

I’m sure there are other built-in modems with fully open-source drivers as well.
	
I'm not going to pay for something I can't use – all that does is send the wrong message to the hardware manufacturers (ie. that it's ok to make Windows-only hardware). I suggest offering laptop models without these softmodems if they don’t work.

---

### Post by zachtib on 2006-10-05
> **DRM_free said:**
> The ipw3945 driver is useless without the binary userland blob, which prevents you from using your laptop in another country. Also, a userland daemon is in some ways more dangerous to privacy than an in-kernel binary driver because the userland blob has access to all the computer's resources (ie. filesystem). Not to mention that the artificial separation makes it slow and bloated.

Hmm... I didn't know about the binary issue.

still, I think you're overreacting to some of these things, not trying to start a flame war here, just saying.

I think the best thing that could happen for Linux laptops right now is for AMD to partner with someone like say, Atheros, and release their Centrino-like platform, in the process opening the specs for ATI cards so that the radeon drivers can gain 3d support for the newer model cards.  hell, if they just opened the specs for their cards, they wouldn't even have to continue developing their fglrx driver.

---

### Post by jdong on 2006-10-11
I used to, but no longer recommend ralink/RT wireless cards. Sure, their drivers are completely open source, but they are crap to be honest. They disassociate and go into radio-off mode for no apparent reason, start resetting under heavy traffic, and worst of all cause kernel panics with SMP or preempt.

Combine that with a dual-core or HT processor, and you've got an unusable mess.

---

### Post by az on 2006-10-11
> **DRM_free said:**
> ***** An embedded 802.11 abg wireless card that is fully supported by FOSS drivers and that doesn’t need binary blobs. The Free Software Foundation says Ralink/RT wireless chipsets meet this criteria:

[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

***** An embedded modem that works with FOSS drivers in Linux.

***** A graphics card that can run Compiz or Beryl and that is supported by open source drivers. ATI Radeon 9600 through X850 cards (using the r300 open source driver) have been reported to run Compiz / AIGLX out of the box on Fedora 6. The Open Graphics project is also getting ready to release a 3D and OpenGL-capable card with completely open specifications and an internal design licensed under the GPL:

[http://OpenGraphics.org](http://OpenGraphics.org)



The Realtek wireless cards (818x) are also GPL friendly.  They seem to work just fine for me.

The intel i810 (955) graphics chipset also has GPLed drivers and they seem to work with the fancy desktop eye candy software.

---

### Post by jdong on 2006-10-11
Thanks for bringing up the rtl8180's. I've had MUCH MUCH better experiences with the rtl8180 series than any of Ralink's USB or PCI cards. Apart from one minor annoyance with automatic bitrate not working (i.e. if you're far away from your AP and need to scale down below 54Mbit to work reliably), it's been very smooth to me.

---

