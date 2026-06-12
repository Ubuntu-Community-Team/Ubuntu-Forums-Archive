---
title: "New Update Notifier in Hoary!"
date: 2004-11-17
forum: The Cafe
---

### Post by piedamaro on 2004-11-17
It's neat ;) Did anyone know anything about it? I was like: "what? this is an update notify icon and a simplified synaptic!"

---

### Post by knappen on 2004-11-18
Never seen it before. Where did you find it?

---

### Post by oseb on 2004-11-18
$ sudo apt-get install upgrade-notifier
$ sudo apt-get install gnome-app-install

This is new package. I like manually update. ^^;

---

### Post by Jspired on 2004-11-18
Thanks for the tip.  Going to check it out now.

---

### Post by HiddenWolf on 2004-11-18
Hmm. Very Fedora. :-)

---

### Post by piedamaro on 2004-11-18
[QUOTE=HiddenWolf]Hmm. Very Fedora. :-)[/QUOTE]
 It's good, I was missing a update notifier which works well (unlike apt-watch).
Also the new add/remove interface will help newbies a lot.

> Never seen it before. Where did you find it?
I was poking with the ubuntu wiki, when I've found a chapter called PackageMangement or something, and there was written that they have these nice applications ready for hoary.

---

### Post by Jspired on 2004-11-18
[QUOTE=HiddenWolf]Hmm. Very Fedora. :-)[/QUOTE]


 :grin: 
That was exactly my thought after installing, though it does serve its purpose for some people and kudos to those who find it useful!

---

### Post by Sensebend on 2004-11-18
[QUOTE=piedamaro]It's neat ;) Did anyone know anything about it? I was like: "what? this is an update notify icon and a simplified synaptic!"[/QUOTE]
 Whoa very useful thanks :D

---

### Post by Magneto on 2004-11-18
[QUOTE=HiddenWolf]Hmm. Very Fedora. :-)[/QUOTE]
 except that it probably works ;)

---

### Post by TravisNewman on 2004-11-18
I don't really dig apt-watch, but I don't yet understand how to get upgrade-notifier to work. I see it running in the process manager, but I've purposefully left upgrades waiting to see if the upgrade-notifier will actually notify me, and so far it's a bust.

---

### Post by Magneto on 2004-11-18
do you have a notification area on your gnome-panel?

---

### Post by TravisNewman on 2004-11-18
[QUOTE=Magneto]do you have a notification area on your gnome-panel?[/QUOTE]
 yyyyup

---

### Post by Magneto on 2004-11-18
[QUOTE=panickedthumb]yyyyup[/QUOTE]
 then it is like fedora! :)

---

### Post by piedamaro on 2004-11-19
[QUOTE=Magneto]then it is like fedora! :)[/QUOTE]
 *LOL* No, it's not. This one works (at least for me), see the screenshot, there is the nice update icon in the notification area.

---

### Post by HungSquirrel on 2004-11-19
Will this work with any repository?

I ask because I'd like to add hoary to my sources.list, get just this package (if possible), and use it to monitor warty-security without actually doing a full hoary upgrade.

---

### Post by jdong on 2004-11-19
Has anyone gotten it to *work*? I can't get the upgrade notifier  to show updates!

---

### Post by TravisNewman on 2004-11-19
I purposefully left it without upgrading, as I stated earlier, and 4 hours later when I went to bed, it still hadn't shown up. This morning when I woke up, there were updates.

---

### Post by ubuntu-geek on 2004-11-19
[QUOTE=jdong]Has anyone gotten it to *work*? I can't get the upgrade notifier  to show updates![/QUOTE]
 Same for me..

---

### Post by castrojo on 2004-11-19
Doesn't work for me either, but it does for a friend of mine. :(

---

### Post by jdong on 2004-11-19
ok, I'll leave my desktop on overnight and see if any updates show tomorrow... Hoary has plenty of updates, so that won't be an issue!

---

### Post by Magneto on 2004-11-19
I can now add my 2 hoary cents- no work here either-

---

### Post by zenwhen on 2004-11-19
*Looks* slick. It should make a lot of newbies happy if it works correctly.

---

### Post by piedamaro on 2004-11-20
Weird. It works for me. It should follow any repository specified in sources.list and pop up the icon when there are available updates.

---

### Post by knappen on 2004-11-21
[QUOTE=zenwhen]*Looks* slick. It should make a lot of newbies happy if it works correctly.[/QUOTE]

Why only newbies?

---

### Post by WiLLiE on 2004-12-08
Where is it?

I installed:

update-manager
upgrade-notifier
gnome-app-install

and there's no icon in the systray.
I even rebooted, still no joy.

(I am however up-to-date)

---

### Post by adbak on 2004-12-08
You probably need to add it to your panel.  Right-click on your panel, click Add To Panel, and search for the Upgrade Notifier.

---

### Post by WiLLiE on 2004-12-08
> You probably need to add it to your panel. Right-click on your panel, click Add To Panel, and search for the Upgrade Notifier. 

I just checked (again). There's nothing (new) there.
Do I need to start the daemon manually? I don't see anything new in /etc/init.d/

I do however have some new stuff in the program menu:
Program-->System Settings-->Software Properties
Program-->System Tools-->Ubuntu Update Manager

But none of them launches the systray icon.

---

### Post by TravisNewman on 2004-12-08
Icon doesn't just "launch." You'll only see it if there are available updates.

That being said, it used to come up when there were available updates for me, but not anymore.

---

### Post by WiLLiE on 2004-12-08
ok.
I thought it behaved like the one in fedora.

