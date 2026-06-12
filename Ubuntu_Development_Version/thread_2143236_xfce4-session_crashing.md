---
title: "xfce4-session crashing"
date: 2013-05-08
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-05-08
i am using raring and found a way to crash xfce4-session and would like to know if it is fixed in saucy
open terminal
run
export LC_TIME=en_DK.UTF-8
close terminal
open anything (terminal; Thunderbird)

i was messing with this, looking for a better solution
[http://askubuntu.com/questions/292436/how-to-make-thunderbird-obey-locale/292456?noredirect=1#comment367815_292456](http://askubuntu.com/questions/292436/how-to-make-thunderbird-obey-locale/292456?noredirect=1#comment367815_292456)

apport does not like that i am using a mainline kernel

edit:
unable to reproduce on live cd or guest account, now getting strange behavior here
apport does not even open firefox when it happened

---

### Post by slickymaster on 2013-05-08
Running it on a VirtualBox, but don't have Thunderbird installed, though.

Here are my specs:
```
lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
3.9.0-030900rc3-generic
```

```
dpkg --get-selections | grep xfce4
libxfce4ui-1-0     install
libxfce4ui-utils    install
libxfce4util-bin    install
libxfce4util-common    install
libxfce4util6     install
xfce4-appfinder     install
xfce4-cpugraph-plugin    install
xfce4-dict     install
xfce4-indicator-plugin    install
xfce4-mailwatch-plugin    install
xfce4-netload-plugin    install
xfce4-notes     install
xfce4-notes-plugin    install
xfce4-notifyd     install
xfce4-panel     install
xfce4-places-plugin    install
xfce4-power-manager    install
xfce4-power-manager-data   install
xfce4-power-manager-plugins   install
xfce4-quicklauncher-plugin   install
xfce4-screenshooter    install
xfce4-session     install
xfce4-settings     install
xfce4-systemload-plugin    install
xfce4-taskmanager    install
xfce4-terminal     install
xfce4-verve-plugin    install
xfce4-volumed     install
xfce4-weather-plugin    install
xfce4-xkb-plugin
```

Reproduce what you ask, run ```
export LC_TIME=en_DK.UTF-8
```closed the terminal and reopened it and xfce-session didn't crash.

Can't say if it's due to some kind of a fix in Saucy or if it's due to the fact that I don't have Thunderbird installed.

---

### Post by pqwoerituytrueiwoq on 2013-05-08
it is happing when at random now, i just deleted a couple files hopefully it will stop, it happens sometimes when i open a terminal and ff is open now, never even ran a command
a happen to know how to make apport stop ignoring a crash? it wont even tell me it crashed now it happened so may times

---

### Post by slickymaster on 2013-05-08
> **pqwoerituytrueiwoq said:**
> ... happen to know how to make apport stop ignoring a crash? it wont even tell me it crashed now it happened so may times

Sorry if this seems to be a stupid question, but you do have it enable, don't you?

---

### Post by mörgæs on 2013-05-08
Changed the thread title to a more informative one.

---

### Post by matt_symes on 2013-05-08
Hi

> **slickymaster said:**
> Sorry if this seems to be a stupid question, but you do have it enable, don't you?

If the OP is using a mainline kernel then it's a non standard install and so, consequently, not supported.

Apport will detect this and not upload a crash report.

Kind regards

---

### Post by slickymaster on 2013-05-08
> **matt_symes said:**
> Hi

If the OP is using a mainline kernel then it's a non standard install and so, consequently, not supported.

Apport will detect this and not upload a crash report.

Kind regards

Thanks for the heads-up matt. Didn't knew that. We're always learning.

---

### Post by pqwoerituytrueiwoq on 2013-05-08
> **matt_symes said:**
> Hi



If the OP is using a mainline kernel then it's a non standard install and so, consequently, not supported.

Apport will detect this and not upload a crash report.

Kind regards

it is not even telling me something crashed anymore, it will not even tell me to not use the mainline kernel

---

### Post by matt_symes on 2013-05-09
Hi

> **pqwoerituytrueiwoq said:**
> it is not even telling me something crashed anymore, it will not even tell me to not use the mainline kernel

Apport is enabled ? It should be but it's worth checking

```
matthew-S206:/home/matthew/thunar_dbus % cat /etc/default/apport 
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=1
matthew-S206:/home/matthew/thunar_dbus %
```

Is it running ?

```
matthew-S206:/home/matthew/thunar_dbus % initctl status apport        
apport start/running
matthew-S206:/home/matthew/thunar_dbus %
```

Kind regards

---

### Post by slickymaster on 2013-05-09
> **matt_symes said:**
> Hi
Apport is enabled ? It should be but it's worth checking


Sorry for stepping in matt, but now you got me all confused. In post #4, I ask the OP exactly that and you said > If the OP is using a mainline kernel then it's a non standard install and so, consequently, not supported.
Apport will detect this and not upload a crash report.Please don't misread this post as being rude or arrogant, it's not that at all. It's just that now you gave me a knot in the brain. :confused:

---

### Post by matt_symes on 2013-05-09
Hi

> **slickymaster said:**
> Sorry for stepping in matt, but now you got me all confused. In post #4, I ask the OP exactly that and you said 

It should be enabled by default on a dev install and quite possibly on a standard install as well but i can't currently check that as my only Ubuntu derived desktop install is Xubuntu saucy at the moment.

If running the mainline kernel apport should still run but not upload a crash report. It should display an error message about the mainline kernel being installed.

As the system on this PC seems really messed up, i'm wondering if Apport is not running at all and whether you were right in the first place. One would expect to see the Apport window popup.

> Please don't misread this post as being rude or arrogant, it's not that at all. It's just that now you gave me a knot in the brain. :confused:

Your question was not in any way rude. It was a very valid question :D

Kind regards

---

### Post by slickymaster on 2013-05-09
> **matt_symes said:**
> Hi



It should be enabled by default on a dev install and quite possibly on a standard install as well but i can't currently check that as my only Ubuntu derived desktop install is Xubuntu saucy at the moment.

If running the mainline kernel apport should still run but not upload a crash report.

As the system on this PC seems really messed up, i'm wondering if Apport is not running at all and whether you were right in the first place. One would expect to see the Apport window popup.



Your question was not in any way rude. It was a very valid question :D

Kind regards

Thanks for the explanation and for not misreading my post, I really appreciate it. Truth is I was really confused.
Once again I thank you.

---

### Post by fowlslegs on 2013-05-09
Please see my post at [http://ubuntuforums.org/showthread.php?t=2143167](http://ubuntuforums.org/showthread.php?t=2143167). This will likely fix your problem.

---

### Post by pqwoerituytrueiwoq on 2013-05-09
> **fowlslegs said:**
> Please see my post at [http://ubuntuforums.org/showthread.php?t=2143167](http://ubuntuforums.org/showthread.php?t=2143167). This will likely fix your problem.
if that is for this bug
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435)
i think i was getting a different crash
i had that one once during testing, very reproducible scenario
this suddenly started happening, i have been using raring since beta, and suddenly hit a crash fest, i applied the fix for the above bug after it hit me today, sill needs more testing to confirm that got it

---

