---
title: "touchpad scroll not working"
date: 2010-05-02
forum: System76 Support
---

### Post by shadhavar on 2010-05-02
I just upgraded my Gazelle (gazp5 according to the System76 driver) from Karmic to Lucid. This was a clean install. I have run all the updates and the system 76 driver has been installed and run. My problem is my touchpad scroll no longer works. I remember when I upgraded to Karmic I had the same problem, but I do not remember how I fixed it. A quick web search turned up instructions for getting it to work in xubuntu 9.04 [http://blog.technicallyworks.com/2009/08/fix-touchpad-scroll-area-in-xubuntu-904.html]("http://blog.technicallyworks.com/2009/08/fix-touchpad-scroll-area-in-xubuntu-904.html") but I'd like to make sure that this is okay to use for regular ubuntu and 10.04 instead of 9.04. Or if there is another/better solution available.

Thanks.

---

### Post by thomasaaron on 2010-05-03
You can go ahead and try those instructions. If they don't work, they're easy enough to reverse.

We'll do some testing on this end too.

---

### Post by shadhavar on 2010-05-03
Ok so I tried the instructions from the site I found, but when I try the ```
synclient -m 1
``` I get the error: 
> 
Can't access shared memory area. SHMConfig disabled?

I checked and double checked the fdi file, rebooting after each time. I then followed the instructions at [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig") for enabling the SMHConfig and rebooted again. Still getting the same error.

Any suggestions?

---

### Post by isantop on 2010-05-04
Here you're getting errors because Ubuntu 9.04 still had most of HAL implemented, and now in 10.04, the HAL is completely gone. Make sure you have the option enabled in your Mouse Properties (System > Preferences > Mouse, then go to the Touchpad tab.)

---

### Post by shadhavar on 2010-05-04
> **isantop said:**
> Here you're getting errors because Ubuntu 9.04 still had most of HAL implemented, and now in 10.04, the HAL is completely gone. Make sure you have the option enabled in your Mouse Properties (System > Preferences > Mouse, then go to the Touchpad tab.)

Thanks for the info on HAL. I wish it was just an easy mouse/touchpad setting, :( the mouse properties/touchpad settings are the first thing I checked when I realized the scroll wasn't working. I even deactivated it, rebooted then reactivated it. No joy.

---

### Post by shadhavar on 2010-05-05
Found this while searching the web for answers: [http://superuser.com/questions/136568/touchpad-scrolling-is-gone-in-kubuntu-10-04-how-to-get-it-back]("http://superuser.com/questions/136568/touchpad-scrolling-is-gone-in-kubuntu-10-04-how-to-get-it-back")
It works!

---

