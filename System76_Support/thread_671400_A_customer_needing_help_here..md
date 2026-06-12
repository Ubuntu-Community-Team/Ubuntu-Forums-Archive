---
title: "A customer needing help here."
date: 2008-01-18
forum: System76 Support
---

### Post by weverjames on 2008-01-18
I reinstalled ubuntu 7.10 in my gazelle value.  I don't have sound.  I haven't been able to install the system 76 drivers.  I downloaded them from the system 76 webpage.  I do the install order and a little wondow shows up with the text:  "installing drivers" and it remains in the screen.  I did it last night and left the computer running to see if it needed more time.  This morning the same window was there and nothing happened.  I still don't have sound.  I have tried with different versions of the drivers and I have reinstalled ubuntu twice w/o success.
I am w/o ideas.  I am needing system 76 support.

---

### Post by thomasaaron on 2008-01-18
Which Gazelle Value do you have? Is it the S2FM? If so, did you ever flash your dvd drive's firmware to fix the freezing bug? If not, it's almost guaranteed that this is the problem. Email me and I'll send you instructions. (support(at)system76(dot)com.

If you did flash the dvd drive firmware, try re-installing the driver.

Make sure you're connected to the Internet.

From a command line, enter:
sudo --purge remove system76-driver
sudo wget [http://planet76.com/repositories/system76-driver-2.1.13.deb](http://planet76.com/repositories/system76-driver-2.1.13.deb)
sudo dpkg -i system76-driver-2.1.13.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

---

