---
title: "New Lemur with 16.04 factory installed"
date: 2016-04-26
forum: System76 Support
---

### Post by capemayal on 2016-04-26
1) Bluetooth mouse paired, but does not work.
2) wifi connects, FF  cannot find server ([www.Google.com](www.Google.com)).
4) Ethernet connects. Can't access server.

Right now, not impressed at all. Should I send it back?

---

### Post by Geoffrey_Arndt on 2016-04-26
Why not contact System76 and give them a chance to troubleshoot & provide advice?

---

### Post by DragonBoy on 2016-07-19
If it is factory installed and you have reinstalled anything. I would try the following:

Press "Fn" + "F11"

On my lemur the "F11" has a blue airplane on it. If you press "Fn" + "F11" you can toggle all the wireless/blue tooth access on and off.



If you need to restore or in the process of restoring your System 76 PC all the information is here:
[http://docs.system76.com/articles/restore/](http://docs.system76.com/articles/restore/)


sudo apt-add-repository ppa:system76-dev/stable
sudo apt update
sudo apt install system76-driver

Only do the nvidia install if you have nvidia card.
sudo apt install system76-driver-nvidia



You can all call the support team or web chat with them. They are very helpful.

---

### Post by capemayal on 2016-08-31
It's not that the bluetooth/wifi doesn't work, its that the bluetooth may or maynot connect, and if does connect, drops after a minute or so.  Wifi works fine.

---

### Post by Skaperen on 2016-09-02
what does *ping* and *traceroute* show (to places like 8.8.8.8)?

---

### Post by Geoffrey_Arndt on 2016-09-03
Re the mouse, . . . frankly, I wouldn't even spend 5 minutes on that mouse, and I'd replace it with something like the Logitech M325 (small mouse).    Have had at least 15 or so "wireless" Logitech mouses over the past 8-10 years on multiple PC's running Linux.   Not one failure or drop.

---

