---
title: "wifi--again"
date: 2007-11-14
forum: System76 Support
---

### Post by ncappel1 on 2007-11-14
Hi again,
I just upgraded my gazp3 to Gutsy, it is great! I followed the official upgrade procedure then did a system76 driver upgrade, did a system restore with the driver, and everything works like a charm....except :)

The wifi (internet share from a mac) does not resume after a suspend. It works fine from a fresh boot. 
more details: 
*After suspend, on iwconfig will show eth0_rename as a wireless device with no essid or access point.
*iwlist scan shows the wireless network -- it is so close!!
*the network manager applet doesn't show any wireless options, only "wired connection" and "manual configuration..."

I have tried: 
*the how-to from the sys76 wiki about the network manager applet, everything it it was already done! 
*looking at other posts, didn't seem to find anything exactly similar...

any ideas?

Edit:
I also just noticed that anytime I try to shutdown or reboot the system, the progress bar stops right before the end, and will not powerdown. sysrq keys aren't responsive. only thing that works is pressing the power button down for 5 secs. I remember that both these problems were happening with my previous install of feisty, but they were solved. Should I just try a fresh install? It's going to be a pain to have to backup all my files!

---

### Post by thomasaaron on 2007-11-14
There are previous bugs that have been filed about wireless being broken after suspend. It might be worth trying some of those fixes. I'll try to hunt some down.

---

### Post by subbuss on 2007-11-16
I have created a shell script call 'netfixup' in my ~/bin/ directory which I run whenever I notice that the wi-fi network applet is acting funky.  I work with flaky wifi networks (at the coffee shop where I spend a few hours each day), and other places and sometimes when I come out of hibernate.  Additionally, when I come out of hibernate, the radio is off, and I have to turn it back on with Fn-F2.

The problems seem to be worse after I upgraded to Gutsy.  With Feisty, there were fewer problems.

---------------------
#/bin/sh

sudo killall -r NetworkManager
sudo rm /var/run/NetworkManager/Net*.pid
sudo /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
sudo /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
--------------------

Occasionally, the killall doesn't get rid of the NetworkManager process and I then do a ps -auxww | grep NetworkManager and kill the offending process with a kill -9.

Hope this helps.

subbu.

---

### Post by ImpressMe on 2007-11-16
Does it have to be Ubuntu/OS related? When I suspend or hibernate my PC I loose my internet connection somehow. The wireless connection with the router is fine, but the internet does not work (cannot lookup anything). I think the problem arises after the pc was suspended for more than just seconds. I have had this problem on Windows XP as well. Always have to reboot. 

Now and then I could reconnect to the wireless network and get it working, but that happened 1 out of 20 times. 

Did it ever work for you before? It really is annoying, I prefer to suspend my PC when I leave it.

---

### Post by ncappel1 on 2007-11-19
subbuss, thanks for the great script. It unfortunately didn't work for me. :(

After I run it, it successfully does what it is supposed to do (though I've also used your tip of ps -auxww | grep NetworkManager when not all the network manager processes were ended) but at that point I can't even see the network anymore in the dock applet or iwconfig.

edit: I was wrong, I can still see the network with iwlist scan, and when I call iwconfig, my device sees the network. no connection, though!

---

