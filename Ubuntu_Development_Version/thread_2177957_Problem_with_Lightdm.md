---
title: "Problem with Lightdm"
date: 2013-10-01
forum: Ubuntu Development Version
---

### Post by gspe on 2013-10-01
This is the most annoying bug in Ubuntu (not only in 13.10).
Every 2 or 3 boots lightdm refuse to start leaving me with the cursor prompt...
i`m using Linux since 1994, so command line doesn`t intimidate me but for a new user is simply **unacceptable** for me too is simply [B]unacceptable!!!
[/B]
How long does it take to fix this!!!
You can have the best Operating System without the possibility to login.

---

### Post by mörgæs on 2013-10-01
If you want a serious debate a good beginning is to add links to bug reports in Launchpad.

---

### Post by gspe on 2013-10-01
Sorry for the tone, but as i sad is very annoying.
I`ve installed Ubuntu on all of my systems and this problem is present on all.
I`ll repoduce the crash and I`l attach the lightdm.log file

---

### Post by gspe on 2013-10-01
This is the lightdm.log form a failed session

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.7.17, UID=0 PID=1043
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating greeter session
[+0.00s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.00s] DEBUG: Seat: Creating display server of type x
[+0.00s] DEBUG: Seat: Starting local X display
[+0.01s] DEBUG: Deactivating Plymouth
[+0.05s] DEBUG: Using VT 7
[+0.05s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.05s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.05s] DEBUG: DisplayServer x-0: Launching X Server
[+0.05s] DEBUG: Launching process 1060: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.05s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.05s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.05s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.68s] DEBUG: Got signal 10 from process 1060
[+0.68s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+0.68s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+0.68s] DEBUG: Quitting Plymouth; retaining splash
[+0.72s] DEBUG: Seat: Display server ready, starting session authentication
[+0.72s] DEBUG: Session: Setting XDG_VTNR=7
[+0.72s] DEBUG: Session pid=1077: Started with service 'lightdm-greeter', username 'lightdm'
[+1.13s] DEBUG: Session pid=1077: Authentication complete with return value 0: Success
[+1.13s] DEBUG: Seat: Session authenticated, running command
[+1.13s] DEBUG: Session pid=1077: Setting XDG_VTNR=7
[+1.13s] DEBUG: Session pid=1077: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+1.15s] DEBUG: Session pid=1077: Logging to /var/log/lightdm/x-0-greeter.log
[+1.17s] DEBUG: Activating VT 7
[+1.79s] DEBUG: Session pid=1077: Greeter connected version=1.7.17
[+1.96s] DEBUG: Session pid=1077: Greeter start authentication for gspe
[+1.96s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+1.96s] DEBUG: Session: Setting XDG_VTNR=7
[+1.96s] DEBUG: Session pid=1161: Started with service 'lightdm', username 'gspe'
[+1.96s] DEBUG: Session pid=1077: Greeter start authentication for gspe
[+1.96s] DEBUG: Session pid=1161: Sending SIGTERM
[+1.97s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+1.97s] DEBUG: Session: Setting XDG_VTNR=7
[+1.97s] DEBUG: Session pid=1162: Started with service 'lightdm', username 'gspe'
[+1.98s] DEBUG: Session pid=1162: Got 1 message(s) from PAM
[+1.98s] DEBUG: Session pid=1077: Prompt greeter with 1 message(s)
[+1.98s] DEBUG: Got signal 15 from process 1043
[+1.98s] DEBUG: Caught Terminated signal, shutting down
[+1.98s] DEBUG: Stopping display manager
[+1.98s] DEBUG: Seat: Stopping
[+1.98s] DEBUG: Seat: Stopping display server
[+1.98s] DEBUG: Sending signal 15 to process 1060
[+1.98s] DEBUG: Seat: Stopping session
[+1.98s] DEBUG: Session pid=1077: Sending SIGTERM
[+1.98s] DEBUG: Seat: Stopping session
[+1.98s] DEBUG: Session pid=1162: Sending SIGTERM
[+1.98s] DEBUG: Session pid=1162: Terminated with signal 15
[+1.98s] DEBUG: Session: Failed during authentication
[+1.98s] DEBUG: Seat: Session stopped
[+1.99s] DEBUG: Session pid=1077: Exited with return value 0
[+1.99s] DEBUG: Seat: Session stopped
[+1.99s] DEBUG: Session pid=1161: Got 1 message(s) from PAM
[+2.09s] DEBUG: Process 1060 exited with return value 0
[+2.09s] DEBUG: DisplayServer x-0: X server stopped
[+2.09s] DEBUG: Releasing VT 7
[+2.09s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+2.09s] DEBUG: Seat: Display server stopped
[+368.42s] DEBUG: Got signal 15 from process 1
[+368.42s] DEBUG: Caught Terminated signal, shutting down
[+368.42s] DEBUG: Session pid=1161: Terminated with signal 15
[+368.42s] DEBUG: Session: Failed during authentication
[+368.42s] DEBUG: Seat: Session stopped
[+368.42s] DEBUG: Seat: Stopped
[+368.42s] DEBUG: Display manager stopped
[+368.42s] DEBUG: Stopping daemon
[+368.42s] DEBUG: Releasing VT 7
[+368.42s] DEBUG: Exiting with return value 0

```

