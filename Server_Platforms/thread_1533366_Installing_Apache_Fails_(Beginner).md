---
title: "Installing Apache Fails (Beginner)"
date: 2010-07-17
forum: Server Platforms
---

### Post by BigCheese01 on 2010-07-17
I don't have much experience working with Ubuntu servers, but I recently decided to try to set one up. I have a remote server hosted with a static ip address, but I can't seem to install apache. 

When I run the command
```
sudo apt-get install apache2
```
It fails to install with because it is missing dependencies. 

[IMG]http://i25.tinypic.com/2irte84.png[/IMG]

"apt-get install -f" doesn't help. How can I install the necessary dependencies to get this working?

Thanks! If you need any further clarification, feel free to ask.

---

### Post by madverb on 2010-07-17
Try do the install with aptitude.

sudo aptitude install apache2

---

### Post by BigCheese01 on 2010-07-17
Well that got me at least installing the dependencies, however when it starts to install, I get an error that says:

[IMG]http://i28.tinypic.com/igggnk.png[/IMG]

My statoverride file looks like this:
[IMG]http://i27.tinypic.com/ddgymh.png[/IMG]

From my googling it looks like it should have at least a few other lines in it.

---

### Post by BigCheese01 on 2010-07-18
Bump. Anyone have a solution?

---

