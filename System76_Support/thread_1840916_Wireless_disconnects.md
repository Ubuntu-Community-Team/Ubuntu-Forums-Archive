---
title: "Wireless disconnects"
date: 2011-09-08
forum: System76 Support
---

### Post by Carleas on 2011-09-08
Star4 running 11.04.  I am not super savvy, to say the least.  I regret my inanity.

I'm having a problem where I'm able to connect to wireless, but after a variable period I lose connection and can't reconnect.  However, if I restart my computer, I reconnect immediately and at full strength.  The problem is only using wireless.

I would like to solve this problem, but in the interim it would be a big improvement if I could restart only those parts of the system that need to be restarted.  Is there a way to restart the wireless process without the rest?  [Another thread]("http://ubuntuforums.org/showthread.php?t=1372464") suggested
```
$ sudo killall NetworkManager
```
Is that safe?  Is it reasonable? :confused:

---

### Post by osx424242 on 2011-09-08
(FYI, I'm not a System76 employee)

> **Carleas said:**
> ```
$ sudo killall NetworkManager
```
Is that safe?  Is it reasonable? :confused:

That should be reasonably safe, although keep in mind it's only a temporary workaround.  It'll be handy in the short term, but really you'd be better off figuring out and fixing the problem.  When I was having network problems (I was having a lot of trouble with a balky RealTek chipset that I eventually gave up on and replaced) I often restarted Network Manager, although instead of using 'killall' I'd recommend using the command: ```
sudo service network-manager restart
```.  That will allow Network Manager to stop and restart itself normally, using the init scripts provided for that purpose (you can look at the script if you're interested, it should be /etc/init.d/network-manager, but I'd strongly recommend that you avoid trying to modify it!).

If I remember correctly, though, that only worked some of the time.  Sometimes I also had to remove the driver module and modprobe it again, and sometimes even that didn't work and I ended up needing to restart the computer anyway.  I hope your issue isn't as severe!

---

### Post by Carleas on 2011-09-08
I just tested ```
sudo killall NetworkManager
``` because I couldn't get on to check responses to this thread!  It worked, but I agree that it's no ideal.  What steps can I take to diagnose this problem?  Is there a log you'd recommend monitoring?  Are there tests I can run while it's locked up that will give me some hint?  

I sure hope there's no driver module removal needed, I don't even know what that means!

A little further information:  when the wireless gets locked up, I can detect the network, but I can't connect to it.  It may read a weaker signal before I disconnect, and the icon in the upper right indicating the signal doesn't indicate that I've disconnected until after webpages and ping stop working and I've tried to reconnect.

Also, when I try to use ping, it doesn't tell me I'm not connected, at least not that I've seen.  It seems to just run and run, never returning any results. (using ping is the extent of my highly sophisticated diagnostic repetoire, I'm hoping someone can help me expand it!;))

---

### Post by ktmhz on 2011-09-09
I was having the same problem on my star4, and no amount of restarting network manager or modprobing the driver would get my internal realtek to reconnect. Only restarting the machine would fix it (sometimes for as little as a couple of minutes). It worked fine before, but I moved a couple of weeks ago and it doesn't seem to get along with the router we have here. I ended up ordering a TP-LINK TL-WN722N for $15 (on the recommendation of another starling wireless failure thread) which has been working flawlessly for the past 3 days. I wish system76 had been more helpful when I posted about this a couple of weeks ago, it seems like the wireless on a netbook ought to just work (like how the TP-Link just works with 11.04). If you don't mind carrying around a usb wireless adapter, I would recommend that. One quirk is that fn-f11 doesn't just disable the internal realtek, but disables all wireless networking, which is a hassle since I don't want the unreliable realtek trying to connect and screwing things up anymore. I got around this by blacklisting the realtek in /etc/modprobe.d/ 

A fix for the realtek would really be ideal, though.

---

### Post by mapman88 on 2011-09-10
Hi,I hope it's ok to butt in....I just purchased a gazp6, and I was in a hotel room the first day doing my fantasy football draft, and about 20 minutes in I started losing my connection. No indication of what was going on, I stopped and started Firefox a few times with not much success.

 Now I am at home and wireless is very slow, although I don't think it is disconnecting. I hooked up to my router using a cable and internet is much faster. Is there a way to monitor what my connection speed is? How do I tell if it is the computer wireless or the network.

---

