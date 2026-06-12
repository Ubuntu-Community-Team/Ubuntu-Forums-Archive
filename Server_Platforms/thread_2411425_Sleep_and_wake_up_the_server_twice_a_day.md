---
title: "Sleep and wake up the server twice a day"
date: 2019-01-30
forum: Server Platforms
---

### Post by markeworth on 2019-01-30
Hey everyone!

I have a Plex server and a file server at home. Most of the time the servers are in use in the morning and in the evening on weekdays. How can I schedule to sleep and wake up in a specific time twice a day? With a cron, I can send servers to sleep. Any solutions to waking up them? WOL is enabled and it works. I want to automate this process without using my phone for waking up both servers ;)

P.S. I have a TP-Link (supports OpenWRT) and Mikrotik routers. Maybe someone can recommend any solutions or scripts to use on my devices to make my idea come true?

Thanks

---

### Post by TheFu on 2019-01-31
Interesting question.  I could use something like this too, but my plex server is also the main NAS for the other 10+ systems on our network. It would be handy for some of the kodi players on r-pis, but I don't know if those support WoL. Hummmm.

For waking up any OS, only the BIOS can do that if you don't use WoL.

Did you google WoL with those devices?
* [https://openwrt.org/docs/guide-user/services/w_o_l/wol](https://openwrt.org/docs/guide-user/services/w_o_l/wol)
* [https://openwrt.org/docs/guide-user/services/w_o_l/etherwake](https://openwrt.org/docs/guide-user/services/w_o_l/etherwake)
* [https://wiki.mikrotik.com/wiki/Manual:Tools/Wake_on_lan](https://wiki.mikrotik.com/wiki/Manual:Tools/Wake_on_lan)  <--- I'd use this.

---

### Post by markeworth on 2019-01-31
> **TheFu said:**
> 
For waking up any OS, only the BIOS can do that if you don't use WoL.

Of course BIOS can do it, but once a day only :sad:

> **TheFu said:**
> Did you google WoL with those devices?

Please, sorry, I didn't google. But thank you for links ;)

---

### Post by volkswagner on 2019-01-31
I remember years ago dabbling in MythTV, I used [ACPI wake]("https://www.mythtv.org/wiki/ACPI_Wakeup") (to wake the server in time for recordings)

Perhaps you can adapt this to your needs with cron as the trigger.

---

### Post by TheFu on 2019-02-01
volkswagner, I tested this on my 16.04 modified chromebook laptop and it worked!
Very nice.  I didn't have to anything, just 
```
sudo bash -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"  # to reset any existing alarms
sudo bash -c "echo `date '+%s' -d '+ 5 min'` > /sys/class/rtc/rtc0/wakealarm"  # to wake in 5 minutes.
```

Looks like specifying the future time is flexible: 
```
date '+%s' -d '6 am tomorrow'
```

I use 'at' to schedule things in the future all the time. The same time methods work.
```
echo "/path/to/script"| at 6 am
echo "/path/to/script"| at now + 6 hours

```
Good for doing trivial things later, but not having to remember to actually do them.  Scheduled 'at' tasks survive reboots, shutdowns, whatever, but require the system actually be on at the instant the future job should run.

---

### Post by LHammonds on 2019-02-02
I use [TP-Link SmartPlugs](https://www.amazon.com/TP-Link-HS100-Required-Google-Assistant/dp/B0178IC734) for running all my Android TV Players at work.  Once the smartplugs are added to the Kasa app on your phone, you can setup an on/off schedule.  Since my machines can handle having power cut off, I just schedule power to turn on at 7:00am Mon-Fri and power off at 5:30pm Mon-Fri.

In your case, you could just set them up to power on at the times you want and have a crontab schedule on your servers to gracefully shutdown and poweroff when you want them to be off.

And yes, you can set multiple on/off schedules each day or manually control them with a click of a button.

LHammonds

---

