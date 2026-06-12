---
title: "I paid 30 dollars and all I got was &quot;wow, I'm an idiot.&quot;"
date: 2008-10-16
forum: The Cafe
---

### Post by Roasted on 2008-10-16
I paid 30 bucks and got an 8gb flash drive on NewEgg.

3 weeks later (last night), I was helping my buddy build his computer. He got a triple core AMD system, 2gb ram, blah blah... 

So I was helping him hook up some stuff and we all got done. System booted up, XP installed first, etc. 

So then I plug in my flash drive cause, since I work at a school and I have to manage a couple hundred computers, I keep a lot of things on my flash drive... Flash 9, Reader 9, Java, quicktime, vlc, IE6, IE7, Firefox, etc... so, my flash drive doesn't respond. Oh no? Plug it in the back of the motherboard. No response. I touched the metal of the flash drive and the sucker was pretty darn hot.

So then I tried a spare 1gb flash drive I had laying around. Same deal, except it never got hot. It was just simply... non responsive.

So I bust open the case to find out his front USB ports I accidentally hooked up to the firewire connection on the board. The firewire connection and USB connections both had the same number of pins. I just didn't read the 1394 above one and JUSB above the other. Duuuur.

So now I have 2 dead flash drives. But luckily, I have this folder. It's kind of neato. It's in my home directory and labeled "FlashDriveBackup." Needless to say, there's 2.6gb of data in there... and I have a 4gb spare flash drive... so I'm back in business!!


Question, though... do you think I could have damaged his motherboard by doing that? Or was the worst that could have happened simply the flash drives getting fried?

---

### Post by Canis familiaris on 2008-10-16
It is indeed possible that the Motherboard has been affected too. I believe that the Firewire might not work now.

---

### Post by damis648 on 2008-10-16
> **Anurag_panda said:**
> It is indeed possible that the Motherboard has been affected too. I believe that the Firewire might not work now.

I would say that too... plug something in there (that won't kill you if it fries!) and see if it works.

---

### Post by cookieofdoom on 2008-10-16
> **damis648 said:**
> I would say that too... plug something in there (that won't kill you if it fries!) and see if it works.

Yeah, I wouldn't plug in a $300 digital video camera.:lolflag:

---

### Post by damis648 on 2008-10-16
> **cookieofdoom said:**
> Yeah, I wouldn't plug in a $300 digital video camera.:lolflag:

Ha, please don't. :-P

---

### Post by Roasted on 2008-10-16
We don't have any firewire devices to even test it with. That's why I'm curious...

I wasn't sure if the firewire controller would still retain itself and just push power through the wires regardless, and the devices on the end just being the ones that get fried if they are not of the right standard (aka, the usb flash drives).

Kind of sucks, cause it's brand new, and I'm stupid for not checking... but the rest of the board seems to function fine and there's no problems with it at all.

I wonder if there's something in BIOS to check the integrity of controllers, such as firewire? I'm just curious to know if it works...

---

### Post by Octagonal on 2008-10-16
I would find it highly unlikely that anything with the firewire port is damaged.  I could understand the usb drives being affected as power is coming from the motherboard to the usb device--but you wouldn't have power coming from the usb device to the motherboard with a usb thumbdrive.
I'd probably bet my life that the firewire port is fine.

---

### Post by forrestcupp on 2008-10-16
> **Octagonal said:**
> I would find it highly unlikely that anything with the firewire port is damaged.  I could understand the usb drives being affected as power is coming from the motherboard to the usb device--but you wouldn't have power coming from the usb device to the motherboard with a usb thumbdrive.
I'd probably bet my life that the firewire port is fine.

That's kind of what I was thinking.  Unless the jump drive shorted the circuit and sent the power back to the motherboard through the wrong pin.  I think it might be ok, but I wouldn't bet my life on it.

---

### Post by Roasted on 2008-10-16
Well, what about my flash drive heating up like that? Remember, the 8gb one gets hot, while 1gb one does not... however both are dead.

Note - the 8gb one gets hot no matter where I plug it into. I've plugged it into completely different computers, Ubuntu and XP, and the thing gets hot either way. So I'm wondering if something within the USB flash drive (the 8gb one) got damaged to the point where it gets scorching hot, whereas the 1gb one just went... POP. Done.

---

### Post by pp. on 2008-10-16
> **Octagonal said:**
> I could understand the usb drives being affected as power is coming from the motherboard to the usb device--but you wouldn't have power coming from the usb device to the motherboard with a usb thumbdrive.
I'd probably bet my life that the firewire port is fine.

I wouldn't underwrite you insurance.

Since one of the USB sticks became hot, we know that there was a current flowing, possibly more than what the Firewire interface could sustain. 

There's a perceptible chance that something burned out in the firewire interface or even somewhere else on the motherboard, albeit it's not very likely.

---

### Post by Roasted on 2008-10-16
My 8gb flash drive is also significantly different from all other ones I used. It's insulated with a bunch of soft rubber to make it shock resistant and drop resistant and all kinds of other garbage. 

But I don't think it'd be a stretch to say that it's simply the flash drive that's blown. Think about it. It reacts the same way in multiple computers. The power is getting pushed FROM the motherboard out of the USB ports and to the flash drive... so if a circuit blew within the flash drive, I don't think it's far fetched to consider that maybe it's just that device which is malfunctioning resulting in the fact it heats up... whereas the 1gb kingston I had simply went BOOP gone. Wiped. Over. *shrug*

I just hope everything's okay with it. Also, there's 2 firewire ports on the back of the motherboard along with all of the other ports and whatnot. Is it likely that those 2 ports are wired to the firewire pin connector on the mobo??

EDIT - USB being more power than the firewire could sustain?

Firewire draws 30v
USB 2.0 draws 3v

---

### Post by pp. on 2008-10-16
> **Roasted said:**
> 
EDIT - USB being more power than the firewire could sustain?

Firewire draws 30v
USB 2.0 draws 3v

It's current we're concerned with here, not primarily voltage. The unit called 'V' (Volts) measures the voltage, while the current is measured in 'ampères' ('A'). It's most certainly not correct to say that USB 'draws' some voltage.

I do not know the number of pins involved in USB and Firewire connectors. Even if the number is as low as two, additional complications can exist because of connecting the wrong wires to the wrong pins. Hence, you could cause a current to flow where there shouldn't or apply an inverse voltage.

---

### Post by Roasted on 2008-10-16
> **pp. said:**
> It's current we're concerned with here, not primarily voltage. The unit called 'V' (Volts) measures the voltage, while the current is measured in 'ampères' ('A'). It's most certainly not correct to say that USB 'draws' some voltage.

I do not know the number of pins involved in USB and Firewire connectors. Even if the number is as low as two, additional complications can exist because of connecting the wrong wires to the wrong pins. Hence, you could cause a current to flow where there shouldn't or apply an inverse voltage.

They're the same. That's how I goofed it up in the first place. It was 2 rows of pins... 4 in the top row, 5 in the bottom.

---

