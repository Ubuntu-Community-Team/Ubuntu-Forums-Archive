---
title: "Compaq Presario C300 - speakers affect HDD"
date: 2011-04-05
forum: The Cafe
---

### Post by youbuntu on 2011-04-05
My friend has a Compaq Presario C300, and when he listens to music at moderately loud volumes, using the *internal* speakers, the hard drive tends to lock up for a few Ms or stutter. 

My thinking is that the magnetic field from the built in speakers, is emitting a strong magnetic flux, which is in turn affecting the HDD (located NEXT TO THE INTERNAL SPEAKER! :?)

If anyone has any ideas, I'd be grateful indeed ^_^

Thanks! :)

---

### Post by LowSky on 2011-04-05
get some of those electrostatic bags electronic gear like HD comes in. open laptop. cut bag into a small sheet and wrap speaker or HD.

---

### Post by pi3.1415926535... on 2011-04-05
I have heard of something similar with old Macintosh computers. A solution could be to not use such a high volume, or to use instead headphones or external speakers.

---

### Post by disabledaccount on 2011-04-05
> **glossywhite said:**
> My thinking is that the magnetic field from the built in speakers, is emitting a strong magnetic flux, which is in turn affecting the HDD (located NEXT TO THE INTERNAL SPEAKER! :?)This is impossible.
There are 3 main reasons that can cause HDD lockups/slowdowns in such case:
- damaged/buggy software or codecs, damaged filesystem, wrong/damaged drivers wrong settings (in the player - sometimes it's sufficient to select different output device or change buffers size)
- damaged hdd - check SMART for pending/reallocated sectors number, read/write/UDMA crc errors ("slow" sectors).
- wrong HDD - most today's HDDs have integrated accelerometers that are measuring vibrations. Those results are used both to inform drive that it should correct head position and to inform manufacturer that customer have had kicked the device ( :) ) - check G-Sense Error Rate in SMART. Some HDDs, like first green series from Samsung have buggy firmware that caused serious slowdowns f.e. in situation when 2 drives were mounted close to each other (vibrations).

---

### Post by youbuntu on 2011-04-05
> **pi3.1415926535... said:**
> I have heard of something similar with old Macintosh computers. A solution could be to not use such a high volume, or to use instead headphones or external speakers.

I knew someone would mention the old Mac. That is the first thing which I told my friend about (his laptop).


> **tomazzi said:**
> This is impossible.
There are 3 main reasons that can cause HDD lockups/slowdowns in such case:
- damaged/buggy software or codecs, damaged filesystem, wrong/damaged drivers wrong settings (in the player - sometimes it's sufficient to select different output device or change buffers size)
- damaged hdd - check SMART for pending/reallocated sectors number, read/write/UDMA crc errors ("slow" sectors).
- wrong HDD - most today's HDDs have integrated accelerometers that are measuring vibrations. Those results are used both to inform drive that it should correct head position and to inform manufacturer that customer have had kicked the device ( :) ) - check G-Sense Error Rate in SMART. Some HDDs, like first green series from Samsung have buggy firmware that caused serious slowdowns f.e. in situation when 2 drives were mounted close to each other (vibrations).


I agree with your possible causes, but I hardly think my suggestion is "impossible". In fact, it is VERY possible.

Thanks :)

---

### Post by disabledaccount on 2011-04-06
> **glossywhite said:**
> I agree with your possible causes, but I hardly think my suggestion is "impossible". In fact, it is VERY possible.
Thanks :)Well, that's your problem - but consider the fact, that *many* laptops have speakers mounted near HDD. Furthermore speakers have relatively low flux density outside - faaaar lower than neodymium magnets that are built in HDD (actuator drive) :)

---

### Post by KiwiNZ on 2011-04-06
> **tomazzi said:**
> This is impossible.
There are 3 main reasons that can cause HDD lockups/slowdowns in such case:
- damaged/buggy software or codecs, damaged filesystem, wrong/damaged drivers wrong settings (in the player - sometimes it's sufficient to select different output device or change buffers size)
- damaged hdd - check SMART for pending/reallocated sectors number, read/write/UDMA crc errors ("slow" sectors).
- wrong HDD - most today's HDDs have integrated accelerometers that are measuring vibrations. Those results are used both to inform drive that it should correct head position and to inform manufacturer that customer have had kicked the device ( :) ) - check G-Sense Error Rate in SMART. Some HDDs, like first green series from Samsung have buggy firmware that caused serious slowdowns f.e. in situation when 2 drives were mounted close to each other (vibrations).

I would tend to agree with this and given that it's a Compaq I would add to list of possible causes...
1 Heat
2 Capacitors

---

### Post by unknownPoster on 2011-04-06
I doubt that any sort of "magnetic flux" is to blame considering the amount of shielding that is put in modern electronics.

---

