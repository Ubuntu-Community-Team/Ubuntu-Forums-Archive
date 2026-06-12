---
title: "How do I install the latest nvidia bianry?"
date: 2012-06-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kyleabaker on 2012-06-15
I just setup my Quantal Quetzal partition and installed a couple days ago and have been giving Neavou a test drive since I've never really used it. After a couple days and use its just annoyingly slow and sluggish.

I decided I want to install the latest nvidia drivers again, like on my Percise partition, but the Additional Drivers window is now populated with a lot of new drivers and is not very specific about versions.

Which one should I activate for my nvidia 7300le card?

[img]http://img205.imageshack.us/img205/2118/screenshotfrom201206151.png[/img]

---

### Post by cariboo on 2012-06-15
As a work-around, I'd suggest you use synaptic to innstall the driver you normally use, until things get straightened out.

---

### Post by balloons on 2012-06-15
> **kyleabaker said:**
> I just setup my Quantal Quetzal partition and installed a couple days ago and have been giving Neavou a test drive since I've never really used it. After a couple days and use its just annoyingly slow and sluggish.

I decided I want to install the latest nvidia drivers again, like on my Percise partition, but the Additional Drivers window is now populated with a lot of new drivers and is not very specific about versions.

Which one should I activate for my nvidia 7300le card?

[img]http://img205.imageshack.us/img205/2118/screenshotfrom201206151.png[/img]

I have a 7300gt; both the noveau and nvidia drivers worked. For nvidia, 

```
sudo apt-get install nvidia-current-updates nvidia-common nvidia-settings-updates
```

works for me.

---

### Post by kyleabaker on 2012-06-15
Thanks guys!

---

### Post by ronacc on 2012-06-16
for me nvidia-current-updates and nvidia-settings-updates fail with error code 1 .

---

