---
title: "Serial vs Parallel - trying to understand"
date: 2011-12-09
forum: The Cafe
---

### Post by flyingsliverfin on 2011-12-09
Can I think of a parallel port as a bunch of serial pins in one plug?

I was looking at analog digital converters and some are parallel and some are serial. If i connect to them with a microcontroller (eg arduino etc) can i read each pin of the parallel with the same function as I would with a serial?

---

### Post by lisati on 2011-12-09
> **flyingsliverfin said:**
> Can I think of a parallel port as a bunch of serial pins in one plug?

I was looking at analog digital converters and some are parallel and some are serial. If i connect to them with a microcontroller (eg arduino etc) can i read each pin of the parallel with the same function as I would with a serial?

At a basic level, "parallel" transmits several chunks of information at once, and "serial" sends one chunk at a time.

---

### Post by mips on 2011-12-10
> **flyingsliverfin said:**
> Can I think of a parallel port as a bunch of serial pins in one plug?


No.

With parallel you will be sending a full byte at once across the 8 data pins. With serial you send a byte in sequence 1 bit at a time in conjunction with stop start bits etc.

---

### Post by YeOK on 2011-12-10
> **flyingsliverfin said:**
> Can I think of a parallel port as a bunch of serial pins in one plug?

I was looking at analog digital converters and some are parallel and some are serial. If i connect to them with a microcontroller (eg arduino etc) can i read each pin of the parallel with the same function as I would with a serial?

Not sure I fully understand your question. Do you want to use each of the parallel ports data pins for different things, ie: not parallel data transfer ? 

You can do that, if you want too. You will just have to Google parallel port programming.

---

### Post by grahammechanical on 2011-12-10
Here are two links that might help or confuse you even more. Still it is all knowledge.

[http://en.wikipedia.org/wiki/Serial_port]("http://en.wikipedia.org/wiki/Serial_port")

[http://en.wikipedia.org/wiki/Parallel_port]("http://en.wikipedia.org/wiki/Parallel_port")

Compare the pinouts. The reason that some analogue to digital converters use serial connections and some use parallel is more to do with the connections on the device that they are to plug into than to the way analogue to digital conversion takes place.

The amount of data needing to be sent between the two devices at each moment will also make a difference as well as the speed at which the conversion needs to take place.

Some serial devices need a 25 pin plug and socket. Others can get by with 9 pin plug and socket. Such as computer mice.

These analogue to digital converters might not be serial or parallel devices at all. They might only be using convenient sized plugs and sockets. Have you thought of that?

Regards.

---

### Post by flyingsliverfin on 2011-12-10
Thanks for all the answers. Makes more sense now.


> **mips said:**
> No.

With parallel you will be sending a full byte at once across the 8 data pins. With serial you send a byte in sequence 1 bit at a time in conjunction with stop start bits etc.

Doesn't this mean that parallel would be much faster? Why do we use USB then?

---

### Post by YeOK on 2011-12-10
> **flyingsliverfin said:**
> Thanks for all the answers. Makes more sense now.




Doesn't this mean that parallel would be much faster? Why do we use USB then?

No, USB is faster. Parallel was limited by the old ISA bus and when they designed a replacement it just happened to be USB. USB is not just faster either, it happens to be a standard, supports longer cable lengths, can power a device and most importantly, costs less. You only need four wires in a cable for example.

---

