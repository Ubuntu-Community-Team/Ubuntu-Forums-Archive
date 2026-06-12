---
title: "Low latency in PureData(Pd) with Jack in Ubuntu Studio 12.04"
date: 2013-03-25
forum: Ubuntu Studio
---

### Post by calimastrusia on 2013-03-25
I´m having trouble to make PureData(Pd) to work at low latency in Ubuntu Studio 12.04.
  I get Pd and Jack to work together with my Audio Interface (Alesis  IO4) but only at a frames/Period of 1024, which means a latency of 45.2  ms.
  As soon as I try to lower the Frames/period to lower the latency, I get an Audio I/O error from Pd.
  I tried to mess around with the oder parameters, but the only one who  appears to affect Pd (and the latency) is the Frames/Period.
  I also tried to use the configuration explained here: [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) , but it doesn´t work either. I really need to get the lowest latency possible, because I work with live instruments and proccesing.
  Any thoughts that may help?

---

### Post by Sylos on 2013-03-25
I dont know much that could help you here, but have you checked that yours "Periods/buffer" is set to 3 (I believe that is what is required for USB interfaces).

Cheers

---

### Post by jejeman on 2013-03-25
What is your CPU? Is it set to performance governour?

---

### Post by zequence on 2013-04-04
> **calimastrusia said:**
> I´m having trouble to make PureData(Pd) to work at low latency in Ubuntu Studio 12.04.
  I get Pd and Jack to work together with my Audio Interface (Alesis  IO4) but only at a frames/Period of 1024, which means a latency of 45.2  ms.
  As soon as I try to lower the Frames/period to lower the latency, I get an Audio I/O error from Pd.
  I tried to mess around with the oder parameters, but the only one who  appears to affect Pd (and the latency) is the Frames/Period.
  I also tried to use the configuration explained here: [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) , but it doesn´t work either. I really need to get the lowest latency possible, because I work with live instruments and proccesing.
  Any thoughts that may help?

Make sure you are on linux-lowlatency. 
```
$ uname -r
3.8.0-14-lowlatency 
```

Much depending on your audio device, you should be able to set frames/pediod as low as 64. This is what I would recommend for live audio (this is what I use myself with pd).

Also, you can start pd in realtime, with the flag -rt

I would not be fully concerned about errors, as long you don't hear anything.

---

