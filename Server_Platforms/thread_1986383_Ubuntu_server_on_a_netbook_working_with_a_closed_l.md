---
title: "Ubuntu server on a netbook working with a closed lid"
date: 2012-05-24
forum: Server Platforms
---

### Post by funenga on 2012-05-24
Hello,
I don't know if this is the right place to ask for support about this. If not, please tell me where to post.

I decided to use my *eeepc 1001HA* as a home server. I have connected it throw wifi to the router, running *UbuntuServer12.04*. Everything works fine except this annoying problem:

**when I close the lid, the ssh server stops working and, I guess, wlan0 too.**

Tried the BIOS and nothing, no option about the lid. My wlan0 is a *RaLink RT3090*.

Tried "ls -lrt /var/log" bettween lid derivatives, but I can't understand those satanic logs. I can share them if needed.

*pm-powersave.log* seems to be updated between lid movements. So I guess I've to disable this "powersave" mechanism. Can I do this? I don't want the wireless adapter to turn off.

Remeber that there is no UI, this is a netbook with a lid and its connected to the ac adapter.

Filipe Funenga
Lisbon PT

---

### Post by papibe on 2012-05-24
Hi funenga.

I have accomplish that with a Toshiba Satellite laptop.

What did the trick for me was WOL. I manage to turn on the laptop using wake-on-lan while the lid is closed, and it worked perfectly.

Just am idea.
Regards.

---

### Post by funenga on 2012-05-25
Thanks for the idea!

I have not used WOL (in my case would be [WoWLAN]("http://en.wikipedia.org/wiki/Wake-on-LAN")) but I've clicked the power-button and immediately closed the lid. It works with the lid closed, that's all I want.

Now I just hope the server don't enters the suspend mode, or something like that, for power saving. (edit: it does :()

Filipe Funenga
Lisbon PT

---