and this is the launchpad link

[https://bugs.launchpad.net/upstart/+bug/969489](https://bugs.launchpad.net/upstart/+bug/969489)

---

### Post by grahammechanical on 2013-10-02
Did you notice this?

> [+0.00s] Debug: Loading configuration from /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf

Have you installed unity-system-compositor? If so then you have confirmed a comment I just made in another post as to the explanation why two of my Saucy installs boot to a black screen and not a login screen, and why Xmir is not going to be default in 13.10 due to serious technical difficulties - Lightdm is messing up the connection between Xmir and Unity System Compositor.

I have two Saucy installs that I have not installed unity-system-compositor/xmir on and they load fine. Besides, what do you expect when running beta software? Be fair. This is why Mark Shuttleworth has said, in so many words, if you want stability run an LTS and not an interim release. They are for development testing. If you want the bleeding edge then run the development branch. We are at the bleeding edge in this section. We often bleed.

Regards.

---

### Post by Mateusz Stachowski on 2013-10-02
That message is harmless it just means that the config has been loaded. I think that there is some problem with authentication Linux-PAM (Pluggable
Authentication Modules for Linux).

```
[+1.97s] DEBUG: Session pid=1162: Started with service 'lightdm', username 'gspe'
[+1.98s] DEBUG: Session pid=1162: Got 1 message(s) from PAM
[+1.98s] DEBUG: Session pid=1077: Prompt greeter with 1 message(s)
[+1.98s] DEBUG: Got signal 15 from process 1043
[+1.98s] DEBUG: Caught Terminated signal, shutting down 
[+1.98s] DEBUG: Stopping display manager
```

Similar messages are at the end of that log so it's most likely not XMir problem.

---

### Post by grahammechanical on 2013-10-02
The message is harmless but it does indicate that unity-system-compositor/xmir is installed. I am running 13.10 at the moment without unity-system-compositor being installed and I do not have 10-unity-system-compositor.conf in this lightdm.conf.d folder. My point is that 13.10 without unity-system-compositor installed works fine.

Regards.

---

### Post by powder on 2013-10-02
Symptom sounds like a bug report I opened a while back.  Check it out and see if the workarounds work for you.

[https://bugs.launchpad.net/lightdm/+bug/1070150](https://bugs.launchpad.net/lightdm/+bug/1070150)

---

### Post by gspe on 2013-10-02
yes i have installed unity-system-compositor but the lines that call Xmir are commented out.
I'm experimenting with Mir but this log is about a normal xorg not mir

---

### Post by gspe on 2013-10-02
> **powder said:**
> Symptom sounds like a bug report I opened a while back.  Check it out and see if the workarounds work for you.

[https://bugs.launchpad.net/lightdm/+bug/1070150](https://bugs.launchpad.net/lightdm/+bug/1070150)


Yeah i know  this bug report, and is exactly the same bug that i'm experiencing since almost 2 years ago!!
For this reason my first post was so critical because you can't stay 2 years with a bug like this.

---

