---
title: "Incorrect memory usage in system monitor."
date: 2018-03-31
forum: Ubuntu Development Version
---

### Post by rektr3x99 on 2018-03-31
I have this issue with the System Monitor, under the resource tab -> Memory. 

The memory displayed is for the most part incorrect. 

OS : Ubuntu  18.04 Beta 1 
Environment : budgie 

applications used to monitor resources - Saidar and System Monitor. 

Attached is a screenshot from Saidar and System Monitor

Update : I just noticed that the screenshot is a bit blurry, System Monitor shows about 2.3GB of memory usage while Saidar shows about 3.8GB of usage.

---

### Post by deadflowr on 2018-03-31
What does free tell you?
```
free -h
```

---

### Post by jeremy31 on 2018-03-31
*Thread moved to **Ubuntu Development Version**.*

---

### Post by rektr3x99 on 2018-03-31
Hey, sorry for the late reply. 

But free -h still shows me 1.5GB used, this is closer to what system monitor's reading is showing. 

Though, I've seen other application report an incorrect value as well.

---

### Post by rektr3x99 on 2018-03-31
Here's top, system monitor and free -h. 

All of them report different values differing about ~100mb.

System Monitor before taking the screenshot read 1.7G, free -h returned 1.8G and top gave 1.91G

---

### Post by mörgæs on 2018-04-01
Please post terminal output as text in CODE tags. Makes it easier for everyone to read.

---

### Post by rektr3x99 on 2018-04-01
Sorry about the formatting 

Here's the terminal output : 

```
  
              total        used        free      shared  buff/cache   available
Mem:            15G        2.2G         12G        116M        1.4G         13G
Swap:          3.8G          0B        3.8G



```

---

### Post by dino99 on 2018-04-01
Feels like the shared mem does the difference  ;)

---

