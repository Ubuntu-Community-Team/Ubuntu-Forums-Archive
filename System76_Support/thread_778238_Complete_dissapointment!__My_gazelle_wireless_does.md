---
title: "Complete dissapointment!  My gazelle wireless does not work!"
date: 2008-05-01
forum: System76 Support
---

### Post by weverjames on 2008-05-01
It was working fine with festy.  Now it does not work with hardy.  It is not a problem unique to me.  However system 76 people have not given a resolution to this problem (I am seeing other similar posts).
What can I do with a laptop that is not able to connect wireless internet.
This is very sad.  I invested in it for my work.  What am I going to do?](*,)](*,)

---

### Post by Tart on 2008-05-02
Have some patience. You rushed with upgrade, it is expected that newly released OS will have some bugs. People are working hard on fixing them. I'm sure system76 staff are doing all they can to resolve those issues. As they say, early adopters always get screwed.

---

### Post by thomasaaron on 2008-05-02
You said it was working fine under Feisty. Can I assume, then, that you did a fresh install of Hardy (as opposed to upgrading to Gutsy and then upgrading to Hardy)?

Please provide more information to us:

1. Can you see your wireless access point? If not, double check your wireless switch on the leading, left edge of your Pangolin. It should be toggled to the right.
2. If you can see the access point but cannot connect to it, please send me the output of this command...
cat /var/log/daemon.log > ~/Desktop/daemon.log.txt
...after a failed connection attempt.
3. Tell me more about your wireless configuration.

Also, just to make sure your interfaces file is correct, please follow these directions. It could even fix the problem.

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

---

