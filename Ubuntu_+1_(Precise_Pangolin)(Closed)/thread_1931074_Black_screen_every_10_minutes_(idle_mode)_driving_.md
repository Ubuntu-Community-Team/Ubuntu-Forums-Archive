---
title: "Black screen every 10 minutes (idle mode) driving me nuts!"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by optikz on 2012-02-24
Hi All,

I am using Precise Pangolin 12.04. Every 10 minutes, especially when using xbmc to view videos, or when my PC is idle, I get a black screen. And, I have to move my mouse to get rid of it.

OK, before you give me a bunch of suggestions, I can tell you that I already went to the power management option and disabled everything. I already removed the gnome-screensaver and xscreensaver. 

Ran the commands:

xset s off
xset s noexpose
xset s noblank
setterm -blank 0
setterm -powersave off -powerdown off

Also, placed the above in my xinitrc.

I even download caffeine, but nothing works. I still get that damn black screen every 10 minutes.

The only thing that I Googled and that I didn't get to try is to modify xorg.conf, simply because there's no such file in Precise Pangolin distro.

Any solutions other than the above would be most appreciated. This black screen is driving me nuts.

--
Cheers,
Peter

---

### Post by QIII on 2012-02-24
Are you using Precise as a daily use machine, or are you testing it?

If the former, I wouldn't recommend it yet.

If the latter, this is better geared toward the testing forum.

What you have may be a reportable bug.  Do you have a launchpad account?

---

### Post by optikz on 2012-02-24
Hi QIII,

Right now, it's being used a media center. You may be right. I probably should run it by the testing forum.

Thanks for the reply.

--
cheers,
Peter.

---

### Post by QIII on 2012-02-24
I think XBMC has an option to disable screensaver while running video.  I'll check when I get home.

---

### Post by uRock on 2012-02-24
Moved to *Ubuntu +1*

---

### Post by effenberg0x0 on 2012-02-24
I'm also using PP in a XBMC server. I lost patience with the screen idling, screensaver, dpms turning monior off, etc a while ago and cheated with the following script. It's a layman's 2-minutes approach to ensure XBMC is running in both TVs - not a script one would be proud of, but it works to keep the displays active. The important part for you is when it uses xdotool to emulate mouse movement every 10 seconds. 


