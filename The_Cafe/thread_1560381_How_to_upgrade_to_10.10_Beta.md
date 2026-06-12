---
title: "How to upgrade to 10.10 Beta?"
date: 2010-08-24
forum: The Cafe
---

### Post by Cam! on 2010-08-24
Through 10.04's Update app, how is it possible for me to upgrade to 10.10's latest beta? What do I add in the Terminal?

---

### Post by Madspyman on 2010-08-24
Hit alt+f2 and type, ```
update-manager -d
``` also 10.10 is still in alpha.

---

### Post by NightwishFan on 2010-08-24
Please note that the version of Ubuntu in development may not be suitable for day to day use.

From:
[https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Upgrading%20from%20Ubuntu%2010.04%20LTS](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Upgrading%20from%20Ubuntu%2010.04%20LTS)

[QUOTE=Ubuntu.com]To upgrade from Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.10' is available. Click Upgrade and follow the on-screen instructions.

To upgrade from Ubuntu 10.04 LTS on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade -d; and follow the on-screen instructions. [/QUOTE]

---

### Post by The Thunder Chimp on 2010-08-24
Nothing to crafty needed for this.

Just press Alt-F2 for a "Run Application" box in which you type

```
 update-manager -d 
```

From there an update manager appears with an option for upgrade.

That's it, that's all!

;)

---

### Post by slackthumbz on 2010-08-24
open up /etc/apt/sources.list (and any files in sources.list.d) and change every instance of 'lucid' to 'maverick'; then run 'sudo apt-get update' followed by 'sudo apt-get dist-upgrade'.

You could run 'update-manager -d' but that's not as much fun ;)

But in all seriousness I wouldn't recommend using pre-release version of a distro for day to day use.

---

### Post by 23meg on 2010-08-24
> **Cam! said:**
> Through 10.04's Update app, how is it possible for me to upgrade to 10.10's latest beta? What do I add in the Terminal?

There's no beta yet. Take a look at the [release schedule]("https://wiki.ubuntu.com/MaverickReleaseSchedule").

```
update-manager -d
```

will take you to the latest state of Maverick, but I'm not sure that's where you want to go. Depending on why exactly you want to run Maverick at this point, it may be a better idea to start with the latest milestone release (Alpha 3), or a daily build. 

Read the sticky threads in [the Maverick forum]("http://ubuntuforums.org/forumdisplay.php?f=385") for a start.

---

### Post by NightwishFan on 2010-08-24
> **slackthumbz said:**
> open up /etc/apt/sources.list (and any files in sources.list.d) and change every instance of 'lucid' to 'maverick'; then run 'sudo apt-get update' followed by 'sudo apt-get dist-upgrade'.

You could run 'update-manager -d' but that's not as much fun ;)

But in all seriousness I wouldn't recommend it.


On a command line system, use the "ubuntu server" method.

---

