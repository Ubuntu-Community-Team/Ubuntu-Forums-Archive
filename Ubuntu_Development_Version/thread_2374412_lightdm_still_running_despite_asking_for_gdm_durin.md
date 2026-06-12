---
title: "lightdm still running despite asking for gdm during upgrade from 17.04 to 17.10"
date: 2017-10-15
forum: Ubuntu Development Version
---

### Post by jamesjones01 on 2017-10-15
Today I upgraded from 17.04 to 17.10 on my laptop. Since I read that Canonical is moving from lightdm to gdm, when prompted during the installation of packages I chose gdm... but with the upgrade finished, I see that lightdm is still running. (I looked because there's a consistent fifty second delay between entering my password and seeing the session window.)  I will track down how to set things up so that it runs gdm (or is that gdm3 now?), and see if there's some session log with timestamps--I just want to have on the record that it didn't honor what I believe I requested.

---

### Post by dino99 on 2017-10-16
It is now gdm3 on Artful. As you have dist-upgraded your system, you might want to clean it to remove the old settings left behind, which can disturb it: use gtkorphan & bleachbit (as root).
Then run: 'sudo dpkg-reconfigure lightdm' and choose gdm3.

---

### Post by jamesjones01 on 2017-10-16
Thanks. I am now getting gdm3. (It randomly appears rotated 90 degrees, but that's a separate issue.)

---

### Post by jbicha on 2017-10-16
Did you reboot after the upgrade?

---

### Post by jamesjones01 on 2017-10-16
Yes, I did.

---

