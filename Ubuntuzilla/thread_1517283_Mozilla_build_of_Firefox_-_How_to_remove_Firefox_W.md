---
title: "Mozilla build of Firefox - How to remove Firefox Web Browser"
date: 2010-06-24
forum: Ubuntuzilla
---

### Post by nomnex on 2010-06-24
Hi,

First a big thanks to nanotube for this project (we got in touch through an email exchange). I have installed Mozilla build of Firefox today.

My questions:

[karmic 9.10 - FF 3.6.3 from the stable PPA - FF 3.6.4 from Ubutntuzilla]

a. I have already removed the PPA from my source list.  Can I also remove (is it advisable) the Firefox Ubuntu version from my sytem, and how to do it properly? When I select remove in synaptic, firefox-branding is also selected for removal, see: print-screen attached. 

b. What are the differences between the Firefox Ubuntu version, and the vanilla Mozilla build. Is it cosmetic only, or does it go to a deeper extend (in comparison the vanilla OOo form Oracle vs. the OOo with Novel patched, are quite different)

Thanks

---

### Post by nanotube on 2010-06-25
> **nomnex said:**
> 
First a big thanks to nanotube for this project (we got in touch through an email exchange). I have installed Mozilla build of Firefox today.

cheers! :)

> 
My questions:

[karmic 9.10 - FF 3.6.3 from the stable PPA - FF 3.6.4 from Ubutntuzilla]

a. I have already removed the PPA from my source list.  Can I also remove (is it advisable) the Firefox Ubuntu version from my sytem, and how to do it properly? When I select remove in synaptic, firefox-branding is also selected for removal, see: print-screen attached. 

unless you have really strong feelings about it... best to just leave it alone. it won't hurt anything.

> 
b. What are the differences between the Firefox Ubuntu version, and the vanilla Mozilla build. Is it cosmetic only, or does it go to a deeper extend (in comparison the vanilla OOo form Oracle vs. the OOo with Novel patched, are quite different)


i'm not really quite sure... some different build flags maybe... including possibly some font rendering libraries... all i know is that the mozilla build works fine :)

---

### Post by nomnex on 2010-06-25
> unless you have really strong feelingsI just want to know how to remove it, and if it creates conflict with the Ubunzilla version or not.

a. sudo apt-get autoremove

or

b. sudo apt-get purge

or

c. Else

and if I simply need to re-install the firefox-branding

If someone knows, thank you.

---

### Post by nanotube on 2010-06-25
just "sudo apt-get remove firefox" and let it take "firefox-branding" along with it.
you don't need it, if you uninstall the ubuntu-repos version of firefox, anyway.

---

### Post by nomnex on 2010-06-25
Thanks nanotube

---

