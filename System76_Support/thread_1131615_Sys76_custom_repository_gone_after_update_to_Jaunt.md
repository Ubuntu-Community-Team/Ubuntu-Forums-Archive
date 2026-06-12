---
title: "Sys76 custom repository gone after update to Jaunty?"
date: 2009-04-21
forum: System76 Support
---

### Post by xakh on 2009-04-21
I've updated to Jaunty, since the new driver released today has support for it. However, in the update, it seems the repository provided by System76 has been deleted. Help?

---

### Post by thomasaaron on 2009-04-21
It's here...

[http://planet76.com/repositories/](http://planet76.com/repositories/)

---

### Post by Eldera on 2009-04-21
Tom: I hit the link in your post and got "file not found". (Was curious about what the 76 repositories were. Just trying to learn stuff.) Tried link twice. Maybe something is wrong with it.

---

### Post by thomasaaron on 2009-04-21
Oops! Typo!

Try the link now.

It's just where we keep the .deb files for the driver.

---

### Post by Eldera on 2009-04-21
Understood. Thanks, Eldera

---

### Post by xakh on 2009-04-21
I pointed the sources program to that site, but what do I do after that? it didn't read correctly from there.

---

### Post by thomasaaron on 2009-04-21
First, remove whatever you added via the sources program.

Then, run these two commands...

```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
```

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

I'm not sure, though, if the repository is currently set up for automatic update notifications. That feature may have been temporarily disabled.

EDIT: I just checked. Yes, it is set up.

---

### Post by xakh on 2009-04-21
And this is why I love you guys. Thanks! Someone close this topic? Thanks.

---

