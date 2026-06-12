---
title: "Installing Gimp Brushes"
date: 2009-01-20
forum: Ubuntu Studio
---

### Post by LoversEnd on 2009-01-20
I can't find a darn thing on how to fix this. xD
Okay, so I downladed a few brushes and tried to install them into 
/usr/share/gimp/2.0/brushes.
It came up with a message that I don't have permission and to notify the System Administrator or.. something like that.
One prob, I AM THE ADMIN. x.x
That's my problem, I don't know how to make it to where I can install these and I'm a little bit slow, so can someone PLEASE give me step-by-step instructions on how to fix this?
I'm the only person running Ubuntu in my house, so I don't know who else would be the Admin. x.x

Help?

---

### Post by Denestria on 2009-01-20
Since you are the only person using the computer you don't need to install them to the system directory.  You can install them to your personal directory where you do have write access.

/home/username/.gimp-2.0/brushes

If you want to install them to the system directory then you need to use **sudo**.
```
sudo mv nameofgimpbrush /usr/share/gimp/2.0/brushes
```

---

### Post by LoversEnd on 2009-01-22
Ahh, thanks. x.x
I finally got them to work. xD

---

