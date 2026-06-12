---
title: "How can I see what window manager is actually running"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-02-18
I know this sounds like a stupid question :redface:

But I've been playing a lot with themes in gnome-shell, unity, and gnome-session-fallback. Also add to that unity-2d and classic w/o effects so I may have either compiz, mutter, or metacity in play :D

I know what should be running based on the session I'm logged into but I need to know how to check. I've been trying to parse the parameters in "top" but "man" is leaving me confused.

Thanks in advance.

---

### Post by dino99 on 2012-02-18
might not be exactly what you expect but a first step is to watch dependencies/dependants via synaptic

---

### Post by paul_in_london on 2012-02-18
Don't know if it'll work with gnome-shell, but what about this?

[ubuntuforums.org/showpost.php?p=7641318&postcount=11](ubuntuforums.org/showpost.php?p=7641318&postcount=11)

---

### Post by dino99 on 2012-02-18
> **paul_in_london said:**
> Don't know if it'll work with gnome-shell, but what about this?

[ubuntuforums.org/showpost.php?p=7641318&postcount=11](ubuntuforums.org/showpost.php?p=7641318&postcount=11)

No sadly, this package has not been updated since 2006, so no expect it knows about so new things like unity, gnome-shell, or whatever created recently.

---

### Post by paul_in_london on 2012-02-18
> **dino99 said:**
> No sadly, this package has not been updated since 2006, so no expect it knows about so new things like unity, gnome-shell, or whatever created recently.

I checked to see that the package still exists, but I wasn't sure if it would do what was requested.

```
ps -ef | **[COLOR="Red"]egrep[/COLOR]** 'compiz|metacity|gnome-shell' | grep $USER
```

Or two other ways.

```
sudo tail -n 20 /var/log/lightdm/lightdm.log | grep "Starting session" | cut -d ' ' -f5
```

Otherwise:

```
echo $DESKTOP_SESSION
```

EDIT: Maybe you're not using lightdm of course, but the last command worked for me too! :-)

---

### Post by ajgreeny on 2012-02-18
Run command ```
ps aux | grep metacity
```which may give you output something like ```
*username*   13588  0.0  0.0   3372   740 pts/0    S+   13:07   0:00 grep --color=auto metacity
``` which shows it is not running, whereas the command looking at compiz is ```
ps aux | grep compiz
``` which gives in my case ```
*username*    1457  0.4  1.2  64180 26644 ?        S    11:26   0:28 compiz
*username*    1523  0.0  0.0   1880   492 ?        Ss   11:26   0:00 /bin/sh -c /usr/bin/compiz-decorator
*username*   13590  0.0  0.0   3376   740 pts/0    S+   13:08   0:00 grep --color=auto compiz
``` when I am using compiz.

I'm not sure why the three entries for a running app, but no doubt others will be able to tell us why.

---

### Post by 23dornot23d on 2012-02-18
It picks up Mutter

keith@keith-Aspire-7730ZG:~$ wmctrl -m 
Name: Mutter
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
keith@keith-Aspire-7730ZG:~$

and in KDE 4.8 just reports

keith@keith-Aspire-7730ZG:~$ wmctrl -m 
Name: KWin
Class: kwin
PID: 8291
Window manager's "showing the desktop" mode: OFF
keith@keith-Aspire-7730ZG:~$

---

### Post by philinux on 2012-02-18
wmctrl -m | grep "Name" | cut -c7-

Credit where it's due. [http://ubuntuforums.org/showpost.php?p=8947364&postcount=7](http://ubuntuforums.org/showpost.php?p=8947364&postcount=7)

---

### Post by paul_in_london on 2012-02-18
Sorry guys, I should have been talking about mutter here rather than GS. :oops:

---

### Post by kansasnoob on 2012-02-18
Thanks everyone, this gives me enough to work with :)

---

