---
title: "Detect a Hacking Event?"
date: 2013-09-03
forum: Security
---

### Post by BuntuSeriously on 2013-09-03
Greetings!

OK.  I have a laptop install of 12.04 with all FW defaults in place (UFW just enabled); and was interested to know what primary log(s) I should look at from time-to-time to see if someone has attempted to hack into my system.  Just curious...

Also, is there a list somewhere that will (intelligibly) show which ports are open, and which services are listening at those ports?  Back in the day, I remember hardening XP with dozens of services tweaks courtesy of [Black Viper]("http://www.blackviper.com/") and others.  Is there an analogous procedure for 'buntu installs which aren't used in server scenarios?  In short, is this type of work necessary with the everyday distro, or will deviating from the default UFW settings create headaches for some home-user scenarios?

Thoughts?  Links?


Thanx --

---

### Post by Hungry Man on 2013-09-03
To see services connecting to the internet:
netstat -tuapw --numeric-hosts --numeric-ports

---

### Post by ventrical on 2013-09-03
> **BuntuSeriously said:**
> Greetings!

OK.  I have a laptop install of 12.04 with all FW defaults in place (UFW just enabled); and was interested to know what primary log(s) I should look at from time-to-time to see if someone has attempted to hack into my system.  Just curious...

Also, is there a list somewhere that will (intelligibly) show which ports are open, and which services are listening at those ports?  Back in the day, I remember hardening XP with dozens of services tweaks courtesy of [Black Viper]("http://www.blackviper.com/") and others.  Is there an analogous procedure for 'buntu installs which aren't used in server scenarios?  In short, is this type of work necessary with the everyday distro, or will deviating from the default UFW settings create headaches for some home-user scenarios?

Thoughts?  Links?


Thanx --

as always .. here is the Shields Up! kink.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by unspawn on 2013-09-03
> **BuntuSeriously said:**
> (..) what primary log(s) I should look at from time-to-time to see if someone has attempted to hack into my system.  
Please see [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security), [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) and [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned) and use Logwatch if you don't feel like grepping through log files manually. (Also see 'petit' for the more adventurous.)

---

### Post by BuntuSeriously on 2013-09-03
Good enough, and thanks all.

However, I found something interesting (at least to me at this juncture); and don't quite have enough of a handle on the syntax here to make heads-or-tails.

From ufw.log.1:

```

Aug 27 09:06:08 laptop1 kernel: [32818.256884] [UFW BLOCK] IN=wlan0 OUT= MAC={my_wireless_device_MAC}:{unknown_device_MAC} SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=11463 PROTO=2
Aug 27 09:06:11 laptop1 kernel: [32820.993489] [UFW BLOCK] IN=wlan0 OUT= MAC={my_wireless_device_MAC}:{unknown_device_MAC} SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=11465 PROTO=2
Aug 30 09:53:10 laptop1 kernel: [62026.569974] [UFW BLOCK] IN=wlan0 OUT= MAC={my_wireless_device_MAC}:{unknown_device_MAC} SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=1266 PROTO=2

```

If anyone has a moment, what does this signify; particularly the "mystery MAC" which I see in the original output?  Does the kernel number have any particular significance?

Is the dog's nose wet or dry???

Cheers; and thanks again :)

---

