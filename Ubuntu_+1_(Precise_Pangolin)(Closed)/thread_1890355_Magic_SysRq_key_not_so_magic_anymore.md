---
title: "Magic SysRq key not so magic anymore?"
date: 2011-12-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2011-12-03
This is something I've noticed for quite some time, both in Oneiric and Precise. Also in both Ubuntu and Lubuntu.

For as long as I can remember I've used Alt > SysReq > K to restart X or log out, and of course Alt > SysReq > REISUB (or sometimes just "B") to reboot if things are unresponsive other than the keyboard.

Now it seems like kind of a crap shoot now, sometimes it works and sometimes it doesn't. Anyone have any info about that :confused:

I've checked in "/proc/sys/kernel/sysrq" and it's set properly. I just wonder what's up :)

---

### Post by Jordanwb on 2011-12-03
I've noticed that too. Not working for me.

---

### Post by JRV on 2011-12-03
It works for me. (64 bit)

I wish they would re-enable <CTRL><ALT><BACKSPACE>.

---

### Post by coffeecat on 2011-12-03
> **kansasnoob said:**
> Now it seems like kind of a crap shoot now, sometimes it works and sometimes it doesn't. Anyone have any info about that :confused:

It's worked for me, but I've only tried it once so far. Fresh install of Pangolin alpha 1 on this laptop, just booted up and typing in the WPA key for wireless and the mouse cursor disappeared. So I AltGr+SysRq+k to get back to the login screen. (Mouse cursor reappeared).

I'll try it a few more times to see if it is consistent or inconsistent. Are you using Alt or AltGr? Some keyboards/systems I've tried only work with the AltGr key.

**EDIT**: seems consistently OK for me. Just did AltGr+SysRq+k and then Alt+SysRq+k and both took me to the login screen. I'm running 64-bit.

---

### Post by kansasnoob on 2011-12-03
Right now it's working OK on both of my boxes in Precise but I repeated some Oneiric testing of my "classic DE" venture to try and determine what exact package update changed the need to edit "/usr/lib/lightdm/lightdm-set-defaults" and it was messed up, so I'm thinking it may be a Oneiric kernel thing.

I'm thinking it's something we need to watch for in Precise and if it appears then we need to try and figure out if it's the kernel by reverting to the last kernel etc, etc. I know I'll be checking from time to time :D

Right now I'm amazed at how stable this Alpha 1 is, but also fearful of what's to come. I do see a lot of effort being made to fix bugs ATM - more than I've ever seen.

---

### Post by effenberg0x0 on 2011-12-04
Sysrq is enabled / disabled here:
```
sudo cat /proc/sys/kernel/sysrq
```or via sysctl, one can check with:
```
sudo sysctl -A | grep -i sysrq
```So one can auto-enable at boot adding this to init in a way that only will be enabled when the default user is logged (put it on a script inside $HOME owned/chmod you:you and use init to check $USER)
```
if [ $(cat /proc/sys/kernel/sysrq) -ne 1 ]; then echo 1 | tee /proc/sys/kernel/sysrq; fi
```Or brute-force it with sysctl. But it's gonna be temporary unless set to sysctl.conf. 
```
sudo sysctl kernel.sysrq=1 
```If it's disabled, it usually is done via sysctl conf files. So check /etc/sysctl* to find where is being done and edit/comment it, if any occurrence is found:
```

sudo grep -iHnr "sysrq" /etc/sysctl*
```
Not sure if it's been done for PP, but it is considered to be a good security setting to disable sysrq completely, so root can enable it using other ways only for admin users. Many implementations disable it.

---

### Post by MacUntu on 2011-12-04
> **JRV said:**
> I wish they would re-enable <CTRL><ALT><BACKSPACE>.

Why? Those who need it can enable it themselves.

---

### Post by kansasnoob on 2011-12-05
ATM this seems to be working great in Precise, but it is inconsistent in Oneiric.

So I'm marking this solved and I'll watch for further trouble in Precise :)

---

### Post by seeker5528 on 2011-12-05
> **JRV said:**
> It works for me. (64 bit)

I wish they would re-enable <CTRL><ALT><BACKSPACE>.

If you want to implement the setting system wide, create an 'xorg.conf' file (assuming you don't already have one) in '/etc/X11' and add the following text to it```
Section "InputClass"
    Identifier          "Keyboard Defaults"
    MatchIsKeyboard     "yes"
    Option              "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection

```

If you already have an 'xorg.conf' file, make sure the relevant lines are added.

If you want to implement the setting in a user specific way create a file named '.xprofile' in your home directory with the following line of text ```
setxkbmap -option terminate:ctrl_alt_bksp
```

Later, Seeker

---

