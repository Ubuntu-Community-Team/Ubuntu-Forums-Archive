---
title: "GUI login fails"
date: 2011-12-25
forum: System76 Support
---

### Post by tbear2500 on 2011-12-25
I got a Pangolin Performance from System76 a few days ago (just before the price increase!) and so far I love it. After making some changes, though, I cannot login to a GUI session. I tried installing several libraries to mount my iPod Toich, which I sudo apt-get removed after having no success. I then played some videos on my HDTV and had to turn off the laptop display to do so, and was then for some reason unable to access the settings to make the display not go to sleep or bring the laptop display back. I then unplugged the HDMI cable and got my laptop display back, and thought all was well, less the missing user session options and battery indicator in the status bar (or whatever it's called, at the top right of the screen). I shutdown with sudo shutdown -P now. Upon rebooting, the login screen loads correctly and I can use Ctrl+Alt+F<1-6> to use a terminal session, but if I type my password at the GUI login prompt a terminal briefly flashes and I am returned to the GUI login prompt. One of the few things I managed to make out on the terminal was something about saned being disabled in /etc/default/saned. I changed the enabled value in that file to 'yes' and nothing changed. Any idea what might have caused this and how I might boot a GUI session again?

---

### Post by drewbenn on 2011-12-25
You might have better luck posting in a more general forum, since it could be a couple days before the System 76 folks start to respond.  Also, from a Virtual Terminal I'd check the file .xsession-errors in your home directory (look at it after a failed GUI login) and maybe some logs in /var/log/ like syslog or Xorg.0.log, to see if you can get more hints.

---

### Post by isantop on 2011-12-27
What happens if you run these commands from the terminal:

```
sudo killall lightdm
startx
```

This should (normally) kill the running x server and then start the graphical environment from the terminal.

---