---

### Post by macewan on 2004-12-08
[QUOTE=WiLLiE]ok.
I thought it behaved like the one in fedora.[/QUOTE]
 gksudo /usr/sbin/gnome-app-install

---

### Post by WiLLiE on 2004-12-08
[QUOTE=macewan]gksudo /usr/sbin/gnome-app-install[/QUOTE]

Yes? That pops up Add/Remove (which is empty under the System Services), not the icon in the systray.
Oh well, I guess it will show itself when there are some new packages then.. (if its not broken)  :wink:

---

### Post by stoffe on 2005-02-20
Is there anything I have to do for this to work? I've had these installed for quite some time, and there never pops up any notifications, no matter what...?

---

### Post by machiner on 2005-02-20
Seems to work fine for me. Any repositories in my list...

I don't see the icon unless an appy I have installed needs updating. I hover over the notification area icon and it tells me the number of updates.  Click it and it'll open my default package manager (synaptic in my case) or choose to install or download the updates.

Works a charm for me. Yeah - a la Fedora, ey - that's terrific. I like it.

Too bad it seems sketchy for so many other posters.

---

### Post by stoffe on 2005-02-20
[QUOTE=machiner]Seems to work fine for me. Any repositories in my list...

I don't see the icon unless an appy I have installed needs updating. I hover over the notification area icon and it tells me the number of updates.  Click it and it'll open my default package manager (synaptic in my case) or choose to install or download the updates.

Works a charm for me. Yeah - a la Fedora, ey - that's terrific. I like it.

Too bad it seems sketchy for so many other posters.[/QUOTE]

So I take it you didn't need to activate it somehow then?

---

### Post by jdong on 2005-02-20
Here's the deal: Upgrade-notifier relies on a nightly cron job to perform "apt-get update". 
```

jdong@omega:~$ cat /etc/cron.daily/apt
#!/bin/sh
#

#set -e

check_stamp()
{
    stamp="$1"
    interval="$2"

    if [ $interval -eq 0 ]; then
        return 1
    fi

    if [ ! -f $stamp ]; then
        return 0
    fi

    # compare midnight today to midnight the day the stamp was updated
    stamp=$(date --date=$(date -r $stamp --iso-8601) +%s)
    now=$(date --date=$(date --iso-8601) +%s)
    delta=$(($now-$stamp))

    if [ $delta -ge $interval ]; then
        return 0
    fi

    return 1
}

update_stamp()
{
    stamp="$1"

    touch $stamp
}

UpdateInterval=0
DownloadUpgradeableInterval=0
eval $(apt-config shell UpdateInterval APT::Periodic::Update-Package-Lists DownloadUpgradeableInterval APT::Periodic::Download-Upgradeable-Packages)
AutocleanInterval=$DownloadUpgradeableInterval
eval $(apt-config shell AutocleanInterval APT::Periodic::Autoclean)

# laptop check, on_ac_power returns:
#       0 (true)    System is on mains power
#       1 (false)   System is not on mains power
#       255 (false) Power status could not be determined
# Desktop systems always return 255 it seems
if which on_ac_power >/dev/null; then
    on_ac_power
    if [ $? -eq 1 ]; then
        exit 0
    fi
fi

UPDATE_STAMP=/var/lib/apt/periodic/update-stamp
if check_stamp $UPDATE_STAMP $UpdateInterval; then
    if apt-get -qq update 2>/dev/null; then
        if which dbus-send >/dev/null; then
            dbus-send --system / app.apt.dbus.updated boolean:true
        fi
        update_stamp $UPDATE_STAMP
    fi
fi

DOWNLOAD_UPGRADEABLE_STAMP=/var/lib/apt/periodic/download-upgradeable-stamp
if check_stamp $DOWNLOAD_UPGRADEABLE_STAMP $DownloadUpgradeableInterval; then
    apt-get -qq -d dist-upgrade 2>/dev/null
    update_stamp $DOWNLOAD_UPGRADEABLE_STAMP
fi

AUTOCLEAN_STAMP=/var/lib/apt/periodic/autoclean-stamp
if check_stamp $AUTOCLEAN_STAMP $AutocleanInterval; then
    apt-get -qq autoclean
    update_stamp $AUTOCLEAN_STAMP
fi


```
If this isn't performed, then you'll have no luck with the tool.

ALSO:

This applet only performs the safe "apt-get upgrade" command, not the deeper, potentially riskier "apt-get dist-upgrade" command. So, especially in development branches like Hoary, it may not catch all upgrades.

---

### Post by stoffe on 2005-02-21
[QUOTE=jdong]Here's the deal: Upgrade-notifier relies on a nightly cron job to perform "apt-get update". 
[...]
If this isn't performed, then you'll have no luck with the tool.[/QUOTE]Yep, yep, I understood as much, and I do have that exact file too, in that very place. If that is all it should take, then I have no idea what is up...

Is there something I could check for? Is there some daemon that should be running, or is it just a once-a-night cron job that will pop the icon then, and only then? Any suggestions for debugging this situation, in other words. :)

---

### Post by piedamaro on 2005-02-21
[QUOTE=stoffe]Yep, yep, I understood as much, and I do have that exact file too, in that very place. If that is all it should take, then I have no idea what is up...

Is there something I could check for? Is there some daemon that should be running, or is it just a once-a-night cron job that will pop the icon then, and only then? Any suggestions for debugging this situation, in other words. :)[/QUOTE]
 Cron should update the apt database, then the upgrade-notifier should notice the available updates.

---

