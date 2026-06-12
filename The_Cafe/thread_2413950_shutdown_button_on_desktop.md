---
title: "shutdown button on desktop"
date: 2019-03-04
forum: The Cafe
---

### Post by amadness on 2019-03-04
Found this little article on how to create a single-click shutdown button situated on the desktop. [https://community.linuxmint.com/tutorial/view/1113](https://community.linuxmint.com/tutorial/view/1113) I know it works in Mint & Peppermint. Anyone wanna try it in Ubuntu et al?

---

### Post by mastablasta on 2019-03-05
so instead of two clicks you have one click.

i setup the button to reboot to windows once and then when you reboot in windows it boots back to linux.

---

### Post by TheFu on 2019-03-05
Rather than making a dangerous program like shutdown available for **any** userid on the box to use, I'd setup a sudoer entry to allow only your userid to run it and without a password prompt. Same for reboot.

As for making a button on a desktop, that is just too specific for my needs, since I don't run any stock GUI.

But why don't you try it?  Just take careful notes so you can put things back - or if you have good backups and know how to restore them, then this isn't any issue to try.

---

