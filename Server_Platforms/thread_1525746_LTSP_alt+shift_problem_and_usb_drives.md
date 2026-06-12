---
title: "LTSP alt+shift problem and usb drives"
date: 2010-07-07
forum: Server Platforms
---

### Post by Hety on 2010-07-07
Hello everyone,

i ahve a problem with my LTSP setup. here is the deal: i installed LTSP 5 from 10.04 alternate CD. All works fine after i use nomodeset flag (omg took me while), but there is still one issue that bugs me. 

I dont actually start X , but instead use integrated rdesktop functionality of ltsp-client. My lts.conf looks like this:

```

[default]
        SCREEN_02 = ldm
        SCREEN_07 = rdesktop
        RDP_SERVER = 192.168.2.4
        RDP_OPTIONS = -f  -k ru-ru  -x l -r sound:local -5 -N
        LDM_DIRECTX = True

```All is fine, rdesktop starts and connects. BUT:

1. If i press alt, then shift, then release alt then release shift - i end up with toggled meta key. Which drives me mad, to be honest. if i press shift, then alt, then release shift then release alt i end up with toggled alt key. Which drives me just as mad as previous example. The meta key problem can be solved with xmodmap, but i dont run X. I just have full screen rdesktop, which means no xmodmap for me. Thats issue number one.

2. Number two. When i plug in USB drive using such config it is not visible on the host system - i guess another drawback of not running X. Any way to work around this?

I just hope there is someone here who dealed with such problems earlier, coz after week of banging my head against that wall i'm pretty exausted.

Thanks in advance.

P.S.: using raw keyboard fixes the issue number one (adding -y key to rdesktop) but disables lots of keys. If they can be reenabled that will be a solution.

P.S.S.: xmodmap -e "keysym Alt_L = Alt_L" fixes the issue if is invoked in a terminal in full gnome session and after that rdesktop is started. Is there any way to add it to autostart

---

### Post by Hety on 2010-07-08
The problem was solved by adding
```

xmodmap -display ${DISPLAY} -e "keysym Alt_L = Alt_L" >/dev/null 2>&1
```

ath the end of /opt/ltsp/i386/usr/share/ltsp/screen.d/rdesktop script.

Have fun :)

---

