---
title: "Presonus firebox with firewire pc card adapter - trails and tribulations"
date: 2010-03-01
forum: Ubuntu Studio
---

### Post by prouddad1 on 2010-03-01
I'm able to connect to the firebox consistently, but having to reboot every time jack crashes or looses contact with Ardour is driving me crazy.  Is there a way to flush jack and restart without having to restart ubuntu?  

What settings should I adjust to reduce xrun errors?  Changing settings causes Ardour to loose contact with jack and requires reboot to reconnect - any way around the reboot process?

Does the Thinkpad T40 (pentium m) have enough umph to record in realtime mode?  I haven't been able to connect in realtime mode yet.  Only 1 gig of memory - I thought I had more.  But before I go get more memory, can someone tell me the minimum hw requirements to record two tracks, simultaneously, fair quality in realtime mode?  Should I spend time getting it working on this box or should I move to something more powerful?  I like the idea of running on the laptop for portability.
---------------------------------------------------------------

Ok after reading and researching the forums, I'm refreshed and ready to try to tackle this again.  Logging out and logging back in is less painless than a reboot - seems to work (to free up jack) most of the time.

This document looks to be straight forward, although I'm running Karmic:
[http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=1e8e80153b26ce1edf2da3a58b0ad31c](http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=1e8e80153b26ce1edf2da3a58b0ad31c)

I examined the irq priority list - it looks like it needs to be modified:  USB interrupts are currently higher priority than yenta but I'm not sure how to change this. BTW, I didn't add the usb stuff when I originally edited the irq priority list - it just appeared.  (Trulan, I followed the link you provided in the other thread, but as a newbie to linux, its a bit over my head).  I'm not at my linux box so I'm writing this from memory.  I could use some guidance from the gurus.   

some other ideas:  should wireless networking be disabled or just moved down in priority?  I want usb and/or networking available to move files around - could live without wireless but need one of the other two mentioned.  Please help.

---

### Post by trulan on 2010-03-02
> **prouddad1 said:**
> I examined the irq priority list - it looks like it needs to be modified:  USB interrupts are currently higher priority than yenta but I'm not sure how to change this.
I certainly can't answer all your questions but I'll try to answer this one.  The irq priorities list (RTIRQ_NAME_LIST) is simply a space separated list.  The things named on that list are prioritized in the order they are listed.  The first item on the list gets a priority of 90, the next item gets 85, the next 80, etc.  The default step size is 5, but you can change that with this line:  ```
# Priority decrease step.
RTIRQ_PRIO_DECR=5
```Anytime rtirq sees a space in the RTIRQ_NAME_LIST (in between the quotation marks), it treats the next word as a new item, and gives it a priority that is 5 lower than what was given to the previous item.  So the default list
```
RTIRQ_NAME_LIST="rtc snd usb i8042"
```sets the real time clock to 90, the sound card to 85, the usb hub to 80, and i8042 to 75 (I think that's the keyboard but I'm not sure).  Since there are usually several USB devices, they will get set to 80, 79, 78, etc.

So if your list reads
```
RTIRQ_NAME_LIST="rtc ohci1394 snd usb i8042 yenta"
```then it won't work because your card controller, yenta, will only get a priority of 65.  If yenta is put into its proper place in the order, like this:
```
RTIRQ_NAME_LIST="rtc yenta ohci1394 snd usb i8042"
```Then yenta gets set to 85, ohci1394 gets set to 80, and as long as the real time priority for Jack is less than 80 it should work.

The catch is, you can only have yenta in that list is you have a card controller named yenta.  I don't know how many computers this applies to but I believe it's fairly common.

Make sense?

---

