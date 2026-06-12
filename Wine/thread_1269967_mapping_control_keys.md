---
title: "mapping control keys"
date: 2009-09-18
forum: Wine
---

### Post by hhoyt on 2009-09-18
Wine 1.0.1

I am running a radio ham logging program successfully under wine (TR4W).

The problem I have is that the program expects some functions to be controlled by, say, the 
CTRL-A key sequence (in Win32) and I have been unsuccessful in figuring how to get wine to translate (if possible).

Specifically, in TR4W, a sequence can be sent to the program to talk to a second radio. 
The command is built as a text file that TR4W reads. The actual text "CQ TEST \\' works perfectly.
--Problem is that text may be prefixed with commands. For example CTRL-A stipulates to send the command to the second radio.
How to get wine to translate this ?

Is something like this possible ?

TIA, Howard

---

### Post by hhoyt on 2010-08-30
TR4W now handles this for the user.
<03>SWAPRADIOS<04>CQ
or <01>CQ

---

