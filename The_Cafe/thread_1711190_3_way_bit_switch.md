---
title: "3 way bit switch"
date: 2011-03-21
forum: The Cafe
---

### Post by ki4jgt on 2011-03-21
OK, so the normal memory is 1 and 0. I know in the old days the numbers where about 8 or 9 different settings. But has anyone tried, just 3. I mean, technology has changed. We're no longer relying on vacuums and light bulbs. Could we not increase technology by going from a 01 system to a 012 system? Just asking.

---

### Post by NightwishFan on 2011-03-21
I believe you are talking about this:
[https://secure.wikimedia.org/wikipedia/en/wiki/Ternary_computer](https://secure.wikimedia.org/wikipedia/en/wiki/Ternary_computer)

Sounds interesting, though I am not worried about it at the moment.

---

### Post by LowSky on 2011-03-21
0 means off
1 means on
explain what two cold really mean?
the number only represents a open or closed circuit in its most basic sense.

---

### Post by NightwishFan on 2011-03-21
Try something like -1 0 +1. Some light based technology could recognise it. It might be useful for more precise math.

---

### Post by ki4jgt on 2011-03-21
Back in the day (When computers where first being expirimented with) it wasn't just on and off. It had anywhere from 5 - 8 settings. Each setting would make the light bulb just a little bit brighter [citation needed - read about this in HS] then someone had the bright idea of "Hey, on and off" This idea happened because of the quality of the mediums which kept up with weather a switch was on or off determining 8 levels of dimness was impossible [lights and vacuums]. Today, we not only have the technology to do this, but we no longer use the old technology. New switches would be 0 - completely off 1 - half way on 2 - all the way on. Modern computers would be able to know the difference.

My question is: would this speed things up, or benefit the computer world in any way?

---

### Post by ki4jgt on 2011-03-21
> **NightwishFan said:**
> I believe you are talking about this:
[https://secure.wikimedia.org/wikipedia/en/wiki/Ternary_computer](https://secure.wikimedia.org/wikipedia/en/wiki/Ternary_computer)

Sounds interesting, though I am not worried about it at the moment.

Exactly what I meant.

---

### Post by Cracklepop on 2011-03-21
> **LowSky said:**
> 0 means off
1 means on
explain what two cold really mean?
the number only represents a open or closed circuit in its most basic sense.

No, actually:
off means 0,
on means 1.

---

### Post by koenn on 2011-03-21
> **LowSky said:**
> 0 means off
1 means on
explain what two cold really mean?

unknown, undetermined, not yet initialized, ....
& see also below

> **NightwishFan said:**
> Try something like -1 0 +1. Some light based technology could recognise it.
not just light.
Some signalling technology uses multiple voltage levels, or even transitions from one level to another, to represent multiple "bits".

---

### Post by mcduck on 2011-03-21
On the other hand we are already having troubles with the binary machines and the way how higher operating frequencies would require higher voltages to reliably make a difference between a 0 and a 1.

At hardware level things aren't actually binary but analogic, the voltage doesn't immediately switch from 0 to 0.5V, for example, it gos through all the values in between.  Try switching between the values quick enough, and the voltage will never have time to fully reach the value that would be a 0 or a 1. Increasing the difference of voltage that defines the values helps, but on the other hand increases power usage and heat generation. Which is one of the main things limiting the clock frequencies on current computers. Trying to add more values than just the extreme ends (0 and 1) would make this problem even worse.

So it's definitely not quite as simple as "more numbers = faster". At least if you expect it to work using technology anything like what the computers are currently based on. Actually getting rid of the in-between values by improving the response time of the components and reducing the time it takes them to switch between different voltages might be the better way. At least this far that route has worked a lot better...

---

### Post by lz1dsb on 2011-03-21
The digital modulations (QPSK, different types of QAMs, etc.) have been using multiple voltage (amplitude) and phase levels to represent more than one bit of information in a modulated symbol. But still the logic is binary though. It's only optimized for data transmission...

---

### Post by Paqman on 2011-03-21
Quantum computers sort of do this, don't they?

---

### Post by 3Miro on 2011-03-21
This reminds me of an old speech by a famous politician: "This year we are opening a factory for semi-conductors, next year we will work towards full conductors". lz1dsb knows what I am talking about.

From mathematical point of view (which includes writing code) binary and ternary are identical. From hardware point of view, this makes a difference, but it is not as clear as: more values -> more power.

Take analog signal for example, theoretically it can take infinitely many values, however, it is clear that digital (i.e. finite) devices are more reliable (tape vs CD for example). There have been analog computers in the past, however, those don't hold against the binary machines. Unless we see a major change in architecture (like going from transistors to something else), then there would not be any real advantage of going ternary.

The wiki article about ternary machines gives optics as an example of how we can benefit from ternary. However, optical computers are still sci-fi material. Fiber optics is here, but even if fiber optics goes to ternary signal, this would not be anything new. Binary computers have been using non-binary ways of communication in the past (coaxial token ring network for example).

---

### Post by ki4jgt on 2011-03-21
Well, I wasn't suggesting analog by far it would have to be horrible in a computer. (I want to see a truly analog computer - Looking it up) But from a 2 base to 3 base which is still digital.

---

### Post by 3Miro on 2011-03-21
[http://www.youtube.com/watch?v=xISG4nGTQYE](http://www.youtube.com/watch?v=xISG4nGTQYE)

on/off is easy to detect by transistors. If you want to measure the voltage power or something else to make a third state, you will have to change the hardware. Transistor based computers cannot efficiently work with anything other than binary.

---

### Post by forrestcupp on 2011-03-21
We already kind of do this in a way by using strings of bits. One example is in pixel colors and effects. Each pixel is either on or off, then we have a string of bits that represent the varying levels of RGB and transparency values. All of that data is information for one pixel bit that is either on or off. In the Commodore days, we had 4-bit color depth which gave us 16 colors. Now we just use longer strings of bits, which gives us millions of colors.

You're basically talking about the same thing we already do with bytes and words. I don't think it would actually add anything that we can't already do to make bits multilevel.

---

