---
title: "Very curious question"
date: 2011-12-19
forum: The Cafe
---

### Post by AlexTolic on 2011-12-19
Not sure if this is a good spot to put this but ive run out of options 

My question is...

Is it not possible to store data in radio waves but keeping them in a close location but another and possibly a third piece of hardware to keep the waves bouncing or just floating in an accessible place

I dont really know much about radio waves and transmission and i cant think of a place for the data to be stored if and in case of a power failure but it was just a lazy day and i had a lazy idea.

Dont make fun of me too hard

---

### Post by Buntumatic on 2011-12-19
> **AlexTolic said:**
> Is it not possible to store data in radio waves but keeping them in a close location but another and possibly a third piece of hardware to keep the waves bouncing or just floating in an accessible place 

:shock: OoO ... I'm a radio engineer and computer expert but I have no clue what you just said. Must be way above my head ...

---

### Post by AlexTolic on 2011-12-19
Haha sorry about that i am neither of those things just a crazy idea ill try to explain again.

I dont know its easier to explain in person i guess haha. Just imagine i suppose 2 (or more) radio transmitters and receivers
sending out data and then just keeping it in almost a dome? of radio waves making it so the data cant leave? 

I dont know this is really hard to explain.

HERE instead do this: I want to store data in radio waves. How can i do this good sir?

you answer lol

---

### Post by lisati on 2011-12-19
*Thread moved to **The Community Cafe**.*

---

### Post by Paqman on 2011-12-20
> **AlexTolic said:**
> I want to store data in radio waves.

No reason you couldn't do this, it would be incredibly impractical though. The question is: why would you want to?

---

### Post by crazy bird on 2011-12-20
For what i understand you want described a situation in which you work with transmitters/receivers and want data to be send/received bewteen these transmitters/receivers? 
 
I'm not a radio-engineer, but i guess this should be possible. Although i'm afraid that there migth be a signal loss after a period or interference in this (radio) signal from other sources which weaken the signal you suggest. If this can be done in a enclosed environment in which it is alomst impossible to have interfering signals from others sources, then it could work. But it looks very complicated and technically difficult.

---

### Post by detroit/zero on 2011-12-20
[SIZE=4]_**Long Answer:**_[/SIZE]

In theory, if you had a resonant cavity, your transmitter(s)/receiver(s) operated at that resonant frequency, you could set up what is referred to as a standing wave. Once standing waves are established, the energy input to keep them standing is considerably less than what is required to create them from nothing.

If this standing wave could be created, you could use it as your carrier. Since it is a standing wave resonating at the frequency of (and only because of) the cavity it's in, your modulation (the information you propose to store) would have to be an Nth harmonic of the carrier/resonant frequency. Again, in theory, those waves would also stand in the cavity, with minimal energy input required to maintain them.

Unfortunately, all the waves - carrier and modulation - would be standing; that is, not really moving. All the information you propose to "store" would have to be modulated on a single carrier.

If Nikola Tesla's patents and theories hold true (and since, to this day, his resonant air-core transformer is at the heart of most modern radio equipment), you could use the earth itself as your resonant cavity. This cavity is known to resonate at or around 8Hz. At a usable Nth harmonic suitable for purposes such as this, your modulated "data" would have to run at multiples of eight, depending how much data you needed to "store".

If, for example, you only needed to store two conditions, be they on/off or yes/no or whatever, your modulated signal would only need to be 16Hz. If you needed to meet the conditions of a more complex logic statement with, say 8 conditions, it would need to be running at 64Hz. If you wanted to encode a relatively secure password consisting of one capital letter, seven small letters, two numbers, and one symbol in plain ASCII format, you modulation would end up having to run in the high kilohertz to low megahertz range. If you wanted to encode the text of this message in plain ASCII format, you would likely need terahertz-range frequencies that current technology available to the average consumer can not yet reliable create (always in a harmonic of eight, remember).

[SIZE=4]_**TL;DR:**_[/SIZE]

No.

Buntumatic, as an expert in the field, please correct me if I'm wrong - keeping in mind that I've kept everything in layman's terms and stepped things down a notch for the uninitiated.

---

### Post by 3rdalbum on 2011-12-20
> **AlexTolic said:**
> Not sure if this is a good spot to put this but ive run out of options 

My question is...

Is it not possible to store data in radio waves but keeping them in a close location but another and possibly a third piece of hardware to keep the waves bouncing or just floating in an accessible place

