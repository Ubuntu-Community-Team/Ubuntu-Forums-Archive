---
title: "RS232 monitor"
date: 2006-01-17
forum: The Cafe
---

### Post by estratos on 2006-01-17
I'm looking for a good serial communication monitor for Linux. Something like Portmon for Windows although having send capabilities would be great.

Any idea?

Thanks,

Daniel.

---

### Post by AmboyGuy on 2006-01-17
Snooper 
> Snooper passes data transparently between two serial (RS232C)
devices, capturing and logging the data and occasional comments you
want to insert into the logs.

It is useful for debugging or analyzing the communications protocol
between two devices that would normally be connected directly to each
other, e.g. a digital camera and a personal computer.  By sitting
"in the middle" (after you connect the two devices to serial ports
on your Linux machine) snooper is able to capture data traveling in
either direction while also passing it unmodified to the other device.

It is also possible to operate with a single serial device, using
your console and keyboard as the second device.
 Found out about it in Linux Journal. Pulled the description from Synaptic Package Manager. ( it's in the repo's )

---

### Post by estratos on 2006-01-17
Thanks but snooper doesn't let me specify binary frames to send, just ASCII characters.

---

### Post by mt-soft on 2010-05-06
Sorry if a bit late, but there is STermPro, a kind of advanced serial port monitor. May be handy just for your needs.

---

### Post by sydbat on 2010-05-06
> **mt-soft said:**
> Sorry if a bit late, but there is STermPro, a kind of advanced serial port monitor. May be handy just for your needs.No. This is only a 4 year old thread. You're not late at all.

---

### Post by cariboo on 2010-05-06
this thread is 4 years old, even if the op is still looking, he would have updated the thread. closed.

---

