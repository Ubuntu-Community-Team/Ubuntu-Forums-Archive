---
title: "Reloading /etc/network/interfaces?"
date: 2010-05-10
forum: Server Platforms
---

### Post by paulehoffman on 2010-05-10
Greetings. For a particular application, I am changing /etc/network/interfaces. What is the proper way to get rid of the old settings and use the new ones? Do I need to do a full reboot and/or halt? Can I do something less drastic?

---

### Post by arrrghhh on 2010-05-10
```
sudo /etc/init.d/networking restart
```

Although in Lucid there may be a new start/stop service script...

---

### Post by Iowan on 2010-05-10
Keep your fingers crossed - Network Manager is a little more aggressive than it used to be. It used to ignore interfaces defined in */etc/network/interfaces*, but in Karmic that wasn't always true.

---

