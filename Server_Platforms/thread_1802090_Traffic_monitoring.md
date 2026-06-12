---
title: "Traffic monitoring?"
date: 2011-07-11
forum: Server Platforms
---

### Post by thobiasn on 2011-07-11
Just finished installing my first ubuntu apache, php, mysql server. This might be a nooby question, but is there a way to monitor the traffic that my website recieves, in realtime?

---

### Post by SoFl W on 2011-07-11
In terminal (or two terminal windows) run these commands.

To see what is being accessed:
tail -fn 100 /var/log/apache2/access.log

To see any errors:
tail -fn 100 /var/log/apache2/error.log

---

### Post by thobiasn on 2011-07-11
Perfect, Thanks! :D

---

### Post by karlson on 2011-07-11
> **thobiasn said:**
> Just finished installing my first ubuntu apache, php, mysql server. This might be a nooby question, but is there a way to monitor the traffic that my website recieves, in realtime?
What information are you looking to get?

---

### Post by thobiasn on 2011-07-11
Page requests.

---

### Post by elroyinc on 2011-07-11
On my server this is what I look at... webalizer... seems to break everything down

[http://70.126.188.158/webalizer/usage_201107.html](http://70.126.188.158/webalizer/usage_201107.html)

---

### Post by brokenbynubs on 2011-11-02
> **SoFl W said:**
> In terminal (or two terminal windows) run these commands.

To see what is being accessed:
tail -fn 100 /var/log/apache2/access.log

To see any errors:
tail -fn 100 /var/log/apache2/error.log

I was just looking for this exact solution, thank you!

---

