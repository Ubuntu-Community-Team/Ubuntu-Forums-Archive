---
title: "Login Screen showing on Wrong Monitor"
date: 2022-04-05
forum: Ubuntu Development Version
---

### Post by yaminb on 2022-04-05
I have a 2 monitor setup (M1, M2)
After upgrading to Jammy Jellyfish, the login screen only shows up on M2. It used to show up 'correctly' on M1.
Now, M1, just shows a grey screen.

I have tried to set M1 as the primary display and orient it properly in the Gnome Settings (Screen Display Menu).
This works as expected once logged in. 

But it doesn't seem to have an effect on the login screen.

Is there anyway to force the login screen to M1? I need this as sometimes I don't turn on M2.

---

### Post by guiverc on 2022-04-05
I switched to using `sddm` many releases ago as I often *used *to have a monitor turned off, and with `sddm` both monitors are treated the same (*input dialogs are displayed on both screens so I can just move the pointer to the powered screen if I need to make selections*).

Yes I'm aware changes were made in gdm3 ver 42, but sorry I have no clues (*even the `man` page on configuration was removed*!), but if you don't get a useful `gdm3` answer, switching the DM maybe an work-around.

---

### Post by yaminb on 2022-04-05
found a fix:
[https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor](https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor)

sudo cp ~/.config/monitors.xml  /var/lib/gdm3/.config/

---

