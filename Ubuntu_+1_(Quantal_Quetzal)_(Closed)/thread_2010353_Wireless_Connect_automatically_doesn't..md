---
title: "Wireless Connect automatically doesn't."
date: 2012-06-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-06-25
>  Re: QQ Changes & Updates - Alpha 2 pre testing.
Sorry I missed this in my emaills. From Nick Skaggs.

The Alpha Two milestone will be released next Thursday. Starting today, I am issuing a call to everyone to take a moment this week and test your favorite iso using the daily image. Be sure and record your results (and bugs) if any.

Starting next Monday the first images will be generated for the milestone and we'll begin milestone testing
This is Monday, the 25 June daily build of i386.iso is a royal pain to get wireless WPA connected.  Bug #1015096.  Regression compared to Precise on the same hardware which actually does connect.

System Settings network doesn't show the network.  Network applet edit wireless security refuses to select and show the menu.  Very strange since the 25 June live would allow selecting the menu.

Bounce back and forth between Systems Settings network and network applet edit and it finally connects.  Some time after connecting the Systems Settings Network finally shows the network.

Any way to trace what Ubuntu network code is doing for minutes on end at 1.66 gHz?

Thanks, Jerry

---

### Post by jerrylamos on 2012-06-25
Wireless running, did a reboot.

First thing Ubuntu Quantal did on booting up was "disconnect" even though "Enable Wireless" and "Connect Automatically" are both selected.

Tried doing anything to Network applet edit menu, and System Settings Network.  No luck.

Finally after 9 minutes network decided to wake up.

Network controller: Intel Corporation Centrino Wireless-N 1000

So far this milestone is a stone.

Jerry

---

