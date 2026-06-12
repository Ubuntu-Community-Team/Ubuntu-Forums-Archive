---
title: "What if a full screen Gnome app didn't respond?"
date: 2009-09-19
forum: The Cafe
---

### Post by praveesh on 2009-09-19
If the app is not full screen, it is possible to close it using force quit applet in the Gnome panel. But if the app is full screen, there is no way of using force quit applet because the Gnome panel won't be visible. If it were kde, there is an idea . Alt+f2 , click on second button to get a list of all running applications . Select the unresponding application and click on kill. I don't know if it is possible in Gnome. I would like to know if there is any way to do that GRAPHICALY in Gnome .

---

### Post by Islington on 2009-09-19
Alt-f2
gnome-system-monitor
select process to kill


I generally just use xkill instead of going through the monitor.

---

### Post by PurposeOfReason on 2009-09-19
Switch workspaces.

---

### Post by j.bell730 on 2009-09-19
Alt+Tab > Terminal > killall <app-name>

---

### Post by hoppipolla on 2009-09-19
> **Islington said:**
> Alt-f2
gnome-system-monitor
select process to kill


I generally just use xkill instead of going through the monitor.

Yeah, why wouldn't Gnome's Alt+F2 work?

---

### Post by abhishek.malhotra35 on 2009-09-19
Lets say Alt + F2 stopped working when the application hanged. Then how should we kill the process. It has happened with me a few times.

---

### Post by Xbehave on 2009-09-19
if you can run a command pkill <app-name>, if you cant then ctrl+alt+F2 > login > pkill <app-name>

---

### Post by Paqman on 2009-09-19
Alt-F2 > xkill and click on the app. Job done.

---

### Post by PurposeOfReason on 2009-09-19
> **abhishek.malhotra35 said:**
> Lets say Alt + F2 stopped working when the application hanged. Then how should we kill the process. It has happened with me a few times.
Ctrl+alt+f1 and then ctrl+c.

---

### Post by yabbadabbadont on 2009-09-19
> **PurposeOfReason said:**
> Ctrl+alt+f1 and then ctrl+c.

Control+c won't do anything in that context.  Control-Alt-F1 (if it works) will drop you to a login at the text console.  You would have to then login and run something like "killall -9 <name of misbehaving program>" in order to kill it.  Then exit and finally hit Alt-F7 to (try to) return to your X windows session.

---

### Post by Bachstelze on 2009-09-19
And if it is X itself that hanged, SSH into your box. ;)

---

### Post by madjr on 2009-09-19
**KILLALL**

or use:

**URBASESBELONG2US**

---

### Post by PurposeOfReason on 2009-09-19
> **yabbadabbadont said:**
> Control+c won't do anything in that context.  Control-Alt-F1 (if it works) will drop you to a login at the text console.  You would have to then login and run something like "killall -9 <name of misbehaving program>" in order to kill it.  Then exit and finally hit Alt-F7 to (try to) return to your X windows session.
If you use xinit it works, I forget that he uses gdm.

---

### Post by spupy on 2009-09-19
For that reason the command
```
xkill -button 1
```
is bound as a shortcut Ctrl+WinKey+Q. I use it for all misbehaving programs, not just fullscreen ones. The philosophy of that program is zen-line: "Click the bad thing and it dies".

---

### Post by hoppipolla on 2009-09-19
> **madjr said:**
> **KILLALL**

or use:

**URBASESBELONG2US**

I second this approach. lol :)

---

### Post by praveesh on 2009-09-19
Some times , the whole system hangs up . Even the ctrl + alt +f1 doesn't bring a text only terminal . What to do ? It's not a rare case . In 50 % of the times , it's case

---

### Post by magmon on 2009-09-20
Ctrl alt backspace?

---

### Post by praveesh on 2009-09-20
> **magmon said:**
> Ctrl alt backspace?

that has been removed from Ubuntu jaunty

---

### Post by FuturePilot on 2009-09-20
> **praveesh said:**
> that has been removed from Ubuntu jaunty

Alt+Sysrq+K

---

### Post by sertse on 2009-09-20
At some point if you're making up situations where X,Y and Z breaks down: it's is "ok" to have no solution. :P

I mean we've come to a point where we're asking what to do if your app froze, it was full screen, your keyboard ain't working etc... It think it's not unreasonable that you can't salvage it and need to reboot. :)

---

