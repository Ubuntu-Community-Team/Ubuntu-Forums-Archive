---
title: "UbuntuOne OpenID login with each resume"
date: 2009-11-04
forum: Ubuntu One (CLOSED)
---

### Post by bertmanphx on 2009-11-04
Hello,
I'm running Ubuntu 9.10 here, 64 bit, upgraded from 9.04.

UbuntuOne seems to work well between my laptop and desktop, with one small exception:  When resuming from suspend on my desktop, the UbuntuOne client will not reconnect, until I tell it to "disconnect" and "connect".  Upon doing so, I have to add my machine again to the list of authenticated computers on my account.

My Laptop, seems to be working fine.  The only difference is that the laptop is a fresh install, the Desktop is an upgraded from 9.04.

Thoughts?

bertmanphx

---

### Post by duanedesign on 2010-01-27
I'm sorry to hear Ubuntu One isn't working properly for you. Can you try the following and let us know the results?

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. A web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after you follow these steps. If you are not connected, please file a bug report and attach the files below. 

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

The easiest way to file a bug is r-click on the Ubuntu One Applet in your panel at the top of your screen and select 'report a problem.

---

