---
title: "Starling Touchpad Not Configuring on Startup"
date: 2010-10-20
forum: System76 Support
---

### Post by silverhammermba on 2010-10-20
I followed the [guide]("http://knowledge76.com/index.php/Star3") on Knowledge 76 to set up my touchpad. And I got it working inasmuch as the command start-touchpad will load my touchpad config. However, even though I set start-touchpad as a startup program, my config is not loaded on startup.

After starting up, tap to click is on (the default behavior). If I open a terminal and type "start-touchpad" tap to click turns off (as set in the config file). I know that the command is being run on startup since if I add other stuff to the script I see the results of that.

tl;dr start-touchpad doesn't work when run on startup, but does work when run manually right after startup. What can I do?

---

### Post by isantop on 2010-10-20
Hi.

Could you try adding this command as a startup program directly?

```
gksudo "fspc -t -l /home/[username]/.fspc/fspc.ini"
```

---

### Post by silverhammermba on 2010-10-20
No luck. That still doesn't work.

---

### Post by isantop on 2010-10-20
Let's try enabling it at boot up. Open a Terminal (Applications > Accessories > Terminal) and run:

```
sudo crontab -e
```

You'll have to select an editor; I recommend nano. Once you've done that, it will open up a configuration file. Add the following to the bottom:

```
@reboot gksudo "fspc -t -l /home/[username]/.fspc/fspc.ini"
```

Then reboot. Did that get it?

---

### Post by silverhammermba on 2010-10-20
That didn't work either.

---

