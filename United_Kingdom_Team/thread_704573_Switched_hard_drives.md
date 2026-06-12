---
title: "Switched hard drives"
date: 2008-02-22
forum: United Kingdom Team
---

### Post by g7mjv on 2008-02-22
Hi people

l do hope that this hasn't been asked too many times before..

l have 2 hard drives in my machine, 1 with windows 2k and the other with Ubuntu on it. l've tried having them both connected to the same ribbon and rebooting with either of the 2 hard drives powered. Sadly it doesn't seem to work so l wonder whether there's a solution..Both drives are set as masters.. l don't want to have both OSs on the same hard drive 

Please could someone offer a solution

---

### Post by kyphi on 2008-02-22
If you are using ribbon cable to connect your hard drives then you must set one as master and the other as slave and both have to be connected to power.

If you are using SATA drives there is no master/slave adjustment needed.

---

### Post by g7mjv on 2008-02-23
Thanks for the response.. What l would like to be able to do is:

Be able to flick a switch so that l have the option to boot the PC with either the windows HD or the Ubuntu HD.

---

### Post by kyphi on 2008-02-23
That is easily done.  What you want to do is called: Dual Boot.

First attach both your drives to the ribbon cable and power supply.  Set one drive to master and the other to slave.

Second, reinstall Ubuntu which will write a boot section including Windows.

Here are two URLs to help you with information.

[http://video.google.com/videoplay?docid=-2369893842637434537](http://video.google.com/videoplay?docid=-2369893842637434537)

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

The first is in English English and the second is in American English.

---

### Post by g7mjv on 2008-02-24
Many thanks, l'll look into it..

---

### Post by cybervegan on 2008-03-20
Many modern BIOSes have a boot-time hot key that allows you to select which disk to boot off. It's often F11 or F12.

-cybervegan

---

### Post by bossa on 2008-03-20
Put a jumper on the relevent pins on your master hard drive and leave the slave jumperless.

[http://www.mysuperpc.com/hdu/jumper_pins.shtml](http://www.mysuperpc.com/hdu/jumper_pins.shtml)

Check with the hard drive manufacturers site for details.

---

