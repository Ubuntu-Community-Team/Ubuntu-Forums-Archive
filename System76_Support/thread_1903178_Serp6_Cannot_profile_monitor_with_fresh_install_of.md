---
title: "Serp6 Cannot profile monitor with fresh install of 11.10"
date: 2012-01-01
forum: System76 Support
---

### Post by ShokTHX on 2012-01-01
I finally updated my Serp6 to 11.10 and did a fresh install. It's looking good so far except for one thing:
I do a lot of photography with my laptop and I need to make an icc profile of the monitor but the monitor does not show up as a device I can profile (using the Gnome color app.).
In the "Additional Drivers" there are two ATI/AMD proprietary drivers but I cannot activate the one that says "post-release updates."
Any ideas?

James

---

### Post by isantop on 2012-01-03
You won't want to use the "Post-release Updates" driver, as it's not particularly stable. Can you activate the other AMD driver?

---

### Post by ShokTHX on 2012-01-03
Yes, the other driver is activated.
The monitor does not show as a device in the System settings>>color application.
The only device that shows is the built in webcam.

---

### Post by isantop on 2012-01-04
This would be due to limitations of the proprietary AMD driver. That said, you my be able to Gamut adjustments and color corrections from the AMD Catalyst Control Center. Just search for AMD in the dash, and be sure to use the "administrative" result to make sure they stick system wide.

---

### Post by ShokTHX on 2012-01-05
That won't really help.
I'd like to make a hardware profile using a measuring device for accuracy.

---

### Post by ShokTHX on 2012-01-05
I found a partial solution.
I was able to profile and calibrate the monitor with Argyll. I know it works as it turns my favorite wallpaper into a yellowish washed out mess.
I just need to figure out how to add it to the startup programs now.
It's not as convenient or simple as the color profile system that is supposed to work in Ubuntu, but at least it works.

Thanks
James

ps What is with the hidden links on the System 76 sticker page? Nuts? Diet pills?

---

### Post by isantop on 2012-01-05
Can you post a link to the page you're at? I'm guessing it was caused by spammers, and if you post a link I'd be happy to remove it.

---

### Post by ShokTHX on 2012-01-05
Second paragraph under "'Powered by Ubuntu' Stickers for All".
Actually, now that I look, the links are hidden all the way down the page. Looks like a script to add links to matching phrases.

[http://knowledge76.com/index.php/International_Powered_by_Ubuntu_Sticker_Program](http://knowledge76.com/index.php/International_Powered_by_Ubuntu_Sticker_Program)

---

### Post by isantop on 2012-01-06
Thanks, I think I've got the spam removed and the spammers blocked.

---

### Post by ShokTHX on 2012-01-25
Found some more spam:
[http://knowledge76.com/index.php/Category:HowToDesktop](http://knowledge76.com/index.php/Category:HowToDesktop)

---

### Post by isantop on 2012-01-25
Fixed. Thanks for the report! 

I should add that we now have a forum thread about Wiki spam. You can find it here: [http://ubuntuforums.org/showthread.php?t=1905323](http://ubuntuforums.org/showthread.php?t=1905323). That will be the best place to report Wiki spam in the future.

---

