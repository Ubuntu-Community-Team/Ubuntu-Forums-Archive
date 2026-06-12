---
title: "Setting repository for System76"
date: 2009-04-28
forum: System76 Support
---

### Post by EnderEcho on 2009-04-28
I have repository to allow for system76 updates.

repo:[http://planet76.com/repositories/](http://planet76.com/repositories/)
distro:jaunty
component:main

It reads new updates but then says:

Failed to fetch [http://planet76.com/repositories/dists/jaunty/main/binary-amd64/Packages](http://planet76.com/repositories/dists/jaunty/main/binary-amd64/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

same result when its set as binary or component.

What am I doing wrong?

---

### Post by thomasaaron on 2009-04-28
To add the System76 repositories to your software sources, please run the following commands one at a time:

```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
```

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by EnderEcho on 2009-04-28
wget: invalid option -- '0'
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.

---

### Post by EnderEcho on 2009-04-28
I saw those command earlier on another thread and tried to run them and got the same error. 0 and O look similar sometimes I suppose.

Thanks!

---

### Post by thomasaaron on 2009-04-28
Did you type them in or copy & paste them?

I copied and pasted both of them into a terminal, hitting enter after each one, and they ran perfectly.

---

### Post by flukeairwalker on 2009-04-28
I was searching for these commands but couldn't find them. IMO they should be up on the wiki in the driver page.

---

