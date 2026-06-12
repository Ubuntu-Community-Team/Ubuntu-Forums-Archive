---
title: "This is Ugly"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by arpanaut on 2012-02-22
When I scroll over the sound indicator or usethe keyboard volume wheel I get:

[ATTACH]213098[/ATTACH]

on one install and it's lime green on another. Neither color have anything to do with either background image,and seems very out of place with Ambiance theme.

I understand there are many inconsistencies with the light-themes ATM, but with UI freeze tomorrow the 23rd, I am beginning to  become worried. I know that appearance is important to the desktop team so do I just need to be patient or what?  (How might one go about changing this color?)

Others seeing this?

---

### Post by fjgaude on 2012-02-22
No, not with light or dark themes... all seems pretty, by me. But I'm using Intel video.

---

### Post by PaulW2U on 2012-02-22
> **arpanaut said:**
> Others seeing this?

Reported some time ago - [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/929425](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/929425)

---

### Post by mc4man on 2012-02-22
If you happened to change the "Background Color" in unity  settings then that **could**  colorize your notifications in a less than subtle manner, maybe take a look there

---

### Post by arpanaut on 2012-02-22
Well, It seems to be a problem of image size re:
> 
 Backgrounds with height smaller than 1300 px result in blue OSD-notification-backgrounds


from comment on :[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/934425](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/934425)
still wonder why I'm getting lime green on the other install ???

Seems a bugfix is in progress.

Thanks for the feedback!

ps... I was looking for bugs having to do with indicators not notify-osd  (oh_dunb_me)
........I will mark solved when it becomes so.

---