### Post by Xbehave on 2009-09-20
> **praveesh said:**
> Some times , the whole system hangs up . Even the ctrl + alt +f1 doesn't bring a text only terminal . What to do ? It's not a rare case . In 50 % of the times , it's case
This suggests you have a serious problem*, youll want to enable shortcut keys at all levels 
window manager shortcuts (probably don't work when fullscreen)
windowing system shortcut ([ctrl+alt+bkspace]("http://lifehacker.com/5259425/re+enable-ctrl%252Balt%252Bbackspace-for-ubuntu-904"))
```
sudo dontzap --disable
```
kernel shortcuts ([alt+PrintScreen]("http://en.wikipedia.org/wiki/Magic_SysRq_key")+...)
```
echo 1 > /proc/sys/kernel/sysrq
```
or edit /etc/sysctl.conf to contain kernel.sysrq = 1 then run sysctl -p

In order to restart you will want to:
[LIST=1]
[*] alt+f4/close 
[*] ctrl+alt+bkspace (if this fails when enabled you have a serious problem)
[*] alt+print+R (get keyboard control)
[*] ctrl+alt+f1, login to get info kill process
[*] Try and get the kernel to fix it,
[LIST]
[*]alt+print+E (tell programs to **e**xit)
[*]alt+print+I (k**i**ll programs)
[*]If required reboot "safely" by
[*]alt+print+S (**s**ync discs to prevent coruption/data-loss)
[*]alt+print+U (**u**nmount)
[*]alt+print+B (re**b**oot)
[/LIST][/LIST]
You may wish to skip 2 if you know 3+4 will allow you to kill just the bad process
If 4 fails and you want to get info about the cause of the problem, you can try sshing in
```
apt-get install openssh-server
```
then after boot (but before the crash) you need run
>  /etc/init.d/shhd start
and login from a 2nd pc (putty from windows or just ssh name@IP from another linux box)

*I had a similar problem that went away on turning off modesetting (nomodeset added to kernel line in grub), other than that my only other crashes that got past 4 were caused by hardware problems and usually caused a kernel panic.

---

### Post by Mr. Picklesworth on 2009-09-20
This is something that really sucks lately with GTK and X in general: an application can hang while it is grabbing the mouse or the keyboard. Thus, it never releases the grab and that device become unusable except for events handled at a lower level (such as Ctrl Alt F2 to switch to a terminal, which is *not* user friendly). Sometimes, X puts WAY too much trust on its clients.

---

### Post by misfitpierce on 2009-09-20
> **Paqman said:**
> Alt-F2 > xkill and click on the app. Job done.

Thats what I was going to say :p ... Well said lol

---

### Post by chris4585 on 2009-09-20
Alt+F1 to make the menu appear, then from there you have plenty of control, or Alt+F2 as earlier stated.

---

### Post by praveesh on 2009-09-20
> **Xbehave said:**
> This suggests you have a serious problem*, youll want to enable shortcut keys at all levels 
window manager shortcuts (probably don't work when fullscreen)
windowing system shortcut ([ctrl+alt+bkspace]("http://lifehacker.com/5259425/re+enable-ctrl%252Balt%252Bbackspace-for-ubuntu-904"))
```
sudo dontzap --disable
```
kernel shortcuts ([alt+PrintScreen]("http://en.wikipedia.org/wiki/Magic_SysRq_key")+...)
```
echo 1 > /proc/sys/kernel/sysrq
```
or edit /etc/sysctl.conf to contain kernel.sysrq = 1 then run sysctl -p

In order to restart you will want to:
[LIST=1]
[*] alt+f4/close 
[*] ctrl+alt+bkspace (if this fails when enabled you have a serious problem)
[*] alt+print+R (get keyboard control)
[*] ctrl+alt+f1, login to get info kill process
[*] Try and get the kernel to fix it,
[LIST]
[*]alt+print+E (tell programs to **e**xit)
[*]alt+print+I (k**i**ll programs)
[*]If required reboot "safely" by
[*]alt+print+S (**s**ync discs to prevent coruption/data-loss)
[*]alt+print+U (**u**nmount)
[*]alt+print+B (re**b**oot)
[/LIST][/LIST]
You may wish to skip 2 if you know 3+4 will allow you to kill just the bad process
If 4 fails and you want to get info about the cause of the problem, you can try sshing in
```
apt-get install openssh-server
```
then after boot (but before the crash) you need run

and login from a 2nd pc (putty from windows or just ssh name@IP from another linux box)

*I had a similar problem that went away on turning off modesetting (nomodeset added to kernel line in grub), other than that my only other crashes that got past 4 were caused by hardware problems and usually caused a kernel panic.

thanks

---

