---
title: "Gnome3 Staging PPA: switch to logind instead of consolekit"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-04-23
Please note that continuing to use the Gnome3 Staging PPA
([https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging))
will switch your system to use logind instead of consolekit.

These packages are updated:
- accountsservice
- dbus
- gdm
- gnome-control-center
- gnome-session
- gnome-settings-daemon
- policykit

Should you need to purge this PPA later, you then need to manually run these two commands:
```

sudo apt-get purge libpam-systemd
sudo apt-get install libpam-xdg-support

```

---

### Post by Harry33 on 2013-04-23
Well after installing the logind system I noticed two things:

1. The PC can only be shut down with SysRq R-E-I-S-U-O.
2. The network icon on gnome-shell top panel is not working anymore

---

### Post by bmbaker on 2013-04-23
was just in the same situation 2 reboots from a terminal and the shutdown menu is working again.
logged into tty2 and stopped and restarted gdm and the network icon is there again.

edit: on reboot menu not working again and network icon not showing!

---

### Post by Harry33 on 2013-04-23
The network icon issue is likely to be fixed by upgrading to the version of network-manager (0.9.8.0-0ubuntu7+logind~raring1) in the Gnome3 Staging PPA.
There are also new pulseaudio packages in this PPA (version 1:3.0-0ubuntu6+logind~raring1).

---

### Post by bmbaker on 2013-04-23
There was also an update for libpam-systemd just a few minutes ago none of which resolved the power-off issue or the netwerk icon !

Edit: using power-off seems to crash G-S making the themes ( icon and GTK+ theme) revert to defaults and the power off menu becomes totally in-active!
Not sure where to file a bug on this one. gnome-shell, gdm or?

---

### Post by zika on 2013-04-23
> **Harry33 said:**
> Please note that continuing to use the Gnome3 Staging PPA
([https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging))
will switch your system to use logind instead of consolekit.

These packages are updated:
- accountsservice
- dbus
- gdm
- gnome-control-center
- gnome-session
- gnome-settings-daemon
- policykit

Should you need to purge this PPA later, you then need to manually run these two commands:
```

sudo apt-get purge libpam-systemd
sudo apt-get install libpam-xdg-support

```
Thank You for HU.
What are the main differences?
(I've already upgraded but I'm just (simply) curious...)

---

### Post by darkxst on 2013-04-23
Please file bugs for any issues you have, against gnome-shell is fine.

Network-manager icon bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1172062](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1172062)

---

### Post by darkxst on 2013-04-23
network manager icon should be fixed now...

---

### Post by Harry33 on 2013-04-23
> **darkxst said:**
> network manager icon should be fixed now...

Yes the newest version (0.9.8.0-0ubuntu7+logind~raring2) of network-manager fixed it.
The power off issue is still there.

---

### Post by Harry33 on 2013-04-24
> **zika said:**
> Thank You for HU.
What are the main differences?
(I've already upgraded but I'm just (simply) curious...)

In practice, I see no differencies. It is just another starting system.
There are other linux distros where systemd is in pure use (like arch linux).
We in Ubuntu have a mixed system ATM.

But this Gnome3 Staging PPA is now buggy because of issues with powering off.

What happens if you command shutdown in terminal?

---

### Post by Harry33 on 2013-04-24
> **darkxst said:**
> Please file bugs for any issues you have, against gnome-shell is fine.

Network-manager icon bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1172062](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1172062)

The poweroff issue we are seeing now is not a gnome-shell issue.
Reboot and shutdown are upstart jobs.
Now that we try to use systemd more extensively, this may affect upstart too.

---

