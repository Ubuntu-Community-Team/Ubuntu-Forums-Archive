---
title: "Jittery Windows, Flickering, Text Jumping Around..."
date: 2016-11-11
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-11-11
I've noticed this as a problem in both of my Ubuntu based OS's. They both use Intel graphics. I also thought I remembered this being a problem with 16.04 and Intel Graphics. Is that correct? The thrust of my question is this: If I were to try a different Ubuntu-based distro, using GTK rather than QT for example, would it make any difference?

I have Linux Mint (based on 16.04) installed on an older desktop. Also uses Intel graphics but I haven't noticed any flickering or display problems. Leads me to think this may all be QT related?

---

### Post by neu5eeCh on 2016-11-28
Within an hour or two of giving up, I  may have found the source of the problem. Give it a day or two but, for  the next person, the solution might be:

sudo apt-get purge xserver-xorg-video-intel

From here:

[https://bugs.launchpad.net/ubuntu/+sour ... ug/1450228]("https://bugs.launchpad.net/ubuntu/+source/plasma-desktop/+bug/1450228")

Which got it from here:

[https://askubuntu.com/questions/766725/ ... 226#814226]("https://askubuntu.com/questions/766725/annoying-flickering-in-16-04-lts-chrome/814226#814226")

So  far, I haven't suffered any of the severe flickering and jumping text  that usually plagues browsing and Libre Office. I found this potential  solution by Googling <Plasma Intel Bug>. It _does_ appear to be an Ubuntu/16.04 related bug. So this solution might work for anyone else using any Ubuntu based distro?

---

### Post by g33zr on 2016-11-28
I had the same problem with 16.04 as well as with Mint 18, but found a couple of fixes that worked more or less, but not 100%. 

See, for example, [https://ubuntuforums.org/showthread.php?t=2340056&highlight=flickering](https://ubuntuforums.org/showthread.php?t=2340056&highlight=flickering)

In the end, I replaced Ubuntu 16.04 with 16.10 and haven't had a problem since.

---

### Post by neu5eeCh on 2016-11-28
Thanks g33r. So far, having purged xserver-xorg-video-intel seems to have done the trick. There hasn't been a single flicker or jitter. Everything is as it should be -- smooth and stable on all my Ubuntu-based distros, including my wife's installation of Ubuntu.

If this doesn't fly, then I'll try editing grub and switch to 16.10 as a last resort, which would be disappointing to say the least. Mint, KDE NEON, and Maui Linux are all based on 16.04 and are all using the partial rolling release model to update their respective desktops. I'd rather not go chasing after each release again.

---

