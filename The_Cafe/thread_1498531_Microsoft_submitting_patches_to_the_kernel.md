---
title: "Microsoft submitting patches to the kernel?"
date: 2010-05-31
forum: The Cafe
---

### Post by pt123 on 2010-05-31
> The performance of the Linux 2.6.35 kernel code right now is a disaster. There is no other way to put this situation. While, yes, there still is a number of weeks left before the Linux 2.6.35 kernel release, it's inexplicable that a regression like this or change in behavior can even be accepted into the mainline Git tree at any point in the development cycle for such a mature project. That it can not only enter the kernel tree, but it can live for a week or more without either being corrected or the problematic commit being reverted. This is such a glaring performance issue across so many different tests and differently configured systems that it calls to question the current development practices and test procedures of the Linux kernel. These performance problems are affecting systems from Atom desktops to multi-core, high-end notebooks in tests from media encoding to synthetic disk tests.
[http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=5](http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=5)

Time to look for a new OS

---

### Post by Legendary_Bibo on 2010-05-31
I don't get it. What's going on exactly?

---

### Post by NightwishFan on 2010-05-31
Wasn't 2.6.34 just released only a bit ago?

---

### Post by BoneKracker on 2010-05-31
[IMG]http://www.seanpercival.com/blog/wp-content/uploads/sky-is-falling.jpg[/IMG]

---

### Post by Firestem4 on 2010-05-31
Microsofts work on the kernel comes after tons of demand from the enterprise (from what i remember) due to incompatibilities with the kernel and certain microsoft products that are supposed to work in the Unix enviroment. I wouldn't call this anything close to "Need to find a new OS."

---

### Post by NightwishFan on 2010-05-31
It is just phoronix.. Call me when a core developer gets word to you about this epic failure.

---

### Post by FuturePilot on 2010-05-31
How on earth does regressions in the kernel equate to Microsoft submitting patches to the kernel?
...

](*,)

---

### Post by chillicampari on 2010-05-31
The Microsoft Hyper-V kernel submissions were last year and this article isn't about that, this thread is confusing.

---

### Post by RiceMonster on 2010-05-31
In fact, they did submit code to the kernel already.

---

### Post by YuiDaoren on 2010-05-31
> **Firestem4 said:**
> Microsofts work on the kernel comes after tons of demand from the enterprise (from what i remember) due to incompatibilities with the kernel and certain microsoft products that are supposed to work in the Unix enviroment. I wouldn't call this anything close to "Need to find a new OS."
I was just going to post this. [Article.]("http://www.linux-mag.com/cache/7439/1.html")

So, clearly time to [FONT=Book Antiqua][SIZE=4]***[COLOR=Red]PANIC![/COLOR]***[/SIZE][/FONT] :P

(Especially as MS isn't mentioned in the OP article...)

---

### Post by pt123 on 2010-05-31
The Microsoft part is a joke, but the fact the 2.6.35 Kernel is so slow is perplexing. That you can only joke MS are submitting patches.

---

### Post by YuiDaoren on 2010-05-31
> **pt123 said:**
> The Microsoft part is a joke, but the fact the 2.6.35 Kernel is so slow is perplexing. That you can only joke MS are submitting patches.
I don't see how you get from one to the other...

But still, it's a regression. Regressions happen throughout FOSS, and even proprietary computing really. They tend to get fixed though.

I agree with the article that it's bewildering that such a significant regression got into the release, but I can't go from there to "time to get a new OS".

---

### Post by chessnerd on 2010-05-31
> **FuturePilot said:**
> How on earth does regressions in the kernel equate to Microsoft submitting patches to the kernel?
I believe the poster is trying to make a joke. Like, "Ha ha, bad coding. It must be from Microsoft."

My response to this:

So the kernel has some bad regressions? Big deal.

It's a development build, what do you expect. Someone committed some code and the code borked some systems. This happens in software projects ever day. My alpha testing of Opera 10.5x has shown me that. One build, Flash worked better than ever. The next, oops, bye-bye Flash. The next one, Flash works great again.

As the article said, 2.6.35 is *weeks* away from release. A lot can happen in a few weeks, and, if worst comes to worst, the bad code can be replaced with the older, working code. 

Linus Torvalds and his fellow hackers have been working on this project for 19 years. I trust them to work these issues out. :)

---

### Post by pt123 on 2010-05-31
> **YuiDaoren said:**
> I don't see how you get from one to the other...
Really ??? Linux is MS biggest competitor in the OS market. So whose interest would it be to have a Kernel release that performs 20-30% slow?
Jeezz

---

### Post by pwnst*r on 2010-05-31
> **pt123 said:**
> The Microsoft part is a joke, but the fact the 2.6.35 Kernel is so slow is perplexing. That you can only joke MS are submitting patches.

Are you for real?

THIS is the kind of member that the community does NOT need.  You're a joke.

---

### Post by chessnerd on 2010-05-31
> **pwnst*r said:**
> Are you for real?

THIS is the kind of member that the community does NOT need.  You're a joke.

Calm down, my friend. Ignorance must be met with knowledge and intelligence, not harsh words. This article/thread is not worth exiling or alienating a member of the community.

---

### Post by YuiDaoren on 2010-05-31
> **pt123 said:**
> Really ??? Linux is MS biggest competitor in the OS market. So whose interest would it be to have a Kernel release that performs 20-30% slow?
Jeezz
It's a huge jump from "competitor" to "saboteur".

More to the point: The whole MS bashing thing has just gotten *that* old.

---

### Post by chillicampari on 2010-05-31
> **pt123 said:**
> Really ??? Linux is MS biggest competitor in the OS market. So whose interest would it be to have a Kernel release that performs 20-30% slow?
Jeezz

The way it works is that anyone (or entity) has the freedom to make a submission. The submissions are tested and vetted prior to adoption. If anyone tried to slip a mickey in, their submission would be rejected.

---

### Post by KiwiNZ on 2010-05-31
Thread closed 
And not by Microsoft

---

