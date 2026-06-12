---
title: "Who decides what's in Universe/Multiverse?"
date: 2021-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by jcwjcw42 on 2021-05-16
Just wondering how it is decided which packages are included in the community-supported universe and multiverse repositories. All my web searches have uncovered is how to enable the repositories, which I've known how to do since 8.04. :)  Is there a good overview somewhere?

---

### Post by deadflowr on 2021-05-16
Universe contains community-maintained packages which are fully open source.
Multiverse are packages where the licensing may be questionable, depending on what they are and upon where the user maybe.

See: [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by jcwjcw42 on 2021-05-16
> **deadflowr said:**
> Universe contains community-maintained packages which are fully open source.
Multiverse are packages where the licensing may be questionable, depending on what they are and upon where the user maybe.

See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I understand that, but how is it decided what packages are included in them?

ETA: To clarify, not how is it decided if a package belongs in universe vs. mutliverse, but how is it decided that it will be included in either in the first place?

---

### Post by grahammechanical on 2021-05-16
The developer would have to make a request for the software to be included in Ubuntu. The licensing terms would separate Universe and Multiverse software at once. As for open source software there are hurdles to be jumped. Read about it.

[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

If an application is packaged as a snap then the process is much simpler. The application goes into the snap store. The process of creating a snap application includes verification that the application does not contain malicious code. The terms Universe and Multiverse do not apply to snap applications.

Regards

---

### Post by jcwjcw42 on 2021-05-16
> **grahammechanical said:**
> The developer would have to make a request for the software to be included in Ubuntu. The licensing terms would separate Universe and Multiverse software at once. As for open source software there are hurdles to be jumped. Read about it.

[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

If an application is packaged as a snap then the process is much simpler. The application goes into the snap store. The process of creating a snap application includes verification that the application does not contain malicious code. The terms Universe and Multiverse do not apply to snap applications.

Regards

Thanks, that is what I was looking for.

---

