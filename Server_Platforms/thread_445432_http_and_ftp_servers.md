---
title: "http and ftp servers"
date: 2007-05-15
forum: Server Platforms
---

### Post by dcskater_12 on 2007-05-15
I was wondering if there are any good http server programs for ubuntu 6.10 edgy? im running apache 2.2 on windows right now. apache is good but windows is unreliable and want to use my ubuntu computer for my website server because it has better programming features and is more reliable than windows

thanks

---

### Post by heimo on 2007-05-15
> **dcskater_12 said:**
> I was wondering if there are any good http server programs for ubuntu 6.10 edgy? im running apache 2.2 on windows right now.

I'd suggest using Apache (2), which is in repositories. You can check what Apache versions are on which Ubuntu versions using package search:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Frosty Cold Drink on 2007-05-16
You can always check out lighttpd as well. Its rocks.

---

### Post by MJN on 2007-05-16
Go with Apache, like the rest of the world... ;)

---

### Post by Frosty Cold Drink on 2007-05-16
> **MJN said:**
> Go with Apache, like the rest of the world... ;)

Nah lets just go with Windows like the rest of the world :)

---

### Post by MJN on 2007-05-16
Different cause and effect... Apache is popular because it's widely regarded as being the best. Windows is popular primarily 'cos everyone else is using it! ;)

Mathew

---

### Post by Frosty Cold Drink on 2007-05-16
> **MJN said:**
> Different cause and effect... Apache is popular because it's widely regarded as being the best. Windows is popular primarily 'cos everyone else is using it! ;)

Mathew

Yeah, but the "just use Apache" mentality seems odd coming from the open source community.

Apache is great. It can do a lot of things, its feature-rich, well document, and plenty of other good things. But that fact is that at least 2/3 apache installs I see don't really need Apache. Lighttpd is a great option, which uses less resources than Apache. If you can get everything you need in Lighttpd, then I say go for it.

Using Apache all the time is like driving a Winnebago to the corner convenience store.

---

### Post by heimo on 2007-05-16
Choice is good. :) I've heard good things about lighttpd earlier, and should try it one day.

 Packages in Edgy under Web category:
[http://packages.ubuntu.com/edgy/web/](http://packages.ubuntu.com/edgy/web/)

---

### Post by DJ_Max on 2007-05-16
I completly agree with ol'  Frosty. For most setups, Apache HTTP is an overkill and the person would be a lot better off with something like LightTPD. Instead of me reiterating what I said before. [http://ubuntuforums.org/showthread.php?t=432878](http://ubuntuforums.org/showthread.php?t=432878)

---

### Post by MJN on 2007-05-16
I can see your points. However I still think developing experience with Apache stands you in good stead.

Horses for courses, but as the OP hasn't mentioned which course they're on perhaps none of us should be making recommendations! ;) However, as they're already running Apache why change without good reason?

Mathew

---

### Post by dcskater_12 on 2007-05-16
okay so i think im gonna try the lighttpd but im a no0b with ubuntu and i have no clue how to install it or any third party software for that matter?

help :)

---

### Post by heimo on 2007-05-17
> **dcskater_12 said:**
> okay so i think im gonna try the lighttpd but im a no0b with ubuntu and i have no clue how to install it or any third party software for that matter?

lighttpd is in repositories, which makes it easy to install (I haven't tried though). For general instructions on how to install stuff on Ubuntu, check these:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

EDIT: Added a link.

---

### Post by Frosty Cold Drink on 2007-05-17
MJN does have a point though. If you intend to do any of this at least semi-professionaly, the more familiar you are with Apache the better.

---

