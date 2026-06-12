---
title: "how exactly do smartphones and tablets benefit from quad core?"
date: 2012-09-23
forum: The Cafe
---

### Post by burnitdown on 2012-09-23
Today most tablets and smartphones on the market have dual core processors on them. But some of them have quad core processors like iphone 5 and Nexus 7. I know dual core has benefits but how does quad core help when you basically can only run one app at a time?

---

### Post by vexorian on 2012-09-23
One app at a time, does not mean one process thread at a time. And often, it does not.

For example, you usually need a thread to detect events like network updates. Another thread to do processing, and perhaps a thread to draw. It requires the people behind the OS and the apps to really now how to do multi-threading though.

A web browser can really benefit for this. There are typically multiple things going on while a web page loads. Rendering, parsing HTML, interpreting Javascript...

---

### Post by szymon_g on 2012-09-23
they don't.
it's good for marketing, but for most people the difference between 2 and 4 cores are non-existing (same as on desktop).

---

### Post by Lightstar on 2012-09-23
Like everywhere else, I believe phone systems and apps will become bloated, bigger in size, requiring more memory and processing power even though they do simple tasks.  Creating a need for higher end phones.

I could run the old skype just fine on my old motorola milestone.  Now the newer skype wont load properly.  Making me wish I had a quad core phone, or even dual.  It's all about forcing people to upgrade to make money.  I think.

---

### Post by Mikeb85 on 2012-09-23
> **burnitdown said:**
> Today most tablets and smartphones on the market have dual core processors on them. But some of them have quad core processors like iphone 5 and Nexus 7. I know dual core has benefits but how does quad core help when you basically can only run one app at a time?

The iPhone 5 only has a dual core...

More cores in phones = better multitasking, and multi-threaded application performance.  For more day to day tasks though, you won't really notice more cores.

---

### Post by Copper Bezel on 2012-09-23
And it's definitely not true that a phone doesn't have background applications, anyway. I mean, there's a difference between multitasking as applies to daemons or services (and you can check the process list on an Android phone) but there are end-user applications that really do run actively in the background instead of suspending, too, like terminal sessions, anything to do with audio, etc. Tray apps that would be tray apps on a desktop, too, like a clipboard manager, if you have them.

---

### Post by KiwiNZ on 2012-09-23
A better user experience, greater capability, more feature rich applications.

---

### Post by vexorian on 2012-09-23
> **szymon_g said:**
> they don't.
it's good for marketing, but for most people the difference between 2 and 4 cores are non-existing (same as on desktop).
If your applications don't benefit from more cores, they are probably not coded very well.

---

### Post by Paqman on 2012-09-24
> **Mikeb85 said:**
> The iPhone 5 only has a dual core...


So basically what you're saying is Apples have less cores?

---

### Post by 3rdalbum on 2012-09-24
> **vexorian said:**
> If your applications don't benefit from more cores, they are probably not coded very well.

Not necessarily. It's really, really difficult to write an algorithm to spread work across multiple cores. Some things probably can't be split up into two discrete units, let alone four.

---

