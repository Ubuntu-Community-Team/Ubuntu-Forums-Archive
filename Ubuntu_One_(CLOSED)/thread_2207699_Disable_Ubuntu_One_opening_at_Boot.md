---
title: "Disable Ubuntu One opening at Boot"
date: 2014-02-24
forum: Ubuntu One (CLOSED)
---

### Post by adec2 on 2014-02-24
Hello,

I would like to know if there is anyway to disable the ubuntu one folder opening up on the desktop at boot and just have the indicator launch. Its frustrating having to close the folder every time i boot up. I would just prefer the indicator to load up without the ubuntu one folder opening

Many thanks!

---

### Post by Irihapeti on 2014-02-24
That's not usual behaviour for Ubuntu One. What version and desktop environment are you running?

---

### Post by adec2 on 2014-02-24
Sorry I have just moved to kubuntu and kde. When i say the ubuntu one folder i mean the window that has all the settings on it, not the shared folder in my home dir

---

### Post by Irihapeti on 2014-02-24
I don't think that's normal, either. Perhaps you've saved a session with the window open, so it loads each time. I don't know my way around KDE, unfortunately, so I can't tell you exactly where those settings are, but I expect there's a "saved sessions" or "programs loaded on startup" option somewhere.

---

### Post by adec2 on 2014-03-26
Hi, I have no saved sessions with ubuntu one open it is just set to run at boot with the command "ubuntuone-control-panel-qt --with-icon"
Also at every boot it ask for the keyring password and having had a look around for solutions they all tell me to delete "default.keyring" in the .gnome2 folder in my home dir but I dont have that file in there. I have two other files to do with keyrings in "~/.local.share/keyrings" called "login.keyring" and "user.keystore".
Tried deleting both of these and rebooting but still the same. Tried a total uninstall as per the ubuntu one website and still asks me for the password at every boot. On the keyring password pop up there is an option to check that is supposedly to allow it to log on without asking for the password but it is greyed out all the time

---

