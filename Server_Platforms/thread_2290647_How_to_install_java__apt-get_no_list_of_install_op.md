---
title: "How to install java?  apt-get no list of install options?"
date: 2015-08-14
forum: Server Platforms
---

### Post by Higgins909 on 2015-08-14
I've trying to install java and am having difficulties...
I would like to get jre 8 if possible.
You used to be able to type sudo apt-get install java
and if it went wrong it would be like do you want to install java7 or java is not a package but here are some similar names.
you could even type java and not even have it and it would suggest versions to install.
This is on a VM ubuntu server install.

---

### Post by howefield on 2015-08-14
This one ?

```
openjdk-8-jre
```

---

### Post by Higgins909 on 2015-08-14
When I try to install it I get
```

Errors were encountered while processing:
 systemd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
at the end of trying to install.  It did this before and I just got done reinstalling whole os (its a vm so its not too hard)
I tried to sudo apt-get autoremove it and it wouldn't complete, was timing out on something.

I also don't understand why its half a GB... it should be like 50MB
Edit: also typing java in, nothing happens.

---

### Post by Higgins909 on 2015-08-14
If anyone ever see's this and is having issues... don't install openjdk-8-jre.
instead install openjdk-7-jre, 8 broke my installation in so many ways... ssh became so unresponsive and wouldn't shutdown and way slower startup.

But I would like to get back how I could type apt-get install java and it would be like did you mean openjdk-7-jre?

---

### Post by nerdtron on 2015-08-16
> But I would like to get back how I could type apt-get install java and it would be like did you mean openjdk-7-jre? 
Apt-get will suggest it it knows probably what you want, but there are many java version out there so it's better to just perform a search and read the description of possible install candidates.
```
 sudo apt-cache search java 
sudo apt-cache show openjdk-7-jre 
```

---

