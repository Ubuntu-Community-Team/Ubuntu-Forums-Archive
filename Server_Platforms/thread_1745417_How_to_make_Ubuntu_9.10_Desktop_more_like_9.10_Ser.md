---
title: "How to make Ubuntu 9.10 Desktop more like 9.10 Server??"
date: 2011-05-01
forum: Server Platforms
---

### Post by GeissT on 2011-05-01
Hey,

So, another thread that I made [here]("http://ubuntuforums.org/showthread.php?t=1706703") did solve my issues, but the Downloads were an issue. So I have come to a conclusion that I will install Desktop rather than server and simply remove the packages that aren't needed. Now, this sounds easy enough, right? Sorta' but I am not sure of all the packages that need to be uninstalled, obvious ones like Open Office etc etc are easy enough to recognize, but what would be other packages that would be a good idea to remove?

Also whilst im here, I am going to use Webmin for administration, so is that compatible with XAMPP for Linux, or would i need to use the package manager to install apache2, mysql-server etc etc?

Thanks in advance.

GeissT

---

### Post by CharlesA on 2011-05-01
You could purge the ubuntu-desktop package, but keep in mind that 9.10 is no longer supported since Natty is out.

I do know that wireless is iffy on the server install - iffy in that it can be a pain to configure without a GUI.

---

### Post by GeissT on 2011-05-01
Yeah,

Well thank you, I think the wireless issues you are reffering to are the same as I have encountered, I shall install 9.10 as its a old laptop and i cant use 10.04 or higher. (500, yes 500MB of RAM.) But Im getting a new server machine in the next year or so.

Thanks mate,

GeissT

PS: Any help with the Webmin question?

---

### Post by CharlesA on 2011-05-01
Webmin should work fine. I used to use it, but not since I got used to just SSHing into the box and doing my work there.

---

### Post by GeissT on 2011-05-01
Okay, what about installing LAMP and SSH from the TASKSEL command? Good idea or not?

---

### Post by CharlesA on 2011-05-01
That's how I installed it. :)

Just remember not to deselect anything, as it can remove packages that ubuntu desktop needs.

---

### Post by GeissT on 2011-05-01
Sure thing :) Thanks alot, I just tried reinstalling Ubuntu Desktop and then my HDD literally died XD Ill have to do all this when i get a new hdd, thanks soo much again :)

GeissT

---

