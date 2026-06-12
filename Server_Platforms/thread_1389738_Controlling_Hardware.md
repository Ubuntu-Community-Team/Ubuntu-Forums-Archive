---
title: "Controlling Hardware"
date: 2010-01-24
forum: Server Platforms
---

### Post by Hozza on 2010-01-24
I have been a website designer for sometime now and i was wondering about tring out some of the hardware world. (dont get me wrong im no n00b, i can build a pc from scratch)

What is the best way to get started on Controlling Hardware? i mean controling a small electric motor to spin a wheel when a button is pressed on the computer or somthing like that?

And can this be done with PHP so i wont have to worry about leaning another programming language?

Is it very difficalt? Where should i start?

---

### Post by Xianath on 2010-01-25
Putting a PC together from scratch and using it as a controller are two quite different aspects of hardware aptitude. What you're describing is perfectly possible but requires a fair bit of hardware work as well as software. Also, depending on the scope of what you want to do, PHP won't cut it, nor would the stock kernel. Have a look at [http://linuxcnc.org/](http://linuxcnc.org/) for a taste of what's involved.

Cheers,
Peter

---

### Post by Lars Noodén on 2010-01-25
> **Hozza said:**
> I have been a website designer for sometime now and i was wondering about tring out some of the hardware world. (dont get me wrong im no n00b, i can build a pc from scratch)

What is the best way to get started on Controlling Hardware? i mean controling a small electric motor to spin a wheel when a button is pressed on the computer or somthing like that?

And can this be done with PHP so i wont have to worry about leaning another programming language?

Is it very difficalt? Where should i start?


It's not difficult, but there are so many possible hardware setups and ways to do that, it can be confusing if not overwhelming.  

Usually you want to work with some kind of digital input/output and that is dependent on what hardware you have.  Try looking at [Linux For Devices](http://www.linuxfordevices.com/) for an idea of possible hardware.  Often, turning these I/O devices on or off can be done using **gpio** or General Purpose Input Output.

I had a box with +3.3 V DC output and used a 3.3 V LED to see when a particular I/O pin was on or off before getting a more complicated hardware set up.

---

