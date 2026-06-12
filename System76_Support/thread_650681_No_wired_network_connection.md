---
title: "No wired network connection"
date: 2007-12-26
forum: System76 Support
---

### Post by ewg on 2007-12-26
System 76 Sable
Ubuntu 7.10

After no problems for several months, I can no longer get my wired connection consistently. Sometimes it's there, sometimes it's not. When it's not there, the button for it is grayed out in the network manager box.The wireless works fine. Any suggestions?

Thanks,

---

### Post by thomasaaron on 2007-12-27
Check your /etc/network/interfaces file against these instructions:

---------------------------------------------------------------------------------------

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

### Post by ewg on 2007-12-28
Thanks for your response. I checked the interface file but it was already set up as you suggested. I did save it again and reboot. Still no wired connection.

Re your NOTE: I have always used the network manager for connecting. Actually it had always just started automatically. Now the 'little computer" icon doesn't even display. All I get is the wireless status bars. When I open the manager, the wired connection choice is grayed out.

Thanks,

---

### Post by thomasaaron on 2007-12-28
For efficiency's sake, I'll give you a number of things to try. What kind of ouput/results do you get from each? Then, we can home in on whatever seems to be the best lead.

1. Is there a way to confirm that you are actually getting a wired signal from your cable? Can you check it with another computer? (You definitely want to be thorough with this one, as no other tests will be helpful if you don't have a signal anyway :)) Check connections from modem to router to computer, etc... making sure they are tight.

2. Try restetting Network Manager. First right-click on the icon, then enable networking and disable wireless networking. Then:
sudo /etc/dbus-1/event.d/25NetworkManager restart

3.Try these commands from a terminal:
sudo ifdown eth0
sudo ifup eth0
Do you have wired connectivity now?

4. Try pinging your router. For a linksys, it would be something like...
ping 192.168.1.1

5. What is the output of:
ifconfig

---

### Post by ewg on 2007-12-28
Before your reply, I unplugged  all power cables and all modem & router connectors. I let everything alone for 20 minutes then reconnected all and it works. We have had no power disruptions lately so I no reason to suspect that. Sorry i did not try that before I posted.

Thanks for your help and Happy New Year to you and all at System 76!

EWG

---

### Post by thomasaaron on 2007-12-28
Glad you're up and running.

If it happens again, you might just try re-setting your router. There should be a little button on it somewhere to do this.

You'll probably have to reboot your computer afterwards.

Anyway, Happy New Year to you too.

Best,
Tom

---

