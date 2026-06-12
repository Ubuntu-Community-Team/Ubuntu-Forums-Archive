---
title: "Ubuntu &amp; ease of use for first time wireless"
date: 2007-07-23
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2007-07-23
I've spent two weeks doing and undoing ndiswrapper stuff. It was on the computer so I could help a friend set up Ubuntu on his computer.

Now I can't make my wireless card work.

Multiple posts about this to Ubuntu's Wireless (and Networking) forum have brought useless or no results. Upwards of 70 people looked at one post and nearly 60 at another. The one response was completely useless. The responder simply knows nowhere near enough to respond to my problem(s). Thank you, although.

Ubuntu's devoleper's must make the wireless process more transparent to the end user, and as much as I truly hate to say this, it should be like MS as much as there is a way too graphically find and check the status of drivers. 

No! to:

lsmod
depmod
dmesg | grep

and other arcane commands, that while the development of Ubuntu continues to where it is meaningfully user friendly in this area, the end user must follow instructions that MAY or MAY NOT be helpful and could be possibly harmful.

---

### Post by kidders on 2007-07-24
Hi there,

Forcing Linux to use drivers designed for another operating system isn't something a user can expect to be able to do without a certain amount of background knowledge, and should always be undertaken with care. I'm not sure how easy one can expect it to be.

---

### Post by init1 on 2007-07-24
> **Mark_in_Hollywood said:**
> I've spent two weeks doing and undoing ndiswrapper stuff. It was on the computer so I could help a friend set up Ubuntu on his computer.

Now I can't make my wireless card work.

Multiple posts about this to Ubuntu's Wireless (and Networking) forum have brought useless or no results. Upwards of 70 people looked at one post and nearly 60 at another. The one response was completely useless. The responder simply knows nowhere near enough to respond to my problem(s). Thank you, although.

Ubuntu's devoleper's must make the wireless process more transparent to the end user, and as much as I truly hate to say this, it should be like MS as much as there is a way too graphically find and check the status of drivers. 

No! to:

lsmod
depmod
dmesg | grep

and other arcane commands, that while the development of Ubuntu continues to where it is meaningfully user friendly in this area, the end user must follow instructions that MAY or MAY NOT be helpful and could be possibly harmful.
I can't do it either. That's why I use Mepis for my wireless needs.

---

### Post by mrgnash on 2007-07-24
It's difficult, especially when you're using an Acer laptop like mine, which has all sorts of quirks to it with regard to switching the WiFi card on. Now my sister has the **exact same** card (the notorious BCM4318) in her Aspire 3000, and it took all of 5 minutes to get it up and running in PCLOS2007. Mightily impressed by this, I installed PCLOS2007 on my laptop as well -- 6 hours of frustration later, without any progress, and I was back to Ubuntu like a bat out of hell. At least with Ubuntu, I could actually ```
make
``` something (namely the Acer ACPI module), and get the card to switch on at least -- albeit, after a very convoluted process, during which numerous hiccups were encountered. This wasn't the case with PCLOS2007, which I found fronts you with the dilemma so familiar to Windows users; namely, if it 'just works', then wonderful, you're set -- but if it doesn't, you're screwed. Now I know that I could have probably installed the relevant tools to compile and so forth, and I did try, but the repositories for that distro are so screwed up that all this did was begin to brew a fresh new nightmare. 

In short, if you wireless somewhat difficult in ole 'bunty, then try another distro -- you may be pleasantly surprised -- but, on the other hand, you can probably knuckle through it if you search for the relevant how-tos and whatnot, and then you'll also have the advantage of knowing how it all works a little better.

---

### Post by jeyaganesh on 2007-07-24
Actually, lot of people starting to use linux nowadays like me and this thread creater. We have been using windows for years, now we came to linux for new and alternative experience. As we dont have any programming skills like foremost generation of linux users, we have to do lot of search and read loads of forums to make our device work. I used to find almost all solution in ubuntu forum. Currently I am also looking for integrating my belkin wireless adaptor with ubuntu. Hope I will find some solution soon.:guitar:

---

