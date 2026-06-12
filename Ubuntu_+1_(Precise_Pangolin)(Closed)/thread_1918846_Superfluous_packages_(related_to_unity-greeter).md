---
title: "Superfluous packages (related to unity-greeter)"
date: 2012-02-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-02-01
So last night I applied the latest updates - as you do - and when these new packages were pulled in I thought "What the..."?!

```
Aptitude 0.6.4: log report
Tue, Jan 31 2012 19:53:43 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 57 packages, and remove 1 packages.
17.1 MB of disk space will be used
===============================================================================
[REMOVE, NOT USED] libllvm2.9
[INSTALL, DEPENDENCIES] exo-utils
[INSTALL, DEPENDENCIES] geoclue
[INSTALL, DEPENDENCIES] geoclue-ubuntu-geoip
[INSTALL, DEPENDENCIES] indicator-datetime
[INSTALL, DEPENDENCIES] indicator-messages-gtk2
[INSTALL, DEPENDENCIES] indicator-power
[INSTALL, DEPENDENCIES] libexo-1-0
[INSTALL, DEPENDENCIES] libexo-common
[INSTALL, DEPENDENCIES] libexo-helpers
[INSTALL, DEPENDENCIES] libgarcon-1-0
[INSTALL, DEPENDENCIES] libgarcon-common
[INSTALL, DEPENDENCIES] libindicator7
**[COLOR="Red"][INSTALL, DEPENDENCIES] libllvm3.0[/COLOR]** **[COLOR="Red"]# only needed this one[/COLOR]**
[INSTALL, DEPENDENCIES] libxfce4ui-1-0
[INSTALL, DEPENDENCIES] libxfce4util-bin
[INSTALL, DEPENDENCIES] libxfce4util-common
[INSTALL, DEPENDENCIES] libxfce4util4
[INSTALL, DEPENDENCIES] libxfconf-0-2
[INSTALL, DEPENDENCIES] xfce-keyboard-shortcuts
[INSTALL, DEPENDENCIES] xfce4-indicator-plugin
[INSTALL, DEPENDENCIES] xfce4-panel
[INSTALL, DEPENDENCIES] xfconf
...
```

```
paul@precise-64:~$ aptitude why **[COLOR="Red"]libllvm3.0[/COLOR]**
i   **[COLOR="Red"]libgbm1[/COLOR]** Depends **[COLOR="Red"]libllvm3.0[/COLOR]**
paul@precise-64:~$
```

```
paul@precise-64:~$ aptitude why **[COLOR="Red"]libgbm1[/COLOR]**
i   **[COLOR="Red"]libegl1-mesa-drivers[/COLOR]** Depends**[COLOR="Red"] libgbm1[/COLOR]** (>= 7.11~1)
paul@precise-64:~$
```

I forgot that after my recent problems with unity-greeter I'd only changed /etc/lightdm/lightdm.conf like this:

```
[SeatDefaults]
user-session=ubuntu
#greeter-session=unity-greeter
greeter-session=lightdm-gtk-greeter
paul@precise-64:~$
```

I now realise I hadn't actually purged the unity-greeter package (which I've now done) so I didn't actually need any of those other packages above except libllvm3.0 and (having checked the dependencies) I've been able to remove them. :)

---

