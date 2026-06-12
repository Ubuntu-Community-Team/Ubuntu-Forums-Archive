---
title: "Forcing a resolution with xrandr / lightdm (14.04)"
date: 2014-03-31
forum: Ubuntu Development Version
---

### Post by bunkerbound on 2014-03-31
I'm trying to set a specific resolution (1920x1200) so the resolution is persistent and applied for the login screen / greeter.  In searching the forums, it seems that I should be making updates to lightdm.conf.  However, it looks like the lightdm configuration files moved recently in 14.04.  They used to be here: /etc/lightdm/ and are now here: /usr/share/lightdm/lightdm.conf

```
ls /usr/share/lightdm/lightdm.conf.d/
50-greeter-wrapper.conf  50-guest-wrapper.conf  50-ubuntu.conf  50-unity-greeter.conf  50-xserver-command.conf
```

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2560 x 1600, maximum 32767 x 32767
eDP1 connected primary 2560x1600+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   2560x1600      60.0*+
   2048x1536      60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   1920x1200      60.0  
   1920x1080      59.9  
   1600x1200      60.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```



I believe this is the command I need to add... somewhere.
```
display-setup-script=xrandr --output eDP1 --primary --mode 1920x1200
```

Any ideas?

---

### Post by hamishmb on 2014-04-01
Okay, I don't know if that's the right command, so the first thing to do is create a copy of your lightdm conifig. The run commands, you need to open a terminal (you'll find it in your menu system, or in the Unity Dash), and before running the command in your post, backup your configuration by running "sudo mkdir /usr/share/lightdm/lightdm.conf.d.bak/ && cp -R /usr/share/lightdm.conf.d/* /usr/share/lightdm.conf.backup/" in the terminal, but without the quotes. Then it should be safe to try "display-setup-script=xrandr --output eDP1 --primary --mode 1920x1200" in the terminal without any worries.

Hope this helps,
Hamish

---

### Post by bunkerbound on 2014-04-01
I didn't backup my configs as I'm fairly certain just running this would not change the config files in any way. 

I assume you mean just run: 
> xrandr --output eDP1 --primary --mode 1920x1200

Yes, I've run this and can confirm it works.  My concern is I'm not sure which variable to set (as far as I can tell, it's 'display-setup-script') and which config file I need to dump that in.  It used to be lightdm.conf, but the config files were changed around, so I assume that's no longer the official way.

---

### Post by Toz on 2014-04-01
*Moved to the **Ubuntu+1** sub-forum.*

---

### Post by infectedorganism on 2014-04-11
I have yet to test this on Lubuntu 14.04, but it was working on the previous version.

The  file you are interested in is still located at  /etc/lightdm/lightdm.conf. What you'll want to do is make a backup of that before changing anything.

Create a script (resolution.sh) with this inside of it:
```
xrandr --output eDP1 --primary --mode 1920x1200

```

Next, chmod +x that file, giving it the correct permissions.

Now, open /etc/lightdm/lightdm.conf and place this inside of it, being sure to change the path to point to the script you just created:
```

display-setup-script=/home/bunkerbound/.scripts/resolution.sh

```

Reboot and all should be good.

If you run into trouble and can't login: alt+f2 should exit lightdm and take you to a terminal. From there you should be able to restore the original lightdm.conf file.

```

sudo cp /etc/lightdm/lightdm.conf.bak /etc/lightdm/lightdm.conf

```

---

### Post by bunkerbound on 2014-04-11
Thanks for the reply.  Unfortunately it seems like they did away with lightdm.conf in 14.04 (?).  The only file under /etc/lightdm/ is users.conf.  I'm speculating that I'm supposed to add that type of call in one of these files instead (or create a new one):
```
v\$ ls /usr/share/lightdm/lightdm.conf.d/
50-display-setup-script.conf  50-guest-wrapper.conf  50-unity-greeter.conf
50-greeter-wrapper.conf       50-ubuntu.conf         50-xserver-command.conf


```

*Edit* - I should note that I manually created the "50-display-setup-script.conf", but haven't been able to get it working.

---

### Post by lalsam on 2014-04-21
Found an answer to your question here:

[http://askubuntu.com/questions/445957/is-it-normal-for-lightdm-conf-edits-to-not-affect-the-desktop-screen-resolution/446050#446050](http://askubuntu.com/questions/445957/is-it-normal-for-lightdm-conf-edits-to-not-affect-the-desktop-screen-resolution/446050#446050)

---

