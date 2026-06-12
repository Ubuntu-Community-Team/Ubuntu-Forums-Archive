---
title: "Starling Had Wifi, then lost all network connectivity"
date: 2009-12-08
forum: System76 Support
---

### Post by hilde45 on 2009-12-08
**System 76 Starling Had Wifi, then lost all network connectivity**                                                                             I got my Starling System 76 netbook today. Started it up and had good luck with my wifi. I saw that updates were available and I did them. They took about 14 minutes and I don't believe I did upgrade to 9.10 Karmic. I am still at 9.04 Jaunty.

Tried to troubleshoot the problem, by flicking switch on front and rebotting. No wifi. Next, I hooked the Starling directly up to my cable modem via ethernet cable, but could not connect to the internet using a WIRED connection. I saw the eth0 option, selected it, it spun for a while in "connecting" mode, then gave me a "no connection X icon."

Next, I tried to create a new wired connection in the preferences for Networking. No connection. Further reboots/restarts have not enabled an internet connection, either wired or wireless and I am at a loss about what to do.

So, in sum: Starling netbook, out of the box, wireless internet fine. Update software but not to Karmic, ALL internet broken.

I really want to love this thing but a netbook with no wifi is hardly loveable!

Your help appreciated, really, truly, deeply.

In Denver, BTW.

---

### Post by thomasaaron on 2009-12-08
Please see...
[http://ubuntuforums.org/showthread.php?t=1330531](http://ubuntuforums.org/showthread.php?t=1330531)

---

### Post by smulloni on 2009-12-08
I was helping the author of this post troubleshoot a bit over the phone, so I'll answer for him -- he has a brand new Starling with Jaunty.  He did *not* upgrade to karmic.  When he couldn't get even a wired connection, much less a wireless one, to work again, I didn't know how to help him, so I hope you can, Tom!

---

### Post by smulloni on 2009-12-08
(In my reply above, I misunderstood what part of your message was the sig and what wasn't.)  As for the thread you link to, we weren't able to follow the wireless troubleshooting instructions there, because of the difficulty getting a wired connection.

---

### Post by hilde45 on 2009-12-08
The following actions fixed the wifi. Thanks to Tom and System76 for their blazingly fast and effective response.

First...
--------------------------------
To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
You *should* now be able to establish a wired connection.
--------------------------------

Once that is done...

--------------------------------
Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.

---

### Post by Bromo on 2009-12-12
Hmmmm .... my system broke last night - after update.

I lost WiFi, but wired worked OK.  I updated System76 driver. rebooted.  Then toggled switch (Wifi to the right ONCE, or so I thought) and rebooted.  WiFi light was off.

I carefully toggled the switch ONCE and then did a full reboot (not "restart" but "Shut down" and then powered up after a a minute or so).  When it rebooted the light was on.
Mine was a Starling, 9.04 as shipped (got it a couple of weeks ago - star1).

I don't know if this makes a difference, but I did a cold reboot and it all started working, though I did 2 things (cold reboot AND a careful single WiFi switch) if that makes a difference.

So ... 

1. Established wired connection (wired didn't break)
2. Updated System76 driver & reboot (restart)
3. Toggled the WiFi spring switch ONCE and ONCE only, and System "Shut Down"
4. After about 30 seconds to a minute started computer and saw WiFi light was on.


Thank you System76! :D

---

### Post by Streacker on 2009-12-13
I recieved my new Starling (star1) a week ago. I'm new to Ubuntu and new to the open source community.
 
I ran updates (didn't upgrade to 9.10) and am experiencing the exact same problem with network connectivity as hilde45. 
 
I've read the other thread on the 9.10 problem: [[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=1330531[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1330531")
 
I followed hilde45's instructions on this thread to fix the wired and wifi connections with no luck.
 
1) fixed /etc/network/interfaces file - when I opened this file in the terminal the only two lines in the file were:
 
auto lo
iface lo inet loopback
 
...so nothing to fix with the file I presume.
 
2) I rebooted (tried restart and cold start multiple time) and have not been able to establish a wired connection. I've got a cable modem hooked up to a wireless router. My desktop (using the wi-fi) has a connection, so I know my cable modem is working fine. When I disconnect the ethernet cable from the wireless router (coming from the cable modem) and plug it into my Starling, the networking icon at the top right spins as it tries to establish the connection, but eventually stops and tells me it can't make a wired connection.
 
Can't do much else without the wired connection.
 
I would really appreciate the help to get this fixed.
 
I really love this little netbook and can't wait to get things back to normal with it.
 
Thanks

---

### Post by thomasaaron on 2009-12-14
Please give me a call at your convenience, and we'll get it figured out.

---

### Post by Streacker on 2009-12-15
Thanks Tom. All fixed!!
 
The problem with my wired connection was a simple mistake I was making with the ethernet cable connections between my modem --> router --> Starling (a very novice mistake I'm sure). Thanks for being patient with me Tom.
 
Once System76 helped me correct that mistake, the directions hilde45 provide in this thread to fix the wireless connection work as advertised.
 
Thanks all!

---

