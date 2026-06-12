---
title: "Low graphics mode followed by blank screen after upgrade"
date: 2013-10-17
forum: System76 Support
---

### Post by cwk on 2013-10-17
I have a gazp8 that came with 13.04, so this is the first upgrade on this machine. 

When I boot up I get a box that says " the system is running in low-graphics mode. your screen, graphics card, and input device settings could not be detected correctly. You'll need to configure these yourself." It then asks me what I would like to do: run in low graphics mode for just one session, reconfigure graphics, troubleshoot the error, or exit to console login. Run in low graphics mode and exit to console login go to a black screen with a blinking cursor in the corner. The other options do nothing useful either.

I have opened the console and updated the system76 driver, and made sure that the rest of the packages were up to date, and am at a loss as to what to do next.

 I really needed my computer to work tonight, and am pretty disappointed about this, especially since I got an email saying that system76 machines were ready to go for 13.10.

---

### Post by isantop on 2013-10-18
I'm thinking this was a one-off issue caused by the upgrade. Were there any error messages or freezes that occurred when you upgraded?

---

### Post by no_name_22525 on 2013-10-19
I had the same problem. Here's what I did to fix it.

Basically something is going wrong between X and startkde. I had to alter the permissions of a few files (~/.Xauthority and ~/.ICEauthority). This was, however, after completely reinstalling X and many other packages, so it's hard to say exactly what made the difference. 

I suggest that you try to run startx and startkde from a console log in and look for any files that are reported as errors. You may need to add "exec /usr/bin/startkde" to either /etc/X11/xinit and/or ~/.xinitrc

---

