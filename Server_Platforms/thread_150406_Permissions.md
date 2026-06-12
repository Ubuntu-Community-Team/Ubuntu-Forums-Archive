---
title: "Permissions"
date: 2006-03-26
forum: Server Platforms
---

### Post by Bonafide on 2006-03-26
Ok i just installed ubuntu and i am currently trying to install java to my firefox browser i did everything but it won't move the plugin from my java folder to my plugin folder in mozilla-firefox folder. It tells me error in permissions. How do i change that?

---

### Post by IYY on 2006-03-26
If you're using the terminal to move, use **sudo mv** instead of **mv**. There are easier ways to install Java, though: 

Just run 

> sudo apt-get install sun-j2re1.5
java -version

after enabling the universe and multiverse repositories.

---

### Post by Bonafide on 2006-03-26
how do i go about enableing universe and mutivers respositories?

---

### Post by cutOff on 2006-03-26
[http://ubuntuguide.org/](http://ubuntuguide.org/) <--

---

### Post by Sutekh on 2006-03-26
You should check out [Ubuntu Wiki - Restricted Formats - Getting Java](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

There is information on getting Java in Firefox too.

---

