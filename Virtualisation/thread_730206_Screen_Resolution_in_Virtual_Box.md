---
title: "Screen Resolution in Virtual Box"
date: 2008-03-20
forum: Virtualisation
---

### Post by sbussy89 on 2008-03-20
Ok, I installed the virtual box guest additions, but when I changed to 1024x768 resolution the screen got all messed up and I couldn't even tell what was going on, i just had to wait the 20 secs for it to reset itself.  So I found another post and and ran the command "sudo dpkg-reconfigure -phigh xserver-xorg" in recovery mode as instructed by that post (which worked for another person), but the resolution was still 800x600 after reboot.  When I change it to 1024x768 as before, instead of messing up the screen the resolution doesn't actually change, but it asks me if I wan tot keep the new settings as if it had changed.  I say yes, but if I go back to select the screen resolution it is still set at 800x600 as if I had never changed it.  How can I fix this?

---

### Post by herbster on 2008-03-20
I'm confused-- are you running Windows in Virtualbox and asking about that? Or Ubuntu in Virtualbox?

---

### Post by Kiri on 2008-03-21
After you set the new resolution, if there is no change. Try to reload X (ctrl+alt+backspace). For me this is how I got ubuntu to use the new resolution.

---

