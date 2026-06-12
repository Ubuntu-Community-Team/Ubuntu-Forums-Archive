---
title: "Focusrite Saffire Pro 10, Ubuntu Studio 11.04 64 bit"
date: 2011-11-20
forum: Ubuntu Studio
---

### Post by noisemaker? on 2011-11-20
hello,

i have buy everything what everybody says working with ubuntu studio...

i have texas instruments firewire card and i just buy focusrite saffire pro 10 


 have made a clean install with ubuntu studio 11.04 64 bit and have changed not a thing... when i start ffado mixer i get the error message could not communicate with ffado dbus something....

i have tryed allready al the standard solutions like reboot interface on of and so on

any help please, thank you

---

### Post by noisemaker? on 2011-11-20
as stupid as it is, with ubuntu studio 11.10 it does work

---

### Post by sgx on 2011-11-22
Linux software is always in flux, so it's good to keep that
working system, and avoid major updates. It is good luck do your testing and experiments on a secondary install on a separate hard-disk/usbstick. I watch the forums for a few months when
the next big thing arrives, and let the experts sort out the
wobblers. Glad you got some excellent hardware to use!

---

### Post by noisemaker? on 2011-11-23
all i get are xruns and harsh noise, ffado mixer lets hang up the interface... clicks and pops.. i use windows, then i know it works

even if i hate microsoft, but what other choice do i have

---

### Post by noisemaker? on 2011-11-23
OK, i give it another try because i found something here, especialy Step 5

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by noisemaker? on 2011-11-23
OK, i have to appologise for my rude thread i have postet earlier and got deleted by some Admin :D

I have fixxed all the issues with the saffire pro 10...

You need to go trhough the link i have postet above... the key for me was Step 5 and Driver Confusion... First do the steps as told in driver Confusion and look for the firewire stack, then do so as told in Step 5 and add the word yenta (which stands for the firewire controller) and after the name of the firewire stack and...

i am curently sitting infront of another pc so i can not see what i have exactly changed, but if you do so like in the link it is all good. as a side efect i have seen... before when i start jackd i had about 5 % CPU and lots of Xruns, now after i have made the change on the rtirq file i have only 0,86 % CPU in Jackd and no Xrun...

I also had the Problem, when i press Stop at jackd, jackd gave me a message cannot stop dbus... something... and i had to reboot the pc.. but i have founf some option at the last page of jackd, the last option (use dbus).. i have unticked this one and now i can just press stop and play again in jackd without the interface hangs up or the pc crashes

if anyone has problem with performance at ubuntu studio 11,10 and focusrite saffire pro.. you can also give me shout.. i will try to help

i am so happy it now works

so the problem was that the firewirestack was not setup for rt priority... well

---

