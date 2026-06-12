---
title: "Enable / Disable touchpad if mouse plugged in."
date: 2014-09-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2014-09-23
I find myself bumping my touchpad often and causing all sorts of issues while I'm doing something, Minecraft in particular. I use a regular mouse most of the time. I use the Ubuntu Gnome version and the gnome extensions webpage can't detect a valid copy of gnome running for whatever reason. So I turned to scripting. Following this [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) I wrote a small script. Once you set the variables it should be good to go, just add it to startup programs. I hope someone finds it useful. Should work on virtually any distro if xinput is used.

```
#!/bin/bash
#Tadaen Sylvermane
#Touchpad Detector


##### begin script #####


tp_toggle() {
	MYMOUSE="Logitech Unifying Device"
	TPID=$(xinput list | grep Synaptics | awk '{ print $6 }' | cut -c4-6)
	if xinput list | grep "$MYMOUSE" > /dev/null ; then
		if [[ $(xinput list-props "$TPID" | grep "Device Enabled" | awk '{ print $4 }') == 1 ]] ; then
			xinput set-prop "$TPID" "Device Enabled" 0
		fi
	else
		if [[ $(xinput list-props "$TPID" | grep "Device Enabled" | awk '{ print $4 }') == 0 ]] ; then
			xinput set-prop "$TPID" "Device Enabled" 1
		fi
	fi
}


while true
do
	tp_toggle
	sleep 5
done


##### end script #####

```

---

### Post by buzzingrobot on 2014-09-26
Next time you're at the extensions site, check at the top of Firefox's display to see if there's a dialogue asking you if you want to enable the site to load extensions on your machine.

---

