---
title: "getting error"
date: 2008-03-04
forum: System76 Support
---

### Post by P0CKETS on 2008-03-04
In gnome, I am getting an error whenever I press the caps lock key.
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host- The Box/0/numlock_on": ` ' is an invalid character in key/directory names

This started after I tried running nautilus in fluxbox, which has yet to work. It seems to hang the system every time I try to run the program. How can I fix this?

---

### Post by thomasaaron on 2008-03-05
That's a first.

It sounds like something has bound your caps lock key to a command. And the path name for the command has a ' (single-quote) in it, which is causing it to fail.

You might go to System > Prefs > Keyboard shortcuts and see if you can figure it is recorded there. If not, there's a good chance that there is a keymapping conf file somewhere for the software you downloaded.

---

### Post by osx424242 on 2008-03-05
Actually, I think that it's the space character that is being rejected:
> ` ' is an invalid character
A reinstall of "host- The Box" to a directory without spaces (e.g. host_the_box) might help; or if you can figure out what config file has that path in it, you could try escaping the spaces
(change "host- The Box" to "host-\ The\ Box").
```
find ~ -type f -exec grep "The Box" '{}' \; -print
```
(yes there are more efficient ways to do that ;))

The bigger question, nautilus in fluxbox, I have no idea.

---

### Post by thomasaaron on 2008-03-05
:oops: Yep. You're right. Thanks for catching that. I knee-jerked the answer instead of paying attention!

---

### Post by P0CKETS on 2008-03-05
Yea I ended up changing my host name to one without spaces, and the nautilus thing was because it was switching to metacity, so I just started using the ```
nautilus --no-desktop 
```command and it stops it from hanging. Even better I have been figuring out how to use mc instead of nautilus while in fluxbox. Thanks for your help.:)

---

