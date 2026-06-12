---
title: "M-Audio &amp; delta 2496"
date: 2011-07-18
forum: Ubuntu Studio
---

### Post by fucow23 on 2011-07-18
Hi all this is my first post and i need some help setting up my sound cards. I have a Delta 1010lt & a Delta 2496 in my Ubuntu 11.04 recording box and need to know how to setup both cards. When i look at the ENVY controls all i see is the 2496 as default sound card. I had the 1010lt in the system first got it working perfect but when i installed the 2496 every thing changed. I would like both cards working so i can have the other 2 inputs on the 2496. Any help is welcome. 
THANKS
Mike

---

### Post by Pablo_F on 2011-07-19
Hi, 

You can list your audio interfaces in a terminal via this command:

cat /proc/asound/cards

Assuming your 1010 is number 1 (i.e., the second one as the count is zero based) you can run envy24control on it via the -c option, like this:

envy24control -c1

To use both interfaces at the same time there are different approaches. If you use jack (the audio server that you very probably will want to use, as it is needed for ardour and many other audio/music creation apps) you should read this[1]:

Read also the ubuntuforums thread [2] and how to make a virtual device out of two 1010LT's [3]. Not exactly the case, but you could do something similar.

[1] [http://jackaudio.org/multiple_devices](http://jackaudio.org/multiple_devices)
[2] [http://ubuntuforums.org/showthread.php?t=1675400](http://ubuntuforums.org/showthread.php?t=1675400)
[3] [http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

Cheers, Pablo

---

### Post by fucow23 on 2011-07-19
Thanks for the quick reply. I sorta understand so i will give it a try. Like i said im kinda new to this audio setup in linux but Its time for me to dig in and get my hands dirty. I will most likely be back with more questions. Thanks for the info that really helped.
Thanks

Mike

---

### Post by sgx on 2011-07-20
> **fucow23 said:**
> Thanks for the quick reply. I sorta understand so i will give it a try. Like i said im kinda new to this audio setup in linux but Its time for me to dig in and get my hands dirty. I will most likely be back with more questions. Thanks for the info that really helped.
Thanks

Mike
If trouble persists, you can try changing which pci slots are used,
and note how each card presents itself when alone, and what
changes when a second card is inserted. If you have a motherboard video chip, and also use a separate video card, you can remove the
card and go with the video chip temporarily, while the audio system gets perfected. The motherboard sound should be turned off at the bios, or at least blacklisted. You'll have a great setup shortly!

If you play guitar, a $99 Fender Mustang I or $199 Mustang II is a great usb interface/amp combo, and even has a nifty patch linux editor called 'plug', to enable the functions of Fuse, a bundled Silverlight/.net editing app for windows/mac users.

Cheers

---

### Post by fucow23 on 2011-07-20
Thanks for the info from you both Poblo & SGX. I can use the command line & get the envy control to come up foe each card but i have to bring up 2 envy control windows. One for the 1010lt & one for the 2496. Will both cards work this way? I also have the digital out of the 1010lt to the digital input on the 2696. Am i heading in the right direction?
Many thanks in advance. 
Mike

---

### Post by sgx on 2011-07-21
This discussion may help a bit. I would try recording, and see if
you notice any weird timing.

[http://www.homerecordingconnection.com/forum.php?action=view_thread&id=11997&frm=5](http://www.homerecordingconnection.com/forum.php?action=view_thread&id=11997&frm=5)

2 1010s linux example:

[http://www.remastersys.com/forums/index.php?topic=1208.0;wap2](http://www.remastersys.com/forums/index.php?topic=1208.0;wap2)

alsa config example

[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

Cheers

---

### Post by Pablo_F on 2011-07-22
> Am i heading in the right direction?

I think so. Now you have to write the right ~/.asoundrc file.

---

