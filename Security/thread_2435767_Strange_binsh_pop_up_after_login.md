---
title: "Strange /bin/sh pop up after login"
date: 2020-01-25
forum: Security
---

### Post by mlabowicz on 2020-01-25
[IMG]https://www.dropbox.com/s/il3ds7u4j4lweaz/Screenshot%20from%202020-01-12%2009-04-47.png?dl=0[/IMG]I'm seeing a strange pop up show up a little after I login to my Ubuntu 18.04 desktop.  Does anyone have any ideas how I can trouble shoot where this pop up is coming from? I'm thinking its being triggered by a startup or login script. See attachment for screenshot
[IMG]https://www.dropbox.com/s/il3ds7u4j4lweaz/Screenshot%20from%202020-01-12%2009-04-47.png?dl=0[/IMG]

---

### Post by ubu6 on 2020-01-25
Sounds like it might be a challenge. You might want to start by looking into 2 directories:

1) /home/$USER/.config/autostart/
or
2) /etc/init.d/

there is also the services directories, you may also like to look into, i think they are here
/lib/systemd/system/
and here
/etc/systemd/system/

Lots of luck!

---

