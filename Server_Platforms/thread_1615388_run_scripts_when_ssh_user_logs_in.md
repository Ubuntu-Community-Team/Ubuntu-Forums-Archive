---
title: "run scripts when ssh user logs in?"
date: 2010-11-06
forum: Server Platforms
---

### Post by felix_mc on 2010-11-06
I'm a bit of a unix noobie trying to manage a small ubuntu server. I want to run a bash script automatically after an ssh user logs in. For example, after they log in and the default welcome message is displayed, I want to run a script that displays some server statistics since the last session. I made an alias to the script, and I could run it manually after I log in, but it's a bit of a hassle. Is there any way I could do this? Like by changing an ssh config file or something?

---

### Post by felix_mc on 2010-11-07
well apparently just adding the script at the top of .bashrc did the trick :)

---

### Post by FuturePilot on 2010-11-07
~/.bash_login will also work.

---

