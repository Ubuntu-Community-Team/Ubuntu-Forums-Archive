---
title: "ffado mixer not working in 10.04 (echo audiofire4)"
date: 2010-05-01
forum: Ubuntu Studio
---

### Post by fedexnman on 2010-05-01
ffado mixer is not seeing my echo audiofire4 (ubuntustudio 10.04), its says cant connect to dbus and there is a retry button below it,  qjackctrl works and im able to use my device in ardour, but im unable to get the ffado mixer to work, it works in 9.04, 9.10 but not 10.04. it wasnt working in the 10.04 beta either. :confused:

---

### Post by fedexnman on 2010-05-07
bump   , still have'nt figured out how to fix this issue,  ffado mixer works with my device in 9.04 and 9.10, but not 10.04 .  should i report as a bug or email a ubuntustudio dev ??  things are smooth sailing in 10.04 other than that.

---

### Post by babarosa on 2010-05-08
fedexnman,

visit [www.ffado.org](www.ffado.org), join the mailing list and post there. The developers of ffado themselves are very friendly to help.

---

### Post by nacho al horno on 2010-05-09
I have a similar problem. My Echoaudiofire 4 works fine in Karmic but when i did the upgrade to Lucid it didn't work anymore. I can't get the ffado-mixer to show and I also can't start jack with the firewire driver

---

### Post by fedexnman on 2010-05-09
mine works, but i did a fresh install(not upgrade), and followed the ubuntu studio prep pages for setting it all up. i think lucid uses libffado2, maybe jaunty n karmic used libffado1 ?? it all works except for ffado-mixer dbus server. im gonna email the ffado devs at the ffado site soon.

---

### Post by nacho al horno on 2010-05-25
I don`t understand what happend but my ffado mixer start to work after I did this. 
First I installed the libffado 2.0.0 from the ffado website, but still the fffado mixer didn`t work... the strange thing is that when i run in the terminal this comand: ffado-dbus-server then I clik on the ffado mixer and it start.... if i dont run that comand on the terminal the ffado mixer doesn`t appear...any ideas???... 
still it doesn`t run as well as it does on karmic...

---

### Post by Tofigh on 2010-06-17
Hi
Do you know any tutorial to learn how to work with ffado-mixer. After 4 days listening to silence I get mad...
The problem is I canät hear or record anzthing in Arour. Just as a test I connected two microhpnes to audio interface (saffire pro 40) and try to recording them but  nothing can be heart from them in ardour. SILENCE for more than 4 days make me crazy. I thought maybe its because of my wrong settings in ffado-mixer. So if you have worked with this ffado-mixer would you please look at these attached pics and let me know if my setting are correct? I just want to do very simple test. connect 2 microphones to audio interface and record them by ardour.

---

### Post by nacho al horno on 2010-06-17
Did you check the connections in jack? in my case, if I don`t connect the system capture 1 & 2 with the system out 1 & 2 nothing sounds

---

### Post by AutoStatic on 2010-06-17
Yeah try that with a pair of AT2020's connected and your headphones on ;)

---

### Post by Tofigh on 2010-06-18
I wanne cry. Still no sound
I attached a pic of connection configuration in jack
I almost connect everything to everything.
Cheers

---

### Post by mango42 on 2010-06-18
> **AutoStatic said:**
> Yeah try that with a pair of AT2020's connected and your headphones on ;)

But only if you are *really* desperate to get tinnitus, or worse!
:lolflag:

I haven't even arrived at ffado mixer yet - looks to be quite a puzzle in itself - matrix mixer, hmmm, what gives? Braincells, probably! ;-)

---

### Post by AutoStatic on 2010-06-18
> **mango42 said:**
> But only if you are *really* desperate to get tinnitus, or worse!The 'problem' with Focusrite devices, at least with my Focusrite Saffire Pro 10, is that zero gain is not zero gain but +13dB ([http://www.focusrite.com/products/saffire/saffire_pro_10_io/](http://www.focusrite.com/products/saffire/saffire_pro_10_io/)). And especially with high output mics like the AT2020 you'll probably blow up your ears when you connect the capture ports directly to the system out ports.

---

