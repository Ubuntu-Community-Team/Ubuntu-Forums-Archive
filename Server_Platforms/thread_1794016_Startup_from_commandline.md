---
title: "Startup from commandline"
date: 2011-06-30
forum: Server Platforms
---

### Post by compulsiveguile on 2011-06-30
For certain (dumb) reasons, I installed Gnome on top of an 11.04 server installation. Upon boot, this automatically starts and hogs more resources than I want/need it to. I want to go back to basic command line startup. How do I go about doing this? 

Thanks in advance!

---

### Post by Cheesehead on 2011-06-30
Do you mean that you want to uninstall Gnome?
Or do you mean that you want a choice of CLI vs Gnome at each boot?
Or do you mean something else?

---

### Post by compulsiveguile on 2011-06-30
> **Cheesehead said:**
> Do you mean that you want to uninstall Gnome?
Or do you mean that you want a choice of CLI vs Gnome at each boot?
Or do you mean something else?


Option 2... CLI vs Gnome choice. I would also like to know how to uninstall Gnome should I decide later to go that route. 

Thanks for the quick response!

---

### Post by ajgreeny on 2011-06-30
You could just remove gdm from /usr/sbin, or make it non executable, or rename the gdm file in /etc/init.d, then on the occasions that you do need gnome you would need to use the command **startx**.

See also [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

---

### Post by rubylaser on 2011-06-30
These directions will let you remove GDM from your startup items, but still allow you to startup gdm (Gnome) if you want it.  The first few methods should still work on 11.04 with upstart.

[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/]("http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/")

---

### Post by compulsiveguile on 2011-06-30
> **rubylaser said:**
> These directions will let you remove GDM from your startup items, but still allow you to startup gdm (Gnome) if you want it.  The first few methods should still work on 11.04 with upstart.

[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/]("http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/")

I tried the first 2 methods, and I had no luck. Thanks for the link, though.

> **ajgreeny said:**
> You could just remove gdm from /usr/sbin, or make it non executable, or rename the gdm file in /etc/init.d, then on the occasions that you do need gnome you would need to use the command **startx**.

See also [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

[http://ubuntuforums.org/showpost.php?p=10798400&postcount=4 ](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4 ) did the trick. Thanks! :D

---

