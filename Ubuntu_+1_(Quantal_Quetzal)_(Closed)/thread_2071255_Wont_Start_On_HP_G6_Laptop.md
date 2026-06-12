---
title: "Wont Start On HP G6 Laptop"
date: 2012-10-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mr john on 2012-10-15
Screen goes black and wont start when I try to boot from the unetbootin created usb stick. It works fine on other computers. This laptop is quite a common laptop. I think the problem could be relating to video drivers.

I've heard that using the nomodeset option at boot time might work, but 1. I don't know how to do this from a unetbootin generated installer and 2. The average joe shouldn't need to be messing around with this sort of thing.


update: pressing the tab button on the unetbootin menu allowed me to add nomodeset and it seems to be starting. However I still believe this issue can give new users a bad first-time experience and needs to be fixed.

update2: The purple screen came up and it looked like it was going to boot with nomodeset... Sadly that went away and left me with a black screen.

---

### Post by tista on 2012-10-15
> **mr john said:**
> Screen goes black and wont start when I try to boot from the unetbootin created usb stick. It works fine on other computers. This laptop is quite a common laptop. I think the problem could be relating to video drivers.

I've heard that using the nomodeset option at boot time might work, but 1. I don't know how to do this from a unetbootin generated installer and 2. The average joe shouldn't need to be messing around with this sort of thing.


update: pressing the tab button on the unetbootin menu allowed me to add nomodeset and it seems to be starting. However I still believe this issue can give new users a bad first-time experience and needs to be fixed.

update2: The purple screen came up and it looked like it was going to boot with nomodeset... Sadly that went away and left me with a black screen.

Hi John.. :)

Well.. I don't have any ideas why newbie wants to try Quantal out in this period... If you were one of new users, please use Precise Pangolin (12.04 LTS). Quantal is still under RC.

Best Regards,
Tista

**EDIT**
I've found some article about your HP G6 laptop, and then this might help you:
[http://admaris.com/wp/blog/2012/07/15/hp-g6-laptop-ralink-problems-solved-in-ubuntu-12-04/]("http://admaris.com/wp/blog/2012/07/15/hp-g6-laptop-ralink-problems-solved-in-ubuntu-12-04/")

It seems that your laptop would have some problems on backlight control via linux's acpi. I don't think it's Ubuntu's fault. Yeah means kernel problems, but anyway it could be solved by that workaround. If so, I could recommend Precise stable release for you at all. :)

---

### Post by rtalcott on 2012-10-15
This worked for me...HP dm4 with 12.04:
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)

Same thing (mostly) as what has been suggested....my HP does not want to boot to anything but black with 12.10 but I have not had time to work on this.

---

### Post by mr john on 2012-10-15
By this freeze stage of the development process for Quetzal I would have expected this bug to be fixed. It was reported a considerable amount of time ago. 

Ps. I'm not a new user, I've been using Ubuntu since 2006. The reason I mentioned new users is that HP is the second largest PC manufacturer, and what we see in Quetzal this week is probably what the final is going to look like.

---

