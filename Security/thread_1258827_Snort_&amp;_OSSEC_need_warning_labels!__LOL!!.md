---
title: "Snort &amp; OSSEC need warning labels!  LOL!!"
date: 2009-09-05
forum: Security
---

### Post by Lori700698 on 2009-09-05
I have both finally installed and they should have waring labels: "Caution, you will be up all night the first day of installation"  I got locked out around 10 times until I figured out I needed to white list my laptop's internal address, and the sheer amount of activity is mind blowing.  I did find great relief in the white list for the /etc/int.d/snort file, after white listing my own IP most of the craziness stopped.   Now I have some questions:

1.  Is there a way to make base & ossec only accessible from inside the network? Example, Webmin = [https://server-name:1000](https://server-name:1000).  You can't touch this if the port is closed and you are not sitting here at my house.

2.  Can SSH & Squid be made to only accept certain IP's?  I'm guessing this could be done in the ITables, but I don't know enough about them yet to really be messing around.

3.  Does OSSEC freeze people if they are browsing your website (like I kept getting locked out while I was looking at the OSSEC & base pages before I whitelisted my IP?)

FYI, I'm still getting all kinds of attempted attacks on SSH, although many are being put in jail now.
Wow,what a ride this has been.  I didn't understand any of this before I got hacked!
Thanks for all the help!

---

### Post by bodhi.zazen on 2009-09-05
> **Lori700698 said:**
> I have both finally installed and they should have waring labels: "Caution, you will be up all night the first day of installation"  I got locked out around 10 times until I figured out I needed to white list my laptop's internal address, and the sheer amount of activity is mind blowing.  I did find great relief in the white list for the /etc/int.d/snort file, after white listing my own IP most of the craziness stopped.   Now I have some questions:

:lolflag:

> 1.  Is there a way to make base & ossec only accessible from inside the network? Example, Webmin = [https://server-name:1000](https://server-name:1000).  You can't touch this if the port is closed and you are not sitting here at my house.

use iptables.

> 2.  Can SSH & Squid be made to only accept certain IP's?  I'm guessing this could be done in the ITables, but I don't know enough about them yet to really be messing around.

Yes. You can configure both and you can also use iptables =)

ssh is easier 

You can also use tcpwrapper (hosts.allow / hosts.deny).

[code]3.  Does OSSEC freeze people if they are browsing your website (like I kept getting locked out while I was looking at the OSSEC & base pages before I whitelisted my IP?)

FYI, I'm still getting all kinds of attempted attacks on SSH, although many are being put in jail now.
Wow,what a ride this has been.  I didn't understand any of this before I got hacked!
Thanks for all the help![/quote]

Yes, if you have false positives from either snort or ossec people will be locked out.

You really need to watch your logs.

---

### Post by phillw on 2009-09-05
Dunno about squid, but SSH can be locked down to IP's - doesn't really help you if someone spoofs the IP. (No, I am not going into what is & isn't possible in spoofing, except that it can be done)

Follow Bodhi Zazen's tutorials on securing, and make sure you have SSH tied up so tightly that it can notice if you've passed wind near it.

One thing I have learned (the hard way), is that the system is set to repel all borders - it's us users (yeah, we can call our-selves wannabe admins) who mess it up !!!

Have fun, well - we are supposed to be able to :popcorn:

Phill.

---

