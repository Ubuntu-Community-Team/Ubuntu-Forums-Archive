---
title: "Starling Netbook problem...."
date: 2010-12-26
forum: System76 Support
---

### Post by EJJ on 2010-12-26
Hey guys, just got a new Starling Netbook yesterday for christmas. It's one of the newer ones (Star4)

It was working wonderfully yesterday and most of today until earlier when it wouldn't restart.


Basically it locked up and I used the power button to turn it off. After trying to turn it back on-it goes past the System 76 logo then stays at a black screen with a blinking cursor in the upper left hand corner. It will not launch Ubuntu.


Any ideas? The machine is brand new....does this happen often? I'm a bit new to Ubuntu and Linux in general.....


Any help would be appreciated, Thanks.

---

### Post by jml on 2010-12-26
No, this problem does not happen "often" but it can happen.  If you are left with just a blinking cursors, hold down the power button long enough to force a shut down. Then try the following steps.  Press the power button again and see if the Starling boots normally.  If not, then force a shut down again.  With the starling turned off, remove the battery pack and power supply.  Push the power button once and let the Starling sit for about 5 minutes.  Then re-install the battery, making sure that it clicks into place completely.  Plug in the power supply and then press the power button again.  Hopefully you will be greeted by a log in screen.  If not, since your Starling is still under warranty, contact System 76 customer support by clicking on this link, (with another computer, obviously):

[http://www.system76.com/articles.php?tPath=5](http://www.system76.com/articles.php?tPath=5)

I have purchased three laptops from this company and have been very impressed with their customer service.  Good luck, and welcome to the forum.

Joe

---

### Post by rdelfin on 2010-12-27
Hello JML & EJJ,

Not that I'm glad this happened to someone else, but I feel a little less anxious knowing that this has happened before to other people.

I'm in the middle of experiencing the very same thing described by JML:

I have the star3 model (the newest one), and everything was perfectly fine yesterday and then I got this notice by the UPDATE MANAGER program saying my system required to have some important updates installed.

After the packages were downloaded and installed, the system requiered to be restarted.   And the after that, the black screen with the blinking cursor in the upper left corner and nothing else.

I have tried doing exactly what EJJ has recommended, but it hasn't worked for me, I still get the black screen with the blinking cursor.

I did not bring my main laptop with me for the holidays I'm spending at my parents home, so I brought my Starling netbook instead so I can do my office work remotely via VPN and now I'm stuck with this problem, so any help that leads to a solution would be deeply appreciated.

I'm suspecting the issue arose upon the installed updates.

Is there any other solution I should be trying now?  

Thank you again!!!
rdelfin   ;)

---

### Post by EJJ on 2010-12-27
It is fixed!
Thanks to Ian at System 76 for his support (their customer service is wonderful!)


If anyone else is having this problem-it resides potentially in the Grub Bootloader. The theory was that my machine locked up during an update for this-thus it never went through the process properly and had a problem rebooting.

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

Follow that to fix it.

If you're running 10.04 (which system 76 recommends) you should use that for the process. And obviously if you have a netbook and no external cd drive-you'll have to create a usb flash drive.

---

