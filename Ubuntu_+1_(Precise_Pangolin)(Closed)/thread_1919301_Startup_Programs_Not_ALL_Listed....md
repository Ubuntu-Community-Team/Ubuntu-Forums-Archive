---
title: "Startup Programs Not ALL Listed..."
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TenPlus1 on 2012-02-02
How come you aren't able to turn all the startup programs on/off like you were able to in Ubuntu 11.04 ?  Allowing users to turn off things like bluetooth, network manager etc to lighten the load a little...  All 12.04 allows is to add startup apps and turn off startup sound...

Please add a system tab to the startup applications to allow advanced users to tweak their setup a little more than usual...

---

### Post by philinux on 2012-02-02
> **TenPlus1 said:**
> How come you aren't able to turn all the startup programs on/off like you were able to in Ubuntu 11.04 ?  Allowing users to turn off things like bluetooth, network manager etc to lighten the load a little...  All 12.04 allows is to add startup apps and turn off startup sound...

Please add a system tab to the startup applications to allow advanced users to tweak their setup a little more than usual...

See the links in my Sig its in there somewhere. I'm away from pc. It's to stop "users" borking their system I guess.

---

### Post by cariboo on 2012-02-02
Making a request to the developers here, won't do a lot of good, but to solve your problem, use the following commands:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

### Post by philinux on 2012-02-02
^^^ that was it. ;)

---

### Post by VMC on 2012-02-02
> **cariboo907 said:**
> Making a request to the developers here, won't do a lot of good, but to solve your problem, use the following commands:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

I knew about the 'nodisplay=true' for a while now, but only discovered the sed way yesterday. Very nice.

---

### Post by cariboo on 2012-02-02
Actually that came up during Oneiric testing, I just copied the command to a note in Zim. There is always a lot of good info in these threads, but finding it sometimes takes a bit, so I've taken to creating notes so I can find things easily.

---

### Post by xyzzyman on 2012-02-02
It also comes up when you google 'gnome session properties empty'. That's how I look it up when I don't have my bash script for my new installs handy. :)

---

### Post by TenPlus1 on 2012-02-03
Thanks cariboo907...

---

### Post by lucazade on 2012-02-03
deja vu :)

glad this is command is still useful!

---

