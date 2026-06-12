---
title: "Unable to Install Program"
date: 2017-01-02
forum: Ubuntu/Debian BASED
---

### Post by cook150 on 2017-01-02
I have no idea how to install [https://github.com/Agadar/NationStates-Telegrammer/releases](https://github.com/Agadar/NationStates-Telegrammer/releases) on Elementary OS. How do I do it?

---

### Post by alexandari on 2017-01-03
It's using java, by the looks of the .jar file. So it may not be installable, instead you just have to open it. You need to install Java runtime environment. Try the following:
```
apt-get install openjdk-8-jre 
```
Then you can launch it via terminal like so:
```
 java -jar Yourapp.jar
```

---

