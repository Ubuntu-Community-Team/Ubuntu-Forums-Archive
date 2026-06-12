---
title: "How to log transfered data from/to server?"
date: 2010-01-13
forum: Server Platforms
---

### Post by rado3105 on 2010-01-13
Is any way to see or log downloaded and uploaded data from ubuntu server? How much data per day,month, year..I also tryed cacti but I couldnt find any template to graph network traffic.

---

### Post by Barriehie on 2010-01-13
> **rado3105 said:**
> Is any way to see or log downloaded and uploaded data from ubuntu server? How much data per day,month, year..I also tryed cacti but I couldnt find any template to graph network traffic.

[[color="blue"]This[/color]](http://www.mrunix.net/webalizer/) is in the repos.  Haven't used it but it's touted to do what you're looking for.

---

### Post by rado3105 on 2010-01-14
Thanks, looks nice. To get on page: localhost/webalizer. It dont count network traffic, propably it nees some other program.

---

### Post by mtron on 2010-01-14
i use vnstat for the monitoring. In conjunction with the "[VNstat php frontend]("http://www.sqweek.com/sqweek/index.php?p=1")" (that generates nice statistics)  it's a easy and appealing way that should fit your needs.

Screenshot: [http://www.sqweek.com/sqweek/files/scrot1.png](http://www.sqweek.com/sqweek/files/scrot1.png)

---

### Post by rado3105 on 2010-01-14
thanks mtron, it works

---

