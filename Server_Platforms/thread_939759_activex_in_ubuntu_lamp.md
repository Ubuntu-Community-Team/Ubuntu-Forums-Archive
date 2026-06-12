---
title: "activex in ubuntu lamp???"
date: 2008-10-06
forum: Server Platforms
---

### Post by chriswebb18 on 2008-10-06
Is there any way to use active x controls on a ubuntu LAMP server?
i know activex is a microsoft thing, but does anyone know a workaround or something?  i want to use this menu on my web site([http://www.dynamicdrive.com/dynamicindex1/slashdot.htm](http://www.dynamicdrive.com/dynamicindex1/slashdot.htm)), but when i finished the site and confgured my web server, it works with firefox, opera, safari, but not ie.  i noticed that when i try to look at the menu in ie from the link above, it prompts me to enable activex controls... so i am not sure whether it needs active x or not, considering it works in firefox, safari, opera.  any ideas?

---

### Post by lykwydchykyn on 2008-10-06
Sounds like the problem is that this menu is coded in such a way to use ActiveX when it detects a windows/IE client, and due to security precautions you need to manually allow ActiveX in IE.  Other platforms or browsers use alternative technologies which are presumably safer than ActiveX, so they don't prompt you.  You just need to enable the activeX control client-side and it should work.

If it were me, I'd pick a different menu system that didn't require activeX.

---

### Post by chriswebb18 on 2008-10-06
yeah, im using something different for now, i just liked the look of that one.  i will try to sort through the code to see if i can make it work.  thanks

---

### Post by cariboo on 2008-10-06
If I remeber correctly most of Slashdot was written in Perl, why not just download [slashcode]("http://www.slashcode.com/faq.shtml#Slashcodecom5") and take what you need from there? It would be way easier and safer then trying to run active x on Apache.

Jim

---

### Post by chriswebb18 on 2008-10-06
wow thanks.

---

### Post by rovae on 2008-10-06
What an absolutely crazy year it was! But you look brilliant as always as [Naruto Cosplay](http://www.cosprops.com/cosplay-costumes-naruto-cosplay-c-14_15.html),maybe [Naruto Costumes](http://www.cosprops.com/cosplay-costumes-naruto-cosplay-c-14_15.html) oh yeah well thanks 4 telling me that, of cause, i should share my interesting [Naruto Cosplay Costumes](http://www.cosprops.com/cosplay-costumes-naruto-cosplay-c-14_15.html) [Foot Detox](http://www.cosprops.com/100-detox-foot-pad-patches-p-155.html)

---

