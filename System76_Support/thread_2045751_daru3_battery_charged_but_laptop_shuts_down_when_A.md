---
title: "daru3 battery charged but laptop shuts down when AC adapter is removed"
date: 2012-08-21
forum: System76 Support
---

### Post by Cicer on 2012-08-21
Hi guys, my daru3 has been cruising along until a recent power supply problem. I normally get about 2 hours to a charge but recently, after using up most of the battery power, shutting down, and recharging, the laptop stopped powering up unless the ac adapter was plugged in. If the AC adapter is removed, the laptop shuts down immediately.

Here's where the system says my battery is:
```
user:~$ cat /proc/acpi/battery/BAT0/*
alarm:                   unsupported
present:                 yes
design capacity:         2400 mAh
last full capacity:      1595 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
cycle count:		  0
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M720T/M730T
serial number:            
battery type:            LION
OEM info:                Clevo Co.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      1595 mAh
present voltage:         14800 mV

```

After looking [here]("http://askubuntu.com/questions/27065/brand-new-battery-is-100-charged-but-at-0-capacity?rq=1") and [here]("http://ubuntuforums.org/showthread.php?t=1602758") it sounds as if there could be a hardware problem in the battery or in the AC adapter.

Has anyone else had this problem? Any ideas of what I could do to look into it further?

---

### Post by isantop on 2012-08-23
> **Cicer said:**
> Hi guys, my daru3 has been cruising along until a recent power supply problem. I normally get about 2 hours to a charge but recently, after using up most of the battery power, shutting down, and recharging, the laptop stopped powering up unless the ac adapter was plugged in. If the AC adapter is removed, the laptop shuts down immediately.

Here's where the system says my battery is:
```
user:~$ cat /proc/acpi/battery/BAT0/*
alarm:                   unsupported
present:                 yes
design capacity:         2400 mAh
last full capacity:      1595 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
cycle count:		  0
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M720T/M730T
serial number:            
battery type:            LION
OEM info:                Clevo Co.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      1595 mAh
present voltage:         14800 mV

```

After looking [here]("http://askubuntu.com/questions/27065/brand-new-battery-is-100-charged-but-at-0-capacity?rq=1") and [here]("http://ubuntuforums.org/showthread.php?t=1602758") it sounds as if there could be a hardware problem in the battery or in the AC adapter.

Has anyone else had this problem? Any ideas of what I could do to look into it further?

Try reseating the battery. It may have been jostled loose.

---

### Post by Cicer on 2012-08-24
No luck with jiggling.

---

### Post by jbelmonte on 2012-08-24
> **Cicer said:**
> No luck with jiggling.

I'm not sure just jiggling is the same a re-seating. Try:

1.  Shut down and turn off the laptop
2.  Unplug
3.  Remove the battery
4.  Inspect the connections and clean/blow out any debris/dust
5.  Put the battery back in making sure it is properly seated
6.  Make sure that the lock tabs are set.
7.  Let us know if this helps.

---

### Post by Cicer on 2012-08-27
> **jbelmonte said:**
> I'm not sure just jiggling is the same a re-seating. Try:

1.  Shut down and turn off the laptop
2.  Unplug
3.  Remove the battery
4.  Inspect the connections and clean/blow out any debris/dust
5.  Put the battery back in making sure it is properly seated
6.  Make sure that the lock tabs are set.
7.  Let us know if this helps.

That's what I meant by jiggling :) No luck reseating. I suppose the next thing to do would be to test another adapter and another battery, if I can find them.

---

### Post by Cicer on 2013-01-08
Well, it seems that the problem was the logic board, not the battery or the adapter. At least that's what the repair shop said when I brought it in after the dartur ultra finally died last night. It now attempts to start and then fails after 15 seconds or so. I thought that it was the adapter at first, but a multimeter showed it to be working fine. The laptop lasted just over 4 years, which is kind of a bummer--it was fine for my uses and I had hoped it would hold me for another couple. On the other hand, it did a great job and made getting into ubuntu easy.

---

