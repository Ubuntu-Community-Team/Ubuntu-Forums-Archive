---
title: "Gui"
date: 2008-10-27
forum: Server Platforms
---

### Post by baudday on 2008-10-27
So I have Ubuntu Server with a Kubuntu GUI. I am starting to use the gui less and less. I was wondering how I can shut it off, and if this will affect anything.

---

### Post by theman on 2008-10-27
sudo apt-get remove kubuntu-desktop

---

### Post by baudday on 2008-10-27
I read something about turning it off. Not completely removing it. Is that possible?

---

### Post by cdtech on 2008-10-27
Ubuntu uses the "/etc/event.d/rc-default" file for the default runlevel.

You can change the default runlevel by editing the "/etc/event.d/rc-default" file:
First (standard procedure) backup the original file:
sudo cp /etc/event.d/rc-default /etc/event.d/rc-default.backup

Open the file:
sudo pico /etc/event.d/rc-default

Find all the lines that read "telinit 2" and replace them with "telinit 3"
telinit 3

Then just Reboot the system.
Hope this helps.....

---

### Post by baudday on 2008-10-27
And will this affect anything?

---

### Post by cdtech on 2008-10-27
sorry, almost double posted...

---

### Post by cdtech on 2008-10-27
> **baudday said:**
> And will this affect anything?

No, it just changes the run level, if you find you would like to stick with the command line then and only then you could remove all GUI.

---

### Post by baudday on 2008-10-27
Alright thanks a lot

---

### Post by baudday on 2008-10-28
I'm sorry for bringing this up again, but could i just reverse the above mentioned process and that would turn it back on?

---

### Post by cariboo on 2008-10-28
You can undo the chages and get back to the way it was.

An easier solution might to stop kdm from starting. To do this 
in a terminal type:

```
sudo update-rc.d -f kdm remove
```

This will stop kdm from loading at boot up, if you need the gui, at a prompt type:

```
startx
```

Jim

---