I dont really know much about radio waves and transmission and i cant think of a place for the data to be stored if and in case of a power failure but it was just a lazy day and i had a lazy idea.

Dont make fun of me too hard

I laughed when I read your idea. Not because it's a bad idea, or a silly idea; it's not. I laughed because it's a great idea I had never thought of before.

Unfortunately, it won't work for any practical purpose. But it's a cool idea and it would be awesome if it could be made to work, which it can't :-)

---

### Post by TheNessus on 2011-12-20
i figure it could work with very distant radio transmitters-recievers. that is, light years apart.

they only need to transmit once, and the one at the other end will only to need to receive once, in a time frame of years. then when the receiver receives it, it will transmit it back, taking again years for the signal to reach the first device. and so on and so forth. 

But that would require a storage of some kind like RAM, where the received information is stored momentarily before being analyzed and transmitted back. 


- a less sophisticated post than previous ones.

---

### Post by grahammechanical on 2011-12-20
Surely, we already have data stored in radio waves. How else do you explain radio and television? The data that we listen to on our radios and the data we watch and listen to on our televisions must surely be stored in the radiated energy being transmitted. The data is carried on a carrier wave of energy. It must be a form of storage.

Regards.

---

### Post by forrestcupp on 2011-12-20
The only problem is that the hardware transmitting/receiving/and transmitting again would have to have enough local storage space to store the data before it could transmit it again. So if you're already storing it in local storage, what would be the point in continually transmitting it, too?

---

### Post by lisati on 2011-12-20
> **forrestcupp said:**
> The only problem is that the hardware transmitting/receiving/and transmitting again would have to have enough local storage space to store the data before it could transmit it again. So if you're already storing it in local storage, what would be the point in continually transmitting it, too?

I'm wondering if some kind of repeater would have the same requirements for data storage. I suspect that the answer would depend in part on what kind of error correction you'd need to put in place.

---

### Post by koenn on 2011-12-20
> **lisati said:**
> I'm wondering if some kind of repeater would have the same requirements for data storage. 

it probably wouldn't. You'd just need a buffer to 'store' only the data you've received but haven't transmitted yet

> **lisati said:**
> 
I suspect that the answer would depend in part on what kind of error correction you'd need to put in place.

that's processing, not so much storage/buffering

---

### Post by ofnuts on 2011-12-20
> **AlexTolic said:**
> Not sure if this is a good spot to put this but ive run out of options 

My question is...

Is it not possible to store data in radio waves but keeping them in a close location but another and possibly a third piece of hardware to keep the waves bouncing or just floating in an accessible place

I dont really know much about radio waves and transmission and i cant think of a place for the data to be stored if and in case of a power failure but it was just a lazy day and i had a lazy idea.

Dont make fun of me too hard
See [http://en.wikipedia.org/wiki/Delay_line_memory](http://en.wikipedia.org/wiki/Delay_line_memory)

IIRC Arthur Clarke suggested to use three geostationary satellites beaming data at each other as a gigantic storage (*) . Of course the capacities you could achieve looked gigantic at the time (tens of megabytes...), but that was before the invention of the mp3 and the mpeg files...

---

### Post by forrestcupp on 2011-12-21
> **ofnuts said:**
> See [http://en.wikipedia.org/wiki/Delay_line_memory](http://en.wikipedia.org/wiki/Delay_line_memory)

IIRC Arthur Clarke suggested to use three geostationary satellites beaming data at each other as a gigantic storage (*) . Of course the capacities you could achieve looked gigantic at the time (tens of megabytes...), but that was before the invention of the mp3 and the mpeg files...

Wow. That would be a way more efficient and inexpensive solution than buying a small hard drive. :D

It *is* a cool idea, though.

---

### Post by HugoSerrano on 2011-12-21
> **TheNessus said:**
> i figure it could work with very distant radio transmitters-recievers. that is, light years apart.

they only need to transmit once, and the one at the other end will only to need to receive once, in a time frame of years. then when the receiver receives it, it will transmit it back, taking again years for the signal to reach the first device. and so on and so forth. 

But that would require a storage of some kind like RAM, where the received information is stored momentarily before being analyzed and transmitted back. 


- a less sophisticated post than previous ones.

In this case, when you need to retrieve the data, you will need to wait (some years) until the waves come back to you!

Regards!

---

