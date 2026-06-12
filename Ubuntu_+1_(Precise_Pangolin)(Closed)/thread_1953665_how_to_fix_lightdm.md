---
title: "how to fix lightdm"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-04-06
what is the command to reset lightdm somehow i got stuck with gdm at login
tks

---

### Post by cariboo on 2012-04-06
To get lightdm back, run the following command:

```
sudo dpkg-reconfigure lightdm
```

---

### Post by rburkartjo on 2012-04-06
car that was the command i was looking for but didnt work. still have gdm login screen. i have desktop nova set to autostart so i get a different full screen logon background every time i reboot. go figure

---

### Post by cariboo on 2012-04-06
Have you tried to purge gdm?

---

### Post by rburkartjo on 2012-04-07
tks will give that a try

---

### Post by rburkartjo on 2012-04-07
ok what would be the command to do that

---

### Post by BigCityCat on 2012-04-07
sudo apt-get purge gdm

---

### Post by rburkartjo on 2012-04-07
tks big

---

### Post by rburkartjo on 2012-04-08
nothing seemed to work so install the gdm and that works fine

---

### Post by rburkartjo on 2012-04-08
it seems that trying to initiate the lightgm caused my computer to go into low graphic mode no idea why. worked fine until i tinkered

---

### Post by thelordvimes on 2012-04-08
Thanks [rburkartjo]("http://ubuntuforums.org/member.php?u=459705"), ive tried so many things to try and get this to work properly after upgrading from 11.10, mainly due to the low graphics mode problem. purge lightdm and install gdm :)
And if you want to change the background image give ubuntu tweak a shot.
To get back to lightdm i used synaptics to completely remove gdm and than reinstalled light dm. Alternatively if something has gone strange, i was considering deleting the gdm folder /etc/gdm.

---

