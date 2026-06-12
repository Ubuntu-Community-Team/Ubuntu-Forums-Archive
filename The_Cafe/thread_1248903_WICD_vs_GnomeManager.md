---
title: "WICD vs GnomeManager"
date: 2009-08-24
forum: The Cafe
---

### Post by sefs on 2009-08-24
Hi there,

I used to use serialmonkey which was good for me.  When there rt73 division went bottom up, I moved to NetworkManger this was very very bad to me.  Low signal (50 - 75 percent), dropouts when playing tremulous, and no network access until I logged in first.

I discovered wicd and am very please about this little application.

Single a steady 94%, no dropouts when playing tremulous, and the network is up before I hit my desktop.

I just wanted to hear what people are using and if wicd is as it seems, light years ahead of GnomeManager.

And take the poll tool.

Thanks.

---

### Post by aesis05401 on 2009-08-24
Heya, 

I do everything via scripts because I mess with all sorts of virtual configs. 

You may want to reword the poll, though.  There is no Gnome NetworkManager.  The gnome interface is called nm-applet.  NetworkManager=RedHat, the gnome part just plugs in.

---

### Post by xpod on 2009-08-24
On my own Desktop i`m still using /etc/network/interfaces.
I began using it due to the problems Gnome Network Manager had with static ip`s a while back.I`ve just never bothered reinstalling it although i probably will when i upgrade the Desktop to karmic.
On this particular laptop,that does have Karmic installed, i am using the Gnome Network Manager again as it works just fine but i did use wicd with the previous installation of Jaunty.

Between the kids machines & mine there`s still a combination of all 3 so there was no point picking any particular one.We use what works best for us.

---

### Post by lswb on 2009-08-24
Just some random thoughts:

I use NM most of the time but occasionally have to disable it and use other tools to get a working connection.

In comparison with Network Manager, wicd is a very simple tool focused on working well with wireless adapters. I have certainly had issues with Network Manager myself and continue to have trouble in certain locations, that is why I keed the "rutilt" ap on my system. It can be installed without forcing the uninstallation of NM. It is also a very simple app focused on wifi and there are a few hotspots where it will work but NM won't. NM can be unloaded if necessary first, the exact command varies with which release & version you are running.

The developers of NM appear to be trying to make it a be-all, end-all solution to networking, and seem to have taken the approach of reinventing all the wheels of networking. They have made many improvements and added many features over the last year or 2 but some of the basics have yet to be solved. The lack of connection til there is a gui login is a big one, also recent versions cause trouble when more than one user is logged on to a single system. There are so many variations on networking that I am not sure their approach can ever be successful for 100% of all users.

---

### Post by Firestem4 on 2009-08-24
I personally use Wicd. It works, and works very well. I can't stand using NetworkManager. (Because of NetworkManagers inability to do some of the basic functions it should I actually had to resort to configuring /etc/network manually. I don't have a problem with it but its something NetworkManager should at least have been able to till I could replace it with Wicd).

On a side note do be aware that every program may use a different scale to determite how good of a Signal Strength an access point actually is. One scale in NM may say 50% while Wicd may say 90%. It just depends on how it was programmed but it doesn't really mean much. (I prefer to use dB rating for more accuracy rather than an interpreted scale)

---

### Post by ssam on 2009-08-24
NM has always worked for me on many machines. interface is nice and simple. i even use it to setup a static wired network, that needs to be brought up before login (so i can wake-on-lan the machine and ssh in).

i have a headless machine that still uses /etc/network/interfaces.

---

### Post by sefs on 2009-08-24
> **Firestem4 said:**
> I personally use Wicd. It works, and works very well. I can't stand using NetworkManager. (Because of NetworkManagers inability to do some of the basic functions it should I actually had to resort to configuring /etc/network manually. I don't have a problem with it but its something NetworkManager should at least have been able to till I could replace it with Wicd).

On a side note do be aware that every program may use a different scale to determite how good of a Signal Strength an access point actually is. One scale in NM may say 50% while Wicd may say 90%. It just depends on how it was programmed but it doesn't really mean much. (I prefer to use dB rating for more accuracy rather than an interpreted scale)

What impressed me is that with NM the frequent dropped connections, and with wicd no dropped connections.  I mean it could just be a good day, but I never had a good day with tremulous where NM was concerned.

---

### Post by qamelian on 2009-08-24
> **sefs said:**
> What impressed me is that with NM the frequent dropped connections, and with wicd no dropped connections.  I mean it could just be a good day, but I never had a good day with tremulous where NM was concerned.

I found just the opposite. On my laptop, no version of wicd has ever maintained a connection for more than 5 to 10 minutes. Network-manager, on the other hand, has always been rock solid for me.

---

### Post by hanzomon4 on 2009-08-24
I just want a working wifi connector Network Manager that does not need a gui... wpa_supplicant gives me a messed up password so I can't use it

---

### Post by slakkie on 2009-08-24
I haven't used wicd, and I haven't used network managers. I always configured my networks via the interfaces file. I believe that gives me more freedom and insight in how everything works.

---

### Post by &#32 Greg on 2009-08-24
> **hanzomon4 said:**
> I just want a working wifi connector Network Manager that does not need a gui... wpa_supplicant gives me a messed up password so I can't use it

[http://hg.horna.org.ua/wifi-select/](http://hg.horna.org.ua/wifi-select/)

---

### Post by calrogman on 2009-08-25
I use WICD because network manager wouldn't let me use a USB dongle while my laptops internal wifi card was turned off, I have since got it working using acerhk (which is getting removed from 9.10 but which is also the only way of turning on an iwl3945 with no radio switch) but haven't switched back to network-manager out of laziness.

---

### Post by hellion0 on 2009-08-25
I use Wicd on both of my laptops. While nm-applet is good for a wired connection, I'm not using it for wireless anymore, especially since one of my wireless cards has the rt2500 chipset.

---

