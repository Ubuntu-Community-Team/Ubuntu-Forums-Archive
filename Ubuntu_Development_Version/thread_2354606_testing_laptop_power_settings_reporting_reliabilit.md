---
title: "testing laptop power settings reporting reliability"
date: 2017-03-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-03-04
I don't want to hijack the other thread  so I am starting a new one here.  My goal is to investigate if:
1.ubuntu-gnome 17.04 "live" session from daily will run my power down on HP 2000 in a destructive manner
2. To clarifiy my assumption that ubuntu-mate affected the power geometry on another battery running on a Toshiba.

 I will post results later.

thanks

---

### Post by #&amp;thj^% on 2017-03-04
> **ventrical said:**
> 
2. To clarifiy my assumption that ubuntu-mate affected the power geometry on another battery running on a Toshiba.

 I will post results later.

thanks

I have seen similar results with a Lenovo B470 Laptop && Acer 5560 Laptop && Ubuntu-Mate with a Gnome and Unity entry session.
Sure seems the Mate setting with regards to power management lingers into the other sessions.
OpenBox is the only DE session that is not effected by the Mate Power settings.:D
Just my 2 cents here is all.

---

### Post by ventrical on 2017-03-04
> **1fallen said:**
> I have seen similar results with a Lenovo B470 Laptop && Acer 5560 Laptop && Ubuntu-Mate with a Gnome and Unity entry session.
Sure seems the Mate setting with regards to power management lingers into the other sessions.
OpenBox is the only DE session that is not effected by the Mate Power settings.:D
Just my 2 cents here is all.

Really .. thats exactly it. I could not have said it better myself.

I am currently uploading video re; gnome-desktop live session and could not find any probs as which mac4man had pointed to but thats just one test. I am still testing the Mate problem test case to see if I can document my work, otherwise I will strike it as per failing battery.

Regards..

---

### Post by ventrical on 2017-03-04
Here is video of ubuntu-gnome 17.04 *live* battery test on HP 2000.

It actually worked awesomely .. I shut it down after 2 and 1/2 hours of continual run time.



[https://www.youtube.com/watch?v=2wslXlNIW-E&feature=youtu.be](https://www.youtube.com/watch?v=2wslXlNIW-E&feature=youtu.be)

---

### Post by ventrical on 2017-03-07
I am on the final stretch of my test run on Toshiba Satallite  L300 which is circa 2007. I drained the batteries down manually using fans and got it down to 2.56 volts. 

One of the tricks are;  is to charge it without operating system and so I am doing that now. After it is charged and I get the same behaviour (of a run on the battery) I will strike my assumptions and declare that the eeprom RISC microcontroler has deprecated (most likely case scenario).

Regards..

---

### Post by ventrical on 2017-03-08
I am marking this thread as solved. This appears to be a deprecated eeprom RISC microcontroller and not ubuntu-mate desktop causing the problem.

---

