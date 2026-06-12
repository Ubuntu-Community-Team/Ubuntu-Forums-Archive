---
title: "im not new to ubuntu but this option is not in ubuntu by default without gnome tweaks"
date: 2024-02-22
forum: Ubuntu, Linux and OS Chat
---

### Post by zarosath on 2024-02-22
[https://askubuntu.com/questions/1263698/cant-use-both-mouse-and-keyboard-at-the-same-time](https://askubuntu.com/questions/1263698/cant-use-both-mouse-and-keyboard-at-the-same-time)

its not native without installing the app gnome tweaks.

some people use ubuntu for gaming. it has the most repositories and may be the most active, am i mistaken?

keyboard and mouse - disable touchpad while typing.

im developing an app from legacy software/compiler, its much unix-like and i had mistaken that i thought the software library it uses became broken/deprecated.

most of the time i cant have a mouse its most convenient to use the touchpad on my laptop.

---

### Post by deadflowr on 2024-02-22
The option is always there.
gnome tweaks just makes it easier to enable.

---

### Post by zarosath on 2024-02-22
your right, it is an option. my mistake. but i could not find it in the settings menu.

---

### Post by TheFu on 2024-02-23
Please mark this thread "SOLVED" using the _thread tools_ button so people don't waste time and those seeking the same answer easily find this thread.

---

### Post by grahammechanical on 2024-02-25
Ubuntu 24.04 LTS (at present under development) has an option in the settings utility>mouse & touchpad. There is a touchpad tab. We can disable the touchpad while typing. We can also disable the touchpad entirely. Take care doing that. It seems impossible to re-enable the touchpad without having a mouse plugged in.

Regards

---

### Post by him610 on 2024-02-25
You can also [en | dis]able the touchpad from the terminal. My spouse uses a laptop and I sometimes use an ancient netbook - both have touchpads. 
```

# Needs to be installed
apt install xserver-xorg-input-synaptics
# Disable/enable touchpad when mouse connected
#disable
synclient TouchpadOff=1
#enable
synclient TouchpadOff=0

```
Make easy to remember
```

# place aliases in [.bashrc | .bash_aliases]
alias trkon="synclient TouchpadOff=0"
alias trkof="synclient TouchpadOff=1"

```
Oh, one other thing, I don't know if it works with Wayland.

---