$ cat keep_awake3.sh
```

#!/usr/bin/env bash
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
#set -x
#set -v

mouse_x=0
mouse_y=0

sleep_period=10s #seconds
movement_px=2
  mouse_x=$(xdotool getmouselocation 2>/dev/null |  sed -e 's/x://' -e 's/y//' -e 's/ screen:.*$//' -e 's/ //' | awk 'BEGIN {FS=":"} {print $1}')
  mouse_y=$(xdotool getmouselocation 2>/dev/null |  sed -e 's/x://' -e 's/y//' -e 's/ screen:.*$//' -e 's/ //' | awk 'BEGIN {FS=":"} {print $1}')

#Kill any previous instances of xbmc, lirc
if [[ $(pidof xbmc.bin | wc -w) -gt 0 ]]; then
  echo "Previous instances of xbmc found. Attempting to kill them"
  while [[ $(pidof xbmc.bin | wc -w) -gt 0 ]]; do
    kill -s KILL $(pidof xbmc.bin)
  done
  echo "Previous instances of xbmc killed"
else
  echo "No previous instances of xbmc found"
fi

if [[ $(pidof lircd | wc -w) -gt 0 ]]; then
  echo "Previous instances of lircd found. Attempting to kill them"
  while [[ $(pidof lircd | wc -w) -gt 0 ]]; do
    kill -s KILL $(pidof lircd)
  done
  echo "Previous instances of lircd killed"
else
  echo "No previous instances of lircd found"
fi

#Find out input devices for RC0 and RC1, to be used by LIRCD
echo "Finding out /dev/event numbers for RC0 and RC1"
RC0_EVENT=$(cat /proc/bus/input/devices | grep -i rc0 | awk 'BEGIN {FS="/"} {print $NF}' | grep -o '[[:digit:]]')
echo "RC0 found at /dev/event${RC0_EVENT}"

RC1_EVENT=$(cat /proc/bus/input/devices | grep -i rc1 | awk 'BEGIN {FS="/"} {print $NF}' | grep -o '[[:digit:]]')
echo "RC1 found at /dev/event${RC1_EVENT}"

#Launch Lirc
echo "Launching lircd instances"
/usr/sbin/lircd --output=/var/run/lirc/lircd01 --driver=devinput --device=/dev/input/event${RC0_EVENT} --pidfile=/var/run/lirc/lircd01.pid
echo "lircd01 (RC0) launched"
/usr/sbin/lircd --output=/var/run/lirc/lircd02 --driver=devinput --device=/dev/input/event${RC1_EVENT} --pidfile=/var/run/lirc/lircd02.pid
echo "lircd02 (RC1) launched"

#start ir-keytable for RC0 and RC1
echo "Launching ir-keytable for RC0 and RC1"
ir-keytable -c -p RC6,LIRC -w /etc/rc_keymaps/ms-rc6 --sysdev=rc0
ir-keytable -c -p RC6,LIRC -w /etc/rc_keymaps/ms-rc6 --sysdev=rc1
echo "Launched ir-keytable for RC0 and RC1"

#Keep xbmc instances running
while true; do
  if [[ $(pidof xbmc.bin | wc -w) -ne 2 ]]; then
    if [[ $(pidof xbmc.bin | wc -w) -ne 0 ]]; then
      echo "Killing and relaunching xbmc instances"
      while [[ $(pidof xbmc.bin | wc -w) -ne 0 ]]; do
        kill -s KILL $(pidof xbmc.bin)
      done
      echo "XBMC instances killed"
      sleep 1s
    fi
    echo "Starting XBMC on DISPLAY 0.1"
    DISPLAY=:0.1 /mnt/nas/public/daemons/xbmc/xbmc.unstable/xbmc.bin --lircdev /var/run/lirc/lircd02 &
    sleep 2s
    echo "Starting XBMC on DISPLAY 0.2"
    DISPLAY=:0.2 /mnt/nas/public/daemons/xbmc/xbmc01/xbmc.bin -p --lircdev /var/run/lirc/lircd01  &
  fi
  xdotool mousemove $((mouse_x+${movement_px})) $((mouse_y+${movement_px}))
  xdotool mousemove $((mouse_x-${movement_px})) $((mouse_y-${movement_px}))
  sleep ${sleep_period}
done

```Regards,
Effenberg

---

### Post by optikz on 2012-02-25
Great Effenberg!

That's the way to do it "for now"! Actually, I needed only the xdotool part to ensure that my mouse popped up every ~9 mins or so, preventing the screen to go blank!

Thank you very much.

--
Cheers,
Peter.

---

### Post by lucazade on 2012-02-25
these xorg options alongside proper gnome-power settings are enough to disable screen blanking at all:

Section "ServerFlags"
	Option "blank time" "0"
	Option "standby time" "0"
	Option "suspend time" "0"
	Option "off time" "0"
	Option "dpms" "false"
EndSection

hope this help you..

---

### Post by Gregory Lee on 2012-02-25
> **optikz said:**
> 
The only thing that I Googled and that I didn't get to try is to modify xorg.conf, simply because there's no such file in Precise Pangolin distro.

I have it:
> # locate xorg.conf
/etc/X11/xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz
I'm interested in XBMC, since none of the video players (outside of Firefox) works for me -- they all abort my login session.

---

### Post by effenberg0x0 on 2012-02-25
> **lucazade said:**
> these xorg options alongside proper gnome-power settings are enough to disable screen blanking at all:

Section "ServerFlags"
    Option "blank time" "0"
    Option "standby time" "0"
    Option "suspend time" "0"
    Option "off time" "0"
    Option "dpms" "false"
EndSection

hope this help you..

I think you're right, I tested some of these options a while ago. I just gave up and went for the mouse-move workaround cause xorg.conf, gconf settings don't "stick" for me after updates. 

