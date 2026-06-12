---
title: "laptop mute button"
date: 2012-03-10
forum: Tutorials
---

### Post by boblizar on 2012-03-10
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

upon inspection, my format from scratch was broken not umuting pcm.  this is what it took to fix it

alt + f2

gksu gnome-terminal

run

then drop this code

```

cat > /etc/asound.conf << EOF
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
EOF

```

and then in xfce's keyboard settings add

```

amixer -c 0 set Master 4dB- -q XF86AudioLowerVolume
amixer -c 0 set Master 4dB+ -q XF86AudioRaiseVolume
amixer set Master toggle -q XF86AudioMute

```

and a restart makes the keyboard mute button work propperly again.  this is a problem i found in xfce on ubuntu 11.10

---

