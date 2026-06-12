---
title: "PNP9 boot up issue"
date: 2013-08-10
forum: System76 Support
---

### Post by cranet on 2013-08-10
Hello all:

I upgraded my Pangolin Performance 9 to 13.04 about 2 months ago.  Recently when I boot the computer up, I get the Ubuntu splash screen with the dots filling up then it goes to a blank (black) screen with the cursor blinking in the upper left hand corner.  The only way to reset it is to pull the battery then it boots up normally.  This only happens every 7th or 8th time I turn on the computer.  After I pull the battery, and reboot it works fine.  I have tried to correlate the occurrence of the issue with something I was doing the last time I turned off the computer, but have been unable to find anything.  What could be causing this?  More importantly, how can I resolve this issue?


Advanced thank yous for any assistance!

---

### Post by cranet on 2013-08-12
Yet again I am floored by the lack of customer service from System 76. I bought this computer on the reputation of their outstanding support, but they have disappointed me at every question.  I guess I get to call their tech support (sic) for the daily line of BS fed to all customers.  Looking back it is my fault for drinking the Kool-aid Mr. System 76 dispensed.  I really wanted to believe the dream of a company supported Ubuntu laptop.

---

### Post by isantop on 2013-08-13
Sorry about the slow response, I was hammered with support on our website yesterday and was unable to attend to the forums.

When this happens, do you see a mouse cursor in the center? Try typing your password and hitting enter, as we've seen an occasional LightDM glitch where the display manager tries to initialize before the graphics drivers are ready.

---

### Post by phxpx on 2013-08-13
I am not sure if it is the same bug but sometimes on boot up, I see dark screen with just my cursor in the center. Then I switch to tty1 and restart computer.

---

### Post by cranet on 2013-08-14
The screen is absolutely black, no mouse cursor visible, only a blinking cursor in the upper left hand corner.  So you want me to type in my password to see if the computer will enter in my desktop?

---

### Post by cranet on 2013-08-14
The screen is absolutely black, no mouse cursor visible, only a blinking cursor in the upper left hand corner.  So you want me to type in my password to see if the computer will enter in my desktop?

---

### Post by isantop on 2013-08-15
> **phxpx said:**
> I am not sure if it is the same bug but sometimes on boot up, I see dark screen with just my cursor in the center. Then I switch to tty1 and restart computer.

You're seeing the bug I mentioned above. Instead of restarting, try typing your password and hitting enter.

> **cranet said:**
> The screen is absolutely black, no mouse cursor visible, only a blinking cursor in the upper left hand corner.  So you want me to type in my password to see if the computer will enter in my desktop?

Give that a try, and let me know if that fixes it. It may be the same issue but with different specific symptoms.

---

### Post by cranet on 2013-08-20
> **isantop said:**
> You're seeing the bug I mentioned above. Instead of restarting, try typing your password and hitting enter.



Give that a try, and let me know if that fixes it. It may be the same issue but with different specific symptoms.

Same black screen, cursor in the upper left hand corner blinking, tried "blindly" typing in password (3 times) to no avail. This was the ~8th time I have rebooted my PNP 9. If this is a known issue why not publicly admit to these issues before buying a computer from System 76?  I fully understand that I was buying an Ubuntu (OS) laptop that was still and (always) is under development.  Why the secrecy to known issues that may affect your product?  I understand that I may have to deal with some weird issues that may involve me actually thinking and tinkering to get resolved.  I get that and readily accept the challenge,but it should not take a week to get issues resolved if they are known. I guess what I'm saying is why not list on your website the known issue that a customer may encounter with a purchase of a specified device?  

With that said, i love my System 76 laptop.  This thing screams in performance and I love to laugh at my Mac friends who bought their laptop for more than 1/2 of what I paid for the same specs.

Dayspring

---

### Post by isantop on 2013-08-21
I think you're seeing a different issue. If it was the same, then you'd definitely be able to log in after typing your password. Assuming it was typed correctly, there's a different issue. Can you try running from a live disk of 13.04?

---

