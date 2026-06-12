---
title: "3G-modem (ZTE MF190J) still requires manual tweaking."
date: 2013-01-29
forum: Ubuntu Development Version
---

### Post by moma on 2013-01-29
Hello,
I have a 3G-modem of type ZTE MF190J. It works very well in Ubuntu 12.10 and 13.04 after I add or modify these two files.

1) 
$ [COLOR="DarkGreen"]sudo gedit /etc/usb_modeswitch.d/19d2:1542 [/COLOR]

```
# ZTE MF190J
DefaultVendor= 0x19d2
DefaultProduct= 0x1542

TargetVendor=  0x19d2
TargetProduct= 0x1544

MessageContent="5553424312345678000000000000061e000000000000000000000000000000"
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000"
NeedResponse=1
```

2) Added one line to /lib/udev/rules.d/40-usb_modeswitch.rules (just below the last ZTE line): 

$ [COLOR="DarkGreen"]sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules[/COLOR]
```
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1542", RUN+="usb_modeswitch '%b/%k'"
```

Will these changes become part of the final Ubuntu 13.04? 
I had still edit the files manually in Raring 13.04 (daily test).

Detailed instructions and facts about the 3G-modem: 
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=4&t=1100&p=7109](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=4&t=1100&p=7109)

---

### Post by dino99 on 2013-01-29
if no one report that issue (and your tweak), then its an unknown issue and so will not be fixed :(

ubuntu-bug linux

---

### Post by moma on 2013-01-29
Ok, I will file a bug-report.
Actually, I think the /lib/udev/rules.d/40-usb_modeswitch.rules file was already updated with right data (by default). I need to re-install 13.04 and check the files.

---

