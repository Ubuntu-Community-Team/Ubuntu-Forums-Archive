---
title: "I love it when a plan comes together -- print server trials &amp; success"
date: 2012-01-26
forum: Testimonials &amp; Experiences
---

### Post by kurt18947 on 2012-01-26
I'm so proud of myself I just gotta tell somebody:). We had a HP Photosmart printer that developed a terminal error.  HP's web site had one procedure to try and if that didn't fix the problem, call HP's friendly service people.

No. In all liklihood service would cost more than a new printer.  We have an old warhorse HP 940C which is still soldiering on but has no provisions for networking.  I considered trying to share the printer but that PC is not always on, I'd rather network through the router.  I had an old Netgear PS101 parallel port print server which hadn't been used for years.  My last experience with it was under Win9x and the whole experience was a study in frustration.  "Well," says I "Let's see how Ubuntu does." Fire up Google and find that to reset the print server requires a Windows app as far as I could determine.  Download the Windows app in Win7. Setup.exe file is from 2002 -- Uh oh. Well download and install it anyway. That worked.  Plug everything in and start the print server admin app. "ScanServer Crashed. Click here to try and fix it."  Click there and get the Windows equivalent of a blank stare. CRAP. In hindsight I should have checked to see if I could run the app in XP compatibility mode, I didn't think about it at the time.

Well, I have a notebook with an XP install, I'll try that.  Downloaded the .zip file, extracted it and clicked on the setup.exe file. Couple hard drive flickers and nothing. Try it again, nothing.  DOUBLE CRAP. I decided to restart in safe mode and install.  That worked.  Restart again -- each cycles take 3+ minutes. This time I was able to connect to the print server to activate TCP/IP and reset the I.P. address. Disconnect everything, shut XP down (thank goodness) and connect the print server to the HP 940C. Start everything up, fire up SWMBOs machine running Meerkat, install the printer, specify the URI (the printer wasn't found automagically).  The printer showed up but was paused. I tried printing anyway and got a message to go to policy and enable the printer. Did that and -- MAGIC!!! IT WORKS!!!  Try my put- upon-from-XP Thinkpad restarted in 11.10 (aahhhh, that's better!). That time I didn't even have to go to policy to enable the printer, just specify the URI and it was there. I'm so proud of myself :D and mega kudos to the devs that designed and coded a modern system that still works so well with vintage hardware.

---

