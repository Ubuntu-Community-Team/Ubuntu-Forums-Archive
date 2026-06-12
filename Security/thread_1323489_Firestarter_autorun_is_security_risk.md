---
title: "Firestarter autorun is security risk?"
date: 2009-11-11
forum: Security
---

### Post by Limeni on 2009-11-11
I was googling alot lately about linux firewall, iptables and GUI tools to manage them.

I find Firestarter great and I wanted to autostart Firestart with system when i turn my computer on. And now im thinking... iptables are working with or without Firestarter, and Firestarter requires root privilages to run. So if you start and run Firestarter all the time you are on your computer then you are risking you seurity right? 

Im new to linux, correct me if Im wrong, please. Im used to M$ windows and i feal safe if there is firewall runing, right there where I can see him and be sure everything is ok. 

So, is it risky to have Firestarter opend all the time?

And btw, is there any good tool to monitor network traffic? But advanced one, I saw coupel of Screenlets but i would like what process is active and how big his upload and download are... yes, yes, Im control freak, cant help my self :D youst kidding, and some tool to monitor opend ports would be cool.

I really like Firestarter beacuse there i have it all, but is it safe tu run ti all day??

---

### Post by bodhi.zazen on 2009-11-11
Your reasoning is right on target, firestarter runs as root an you should not run it all the time.

Your firewall is iptables and firestarter is a gui front end to configure iptables, so if yo uuwe firestarter, configure your firewall and close the gui application.

FYI: The default configuration tool for Ubuntu is UFW, if you want a gui front end you can install gufw.

You do not need firestarter at all, simply open a terminal and enter:

```
sudo ufw enable
```

---

### Post by Limeni on 2009-11-11
> **bodhi.zazen said:**
> Your reasoning is right on target, firestarter runs as root an you should not run it all the time.

Your firewall is iptables and firestarter is a gui front end to configure iptables, so if yo uuwe firestarter, configure your firewall and close the gui application.

FYI: The default configuration tool for Ubuntu is UFW, if you want a gui front end you can install gufw.

You do not need firestarter at all, simply open a terminal and enter:

```
sudo ufw enable
```

Thanks!

---

