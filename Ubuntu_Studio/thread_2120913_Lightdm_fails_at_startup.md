---
title: "Lightdm fails at startup"
date: 2013-02-27
forum: Ubuntu Studio
---

### Post by jonathanfv on 2013-02-27
Hi! I would need some help to understand what's happening better, please. I have a recurring problem. On startup, my computer boots, but when the time comes for the greeter screen to appear, the Ubuntu Studio image just disappears and the screen turns black. Then I have to use the following commands (after pressing ctrl+alt+f1) to be able to log in using the user graphical interface.

```
sudo service lightdm stop
sudo service lightdm start
```Once I do that, I can access the greeter and log in normally. I tried to look at lightdm's logs from my normal session, but they looked normal, so I restarted and copied the logs in a different folder before restarting lightdm. Here is what the log looks like:

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.4.0, UID=0 PID=1530
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Activating VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 1574: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Stopping Plymouth, no displays replace it
[+0.41s] DEBUG: Process 1574 terminated with signal 6
[+0.41s] DEBUG: X server stopped
[+0.41s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.41s] DEBUG: Releasing VT 7
[+0.41s] DEBUG: Display server stopped
[+0.41s] DEBUG: Stopping display
[+0.41s] DEBUG: Display stopped
[+0.41s] DEBUG: Stopping X local seat, failed to start a display
[+0.41s] DEBUG: Stopping seat
[+0.41s] DEBUG: Seat stopped
[+0.41s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
```Does anybody have an idea of what's happening? I have bumblebee and CUDA installed.

---

### Post by jonathanfv on 2013-02-27
Well, I'd really like to know what was wrong, but it's too late now. I wondered if reinstalling Xorg, lightdm and lightdm-gtk-greeter would fix the problem, and it did. What annoys me is that now I can no longer replicate the bug and won't know what was wrong. :( If anybody has an idea of what could potentially cause that, please tell me, even if this thread is technically solved. :)

---

### Post by matt_symes on 2013-02-27
Hi

```
[+0.01s] DEBUG: Waiting for ready signal from X server :0 
[+0.01s] DEBUG: Stopping Plymouth, no displays replace it
```I'm wondering if dbus is not running at this point ? It does not seem to be getting a response from dbus at that point.

Let's try something.

Open a terminal and type 

```
sudo nano /etc/init/lightdm.conf
```Look for the line that says

```
exec lightdm
```before it put a sleep statement so it becomes

```

sleep 5
exec lightdm
```Press 

ctrl + o and ctrl + x 

to save and exit.

This will add a 5 second delay to your boot time.

Reboot the system.

```
sudo reboot
```If you still get the same issue, try a delay of 10 and then 15.

After that give up because i'm wrong :)

And thanks because you have inspired me to have a look at the lightdm source code :)

EDIT: Doh. I wish you had waited :D That'll teach me not to refresh a page for an hour or so.

Kind regards

---

### Post by jonathanfv on 2013-02-27
Hey, thanks a lot for your help! After my second restart, the problem came back, and your solution does work, so it's very fortunate that you posted that! :) I find the problem itself kinda weird, tho. Technically, it shouldn't be because my computer is slow, I have an i7 3720QM, and I just tried out 1 second delay, and it worked.

---

### Post by matt_symes on 2013-02-28
Hi

Excellent. I'm glad that helped :D

It makes sense of what i was looking at in the source code as well so we both benefited.

Kind regards

---

