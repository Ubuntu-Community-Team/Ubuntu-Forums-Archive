---
title: "apt-get now working in ubuntu server 9.10"
date: 2010-02-09
forum: Server Platforms
---

### Post by oboedude on 2010-02-09
[SIZE=2][FONT=Arial]I am currently running Ubuntu Server 9.10 [/FONT]and having trouble with apt-get. I have tried to run the following commands and none seem to work:

[/SIZE]```
sudo apt-get install sun-java6-jdk
```
```
sudo apt-get install flex
```
```
sudo apt-get install bison
```
[FONT=Arial][SIZE=2]
Every time I get a package not found error back. I know they [/SIZE][/FONT][SIZE=2]are all valid packages because I have successfully installed them via apt-get in the past couple of days on other linux systems, but for some reason apt-get is not working on my machine.

At this point I know the networking is working properly. I am able to ping the outside world, including us.ubuntu.com and security.ubuntu.com, and ssh to and from my machine.

I'm fairly new to linux, so any help anybody can offer would be greatly appropriated in resolving my apt-get issue.
[/SIZE]

---

### Post by BobVila on 2010-02-09
what does sudo-apt get update do for you?

---

### Post by oboedude on 2010-02-09
[SIZE=2][FONT=Arial]That did the trick. Apparently my proxy setting was messed up and not [/FONT]allowing access to the sources in my source list. Thank you very much for the help![/SIZE] :D

---

### Post by BobVila on 2010-02-09
Glad to provide a nudge in the right direction!

---

