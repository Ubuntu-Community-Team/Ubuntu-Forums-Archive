---
title: "x screen is larger then monitor"
date: 2009-11-16
forum: System76 Support
---

### Post by miniyak on 2009-11-16
This seems like a fairly simple issue but its annoying and i haven't the time to look really look it up. (new job, longer hours..)

After installing the proprietary nvidia driver (185 i think.. whichever one was recommended) in 9.10, my X screen as become way too large for the actual screen (black margin to the right the can be moused over to). How do should i go about getting it back to normal?

This is more of annoyance then anything, but its one of the few bugs ive been bitten by with 9.10 preventing from switching from my bogged down install of 9.04. That and getting all my customization back to normal, lol

---

### Post by 3Miro on 2009-11-16
In Admin -> System and/or Prefs, you should see NVIDIA X SERVER SETTINGS. Try changing some of the options from there.

There should be an easy workaround for this one without the need for downgrade to 9.04.

---

### Post by miniyak on 2009-11-17
ill defiantly mess around with it more when i get the time. As far as i could see with a quick glance all of the settings were looking the same as how it it set in my 9.04 install.

  As far as upgrades and downgrades go, its all in a manner of perspective. Upgrade for developers and enthusiast, downgrade for those who just want a hassle free desktop experience. I just dual-boot to keep it safe. Ubuntu still beats the hell out of using windows or mac so ill be on board with it for the foreseeable future. Though if Puppy ever gets as more friendly i would probably switch without batting an eye.

---

### Post by miniyak on 2009-11-21
i just look at the settings and it seems that the resolution is right, but im not too sure about the refresh rate. On my 9.04 install the refresh rate is 50 and now it is set to 59.9. Should this make a difference in the size of the screen?

---

### Post by thomasaaron on 2009-11-23
...possibly.

After reviewing this thread, I'm not sure if you have upgraded to 9.10 or done a fresh installation (or dual boot) of it. Could you please clarify.

Also, do you have any other nvidia driver options?
Have you tried disabling the driver and then re-enabling it?

---

### Post by miniyak on 2009-11-23
its a fresh installation in another partition, so dual boot.

I didn't have the problem till installing the driver. So latter ill try another driver or just disable. I was getting wsxga+ without it anyway.

the only thing that i would think of to be off in the settings is the resolution being higher then my screens capabilities. Which is not the case. Its set to 1680*1050 and that is the capability of the display.

the only discrepancy i noticed was the refresh rate.

---

### Post by miniyak on 2009-11-27
ok, i just removed the nvidia 185 driver and the problem is gone 

To be honest i would like to have the graphics card to its fullest potential but at this point im wondering if it really matters? Just tested out one of the game emulators I use on occasion and it runs at the same speed with or without the driver in action. Compressed 720p quicktime content runs smoothly also. These are the only things I do at the moment that would seem to me to be graphically intensive.

I'm curious what goes on with the hardware when the graphics drivers are not being used. Is the graphics processing just going though the main cpu or are there generic drivers that Ubuntu uses to get the gpu to work? 

Maybe i should reload the driver?

---

### Post by thomasaaron on 2009-11-27
Well, with nVidia cards, you need *a* driver. You could use the nVidia drivers that you now are using, or you could switch to the open source nv driver... which is pretty lame and may not work well at all with more recent chipsets.

---

### Post by miniyak on 2009-11-27
So basically Ubunutu uses the open source driver when your not using the proprietary driver. 

I wonder if the power consumption is any different in between the two?

As much as i want to have the best of the best. I have to play the devils advocate here for the sake of not wanting to take the time to solve odd issues.

What exactly is the difference in capability between the open and proprietary versions of the drivers?

---

### Post by thomasaaron on 2009-11-30
There is a world of difference in performance. The nv driver will give you no 3d acceleration, and I doubt you will have much in the way of ability to configure an external monitor (although I've never tried it).

We've also never tested battery life with the nV driver. It kind of makes sense that it *might* improve battery life since it isn't really leveraging the power of the graphics card, though.

---

### Post by miniyak on 2009-11-30
yah, there isn't much in the way of configuring and external monitor. When i first installed 9.10 i tried HDMI without the driver and never ended up getting anything to work. 

For me the driver really doesn't make things all that much better. I think i might have one game that uses 3d acceleration that i may play maybe once every couple of months or so. As far as the external monitor goes having the driver doesn't change the fact that a 720p display, One, looks worst then the panp5's 15', and two, Looks even more like crap if you dont know how to configure to a monitor of a lower resolution, Or in my case, just don't care enough to jump through the hoops to do it. With 1080p displays ubuntu always seems to have a hard time centering the screen which i think is more of and issue that depends on the TV set in question. Unless using vga...

So if the battery life is 10minutes better or more, that benefit would outweigh the performance of the graphics card.

---