It's a shame: I had a really cool script I had been improving for years named xbmc-manager. It could deal with everything xbmc, from downloading, compiling, installing 'n' instances of it, creating a init script and putting the desired settings on /etc/default or per-user on ~/.xbmc-manager. It also worked with everything relevant via gconftool-2 and would parse xbmc userdata xml to fix the player library too. It went to the oint of looking through vidia-settings to fix flickering issues. It was 100% successful to avoid screensaver, dpms monitor off and idling. But it became a piece of trash in the Precise cycle....

Regards,
Effenberg

---

### Post by mc4man on 2012-02-25
Just curious - in all the above have you tried adjusting the various gsettings, easiest thru dconf-editor.
(as is still a bit common in dconf(editor), just because something is set, enabled or disabled, sometimes you need to cycle thru  a key once to have gsettings actually control.

There are the 3 idle-dim* in org.gnome.settings-daemon.plugins.power & the 'idle-activation..' in org.gnome.desktop.screensaver

---

### Post by optikz on 2012-02-26
Effenberg's script is the best for Precise Pangolin. There's not even a xorg.conf on my machine. to begin with.

optikz@Optikz-Aspire-5550:~$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz
optikz@Optikz-Aspire-5550:~$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

---

### Post by optikz on 2012-02-26
I tried dconf-editor also. It sucks for precise again. Some developer broke the system...

Nothing works. Bleeding-edge version??!1 You've got to be kidding me.

---

### Post by lucazade on 2012-02-26
> **optikz said:**
> Effenberg's script is the best for Precise Pangolin. There's not even a xorg.conf on my machine. to begin with.

optikz@Optikz-Aspire-5550:~$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz
optikz@Optikz-Aspire-5550:~$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

even if xorg.conf doesn't exist by default you can always create one without too much efforts.. and together with gnome-power settings will solve the blanking issue you are experiencing.

---

### Post by effenberg0x0 on 2012-02-26
> **optikz said:**
> Effenberg's script is the best for Precise Pangolin. There's not even a xorg.conf on my machine. to begin with.

optikz@Optikz-Aspire-5550:~$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz
optikz@Optikz-Aspire-5550:~$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

> **lucazade said:**
> even if xorg.conf doesn't exist by default you can always create one without too much efforts.. and together with gnome-power settings will solve the blanking issue you are experiencing.

@OP
Ideally, one shouldn't need to "cheat" like the my script does. The settings others here recommended are very likely to work at this point (I'm convinced some of them did not when this development cycle started). The main reason I still use that script is that many times I'm physically away from media servers used in Digital Signage deployments, the servers are set to auto update/upgrade and some settings were lost or adjusted back to default values. I got tired of SSH'ing in the middle of the night to check on clients blacked out LFDs... It's sort of a brute force thing. You can see by the way it handles XBMC, unintelligently killing instances, etc. As I said, it's a layman's solution :) It works for me, but you should give it a try to a softer approach too. 

Regards,
Effenberg

---

### Post by optikz on 2012-03-03
sudo Xorg :1 -configure

This created the file ~/xorg.conf.new, and 

I inserted the following recommended by lucazade (vim xorg.conf.new);

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
Option "dpms" "false"
EndSection

which I then copied to the appropriate place:

cp ~/xorg.conf.new /etc/X11/xorg.conf


and it seemed to have work. Although, the screen dims when xbmc is inactive, it doesn't go completely black. Most importantly, it doesn't go black when I'm watching movies. I wonder now how to get rid of the dimming (but that might be an xbmc issue). 

Thanks all for your help! Have a great weekend.

--
Cheers,
Peter.

---

### Post by lucazade on 2012-03-03
> **optikz said:**
> sudo Xorg :1 -configure

This created the file ~/xorg.conf.new, and 

I inserted the following recommended by lucazade (vim xorg.conf.new);

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
Option "dpms" "false"
EndSection

which I then copied to the appropriate place:

cp ~/xorg.conf.new /etc/X11/xorg.conf


and it seemed to have work. Although, the screen dims when xbmc is inactive, it doesn't go completely black. Most importantly, it doesn't go black when I'm watching movies. I wonder now how to get rid of the dimming (but that might be an xbmc issue). 

Thanks all for your help! Have a great weekend.

--
Cheers,
Peter.

you're welcome :)

---

