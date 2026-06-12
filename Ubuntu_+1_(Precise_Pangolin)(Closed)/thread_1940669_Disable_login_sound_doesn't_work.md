---
title: "Disable login sound doesn't work"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-03-14
Hi,
Unchecking "Gnome login sound" from startup applications doesn't disable the drum beat when logging out/in.

It doesn't work either if you go to Settings->Sound->Sound Effects->Check "Alert Volume" Mute.

**Anyone knows if someone's gonna fix it?**

I solved this annoying issue manually by deleting the sound file that's being played: system-ready.ogg as explained [here]("http://ubuntuforums.org/showthread.php?t=1807626") (the last post).

---

### Post by ptn107 on 2012-03-14
I looked at the files involved:

/usr/bin/canberra-gtk-play
/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop
/usr/share/glib-2.0/schemas/10_gnome-session-canberra.gschema.override
/usr/share/gnome/autostart/libcanberra-login-sound.desktop
/usr/share/gnome/shutdown/libcanberra-logout-sound.sh
/usr/share/man/man1/canberra-gtk-play.1.gz

and can't find out why yours still plays.  Disabling the gnome login sound option in startup applications works just fine for me.  You have gnome-session-canberra 0.28-3ubuntu2 installed?  FYI removing gnome-session-canberra should work but it also removes ubuntu-desktop.

---

### Post by raja.genupula on 2012-03-14
hi try this , hope it works . 
open software center and look for gconf editor(it gives as configuration editor in search list ).install it . 
after that 

 **/desktop/gnome/sound/event_sounds**  navigate as like that . uncheck the event_sounds .

then try again .

all the best ,.

---

### Post by t1497f35 on 2012-03-14
Yes, gnome-session-canberra 0.28-3ubuntu2 was installed, my system was up to date and I used yesterday's daily iso for an amd64 clean install.

@raja thanks, however I already deleted the sound file and it stopped playing the drum beat, so I'll try your suggestion next time I do a clean install, maybe when Precise gets released.

---

