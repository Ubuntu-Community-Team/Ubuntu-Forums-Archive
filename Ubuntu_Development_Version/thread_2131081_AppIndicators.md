---
title: "AppIndicators"
date: 2013-03-31
forum: Ubuntu Development Version
---

### Post by foxy123 on 2013-03-31
What is the current status of AppIndicators in Raring? I have recently upgraded from 12.10 and do not have neither Skype, nor NetworkManager, nor Keyboard Indicator on the panel, which is a bit annoying. I know that whitelist is depreciated but I wonder if the new system is working or it is just buggy. As I understand all those should work with AppIndicators.

---

### Post by Frogs Hair on 2013-03-31
Install synaptic if not already and look them up and install them if needed and restart. missing indicators have been noted by others as a result of upgrades.  Try indicator-network for example . I don't use Skype and can't comment. This is still beta testing and though 13.04 is running well for me that is not the case for all testers. If you have need of more complete stable system don't use pre-release versions.

---

### Post by stinkeye on 2013-03-31
Try creating a new user to see how things work from there without the 
interference from old configs.

---

### Post by rrnbtter on 2013-03-31
Greetings,
The reality is that the individual software developers will have to make their software compatible with the indicator. Systray is basically going away. It may take a few months for some and perhaps never for others. I like Gajim for my jabber client and currently using Empathy which I don't prefer. Kopete and the other options still don't have indicators. Just the state of affairs right now and not all fixable by Ubuntu.

---

### Post by foxy123 on 2013-03-31
> **Frogs Hair said:**
> Install synaptic if not already and look them up and install them if needed and restart. missing indicators have been noted by others as a result of upgrades.  Try indicator-network for example . I don't use Skype and can't comment. This is still beta testing and though 13.04 is running well for me that is not the case for all testers. If you have need of more complete stable system don't use pre-release versions.

I have tried to install the indocator-network but it is for connman not nm. So I do not think that those indicators will help.

> **stinkeye said:**
> Try creating a new user to see how things work from there without the 
interference from old configs.

I have already done it and it's not different from what I have on my account.

> **rrnbtter said:**
> Greetings,
The reality is that the individual software developers will have to make their software compatible with the indicator. Systray is basically going away. It may take a few months for some and perhaps never for others. I like Gajim for my jabber client and currently using Empathy which I don't prefer. Kopete and the other options still don't have indicators. Just the state of affairs right now and not all fixable by Ubuntu.

Well, it is true but NM and Skype do have appinducators as far as I know. The keyboard indocator is a part of  the default setup and should work unless the whole appindicators system is still buggy.

---

### Post by mc4man on 2013-03-31
The indicator is  nm-applet (from network-manager-gnome package
Is it installed & if so have you disabled it from startup applications (by default is not displayed as a choice so should run if installed

---

### Post by foxy123 on 2013-03-31
> **mc4man said:**
> The indicator is  nm-applet (from network-manager-gnome package
Is it installed & if so have you disabled it from startup applications (by default is not displayed as a choice so should run if installed

It is installed but is not in startup apps. Should I add it?

---

### Post by mc4man on 2013-03-31
> **foxy123 said:**
> It is installed but is not in startup apps. Should I add it?

Really should be no need - 
Does it show up & run if you go -
Alt+F2 > type in nm-a, should show in command box (nm-applet), if so click on 

If it works then what does this show
```
gedit /etc/xdg/autostart/nm-applet.desktop
```

---

### Post by dino99 on 2013-04-01
install that ppa to get whitelist back : [https://launchpad.net/~timekiller/+archive/unity-systrayfix](https://launchpad.net/~timekiller/+archive/unity-systrayfix)

---

### Post by foxy123 on 2013-04-01
> **mc4man said:**
> Really should be no need - 
Does it show up & run if you go -
Alt+F2 > type in nm-a, should show in command box (nm-applet), if so click on 

If it works then what does this show
```
gedit /etc/xdg/autostart/nm-applet.desktop
```

the command does not do anything. Here the contents of the .desktop file:

[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-GNOME-UsesNotifications=true
X-Ubuntu-Gettext-Domain=nm-applet

> **dino99 said:**
> install that ppa to get whitelist back : [https://launchpad.net/~timekiller/+archive/unity-systrayfix](https://launchpad.net/~timekiller/+archive/unity-systrayfix)

The thing is that all those apps (Skype and network and keyboard layout indicators) are said to support AppIndicators framework. I am not sure if I need to white-list them. But I will try it if all other attempts fail. Thanks for the PPA.

---

### Post by foxy123 on 2013-04-03
Still no luck. But I have a black U1 cloud now. Well I have had it since the upgrade but do not remember having it before that. I am wondering if it is a problem with the upgrade. Probably should have done a clean install but is a bit lazy for that.

---

### Post by dino99 on 2013-04-03
> **foxy123 said:**
> Still no luck. But I have a black U1 cloud now. Well I have had it since the upgrade but do not remember having it before that. I am wondering if it is a problem with the upgrade. Probably should have done a clean install but is a bit lazy for that.

Get the same issue  i cant set the locales : so the temperature is missing & the icon always stay cloudly
[https://bugs.launchpad.net/baltix/+source/indicator-weather/+bug/821233](https://bugs.launchpad.net/baltix/+source/indicator-weather/+bug/821233)

---

### Post by foxy123 on 2013-04-03
actually the indicators are back after the recent update.

---

