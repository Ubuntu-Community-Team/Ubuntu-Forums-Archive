---
title: "An open source system can open windows programs and Definitions devices"
date: 2007-07-02
forum: The Cafe
---

### Post by hello_syria on 2007-07-02
:biggrin: 
Hello to all !!! i dont know if pepole know this system or not 
the system name ReactOS the sysytem site [www.reactos.org](www.reactos.org)
but the aske can linux open the windows program in some day

---

### Post by t3r0 on 2007-07-02
Linux & others [can already]("http://www.winehq.org/") run most of the windows programs... :)

---

### Post by GMU_DodgyHodgy on 2007-07-02
Sooooo - They reversed engineered Windows into a "new" operating system. 

Did they bother to reverse engineer the bloat and security holes as well?

---

### Post by Xzallion on 2007-07-02
> **GMU_DodgyHodgy said:**
> Sooooo - They reversed engineered Windows into a "new" operating system. 

Did they bother to reverse engineer the bloat and security holes as well?

As much as we all like to make the occasional joke about Windows bloat and security practices, maybe we should give this project a little more credit.  They are trying to create an open source, clean room reverse engineered operating system completely compatible with all Microsoft Windows XP programs and drivers.  I honestly want them to succeed so I can play my games in a open source OS, and can finally ditch Windows.

---

### Post by init1 on 2007-07-02
> **hello_syria said:**
> :biggrin: 
Hello to all !!! i dont know if pepole know this system or not 
the system name ReactOS the sysytem site [www.reactos.org](www.reactos.org)
but the aske can linux open the windows program in some day
Reactos doesn't work on my computer. Neither the live CD or the installer. I have to use qemu.

---

### Post by GMU_DodgyHodgy on 2007-07-02
> **Xzallion said:**
> As much as we all like to make the occasional joke about Windows bloat and security practices, maybe we should give this project a little more credit.  They are trying to create an open source, clean room reverse engineered operating system completely compatible with all Microsoft Windows XP programs and drivers.  I honestly want them to succeed so I can play my games in a open source OS, and can finally ditch Windows.

I did not mean to dump on the overall effort - however, when reverse engineering - I hope they don't recreate some of the architectural pitfalls MS has in their current offerings.  

It would be interesting to see if they could help WINE complete their compatibility layer so Windows programs could more reliably run on Linux.

---

### Post by forrestcupp on 2007-07-02
> **GMU_DodgyHodgy said:**
> I did not mean to dump on the overall effort - however, when reverse engineering - I hope they don't recreate some of the architectural pitfalls MS has in their current offerings.  

It would be interesting to see if they could help WINE complete their compatibility layer so Windows programs could more reliably run on Linux.

They work closely with wine and I believe they contribute to wine.  It is a totally different environment, though, so what they can contribute is limited.  Even though they say it's not, wine is kind of like an emulator that runs in a different environment where ReactOS is a complete operating system.

I really don't think ReactOS is anywhere near close enough to be dependable as a usable OS, though.

---

### Post by K3ITHK on 2007-07-02
In one of the screenshots they have Adobe Photoshop 3.0. lol

---

### Post by Adamant1988 on 2007-07-02
> **forrestcupp said:**
> They work closely with wine and I believe they contribute to wine.  It is a totally different environment, though, so what they can contribute is limited.  Even though they say it's not, wine is kind of like an emulator that runs in a different environment where ReactOS is a complete operating system.

I really don't think ReactOS is anywhere near close enough to be dependable as a usable OS, though.

Do you even know what WINE stands for? 

**W**ine **I**s **N**ot an **E**mulator

It's a compatibility layer, which is why running programs through WINE/Crossover/Cedega produces no major performance losses.

---

### Post by Dr. C on 2007-07-02
It is no different from what GNU set out to do in the mid 80"s. Create a Free operating system compatible with propriety Unix, and it will end up being a better Windows than Windows just like Gnu / Linux has become a better Unix than Unix. It will take some time ReactOS is still in alpha.

---

### Post by forrestcupp on 2007-07-02
> **Adamant1988 said:**
> Do you even know what WINE stands for? 

**W**ine **I**s **N**ot an **E**mulator

It's a compatibility layer, which is why running programs through WINE/Crossover/Cedega produces no major performance losses.

Yes, that's why I said "they say it's not an emulator."  To me it's pretty much the same thing.  It's just a technical way of making it appear that they are better than an emulator.  If you think there's no performance loss, you're not very perceptive.  I notice visible performance loss on fairly simple apps.

Gnu's not Unix, WINE is not an emulator, LAME is not mp3, who cares?

---

### Post by M$LOL on 2007-07-02
ReactOS is nowhere near ready to be used...

---

### Post by Adamant1988 on 2007-07-02
> **forrestcupp said:**
> Yes, that's why I said "they say it's not an emulator."  To me it's pretty much the same thing.  It's just a technical way of making it appear that they are better than an emulator.  If you think there's no performance loss, you're not very perceptive.  I notice visible performance loss on fairly simple apps.

Gnu's not Unix, WINE is not an emulator, LAME is not mp3, who cares?

I was able to run photoshop 7 in WINE with no major performance losses, but then again I have a fairly powerful computer...

---

### Post by Caedis on 2007-07-03
> **forrestcupp said:**
> Yes, that's why I said "they say it's not an emulator."  To me it's pretty much the same thing.  It's just a technical way of making it appear that they are better than an emulator.  If you think there's no performance loss, you're not very perceptive.  I notice visible performance loss on fairly simple apps.

Gnu's not Unix, WINE is not an emulator, LAME is not mp3, who cares?

I agree to some degree. Don't Get me wrong, I LOVE WINE, but if your computer is not as powerful as it should, you certainly cant run very powerful apps without significant performance loss.

Case in point,  I CAN run my copy of Photoshop CS2 on my laptop, very quickly in fact... BUT thats only under windows, when I boot into Linux and run CS2 under WINE, it takes 5 minutes to load, and once it loads I can use every file type except Photoshop format files.

So to say that WINE has no appreciable performance loss is a gross exaggeration if not bordering on a tall tale.

---

