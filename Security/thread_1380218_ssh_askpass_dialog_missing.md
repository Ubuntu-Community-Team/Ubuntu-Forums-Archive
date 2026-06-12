---
title: "ssh askpass dialog missing"
date: 2010-01-13
forum: Security
---

### Post by gcbzzzz on 2010-01-13
I have 9.10 at work and at home. at home it was installed from scratch. at work it's upgraded from 8.10->9.06(?)->9.10

at work, when I do something over ssh, like subversion, and I have a key for that host, i am presented with a nice dialog box for my ssh key. and that's it. for the rest of my uptime, i can ssh to places without any hassle.

at home, i'm presented with the key input prompt on the terminal. Even If i manually start ssh-agent, it still happens.

what package am i missing? I have the ssh-askpass-gnome on both.

---

### Post by Roti78 on 2010-06-18
Exactly the same problem here.
Interesting that with another user it is working.
Still inspecting ...

---

### Post by Roti78 on 2010-06-18
ok, I solved this by **deleteing** all [FONT="Courier New"]gnome-keyring-daemon*[/FONT] files in my [FONT="Courier New"]~/.config/autostart directory[/FONT]

---

### Post by Roti78 on 2010-06-18
ok, I solved this by **deleteing** all [FONT="Courier New"]gnome-keyring-daemon*[/FONT] files in my [FONT="Courier New"]~/.config/autostart directory[/FONT]

---

### Post by kedder on 2011-02-25
And I solved it by checking "Run command as a login shell" in gnome-terminal preferences.

Terminal opens a little slower in this case, though. I wander what _actually_ causes gnome ssh-askpass dialog to appear (or not).

---

