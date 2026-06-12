---
title: "gedit edit window transparent when using Ambiance and Radiance themes"
date: 2016-09-07
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2016-09-07
I don't normally use gedit to edit text files so I've only just noticed that gedit's edit window is transparent. If I load a file I see the text but against the desktop wallpaper rather then a white back ground, this is using the **Classic** colour scheme.

I've not seen this reported anywhere else so it might just be a problem here but this is a very standard Yakkety install of Ubuntu

Bug reported - [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1620806](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1620806) - after rebooting and making sure installation was fully updated.

Other colour schemes seem to work as they should but a transparent window is not very useful or usable. Anyone else?

Apparently not a problem on today's ISO or in a Guest session.  :confused:

---

### Post by mc4man on 2016-09-07
You could try a wide stroke to see if it goes away. - 
Boot up & at the greeter screen or after logging in go to tty3 (ctrl+alt+F3
log in, then run 
```
mv .config .config.bak && sudo reboot
```

If it fixes then something in .config, possibly in /dconf/user

To restore settings if desired go back to tty3 & 
```
rm -rf .config && mv .config.bak .config && sudo reboot
```

---

### Post by PaulW2U on 2016-09-07
Thanks for your suggestion mc4man. I deliberately made a point of not deleting settings in case I was offered an alternative solution or was asked further questions about the problem. Anyway, I deleted my .config directory and rebooted and the problem remained. (.config now restored.)

I've updated the bug report to say that the problem is only seen while using the Ambiance and Radiance themes. Switching to Adwaita gives me a fully working gedit.

---

### Post by mc4man on 2016-09-07
Did you delete manually or from a tty? (dconf/user can not be 'reset' from a user session, you'll just get what you had before

---

### Post by PaulW2U on 2016-09-07
I deleted from a tty - which gave me a very basic looking desktop devoid of all my customisations.

---

