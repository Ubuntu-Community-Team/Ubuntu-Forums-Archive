---
title: "Ubuntu server 10.04 64-bit corrupt console help"
date: 2010-09-10
forum: Server Platforms
---

### Post by neoideo on 2010-09-10
hello,

after failing when trying to install a GUI for my ubuntu server (just for experimental reasons) i realized that my server terminal got corrupted. 

font is now too big like the double or triple of this font, and text becomes corrupted/invisible very often at random moments. so im accesing via ssh at the moment. The real problem si the corrupt thing, sometimes all text dissapears and sometimes cursor writes where text is already writen, like if the framebuffer wasnt refreshing.

i would like to recover my original server configuration where font was a bit smaller and not corrupt, GUI can go to hell it was just a testing.

please, advices on what to remove/reinstall to remove the corrupt terminal is welcome
thanks in advance

---

### Post by CharlesA on 2010-09-10
What GUI did you install, and how did you remove it?

It sounds like a problem with the framebuffer tbh, but we'd need more info.

---

### Post by neoideo on 2010-09-10
when i tried isntalling GUI i did this
```

#sudo apt-get install ubuntu-desktop

```

then i did this, based on another psot from this forum. to prevent X starting by default

```

sed -e 's/^start on \(.*\)/start on false and \1/' /etc/init/gdm.conf|sudo tee /etc/init/gdm.conf

```

at that isntance, everything was working nice except that the GUI was in 800x600 or seomthing similar, so i tried to install nvidia driver.

```

sudo apt-get install nvidia-current
sudo nvidia-xconfig

```

that made everything corrupt, then as a desperate solution i tried unistalling them

```

sudo apt-get remove nvidia-current
sudo apt-get remove ubuntu-desktop
sudo apt-get remove gdm
sudo apt-get autoremove

```

but the damage was already done :(

ps: i also think is something to do with framebuffer, but honestly i dont know what to do

---

### Post by neoideo on 2010-09-10
i have tried 
```

sudo dpkg-reconfigure console-setup

```

but problem presists

---

### Post by CharlesA on 2010-09-10
Ok. Try this:

```

sudo apt-get install ubuntu-desktop

```

Reboot then run this:

```
sudo apt-get install nvidia-current
```

Set it up and see if the graphics are ok.

If they are, purge both of them.

```
sudo apt-get purge ubuntu-desktop nvidia-current
```

---

### Post by neoideo on 2010-09-10
ok i tried what you suggested, but sadly it didnt work so i purged them anyways.

additionaly i purged gdm, and now things got worse, after selecting kernel on grub, screen flashes a little like if it was enabling some video module and then everything black. 
however i can still login via a notebook with ssh

what do you recommend to do?

---

### Post by neoideo on 2010-09-10
i will keep trying more options

ill post back any good result
thanks already

---

### Post by CharlesA on 2010-09-10
Ok, try this.

edit blacklist.conf:
```
sudo vi /etc/modprobe.d/blacklist.conf
```

Add these at the end:

```
blacklist fbcon
blacklist vga16fb
```

Reboot and see if it's fixed.

The original problem has something to do with the frame buffer.

---

### Post by neoideo on 2010-09-10
charles, 

with your last advice i managed to install the GUI correctly :) !!! (i might use it for something)
with latest nvidia drivers (256)

however, if i stop gdm and go to server mode console command i still have the corrupt fonts, what could this be?

---

### Post by CharlesA on 2010-09-10
It's probably something to do with the drivers. 

It would probably be easier to deal with if you just leave gdm running and do a Ctrl + Alt + F1/F2/F3/F4/F6 to get a terminal and hit Ctrl + Alt + F7 to get back to the GUI.

---

