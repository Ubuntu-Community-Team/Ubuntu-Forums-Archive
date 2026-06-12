---
title: "firestarter does not detect my ethernet connection"
date: 2009-03-31
forum: Security
---

### Post by nightshade209 on 2009-03-31
Hi all. I had firestarter installed previously, configured and runnin properly. However, since a couple of weeks or so, it has not been working. It shows firewall not running, and when i try to enable it, it says " the device eth0 is not ready. Please check your network device settings and that your internet connection is active." Also, when i tried checking my firewall settings using [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2), it failed my machine, saying that it was responding to PING. Pls tell me how to set up my firewall again.

---

### Post by hyper_ch on 2009-03-31
are you sure you need firestarter at all? I think you misunderstand what firestarter does.

---

### Post by bodhi.zazen on 2009-03-31
Although popular, firestarter is quite old and has not been maintained since 2005 and is starting to show it's age.

The default firewall in Ubuntu is now ufw.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

If you want a gui, user gufw (it is in the repositories).

I would ask, are you sure you even need a firewall ?

If so, I would purge firestarter and user ufw (or if you prefer gufw).

---

### Post by nightshade209 on 2009-04-02
> **bodhi.zazen said:**
> 
I would ask, are you sure you even need a firewall ?


> **hyper_ch said:**
> are you sure you need firestarter at all? I think you misunderstand what firestarter does.

I am not sure what u are asking. I need firestarter in the sense that I need to set up my firewall. I do understand that the firewall will run in the background even if i am not actively running firestarter, but i do need it to get the firewall set up in the first place, right?

---

### Post by hyper_ch on 2009-04-02
why do you think you need a firewall?

---

### Post by bodhi.zazen on 2009-04-02
> **nightshade209 said:**
> I am not sure what u are asking. I need firestarter in the sense that I need to set up my firewall. I do understand that the firewall will run in the background even if i am not actively running firestarter, but i do need it to get the firewall set up in the first place, right?

Firewalls are a tool. Most people run Ubuntu as a desktop and are behind a router.

A default installation of Ubuntu has no open ports and therefore there is nothing to firewall.

So the question is , what are you using a firewall for ? Or are you using it because it was part of Windows security ?

By default, windows has a number of documented and undocumented open ports, so on Windows you need a third party firewall as a part of security. This is not necessarily the case with Ubuntu for reasons stated above.

---

### Post by nightshade209 on 2009-04-03
Ya, i guess since i have recently migrated from Windows, that might be why i feel the need to have a firewall. But the Ubuntu documentation also advises having one...
[https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html)

---

### Post by hyper_ch on 2009-04-03
how do you connect to the itnernet?

---

### Post by bodhi.zazen on 2009-04-03
> **nightshade209 said:**
> Ya, i guess since i have recently migrated from Windows, that might be why i feel the need to have a firewall. But the Ubuntu documentation also advises having one...
[https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html)

No it does not :

> You can optionally install a firewall

---

### Post by nightshade209 on 2009-04-04
> **hyper_ch said:**
> how do you connect to the itnernet?

Ethernet connection, broadband

---

### Post by nightshade209 on 2009-04-04
> **bodhi.zazen said:**
> No it does not :

Ok, admittedly, ubuntu does not REQUIRE a firewall, but i would still like to have one. And besides, tht does not answer my original question. Why did firestarter suddenly stop working when i having changed any of my internet connection settings after the intial setup?

---

### Post by brian_p on 2009-04-04
> **nightshade209 said:**
> Ok, admittedly, ubuntu does not REQUIRE a firewall, but i would still like to have one. And besides, tht does not answer my original question. Why did firestarter suddenly stop working when i having changed any of my internet connection settings after the intial setup?

What detected devices does the firewall wizard think you have. Only eth0?

ufw will also configure a firewall. As a matter of interest, would it not be a suitable alternative to use?

---

### Post by nightshade209 on 2009-04-04
> **brian_p said:**
> What detected devices does the firewall wizard think you have. Only eth0?

ufw will also configure a firewall. As a matter of interest, would it not be a suitable alternative to use?

It detects eth0, pan0, ppp0. BTW, i managed to get it working again. I had to change the detected device from eth0 to ppp0. Can someone explain to me why that is so? Since it was working properly with eth0 selected previously?

---

### Post by brian_p on 2009-04-05
> **nightshade209 said:**
> It detects eth0, pan0, ppp0. BTW, i managed to get it working again. I had to change the detected device from eth0 to ppp0. Can someone explain to me why that is so? Since it was working properly with eth0 selected previously?

Without a detailed knowledge of the way networking is set up on your machine and any changes made it is difficult to say. The firestarter mailing list is probably your best bet of tracking down a reason for this behaviour.

---

### Post by hyper_ch on 2009-04-05
I guess you connect through a router to the itnernet. You should then rather setup the router.

---