### Post by bmbaker on 2013-04-24
Can confirm network-manager [COLOR=#000000]0.9.8.0-0ubuntu7+logind~raring2 fixed the icon issue. Power Off from the G-S menu still crashes the shell theming and doesn't  shut-down.
Power Off works though via cli.
[/COLOR]```
[COLOR=#111111][FONT=Consolas]sudo shutdown -h now[/FONT][/COLOR]
```[COLOR=#000000]
however the hibernate/suspend still functions as does Log Out and Lock.[/COLOR]

---

### Post by darkxst on 2013-04-24
> **Harry33 said:**
> The poweroff issue we are seeing now is not a gnome-shell issue.
Reboot and shutdown are upstart jobs.
Now that we try to use systemd more extensively, this may affect upstart too.

This actually has nothing to do with upstart, and atleast if its filed against gnome-shell, we will see it and redirect it to the correct package!

---

### Post by darkxst on 2013-04-24
poweroff issue has been fixed, however it is stuck in raring queue for now. So I have uploaded a fix for that to staging also.

---

### Post by Harry33 on 2013-04-24
> **darkxst said:**
> poweroff issue has been fixed, however it is stuck in raring queue for now. So I have uploaded a fix for that to staging also.

That build (198-0ubuntu10~raring1) in Gnome3 Staging PPA failed, however.
There is also a newer version (198-0ubuntu11) in RR official repos now.

The newer version (198-0ubuntu11~raring1) in Gnome3 Staging PPA is still lower than RR official version (198-0ubuntu11) and thus will not get automatically updated.

---

### Post by zika on 2013-04-24
> **Harry33 said:**
> In practice, I see no differencies. It is just another starting system.
There are other linux distros where systemd is in pure use (like arch linux).
We in Ubuntu have a mixed system ATM.

But this Gnome3 Staging PPA is now buggy because of issues with powering off.

What happens if you command shutdown in terminal?```
alias DOWN='/usr/bin/sudo /bin/sync && dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop'
```works nicely...
I did not try yet simpler method... Habbit...

---

### Post by bmbaker on 2013-04-24
well the latest systemd from the gnome3 staging ppa doesn't solve the poweroff issue.

---

### Post by VinDSL on 2013-04-24
Anybody "notice" this?

When I attempt a shutdown, using the app-indicator, I get a flashing red notification icon, next to my username (top-right corner).

Never seen this before icon before... and clicking on it produces no clue as to what's going on.

---

### Post by Harry33 on 2013-04-24
Evidently this issue will be solved, however.

I was just thinking ... this Gnome3 Staging PPA has now gone way beyond what is called Gnome 3.8.
We have now modified the basic startup system.

RR will be published tomorrow or so.
And many of us install the "SS" tool chain.
I am afraid this PPA with new systemd etc. will make a mess of it.

---

### Post by bmbaker on 2013-04-24
maybe better to revert the changes till the "SS" cycle begins? Maybe in the ricotz/testing ppa perhaps.

---

### Post by dino99 on 2013-04-24
yeah, sitting quietly by now only with gnome3 ppa but staging
3.10 will be a must i feel

---

### Post by jbicha on 2013-04-24
> **Harry33 said:**
> 
I was just thinking ... this Gnome3 Staging PPA has now gone way beyond what is called Gnome 3.8.


The GNOME3 Staging PPA has never been ready for regular users. For Raring it's an early look at parts of GNOME 3.8 that are not ready for the GNOME3 PPA. I apologize if that wasn't clear before.

I believe logind is pretty much a prerequisite for gnome-settings-daemon/control-center 3.8 to work well on Ubuntu.

---

### Post by Harry33 on 2013-04-24
> **jbicha said:**
> The GNOME3 Staging PPA has never been ready for regular users. For Raring it's an early look at parts of GNOME 3.8 that are not ready for the GNOME3 PPA. I apologize if that wasn't clear before.

I believe logind is pretty much a prerequisite for gnome-settings-daemon/control-center 3.8 to work well on Ubuntu.

Thanks Jeremy for your comment. Gnome-settings-daemon and gnome-control-center 3.8 may need logind, I can see that.
However, changing systemd more of a system wide installation is causing issues.
One of those is what I just mentioned. How can we go on testing "SS-ubuntu" as new tool chain will be soon available.
And there are some compatibility issues already.

I have also a new bug now with systemd (198-0ubuntu12~raring3).
My setup does not start Gnome session automatically any more.
I have to use tty1 and do the "startx" from there.
Also shutting down is still non functional from DE.
So I have to use tty1 and command "sudo shutdown -h now".

---

### Post by jbicha on 2013-04-24
> **Harry33 said:**
> 
And there are some compatibility issues already.


I believe the Ubuntu devs were planning to include logind by default in S soon. Finding, reporting, and fixing the bugs before that happens helps everyone.

Of course if the bugs are too much, you can use ppa-purge. I've done that multiple times this cycle for various reasons.

---

### Post by rezzo on 2013-04-24
Today I noticed a bug (?) on my Ubuntu 13.04 with Gnome3 PPA, I can't configure a VPN PPTP (I have the server, user and password). I don't know if it's an bug of 13.04 or some change introduced by the PPA and some newer Gnome 3.8 component.

*Network Settings -> + button*
[IMG]http://i.minus.com/iDnhokzcZ3REW.png[/IMG]

and if I choose *VPN* this are the options:
[IMG]http://i.minus.com/iH4EinaMTvtqK.png[/IMG]

PD: I manually installed these packages without success:
network-manager-pptp-gnome
network-manager-openvpn
network-manager-pptp
network-manager-vpnc
network-manager-pptp
pptp-linux

---

### Post by jbicha on 2013-04-24
> **rezzo said:**
> Today I noticed a bug (?) on my Ubuntu 13.04 with Gnome3 PPA, I can't configure a VPN PPTP (I have the server, user and password). I don't know if it's an bug of 13.04 or some change introduced by the PPA and some newer Gnome 3.8 component.


That [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=698215") was already identified with the GNOME3 Staging PPA but we haven't figured out what's wrong yet.

---

### Post by VinDSL on 2013-04-24
> **jbicha said:**
> That [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=698215") was already identified [...] but **[COLOR="#0000CD"]we haven't figured out what's wrong yet[/COLOR]**.
Heh!  That does it!

I'm sticking with GNOME3 Staging, come <heck> or high water  :D

Who wants an OS that just works?!?!?  Really!

I thought we left that all behind, when we started this adventure...

[QUOTE=jbicha]The GNOME3 Staging PPA has never been ready for regular users.[/QUOTE]

Exactly!  Thank you!  ;)

Keep 'em coming...

---

### Post by rezzo on 2013-04-24
> **jbicha said:**
> That [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=698215") was already identified with the GNOME3 Staging PPA but we haven't figured out what's wrong yet.

thanks for the info, I will be pending about this bug.
great work guys!

---

### Post by bmbaker on 2013-04-25
The latest update systemd (198-0ubuntu12~raring4) in the gnone3 staging ppa has fixed the Power-Off issue :-)

---

### Post by muktupavels on 2013-04-27
Does this mean that now we will be able to use pulseaudio in multi seat environment without running it system wide?

---

### Post by dino99 on 2013-04-27
> **albertsmuktupavels said:**
> Does this mean that now we will be able to use pulseaudio in multi seat environment without running it system wide?

as i know, its the future way they try to set, but not made yet.

---

