---
title: "[KALI LINUX] apt-get autoremove messed up everything"
date: 2014-03-31
forum: Ubuntu/Debian BASED
---

### Post by aaaaaaaaaa2 on 2014-03-31
Hello guys. Sorry if my english is not perfect
Last night I run the infamous lazykali script and asked it to update & clean kali.
This is what the script line does: 
```
 apt-get update && apt-get -y dist-upgrade && apt-get autoremove -y && apt-get -y autoclean
```

now everything is messed up: i have no network drivers anymore, and after rebooting the machine the GUI mode is gone too.
Looking into the web it comes out that **apt-get update --fix-missing** might fix the whole thing.
Is it true?

The problem with doing this is that I have no access to the internet whatsover. My laptop DOESNT have an ethernet access, so im trying to get it connected through the wifi.
Well I set the ESSID and its security key but when i run

dhclient wlan0

it gives me 
```
run-parts: failed to stat component /etc/dhcp/dhclient-enter-hooks.d/samba: no such file or directory
```

is there a possibile workaround despite from reinstalling kali?  I have another windows laptop with access to the internets and a usb drive.

regards paul

---

### Post by oldos2er on 2014-04-02
It would be best to seek help [here]("http://forums.kali.org/").

---

### Post by sam.nyx on 2014-09-25
use getback for re-install all autoremove packages 

Download this program [URL="http://github.com/codex8/getback"]

http://github.com/codex8/getback[/URL]

---

